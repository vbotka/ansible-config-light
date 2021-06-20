.. _ug_variables_services:

Services
--------
.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_services* comprises managed services.

Parameters
^^^^^^^^^^

+---------------------+-----------------------+---------------------------------------+
| Parameter           | Type                  | Comments                              |
+=====================+=======================+=======================================+
| name                | string ``required``   | Name of the service                   |
+---------------------+-----------------------+---------------------------------------+
| state               | string                | State of the service                  |
|                     |                       | default: started                      |
+---------------------+-----------------------+---------------------------------------+
| enabled             | boolean               | Start on boot                         |
|                     |                       | default: true                         |
+---------------------+-----------------------+---------------------------------------+

Example
^^^^^^^

FreeBSD services for Postfix and Sendmail

[`contrib/postfix/conf-light/service.d/postfix.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/postfixd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/postfix.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:

[`contrib/postfix/conf-light/service.d/sendmail.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/sendmail.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/sendmail.yml
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-services.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-services.yml>`_ at GitHub how the variable *cl_services* is combined with the content of the directory *cl_servicesd_dir*

   * See `services.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/services.yml>`_ at GitHub how the services are configured

     **Annotated source code**

   * :ref:`as_vars-services.yml`

   * :ref:`as_services.yml`
