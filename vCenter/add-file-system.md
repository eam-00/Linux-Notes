# Add A File System to LVM

- Add the new drive thru vCenter:  
1. Search for the server on which you are adding the drive  
2. Right click on the server from the inventory  
3. Select "*Edit Settings*"  
4. Add New Device > Select > Hard Disk  
5. The new HDD will be of 16 GB of size (Unless otherwise specified)
- On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan; done``

In order to re-scan the drives, so you can avoid rebooting the virtual server to actually be able to "see" the newly added drive. 
Issue a:  

    fdisk -l /dev/sd* | grep -i 'Disk'

To get the correct Hard Disk (this one has 16 GB).
Use fdisk to create the disk partition table on the new disk:  

    fdisk /dev/sde

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

    t 
    8e
    w

And now there is a ``/dev/sde1`` drive on the server.  
To list the drives issue a ``fdisk -l``:

    ~snip~
    Disk /dev/mapper/vg01-lv_test: 16 GiB, 17179860388 bytes, 12582912 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512
    ~snip~

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

Use ``lvcreate`` to create a logical volume in the already existing volume group:  

``lvcreate -l 100%FREE -n lv_test vg01``  

Format the newly added drive:  

    [root@server ~]# mkfs.xfs /dev/mapper/vg01-lv_test
    meta-data=/dev/mapper/vg01-lv_test isize=256    acount=4, agsize=1048320 blks
             =                          sectsz=512  attr=2, projid32bit=1
             =                          crc=0       finobt=0
    data     =                          bsize=4096  blocks=4193280, imaxpct=25
             =                          sunit=0     swidth=0 blks
    naming   =version 2                 bsize=4096  ascii-ci=0  ftype=0
    log      =internal log              bsize=4096  blocks=2560,    version=2
             =                          sectsz=512  sunit=0 blks,   lazy-count=1
    realtime =none                      extsz=4096  blocks=0, rtextents=0

Create the directory where the new file system will be mounted:

    mkdir /opt/test

Edit the ``/etc/fstab`` file to add the newly created file system and mount point  

    emacs /etc/fstab

Mount the file system:  

    mount /dev/vg01/lv_test /opt/test

Check that you can access it and write onto it.  
Unmount it and -if you can- reboot the server to test the automount of the different file systems.

    umount /opt/test

If you can't reboot the server, issue a:

    mount -a

To test if the mount, getting the info from the ``/etc/fstab`` file, goes smooth.
