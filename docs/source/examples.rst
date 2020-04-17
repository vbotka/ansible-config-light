.. _ex:

########
Examples
########
.. contents:: Table of Contents
   :depth: 4

.. _ex_postfix:

***************
FreeBSD Postfix
***************

.. _ex_postfix_handlers:

Handlers
========

.. _ex_handlersd_postfix_freebsd:

postfix-freebsd
---------------

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
.. _ex_handlersd_sendmail_freebsd:

sendmail-freebsd
----------------

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
.. _ex_postfix_packages:

Packages
========

.. _ex_packagesd_postfix:

postfix
-------

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
.. _ex_postfix_services:

Services
========

.. _ex_servicesd_postfix:

postfix
-------

Synopsis: Configure Postfix service.

Set service (2) state (3). Run the service on boot (4).

[`contrib/postfix/conf-light/services.d/postfix <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/postfix>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/postfix
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables :ref:`ex_config_light_postfix_yml`. See :ref:`as_services_yml` how the services are configured.
.. _ex_servicesd_sendmail:

sendmail
--------

Synopsis: Configure Sendmail service.

Set service (2) state (3). Do not run the service on boot (4).

[`contrib/postfix/conf-light/services.d/sendmail <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/services.d/sendmail>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/services.d/sendmail
    :language: Yaml
    :emphasize-lines: 2,3,4
    :linenos:

.. seealso:: See custom Postfix variables :ref:`ex_config_light_postfix_yml`.
.. _ex_postfix_files:

Files
=====

.. _ex_config_light_postfix_yml:

config-light-postfix.yml
------------------------

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

mailer-conf
-----------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/postfix/conf-light/files.d/mailer-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/mailer-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/mailer-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. _ex_filesd_periodic_conf:

periodic-conf
-------------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/periodic-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/periodic-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/periodic-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. _ex_filesd_main_cf:

postfix-main-cf
---------------

Synopsis: Modify file and notify handlers.

Modify file (2) with the lines (9) and notify handlers (7).

[`contrib/postfix/conf-light/files.d/postfix-main-cf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/postfix-main-cf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/postfix-main-cf
    :language: Yaml
    :emphasize-lines: 2,7,9
    :linenos:

.. _ex_filesd_rc_conf:

rc-conf
-------

Synopsis: Modify file.

Modify file (2) with the lines (7).

[`contrib/postfix/conf-light/files.d/rc-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/postfix/conf-light/files.d/rc-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/postfix/conf-light/files.d/rc-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:



.. _ex_ssmtp:

*******************
Armbian Simple SMTP
*******************

.. _ex_ssmtp_packages:

Packages
========

.. _ex_packagesd_ssmtp:

ssmtp
-----

Synopsis: Install Simple SMTP.

Use package (2) to install sSMTP.

[`contrib/ssmtp/conf-light/packages.d/ssmtp <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp
    :language: Yaml
    :emphasize-lines: 2
    :linenos:

.. seealso:: See :ref:`as_packages_yml` how the Linux packages are installed.
.. _ex_ssmtp_files:

Files
=====

.. _ex_config_light_ssmtp_yml:

config-light-ssmtp.yml
----------------------

Synopsis: Custom variables for sSMTP.

Put the host-specific variables (7) into the ``host_vars``. Optionally other variables might be put into the ``group_vars``.

[`contrib/ssmtp/config-light-ssmtp.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/config-light-ssmtp.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/config-light-ssmtp.yml
    :language: Yaml
    :emphasize-lines: 7
    :linenos:

.. _ex_filesd_revaliases:

revaliases
----------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/ssmtp/conf-light/files.d/revaliases <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/files.d/revaliases>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/files.d/revaliases
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. seealso:: See template `revaliases.j2 <https://github.com/vbotka/ansible-config-light/blob/master/templates/revaliases.j2>`_. See how files are created from template :ref:`as_files_template_yml`.
.. _ex_filesd_ssmtp_conf:

ssmtp-conf
----------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/ssmtp/conf-light/files.d/ssmtp-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/files.d/ssmtp-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/files.d/ssmtp-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. seealso:: See template `ssmtp.conf.j2 <https://github.com/vbotka/ansible-config-light/blob/master/templates/ssmtp.conf.j2>`_. See how files are created from template :ref:`as_files_template_yml`.
