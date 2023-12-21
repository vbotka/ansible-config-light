#########################
Ansible role Config Light
#########################

The role installs packages, creates and configures files and
services. The handlers are created from user provided configuration
data. The control-flow will be determined by the configuration
data. Some attributes of the dictionaries determine which Ansible
module will be used. This `data-driven programming
<https://en.wikipedia.org/wiki/Data-driven_programming>`_ paradigm
provides a flexible, and robust framework to apply basic Ansible
modules:

* apt, yum, snap, package, pkgng, portinstall
* mount, file
* template, copy, replace, patch, lineinfile, blockinfile, ini_file
* service

This `role <https://galaxy.ansible.com/vbotka/config_light/>`_ and the documentation is work in progress. Feel free to `share your feedback and report issues
<https://github.com/vbotka/ansible-config-light/issues>`_.

`Contributions are welcome <https://github.com/firstcontributions/first-contributions>`_.

.. toctree::
   :maxdepth: 2
   :caption: Table of Contents

   qsg
   guide
   examples
   annotation
   collection-bsd
   copyright
   legalnotice


Indices and tables
------------------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
