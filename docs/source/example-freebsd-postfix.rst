***************
FreeBSD Postfix
***************

Handlers
========

contrib/postfix/conf-light/handlers.d/postfix-freebsd
-----------------------------------------------------

Synopsis: Create handlers for Postfix.

Use template (2) to create handlers.

[`contrib/postfix/conf-light/handlers.d/postfix-freebsd <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/postfix-freebsd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/postfix-freebsd
    :language: Yaml
    :emphasize-lines: 2,5,12,19,27,35,40
    :linenos:

.. seealso:: See :ref:`as_setup_yml` how the handlers are created.

contrib/postfix/conf-light/handlers.d/sendmail-freebsd
------------------------------------------------------

Synopsis: Create handlers for Sendmail.

Use template (2) to create handlers.

[`contrib/postfix/conf-light/handlers.d/sendmail-freebsd <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/handlers.d/sendmail-freebsd>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/handlers.d/sendmail-freebsd
    :language: Yaml
    :emphasize-lines: 2,5,12,19,27,35,41
    :linenos:

.. seealso:: See :ref:`as_setup_yml` how the handlers are created.

Packages
========

contrib/postfix/conf-light/packages.d/postfix
---------------------------------------------

Synopsis: Install Postfix.

Use package or port (2) to install Postfix.

[`contrib/postfix/conf-light/packages.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/packages.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/packages.d/postfix
    :language: Yaml
    :emphasize-lines: 2
    :linenos:

.. seealso:: See :ref:`as_packages_yml` how the FreeBSD packages or ports are installed.

Services
========

contrib/postfix/conf-light/services.d/postfix
---------------------------------------------

Synopsis: Configure Postfix service.

Set service (2) state (3). Run the service on boot (4).

[`contrib/postfix/conf-light/services.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/postfix
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables. See :ref:`as_services_yml` how the services are configured.

contrib/postfix/conf-light/services.d/sendmail
----------------------------------------------

Synopsis: Configure Sendmail service.

Set service (2) state (3). Do not run the service on boot (4).

[`contrib/postfix/conf-light/services.d/sendmail <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/sendmail>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/sendmail
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables.

Files
=====

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

contrib/postfix/conf-light/files.d/mailer-conf
----------------------------------------------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/postfix/conf-light/files.d/mailer-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/mailer-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/mailer-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

contrib/postfix/conf-light/files.d/periodic-conf
------------------------------------------------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/periodic-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/periodic-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/periodic-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

contrib/postfix/conf-light/files.d/postfix-main-cf
--------------------------------------------------

Synopsis: Modify file and notify handlers.

Modify file (2) with the lines (9) and notify handlers (7).

[`contrib/postfix/conf-light/files.d/postfix-main-cf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/postfix-main-cf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/postfix-main-cf
    :language: Yaml
    :emphasize-lines: 2,7,9
    :linenos:

contrib/postfix/conf-light/files.d/rc-conf
------------------------------------------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/rc-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/rc-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/rc-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos: