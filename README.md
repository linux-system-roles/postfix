# postfix

[![ansible-lint.yml](https://github.com/linux-system-roles/postfix/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/linux-system-roles/postfix/actions/workflows/ansible-lint.yml) [![ansible-test.yml](https://github.com/linux-system-roles/postfix/actions/workflows/ansible-test.yml/badge.svg)](https://github.com/linux-system-roles/postfix/actions/workflows/ansible-test.yml) [![markdownlint.yml](https://github.com/linux-system-roles/postfix/actions/workflows/markdownlint.yml/badge.svg)](https://github.com/linux-system-roles/postfix/actions/workflows/markdownlint.yml) [![woke.yml](https://github.com/linux-system-roles/postfix/actions/workflows/woke.yml/badge.svg)](https://github.com/linux-system-roles/postfix/actions/workflows/woke.yml)

This role can install, configure and start Postfix MTA.

## Requirements

See below

### Collection requirements

The role requires the `firewall` role and the `selinux` role from the
`fedora.linux_system_roles` collection, if `postfix_manage_firewall`
and `postfix_manage_selinux` is set to true, respectively.
(Please see also [`postfix_manage_firewall`](#postfix_manage_firewall)
 and [`postfix_manage_selinux`](#postfix_manage_selinux))

If the `postfix` is a role from the `fedora.linux_system_roles`
collection or from the Fedora RPM package, the requirement is already
satisfied.

The role requires additional collections to manage `rpm-ostree` systems.
If you need to manage `rpm-ostree` systems, run the below command to
install the collections.

```bash
ansible-galaxy collection install -r meta/collection-requirements.yml
```

## Role Variables

### postfix_conf

```yaml
postfix_conf:
  relayhost: example.com
```

This is a dictionary which can hold key/value pairs of all supported Postfix
configuration parameters. Keys not supported by the installed Postfix are
ignored.  The default is empty `{}`.

You can specify `previous: replaced` within the `postfix_conf` dictionary to
remove any existing configuration and apply the desired configuration on top of
clean postfix installation.

**WARNING**: If you specify `previous: replaced`, the role reinstalls the postfix
package and replaces the existing `/etc/postfix/main.cf` and
`/etc/postfix/master.cf` files. <!--- wokeignore:rule=master -->
Ensure to back up those files to preserve your settings.

**WARNING**: When managing `rpm-ostree` systems, the role cannot reinstall the
postfix package, so it just replaces the modified config files with empty files.
This is not idempotent.

If you specify only `previous: replaced` under the `postfix_conf` dictionary,
the role re-installs the `postfix` package and enables the `postfix` service
without applying any configuration.

For example, to remove existing configuration and set `relayhost: example.com`
on top of clean postfix installation, use `postfix_conf` like this:

```yaml
postfix_conf:
  previous: replaced
  relayhost: example.com
```

### postfix_files

```yaml
postfix_files:
  - name: sasl_passwd
    content: example.com user:password
    postmap: true
  - name: sender_canonical_maps
    content: /.+/  info@example.com
```

This is a list of files that will be placed in /etc/postfix and that can be converted into Postfix Lookup Tables if needed.

It's meant as a simple mechanism to configure things such as SASL credentials and other small snippets.

### postfix_check

```yaml
postfix_check: false
```

This is a boolean which determines if `postfix check` is run before starting
Postfix if the configuration has changed.  The default is `true`.

### postfix_backup

```yaml
postfix_backup: true
```

This is a boolean which determines if the role will make a single backup copy of
the configuration - for example,
`cp /etc/postfix/main.cf /etc/postfix/main.cf.backup`,
thus overwriting the previous backup, if any.  The default is `false`.  NOTE: If
you want to set this to `true`, you must also set `postfix_backup_multiple:
false` - see below.

### postfix_backup_multiple

```yaml
postfix_backup_multiple: false
```

This is a boolean which determines if the role will make a timestamped backup copy of
the configuration - for example,
`cp /etc/postfix/main.cf /etc/postfix/main.cf.$(date -Isec)`,
thus keeping multiple backup copies.  The default is `true`.  NOTE: This setting
overrides `postfix_backup`, so you must set this to `false` if you want to use
`postfix_backup`.

### postfix_manage_firewall

Boolean flag allowing to configure firewall using the firewall role.
Manage the smtp related ports, 25/tcp, 465/tcp, and 587/tcp.
If the variable is set to `false`, the `postfix role` does not manage the
firewall.
Default to `false`.

NOTE: `postfix_manage_firewall` is limited to *adding* ports.
It cannot be used for *removing* ports.
If you want to remove ports, you will need to use the firewall system
role directly.

NOTE: the firewall management is not supported on RHEL 6.

### postfix_manage_selinux

Boolean flag allowing to configure selinux using the selinux role.
Assign `smtp_port_t` to the smtp related ports.
If the variable is set to false, the `postfix role` does not manage the
selinux

NOTE: `postfix_manage_selinux` is limited to *adding* policy.
It cannot be used for *removing* policy.
If you want to remove policy, you will need to use the selinux system
role directly.

## Limitations

There is no way to remove separate configuration parameters.
As a workaround, you can use `postfix_conf`'s `previous: replaced` to remove the existing configuration and then apply
the desired configuration on top of clean postfix installation.
For more information, see [`postfix_conf`](#postfix_conf).

## Example Playbook

Install and enable postfix. Configure `relay_domains=$mydestination` and
`relayhost=example.com`.

```yaml
---
- name: Manage postfix
  hosts: all
  vars:
    postfix_conf:
      relay_domains: $mydestination
      relayhost: example.com
  roles:
    - linux-system-roles.postfix
```

Install and enable postfix. Do not run 'postfix check' before restarting
postfix:

```yaml
---
- name: Manage postfix with no check
  hosts: all
  vars:
    postfix_check: false
  roles:
    - linux-system-roles.postfix
```

Install and enable postfix. Do single backup of main.cf (older backup will be
rewritten) and configure `relayhost=example.com`:

```yaml
---
- name: Manage postfix with relayhost
  hosts: all
  vars:
    postfix_conf:
      relayhost: example.com
    postfix_backup: true
  roles:
    - linux-system-roles.postfix
```

Install and enable postfix. Do timestamped backup of main.cf and
configure `relayhost=example.com` (if `postfix_backup_multiple` is
set to true `postfix_backup` is ignored):

```yaml
---
- name: Manage postfix with multiple backups
  hosts: all
  vars:
    postfix_conf:
      relayhost: example.com
    postfix_backup_multiple: true
  roles:
    - linux-system-roles.postfix
```

## rpm-ostree

See README-ostree.md

## License

Copyright (C) 2017 Jaroslav Škarvada <jskarvad@redhat.com>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.
