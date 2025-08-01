Changelog
=========

[1.6.4] - 2025-08-01
--------------------

### Other Changes

- test: tag tests::reboot for tests_disable_ipv6.yml (#191)

[1.6.3] - 2025-07-24
--------------------

### Other Changes

- test: accept empty relayhost as unset (#189)

[1.6.2] - 2025-07-15
--------------------

### Bug Fixes

- fix: configure postfix to listen only to IPv4 if IPv6 is disabled (#187)

[1.6.1] - 2025-07-09
--------------------

### Other Changes

- ci: ansible-plugin-scan is disabled for now (#168)
- ci: bump ansible-lint to v25; provide collection requirements for ansible-lint (#171)
- ci: Check spelling with codespell (#172)
- ci: Add test plan that runs CI tests and customize it for each role (#173)
- ci: In test plans, prefix all relate variables with SR_ (#174)
- ci: Fix bug with ARTIFACTS_URL after prefixing with SR_ (#175)
- ci: several changes related to new qemu test, ansible-lint, python versions, ubuntu versions (#176)
- ci: use tox-lsr 3.6.0; improve qemu test logging (#177)
- ci: skip storage scsi, nvme tests in github qemu ci (#178)
- ci: Bump sclorg/testing-farm-as-github-action from 3 to 4 (#179)
- ci: bump tox-lsr to 3.8.0; rename qemu/kvm tests (#180)
- ci: Add Fedora 42; use tox-lsr 3.9.0; use lsr-report-errors for qemu tests (#181)
- ci: Add support for bootc end-to-end validation tests (#182)
- ci: Use ansible 2.19 for fedora 42 testing; support python 3.13 (#183)
- refactor: support ansible 2.19 (#184)

[1.6.0] - 2024-12-04
--------------------

### New Features

- feat: support postfix_default_database_type (#165)

### Other Changes

- ci: Use Fedora 41, drop Fedora 39 (#164)
- ci: Use Fedora 41, drop Fedora 39 - part two (#166)

[1.5.2] - 2024-10-30
--------------------

### Other Changes

- ci: Improvements to tmt workflows (#144)
- ci: Fix quotes in citest_bad workflow (#145)
- ci: Fix getting github author_association (#146)
- ci: Fix url to linux-system-roles/tft-tests (#147)
- ci: Improve citest_bad script (#149)
- ci: Fix missing slash in ARTIFACTS_URL (#152)
- ci: Add tags to TF workflow, allow more [citest bad] formats (#154)
- ci: ansible-test action now requires ansible-core version (#157)
- ci: add YAML header to github action workflow files (#158)
- refactor: Use vars/RedHat_N.yml symlink for CentOS, Rocky, Alma wherever possible (#160)

[1.5.1] - 2024-08-01
--------------------

### Other Changes

- ci: Add tft plan and workflow (#136)
- ci: Update fmf plan to add a separate job to prepare managed nodes (#139)
- test: el10 now uses lmdb by default (#140)
- ci: Bump sclorg/testing-farm-as-github-action from 2 to 3 (#141)
- ci: Add workflow for ci_test bad, use remote fmf plan (#142)

[1.5.0] - 2024-07-15
--------------------

### New Features

- feat: Added postfix_files feature as a simple means to add extra files/maps to config (#129)

### Bug Fixes

- fix: add support for EL10 (#134)

### Other Changes

- ci: ansible-lint action now requires absolute directory (#133)

[1.4.5] - 2024-06-11
--------------------

### Bug Fixes

- fix: Reflect smtp-submission service rename in EL 10 and Fedora 40+ (#131)

### Other Changes

- refactor: Modify backup task to use the 'copy' module instead of 'shell' (#2)
- ci: use tox-lsr 3.3.0 which uses ansible-test 2.17 (#124)
- ci: tox-lsr 3.4.0 - fix py27 tests; move other checks to py310 (#126)
- ci: Add supported_ansible_also to .ansible-lint (#127)

[1.4.4] - 2024-04-04
--------------------

### Other Changes

- ci: fix python unit test - copy pytest config to tests/unit (#120)
- ci: Bump ansible/ansible-lint from 6 to 24 (#121)
- ci: Bump mathieudutour/github-tag-action from 6.1 to 6.2 (#122)

[1.4.3] - 2024-01-16
--------------------

### Other Changes

- ci: support ansible-lint and ansible-test 2.16 (#117)
- ci: Use supported ansible-lint action; run ansible-lint against the collection (#118)

[1.4.2] - 2023-12-08
--------------------

### Other Changes

- ci: bump actions/github-script from 6 to 7 (#114)
- refactor: get_ostree_data.sh use env shebang - remove from .sanity* (#115)

[1.4.1] - 2023-11-29
--------------------

### Other Changes

- refactor: improve support for ostree systems (#112)

[1.4.0] - 2023-11-06
--------------------

### New Features

- feat: support for ostree systems (#110)

### Other Changes

- Bump actions/checkout from 3 to 4 (#102)
- ci: ensure dependabot git commit message conforms to commitlint (#105)
- ci: use dump_packages.py callback to get packages used by role (#107)
- ci: tox-lsr version 3.1.1 (#109)

[1.3.9] - 2023-09-08
--------------------

### Other Changes

- ci: Add markdownlint, test_converting_readme, and build_docs workflows (#98)

  - markdownlint runs against README.md to avoid any issues with
    converting it to HTML
  - test_converting_readme converts README.md > HTML and uploads this test
    artifact to ensure that conversion works fine
  - build_docs converts README.md > HTML and pushes the result to the
    docs branch to publish dosc to GitHub pages site.
  - Fix markdown issues in README.md
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

- docs: Make badges consistent, run markdownlint on all .md files (#99)

  - Consistently generate badges for GH workflows in README RHELPLAN-146921
  - Run markdownlint on all .md files
  - Add custom-woke-action if not used already
  - Rename woke action to Woke for a pretty badge
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

- ci: Remove badges from README.md prior to converting to HTML (#100)

  - Remove thematic break after badges
  - Remove badges from README.md prior to converting to HTML
  
  Signed-off-by: Sergei Petrosian <spetrosi@redhat.com>

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
