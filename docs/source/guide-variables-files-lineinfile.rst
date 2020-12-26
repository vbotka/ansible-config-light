lineinfile
^^^^^^^^^^

Parameters for lineinfile
"""""""""""""""""""""""""
=================== ==================== ======================================
| *Parameter*       | *Type*             | *Comments*
=================== ==================== ======================================
| **path**          | *string*           | Path to file
                    | ``required``       |
| **dict**          | *list*             | List of key value dictionaries
                    | ``required``       | Either dict or lines is required
| **lines**         | *list*             | List of regexp and lines
                    | ``required``       | Either dict or lines is required
| **assignment**    | *string*           | Assignment of key and value in dict
                    |                    | default '='
| **owner**         | *string*           | Owner of the file
                    |                    |
| **group**         | *string*           | Group of the file
                    |                    |
| **mode**          | *string*           | Mode of the file
                    |                    |
| **create**        | *boolean*          | Create if does not exist
                    |                    | default: false
| **validate**      | *string*           | Command to validate file
                    |                    |
| **handlers**      | *list*             | List of handlers
                    |                    |
=================== ==================== ======================================

Example of lineinfile with lines
""""""""""""""""""""""""""""""""

File ``/usr/local/etc/lighttpd/lighttpd.conf`` for lighttpd

[`contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-lines
    :language: yaml
    :emphasize-lines: 9
    :linenos:

Example of lineinfile with dict
"""""""""""""""""""""""""""""""

File ``/usr/local/etc/lighttpd/lighttpd.conf`` for lighttpd

[`contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/files.d/lighttpd-lighttpdconf-dict
    :language: yaml
    :emphasize-lines: 10
    :linenos:

See Also
""""""""
.. seealso::

   * See `files-lineinfile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-lineinfile.yml>`_ how the files are modified or created by the Ansible module ``lineinfile``.
