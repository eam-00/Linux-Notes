**Deleting stuff from Debian 12 Stable**

Remove *unnecessary* packages from Debian 12 "Bookworm".

* "Anthy Dictionary editor"

```
ht:~$ sudo apt purge anthy* 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'anthy' for glob 'anthy*'
Note, selecting 'anthy-el' for glob 'anthy*'
Note, selecting 'anthy-common' for glob 'anthy*'
Package 'anthy-el' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgcroots0 libuim-custom2 libuim-data libuim-scm0 libuim8 uim-data
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  anthy* anthy-common* kasumi* libanthy1* libanthyinput0* uim* uim-fep* uim-gtk2.0* uim-gtk2.0-immodule* uim-gtk3* uim-gtk3-immodule* uim-plugins* uim-qt5*
  uim-qt5-immodule* uim-xim*
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 32.0 MB disk space will be freed.
Do you want to continue? [Y/n] 
```
____

* "Mozc Setup"

```
sudo apt purge mozc* 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'mozc-server' for glob 'mozc*'
Note, selecting 'mozc-utils-gui' for glob 'mozc*'
Note, selecting 'mozc-data' for glob 'mozc*'
The following package was automatically installed and is no longer required:
  libprotobuf32
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  mozc-data* mozc-server* mozc-utils-gui* uim-mozc*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 23.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 128940 files and directories currently installed.)
Removing uim-mozc:amd64 (2.28.4715.102+dfsg-2.2) ...
Removing mozc-utils-gui (2.28.4715.102+dfsg-2.2) ...
Removing mozc-data (2.28.4715.102+dfsg-2.2) ...
Removing mozc-server (2.28.4715.102+dfsg-2.2) ...
Processing triggers for gnome-menus (3.36.0-1.1) ...
Processing triggers for mailcap (3.70+nmu1) ...
Processing triggers for desktop-file-utils (0.26-1) ...
(Reading database ... 128898 files and directories currently installed.)
Purging configuration files for mozc-server (2.28.4715.102+dfsg-2.2) ...
Purging configuration files for mozc-data (2.28.4715.102+dfsg-2.2) ...
```
____

* "GNOME Games"

```
sudo apt remove gnome-games

The following packages were automatically installed and are no longer required:
  aisleriot five-or-more four-in-a-row gnome-2048 gnome-chess gnome-klotski gnome-mahjongg gnome-mines gnome-nibbles gnome-robots
  gnome-sudoku gnome-taquin gnome-tetravex guile-3.0-libs hitori hoichess iagno libgc1 libgnome-games-support-1-3
  libgnome-games-support-common libminiupnpc17 libnatpmp1 libqqwing2v5 lightsoff quadrapassel swell-foop tali
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome-games
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 10.2 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 175427 files and directories currently installed.)
Removing gnome-games (1:43+1) ...
```
```

Running apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  aisleriot five-or-more four-in-a-row gnome-2048 gnome-chess gnome-klotski gnome-mahjongg gnome-mines gnome-nibbles gnome-robots
  gnome-sudoku gnome-taquin gnome-tetravex guile-3.0-libs hitori hoichess iagno libgc1 libgnome-games-support-1-3
  libgnome-games-support-common libminiupnpc17 libnatpmp1 libqqwing2v5 lightsoff quadrapassel swell-foop tali
0 upgraded, 0 newly installed, 27 to remove and 0 not upgraded.
After this operation, 130 MB disk space will be freed.
Do you want to continue? [Y/n] 
```



