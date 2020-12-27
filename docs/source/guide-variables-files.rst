Files
-----
.. contents::
   :local:

Synopsis
""""""""

The variable *cl_files* is a dictionary of the files that shall be
created or modified by this role. It's optional which Ansible module
will be used to create or modify a file. More options can be applied
at the same file. For example, it is possible to create a file by the
Ansible module *template* and modify it with the module *lineinfile*
later. Several options are available:

1) copy: If the attribute *copyfile* is defined in the dictionary

2) template: If the attribute *template* is defined in the dictionary

3) create blockinfile markers: If the attribute *markers* is defined in the dictionary

4) lineinfile: If the attribute *dict* or *lines* is defined in the dictionary

5) blockinfile: If the attribute *blocks* is defined in the dictionary

6) ini_file: If the attribute *ini* is defined in the dictionary

Multiple options, when defined in the dictionary, will be applied in this order.

See Also
""""""""
.. seealso::

   * See `vars-files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ how the variable *cl_files* is combined with the content of the directory *cl_filesd_dir*.

   * See `files.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files.yml>`_ how the files are created and modified.

   * See `files-create-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-create-backup.yml>`_ how the backups are created (when enabled by *cl_backup*).

   * See `files-delete-backup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-delete-backup.yml>`_ how the backup files are deleted when the files haven't been modified.
