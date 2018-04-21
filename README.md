Role Name
=========

This role help you to mantain the system administration users.

With this role you can:

* Create a group
* Create system administrator users
* Remove system administrator users
* Add `sudo` permissions to system administrator users

This role need be runned with `sudo` access.

Role Variables
--------------

You need declare a `sys_admins` list with the next structure:

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

* `name`: User name
* `ssh_key`: Path of ssh key to be copied in user ssh authorized keys file.
* `state`: Choices absent or present

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: coopdevs.sys_admins
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
