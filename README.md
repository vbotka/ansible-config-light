# config_light

[![Build Status](https://travis-ci.org/vbotka/ansible-config-light.svg?branch=master)](https://travis-ci.org/vbotka/ansible-config-light)
[![Documentation Status](https://readthedocs.org/projects/docs/badge/?version=latest)](https://ansible-config-light.readthedocs.io/en/latest/)

[Ansible role.](https://galaxy.ansible.com/vbotka/config_light/) Install packages, configure files, services, and handlers.

[Documentation at readthedocs.io](https://ansible-config-light.readthedocs.io). Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-config-light/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Supported platforms

This role has been developed and tested with
* [Ubuntu Supported Releases](http://releases.ubuntu.com/)
* [FreeBSD Supported Production Releases](https://www.freebsd.org/releases/)

This may be different from the platforms in Ansible Galaxy which does not offer all
released versions in time and would report an error. For example:

```
Warnings: 2
IMPORTER101: Invalid platform: "FreeBSD-12.2", skipping.
             Invalid platform: "FreeBSD-11.4", skipping.
```


## Requirements

None.


## Role Variables

* See the [defaults](https://github.com/vbotka/ansible-config-light/blob/master/defaults/main.yml), examples in [vars](https://github.com/vbotka/ansible-config-light/blob/master/vars/main.yml) and [samples](https://github.com/vbotka/ansible-config-light/tree/master/files).
* Put configuration into the variables *cl_files, cl_packages, cl_services* and/or into the files in the directories *cl_filesd_dir, cl_packagesd_dir, cl_servicesd_dir*. Both methods can be used in the same time.
* Create [templates](https://github.com/vbotka/ansible-config-light/tree/master/templates) if configured in *cl_files*.
* Create [handlers](https://github.com/vbotka/ansible-config-light/blob/master/handlers/main.yml) if configured in *cl_files*.
* See [Example. Common variables](https://github.com/vbotka/ansible-config-light#example-common-variables).
* See [Example. SSMTP](https://github.com/vbotka/ansible-config-light#example-ssmtp).


## Dependencies

None.


## Example. Playbook

```
- name: conf_light
  hosts: localhost
  become: yes
  roles:
    - vbotka.config_light
```
### Syntax check

Run the syntax check
```
shell> ansible-playbook conf_light.yml --syntax-check
```

### Assembly of variables

Run the task *vars.yml* first to collect and assemble the variables
```
shell> ansible-playbook conf_light.yml -t cl_vars
```
Review the assembled variables in *cl_dira*

### Dry-run the playbook and display what will be changed

```
shell> ansible-playbook conf_light.yml --check --diff
```

### Run the playbook

Run the playbook twice and make sure the result is idempotent
```
shell> ansible-playbook conf_light.yml
```


## Example. Common variables

```
shell> cat config-light-common.yml
---

cl_debug: true
cl_backup: true

# Assemble data into these variables
cl_files: {}
cl_packages: []
cl_services: []

# Assemble data from these directories
cl_dird: "{{ playbook_dir }}/conf-light"
cl_filesd_dir: "{{ cl_dird }}/files.d"
cl_packagesd_dir: "{{ cl_dird }}/packages.d"
cl_servicesd_dir: "{{ cl_dird }}/services.d"

# Assemble inventory_hostname data into these files (idempotent)
cl_dira: "{{ cl_dird }}/assemble"
cl_filesd: "{{ cl_dira }}/filesd.{{ inventory_hostname }}"
cl_packagesd: "{{ cl_dira }}/packagesd.{{ inventory_hostname }}"
cl_servicesd: "{{ cl_dira }}/servicesd.{{ inventory_hostname }}"

# OS common
install_retries: 10
install_delay: 5

# FreeBSD
freebsd_install_method: "packages"
# freebsd_install_method: "ports"
freebsd_use_packages: true

# EOF
...
```


## Example. SSMTP

### Variables

```
shell> cat config-light-ssmtp.yml
---

# sSMTP - Simple SMTP
# https://wiki.debian.org/sSMTP

# conf-light/files.d/ssmtp-conf
cl_ssmtp_srv: mail.example.com
cl_ssmtp_srv_domain: example.com

cl_ssmtp_postmaster_address: "postmaster@srv.cluster9.example.com"
cl_ssmtp_mailhub: "{{ cl_ssmtp_srv }}:587"
cl_ssmtp_rewriteDomain: "{{ cl_ssmtp_srv_domain }}"

cl_ssmtp_UseTLS: "Yes"
cl_ssmtp_UseSTARTTLS: "Yes"

cl_ssmtp_AuthUser: "my_ssmtp_client"
cl_ssmtp_AuthPass: "{{ smtp_client_password_srv_example_com }}"
cl_ssmtp_AuthMethod: "LOGIN"

cl_ssmtp_FromLineOverride: "yes"

# conf-light/files.d/revaliases
cl_ssmtp_revaliases:
  - "root:root@{{ cl_ssmtp_srv_domain }}:{{ cl_ssmtp_srv }}:587"
  - "admin:admin@{{ cl_ssmtp_srv_domain }}:{{ cl_ssmtp_srv }}:587"
  - "asadmin:asadmin@{{ cl_ssmtp_srv_domain }}:{{ cl_ssmtp_srv }}:587"

# EOF
...
```


### Conf.d

```
shell> cat conf-light/files.d/ssmtp-conf
ssmtp_conf:
  path: '/etc/ssmtp/ssmtp.conf'
  force: true
  owner: 'root'
  group: 'mail'
  mode: 'u=rw,g=r'
  template: 'ssmtp.conf.j2'

shell> cat conf-light/files.d/revaliases
revaliases:
  path: '/etc/ssmtp/revaliases'
  force: true
  owner: 'root'
  group: 'mail'
  mode: 'u=rw,g=r'
  template: 'revaliases.j2'

shell> cat conf-light/packages.d/ssmtp.json
{'name': 'ssmtp'}
```


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
