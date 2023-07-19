Changelog
=========

[1.3.8] - 2023-07-19
--------------------

### Bug Fixes

- fix: facts being gathered unnecessarily (#96)

### Other Changes

- ci: Add pull request template and run commitlint on PR title only (#93)
- ci: Rename commitlint to PR title Lint, echo PR titles from env var (#94)
- ci: ansible-lint - ignore var-naming[no-role-prefix] (#95)

[1.3.7] - 2023-05-26
--------------------

### Other Changes

- docs: Consistent contributing.md for all roles - allow role specific contributing.md section
- docs: add Collection requirements section to README
- docs: Update an outdated limitation and mention previous: replaced

[1.3.6] - 2023-04-27
--------------------

### Other Changes

- test: check generated files for ansible_managed, fingerprint
- ci: Add commitlint GitHub action to ensure conventional commits with feedback

[1.3.5] - 2023-04-13
--------------------

### Other Changes

- ansible-lint - use changed_when for conditional tasks (#81)

[1.3.4] - 2023-04-06
--------------------

### Other Changes

- Add README-ansible.md to refer Ansible intro page on linux-system-roles.github.io (#78)
- Fingerprint RHEL System Role managed config files (#79)

[1.3.3] - 2023-01-23
--------------------

### New Features

- none

### Bug Fixes

- fix issues with jinja, ansible-lint (#70)

### Other Changes

- none

[1.3.2] - 2023-01-20
--------------------

### New Features

- none

### Bug Fixes

- ansible-lint 6.x fixes (#65)

### Other Changes

- Add check for non-inclusive language (#64)
- cleanup non-inclusive words.

[1.3.1] - 2022-11-14
--------------------

### New Features

- none

### Bug Fixes

- none

### Other Changes

- ansible-core 2.14 support (#58)

Make the role work with ansible-core 2.14
clean up ansible-lint 6.x issues

[1.3.0] - 2022-11-01
--------------------

### New Features

- Use the firewall role and the selinux role from the postfix role (#56)

- Introduce postfix_manage_firewall to use the firewall role to
  manage the smtp services.
  Default to false - means the firewall role is not used.

- Introduce postfix_manage_selinux to use the selinux role to
  manage the ports in the smtp services.
  Assign smtp_port_t to the smtp service ports.
  Default to false - means the selinux role is not used.

- Add the test check task tasks/check_firewall_selinux.yml for
  verify the ports status.

- Add meta/collection-requirements.yml.

### Bug Fixes

- none

### Other Changes

- none

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
