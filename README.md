# config_light

[![Build Status](https://travis-ci.org/vbotka/ansible-config-light.svg?branch=master)](https://travis-ci.org/vbotka/ansible-config-light)

[Ansible role.](https://galaxy.ansible.com/vbotka/config_light/)

Install packages, configure files and trigger handlers.


## Requirements

None.


## Role Variables

* Read the defaults and examples in vars.
* Create handlers if configured


## Dependencies

None.


## Example Playbook

```
- name: conf_light
  hosts: localhost
  become: yes
  roles:
    - vbotka.config_light
```

## Example. Common variables

```
$ cat config-light-common.yml
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
$ cat config-light-ssmtp.yml
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
$ cat conf-light/files.d/ssmtp-conf
ssmtp_conf:
  path: '/etc/ssmtp/ssmtp.conf'
  force: true
  owner: 'root'
  group: 'mail'
  mode: 'u=rw,g=r'
  template: 'ssmtp.conf.j2'

$ cat conf-light/files.d/revaliases
revaliases:
  path: '/etc/ssmtp/revaliases'
  force: true
  owner: 'root'
  group: 'mail'
  mode: 'u=rw,g=r'
  template: 'revaliases.j2'

$ cat conf-light/packages.d/ssmtp.json
{'name': 'ssmtp'}
```

## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
