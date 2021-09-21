# Add A File System

- Add the new drive thur vCenter.  
- On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan ; done``

fdisk /dev/sde
pvcreate /dev/sde1
vgextend vg01 /dev/sde1
lvcreate -l 100%FREE -n lv_test vg01
mkfs.xfs /dev/mapper/vg01-lv_test
mkdir /opt/test
vi /etc/fstab


