## ubuntu-1604-collectd

Set up Collectd (client) on Ubuntu 16.04.

#### Variables

* `ubuntu_1604_collectd_plugins_present`: [see: defaults/main.yml]: Names of the plugins to install
* `ubuntu_1604_collectd_plugins_absent`: [default: `[]`]: Names of the plugins to remove

* `ubuntu_1604_collectd_plugin_network_servers`: [default: `[]`]: The servers to send the data to
* `ubuntu_1604_collectd_plugin_network_servers.{n}.server`: [required]: The IP address of the server
* `ubuntu_1604_collectd_plugin_network_servers.{n}.port`: [default: `25826`]: The port of the server
* `ubuntu_1604_collectd_plugin_network_servers.{n}.security_level`: [optional]: The security level is one of three values: None, Sign or Encrypt
* `ubuntu_1604_collectd_plugin_network_servers.{n}.username`: [optional]: Username
* `ubuntu_1604_collectd_plugin_network_servers.{n}.password`: [optional]: Password

* `ubuntu_1604_collectd_plugin_disk_disks`: [default: `['/^[vhs]d[a-f]$/']`]: Names (or regexes to match names) of disks to collect information of

* `ubuntu_1604_collectd_plugin_interface_interfaces`: [default: `[]`]: Network interfaces to collect information of, defaults to all interfaces when empty

#### Examples

##### Minimal (set server IP address for network plugin only)

```yaml
---
- hosts: all
  roles:
    - ubuntu-1604-collectd
  vars:
    ubuntu_1604_collectd_plugin_network_servers:
      - server: '10.0.0.1'
```

##### With encryption

```yaml
---
- hosts: all
  roles:
    - ubuntu-1604-collectd
  vars:
    ubuntu_1604_collectd_plugin_network_servers:
      - server: '10.0.0.1'
        security_level: Encrypt
        username: username
        password: password
```
