# postfix
![CI Testing](https://github.com/linux-system-roles/posffix/workflows/tox/badge.svg)

This role can install, configure and start Postfix MTA.

# Role Variables

### postfix_conf

```
postfix_conf:
  relayhost: example.com
```

This is a dictionary which can hold key/value pairs of all supported Postfix
configuration parameters. Keys not supported by the installed Postfix are
ignored.  The default is empty `{}`.

### postfix_check

```
postfix_check: false
```

This is a boolean which determines if `postfix check` is run before starting
Postfix if the configuration has changed.  The default is `true`.

### postfix_backup

```
postfix_backup: true
```

This is a boolean which determines if the role will make a single backup copy of
the configuration - for example,
`cp /etc/postfix/main.cf /etc/postfix/main.cf.backup`,
thus overwriting the previous backup, if any.  The default is `false`.  NOTE: If
you want to set this to `true`, you must also set `postfix_backup_multiple:
false` - see below.

### postfix_backup_multiple

```
postfix_backup_multiple: false
```

This is a boolean which determines if the role will make a timestamped backup copy of
the configuration - for example,
`cp /etc/postfix/main.cf /etc/postfix/main.cf.$(date -Isec)`,
thus keeping multiple backup copies.  The default is `true`.  NOTE: This setting
overrides `postfix_backup`, so you must set this to `false` if you want to use
`postfix_backup`.

## Limitations

There is no way to remove configuration parameters.  If you know all of the
configuration parameters that you want to set, you can use the `file` module to
remove `/etc/postfix/main.cf` before running this role, with `postfix_conf` set
to all of the configuration parameters you want to apply.

## Example Playbook

Install and enable postfix. Configure `relay_domains=$mydestination` and
`relayhost=example.com`.

```yaml
---
- hosts: all
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
- hosts: all
  vars:
    postfix_check: false
  roles:
    - linux-system-roles.postfix
```

Install and enable postfix. Do single backup of main.cf (older backup will be
rewritten) and configure `relayhost=example.com`:

```yaml
---
- hosts: all
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
- hosts: all
  vars:
    postfix_conf:
      relayhost: example.com
    postfix_backup_multiple: true
  roles:
    - linux-system-roles.postfix
```

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
