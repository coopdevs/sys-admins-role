Sys Admins Role
=========

This role help you to mantain the system administration users.

With this role you can:

* Create a group for the system administrators to manage the permissions easy
* Create system administrator users
* Remove system administrator users
* Add `sudo` permissions to system administrator users
* Add multiple ssh keys to a single system administrator user

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

The name of the system administrators group

```yaml
sys_admin_group: sysadmin-group
``` 

## Single user mode
When you are restricted to a single user, you must set the `sysadmin_multi_user` variable to `false` and set the `sysadmin_user` variable with the user name. The user must be already created on the server with root privileges.

This will iterate over the `sys_admins` list and add each user key to the authorized keys for the user defined in `sysadmin_user` variable.

This mode is disabled by default.

  ```yaml
  sysadmin_multi_user: false
  sysadmin_user: "sysadmin"
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

GPLv3

Author Information
------------------

Coopdevs http://coopdevs.org
