# Ansible Role: shadowsocks-libev

[![Build Status](https://travis-ci.org/sparanoid/ansible-shadowsocks-libev.svg)](https://travis-ci.org/sparanoid/ansible-shadowsocks-libev)

Install [shadowsocks-libev](https://github.com/shadowsocks/shadowsocks-libev) via Ansible.

## Features

- Install or upgrade shadowsocks-libev version easily
- Tuning `sysctl` automatically for better performance
- Detect `tcp_fastopen` support
- Support init startup script

## Requirements

This role requires Ansible 1.6 or higher and platform requirements are listed in the metadata file.

## Dependencies

None

## Example Playbooks

Install shadowsocks-libev with custom location (default: `/etc/shadowsocks-libev`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_home: /home/sparanoid/shadowsocks-libev }
```

Install shadowsocks-libev with different encryption (default: `aes-256-cfb`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_config_encryption_method: salsa20 }
```

Install shadowsocks-libev with different server port (default: `443`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_config_server_port: 9999 }
```

Install shadowsocks-libev without tuning `sysctl` (default: `shadowsocks_sysctl_tweak: true`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_sysctl_tweak: false }
```

Install shadowsocks-libev without shadowsocks/simple-obfs support (default: `shadowsocks_obfs: true`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_obfs: false }
```

Install shadowsocks-libev using custom specified password (default: `apn!proxy!ss!ftw!`):

```yaml
- hosts: servers
  roles:
    - { role: sparanoid.shadowsocks-libev, shadowsocks_password: "myFancy@Passwd!" }
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
    - [x] Better init.d script for 7
  - [ ] Debian
  - [ ] Ubuntu

## License

GPLv3

## Author Information

**Tunghsiao Liu**

- Twitter: @[tunghsiao](http://twitter.com/tunghsiao)
- GitHub: @[sparanoid](http://github.com/sparanoid)
