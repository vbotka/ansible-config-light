.. _ug:

User's guide
************
.. contents:: Table of Contents
   :depth: 3


.. _ug_introduction:

Introduction
============

* Ansible role: `config_light <https://galaxy.ansible.com/vbotka/config_light/>`_
* Supported systems: `FreeBSD <https://www.freebsd.org/releases/>`_, `Ubuntu <http://releases.ubuntu.com/>`_
* Requirements: None

The role installs packages, creates and configures files, services,
and handlers. This provides a simple, but flexible framework to apply
basic Ansible modules. A substantial part of the control-flow will be
determined by the structure of the data. Some attributes of the
dictionaries trigger Ansible modules to modify configuration files,
configure services and create handlers.

The role can be used with any supported OS to install and configure
arbitrary applications. The role is tested with supported releases of
FreeBSD and Ubuntu. It can be expected that other BSD and Linux
distributions, that support the Ansible modules mentioned below,
should work with minimal changes. Red Hat and Debian
*ansible_os_family* should work out of the box.

Used Ansible modules comprise ``package`` to install Linux packages,
and both ``pkgng`` and ``portinstall`` to install FreeBSD packages or
ports.

Ansible modules ``file``, ``template``, ``lineinfile``,
``blockinfile``, and ``ini_file`` are used to configure files. Module
``service`` is used to manage both Linux and FreeBSD services.

The directory ``contrib`` comprises examples of how to install and
configure various applications, and how to create the handlers and
templates.

The user of this role is expected to master at least the following
Ansible topics:

* `Basic Concepts <https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html>`_
* `Roles <https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html>`_
* `Working With Playbooks <https://docs.ansible.com/ansible/latest/user_guide/playbooks.html>`_

Feel free to `share your feedback and report issues <https://github.com/vbotka/ansible-config-light/issues>`_. The contributions to the `project <https://github.com/vbotka/ansible-config-light/>`_ are welcome.

.. _ug_installation:

Installation
============

The most convenient way how to install an Ansible role is to use
Ansible Galaxy CLI ``ansible-galaxy``. The utility comes with the
standard Ansible package and provides the user with a simple interface
to the Ansible Galaxy's services. For example, take a look at the
current status of the role ::

    shell> ansible-galaxy info vbotka.config_light

and install it ::

    shell> ansible-galaxy install vbotka.config_light

.. seealso:: * To install specific versions from various sources see `Installing content <https://galaxy.ansible.com/docs/using/installing.html>`_.
	     * Take a look at other roles ``shell> ansible-galaxy search --author=vbotka``


.. _ug_playbook:

Playbook
========

Below is a simple playbook that calls this role at a single host
srv.example.com (2)

.. code-block:: bash
   :emphasize-lines: 1
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

.. note:: ``gather_facts: true`` (3) must be set to gather facts
          needed to evaluate OS-specific options of the role. For
          example to install packages the variable *ansible_os_family*
          is needed to select the appropriate Ansible module.

.. seealso:: * For details see `Connection Plugins
               <https://docs.ansible.com/ansible/latest/plugins/connection.html>`__ (4-5)
             * and `Understanding Privilege Escalation
               <https://docs.ansible.com/ansible/latest/user_guide/become.html#understanding-privilege-escalation>`__ (6-8).


.. _ug_debug:

Debug
=====

To see additional debug information enable debug output in the
configuration ::

    cl_debug: true

, or set the extra variable in the command: ::

    shell> ansible-playbook config-light.yml -e 'cl_debug=true'

.. note:: The debug output of this role is optimized for the ``yaml``
          callback plugin. Set this plugin for example in the
          environment ``shell> export ANSIBLE_STDOUT_CALLBACK=yaml``.

.. seealso:: * `Playbook Debugger <https://docs.ansible.com/ansible/latest/user_guide/playbooks_debugger.html>`_


.. _ug_tags:

Tags
====

The tags provide a very useful tool to run selected tasks of the
role. To see what tags are available list the tags of the role with
the command:

.. code-block:: bash
   :emphasize-lines: 1
   :linenos:

    shell> ansible-playbook config-light.yml --list-tags

    playbook: config-light.yml

      play #1 (srv.example.com): srv.example.com	TAGS: []
      TASK TAGS: [always, cl_debug, cl_files, cl_packages, cl_sanity, cl_services, cl_setup, cl_states, cl_vars]

For example, display the list of the variables and their values with
the tag ``cl_debug`` (when the debug is enabled ``cl_debug:
true``). With this tag specified ``-t cl_debug`` all imported tasks
before the task *debug.yml* will also run because of the tag ``always``
(when sanity testing is enabled ``cl_sanity: true`` and setup is
enabled ``cl_setup: true``). This is the default. See
:ref:`as_main_yml`. ::

    shell> ansible-playbook config-light.yml -t cl_debug

See what packages will be installed ::

    shell> ansible-playbook config-light.yml -t cl_packages --check

Install packages and exit the play ::

    shell> ansible-playbook config-light.yml -t cl_packages


.. _ug_variables:

Variables
=========

In this chapter we describe role's default variables stored in the
directory ``defaults``.

.. seealso:: * `Ansible variable precedence: Where should I put a variable? <https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable>`_


.. _ug_defaults:

Default variables
-----------------

Most of the variables are self-explaining. There are five very
important variables ``cl_handlers``, ``cl_packages``, ``cl_states``,
``cl_services``, and ``cl_files`` (11-15). These dictionaries, which
comprise the configuration data of handlers, packages, services, and
files, will be explained in details. By default these dictionaries are
empty.

Best practice is to provide the data either in *host_vars* and
*group_vars* or as a files in the directories ``cl_handlersd_dir``,
``cl_packagesd_dir``, ``cl_statesd_dir``, ``cl_servicesd_dir``, and
``cl_filesd_dir`` (22-26). Both methods can be applied at the same
time. The variables will be assembled and combined by the tasks
``vars_handlers.yml``, ``vars_packages.yml``, ``vars_states.yml``,
``vars_services.yml``, and ``vars_files.yml``. The assembled
dictionaries, customized for each host in the play, will be stored in
the host-specific files ``cl_packagesd``, ``cl_statesd``,
``cl_servicesd``, and ``cl_filesd`` (35-38). The variable
``cl_handlers`` is not host-specific, because the handlers will be
created at the controller (localhost) only. Assembled dictionary
``cl_handlers`` will be stored in the file ``cl_handlersd`` (34). Take
a look at the directory ``cl_dira`` (33) to see assembled data.

By default, the base of the directories is ``role_path`` (21). The user
is expected to put the configuration data to a more suitable directory,
e.g., to ``playbook_dir`` directory.

[`defaults/main.yml <https://github.com/vbotka/ansible-config-light/blob/master/defaults/main.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../defaults/main.yml
    :language: yaml
    :emphasize-lines: 2, 11-15
    :linenos:

.. warning:: Defaults of the variables *cl_dird_dmode* (20), *cl_dira_dmode* (31) and *cl_dira_fmode* (32) are very permissive. These are the permissions to access the configuration data and the assembled dictionaries. Restrict the permissions if these dictionaries might comprise classified data.

<TODO: complete description of all default variables>


.. _ug_handlers:

cl_handlers - dictionary with handlers
--------------------------------------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_handlers* is a dictionary of the handlers. The
Structure of the dictionary depends on the template that is used to
create the file with the handlers. For example, the structure below
can be used with the template *handlers-auto1.yml.j2*.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **template**                | *string*           | Template filename
                              | ``required``       |
| **handler**                 | *string*           | Name of the handler
                              | ``required``       |
| **module**                  | *string*           | Ansible module in handler
                              | ``required``       |
| **params**                  | *list*             | Ansible module parameters
                              | ``required``       |
| **conditions**              | *list*             | List of conditions
                              |                    |
============================= ==================== ============================

Example
^^^^^^^
FreeBSD handlers for postfix

[`contrib/postfix/conf-light/handlers.d/postfix-freebsd <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/postfix-freebsd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/postfix-freebsd
    :language: yaml
    :emphasize-lines: 2,5,12,19,27,35,40
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-handlers.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-handlers.yml>`_ how the variable *cl_handlers* is combined with the content of the directory *cl_handlersd_dir*.

   * See `setup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/setup.yml>`_ how the handlers are created.

   * For details see the template `handlers-auto1.yml.j2  <https://github.com/vbotka/ansible-config-light/blob/master/templates/handlers-auto1.yml.j2>`_.
	     
Notes
^^^^^
.. note:: The template *handlers-auto1.yml.j2* is available in the
          role's directory ``templates``. The user is expected to
          create new templates when needed. Feel free to change the
          structure of the data and to create new templates that might
          fit the purpose better. Feel free to contribute new
          templates and configuration examples to the `project
          <https://github.com/vbotka/ansible-config-light/>`_.


.. _ug_packages:

cl_packages - dictionary with packages or BSD ports
---------------------------------------------------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_packages* is a dictionary of the packages or BSD
ports to be installed.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **name**                    | *string*           | Package or BSD port
                              | ``required``       |
============================= ==================== ============================

Example
^^^^^^^

FreeBSD package for Postfix

[`contrib/postfix/conf-light/packages.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix
    :language: yaml
    :emphasize-lines: 2
    :linenos:

Armbian package for Simple SMTP

[`contrib/ssmtp/conf-light/packages.d/ssmtp <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-packages.yml>`_ how the variable *cl_packages* is combined with the content of the directory *cl_packagesd_dir*.

   * See `packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/packages.yml>`_ how the packages or BSD ports are installed.


.. _ug_states:

cl_states - dictionary of files' states
---------------------------------------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_states* is a dictionary of the files' states.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **state**                   | *string*           | State of the filename
                              | ``required``       |
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
============================= ==================== ============================

<TODO: complete parameters. See tasks/states.yml>


Example
^^^^^^^
File's states

[`contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-states.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-states.yml>`_ how the variable *cl_states* is combined with the content of the directory *cl_statesd_dir*.

   * See `states.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/states.yml>`_ how the file's states are set.


.. _ug_services:

cl_services - dictionary with services
--------------------------------------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_services* is a dictionary with the services managed
by this role.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **name**                    | *string*           | Service
                              | ``required``       |
| **state**                   | *string*           | State of the service
                              |                    | default: started
| **enabled**                 | *boolean*          | Start on boot
                              |                    | default: true
============================= ==================== ============================

Example
^^^^^^^
FreeBSD services for Postfix and Sendmail

[`contrib/postfix/conf-light/service.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/postfixd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/postfix
    :language: yaml
    :emphasize-lines: 2
    :linenos:

[`contrib/postfix/conf-light/service.d/sendmail <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/sendmail>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/sendmail
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-services.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-services.yml>`_ how the variable *cl_services* is combined with the content of the directory *cl_servicesd_dir*.

   * See `services.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/services.yml>`_ how the services are configured.


.. _ug_files:

cl_files - dictionary with files
--------------------------------
.. contents::
   :local:

Synopsis
""""""""

The variable *cl_files* is a dictionary of the files that shall be
created or modified by this role. It's optional which Ansible module
will be used to create or modify a file. More options can be applied
at the same file. For example, it is possible to create a file by the
Ansible module *template* and modify it with the module *lineinfile*
later. Several options are available:

1. template: If the attribute *template* is defined in the dictionary
2. lineinfile: If the attribute *dict* or *lines* is defined in the dictionary
3. blockinfile: If the attribute *blocks* is defined in the dictionary
4. ini_file: If the attribute *ini* is defined in the dictionary

Multiple options, when defined in the dictionary, will be applied in
this order.

See Also
""""""""
.. seealso::

   * See `vars-files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ how the variable *cl_files* is combined with the content of the directory *cl_filesd_dir*.

   * See `files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ how the files are created and modified.

   * See `files-create-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-create-backup.yml>`_ how the backups are created (when enabled by *cl_backup*).

   * See `files-delete-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-delete-backup.yml>`_ how the backup files are deleted when the files haven't been modified.

blockinfile markers
^^^^^^^^^^^^^^^^^^^

<TODO: No description yet>

template
^^^^^^^^

Parameters for template
"""""""""""""""""""""""
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **template**                | *string*           | Template filename
                              | ``required``       |
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
| **force**                   | *boolean*          | Replace when different
                              |                    | default: true
| **validate**                | *string*           | Command to validate file
                              |                    |
| **handlers**                | *list*             | List of handlers
                              |                    |
============================= ==================== ============================

Example of template
"""""""""""""""""""

File ``/etc/mail/mailer.conf`` for postfix

[`contrib/postfix/conf-light/files.d/mailer-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/mailer-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/mailer-conf
    :language: yaml
    :emphasize-lines: 7
    :linenos:

See Also
""""""""
.. seealso::

   * See `files-template.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-template.yml>`_ how the files are modified or created by the Ansible module ``template``.
	     
Notes
"""""
.. note:: There are couple of templates ready to be used in the directory ``templates``. The user is expected to create new templates when needed. Feel free to contribute new templates to the `project <https://github.com/vbotka/ansible-config-light/>`_.

lineinfile
^^^^^^^^^^

Parameters for lineinfile
"""""""""""""""""""""""""
=================== ==================== ======================================
| *Parameter*       | *Type*             | *Comments*
=================== ==================== ======================================
| **path**          | *string*           | Path to file
                    | ``required``       |
| **dict**          | *list*             | List of key value dictionaries
                    | ``required``       | Either dict or lines is required
| **lines**         | *list*             | List of regexp and lines
                    | ``required``       | Either dict or lines is required
| **assignment**    | *string*           | Assignment of key and value in dict
                    |                    | default '='
| **owner**         | *string*           | Owner of the file
                    |                    |
| **group**         | *string*           | Group of the file
                    |                    |
| **mode**          | *string*           | Mode of the file
                    |                    |
| **create**        | *boolean*          | Create if does not exist
                    |                    | default: false
| **validate**      | *string*           | Command to validate file
                    |                    |
| **handlers**      | *list*             | List of handlers
                    |                    |
=================== ==================== ======================================

Example of lineinfile with lines
""""""""""""""""""""""""""""""""

File ``/usr/local/etc/lighttpd/lighttpd.conf`` for lighttpd

[`contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines
    :language: yaml
    :emphasize-lines: 9
    :linenos:

Example of lineinfile with dict
"""""""""""""""""""""""""""""""

File ``/usr/local/etc/lighttpd/lighttpd.conf`` for lighttpd

[`contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict
    :language: yaml
    :emphasize-lines: 10
    :linenos:

See Also
""""""""
.. seealso::

   * See `files-lineinfile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-lineinfile.yml>`_ how the files are modified or created by the Ansible module ``lineinfile``.

blockinfile
^^^^^^^^^^^

Parameters for blockinfile
""""""""""""""""""""""""""
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **blocks**                  | *list*             | List of blocks and markers
                              | ``required``       |
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
| **create**                  | *boolean*          | Create if does not exist
                              |                    | default: false
| **validate**                | *string*           | Command to validate file
                              |                    |
| **handlers**                | *list*             | List of handlers
                              |                    |
============================= ==================== ============================

Example of blockinfileinfile
""""""""""""""""""""""""""""

<TODO: No example yet>

See Also
""""""""
.. seealso::

   * See `files-blockinfile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-blockinfile.yml>`_ how the files are modified or created by the Ansible module ``blockinfile``.

ini_file
^^^^^^^^

Parameters for ini_file
"""""""""""""""""""""""
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **ini**                     | *list*             | List of {section,option,
                              | ``required``       | value} dictionaries
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
| **create**                  | *boolean*          | Create if does not exist
                              |                    | default: true
| **handlers**                | *list*             | List of handlers
                              |                    |
============================= ==================== ============================

Example of ini_file
"""""""""""""""""""

<TODO: No example yet>

See Also
""""""""
.. seealso::

   * See `files-inifile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-inifile.yml>`_ how the files are modified or created by the Ansible module ``ini_file``.


.. _ug_bp:

Best practice
=============


Create variables. Take a look at directory ``conf-light/assemble/``
what files were created. ::

    shell> ansible-playbook config-light.yml -t cl_vars

Test sanity. Then disable this task ``cl_sanity: false`` to speedup
the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_sanity

Create handlers. Take a look at directory
``roles/vbotka.config_light/handlers`` what handlers were created. Run
this task once to create the handlers. Then disable this task
``cl_setup: false`` to speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_setup

Display variables. Display the variables for debug if needed. Then
disable this task ``cl_debug: false`` to speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_debug

Install packages. Then disable this task ``cl_install: false`` to
speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_packages

Set files' states. ::

    shell> ansible-playbook config-light.yml -t cl_states

Create and modify files ::

    shell> ansible-playbook config-light.yml -t cl_files

Configure services ::

    shell> ansible-playbook config-light.yml -t cl_services

The role and the configuration data in the examples are
idempotent. Once the application is installed and configured there
should be no changes reported by *ansible-playbook* when running the
playbook repeatedly. Disable setup, sanity, debug, and install to
speedup the playbook ::

    shell> ansible-playbook config-light.yml
