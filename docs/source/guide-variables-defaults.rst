Default variables
-----------------

Default variables are stored in the directory ``defaults``.

Most of the variables are self-explaining. There are five very
important variables ``cl_handlers``, ``cl_packages``, ``cl_states``,
``cl_services``, and ``cl_files`` (13-17). These dictionaries, which
comprise the configuration data of handlers, packages, services, and
files, will be explained in details. By default, these dictionaries are
empty.

Best practice is to provide the data either in *host_vars* and
*group_vars* or as a files in the directories ``cl_handlersd_dir``,
``cl_packagesd_dir``, ``cl_statesd_dir``, ``cl_servicesd_dir``, and
``cl_filesd_dir`` (24-28). Both methods can be applied at the same
time. The variables will be assembled and combined by the tasks
``vars_handlers.yml``, ``vars_packages.yml``, ``vars_states.yml``,
``vars_services.yml``, and ``vars_files.yml``. The assembled
dictionaries, customized for each host in the play, will be stored in
the host-specific files ``cl_packagesd``, ``cl_statesd``,
``cl_servicesd``, and ``cl_filesd`` (37-40). The variable
``cl_handlers`` is not host-specific, because the handlers will be
created at the controller (localhost) only. Assembled dictionary
``cl_handlers`` will be stored in the file ``cl_handlersd`` (36). Take
a look at the directory ``cl_dira`` (35) to see assembled data.

By default, the base of the directories is ``role_path`` (23). The user
is expected to put the configuration data to a more suitable directory,
e.g., to ``playbook_dir`` directory.

[`defaults/main.yml <https://github.com/vbotka/ansible-config-light/blob/master/defaults/main.yml>`_]

.. highlight:: yaml
    :linenothreshold: 5
.. literalinclude:: ../../defaults/main.yml
    :language: yaml
    :emphasize-lines: 2, 13-17, 24-28, 36-40
    :linenos:

.. warning:: Defaults of the variables *cl_dird_dmode* (22), *cl_dira_dmode* (33) and *cl_dira_fmode* (34) are very permissive. These are the permissions to access the configuration data and the assembled dictionaries. Restrict the permissions if these dictionaries might comprise classified data.

<TODO: complete description of all default variables>