# Add A File System

ls /sys/class/scsi_host/ | while read host ; do echo "- - - " > /sys/class/scsi_host/scan ; done
