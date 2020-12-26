Best practice
=============


Create variables. Take a look at directory ``conf-light/assemble/``
what files were created. ::

    shell> ansible-playbook config-light.yml -t cl_vars

Test sanity. Then disable this task ``cl_sanity: false`` to speedup
the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_sanity

Create handlers. Take a look at directory
``roles/vbotka.config_light/handlers`` what handlers were created. Run
this task once to create the handlers. Then disable this task
``cl_setup: false`` to speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_setup

Display variables. Display the variables for debug if needed. Then
disable this task ``cl_debug: false`` to speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_debug

Install packages. Then disable this task ``cl_install: false`` to
speedup the playbook. ::

    shell> ansible-playbook config-light.yml -t cl_packages

Set files' states. ::

    shell> ansible-playbook config-light.yml -t cl_states

Create and modify files ::

    shell> ansible-playbook config-light.yml -t cl_files

Configure services ::

    shell> ansible-playbook config-light.yml -t cl_services

The role and the configuration data in the examples are
idempotent. Once the application is installed and configured there
should be no changes reported by *ansible-playbook* when running the
playbook repeatedly. Disable setup, sanity, debug, and install to
speedup the playbook ::

    shell> ansible-playbook config-light.yml
