=====================================
vbotka.config_light 2.7 Release Notes
=====================================

.. contents:: Topics


2.7.4
=====

Release Summary
---------------
Update README.


2.7.3
=====

Release Summary
---------------
Updated documentation. Updated annotation templates.


2.7.2
=====

Release Summary
---------------
Updated documentation. Updated annotation templates.


2.7.1
=====

Release Summary
---------------
Update docs.

Major Changes
-------------

Minor Changes
-------------
* Update docs.
  Update Quick start guide.

2.7.0
=====

Release Summary
---------------
Major release. Use collection vbotka.freebsd

Major Changes
-------------
* Update meta
  Supported Ansible 2.18
  Freebsd 13.4, 13.5, 14.1, 14.2
  Ubuntu +oracular
* Require collection vbotka.freebsd
* Update tasks/main.yml
  Remove block.
  Execute setup and sanity conditionally.
  Execute vars always.
* Update tasks/services.yml for FreeBSD
  Use community.general.sysrc
  Use vbotka.freebsd.service
  Remove variable cl_services_freebsd_rcconf_auto
* Enable configuration in rc.conf.d for FreeBSD
  Add variable cl_rcconfd (default=false)
  Add variable cl_rcconfd_dir (default=/etc/rc.conf.d)
  Add dictionaries: cl_rcconfd_path, cl_rcconf_rcvar

Minor Changes
-------------
* Improved formatting.
* Update docs TOC. Update Users Guide. Add UCL, rc.conf.d, ansd vbotka.freebsd.*
* Update tasks/packages.yml
  Add variables: freebsd_pkgng_delegate, freebsd_pkgng_use_globs (no defaults)
  Add option use_globs
  Add directive delegate_to (freebsd_pkgng_delegate | d(omit))

Bugfixes
--------

Breaking Changes / Porting Guide
--------------------------------
