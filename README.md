## collectd

[![Build Status](https://travis-ci.org/Oefenweb/ansible-collectd.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-collectd) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-collectd-blue.svg)](https://galaxy.ansible.com/Oefenweb/collectd)

Set up [Collectd](https://collectd.org/) in Debian-like systems.

#### Requirements

None

#### Variables

* `collectd_plugins_present`: [default: `['contextswitch', 'cpu', 'df', 'disk', 'interface', 'irq', 'network', 'processes', 'swap', 'tcpconns', 'uptime']`]: Names of the plugins to install
* `collectd_plugins_absent`: [default: `[]`]: Names of the plugins to remove

* `collectd_plugin_network_servers`: [default: `[]`]: The servers to send the data to
* `collectd_plugin_network_servers.{n}.server`: [required]: The IP address of the server
* `collectd_plugin_network_servers.{n}.port`: [default: `25826`]: The port of the server
* `collectd_plugin_network_servers.{n}.security_level`: [optional]: The security level is one of three values: `None`, `Sign` or `Encrypt`
* `collectd_plugin_network_servers.{n}.username`: [optional]: Username
* `collectd_plugin_network_servers.{n}.password`: [optional]: Password

* `collectd_plugin_disk_disks`: [default: `['/^[vhs]d[a-f]$/']`]: Names (or regexes to match names) of disks to collect information of

* `collectd_plugin_interface_interfaces`: [default: `[]`]: Network interfaces to collect information of, defaults to all interfaces when empty

#### Dependencies

None

#### Example(s)

##### Minimal (set server IP address for network plugin only)

```yaml
---
- hosts: all
  roles:
    - collectd
  vars:
    collectd_plugin_network_servers:
      - server: '10.0.0.1'
```

##### With encryption

```yaml
---
- hosts: all
  roles:
    - collectd
  vars:
    collectd_plugin_network_servers:
      - server: '10.0.0.1'
        security_level: Encrypt
        username: foo
        password: bar
```

#### License

MIT

#### Author Information

* Mark van Driel
* Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-collectd/issues)!
