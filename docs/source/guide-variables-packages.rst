.. _ug_variables_packages:

Packages
--------
.. contents::
   :local:

Synopsis
^^^^^^^^

The dictionary *cl_packages* comprises packages or BSD ports.

Parameters
^^^^^^^^^^

+---------------------+-----------------------+---------------------------------------+
| Parameter           | Type                  | Comments                              |
+=====================+=======================+=======================================+
| name                | list ``required``     | List of package or BSD ports          |
+---------------------+-----------------------+---------------------------------------+
| state               | string                | State of package or BSD ports         |
|                     |                       | default: 'present'                    |
+---------------------+-----------------------+---------------------------------------+
| ...                 | ...                   | <TBD: see tasks/packages.yml>         |
+---------------------+-----------------------+---------------------------------------+


Example
^^^^^^^

FreeBSD package for Postfix

[`contrib/postfix/conf-light/packages.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix
    :language: yaml
    :emphasize-lines: 2
    :linenos:

Armbian package for Simple SMTP

[`contrib/ssmtp/conf-light/packages.d/ssmtp <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp
    :language: yaml
    :emphasize-lines: 2
    :linenos:

See Also
^^^^^^^^
.. seealso::

   * See `vars-packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/vars-packages.yml>`_ at GitHub how the variable *cl_packages* is combined with the content of the directory *cl_packagesd_dir*

   * See `packages.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/packages.yml>`_ at GitHub how the packages or BSD ports are installed

     **Anotated source code**
     
   * :ref:`as_vars-packages.yml`

   * :ref:`as_packages.yml`
