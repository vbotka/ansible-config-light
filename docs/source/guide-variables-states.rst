States
------
.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_states* comprises states of the files.

Parameters
^^^^^^^^^^

+---------------------+-----------------------+---------------------------------------+
| Parameter           | Type                  | Comments                              |
+=====================+=======================+=======================================+
| path                | string ``required``   | Path to file                          |
+---------------------+-----------------------+---------------------------------------+
| state               | string                | State of the filename                 |
+---------------------+-----------------------+---------------------------------------+
| owner               | string                | Owner of the file                     |
+---------------------+-----------------------+---------------------------------------+
| group               | string                | Group of the file                     |
+---------------------+-----------------------+---------------------------------------+
| mode                | string                | Mode of the file                      |
+---------------------+-----------------------+---------------------------------------+
| ...                 | ...                   | <TBD: see tasks/states.yml>           |
+---------------------+-----------------------+---------------------------------------+


Example
^^^^^^^
File's states

[`contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root <https://github.com/vbotka/ansible-config-light/blob/master/contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/lighttpd/conf-light/states.d/lighttpd-server-document-root
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-states.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-states.yml>`_ how the variable *cl_states* is combined with the content of the directory *cl_statesd_dir*.

   * See `states.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/states.yml>`_ how the file's states are set.
