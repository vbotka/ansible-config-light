# config_light

[![Build Status](https://travis-ci.org/vbotka/ansible-config-light.svg?branch=master)](https://travis-ci.org/vbotka/ansible-config-light)

[Ansible role.](https://galaxy.ansible.com/vbotka/config_light/)

Configure files and trigger handlers.


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

## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
