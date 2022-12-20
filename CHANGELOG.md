# Changelog

All notable changes to this project will be documented in this file.

- [1.2.1 (2022-12-20)](#121-2022-12-20)
- [1.2.0 (2022-12-17)](#120-2022-12-17)
- [1.1.0 (2022-01-28)](#110-2022-01-28)
- [1.0.0 (2021-10-11)](#100-2021-10-11)

---

<a name="1.2.1"></a>
## [1.2.1](https://github.com/aisbergg/ansible-role-networkmanager/compare/v1.2.0...v1.2.1) (2022-12-20)

### Chores

- ignore lint
- change lint config


<a name="1.2.0"></a>
## [1.2.0](https://github.com/aisbergg/ansible-role-networkmanager/compare/v1.1.0...v1.2.0) (2022-12-17)

### CI Configuration

- add branch explicitly to make Ansible import action happy
- bump Ansible Galaxy action version

### Chores

- don't use bump2version to include the CHANGELOG in the bump commit, it doesn't do a good job

### Documentation

- update README

### Features

- include more nmcli options (e.g. wireguard) and add tox+molecule testing


<a name="1.1.0"></a>
## [1.1.0](https://github.com/aisbergg/ansible-role-networkmanager/compare/v1.0.0...v1.1.0) (2022-01-28)

### Bug Fixes

- add generator type to 'list' test

### CI Configuration

- fix automatic release and publish process

### Chores

- include changelog in bump commits
- change issue tracker URL to lower case

### Documentation

- **README.md:** update README


<a name="1.0.0"></a>
## [1.0.0]() (2021-10-11)

Initial Release
