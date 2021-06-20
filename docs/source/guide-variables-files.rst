.. _ug_variables_files:

Files
-----

.. contents::
   :local:


Synopsis
^^^^^^^^

The variable *cl_files* is a dictionary of the files that shall be managed by this role. It's
optional which Ansible module will be used to manage a file. More options can be applied at the same
file. For example, it is possible to create a file by the Ansible module *template* and modify it by
the module *lineinfile* later. Several options, listed in the default order, are available

#. copy: If the attribute *copyfile* is defined in the dictionary
#. template: If the attribute *template* is defined in the dictionary
#. create blockinfile markers: If the attribute *markers* is defined in the dictionary
#. patch: If the attribute *patch* is defined in the dictionary
#. lineinfile: If the attribute *dict* or *lines* is defined in the dictionary
#. blockinfile: If the attribute *blocks* is defined in the dictionary
#. ini_file: If the attribute *ini* is defined in the dictionary


Order of the options
^^^^^^^^^^^^^^^^^^^^

The variable ``cl_files_order`` controls the order of the execution. Multiple options, when present
in the dictionary of a file definition, will be applied in this order. In addition to the options,
listed above, there are ``create-backup`` and ``delete-backup`` tasks to backup files that was
changed if enabled by ``cl_backup`` (default: false). By default, the backup files are created after
*copy, template, and markers*. Fit the order of the execution to your needs.


See Also
^^^^^^^^

.. seealso::

   * See `vars-files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ at GitHub how the variable *cl_files* is combined with the content of the directory *cl_filesd_dir*

   * See `files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ at GitHub how the files are created and modified

   * See `files-create-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-create-backup.yml>`_ at GitHub how the backups are created (when enabled by *cl_backup*)

   * See `files-delete-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-delete-backup.yml>`_ at GitHub how the backup files are deleted when the files haven't been modified

     **Annotated source code**
     
   * :ref:`as_vars-files.yml`

   * :ref:`as_files.yml`

   * :ref:`as_files-create-backup.yml`

   * :ref:`as_files-delete-backup.yml`

Options
^^^^^^^

.. toctree::

   guide-variables-files-copy
   guide-variables-files-template
   guide-variables-files-markers
   guide-variables-files-patch
   guide-variables-files-lineinfile
   guide-variables-files-blockinfile
   guide-variables-files-inifile
