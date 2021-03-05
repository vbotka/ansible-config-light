*************
Best practice
*************


Check syntax of setup
=====================

Check syntax of setup and display variables ::

    shell> ansible-playbook pb.yml -t cl_setup -e cl_debug=true --check

If you want to see the values of the variables enable debug output ``cl_debug=true``.

Setup
=====

Collect variables, create handlers, check sanity, and display variables. When you take a look at
``tasks/main.yml`` you'll see that the first four groups of the tasks (setup, vars, sanity, and
debug) are tagged ``always``. As a result, when you apply any of the four tags (cl_setup, cl_vars,
cl_sanity, and cl_debug) all four groups of the tasks, and only these four groups of the tasks, will
be executed. All four commands below are equivalent to the command ::

    shell> ansible-playbook pb.yml -t cl_setup,cl_vars,cl_sanity,cl_debug

* Create variables. Take a look at directory ``conf-light/assemble/`` what files were created ::

    shell> ansible-playbook pb.yml -t cl_vars

* Test sanity. Then disable this task ``cl_sanity: false`` to speedup the playbook ::

    shell> ansible-playbook pb.yml -t cl_sanity

* Create handlers. Take a look at directory ``roles/vbotka.config_light/handlers`` what handlers
  were created. Run this task once to create the handlers. Then disable this task ``cl_setup:
  false`` to speedup the playbook ::

    shell> ansible-playbook pb.yml -t cl_setup

* Display variables. Then disable this task ``cl_debug: false`` to speedup the playbook ::

    shell> ansible-playbook pb.yml -t cl_debug


Check syntax
============

Check syntax of the complete playbook ::

    shell> ansible-playbook pb.yml --check


Manage packages
===============

Dry-run the management of packages ::

    shell> ansible-playbook pb.yml -t cl_packages -e cl_install=true -CD

Manage packages. Then disable this task ``cl_install=false`` to speedup the playbook ::

    shell> ansible-playbook pb.yml -t cl_packages -e cl_install=true


Manage states of files
======================

Dry-run the management of files' states ::

    shell> ansible-playbook pb.yml -t cl_states -CD

Set the states (existence and attributes) of the files ::

    shell> ansible-playbook pb.yml -t cl_states


Manage configuration files
==========================

Dry-run the configuration of files ::

    shell> ansible-playbook pb.yml -t cl_files -CD

Create and modify files ::

    shell> ansible-playbook pb.yml -t cl_files


Manage services
===============

Dry-run the configuration of services ::

    shell> ansible-playbook pb.yml -t cl_services -CD

Configure services ::

    shell> ansible-playbook pb.yml -t cl_services


Idempotence
===========

The role and the configuration data in the examples are idempotent. When the application is
installed and configured there should be no changes reported by *ansible-playbook* when running the
playbook repeatedly. Disable setup, sanity, debug, and install to speedup the execution when running
the playbook periodicaly to audit the configuration ::

    shell> ansible-playbook pb.yml -e cl_setup=false \
                                   -e cl_sanity=false \
                                   -e cl_debug=false \
                                   -e cl_install=false
