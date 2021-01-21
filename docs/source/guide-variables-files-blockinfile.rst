blockinfile
^^^^^^^^^^^

Create or configure blocks in files.

Parameters for blockinfile
""""""""""""""""""""""""""
+---------------------+-----------------------+-----------------------------+
| Parameter           | Type                  | Comments                    |
+=====================+=======================+=============================+
| path                | string ``required``   | Path to file                |
+---------------------+-----------------------+-----------------------------+
| blocks              | list ``required``     | List of dictionaries        |
|                     |                       | (see files-blockinfile.yml) |
+--+------------------+-----------------------+-----------------------------+
|  | marker           | string ``required``   | Label of the marker         |
|  +------------------+-----------------------+-----------------------------+
|  | block            | string ``required``   | Text between markers        |
|  +------------------+-----------------------+-----------------------------+
|  | ...              | ...                   | <TBD>                       |
+--+------------------+-----------------------+-----------------------------+
| owner               | string                | Owner of the file           |
+---------------------+-----------------------+-----------------------------+
| group               | string                | Group of the file           |
+---------------------+-----------------------+-----------------------------+
| mode                | string                | Mode of the file            |
+---------------------+-----------------------+-----------------------------+
| create              | boolean               | Create if does not exist    |
+---------------------+-----------------------+-----------------------------+
| validate            | string                | Command to validate file    |
+---------------------+-----------------------+-----------------------------+
| handlers            | list                  | List of handlers            |
+---------------------+-----------------------+-----------------------------+

Example of blockinfileinfile
""""""""""""""""""""""""""""

Create the description of the file (2) and declare the list of the blocks (10)

[`contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf
    :language: yaml
    :emphasize-lines: 2,10
    :linenos:

Create the list of the blocks ``cl_lighttpd_modulesconf_blocks`` (89)

[`contrib/lighttpd_nagios/cl-lighttpd.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd_nagios/cl-lighttpd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd_nagios/cl-lighttpd.yml
    :language: yaml
    :lines: 84-97
    :lineno-start: 84
    :emphasize-lines: 1,6
    :linenos:

Then, the command ::

  shell> ansible-playbook config-light.yml -t cl_files_blockinfile

will create this block in ``modules.conf`` ::

  ##

  # BEGIN ANSIBLE MANAGED BLOCK server.modules
  server.modules = (
    "mod_access",
    "mod_alias",
    "mod_auth",
    "mod_setenv",
  )
  # END ANSIBLE MANAGED BLOCK server.modules

  ##


See Also
""""""""
.. seealso::

   * See `files-blockinfile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-blockinfile.yml>`_ at GitHub how the files are modified by the Ansible module ``blockinfile``

   * See :ref:`as_files-blockinfile.yml` annotated source code
