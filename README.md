- [Manjaro](/Manjaro/linux-notes-manjaro.md)


**Manjaro**  
*Some notes and tips that I found useful while setting up & running Manjaro.*



 

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
