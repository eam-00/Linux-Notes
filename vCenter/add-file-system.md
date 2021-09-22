# Add A File System to LVM

- Add the new drive thru vCenter:  
1. Search for the server on which you are adding the drive  
2. Right click on the server from the inventory  
3. Select Edit Settings  
4. Add New Device > Select > Hard Disk  
5. The new HDD will be of 16 GB of size
- On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan ; done``

Use fdisk to create the disk partition table on the newly added disk:  

``fdisk /dev/sde``  

Select the defaults:

    Command (m for help): n
    Partition type:
      p  primary (0 primary, 0 extended, 4 free)
      e  extended
    Select (default p):
    Using default response p
    Partition number (1-4, default 1):
    First sector (2048-33554431, default 2048):
    Using default value 2048
    Last sector, +sectors or +size{K,M,G} (2048-33554431, default 33554431):
    Using default value 33554431
    Partition 1 of type Linux and of size 16 GB is set

and then issue:  

``t``  
``8e``  
``w``  

And now there is a ``/dev/sde1`` drive.  
Use ``pvcreate`` to initialize the volume so it can be used by LVM.  

``pvcreate /dev/sde1``  

Use ``pvs`` to show information about the physical volumes:  

    [root@server ~]# pvs
    PV          VG      Fmt     Attr    PSize   Pfree
    /dev/sda2   rhel    lvm2    a--     39.51g  0
    /dev/sdb1   vg01    lvm2    a--     10.00g  0
    /dev/sdc1   vg01    lvm2    a--    200.00g  0    
    /dev/sdd1   vg01    lvm2    a--     50.00g  0    
    /dev/sde1   vg01    lvm2    a--     16.00g  16.00g   

The new drive doesn't have any disk space alloted yet, it shows the whole 16 GB as free.  
The LVM volume already exists, so use ``vgextend`` otherwise use ``vgcreate``  

    [root@server ~]# vgextend vg01 /dev/sde1
     Volume group "vg01" successfully extended

``lvcreate -l 100%FREE -n lv_test vg01``  

Format the newly added drive:  

``mkfs.xfs /dev/mapper/vg01-lv_test``
mkdir /opt/test
vi /etc/fstab
mount /dev/vg01/lv_test /opt/test
umount /opt/test
mount -a
