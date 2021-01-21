*******************
Armbian Simple SMTP
*******************

Packages
========

contrib/ssmtp/conf-light/packages.d/ssmtp
-----------------------------------------

Synopsis: Install Simple SMTP.

Use package (2) to install sSMTP.

[`contrib/ssmtp/conf-light/packages.d/ssmtp <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/packages.d/ssmtp>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/packages.d/ssmtp
    :language: Yaml
    :emphasize-lines: 2
    :linenos:

.. seealso:: See :ref:`as_packages.yml` how the Linux packages are installed.

Files
=====

contrib/ssmtp/config-light-ssmtp.yml
------------------------------------

Synopsis: Custom variables for sSMTP.

Put the host-specific variables (7) into the ``host_vars``. Optionally other variables might be put into the ``group_vars``.

[`contrib/ssmtp/config-light-ssmtp.yml <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/config-light-ssmtp.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/config-light-ssmtp.yml
    :language: Yaml
    :emphasize-lines: 7
    :linenos:

contrib/ssmtp/conf-light/files.d/revaliases
-------------------------------------------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/ssmtp/conf-light/files.d/revaliases <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/files.d/revaliases>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/files.d/revaliases
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. seealso:: See template `revaliases.j2 <https://github.com/vbotka/ansible-config-light/blob/master/templates/revaliases.j2>`_. See how files are created from template :ref:`as_files-template.yml`.

contrib/ssmtp/conf-light/files.d/ssmtp-conf
-------------------------------------------

Synopsis: Create file.

Create file (2) from the template (7).

[`contrib/ssmtp/conf-light/files.d/ssmtp-conf <https://github.com/vbotka/ansible-config-light/blob/master/contrib/ssmtp/conf-light/files.d/ssmtp-conf>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../contrib/ssmtp/conf-light/files.d/ssmtp-conf
    :language: Yaml
    :emphasize-lines: 2,7
    :linenos:

.. seealso:: See template `ssmtp.conf.j2 <https://github.com/vbotka/ansible-config-light/blob/master/templates/ssmtp.conf.j2>`_. See how files are created from template :ref:`as_files-template.yml`.
