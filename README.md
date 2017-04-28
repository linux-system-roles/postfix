postfix
=======

This role can install, configure and start Postfix MTA.


Role Variables
--------------

This role provides Postfix configuration dictionary 'postfix_conf' which can
hold key/value pairs of all supported Postfix configuration parameters. Keys
not supported by the installed Postfix are ignored.


Example Playbook
-----------------

Install and enable postfix. Configure "relay_domains=$mydestination" and

```
---
- hosts: all
  vars:
    postfix_conf:
      relay_domains: "$mydestination"
      relay_host: "example.com"
  roles:
    - postfix
```

Install and enable postfix. Do not run 'postfix check' before restarting
postfix:

```
---
- hosts: all
  vars:
    postfix_check: false
  roles:
    - postfix
```

Install and enable postfix. Do single backup of main.cf (older backup will be
rewritten) and configure "relay_host=example.com":

```
---
- hosts: all
  vars:
    postfix_conf:
      relay_host: "example.com"
    postfix_backup: true
  roles:
    - postfix
```

Install and enable postfix. Do timestamped backup of main.cf and
configure "relay_host=example.com" (if postfix_backup_multiple is
set to true postfix_backup is ignored):

```
---
- hosts: all
  vars:
    postfix_conf:
      relay_host: "example.com"
    postfix_backup_multiple: true
  roles:
    - postfix
```


License
-------

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
