.. _ug_variables_services:

Services
========

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

Examples
^^^^^^^^

FreeBSD services for Postfix and Sendmail
"""""""""""""""""""""""""""""""""""""""""

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

.. seealso::

   * :ref:`as_vars-services.yml`
   * :ref:`as_services.yml`
