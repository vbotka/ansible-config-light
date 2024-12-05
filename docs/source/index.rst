#########################
Ansible role Config Light
#########################

**vbotka.config_light**

Role version 2.6.7

The role installs packages, creates and configures files and
services. The handlers are created from user provided configuration
data. The control-flow will be determined by the configuration
data. The configuration data also determine which Ansible
modules will be used. This `data-driven programming
<https://en.wikipedia.org/wiki/Data-driven_programming>`_ paradigm
provides a flexible and robust framework to apply basic Ansible
modules:

* apt, dnf, snap, package, pkgng, portinstall
* mount, file
* template, copy, replace, patch, lineinfile, blockinfile, ini_file
* service

| This `role <https://galaxy.ansible.com/vbotka/config_light/>`_ and the documentation is work in progress.
| Feel free to `share your feedback and report issues <https://github.com/vbotka/ansible-config-light/issues>`_.
| `Contributions are welcome <https://github.com/firstcontributions/first-contributions>`_.

| GitHub: `ansible-config-light  <https://github.com/vbotka/ansible-config-light/>`_
| Ansible Galaxy: `vbotka.config_light <https://galaxy.ansible.com/vbotka/config_light/>`_

| This role is licensed and distributed as a whole under
| **BSD 2-Clause "Simplified" License**
| SPDX-License-Identifier: `BSD-2-Clause <https://spdx.org/licenses/BSD-2-Clause.html>`_


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
