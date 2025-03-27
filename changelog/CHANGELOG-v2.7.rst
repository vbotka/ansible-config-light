=====================================
vbotka.config_light 2.7 Release Notes
=====================================

.. contents:: Topics


2.7.0
=====

Release Summary
---------------
Major release.

Major Changes
-------------
* Update meta
  Supported Ansible 2.18
  Freebsd 13.4, 13.5, 14.1, 14.2
  Ubuntu +oracular
  collections +vbotka.freebsd

Minor Changes
-------------
* Improved formatting.
* Update docs TOC.
* Update tasks/packages.yml
  Add variables: freebsd_pkgng_delegate, freebsd_pkgng_use_globs (no defaults)
  Add option use_globs
  Add directive delegate_to (freebsd_pkgng_delegate | d(omit))

Bugfixes
--------

Breaking Changes / Porting Guide
--------------------------------
