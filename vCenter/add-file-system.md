# Add A File System

Add the new drive thur vCenter.  
On the server run:

``ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/$host/scan ; done``


