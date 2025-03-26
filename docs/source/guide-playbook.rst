.. _ug_playbook:

Playbook
********

Below is a simple playbook that calls this role (11) at a single host
*srv.example.com* (2)

.. code-block:: bash
   :emphasize-lines: 2,11
   :linenos:

   shell> cat pb.yml
   - hosts: srv.example.com
     gather_facts: true
     connection: ssh
     remote_user: admin
     become: true
     become_user: root
     become_method: sudo

     roles:
       - vbotka.config_light

.. note::

   * ``gather_facts: true`` (3) must be set to gather facts needed to
     evaluate OS-specific options of the role. For example, the
     variable *ansible_os_family* is needed to select the Ansible
     module to install packages.

   * For details see `Connection Plugins <https://docs.ansible.com/ansible/latest/plugins/connection.html>`__ (4-5)

   * and `Understanding Privilege Escalation <https://docs.ansible.com/ansible/latest/user_guide/become.html#understanding-privilege-escalation>`__ (6-8)
