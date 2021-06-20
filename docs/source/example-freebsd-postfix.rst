.. _ex_freebsd_postfix:

***************
FreeBSD Postfix
***************

.. _ex_postfix_handlers:

Handlers
========

.. _ex_handlersd_postfix_freebsd:

contrib/postfix/conf-light/handlers.d/postfix-freebsd.yml
---------------------------------------------------------

Synopsis: Create handlers for Postfix.

Use template (2) to create handlers.

[`contrib/postfix/conf-light/handlers.d/postfix-freebsd.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/postfix-freebsd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/postfix-freebsd.yml
    :language: Yaml
    :emphasize-lines: 2,5,12,19,27,35,40
    :linenos:

.. seealso:: See :ref:`as_setup.yml` how the handlers are created.
.. _ex_handlersd_sendmail_freebsd:

contrib/postfix/conf-light/handlers.d/sendmail-freebsd.yml
----------------------------------------------------------

Synopsis: Create handlers for Sendmail.

Use template (2) to create handlers.

[`contrib/postfix/conf-light/handlers.d/sendmail-freebsd.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/sendmail-freebsd.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/sendmail-freebsd.yml
    :language: Yaml
    :emphasize-lines: 2,5,12,19,27,35,41
    :linenos:

.. seealso:: See :ref:`as_setup.yml` how the handlers are created.
.. _ex_postfix_packages:

Packages
========

.. _ex_packagesd_postfix:

contrib/postfix/conf-light/packages.d/postfix.yml
-------------------------------------------------

Synopsis: Install Postfix.

Use package or port (3) to install Postfix.

[`contrib/postfix/conf-light/packages.d/postfix.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix.yml
    :language: Yaml
    :emphasize-lines: 3
    :linenos:

.. seealso:: See :ref:`as_packages.yml` how the FreeBSD packages or ports are installed.
.. _ex_postfix_services:

Services
========

.. _ex_servicesd_postfix:

contrib/postfix/conf-light/services.d/postfix.yml
-------------------------------------------------

Synopsis: Configure Postfix service.

Set service (2) state (3). Run the service on boot (4).

[`contrib/postfix/conf-light/services.d/postfix.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/postfix.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/postfix.yml
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables :ref:`ex_config_light_postfix_yml`. See :ref:`as_services.yml` how the services are configured.
.. _ex_servicesd_sendmail:

contrib/postfix/conf-light/services.d/sendmail.yml
--------------------------------------------------

Synopsis: Configure Sendmail service.

Set service (2) state (3). Do not run the service on boot (4).

[`contrib/postfix/conf-light/services.d/sendmail.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/sendmail.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/sendmail.yml
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables :ref:`ex_config_light_postfix_yml`.
.. _ex_postfix_files:

Files
=====

.. _ex_config_light_postfix_yml:

contrib/postfix/config-light-postfix.yml
----------------------------------------

Synopsis: Custom variables for Postfix.

Put the host-specific variables (6) into the ``host_vars``. Optionally other variables might be put into the ``group_vars``.

[`contrib/postfix/config-light-postfix.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/config-light-postfix.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/config-light-postfix.yml
    :language: Yaml
    :emphasize-lines: 6
    :linenos:

.. _ex_filesd_mailer_conf:

contrib/postfix/conf-light/files.d/mailer-conf.yml
--------------------------------------------------

Synopsis: Create file.

Create file (2) from the template (4).

[`contrib/postfix/conf-light/files.d/mailer-conf.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/mailer-conf.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/mailer-conf.yml
    :language: Yaml
    :emphasize-lines: 2,4
    :linenos:

.. _ex_filesd_periodic_conf:

contrib/postfix/conf-light/files.d/periodic-conf.yml
----------------------------------------------------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/periodic-conf.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/periodic-conf.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/periodic-conf.yml
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. _ex_filesd_main_cf:

contrib/postfix/conf-light/files.d/postfix-main-cf.yml
------------------------------------------------------

Synopsis: Modify file and notify handlers.

Modify file (2) with the lines (9) and notify handlers (7).

[`contrib/postfix/conf-light/files.d/postfix-main-cf.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/postfix-main-cf.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/postfix-main-cf.yml
    :language: Yaml
    :emphasize-lines: 2,7,9
    :linenos:

.. _ex_filesd_rc_conf:

contrib/postfix/conf-light/files.d/rc-conf.yml
----------------------------------------------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/rc-conf.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/rc-conf.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/rc-conf.yml
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

