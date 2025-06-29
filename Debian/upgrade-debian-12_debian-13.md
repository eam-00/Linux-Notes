

**Debian 12 to Debian 13**

Right after the Debian 12 netinstall with only the "*SSH Server*" option enabled:

275 packages installed:
```
root@t43:/etc/apt# pfetch 
  _____      os     Debian GNU/Linux 12 (bookworm)
 /  __ \     host   2669C8U ThinkPad T43
|  /    |    kernel 6.1.0-37-686-pae
|  \___-     uptime 19m
-_           pkgs   275
  --_        memory 109M / 2010M
```
```
root@t43:/etc/apt# df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      985M     0  985M   0% /dev
tmpfs                     202M  820K  201M   1% /run
/dev/mapper/t43--vg-root   72G  1.2G   67G   2% /
tmpfs                    1006M     0 1006M   0% /dev/shm
tmpfs                     5.0M     0  5.0M   0% /run/lock
/dev/sda1                 455M  105M  326M  25% /boot
tmpfs                     202M     0  202M   0% /run/user/0
tmpfs                     202M     0  202M   0% /run/user/1000
root@t43:/etc/apt# 
```

cd /etc/apt
cp sources.list sources.list.ORIG
apt-get update && apt-get dist-upgrade --autoremove -y
sed -i 's/bookworm/trixie/g' /etc/apt/sources.list
sudo apt-get update
apt-get dist-upgrade --autoremove -y
reboot

After switching to Trixie:

epsilon-alpha-mu@t43:~$ df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      983M     0  983M   0% /dev
tmpfs                     202M  792K  201M   1% /run
/dev/mapper/t43--vg-root   72G  1.6G   67G   3% /
tmpfs                    1006M     0 1006M   0% /dev/shm
tmpfs                     5.0M     0  5.0M   0% /run/lock
tmpfs                    1006M     0 1006M   0% /tmp
/dev/sda1                 455M  109M  322M  26% /boot
tmpfs                     202M  8.0K  202M   1% /run/user/1000
epsilon-alpha-mu@t43:~$ 
epsilon-alpha-mu@t43:~$ pfetch 
  _____      os     Debian GNU/Linux 13 (trixie)
 /  __ \     host   2669C8U ThinkPad T43
|  /    |    kernel 6.1.0-37-686-pae
|  \___-     uptime 2m
-_           pkgs   294
  --_        memory 107M / 2010M

epsilon-alpha-mu@t43:~$ 
