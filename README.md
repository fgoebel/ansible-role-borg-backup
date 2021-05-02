# ansible-role-borg-backup

**Ansible role for setting up [borg-backup](https://borgbackup.readthedocs.io/).**

**This role does only installation of borgbackup, no configuration at all.**

This Role is able to install borgbackup. It was written because i wanted to use the same and most up to date version of borgbackup on multiple systems with different OS.
As the versions provided differ with each package-manager it is possible to install the binary with the same version.

(I am sorry, i do not use Alpine that much, so the binary installation does not work with Alpine at the moment. You my have a look [here] if you have an idea)

## Supported Platforms

- Alpine 3.11 (via package only!!)
- Archlinux
- CentOS 8
- Debian 9, 10
- Fedora 33
- Ubuntu 18.04, 20.04

## Requirements

Ansible 2.9 or higher is recommended.

## Variables

Variables and defaults for this role:

| variable | default value in defaults/main.yml | description |
| -------- | ---------------------------------- | ----------- |
| borg_backup_role_enabled | False | determine whether role is enabled (True) or not (False) |
| borg_force_binary_installation | False | False: packages from OS-specific manager will be used, may be more or less outdated |
| borg_binary_version | 1.1.11 | Version of binary file to use, only used when binary_installation!! |
| borg_binary_install_path | /usr/local/bin | Path to install binary at |
| borg_binary_arch | linux64 | architecture of binary to download, see [here](https://github.com/borgbackup/borg/releases) |
| borg_binary_download_url | "https://github.com/borgbackup/borg/releases/download/{{ borg_binary_version }}/borg-{{ borg_arch }}" | Path to download borgbackup binaries from |

## Binary Installation

If you want to use borg on a variety of hosts with the exact same version of borg you could use the variable

~~~ yaml
borg_force_binary_installation: True
~~~

## Dependencies

None.

## Example Playbook

This playbook will install the borgbackup package on the system!

```yaml
---
# role: ansible-role-borg-backup
# file: site.yml

- hosts: borg_backup_systems
  become: True
  vars:
    borg_backup_role_enabled: True
  roles:
    - role: ansible-role-borg-backup
```


This Playbook will install the binary in version 1.1.12 even if a package is available
```yaml
---
# role: ansible-role-borg-backup
# file: site.yml

- hosts: borg_backup_systems
  become: True
  vars:
    borg_backup_role_enabled: True
    borg_force_binary_installation: True
    borg_binary_version: 1.1.12
  roles:
    - role: ansible-role-borg-backup
```
## Ideas to Implement

- implement borg backup server configuration
- create authorized_keys entry
- implement retries
- recovery after failures
- implement logging / notifications of backup success/failures


## License and Author

- Author:: [fgoebel](https://github.com/fgoebel/)
- Copyright:: 2020, [fgoebel](https://github.com/fgoebel/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/fgoebel/ansible-role-borg-backup/blob/master/LICENSE) file in repository.

This role was created with a role-skeleton originally created by [jam82](https://github.com/jam82) and changed to suit my needs.
Thank you very much!

## References

- [ArchWiki](https://wiki.archlinux.org/)
