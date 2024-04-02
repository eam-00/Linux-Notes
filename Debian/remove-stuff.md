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

_____

```
#!/usr/bin/env bash

LOG_FILE="/tmp/purged-packages-debian12.log"
echo -e "===========================" > $LOG_FILE
date >> $LOG_FILE
echo -e "===========================" >> $LOG_FILE
pfetch >> $LOG_FILE
echo -e "===========================" >> $LOG_FILE
/usr/bin/df -h >> $LOG_FILE

echo "Removing Evolution"
killall evolution-source-registry
killall evolution-calendar-factory
killall evolution-alarm-notify
apt purge evolution evolution-common evolution-data-server evolution-plugins

The following packages were automatically installed and are no longer required:
  bogofilter bogofilter-bdb bogofilter-common folks-common libcmark0.30.2 libebackend-1.2-11 libebook-1.2-21 libebook-contacts-1.2-4
  libedata-book-1.2-27 libedata-cal-2.0-2 libedataserverui-1.2-4 libfolks26 libgail-3-0 libgnome-autoar-gtk-0-0 libgsl27 libgslcblas0
  libphonenumber8 libprotobuf32 libpst4 libytnef0
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  evolution* evolution-common* evolution-data-server* evolution-plugin-bogofilter* evolution-plugin-pstimport* evolution-plugins* gnome*
  gnome-contacts* gnome-core* libevolution* libfolks-eds26* task-gnome-desktop*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 81.7 MB disk space will be freed.
Do you want to continue? [Y/n] n


echo "Removing Libre Office"
apt purge $(apt-cache search libreoffice | grep -i libreoffice | awk '{print $1}')

The following packages were automatically installed and are no longer required:
  coinor-libcbc3 coinor-libcgl1 coinor-libclp1 coinor-libcoinmp1v5 coinor-libcoinutils3v5 coinor-libosi1v5 fonts-opensymbol javascript-common
  libabw-0.1-1 libboost-filesystem1.74.0 libboost-iostreams1.74.0 libboost-locale1.74.0 libboost-thread1.74.0 libbox2d2 libcdr-0.1-1
  libclucene-contribs1v5 libclucene-core1v5 libcolamd2 libe-book-0.1-1 libeot0 libepubgen-0.1-1 libetonyek-0.1-1 libexttextcat-2.0-0
  libexttextcat-data libfreehand-0.1-1 libgpgmepp6 liblangtag-common liblangtag1 libmhash2 libmspub-0.1-1 libmwaw-0.3-3 libmythes-1.2-0
  libnumbertext-1.0-0 libnumbertext-data libodfgen-0.1-1 liborcus-0.17-0 liborcus-parser-0.17-0 libpagemaker-0.0-0 libqxp-0.0-0 librasqal3
  librdf0 librevenge-0.0-0 libstaroffice-0.0-0 libsuitesparseconfig5 libvisio-0.1-1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libxmlsec1
  libxmlsec1-nss libzmf-0.0-0 lp-solve node-clipboard node-normalize.css node-prismjs
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome* libreoffice-base-core* libreoffice-calc* libreoffice-common* libreoffice-core* libreoffice-draw* libreoffice-gnome*
  libreoffice-gtk3* libreoffice-help-common* libreoffice-help-en-us* libreoffice-impress* libreoffice-math* libreoffice-style-colibre*
  libreoffice-style-elementary* libreoffice-writer* libuno-cppu3* libuno-cppuhelpergcc3-3* libuno-purpenvhelpergcc3-3* libuno-sal3*
  libuno-salhelpergcc3-3* mythes-en-us* python3-uno* uno-libs-private* ure*
0 upgraded, 0 newly installed, 24 to remove and 0 not upgraded.
After this operation, 373 MB disk space will be freed.
Do you want to continue? [Y/n] n

echo "Removing Shotwell"
## dpkg --get-selections | grep shotw*
apt purge shotw*

The following package was automatically installed and is no longer required:
  libraw20
Use 'apt autoremove' to remove it.
The following packages will be REMOVED:
  gnome* shotwell* shotwell-common*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 15.3 MB disk space will be freed.
Do you want to continue? [Y/n] n


echo "Removing Transmission"
## dpkg --get-selections | grep transsmi*
apt purge transmiss*

echo "Removing Rhythmbox"
## dpkg --get-selections | grep rhythmb*
apt purge rhythmb*

The following packages were automatically installed and are no longer required:
  brasero-common cdrdao gir1.2-javascriptcoregtk-4.0 gir1.2-rb-3.0 gir1.2-webkit2-4.0 libbrasero-media3-1 libburn4 libgpod-common libgpod4
  libisofs6 libjte2 liblirc-client0 libminiupnpc17 libnatpmp1 libperl4-corelibs-perl librhythmbox-core10 libsgutils2-1.46-2 media-player-info
  python3-mako python3-markupsafe
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome* rhythmbox* rhythmbox-data* rhythmbox-plugin-cdrecorder* rhythmbox-plugins*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 11.6 MB disk space will be freed.
Do you want to continue? [Y/n] n


echo "Removing Games"
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



echo "Running apt autoremove"
sudo apt autoremove

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
Do you want to continue? [Y/n] y

echo -e "===========================" >> $LOG_FILE
pfetch >> $LOG_FILE
echo -e "===========================" >> $LOG_FILE
/usr/bin/df -h >> $LOG_FILE
echo -e "===========================" >> $LOG_FILE
date >> $LOG_FILE
echo -e "===========================" >> $LOG_FILE

## EOF ##


echo "Xsane"
sudo apt purge $(apt-cache search xsane | grep -i xsane | awk '{print $1}')

* Fonts:

sudo apt-get remove --purge fonts-noto-extra
sudo apt-get remove --purge fonts-dzongkha fonts-noto-cjk fonts-noto-cjk-extra fonts-noto-color-emoji fonts-unikurdweb fonts-vlgothic fonts-urw-base35
sudo apt-get remove --purge fonts-gujr-extra fonts-ipafont fonts-ipafont-gothic fonts-ipafont-mincho fonts-arundina fonts-beng-extra
sudo apt-get remove --purge fonts-telu-extra fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-laksaman fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree fonts-ukij-uyghur fonts-kacst fonts-kacst-one fonts-khmeros fonts-lohit-beng-assamese fonts-lohit-beng-bengali fonts-lohit-deva fonts-lohit-gujr fonts-lohit-guru fonts-lohit-knda fonts-lohit-mlym fonts-lohit-taml fonts-lohit-taml-classical fonts-lohit-telu
sudo apt-get remove --purge xfonts-thai-etl xfonts-thai-manop xfonts-thai-nectec xfonts-thai-poonlap xfonts-thai-vor
sudo apt-get remove --purge fonts-farsiweb fonts-sil-abyssinica fonts-sil-andika fonts-smc-anjalioldlipi fonts-smc-chilanka fonts-smc-dyuthi fonts-smc-karumbi fonts-smc-keraleeyam fonts-smc-manjari fonts-smc-meera fonts-smc-rachana fonts-smc-raghumalayalamsans fonts-smc-suruma fonts-smc-uroob


sudo apt autoremove
```


