# config_light

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/config_light)[![Build Status](https://travis-ci.org/vbotka/ansible-config-light.svg?branch=master)](https://travis-ci.org/vbotka/ansible-config-light)[![Documentation Status](https://readthedocs.org/projects/docs/badge/?version=latest)](https://ansible-config-light.readthedocs.io/en/latest/)

[Ansible role.](https://galaxy.ansible.com/vbotka/config_light/) Install packages, configure files, services, and handlers.

[Documentation at readthedocs.io](https://ansible-config-light.readthedocs.io).

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-config-light/issues).

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


## Requirements and dependencies

### Collections

* ansible.posix
* community.general

### Optional packages

* yamllint

Create the variables cl_assemble_validate and cl_handlers_validate to enable the validation. See defaults/main.yml


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
