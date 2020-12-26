States
------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_states* is a dictionary of the files' states.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **state**                   | *string*           | State of the filename
                              | ``required``       |
| **path**                    | *string*           | Path to file
                              | ``required``       |
| **owner**                   | *string*           | Owner of the file
                              |                    |
| **group**                   | *string*           | Group of the file
                              |                    |
| **mode**                    | *string*           | Mode of the file
                              |                    |
============================= ==================== ============================

<TODO: complete parameters. See tasks/states.yml>


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
