# ansible-role-borg-backup

**Ansible role for setting up borg-backup.**

## Supported Platforms

- Alpine 3.11
- Archlinux
- CentOS 8
- Debian 9, 10
- Fedora 31
- Ubuntu 18.04, 20.04

## Requirements

Ansible 2.9 or higher is recommended.

## Variables

Variables and defaults for this role:

| variable | default value in defaults/main.yml | description |
| -------- | ---------------------------------- | ----------- |
| borg_backup_role_enabled | False | determine whether role is enabled (True) or not (False) |

## Dependencies

None.

## Example Playbook

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

## License and Author

- Author:: [fgoebel](https://github.com/fgoebel/)
- Copyright:: 2020, [fgoebel](https://github.com/fgoebel/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/fgoebel/ansible-role-borg-backup/blob/master/LICENSE) file in repository.

This role was created with a role-skeleton originally created by [jam82](https://github.com/jam82) and changed to suit my needs.
Thank you very much!

## References

- [ArchWiki](https://wiki.archlinux.org/)
