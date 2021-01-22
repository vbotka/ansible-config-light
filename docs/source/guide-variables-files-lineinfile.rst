.. _ug_variables_files-lineinfile:

lineinfile
^^^^^^^^^^

Create or configure lines in a file.

Parameters for lineinfile
"""""""""""""""""""""""""

+---------------------+-----------------------+-----------------------------+
| Parameter           | Type                  | Comments                    |
+=====================+=======================+=============================+
| path                | string ``required``   | Path to file                |
+---------------------+-----------------------+-----------------------------+
| lines               | list ``required``     | Lineinfile params. Either   |
|                     |                       | dict or lines is required.  |
|                     |                       | (see files-lineinfile.yml)  |
+--+------------------+-----------------------+-----------------------------+
|  | regexp           | string ``required``   | Regular expression          |
|  +------------------+-----------------------+-----------------------------+
|  | list             | string ``required``   | Line                        |
|  +------------------+-----------------------+-----------------------------+
|  | backrefs         |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | state            |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | firstmatch       |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | insertafter      |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | insertbefore     |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | ...              | ...                   | <TBD>                       |
+--+------------------+-----------------------+-----------------------------+
| assignment          | string                | Assignment of key and value |
|                     |                       | in dict                     |
+---------------------+-----------------------+-----------------------------+
| dict                | list ``required``     | Lineinfile params. Either   |
|                     |                       | dict or lines is required.  |
|                     |                       | (see files-lineinfile.yml)  |
+--+------------------+-----------------------+-----------------------------+
|  | key              | string ``required``   | Key value for regexp        |
|  +------------------+-----------------------+-----------------------------+
|  | value            | string ``required``   | Value for line              |
|  +------------------+-----------------------+-----------------------------+
|  | firstmatch       |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | insertafter      |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | insertbefore     |                       |                             |
|  +------------------+-----------------------+-----------------------------+
|  | ...              | ...                   | <TBD>                       |
+--+------------------+-----------------------+-----------------------------+
| owner               | string                | Owner of the file           |
+---------------------+-----------------------+-----------------------------+
| group               | string                | Group of the file           |
+---------------------+-----------------------+-----------------------------+
| mode                | string                | Mode of the file            |
+---------------------+-----------------------+-----------------------------+
| attributes          | string                | Attributes of the file      |
+---------------------+-----------------------+-----------------------------+
| other               | string                | Attributes of module file   |
+---------------------+-----------------------+-----------------------------+
| create              | boolean               | Create file                 |
+---------------------+-----------------------+-----------------------------+
| validate            | string                | Command to validate file    |
+---------------------+-----------------------+-----------------------------+
| handlers            | list                  | List of handlers            |
+---------------------+-----------------------+-----------------------------+

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

   * See `files-lineinfile.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/files-lineinfile.yml>`_ at GitHub how the files are modified or created by the Ansible module ``lineinfile``

   * See :ref:`as_files-lineinfile.yml` annotated source code
