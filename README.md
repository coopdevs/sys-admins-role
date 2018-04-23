Sys Admins Role
=========

This role help you to mantain the system administration users.

With this role you can:

* Create a group for the system administrators to manage the permissions easy
* Create system administrator users
* Remove system administrator users
* Add `sudo` permissions to system administrator users

This role need be runned with `sudo` access.

Role Variables
--------------

> **This variables must be declared to run this role.**

The role variables are:

### `sys_admins`

A list of users. Any item need be in the next structure:

```yaml
sys_admins:
  - name: user1
    ssh_key: "~/.ssh/id_rsa.pub"
    state: present
  - name: user2
    ssh_key: "~/.ssh/id_rsa.pub"
    state: absent
``` 

System Administrators vars:

- `name`: User name
- `ssh_key`: Path of ssh key to be copied in user ssh authorized keys file.
- `state`: Choices absent or present

### `sys_admin_group`

The name of the system adnimistrators group

```yaml
sys_admin_group: sysadmin-group
``` 
Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: coopdevs.sys_admins
      sys_admin_group: sysadmin-group
      sys_admins:
       - name: sysadmin
         ssh_key: "~/.ssh/id_rsa.pub"
         state: present
```

License
-------

BSD

Author Information
------------------

Coopdevs http://coopdevs.org
