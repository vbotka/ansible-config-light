=====================================
vbotka.config_light 2.6 Release Notes
=====================================

.. contents:: Topics


2.6.7
=====

Release Summary
---------------
Maintenance update.

Major Changes
-------------

Minor Changes
-------------
* Update docs.


2.6.6
=====

Release Summary
---------------
Maintenance update.

Major Changes
-------------

Minor Changes
-------------
* Exclude dynamically created hanlers from ansible-lint.


2.6.5
=====

Release Summary
---------------
Update docs.

Major Changes
-------------

Minor Changes
-------------
- Update docs.


2.6.4
=====

Release Summary
---------------
Maintenance release with updated docs.

Major Changes
-------------

Minor Changes
-------------
- Update python 3.11 in .travis.yml
- Update docs:
  - Add parameter listen to handlers cl_handlers

Bugfixes
--------


2.6.3
=====

Release Summary
---------------
Maintenance and bugfix release with updated docs.

Major Changes
-------------

Minor Changes
-------------
* Bump role and docs version.
* Add var cl_role_version
* Update tasks/debug.yml
* Update tests/test.yml playbook
* Update setup.yml
* Update formatting templates/handlers-auto2.yml.j2
* Add templates/handlers-auto3.yml.j2; include param 'listen'
* Update docs:
  - Add templates/handlers-auto2.yml.j2
  - For backward compatibility use yum instead of dnf in configuration.

Bugfixes
--------
* Handlers setup. Use search_string instead of line in lineinfile.


2.6.2
=====

Release Summary
---------------
Ansible 2.17 upgrade. Maintenance and bugfix release with updated docs.

Major Changes
-------------
* Add supported FreeBSD 13.3 and 14.1
* Add supported Ubuntu 24.04 Nobel

Minor Changes
-------------
* Bump docs version.
* Remove obsolete comment from docs/source/conf.py
* Update lint config
* Update README

Bugfixes
--------
* Fix my_packages_undef flatten


2.6.1
=====

Release Summary
---------------
Update docs requirements readthedocs-sphinx-search==0.3.2

Major Changes
-------------

Minor Changes
-------------
* Update README

Bugfixes
--------

Breaking Changes / Porting Guide
--------------------------------


2.6.0
=====

Release Summary
---------------
Update Ansible 2.16
