.. _qg:

Quick start guide
*****************

For those users who want to quickly try the role this guide provides
an example of how to install and configure `Lighttpd
<https://www.lighttpd.net/>`_ on single FreeBSD host. The procedure is
generic and can be easily modified to install and configure other
applications on other systems. See examples in the directory
*contrib*. The control node of this example is Linux and the user is
member of the group *adm*.


* Install the role ``vbotka.config_light`` ::

    shell> ansible-galaxy install vbotka.config_light


* Create the playbook ``config-light.yml`` for single host srv.example.com (2)

.. code-block:: bash
   :emphasize-lines: 2
   :linenos:

   shell> cat config-light.yml
   - hosts: srv.example.com
     gather_facts: true
     connection: ssh
     remote_user: admin
     become: yes
     become_user: root
     become_method: sudo
     roles:
       - vbotka.config_light


* Create ``host_vars`` with customized variables of the role and with the variables of the application.

.. code-block:: yaml
   :emphasize-lines: 2-3
   :linenos:

   shell> ls -1 host_vars/srv.example.com/config-light-*
   host_vars/srv.example.com/config-light-common.yml
   host_vars/srv.example.com/config-light-lighttpd.yml


* Create *host_vars* with customized variables of the role. To speedup the execution let's set the control-flow variables (2-5) to *false* and disable some steps. Enable these steps selectively when needed. The configuration files of the role will be stored in the directory *conf-light* in the current directory of the playbook (10). Set the ownership and permissions of the directories on the cont-roll node so that the user who is running the playbook will be able both read and write the files, and create the directories (7-9) (11-14).

.. code-block:: yaml
   :emphasize-lines: 2-5,10
   :linenos:

   shell> cat host_vars/srv.example.com/config-light-common.yml
   cl_sanity: false
   cl_setup: false
   cl_install: false
   cl_debug: false
   cl_backup: true
   cl_dird_owner: "root"
   cl_dird_group: "adm"
   cl_dird_dmode: "0770"
   cl_dird: "{{ playbook_dir }}/conf-light"
   cl_dira_owner: "root"
   cl_dira_group: "adm"
   cl_dira_dmode: "0770"
   cl_dira_fmode: "0660"


* Create *host_vars* with the variables of the application. Start the server (2), run the server at boot (3), and configure two files.

.. code-block:: yaml
   :emphasize-lines: 2,3,5,23
   :linenos:

   shell> cat host_vars/srv.example.com/config-light-lighttpd.yml
   cl_service_lighttpd_enable: true
   cl_service_lighttpd_state: 'started'

   # /usr/local/etc/lighttpd/lighttpd.conf
   cl_lighttpd_server_port: '80'
   cl_lighttpd_server_useipv6: 'disable'
   cl_lighttpd_server_username: 'www'
   cl_lighttpd_server_groupname: 'www'
   cl_lighttpd_server_document_root: "/usr/local/www/lighttpd"
   cl_lighttpd_lighttpdconf_lines:
     - regexp: '^\s*server.port\s*=\s*(.*)$'
       line: 'server.port = "{{ cl_lighttpd_server_port }}"'
     - regexp: '^\s*server.use-ipv6\s*=\s*(.*)$'
       line: 'server.use-ipv6 = "{{ cl_lighttpd_server_useipv6 }}"'
     - regexp: '^\s*server.username\s*=\s*(.*)$'
       line: 'server.username = "{{ cl_lighttpd_server_username }}"'
     - regexp: '^\s*server.groupname\s*=\s*(.*)$'
       line: 'server.groupname = "{{ cl_lighttpd_server_groupname }}"'
     - regexp: '^\s*server.document-root\s*=\s*(.*)$'
       line: 'server.document-root = "{{ cl_lighttpd_server_document_root }}"'

   # /etc/rc.conf
   cl_lighttpd_rcconf_lighttpd_enable: 'YES'
   cl_lighttpd_rcconf_lines:
       - regexp: '^lighttpd_enable(.*)$'
         line: 'lighttpd_enable="{{ cl_lighttpd_rcconf_lighttpd_enable }}"'


* Create configuration files in the directory ``conf-light``.

.. code-block:: bash
   :emphasize-lines: 3,6,8,10,12
   :linenos:

   shell> tree conf-light
   conf-light/
   ├── files.d
   │   ├── lighttpd-lighttpdconf
   │   └── lighttpd-rcconf
   ├── handlers.d
   │   └── lighttpd-freebsd
   ├── packages.d
   │   └── lighttpd
   ├── services.d
   │   └── lighttpd
   └── states.d
       └── lighttpd-server-document-root


*conf-light/files.d*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/files.d/lighttpd-lighttpdconf 
   lighttpd-lighttpdconf:
     path: '/usr/local/etc/lighttpd/lighttpd.conf'
     create: true
     owner: 'root'
     group: 'wheel'
     mode: '0644'
     lines: '{{ cl_lighttpd_lighttpdconf_lines }}'
     handlers:
       - 'reload lighttpd'

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/files.d/lighttpd-rcconf 
   lighttpd_rcconf:
     path: '/etc/rc.conf'
     create: true
     owner: 'root'
     group: 'wheel'
     mode: '0644'
     lines: "{{ cl_lighttpd_rcconf_lines }}"
     handlers:
       - 'reload lighttpd'


*conf-light/handlers.d*

.. code-block:: yaml
   :emphasize-lines: 6,13,20,28,36
   :linenos:

   shell> cat conf-light/handlers.d/lighttpd-freebsd 
   lighttpd_freebsd:
     template: handlers-auto1.yml.j2
     params:
   
       - handler: 'enable and start lighttpd'
         module: service
         params:
           - 'name: lighttpd'
           - 'state: started'
           - 'enabled: true'
   
       - handler: 'disable and stop lighttpd'
         module: service
         params:
           - 'name: lighttpd'
           - 'state: stopped'
           - 'enabled: false'
   
       - handler: 'reload lighttpd'
         module: service
         params:
           - 'name: lighttpd'
           - 'state: reloaded'
         conditions:
           - '- cl_service_lighttpd_enable|bool'
   
       - handler: 'restart lighttpd'
         module: service
         params:
           - 'name: lighttpd'
           - 'state: restarted'
         conditions:
           - '- cl_service_lighttpd_enable|bool'
   
       - handler: 'lighttpd check'
         module: command
         params:
        - 'cmd: /usr/local/sbin/lighttpd -t'


*conf-light/packages.d*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/packages.d/lighttpd 
   lighttpd:
     name: 'www/lighttpd'


*conf-light/services.d*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/services.d/lighttpd 
   lighttpd:
     name: 'lighttpd'
     state: '{{ cl_service_lighttpd_state }}'
     enabled: '{{ cl_service_lighttpd_enable }}'


*conf-light/states.d*

.. code-block:: yaml
   :emphasize-lines: 3
   :linenos:

   shell> cat conf-light/states.d/lighttpd-server-document-root 
   lighttpd_server_document_root:
     state: directory
     path: '{{ cl_lighttpd_server_document_root }}'
     owner: '{{ cl_lighttpd_server_username }}'
     group: '{{ cl_lighttpd_server_groupname }}'
     mode: '0750'


* Enable setup and create variables ::

    shell> ansible-playbook config-light.yml -t cl_vars -e 'cl_setup=true'

This command will assemble the configuration data and create handlers
on the control node. Take a look at directory ``conf-light/assemble/``
what files were created. Also take a look at the directory
``roles/vbotka.config_light/handlers`` what handlers were created.


* Enable and test sanity ::

    shell> ansible-playbook config-light.yml -t cl_sanity -e 'cl_sanity=true'


* Display variables ::

    shell> ansible-playbook config-light.yml -t cl_debug -e 'cl_debug=true'

* Install packages ::

    shell> ansible-playbook config-light.yml -t cl_packages -e 'cl_install=true'

* Set files' states ::

    shell> ansible-playbook config-light.yml -t cl_states

* Create and modify files ::

    shell> ansible-playbook config-light.yml -t cl_files

* Configure services ::

    shell> ansible-playbook config-light.yml -t cl_services

* The role and the configuration data in the examples are idempotent. Once the application is installed and configured there should be no changes reported by *ansible-playbook* when running the playbook repeatedly. Disable setup, sanity, debug, and install to speedup the playbook

.. code-block:: bash
   :emphasize-lines: 6
   :linenos:

    shell> ansible-playbook config-light.yml

    [...]
    
    PLAY RECAP ***************************************************************************
    srv.example.com: ok=21 changed=0 unreachable=0 failed=0 skipped=35 rescued=0 ignored=0


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

