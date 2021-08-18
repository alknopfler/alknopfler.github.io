---
title: "Improve the Libvirt Performance"
date: "2021-08-18"
categories: 
  - "libvirt"
  - "performance"
  - "faster"
tags: 
  - "libvirt"
  - "performance"
  - "faster"
  - "improvement"
---

## The Problem: 

When you're using having performance issues with libvirt, you can try this to improve it.
The idea is use an specific configuration to improve the performance. 
This configuration is the creation of a new volume mounted in the /var/lib/libvirt/images directory.

It's possible to use the same root volume for all the images, but it's not recommended due to a performance issues.

## The Solution: 

```shell
dev="nvme0n1"  # The device to use
vg="vg1"      
lv="lv1"
mountpoint="/var/lib/libvirt/images" 

pvcreate /dev/$dev                 # Create the physical volume
vgcreate $vg /dev/$(basename $dev) # Create the volume group
lvcreate -l 100%FREE -n $lv $vg    # 100% of the free space
mkfs.xfs /dev/$vg/$lv              # Create the filesystem


echo "/dev/$vg/$lv $mountpoint                    xfs    defaults        0 0" >> /etc/fstab
mount -a
```

With this improvement, the performance will be improved.

### Referecence
Thanks to [Karim](https://github.com/karmab) to share with me!!!
