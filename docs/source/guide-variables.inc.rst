.. _ug_variables:

Variables
*********

The :ref:`ug_variables_defaults` control the options of the role.

The most important are the variables that control the collection of
the configuration data. In each project, customize the files with the
configuration data stored in the directory ``cl_dird``

.. seealso::

   * See :ref:`as_vars.yml` annotated source code
   * `Ansible variable precedence: Where should I put a variable? <https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable>`_

.. note::

   The names of the dictionaries in the configuration files
   ``cl_dird/*.d/*`` are not used by the role and can be any arbitrary
   strings that are valid names of Ansible variables. The names must
   be unique in the particular section (files.d, packages.d, ...).
