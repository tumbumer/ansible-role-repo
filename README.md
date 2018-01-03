# tumbumer.soft

Manage software.

## Requirements

None.

## Role Variables

var | default | choices | description
---|---|---|---
tumbumer_soft_country | | us, de, ru, etc. | Country code for mirror site, if not set then nothing happens
tumbumer_soft_standard_packages | | | Comma separated package list for install from standart repos
tumbumer_soft_additional_keys | | | Additional repository key list
tumbumer_soft_additional_keys.url | | | Key url
tumbumer_soft_additional_keys.id | | | Key id
tumbumer_soft_additional_repos | | | Additional repositories list located at `/etc/apt/sources.list.d/`
tumbumer_soft_additional_repos.filename | | | Repository file name without ".list"
tumbumer_soft_additional_repos.repo | | | Repo line
tumbumer_soft_additional_packages | | | Comma separated package list for install from additional repos

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: all
  vars:
  - tumbumer_soft_country: ru
  - tumbumer_soft_standard_packages: bash-completion,screenfetch,apt-transport-https
  - tumbumer_soft_additional_keys:
    - url: https://apt.dockerproject.org/gpg
      id: 58118E89F3A912897C070ADBF76221572C52609D
  - tumbumer_soft_additional_repos:
    - filename: docker
      repo: "deb https://apt.dockerproject.org/repo {{ ansible_distribution | lower }}-{{ ansible_distribution_release }} main"
  - tumbumer_soft_additional_packages: docker-engine
  roles:
  - tumbumer.soft
```

## License

Apache-2.0

## Author Information

Denis Dvoretskov aka tumbumer <denis@tumbum.com>
