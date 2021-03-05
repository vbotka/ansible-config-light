.. _ug_variables_handlers:

Handlers
--------
.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_handlers* comprises handlers. The structure of the dictionary depends on the
template that is used to create the files with the handlers. For example, the structure below can be
used together with the template *handlers-auto1.yml.j2*.

Parameters
^^^^^^^^^^

+---------------------+-----------------------+---------------------------------------+
| Parameter           | Type                  | Comments                              |
+=====================+=======================+=======================================+
| template            | string ``required``   | Template filename                     |
+---------------------+-----------------------+---------------------------------------+
| handlers            | list ``required``     | List of handlers dictionaries         |
+--+------------------+-----------------------+---------------------------------------+
|  | handler          | string ``required``   | Name of the handler                   |
|  +------------------+-----------------------+---------------------------------------+
|  | module           | string ``required``   | Ansible module in handler             |
|  +------------------+-----------------------+---------------------------------------+
|  | params           | list ``required``     | Ansible module parameters             |
|  +------------------+-----------------------+---------------------------------------+
|  | conditions       | list                  | List of conditions                    |
+--+------------------+-----------------------+---------------------------------------+

Example
^^^^^^^
FreeBSD handlers for Postfix

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

   * For details see the template `handlers-auto1.yml.j2  <https://github.com/vbotka/ansible-config-light/blob/master/templates/handlers-auto1.yml.j2>`_

   * See `vars-handlers.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-handlers.yml>`_ at GitHub how the variable *cl_handlers* is combined with the content of the directory *cl_handlersd_dir*

   * See `setup.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/setup.yml>`_ at GitHub how the handlers are created

     **Annotated source code**

   * :ref:`as_vars-handlers.yml`

   * :ref:`as_setup.yml`
	     
Notes
^^^^^
.. note:: The template *handlers-auto1.yml.j2* is available in the role's directory
          ``templates``. The user is expected to create new templates when needed. Feel free to
          change the structure of the data and to create new templates that might fit the purpose
          better. Feel free to contribute new templates and configuration examples to the `project
          <https://github.com/vbotka/ansible-config-light/>`_.
