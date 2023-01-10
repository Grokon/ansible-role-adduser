# ansible-role-adduser

[![Mocelule Test Status](https://github.com/Grokon/ansible-role-adduser/actions/workflows/molecule.yaml/badge.svg?branch=master)](https://github.com/Grokon/ansible-role-adduser/actions/workflows/molecule.yaml)
[![GitHub release](https://img.shields.io/github/release/Grokon/ansible-role-adduser.svg)](https://github.com/Grokon/ansible-role-adduser/release)
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
