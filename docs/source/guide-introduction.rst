************
Introduction
************

* Ansible role: `config_light <https://galaxy.ansible.com/vbotka/config_light/>`_
* Supported systems: `FreeBSD <https://www.freebsd.org/releases/>`_, `Ubuntu <http://releases.ubuntu.com/>`_
* Requirements: `ansible.posix <https://github.com/ansible-collections/ansible.posix/>`_ , `community.general <https://github.com/ansible-collections/community.general>`_

The role installs packages, creates and configures files, services, and handlers. This provides a
simple, but flexible framework to apply basic Ansible modules. A substantial part of the
control-flow will be determined by the structure of the data. Some attributes of the dictionaries
trigger Ansible modules to modify configuration files, configure services and create handlers.

The role can be used with any supported OS to install and configure arbitrary applications. The role
is tested with supported releases of FreeBSD and Ubuntu. It can be expected that other BSD and Linux
distributions, that support the Ansible modules mentioned below, should work with minimal
changes. Red Hat and Debian *ansible_os_family* should work out of the box.

Ansible modules ``package``, ``apt``, ``yum``, and ``snap`` are used to install Linux packages. In
FreeBSD, modules ``pkgng`` and ``portinstall`` are used to install FreeBSD packages and ports.

Ansible modules ``file``, ``template``, ``copy``, ``replace``, ``patch``, ``lineinfile``,
``blockinfile``, and ``ini_file`` are used to configure files. The module ``mount`` is used to mount
and unmount paths, and to configure *fstab*. Module ``service`` is used to manage both Linux and
FreeBSD services.

The directory `contrib <https://github.com/vbotka/ansible-config-light/blob/master/contrib/>`_
comprises examples on how to install and configure various applications and how to create the
handlers and templates. Some of them are commented :ref:`ex`.

The user of this role is expected to master at least the following Ansible topics

* `Basic Concepts <https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html>`_
* `Roles <https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html>`_
* `Working With Playbooks <https://docs.ansible.com/ansible/latest/user_guide/playbooks.html>`_

Feel free to `share your feedback and report issues
<https://github.com/vbotka/ansible-config-light/issues>`_. The contributions to the `project
<https://github.com/vbotka/ansible-config-light/>`_ are welcome.
