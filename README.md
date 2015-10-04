Role Name
=========

Ansible role to manage ssh pub keys on remote systems...allows the addition or removal of keys for remote users.

Requirements
------------

In order to use this role, existing ssh keys must exist in the location which is defined under the keys var. Otherwise, the tasks will error when ran (by design in order to bring attention to missing keys which are expected.)

Role Variables
--------------

````
---
# defaults file for ansible-manage-ssh-keys
enable_manage_ssh_keys: false  #defines if remote ssh keys should be managed
manage_ssh_keys:
  - remote_user: demo_user  #define username on remote system to add defined keys to
    present: true  #defines if ssh key should be added or removed
    keys:  #define key(s) to add to remote username
      - ssh_pub_keys/demo_user.pub
      - ssh_pub_keys/demo_user_1.pub
  - remote_user: demo_user2
    present: false
    keys:
      - ssh_pub_keys/demo_user2.pub
````

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: mrlesmithjr.manage-ssh-keys }

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
