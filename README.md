- [Manjaro](/Manjaro/linux-notes-manjaro.md)


**Manjaro**  
*Some notes and tips that I found useful while setting up & running Manjaro.*



 
``sudo pacman -Scc``

        [eam-00@mbw ~]$ df
        Filesystem      Size  Used Avail Use% Mounted on
        dev             2,0G     0  2,0G   0% /dev
        run             2,0G  1,3M  2,0G   1% /run
        /dev/dm-0       455G  344G   89G  80% /
        tmpfs           2,0G     0  2,0G   0% /dev/shm
        tmpfs           2,0G   51M  1,9G   3% /tmp
        /dev/sda2       511M  424K  511M   1% /boot/efi
        tmpfs           392M   76K  392M   1% /run/user/1000
        [eam-00@mbw ~]$ sudo pacman -Scc
        [sudo] password for esm-00: 

        Cache directory: /var/cache/pacman/pkg/
        :: Do you want to remove ALL files from cache? [y/N] y
        removing all files from cache...

        Database directory: /var/lib/pacman/
        :: Do you want to remove unused repositories? [Y/n] y
        removing unused sync repositories...

        [eam-00@mbw ~]$ df -h
        Filesystem      Size  Used Avail Use% Mounted on
        dev             2,0G     0  2,0G   0% /dev
        run             2,0G  1,3M  2,0G   1% /run
        /dev/dm-0       455G  342G   91G  80% /
        tmpfs           2,0G     0  2,0G   0% /dev/shm
        tmpfs           2,0G   51M  1,9G   3% /tmp
        /dev/sda2       511M  424K  511M   1% /boot/efi
        tmpfs           392M   76K  392M   1% /run/user/1000
        [eam-00@mbw ~]$

- The extra "y" forces the package manager to download package database regardless of whether there is any change in the versions or not.  
This is helpful when you have a corrupted package database and you want to force a synchronization:  
``sudo pacman -Syyu``

- Update and rank the mirrorlist by speed, up to 5 mirrors:  
``sudo pacman-mirrors -f 5``

- DOT bashrc aliases:

        alias upgrade='sudo pacman -Syu'
        alias remove_lock='sudo rm /var/lib/pacman/db.lck'
        alias delete_cache='sudo pacman -Scc'
        alias list_kernels='pacman -Q linux'

- Remove stalled packages after the initial install:  
``sudo pacman -Rdd lib32-libcanberra lib32-libcanberra-gstreamer lib32-libcanberra-pulse libcanberra libcanberra-gstreamer libcanberra-pulse``  

- Enable SSH:  
``sudo systemctl status sshd.service``  
``sudo systemctl enable sshd.service``  
``sudo systemctl start sshd.service``

**Logrotate**  

Edit the file /etc/logrotate.conf

        compress
        dateext

Uncomment the 'compress' entry and add the 'dateext' one in order to have the rotated log files compresssed and the date of the rotation appended to the file name of the log.

**Make Caps Lock another Ctrl key**

Edit the file ``/etc/default/keyboard``:  

        XKBMODEL="pc105"
        XKBLAYOUT="us"
        XKBVARIANT="alt-intl
        XKBOPTIONS="ctrl:nocaps" # Some people prefer "ctrl:swapcaps"

In order for the changes to take effect (on X Window) without rebooting:

``setxkbmap -option ctrl:nocaps``

Another option, on XFCE, would be to add an entry on:

Settings > Session and Startup > Application Autostart > Add Application

Name it whatever you like, same for the description, but be sure to set the command to be:

``/usr/bin/setxkbmap -option ctrl:nocaps``

Make sure the trigger is set: On Login.
