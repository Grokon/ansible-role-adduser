# ansible-role-adduser

[![Molecule Test Status](https://github.com/Grokon/ansible-role-adduser/actions/workflows/molecule.yaml/badge.svg?branch=master)](https://github.com/Grokon/ansible-role-adduser/actions/workflows/molecule.yaml)
[![GitHub release](https://img.shields.io/github/release/Grokon/ansible-role-adduser.svg)](https://github.com/Grokon/ansible-role-adduser/releases)
[![GitHub license](https://img.shields.io/github/license/Grokon/ansible-role-adduser.svg)](https://github.com/Grokon/ansible-role-adduser/blob/master/LICENSE)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-grokon.adduser-blue.svg)](https://galaxy.ansible.com/grokon/adduser/)

## Example Playbook

```yaml
- hosts: all
  roles:
    - grokon.adduser
  vars:
    adduser__groups:
      - name: "foo"
        gid: 3001
        sudo: /usr/bin/sudo
    adduser__users:
      - name: "boo"
        groups: ["foo"]
        ssh_key: ["ssh-rsa blahblahblah"]
        shell: "/bin/bash"
        uid: 3000
        home: "/home/foo"
        system: true
```

An Ansible Role that adds users and groups on Debian

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [adduser__authorized_keys_file](#adduser__authorized_keys_file)
  - [adduser__create_homedir](#adduser__create_homedir)
  - [adduser__create_per_user_group](#adduser__create_per_user_group)
  - [adduser__default_group](#adduser__default_group)
  - [adduser__default_shell](#adduser__default_shell)
  - [adduser__delete_unmanaged](#adduser__delete_unmanaged)
  - [adduser__docker_group](#adduser__docker_group)
  - [adduser__group](#adduser__group)
  - [adduser__groups](#adduser__groups)
  - [adduser__remove_home](#adduser__remove_home)
  - [adduser__stats_file_path](#adduser__stats_file_path)
  - [adduser__user_stats_file](#adduser__user_stats_file)
  - [adduser__users](#adduser__users)
- [Discovered Tags](#discovered-tags)
- [Open Tasks](#open-tasks)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.19`

## Default Variables

### adduser__authorized_keys_file

The file to store authorized keys in

#### Default value

```YAML
adduser__authorized_keys_file: .ssh/authorized_keys
```

### adduser__create_homedir

Create home dirs for new users? Set this to false if you manage home directories in some other way.

#### Default value

```YAML
adduser__create_homedir: true
```

### adduser__create_per_user_group

Create a group for every user and make that their primary group

#### Default value

```YAML
adduser__create_per_user_group: true
```

### adduser__default_group

#### Default value

```YAML
adduser__default_group: users
```

### adduser__default_shell

The default shell for a user if none is specified

#### Default value

```YAML
adduser__default_shell: /bin/bash
```

### adduser__delete_unmanaged

Delete users and groups that are not managed by ansible

#### Default value

```YAML
adduser__delete_unmanaged: true
```

### adduser__docker_group

The group to add users to docker group is docker is installed and this is set to true

#### Default value

```YAML
adduser__docker_group: docker
```

### adduser__group

If we're not creating a per-user group, then this is the group all users belong to

### adduser__groups

List of groups to create

#### Default value

```YAML
adduser__groups: []
```

#### Example usage

```YAML
adduser__groups_to_create:
  - name: "foo"
    gid: 1000
  - name: "bar"
    gid: 1001
```

### adduser__remove_home

Delete the home directory of a user when the user is removed?

#### Default value

```YAML
adduser__remove_home: false
```

### adduser__stats_file_path

#### Default value

```YAML
adduser__stats_file_path: ~/.ansible
```

### adduser__user_stats_file

The file to store user stats in

### adduser__users

List of users to create

#### Default value

```YAML
adduser__users: []
```

#### Example usage

```YAML
adduser__users:
  - name: "foo"
    group: ["foo", "bar"]
    ssh_key: ['ssh-rsa blahblahblah']
    shell: "/bin/bash"
    uid: 1000
    home: "/home/foo"
    is_system_user: true
    docker_group: true
```

## Discovered Tags

**_adduser_**

**_groups_**

**_users_**

## Open Tasks


## Dependencies

None.

## License

MIT

## Author

grokon
