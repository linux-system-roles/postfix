Changelog
=========

[1.2.4] - 2022-07-19
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- make min_ansible_version a string in meta/main.yml (#48)

The Ansible developers say that `min_ansible_version` in meta/main.yml
must be a `string` value like `"2.9"`, not a `float` value like `2.9`.

- Add CHANGELOG.md (#49)

[1.2.3] - 2022-05-06
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- bump tox-lsr version to 2.11.0; remove py37; add py310

[1.2.2] - 2022-04-25
--------------------

### New Features

- none

### Bug Fixes

- fix ansible-lint issues

### Other Changes

- none

[1.2.1] - 2022-04-19
--------------------

### New Features

- support gather\_facts: false; support setup-snapshot.yml

### Bug Fixes

- none

### Other Changes

- none

[1.2.0] - 2022-02-24
--------------------

### New Features

- Remove outdated ansible managed header and use {{ ansible\_managed | comment }}
- Add "previous: replaced" functionality to postfix\_conf dict to reset postfix configuration

### Bug Fixes

- Fix some issues in the role, more info in commits

### Other Changes

- bump tox-lsr version to 2.10.1

[1.1.3] - 2022-01-10
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- bump tox-lsr version to 2.8.3
- change recursive role symlink to individual role dir symlinks

[1.1.2] - 2021-11-08
--------------------

### New Features

- support python 39, ansible-core 2.12, ansible-plugin-scan

### Bug Fixes

- none

### Other Changes

- update tox-lsr version to 2.7.1

[1.1.1] - 2021-09-13
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- use tox-lsr version 2.5.1
- use apt-get install -y

[1.1.0] - 2021-08-10
--------------------

### New Features

- Drop support for Ansible 2.8 by bumping the Ansible version to 2.9

### Bug Fixes

- none

### Other Changes

- Clean up Ansible 2.8 CI configuration entries

[1.0.0] - 2021-05-25
--------------------

### Initial Release
