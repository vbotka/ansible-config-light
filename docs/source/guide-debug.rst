*****
Debug
*****

To see additional debug information enable debug output in the
configuration ::

    cl_debug: true

, or set the extra variable in the command: ::

    shell> ansible-playbook config-light.yml -e 'cl_debug=true'

.. note:: The debug output of this role is optimized for the ``yaml``
          callback plugin. Set this plugin, for example, in the
          environment ``shell> export ANSIBLE_STDOUT_CALLBACK=yaml``.

.. seealso::
   * `Playbook Debugger <https://docs.ansible.com/ansible/latest/user_guide/playbooks_debugger.html>`_
   * `Debugging modules <https://docs.ansible.com/ansible/latest/dev_guide/debugging.html#debugging-modules>`_
   * `Python Debugging With Pdb <https://realpython.com/python-debugging-pdb/>`_
