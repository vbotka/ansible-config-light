.. _ug_variables_files-markers:

blockinfile markers
^^^^^^^^^^^^^^^^^^^

Create markers for Ansible module blockinfile. Mark existing blocks
that you want to configure.

Parameters for blockinfile markers
""""""""""""""""""""""""""""""""""

+---------------------+-----------------------+-----------------------------+
| Parameter           | Type                  | Comments                    |
+=====================+=======================+=============================+
| path                | string ``required``   | Path to file                |
+---------------------+-----------------------+-----------------------------+
| markers             | list ``required``     | List of dictionaries        |
|                     |                       | (see fn/mark-block.yml)     |
+--+------------------+-----------------------+-----------------------------+
|  | regex1           | string ``required``   | Regex of block's beginning  |
|  +------------------+-----------------------+-----------------------------+
|  | replace1         | string ``required``   | Block's beginning           |
|  +------------------+-----------------------+-----------------------------+
|  | regex2           | string ``required``   | Regex of block's ending     |
|  +------------------+-----------------------+-----------------------------+
|  | replace2         | string ``required``   | Block's ending              |
+--+------------------+-----------------------+-----------------------------+

Example of blockinfile markers
""""""""""""""""""""""""""""""

For example, in file ``/usr/local/etc/lighttpd/modules.conf``, create
blockinfile markers in the following block ::

  ##
  
  server.modules = (
    "mod_access",
    #  "mod_alias",
    #  "mod_auth",
    #  "mod_authn_file",
    #  "mod_evasive",
    #  "mod_setenv",
    #  "mod_usertrack",
    #  "mod_redirect",
    #  "mod_rewrite",
    )
  
  ##

Create the description of the file (2) and declare the variable for
the list of the markers (8)

[`contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd_nagios/conf-light/files.d/lighttpd-modulesconf
    :language: yaml
    :emphasize-lines: 2,8
    :linenos:

Create the list of the dictionaries ``cl_lighttpd_modulesconf_markers`` (73)

[`contrib/lighttpd_nagios/cl-lighttpd.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd_nagios/cl-lighttpd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd_nagios/cl-lighttpd.yml
    :language: yaml
    :lines: 68-78
    :lineno-start: 68
    :emphasize-lines: 6
    :linenos:

Then, the command ::

  shell> ansible-playbook config-light.yml -t cl_files_copy,cl_files_markers

will copy sample file ``modules.conf.sample`` to ``modules.conf`` and
will create blockline markers ::

  ##

  # BEGIN ANSIBLE MANAGED BLOCK server.modules
  server.modules = (
    "mod_access",
  #  "mod_alias",
  #  "mod_auth",
  #  "mod_authn_file",
  #  "mod_evasive",
  #  "mod_setenv",
  #  "mod_usertrack",
  #  "mod_redirect",
  #  "mod_rewrite",

  )
  # END ANSIBLE MANAGED BLOCK server.modules

  ##

See Also
""""""""
.. seealso::

   * See `files-markers.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-markers.yml>`_ at GitHub how the markers are created

   * See `fn/mark-block.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/fn/mark-block.yml>`_ at GitHub how the markers are created

     **Annotated source code**

   * :ref:`as_files-markers.yml`

   * :ref:`as_mark-block.yml`
