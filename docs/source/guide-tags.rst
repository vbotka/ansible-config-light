****
Tags
****

The tags provide a very useful tool to run selected tasks of the role. To see what tags are
available list the tags of the role with the command

.. code-block:: bash
   :emphasize-lines: 1
   :linenos:

    shell> ansible-playbook config-light.yml --list-tags

    playbook: config-light.yml

      play #1 (srv.example.com): srv.example.com	TAGS: []
      TASK TAGS: [always, cl_debug, cl_files, cl_packages, cl_sanity,
      cl_services, cl_setup, cl_states, cl_vars]

For example, display the list of the variables and their values with the tag ``cl_debug`` (when
debug is enabled ``cl_debug: true``). With this tag specified ``-t cl_debug`` all imported tasks
before the task *debug.yml* will also run because of the tag ``always`` when sanity testing is
enabled ``cl_sanity: true`` (default) and setup is enabled ``cl_setup: true`` (default). ::

    shell> ansible-playbook config-light.yml -t cl_debug

See what packages will be installed ::

    shell> ansible-playbook config-light.yml -t cl_packages --check

Install packages and exit the play ::

    shell> ansible-playbook config-light.yml -t cl_packages

.. seealso::

   * See :ref:`ug_bp` on how to use tags efficiently
   * See :ref:`as_main.yml` annotated source code
   * See `main.yml  <https://github.com/vbotka/ansible-config-light/blob/master/tasks/main.yml>`_ at GitHub
