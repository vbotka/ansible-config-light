.. _ug_bp:

Best practice
*************


Check syntax
============

Check syntax of the playbook ::

    shell> ansible-playbook pb.yml --syntax-check


Validation
==========

Install ``yamllint`` to use the default validation of the created
handlers and assembled data. See the variables *cl_assemble_validate*
and *cl_handlers_validate* in *defaults/main.yml*. Optionally, use
other linter, for example, *ansible-lint* and change the
variables. You can disable the validation by clearing the variables ::

    cl_assemble_validate: ''
    cl_handlers_validate: ''


Setup
=====

Assemble data, create handlers, check sanity, and display
variables. When you take a look at ``tasks/main.yml`` you'll see that
the first three groups of the tasks (setup, vars, and sanity) are
tagged ``always``. As a result, when you apply the tag *cl_debug* all
three groups of the tasks will be executed before *cl_debug* ::

    shell> ansible-playbook pb.yml -t cl_debug -e cl_setup=true -e cl_sanity=true -e cl_debug=true


Manage packages
===============

Dry-run the management of packages ::

    shell> ansible-playbook pb.yml -t cl_packages -e cl_install=true -CD

Manage packages ::

    shell> ansible-playbook pb.yml -t cl_packages -e cl_install=true

Then disable the installation ``cl_install=false`` to speedup the playbook.


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

.. hint::

   If you know what you are doing skip the above selection of
   particular tags and run the complete role at once ::

    shell> ansible-playbook pb.yml -e cl_setup=true -e cl_install=true


Idempotency
===========

The role and the configuration data in the examples are idempotent. When the application is
installed and configured there should be no changes reported by *ansible-playbook* when running the
playbook repeatedly. Disable setup, sanity, debug, and install to speedup the execution when running
the playbook periodically to audit the configuration ::

    shell> ansible-playbook pb.yml -e cl_setup=false \
                                   -e cl_sanity=false \
                                   -e cl_debug=false \
                                   -e cl_install=false
