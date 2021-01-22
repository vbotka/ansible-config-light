*********
Variables
*********

The :ref:`ug_variables_defaults` control the options of the role. Most important are the
variables that control the collection of the configuration data. For example, in each project,
customize the directory ``cl_dird`` where the files with the configuration data are stored.

See the particular sections below on how to configure the creation of handlers, installation of the
packages or ports, and management of files and services. Most options are available in the section
:ref:`ug_variables_files`. See the particular subsections on how to create the configuration data
for the Ansible modules that serve the options. Review hints in the :ref:`ex`.

.. seealso::
   * See `vars.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/main.yml>`_ at GitHub
   * See :ref:`as_vars.yml` annotated source code
   * `Ansible variable precedence: Where should I put a variable? <https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable>`_

.. note:: The names of the dictionaries in the configuration files ``cl_dird/*.d/*`` are not used by
          the role and can be any arbitrary string that is a valid name of an Ansible variable. The
          name must be unique in the particular option (directory files.d, packages.d, ...).
