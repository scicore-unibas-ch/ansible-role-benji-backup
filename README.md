Role Name
=========

Deploy benji backup using docker containers. 


Requirements
------------

This role assumes docker daemon is already installed in the destination host.

Role Variables
--------------

## ceph cheatsheet

```bash
root@benji-backups:~# rbd --id benji -p volumes ls
e30044c2-61b7-40c3-805c-26a7ece9b2fb
volume-29c99562-9882-481f-aecc-d5b2d104057a
volume-e30044c2-61b7-40c3-805c-26a7ece9b2fb
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
