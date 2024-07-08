# scicore.benji_backup

Deploy benji backup using docker containers. 


# Requirements

This role assumes docker daemon is already installed in the destination host.

You also need the ansible collection `community.docker.docker_compose`.  You
can install it with `ansible-galaxy collection install community.docker`)


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

```
$1 = ceph pool
$2 = volume name

$> benji-backup volumes 29c99562-9882-481f-aecc-d5b2d104057a
```

## Restore a volume 

Before you restore a volume it's recommended to stop the destination VM using `openstack stop vm_id`

You also have to identify to which ceph pool you have to restore the volume. Details below:

### VMs booted from an image

When booting a VM from an image the root volume will be stored in ceph pool `vms`. The volume name
is in format "${vm_id}_disk" e.g. 
```
benji-backups$> sudo rbd -p vms ls
0a5f5bb5-3870-47a5-9925-934065f29bac_disk
```

### VMs booted from a volume or extra volumes attached to a VM

Openstack volumes are stored in ceph pool `volumes`. The volume name format is "${volume_id}" e.g.
```
benji-backups$> sudo rbd -p volumes ls
e30044c2-61b7-40c3-805c-26a7ece9b2fb

```

### Restore a volume 

```
$1 = benji backup uid (get it using benji-list)
$2 = destination ceph pool
$3 = volume name (this must exist in the pool and it will be overriden with the backup data)

$> benji-restore -f volumes/volume-29c99562-9882-481f-aecc-d5b2d104057a-t6ueth volumes e30044c2-61b7-40c3-825c-24a7e4ee9b2fb
```
