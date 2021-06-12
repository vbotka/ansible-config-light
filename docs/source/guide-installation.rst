************
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
`community.general <https://docs.ansible.com/ansible/latest/collections/community/general/>`_
and `ansible.posix <https://docs.ansible.com/ansible/latest/collections/ansible/posix/index.html#plugins-in-ansible-posix/>`_  ::

    shell> ansible-galaxy collection install ansible.posix
    shell> ansible-galaxy collection install community.general

Optionally install package ``ansible-lint`` if you want to enable the validation of created handlers and assembled data.
    
.. seealso:: * To install specific versions from various sources see `Installing content <https://galaxy.ansible.com/docs/using/installing.html>`_
	     * Take a look at other roles ``shell> ansible-galaxy search --author=vbotka``
