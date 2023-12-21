.. _ug_variables_defaults:

Default variables
=================

Default variables are stored in the directory ``defaults``.

Most of the variables are self-explaining. There are five very
important variables ``cl_handlers``, ``cl_packages``, ``cl_states``,
``cl_services``, and ``cl_files`` (26-30). These dictionaries, which
comprise the configuration data of handlers, packages, services, and
files, will be explained in details. By default, these dictionaries
are empty.

Best practice is to provide the data either in *host_vars* and
*group_vars* or as a files in the directories ``cl_handlersd_dir``,
``cl_packagesd_dir``, ``cl_statesd_dir``, ``cl_servicesd_dir``, and
``cl_filesd_dir`` (37-41). Both methods can be applied at the same
time. The variables will be assembled and combined by the tasks
``vars_handlers.yml``, ``vars_packages.yml``, ``vars_states.yml``,
``vars_services.yml``, and ``vars_files.yml``. The assembled
dictionaries, customized for each host in the play, will be stored in
the host-specific files ``cl_packagesd``, ``cl_statesd``,
``cl_servicesd``, and ``cl_filesd`` (60-63). The variable
``cl_handlers`` is not host-specific because the handlers will be
created at the controller (localhost) only. Assembled dictionary
``cl_handlers`` will be stored in the file ``cl_handlersd`` (59). Take
a look at the assembled data in the directory ``cl_dira`` (58).

By default, the base of the directories is ``role_path`` (36). The
user is expected to put the configuration data to a more suitable
directory, for example, to ``playbook_dir`` directory.

[`defaults/main.yml <https://github.com/vbotka/ansible-config-light/blob/master/defaults/main.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../defaults/main.yml
    :language: yaml
    :emphasize-lines: 2, 26-30, 37-41, 60-63
    :linenos:

.. warning::

   The defaults of the variables *cl_dird_dmode* (35),
   *cl_dira_dmode* (56) and *cl_dira_fmode* (57) to access the
   configuration data and the assembled dictionaries are very
   permissive. Restrict the permissions if these dictionaries might
   comprise classified data.

.. comments

   <TODO: complete description of all default variables>
