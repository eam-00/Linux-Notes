# Manjaro

## Commands, tips and notes that I found useful while setting up and running Manjaro

- Fix “Unable to lock database” error:  
``sudo rm /var/lib/pacman/db.lck``

- The Plain Vanilla Update:  
``sudo pacman -Syu``

- Remove cache packages:  
``sudo pacman -Sc``

- Remove all files from the cache, use the clean switch twice.\
This is the most aggressive approach and it will leave nothing in the cache directory:  
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

- DOT bashrc aliases that are Manjaro specific:

        alias upgrade='sudo pacman -Syu'
        alias remove_lock='sudo rm /var/lib/pacman/db.lck'
        alias delete_cache='sudo pacman -Scc'
        alias list_kernels='pacman -Q linux'
        
- Remove stalled packages after the initial install:  
``sudo pacman -Rdd lib32-libcanberra lib32-libcanberra-gstreamer lib32-libcanberra-pulse libcanberra libcanberra-gstreamer libcanberra-pulse``  

- Enable the SSH server:  
``sudo systemctl enable sshd.service``  
``sudo systemctl start sshd.service``  
``sudo systemctl status sshd.service``  

- Install Google Chrome:  
``sudo pamac install google-chrome``

``/etc/systemd/system/swap_opt_cmd.service``

```
[Unit]
Description=Swap Opt Command Key

[Service]
ExecStart=/usr/bin/swap_opt_cmd.sh

[Install]
WantedBy=multi-user.target
```

  chmod 0644 /etc/systemd/system/swap_opt_cmd.service
  systemctl enable swap_opt_cmd.service

-----------------------------

#!/bin/bash
echo "1" > /sys/module/hid_apple/parameters/swap_opt_cmd

chmod +x /usr/bin/swap_opt_cmd.sh

=============================

``/etc/systemd/system/set_swappines.service``

[Unit]
Description=Set Swappiness

[Service]
ExecStart=/usr/bin/set_swappines.sh

[Install]
WantedBy=multi-user.target

  chmod 0644 /etc/systemd/system/set_swappines.service
  systemctl enable set_swappines.service

-----------------------------

#!/bin/bash
/usr/bin/sysctl -w vm.swappiness=5
chmod +x /usr/bin/set_swappines.sh

=============================

/etc/systemd/system/my_suspend.service

[Unit]
Description=Enable Suspend

[Service]
ExecStart=/usr/bin/my_suspend.sh

[Install]
WantedBy=multi-user.target

  chmod 0644 /etc/systemd/system/my_suspend.service
  systemctl enable my_suspend.service

-----------------------------

nano /usr/bin/my_suspend.sh
