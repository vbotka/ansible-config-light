.. _qg:

Quick start guide
#################

For users who want to try the role quickly, this guide provides an
example on how to install and configure `lighttpd
<https://www.lighttpd.net/>`_ on single FreeBSD host. The procedure is
generic and can be easily modified to install and configure other
applications on other systems. See examples in the directory
*contrib*. The control node of this example is Linux and the user
running the playbook on the controller is a member of the group *adm*.


* Install the role ``vbotka.config_light`` ::

    shell> ansible-galaxy role install vbotka.config_light


* Install the collections if necessary ::

    shell> ansible-galaxy collection install ansible.posix
    shell> ansible-galaxy collection install community.general


* Install ``yamllint`` to use the default validation of the created
  handlers and assembled data. See the variables
  *cl_assemble_validate* and *cl_handlers_validate* in
  *defaults/main.yml*. Optionally, use *ansible-lint* or disable the
  validation by clearing the variables ::

    cl_assemble_validate: ''
    cl_handlers_validate: ''


* Create the playbook ``pb.yml`` for single host *srv.example.com* (2)
  and the role *vbotka.config_light* (11)

.. code-block:: yaml
   :emphasize-lines: 2,11
   :linenos:

   shell> cat pb.yml
   - hosts: srv.example.com
     gather_facts: true
     connection: ssh
     remote_user: admin
     become: true
     become_user: root
     become_method: sudo

     roles:
       - vbotka.config_light


* Create files in ``host_vars`` with customized variables of the
  role (2) and with the variables of the application (3)

.. code-block:: bash
   :emphasize-lines: 2-3
   :linenos:

   shell> ls -1 host_vars/srv.example.com/cl-*
   host_vars/srv.example.com/cl-common.yml
   host_vars/srv.example.com/cl-lighttpd.yml


* Configure the role. To speedup the execution set the control-flow variables (2-5) to
  *false* and disable some steps. Enable these steps selectively when
  needed. The configuration data will be stored in the directory
  *conf-light* (10) in the current directory of the playbook. Set the
  ownership and permissions of the directories on the control node so
  that the user who is running the playbook will be able both read and
  write the files, and create the directories (7-9) (11-14).

.. code-block:: yaml
   :emphasize-lines: 2-5,10
   :linenos:

   shell> cat host_vars/srv.example.com/cl-common.yml
   cl_sanity: false
   cl_setup: false
   cl_install: false
   cl_debug: false
   cl_backup: true
   cl_dird_owner: root
   cl_dird_group: adm
   cl_dird_dmode: '0770'
   cl_dird: "{{ playbook_dir }}/conf-light"
   cl_dira_owner: root
   cl_dira_group: adm
   cl_dira_dmode: '0770'
   cl_dira_fmode: '0660'

.. note::
   * The configuration data will be assembled into the directory *cl_dira*
   * The default value of *cl_dira* is *{{ cl_dird }}/assemble*

* Configure the application. Start the server (2), run the server at
  boot (3), and configure two files (5,18).

.. code-block:: yaml
   :emphasize-lines: 2,3,5,18
   :linenos:

   shell> cat host_vars/srv.example.com/cl-lighttpd.yml
   cl_service_lighttpd_enable: true
   cl_service_lighttpd_state: started

   # /usr/local/etc/lighttpd/lighttpd.conf
   cl_lighttpd_server_port: '80'
   cl_lighttpd_server_useipv6: disable
   cl_lighttpd_server_username: www
   cl_lighttpd_server_groupname: www
   cl_lighttpd_server_document_root: /usr/local/www/lighttpd
   cl_lighttpd_lighttpdconf_dict:
     - {key: server.port, value: '"{{ cl_lighttpd_server_port }}"'}
     - {key: server.use-ipv6, value: '"{{ cl_lighttpd_server_useipv6 }}"'}
     - {key: server.username, value: '"{{ cl_lighttpd_server_username }}"'}
     - {key: server.groupname, value: '"{{ cl_lighttpd_server_groupname }}"'}
     - {key: server.document-root, value: '"{{ cl_lighttpd_server_document_root }}"'}

   # /etc/rc.conf
   cl_lighttpd_rcconf_lighttpd_enable: 'YES'
   cl_lighttpd_rcconf_dict:
     - {key: lighttpd_enable, value: '"{{ cl_lighttpd_rcconf_lighttpd_enable }}"'}


* Create configuration data in the directory ``conf-light``

.. code-block:: bash
   :emphasize-lines: 3,6,8,10,12
   :linenos:

   shell> tree conf-light
   conf-light/
   ├── files.d
   │   ├── lighttpd-lighttpdconf.yml
   │   └── lighttpd-rcconf.yml
   ├── handlers.d
   │   └── lighttpd-freebsd.yml
   ├── packages.d
   │   └── lighttpd.yml
   ├── services.d
   │   └── lighttpd.yml
   └── states.d
       └── lighttpd-server-document-root.yml


* conf-light/files.d/*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/files.d/lighttpd-lighttpdconf.yml
   lighttpd-lighttpdconf:
     path: /usr/local/etc/lighttpd/lighttpd.conf
     create: true
     owner: root
     group: wheel
     mode: '0644'
     assignment: ' = '
     dict: "{{ cl_lighttpd_lighttpdconf_dict }}"
     handlers:
       - reload lighttpd

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/files.d/lighttpd-rcconf.yml
   lighttpd_rcconf:
     path: /etc/rc.conf
     create: true
     owner: root
     group: wheel
     mode: '0644'
     assignment: '='
     dict: "{{ cl_lighttpd_rcconf_dict }}"
     handlers:
       - reload lighttpd


* conf-light/handlers.d/*

.. code-block:: yaml
   :emphasize-lines: 7,14,21,29,37
   :linenos:

   shell> cat conf-light/handlers.d/lighttpd-freebsd.yml
   lighttpd_freebsd:

     template: handlers-auto2.yml.j2
     handlers:
   
       - handler: enable and start lighttpd
         module: service
         params:
           - 'name: lighttpd'
           - 'state: started'
           - 'enabled: true'
   
       - handler: disable and stop lighttpd
         module: service
         params:
           - 'name: lighttpd'
           - 'state: stopped'
           - 'enabled: false'
   
       - handler: reload lighttpd
         module: service
         params:
           - 'name: lighttpd'
           - 'state: reloaded'
         conditions:
           - '- cl_service_lighttpd_enable|bool'
   
       - handler: restart lighttpd
         module: service
         params:
           - 'name: lighttpd'
           - 'state: restarted'
         conditions:
           - '- cl_service_lighttpd_enable|bool'
   
       - handler: lighttpd check
         module: command
         params:
           - 'cmd: /usr/local/sbin/lighttpd -t'


* conf-light/packages.d/*

.. code-block:: yaml
   :emphasize-lines: 5
   :linenos:

   shell> cat conf-light/packages.d/lighttpd.yml
   lighttpd:
     module: pkgng
     name:
       - www/lighttpd


* conf-light/services.d/*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/services.d/lighttpd.yml
   lighttpd:
     name: lighttpd
     state: "{{ cl_service_lighttpd_state }}"
     enabled: "{{ cl_service_lighttpd_enable }}"


* conf-light/states.d/*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/states.d/lighttpd-server-document-root.yml
   lighttpd_server_document_root:
     state: directory
     path: "{{ cl_lighttpd_server_document_root }}"
     owner: "{{ cl_lighttpd_server_username }}"
     group: "{{ cl_lighttpd_server_groupname }}"
     mode: '0750'


* Enable setup and assemble configuration data. This command will
  assemble the configuration data and create handlers on the control
  node. Take a look at the directory ``conf-light/assemble/`` what
  files were created. Also take a look at the directory
  ``roles/vbotka.config_light/handlers`` what handlers were
  created. ::

    shell> ansible-playbook pb.yml -t cl_vars -e cl_setup=true

  .. note::

   * The tasks *setup*, *vars*, and *sanity* are tagged ``always``

   * The tasks *setup* and *sanity* are enabled by default
     (*cl_setup: true, cl_sanity: true*)


* Enable and test sanity ::

    shell> ansible-playbook pb.yml -t cl_sanity -e cl_sanity=true


* Display variables ::

    shell> ansible-playbook pb.yml -t cl_debug -e cl_debug=true


* Install packages ::

    shell> ansible-playbook pb.yml -t cl_packages -e cl_install=true


* Set states of the files ::

    shell> ansible-playbook pb.yml -t cl_states


* Create and modify files ::

    shell> ansible-playbook pb.yml -t cl_files


* Configure services ::

    shell> ansible-playbook pb.yml -t cl_services


  .. hint::

     If you know what you are doing skip the above selection of
     particular tags and run the complete role at once ::

      shell> ansible-playbook pb.yml -e cl_setup=true -e cl_install=true


  .. note::

     The role and the configuration data in the examples are
     idempotent. Once the application is installed and configured
     *ansible-playbook* shouldn't report any changes. To speedup the
     playbook disable setup, sanity, debug, and install. This way, the
     role will audit the required infrastructure ::

      shell> ansible-playbook pb.yml

      [...]

      PLAY RECAP ***************************************************************************
      srv.example.com: ok=29 changed=0 unreachable=0 failed=0 skipped=88 rescued=0 ignored=0


* Create file ``/usr/local/www/lighttpd/index.html``

.. code-block:: bash
   :emphasize-lines: 2,4
   :linenos:

   shell> ll /usr/local/www/lighttpd/index.html 
   -rw-r--r--  1 www  www  51 Apr 12 18:58 /usr/local/www/lighttpd/index.html
   shell> cat /usr/local/www/lighttpd/index.html 
   <html><body><h1>Lighttpd works!</h1></body></html>


* Open the page in a browser ``http://srv.example.com/``. The content should be ::

   Lighttpd works!
