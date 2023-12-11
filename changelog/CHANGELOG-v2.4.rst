=====================================
vbotka.config_light 2.4 Release Notes
=====================================

.. contents:: Topics


2.4.3
=====

Release Summary
---------------
Update setup, sanity, and packages. Add changelog. Add
docs/requirements.txt.

Major Changes
-------------
* Update sanity checks.
* Update setup. Optionally delete already assembled data default=false.
* Update packages.
* Update debug.

Minor Changes
-------------
* Add changelog.
* Add docs/requirements.txt
* Update subelements loops.

Bugfixes
--------
* Fix setup debug output.

Breaking Changes / Porting Guide
--------------------------------
* In FreeBSD packages module=pkgng is mandatory both for packages and
  ports.
* Variable cl_handlers_clean_all renamed cl_handlers_delete_all
