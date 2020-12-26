ini_file
^^^^^^^^

Parameters for ini_file
"""""""""""""""""""""""
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **ini**                     | *list*             | List of {section,option,
                              | ``required``       | value} dictionaries
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
| **create**                  | *boolean*          | Create if does not exist
                              |                    | default: true
| **handlers**                | *list*             | List of handlers
                              |                    |
============================= ==================== ============================

Example of ini_file
"""""""""""""""""""

<TODO: No example yet>

See Also
""""""""
.. seealso::

   * See `files-inifile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-inifile.yml>`_ how the files are modified or created by the Ansible module ``ini_file``.
