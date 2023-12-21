.. _ug_variables_packages:

Packages
========

.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_packages* comprises managed packages (Linux or BSD) or BSD ports.

FreeBSD
"""""""

By default packages will be installed. If you want to install ports set ::

  freebsd_install_method: ports

snap
""""

By default snap packages won't be installed or uninstalled if *snap* binary can't be found in
``cl_snap_paths``. If you want the role to fail when *snap* is missing set ::

  cl_snap_missing_fatal: true

The variables *cl_snap_missing_fatal, cl_snap_paths, cl_snap_patterns* are declared in
``defaults/main.yml``.

Parameters
^^^^^^^^^^

.. list-table::
   :widths: 20 20 50
   :header-rows: 1

   * - Parameter
     - Type
     - Comments
   * - name
     - list ``required``
     - List of packages or BSD ports
   * - module
     - string
     - | Ansible module to manage packages.
       | choices: package, apt, yum, snap, pkgng
       | (default=package)
   * - state
     - string
     - | State of packages or BSD ports
       | (default=present)
   * - .
     - .
     - <TBD: see tasks/packages.yml>

Examples
^^^^^^^^

FreeBSD install Postfix package or port
"""""""""""""""""""""""""""""""""""""""

[`contrib/postfix/conf-light/packages.d/postfix.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:

Armbian package for Simple SMTP
"""""""""""""""""""""""""""""""

[`contrib/ssmtp/conf-light/packages.d/ssmtp.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:

Ubuntu delete snap packages
"""""""""""""""""""""""""""

[`contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ubuntu-snap-disable/conf-light/packages.d/snap-deinstall.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:


Ubuntu purge snapd package
""""""""""""""""""""""""""

[`contrib/ubuntu-snap-disable/conf-light/packages.d/snapd.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ubuntu-snap-disable/conf-light/packages.d/snapd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ubuntu-snap-disable/conf-light/packages.d/snapd.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:

.. seealso::

   * :ref:`as_vars-packages.yml`
   * :ref:`as_packages.yml`
