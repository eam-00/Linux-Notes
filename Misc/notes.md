## Setup tmpfs on /etc/fstab

Setup /tmp as tmpfs (on RAM) and other miscelaneous flags for the root / partition.  
Setting /tmp on RAM as well as the options for / reduce the writes on SSD, extending its file span.

     # <file system>                                 <mount point>   <type>	<options>				<dump>	<pass> 
     /dev/mapper/hpenvy--vg-root                     /               ext4    relatime,discard,errors=remount-ro      0       1
     UUID=eded2f34-69eb-450e-b6a7-7930a3ca1046       /boot           ext2    defaults                                0       2
     tmpfs                                           /tmp            tmpfs   defaults,noatime,mode=1777              0       0
     /dev/mapper/cryptswap1                          none            swap    sw                                      0       0

After editing the ``/etc/fstab`` file, issue a:

     mount -a

To force a re-read of the file.

## Install Chrome

     sudo su -
     echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/chrome.list
     wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
     
Run an apt update:

     apt-get update
