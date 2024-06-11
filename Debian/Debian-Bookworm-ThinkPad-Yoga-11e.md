# Debian Bookworm on the ThinkPad Yoga 11e

## Model
```
20D90027US
```
## GNOME install

The GNOME installer options:

![Installer options](https://github.com/eam-00/Linux-Notes/blob/main/Debian/Debian-Bookworm-ThinkPad-Yoga-11e-Pics/tasksel_first_0.png?raw=true)

Disk usage:
```
epsilon-alpha-mu@11e:~$ df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      3.9G     0  3.9G   0% /dev
tmpfs                     783M  1.9M  781M   1% /run
/dev/mapper/11e--vg-root   27G  5.5G   20G  22% /
tmpfs                     3.9G     0  3.9G   0% /dev/shm
tmpfs                     5.0M   12K  5.0M   1% /run/lock
/dev/sda2                 456M  102M  330M  24% /boot
/dev/nvme0n1p1            256M   41M  216M  16% /boot/efi
tmpfs                     783M   80K  783M   1% /run/user/1000
epsilon-alpha-mu@11e:~$ 
```
Number of packages installed:
```
root@11e:~$ pfetch 
  _____      epsilon-alpha-mu@11e
 /  __ \     os     Debian GNU/Linux 12 (bookworm)
|  /    |    host   20SES0M800 ThinkPad 11e Yoga Gen 6
|  \___-     kernel 6.1.0-20-amd64
-_           uptime 18m
  --_        pkgs   1600
             memory 1025M / 7827M
```
*Note:*  
The laptop touch screen works OK even during the installation.

