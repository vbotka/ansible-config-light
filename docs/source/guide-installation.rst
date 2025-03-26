.. _ug_installation:

Installation
************

The most convenient way how to install an Ansible role is to use
Ansible Galaxy CLI ``ansible-galaxy``. The utility comes with the
standard Ansible package and provides the user with a simple interface
to the Ansible Galaxy's services. For example, take a look at the
current status of the role ::

    shell> ansible-galaxy role info vbotka.config_light

and install it ::

    shell> ansible-galaxy role install vbotka.config_light

Install the collections
`community.general <https://docs.ansible.com/ansible/latest/collections/community/general/>`__
and `ansible.posix <https://docs.ansible.com/ansible/latest/collections/ansible/posix/index.html#plugins-in-ansible-posix/>`__ if necessary ::

    shell> ansible-galaxy collection install ansible.posix
    shell> ansible-galaxy collection install community.general

Install ``yamllint`` to use the default validation of the created
handlers and assembled data. See the variables *cl_assemble_validate*
and *cl_handlers_validate* in *defaults/main.yml*. Optionally, install
and configure *ansible-lint*.

.. note::

   * By default sanity checking of *yamllint* is disabled
     (*cl_sanity_yamllint: false*)

.. hint::

   * To install specific versions from various sources see `Ansible
     Galaxy <https://galaxy.ansible.com/ui/>`_

   * Take a look at other roles ``shell> ansible-galaxy
     search --author=vbotka``
