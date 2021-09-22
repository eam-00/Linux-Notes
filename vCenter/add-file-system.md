# Add A File System to LVM

- Add the new drive thru vCenter:  
1. Search for the server on which you are adding the drive  
2. Right click on the server from the inventory  
3. Select Edit Settings  
4. Add New Device > Select > Hard Disk  
- On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan ; done``

Use fdisk to create the disk partition table:  

``fdisk /dev/sde``  

Select the defaults and then:  

``t``  
``8e``  
``w``  

And now there is a ``/dev/sde1``.  
Use ``pvcreate`` to initialize the volume so it can be used by LVM.  

pvcreate /dev/sde1  

The LVM volume already exists, so use ``vgextend`` otherwise use ``vgcreate``  
``vgextend vg01 /dev/sde1``

``lvcreate -l 100%FREE -n lv_test vg01``  
mkfs.xfs /dev/mapper/vg01-lv_test
mkdir /opt/test
vi /etc/fstab
mount /dev/vg01/lv_test /opt/test
umount /opt/test
mount -a
