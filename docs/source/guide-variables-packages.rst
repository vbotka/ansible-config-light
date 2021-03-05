.. _ug_variables_packages:

Packages
--------
.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_packages* comprises packages (Linux or BSD) or BSD ports.

FreeBSD
"""""""

By default packages will be installed. If you want to install ports set ::

  freebsd_install_method: ports

snap
""""

By default snap packages won't be installed or deinstalled if *snap* binary can't be found in
``cl_snap_paths``. If you want the role to fail when *snap* packages are configured in *cl_packages* set
::

  cl_snap_missing_fatal: true

The variables *cl_snap_missing_fatal, cl_snap_paths, cl_snap_patterns* are declared in
``defaults/main.yml``.

Parameters
^^^^^^^^^^

+---------------------+-----------------------+---------------------------------------+
| Parameter           | Type                  | Comments                              |
+=====================+=======================+=======================================+
| name                | list ``required``     | List of packages or BSD ports         |
+---------------------+-----------------------+---------------------------------------+
| module              | string                | Ansible module to manage Linux        |
|                     |                       | packages (default=package)            |
|                     |                       | choices: package, yum, apt, snap      |
+---------------------+-----------------------+---------------------------------------+
| state               | string                | State of packages or BSD ports        |
|                     |                       | (default=present)                     |
+---------------------+-----------------------+---------------------------------------+
| ...                 | ...                   | <TBD: see tasks/packages.yml>         |
+---------------------+-----------------------+---------------------------------------+


Examples
^^^^^^^^

* FreeBSD install Postfix package or port

[`contrib/postfix/conf-light/packages.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix
    :language: yaml
    :emphasize-lines: 2
    :linenos:

* Armbian package for Simple SMTP

[`contrib/ssmtp/conf-light/packages.d/ssmtp <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp
    :language: yaml
    :emphasize-lines: 2
    :linenos:

* Ubuntu delete snap packages

[`contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall
    :language: yaml
    :emphasize-lines: 2
    :linenos:


* Ubuntu purge snapd package

[`contrib/ubuntu-snap-disable/conf-light/packages.d/snapd <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ubuntu-snap-disable/conf-light/packages.d/snapd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ubuntu-snap-disable/conf-light/packages.d/snapd
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-packages.yml>`_ at GitHub how the variable *cl_packages* is combined with the content of the directory *cl_packagesd_dir*

   * See `packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/packages.yml>`_ at GitHub how the packages or BSD ports are installed

     **Anotated source code**
     
   * :ref:`as_vars-packages.yml`

   * :ref:`as_packages.yml`
