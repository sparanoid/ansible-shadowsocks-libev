# Ansible Role: Shadowsocks

[![Build Status](https://travis-ci.org/sparanoid/ansible-shadowsocks.svg)](https://travis-ci.org/sparanoid/ansible-shadowsocks)

Install [Shadowsocks](https://github.com/shadowsocks) via Ansible.

## Features

- Install or upgrade Shadowsocks Python version easily
- Tuning `sysctl` automatically for better performance
- Detect `tcp_fastopen` support
- Support init startup script

## Requirements

This role requires Ansible 1.6 or higher and platform requirements are listed in the metadata file.

## Dependencies

None

## Example Playbooks

Install shadowsocks with custom location (default: `/etc/shadowsocks`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks, shadowsocks_home: /home/sparanoid/shadowsocks }
```

Install shadowsocks with different encryption (default: `aes-256-cfb`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks, shadowsocks_config_encryption_method: salsa20 }
```

Install shadowsocks with different server port (default: `443`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks, shadowsocks_config_server_port: 9999 }
```

Install shadowsocks without tuning `sysctl` (default: `shadowsocks_sysctl_tweak: true`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks, shadowsocks_sysctl_tweak: false }
```

Install shadowsocks using custom specified password (default: `apn!proxy!ss!ftw!`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks, shadowsocks_password: "myFancy@Passwd!" }
```

You can also define password in command line:

```shell
$ ansible-playbook shadowsocks-servers.yml --extra-vars "shadowsocks_password=myFancy@Passwd!"
```

## Todos

- [x] init.d script
- [x] Tuning `sysctl` support
- [x] Detect `tcp_fastopen`
- [ ] Multiple users support
- [ ] Distro support
  - [x] EL
    - [ ] Better init.d script for 7
  - [ ] Debian
  - [ ] Ubuntu

## License

GPLv3

## Author Information

**Tunghsiao Liu**

- Twitter: @[tunghsiao](http://twitter.com/tunghsiao)
- GitHub: @[sparanoid](http://github.com/sparanoid)
