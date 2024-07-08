# scicore.benji_backup

Deploy benji backup using docker containers. 


# Requirements

This role assumes docker daemon is already installed in the destination host.


# Some examples

All the examples are executed in the host running the docker daemon (outside the container)

## List volumes in a ceph pool

This assumes the ceph client is "benji"

```bash
benji-backups$> sudo rbd --id benji -p volumes ls
volume-29c99562-9882-481f-aecc-d5b2d104057a
volume-e30044c2-61b7-40c3-805c-26a7ece9b2fb
```
## Backup a volume from pool "volumes"

`$> benji-backup volumes volume-29c99562-9882-481f-aecc-d5b2d104057a`
