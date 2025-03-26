.. _ug_introduction:

Introduction
************

* Ansible role: `config_light <https://galaxy.ansible.com/vbotka/config_light/>`_
* Supported systems: `FreeBSD <https://www.freebsd.org/releases/>`_, `Ubuntu <http://releases.ubuntu.com/>`_
* Requirements: `ansible.posix <https://github.com/ansible-collections/ansible.posix/>`_ , `community.general <https://github.com/ansible-collections/community.general>`_

The role installs packages, creates and configures files and
services. The handlers are created from user provided data. The
control-flow will be determined by the user provided configuration
data. Some attributes of the dictionaries determine which Ansible
module will be used. This `data-driven programming
<https://en.wikipedia.org/wiki/Data-driven_programming>`_ paradigm
provides a flexible and robust framework to apply basic Ansible
modules. In the code, each Ansible module is used only
once. This makes the implementation, upgrading, and testing of the
modules simple and easy.

The user of this role is expected to master at least the following
Ansible topics:

* `Basic Concepts <https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html>`_
* `Roles <https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html>`_
* `Working With Playbooks <https://docs.ansible.com/ansible/latest/user_guide/playbooks.html>`_

The supported OS (FreeBSD and Ubuntu) can use the role to install and
configure arbitrary applications. Other Linux distributions, that
support the used Ansible modules, should work with minimal
changes. BSD*, Debian, and Red Hat *ansible_os_family* should work out
of the box.

There are four imported tasks in the first part of the role to setup
handlers, assemble, and check the configuration data: ::

  tasks     description                  tags               enabled (default)
  ___________________________________________________________________________
  setup     create handlers              cl_setup, always   cl_setup=true
  vars      assemble configuration data  cl_vars, always    always
  sanity    check sanity                 cl_sanity, always  cl_sanity=true
  debug     help debugging data          cl_debug           cl_debug=false


Then, there are four imported tasks to manage the infrastructure: ::

  tasks     description                  tags               enabled (default)
  ___________________________________________________________________________
  packages  install packages             cl_packages        cl_install=true
  states    modify states of files       cl_states          always
  files     configure files              cl_files           always
  services  configure services           cl_services        always


* packages: The Ansible modules ``package``, ``apt``, ``dnf``, and
  ``snap`` are used to install Linux packages. In FreeBSD, modules
  ``pkgng`` and ``portinstall`` are used to install FreeBSD packages
  and ports.

* states: The Ansible module ``mount`` is used to mount and unmount paths,
  and to configure *fstab*. The module ``file`` is used to modify
  `states <https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html#parameter-state>`_ of files.

* files: The Ansible modules ``template``, ``copy``, ``replace``,
  ``patch``, ``lineinfile``, ``blockinfile``, and ``ini_file`` are
  used to configure files.

* services: The Ansible Module ``service`` is used to configure both Linux and
  BSD services.

.. note::

   For backward compatibility use ``yum`` instead of ``dnf`` in the
   configuration. For example ::

     shell: cat conf-light/packages.d/lighttpd.yml
     lighttpd:
       module: yum
       name:
         - lighttpd

   The module *ansible.builtin.dnf* will be used. See :ref:`as_packages.yml`

.. seealso::

   The directory `contrib
   <https://github.com/vbotka/ansible-config-light/blob/master/contrib/>`_
   comprises examples on how to install and configure various
   applications and how to create handlers and templates. Some of them
   are commented :ref:`ex`.


.. hint::

   Feel free to `share your feedback and report issues <https://github.com/vbotka/ansible-config-light/issues>`_. The contributions to the `project <https://github.com/vbotka/ansible-config-light/>`_ are welcome.
