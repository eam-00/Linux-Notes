# Add A File System

- Add the new drive thru vCenter:  
Search for the sevrer on to add the drive  
Right click on the server from the inventory  
Select Edit Settings  
Add New Device > Select > Hard Disk  
- On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan ; done``

fdisk /dev/sde
pvcreate /dev/sde1
vgextend vg01 /dev/sde1
lvcreate -l 100%FREE -n lv_test vg01
mkfs.xfs /dev/mapper/vg01-lv_test
mkdir /opt/test
vi /etc/fstab


