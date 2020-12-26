Handlers
--------
.. contents::
   :local:

Synopsis
^^^^^^^^

The variable *cl_handlers* is a dictionary of the handlers. The
Structure of the dictionary depends on the template that is used to
create the file with the handlers. For example, the structure below
can be used with the template *handlers-auto1.yml.j2*.

Parameters
^^^^^^^^^^
============================= ==================== ============================
| *Parameter*                 | *Type*             | *Comments*
============================= ==================== ============================
| **template**                | *string*           | Template filename
                              | ``required``       |
| **handler**                 | *string*           | Name of the handler
                              | ``required``       |
| **module**                  | *string*           | Ansible module in handler
                              | ``required``       |
| **params**                  | *list*             | Ansible module parameters
                              | ``required``       |
| **conditions**              | *list*             | List of conditions
                              |                    |
============================= ==================== ============================

Example
^^^^^^^
FreeBSD handlers for postfix

[`contrib/postfix/conf-light/handlers.d/postfix-freebsd <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/postfix-freebsd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/postfix-freebsd
    :language: yaml
    :emphasize-lines: 2,5,12,19,27,35,40
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-handlers.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-handlers.yml>`_ how the variable *cl_handlers* is combined with the content of the directory *cl_handlersd_dir*.

   * See `setup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/setup.yml>`_ how the handlers are created.

   * For details see the template `handlers-auto1.yml.j2  <https://github.com/vbotka/ansible-config-light/blob/master/templates/handlers-auto1.yml.j2>`_.
	     
Notes
^^^^^
.. note:: The template *handlers-auto1.yml.j2* is available in the
          role's directory ``templates``. The user is expected to
          create new templates when needed. Feel free to change the
          structure of the data and to create new templates that might
          fit the purpose better. Feel free to contribute new
          templates and configuration examples to the `project
          <https://github.com/vbotka/ansible-config-light/>`_.
