## nagios-client

[![Build Status](https://travis-ci.org/Oefenweb/ansible-nagios-client.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-nagios-client) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-nagios--client-blue.svg)](https://galaxy.ansible.com/list#/roles/5696)

Set up a machine (client) so it can be monitored by nagios (server).

#### Requirements

None

#### Variables

* `nagios_client_install`  [default: `[]`]: Packages to install (e.g. `percona-nagios-plugins`)
* `nagios_client_user`: [default: `nagios`]: The user that the nagios server will use to login
* `nagios_client_group`: [default: `nagios`]: The primary group of the nagios user
* `nagios_client_groups`: [default: `[]`]: The secondary groups of the nagios user

* `nagios_client_authorized_keys`: [default: `[]`]: Authorized key declarations
* `nagios_client_authorized_keys.{n}.src`: [required]: The local path of the key
* `nagios_client_authorized_keys.{n}.state`: [optional, default: `present`]: State

* `nagios_client_script_map` [default: `{}`]: Script declarations
* `nagios_client_script_map.key`: [required]: The identifier of the file (e.g. `check_raid`)
* `nagios_client_script_map.key.src`: [required]: The local path of the file to copy, can be absolute or relative (e.g. `../../../files/nagios-client/usr/lib/nagios/plugins/check_raid`)
* `nagios_client_script_map.key.dest`: [required]: The remote path of the file to copy (e.g. `/usr/lib/nagios/plugins/check_raid`)
* `nagios_client_script_map.key.owner`: [optional, default `root`]: The name of the user that should own the file
* `nagios_client_script_map.key.group`: [optional, default `root`]:The name of the group that should own the file
* `nagios_client_script_map.key.mode`: [optional, default `0755`]: The mode of the file

## Dependencies

None

#### Example

```yaml
---
- hosts: all
  roles:
    - nagios-client
  vars:
    nagios_client_authorized_keys:
      - src: ../../../files/nagios-client/etc/nagios/id_rsa.pub
```

#### License

MIT

#### Author Information

Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-nagios-client/issues)!
