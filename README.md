jenkins-slave role
==================
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-jenkins-slave/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-jenkins-slave.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-jenkins-slave)

## Summary

This role sets up a new jenkins slave node and adds it to the jenkins master.

## Requirements

- Version of the ansible for installation: 2.5
- **Supported OS**
  - EL
    - 7
  - Ubuntu
    - bionic
  - Windows
    - 10

## Dependencies

Java 8 - either a Java Runtime Environment (JRE) or a Java Development Kit (JDK).

## Role Variables

- required
  - `master_username`
  Jenkins master CLI user name. Default value is `admin`.
  - `master_password`
  Jenkins master CLI user password. Default value is `admin`.
  - `master_host`
  FQDN name or IP address of the jenkins master host. Default value is `{{ ansible_host }}`.
  - `master_port`
  Jenkins master http port. Default value is `8080`.

- general defaults
See defaults/main.yml
## Example Playbook

```yaml
- name: "Install jenkins-slave on remote hosts using default 'Username with password' credentials"
  hosts: slave

  vars:
    master_host: master.example.com

  roles:
    - role: drewbarrett.jenkins_slave
```

```yaml
- name: "Install jenkins-slave on remote hosts using created 'Username with password' credentials"
  hosts: one_slave

  vars:
    master_host: master.example.com
    slave_linux_jenkins_cred_id: new_cred
    slave_linux_jenkins_username: new_user
    slave_linux_jenkins_password: new_password
    slave_agent_name: new_linux_slave

  roles:
    - role: drewbarrett.jenkins_slave
```

```yaml
- name: "Install jenkins-slave on remote hosts using created 'SSH Username with private key' credentials"
  hosts: many_slaves

  vars:
    master_host: master.example.com
    slave_linux_jenkins_cred_id: new_cred
    slave_linux_jenkins_username: new_user
    slave_linux_jenkins_public_key:
Nck6x4HPrsdfkjhwhf98239hfoijhpowifnYXRXAW1GYGC3lsq7FpWjCeN8wT5QzRsblTh6HZKqh96K3Jj6kpob8ykjhsdkfjhskdfuhksdjfhksjdfhksfjhhkjhUHKUHDKFksjdfhkjshdfXPlx2xSUINDsH2IACLjIrxSAppxITzR7fHZyLmkjsdhfkuwhe98237982fhksdfhksdfhkuhCmcvH6fdVtozo42lXt4QgKytGtiuGAT+lN+uJ4LVGOq32WiEbYKbc7WE7N

  roles:
    - role: drewbarrett.jenkins_slave
```

## Inventory example
    [master]
    master.example.com

    [one_slave]
    slave.example.com

    [many_slaves]
    slave1.example.com
    slave2.example.com

## Install jenkins-slave role

```bash
$ ansible-playbook playbook.yml -i inventory
```

## License

Apache

## Author Information

authors:
  - Lean Delivery Team <team@lean-delivery.com>
