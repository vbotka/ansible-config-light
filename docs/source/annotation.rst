.. _as:

Annotated source code
*********************
.. contents:: Table of Contents
   :depth: 3

.. _as_tree:

Tasks
=====

.. _as_main_yml:

main.yml
--------

Synopsis: Tasks of the playbook.


Description of the task.


[`main.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/main.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/main.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_yml:

vars.yml
--------

Synopsis: Combine dictionaries of packages, services and files.


Description of the task.


[`vars.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_packages_yml:

vars-packages.yml
-----------------

Synopsis: Combine dictionaries of packages.


Description of the task.


[`vars-packages.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-packages.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars-packages.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_states_yml:

vars-states.yml
---------------

Synopsis: Combine dictionaries of files' states.


Description of the task.


[`vars-states.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-states.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars-states.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_services_yml:

vars-services.yml
-----------------

Synopsis: Combine dictionaries of services.


Description of the task.


[`vars-services.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-services.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars-services.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_files_yml:

vars-files.yml
--------------

Synopsis: Combine dictionaries of files.


Description of the task.


[`vars-files.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-files.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars-files.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_sanity_yml:

sanity.yml
----------

Synopsis: Test sanity.


Description of the task.


[`sanity.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/sanity.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/sanity.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_setup_yml:

setup.yml
---------

Synopsis: Setup. Create dirs. Create handlers.


Description of the task.


[`setup.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/setup.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/setup.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_vars_handlers_yml:

vars-handlers.yml
-----------------

Synopsis: Combine dictionaries of handlers.


Description of the task.


[`vars-handlers.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-handlers.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/vars-handlers.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_debug_yml:

debug.yml
---------

Synopsis: Display variables.


Description of the task.


[`debug.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/debug.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/debug.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_packages_yml:

packages.yml
------------

Synopsis: Install packages.


Description of the task.


[`packages.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/packages.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/packages.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_states_yml:

states.yml
----------

Synopsis: Configure states of files.


Description of the task.


[`states.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/states.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/states.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_yml:

files.yml
---------

Synopsis: Create or modify files.


Description of the task.


[`files.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_create_backup_yml:

files-create-backup.yml
-----------------------

Synopsis: Create backup files.


Description of the task.


[`files-create-backup.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-create-backup.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-create-backup.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_delete_backup_yml:

files-delete-backup.yml
-----------------------

Synopsis: Delete backup files if the files haven’t been modified.


Description of the task.


[`files-delete-backup.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-delete-backup.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-delete-backup.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_template_yml:

files-template.yml
------------------

Synopsis: Create or modify files by Ansible module ``template``.


Description of the task.


[`files-template.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-template.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-template.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_lineinfile_yml:

files-lineinfile.yml
--------------------

Synopsis: Create or modify files by Ansible module ``lineinfile``.


Description of the task.


[`files-lineinfile.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-lineinfile.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-lineinfile.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_blockinfile_yml:

files-blockinfile.yml
---------------------

Synopsis: Create or modify files by Ansible module ``blockinfile``.


Description of the task.


[`files-blockinfile.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-blockinfile.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-blockinfile.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_files_inifile_yml:

files-inifile.yml
-----------------

Synopsis: Create or modify files by Ansible module ``ini_infile``.


Description of the task.


[`files-inifile.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-inifile.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/files-inifile.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

.. _as_services_yml:

services.yml
------------

Synopsis: Configure services.


Description of the task.


[`services.yml <https://github.com/vbotka/ansible-config-light/blob/master/tasks/services.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../tasks/services.yml
    :language: Yaml
    :emphasize-lines: 1,2
    :linenos:

