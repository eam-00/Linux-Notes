Devuan Stuff

Devuan Daedalus @Dell m1330:
---------------------------

Software selection during the installation:

- SSH Server
- Standard System Utilities

Right up after the install:

root@m1330:/usr/local/bin# pfetch 
    ___       os     Devuan GNU/Linux 5 (daedalus)
   (.· |      host   XPS M1330
   (<> |      kernel 6.1.0-31-amd64
  / __  \     uptime 3m
 ( /  \ /|    pkgs   439
_/\ __)/_)    memory 110M / 7939M
\/-____\/

root@m1330:/usr/local/bin# 

The original -on Daedalus sources.list:

#deb cdrom:[Devuan GNU/Linux 5.0.1 daedalus amd64 - netinstall 20230914]/ daedalus contrib main non-free non-free-firmware

deb http://ar.deb.devuan.org/merged daedalus main non-free-firmware
deb-src http://ar.deb.devuan.org/merged daedalus main non-free-firmware

deb http://deb.devuan.org/merged daedalus-security main non-free-firmware
deb-src http://deb.devuan.org/merged daedalus-security main non-free-firmware

# daedalus-updates, to get updates before a point release is made;
# see https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_updates_and_backports
deb http://ar.deb.devuan.org/merged daedalus-updates main non-free-firmware
deb-src http://ar.deb.devuan.org/merged daedalus-updates main non-free-firmware

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.


To switch to Ceres/ Sid -> Unstable, the /etc/apt/sources.list has to be like this:

deb http://ar.deb.devuan.org/merged ceres main non-free-firmware
deb-src http://ar.deb.devuan.org/merged ceres main non-free-firmware


root@m1330:/etc/apt# apt update
Hit:1 http://ar.deb.devuan.org/merged ceres InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
388 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@m1330:/etc/apt# apt upgrade 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libaio1 libcurl3-gnutls libldap-2.5-0 libldap-common librtmp1 libsasl2-2 libsasl2-modules libsasl2-modules-db libssh2-1 python3-httplib2
  python3-pkg-resources python3-pycurl python3-pyparsing python3-pysimplesoap python3-six
Use 'apt autoremove' to remove them.
The following NEW packages will be installed:
  firmware-ath9k-htc firmware-carl9170 fonts-dejavu-mono gcc-14-base libaio1t64 libsharpyuv0 libunistring5 linux-image-6.12.17-amd64
  linux-sysctl-defaults login.defs systemd-standalone-sysusers
The following packages have been kept back:
  alsa-ucm-conf apt apt-utils at-spi2-core bind9-dnsutils bind9-host bind9-libs bluez coreutils cryptsetup cryptsetup-bin
  cryptsetup-initramfs dconf-gsettings-backend dconf-service e2fsprogs fdisk file grub-common grub-pc grub-pc-bin grub2-common
  gtk-update-icon-cache initramfs-tools initramfs-tools-core initscripts iproute2 kmod libbpf1 libcairo-gobject2 libcairo2 libcolord2
  libcryptsetup12 libdconf1 libfido2-1 libfreetype6 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libglib2.0-0 libgssapi-krb5-2 libgtk-3-bin
  libgtk-3-common libharfbuzz0b libk5crypto3 libkmod2 libkrb5-3 libkrb5support0 libldap-2.5-0 liblocale-gettext-perl libmagic-mgc libnsl2
  libpam-modules libpam-modules-bin libpam-runtime libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpolkit-agent-1-0
  libpolkit-gobject-elogind-1-0 libpython3-stdlib librsvg2-2 librsvg2-common librtmp1 libsasl2-2 libsasl2-modules libsasl2-modules-db
  libtext-charwidth-perl libtext-iconv-perl lsof man-db openssh-client openssh-server openssh-sftp-server openssl perl perl-base pkexec
  polkitd python3 python3-apt python3-charset-normalizer python3-minimal python3-pkg-resources python3-pycurl shared-mime-info
  util-linux-extra wget wireless-tools wpasupplicant
The following packages will be upgraded:
  adduser adwaita-icon-theme alsa-topology-conf anacron apparmor apt-listchanges at-spi2-common avahi-autoipd base-files base-passwd bash
  bash-completion bluetooth bootlogd bsdextrautils bsdutils busybox bzip2 ca-certificates console-setup console-setup-linux cpio cron
  cron-daemon-common dash dbus dbus-bin dbus-daemon dbus-session-bus-common dbus-system-bus-common dbus-x11 debconf debconf-i18n
  debian-archive-keyring debian-faq debianutils devuan-keyring dictionaries-common diffutils discover discover-data distro-info-data
  dmeventd dmidecode dmsetup dpkg eject elogind eudev findutils firmware-iwlwifi firmware-linux-free fontconfig fontconfig-config
  fonts-dejavu-core gcc-12-base gettext-base gpgv grep groff-base gsettings-desktop-schemas gzip hicolor-icon-theme hostname iamerican
  ibritish ienglish-common ifupdown inetutils-telnet init init-system-helpers insserv installation-report iputils-ping isc-dhcp-client
  isc-dhcp-common iso-codes ispell iw kbd keyboard-configuration klibc-utils krb5-locales laptop-detect less libacl1 libapparmor1
  libargon2-1 libasound2-data libattr1 libaudit-common libaudit1 libavahi-client3 libavahi-common-data libavahi-common3 libblkid1
  libbrotli1 libbsd0 libbz2-1.0 libc-bin libc-l10n libc6 libcap-ng0 libcap2 libcap2-bin libcom-err2 libcrypt1 libdaemon0 libdatrie1
  libdbus-1-3 libdebconfclient0 libdeflate0 libdevmapper-event1.02.1 libdevmapper1.02.1 libdiscover2 libduktape207 libedit2
  libelogind-compat libelogind0 libepoxy0 libestr0 libeudev1 libexpat1 libfastjson4 libfdisk1 libffi8 libfontconfig1 libfribidi0 libfstrm0
  libgcc-s1 libgcrypt20 libgdk-pixbuf2.0-common libglib2.0-data libgmp10 libgpg-error0 libgraphite2-3 libicu72 libidn2-0 libjansson4
  libjbig0 libjemalloc2 libjpeg62-turbo libjson-c5 libkeyutils1 libklibc liblcms2-2 libldap-common liblerc4 liblmdb0 liblockfile-bin
  liblognorm5 liblvm2cmd2.03 liblz4-1 liblzma5 libmaxminddb0 libmd0 libmnl0 libmount1 libncursesw6 libnewt0.52 libnftables1 libnftnl11
  libnghttp2-14 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libp11-kit0 libpam-elogind libpam0g libpci3 libpcre2-8-0 libpcsclite1
  libpipeline1 libpixman-1-0 libpolkit-gobject-1-0 libpopt0 libproc2-0 libprotobuf-c1 libseccomp2 libselinux1 libsemanage-common
  libsemanage2 libsepol2 libslang2 libsmartcols1 libsqlite3-0 libss2 libstdc++6 libtasn1-6 libthai-data libthai0 libtiff6 libtinfo6
  libtirpc-common libuchardet0 libusb-1.0-0 libuuid1 libwayland-client0 libwayland-cursor0 libwayland-egl1 libwebp7 libwrap0 libx11-6
  libx11-data libxau6 libxcb-render0 libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxi6
  libxinerama1 libxkbcommon0 libxml2 libxmuu1 libxrandr2 libxrender1 libxtables12 libxtst6 libxxhash0 libzstd1 linux-base linux-image-amd64
  locales login logrotate logsave lsb-release lvm2 mailcap manpages mawk media-types mount nano ncurses-base ncurses-bin ncurses-term
  net-tools netcat-traditional nftables os-prober passwd pci.ids pciutils popularity-contest powertop procps publicsuffix python-apt-common
  python3-certifi python3-chardet python3-debconf python3-debian python3-debianbts python3-httplib2 python3-idna python3-pyparsing
  python3-reportbug python3-requests python3-six python3-urllib3 readline-common reportbug rsyslog runit-helper sed sensible-utils startpar
  sysv-rc sysvinit sysvinit-core sysvinit-utils tar task-english task-laptop task-ssh-server tasksel tasksel-data traceroute tzdata ucf
  util-linux util-linux-locales vim-common vim-tiny wamerican whiptail x11-common xauth xdg-user-dirs xkb-data xml-core xz-utils zlib1g
  zstd
300 upgraded, 11 newly installed, 0 to remove and 88 not upgraded.
Need to get 210 MB of archives.
After this operation, 143 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

root@m1330:/etc/apt# apt upgrade

Fetched 210 MB in 26s (8,058 kB/s)                                                                                                           
Reading changelogs... Done
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 41740 files and directories currently installed.)
Preparing to unpack .../base-files_13.7devuan1_amd64.deb ...


******************************************************************************
*
* The base-files package cannot be installed because
* /bin is a directory, but should be a symbolic link.
*
* Please install the usrmerge package to convert this system to merged-/usr.
*
* For more information please read https://wiki.debian.org/UsrMerge.
*
******************************************************************************


dpkg: error processing archive /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb (--unpack):
 new base-files package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@m1330:/etc/apt# 

apt update && apt --fix-broken install

root@m1330:/etc/apt# apt dist-upgrade

******************************************************************************
*
* The base-files package cannot be installed because
* /bin is a directory, but should be a symbolic link.
*
* Please install the usrmerge package to convert this system to merged-/usr.
*
* For more information please read https://wiki.debian.org/UsrMerge.
*
******************************************************************************


dpkg: error processing archive /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb (--unpack):
 new base-files package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@m1330:/etc/apt#

Found this while searching on the web:
Upgrade broken: base-files installation fails due to alledgedly unmet usrmerge
https://forum.siduction.org/index.php?topic=9457.0

root@m1330:/etc/apt# cd /
root@m1330:/# ln -nsf usr/bin bin
root@m1330:/# ln -nsf usr/sbin sbin
root@m1330:/# ln -nsf usr/lib lib
root@m1330:/# ln -nsf usr/lib64 lib64
root@m1330:/# apt update
Hit:1 http://ar.deb.devuan.org/merged ceres InRelease
Reading package lists... Done       
Building dependency tree... Done
Reading state information... Done
388 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@m1330:/# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libaio1 python3-httplib2 python3-pkg-resources python3-pycurl python3-pyparsing python3-pysimplesoap python3-six
Use 'apt autoremove' to remove them.
The following NEW packages will be installed:
  firmware-ath9k-htc firmware-carl9170 fonts-dejavu-mono gcc-14-base libaio1t64 libsharpyuv0 libunistring5 linux-image-6.12.17-amd64
  linux-sysctl-defaults login.defs systemd-standalone-sysusers
The following packages have been kept back:
  alsa-ucm-conf apt apt-utils at-spi2-core bind9-dnsutils bind9-host bind9-libs bluez coreutils cryptsetup cryptsetup-bin
  cryptsetup-initramfs dconf-gsettings-backend dconf-service e2fsprogs fdisk file grub-common grub-pc grub-pc-bin grub2-common
  gtk-update-icon-cache initramfs-tools initramfs-tools-core initscripts iproute2 kmod libbpf1 libcairo-gobject2 libcairo2 libcolord2
  libcryptsetup12 libdconf1 libfido2-1 libfreetype6 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libglib2.0-0 libgssapi-krb5-2 libgtk-3-bin
  libgtk-3-common libharfbuzz0b libk5crypto3 libkmod2 libkrb5-3 libkrb5support0 libldap-2.5-0 liblocale-gettext-perl libmagic-mgc libnsl2
  libpam-modules libpam-modules-bin libpam-runtime libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpolkit-agent-1-0
  libpolkit-gobject-elogind-1-0 libpython3-stdlib librsvg2-2 librsvg2-common librtmp1 libsasl2-2 libsasl2-modules libsasl2-modules-db
  libtext-charwidth-perl libtext-iconv-perl lsof man-db openssh-client openssh-server openssh-sftp-server openssl perl perl-base pkexec
  polkitd python3 python3-apt python3-charset-normalizer python3-minimal python3-pkg-resources python3-pycurl shared-mime-info
  util-linux-extra wget wireless-tools wpasupplicant
The following packages will be upgraded:
  adduser adwaita-icon-theme alsa-topology-conf anacron apparmor apt-listchanges at-spi2-common avahi-autoipd base-files base-passwd bash
  bash-completion bluetooth bootlogd bsdextrautils bsdutils busybox bzip2 ca-certificates console-setup console-setup-linux cpio cron
  cron-daemon-common dash dbus dbus-bin dbus-daemon dbus-session-bus-common dbus-system-bus-common dbus-x11 debconf debconf-i18n
  debian-archive-keyring debian-faq debianutils devuan-keyring dictionaries-common diffutils discover discover-data distro-info-data
  dmeventd dmidecode dmsetup dpkg eject elogind eudev findutils firmware-iwlwifi firmware-linux-free fontconfig fontconfig-config
  fonts-dejavu-core gcc-12-base gettext-base gpgv grep groff-base gsettings-desktop-schemas gzip hicolor-icon-theme hostname iamerican
  ibritish ienglish-common ifupdown inetutils-telnet init init-system-helpers insserv installation-report iputils-ping isc-dhcp-client
  isc-dhcp-common iso-codes ispell iw kbd keyboard-configuration klibc-utils krb5-locales laptop-detect less libacl1 libapparmor1
  libargon2-1 libasound2-data libattr1 libaudit-common libaudit1 libavahi-client3 libavahi-common-data libavahi-common3 libblkid1 libbrotli1
  libbsd0 libbz2-1.0 libc-bin libc-l10n libc6 libcap-ng0 libcap2 libcap2-bin libcom-err2 libcrypt1 libdaemon0 libdatrie1 libdbus-1-3
  libdebconfclient0 libdeflate0 libdevmapper-event1.02.1 libdevmapper1.02.1 libdiscover2 libduktape207 libedit2 libelogind-compat
  libelogind0 libepoxy0 libestr0 libeudev1 libexpat1 libfastjson4 libfdisk1 libffi8 libfontconfig1 libfribidi0 libfstrm0 libgcc-s1
  libgcrypt20 libgdk-pixbuf2.0-common libglib2.0-data libgmp10 libgpg-error0 libgraphite2-3 libicu72 libidn2-0 libjansson4 libjbig0
  libjemalloc2 libjpeg62-turbo libjson-c5 libkeyutils1 libklibc liblcms2-2 libldap-common liblerc4 liblmdb0 liblockfile-bin liblognorm5
  liblvm2cmd2.03 liblz4-1 liblzma5 libmaxminddb0 libmd0 libmnl0 libmount1 libncursesw6 libnewt0.52 libnftables1 libnftnl11 libnghttp2-14
  libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libp11-kit0 libpam-elogind libpam0g libpci3 libpcre2-8-0 libpcsclite1 libpipeline1
  libpixman-1-0 libpolkit-gobject-1-0 libpopt0 libproc2-0 libprotobuf-c1 libseccomp2 libselinux1 libsemanage-common libsemanage2 libsepol2
  libslang2 libsmartcols1 libsqlite3-0 libss2 libstdc++6 libtasn1-6 libthai-data libthai0 libtiff6 libtinfo6 libtirpc-common libuchardet0
  libusb-1.0-0 libuuid1 libwayland-client0 libwayland-cursor0 libwayland-egl1 libwebp7 libwrap0 libx11-6 libx11-data libxau6 libxcb-render0
  libxcb-shm0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxi6 libxinerama1 libxkbcommon0 libxml2
  libxmuu1 libxrandr2 libxrender1 libxtables12 libxtst6 libxxhash0 libzstd1 linux-base linux-image-amd64 locales login logrotate logsave
  lsb-release lvm2 mailcap manpages mawk media-types mount nano ncurses-base ncurses-bin ncurses-term net-tools netcat-traditional nftables
  os-prober passwd pci.ids pciutils popularity-contest powertop procps publicsuffix python-apt-common python3-certifi python3-chardet
  python3-debconf python3-debian python3-debianbts python3-httplib2 python3-idna python3-pyparsing python3-reportbug python3-requests
  python3-six python3-urllib3 readline-common reportbug rsyslog runit-helper sed sensible-utils startpar sysv-rc sysvinit sysvinit-core
  sysvinit-utils tar task-english task-laptop task-ssh-server tasksel tasksel-data traceroute tzdata ucf util-linux util-linux-locales
  vim-common vim-tiny wamerican whiptail x11-common xauth xdg-user-dirs xkb-data xml-core xz-utils zlib1g zstd
300 upgraded, 11 newly installed, 0 to remove and 88 not upgraded.
Need to get 0 B/210 MB of archives.
After this operation, 143 MB of additional disk space will be used.
Do you want to continue? [Y/n] y

(Reading database ... 41740 files and directories currently installed.)
Preparing to unpack .../base-files_13.7devuan1_amd64.deb ...


******************************************************************************
*
* The base-files package cannot be installed because
* /bin is a directory, but should be a symbolic link.
*
* Please install the usrmerge package to convert this system to merged-/usr.
*
* For more information please read https://wiki.debian.org/UsrMerge.
*
******************************************************************************


dpkg: error processing archive /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb (--unpack):
 new base-files package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/base-files_13.7devuan1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@m1330:/# 

But it failed...

So installed the package listed by the error message:

root@m1330:/# apt install usrmerge
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libfile-find-rule-perl libnumber-compare-perl libtext-glob-perl
The following NEW packages will be installed:
  libfile-find-rule-perl libnumber-compare-perl libtext-glob-perl usrmerge
0 upgraded, 4 newly installed, 0 to remove and 388 not upgraded.
Need to get 53.9 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

root@m1330:/# apt upgrade

root@m1330:/# apt dist-upgrade 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  adwaita-icon-theme at-spi2-common at-spi2-core dconf-gsettings-backend dconf-service fontconfig fontconfig-config fonts-dejavu-core
  fonts-dejavu-mono gsettings-desktop-schemas gtk-update-icon-cache hicolor-icon-theme libaio1 libargon2-1 libatk-bridge2.0-0t64
  libatk1.0-0t64 libatspi2.0-0t64 libavahi-client3 libavahi-common-data libavahi-common3 libcairo-gobject2 libcairo2 libcbor0.8
  libcloudproviders0 libcolord2 libcups2t64 libcurl3t64-gnutls libdatrie1 libdav1d7 libdconf1 libdeflate0 libepoxy0 libfontconfig1 libfuse2
  libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgraphite2-3 libgtk-3-0t64 libgtk-3-bin libgtk-3-common libharfbuzz0b
  libjbig0 libjpeg62-turbo liblcms2-2 libldap-2.5-0 libldap-common libldap2 liblerc4 libnghttp3-9 libngtcp2-16 libngtcp2-crypto-gnutls8
  libnsl2 libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libperl5.36 libpixman-1-0 libpython3.11-minimal libpython3.11-stdlib
  librsvg2-2 librsvg2-common librtmp1 libsasl2-2 libsasl2-modules libsasl2-modules-db libsharpyuv0 libssh2-1t64 libthai-data libthai0
  libtiff6 libwayland-client0 libwayland-cursor0 libwayland-egl1 libwebp7 libxcb-render0 libxcb-shm0 libxcomposite1 libxcursor1 libxdamage1
  libxfixes3 libxi6 libxinerama1 libxkbcommon0 libxrandr2 libxrender1 libxtst6 perl-modules-5.36 pkexec policykit-1-gnome
  python3-autocommand python3-httplib2 python3-inflect python3-jaraco.context python3-jaraco.functools python3-more-itertools
  python3-pkg-resources python3-pycurl python3-pyparsing python3-pysimplesoap python3-six python3-typeguard python3-typing-extensions
  python3.11 python3.11-minimal x11-common
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  libasound2 libatk-bridge2.0-0 libatk1.0-0 libatspi2.0-0 libcups2 libcurl3-gnutls libdb5.3 libdw1 libefiboot1 libefivar1 libelf1 libext2fs2
  libgdbm-compat4 libgdbm6 libglib2.0-0 libgnutls30 libgtk-3-0 libhogweed6 libiw30 libmagic1 libnettle8 libpng16-16 libpsl5 libreadline8
  libssh2-1 libssl3 libtirpc3 libuv1 linux-image-6.1.0-10-amd64 policykit-1 polkitd-pkla
The following NEW packages will be installed:
  dracut-install libapt-pkg7.0 libasound2t64 libatk-bridge2.0-0t64 libatk1.0-0t64 libatomic1 libatspi2.0-0t64 libcbor0.10 libcloudproviders0
  libcups2t64 libcurl3t64-gnutls libdav1d7 libdb5.3t64 libdw1t64 libefiboot1t64 libefivar1t64 libelf1t64 libext2fs2t64 libfuse3-3
  libgdbm-compat4t64 libgdbm6t64 libglib2.0-0t64 libgnutls30t64 libgtk-3-0t64 libhogweed6t64 libiw30t64 libldap2 liblsof0 libmagic1t64
  libnettle8t64 libnghttp3-9 libngtcp2-16 libngtcp2-crypto-gnutls8 libperl5.40 libpng16-16t64 libpsl5t64 libpython3.13-minimal
  libpython3.13-stdlib libreadline8t64 libssh2-1t64 libssl3t64 libtirpc3t64 liburcu8t64 libuv1t64 openssl-provider-legacy perl-modules-5.40
  python3-autocommand python3-inflect python3-jaraco.context python3-jaraco.functools python3-more-itertools python3-typeguard
  python3-typing-extensions python3.13 python3.13-minimal
The following packages will be upgraded:
  alsa-ucm-conf apt apt-utils at-spi2-core bind9-dnsutils bind9-host bind9-libs bluez coreutils cryptsetup cryptsetup-bin
  cryptsetup-initramfs dconf-gsettings-backend dconf-service e2fsprogs fdisk file grub-common grub-pc grub-pc-bin grub2-common
  gtk-update-icon-cache initramfs-tools initramfs-tools-core initscripts iproute2 kmod libbpf1 libcairo-gobject2 libcairo2 libcolord2
  libcryptsetup12 libdconf1 libfido2-1 libfreetype6 libgdk-pixbuf-2.0-0 libgdk-pixbuf2.0-bin libgssapi-krb5-2 libgtk-3-bin libgtk-3-common
  libharfbuzz0b libk5crypto3 libkmod2 libkrb5-3 libkrb5support0 libldap-2.5-0 liblocale-gettext-perl libmagic-mgc libnsl2 libpam-modules
  libpam-modules-bin libpam-runtime libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpolkit-agent-1-0 libpolkit-gobject-elogind-1-0
  libpython3-stdlib librsvg2-2 librsvg2-common librtmp1 libsasl2-2 libsasl2-modules libsasl2-modules-db libtext-charwidth-perl
  libtext-iconv-perl lsof man-db openssh-client openssh-server openssh-sftp-server openssl perl perl-base pkexec polkitd python3 python3-apt
  python3-charset-normalizer python3-minimal python3-pkg-resources python3-pycurl shared-mime-info util-linux-extra wget wireless-tools
  wpasupplicant
87 upgraded, 55 newly installed, 31 to remove and 0 not upgraded.
Need to get 0 B/66.7 MB of archives.
After this operation, 320 MB disk space will be freed.
Do you want to continue? [Y/n] 

root@m1330:/# pfetch 
    ___       os     Devuan GNU/Linux 6 (excalibur/ceres)
   (.· |      host   XPS M1330
   (<> |      kernel 6.1.0-31-amd64
  / __  \     uptime 55m
 ( /  \ /|    pkgs   483
_/\ __)/_)    memory 137M / 7939M
\/-____\/

root@m1330:/# 


root@m1330:/# apt autoremove
REMOVING:                       
  adwaita-icon-theme         libcbor0.8               liblcms2-2                libsharpyuv0        pkexec
  at-spi2-common             libcloudproviders0       libldap-2.5-0             libssh2-1t64        policykit-1-gnome
  at-spi2-core               libcolord2               libldap-common            libthai-data        python3-autocommand
  dconf-gsettings-backend    libcups2t64              libldap2                  libthai0            python3-httplib2
  dconf-service              libcurl3t64-gnutls       liblerc4                  libtiff6            python3-inflect
  fontconfig                 libdatrie1               libnghttp3-9              libwayland-client0  python3-jaraco.context
  fontconfig-config          libdav1d7                libngtcp2-16              libwayland-cursor0  python3-jaraco.functools
  fonts-dejavu-core          libdconf1                libngtcp2-crypto-gnutls8  libwayland-egl1     python3-more-itertools
  fonts-dejavu-mono          libdeflate0              libnsl2                   libwebp7            python3-pkg-resources
  gsettings-desktop-schemas  libepoxy0                libpango-1.0-0            libxcb-render0      python3-pycurl
  gtk-update-icon-cache      libfontconfig1           libpangocairo-1.0-0       libxcb-shm0         python3-pyparsing
  hicolor-icon-theme         libfuse2                 libpangoft2-1.0-0         libxcomposite1      python3-pysimplesoap
  libaio1                    libgdk-pixbuf-2.0-0      libperl5.36               libxcursor1         python3-six
  libargon2-1                libgdk-pixbuf2.0-bin     libpixman-1-0             libxdamage1         python3-typeguard
  libatk-bridge2.0-0t64      libgdk-pixbuf2.0-common  libpython3.11-minimal     libxfixes3          python3-typing-extensions
  libatk1.0-0t64             libgraphite2-3           libpython3.11-stdlib      libxi6              python3.11
  libatspi2.0-0t64           libgtk-3-0t64            librsvg2-2                libxinerama1        python3.11-minimal
  libavahi-client3           libgtk-3-bin             librsvg2-common           libxkbcommon0       x11-common
  libavahi-common-data       libgtk-3-common          librtmp1                  libxrandr2
  libavahi-common3           libharfbuzz0b            libsasl2-2                libxrender1
  libcairo-gobject2          libjbig0                 libsasl2-modules          libxtst6
  libcairo2                  libjpeg62-turbo          libsasl2-modules-db       perl-modules-5.36

Summary:
  Upgrading: 0, Installing: 0, Removing: 106, Not Upgrading: 0
  Freed space: 174 MB

Continue? [Y/n] 

root@m1330:/# pfetch 
    ___       os     Devuan GNU/Linux 6 (excalibur/ceres)
   (.· |      host   XPS M1330
   (<> |      kernel 6.1.0-31-amd64
  / __  \     uptime 1h 37m
 ( /  \ /|    pkgs   392
_/\ __)/_)    memory 130M / 7939M
\/-____\/

root@m1330:/# 

epsilon-alpha-mu@m1330:~$ df -h 
Filesystem                  Size  Used Avail Use% Mounted on
udev                        3.9G     0  3.9G   0% /dev
tmpfs                       795M  732K  794M   1% /run
/dev/mapper/m1330--vg-root  218G  1.7G  205G   1% /
tmpfs                       5.0M     0  5.0M   0% /run/lock
tmpfs                       1.6G     0  1.6G   0% /dev/shm
/dev/sda1                   455M   97M  334M  23% /boot
tmpfs                       3.9G     0  3.9G   0% /tmp
tmpfs                       795M     0  795M   0% /run/user/1000
epsilon-alpha-mu@m1330:~$ 

epsilon-alpha-mu@m1330:~$ pfetch 
    ___       os     Devuan GNU/Linux 6 (excalibur/ceres)
   (.· |      host   XPS M1330
   (<> |      kernel 6.12.17-amd64
  / __  \     uptime 4m
 ( /  \ /|    pkgs   392
_/\ __)/_)    memory 135M / 7946M
\/-____\/

epsilon-alpha-mu@m1330:~$ 

root@m1330:~# apt clean
root@m1330:~# df -h 
Filesystem                  Size  Used Avail Use% Mounted on
udev                        3.9G     0  3.9G   0% /dev
tmpfs                       795M  732K  794M   1% /run
/dev/mapper/m1330--vg-root  218G  1.4G  206G   1% /
tmpfs                       5.0M     0  5.0M   0% /run/lock
tmpfs                       1.6G     0  1.6G   0% /dev/shm
/dev/sda1                   455M   97M  334M  23% /boot
tmpfs                       3.9G     0  3.9G   0% /tmp
tmpfs                       795M     0  795M   0% /run/user/1000
root@m1330:~# 

root@m1330:~# apt install --no-install-recommends gnome-core
Installing:                     
  gnome-core

Installing dependencies:
  accountsservice                   libavif16                          libharfbuzz-gobject0         libspelling-common
  acl                               libavtp0                           libharfbuzz-icu0             libsratom-0-0
  adwaita-icon-theme                libavutil59                        libharfbuzz-subset0          libsrt1.5-gnutls
  apg                               libblockdev-crypto3                libharfbuzz0b                libsrtp2-1
  appstream                         libblockdev-fs3                    libheif-plugin-dav1d         libssh2-1t64
  apt-config-icons                  libblockdev-loop3                  libheif-plugin-libde265      libstartup-notification0
  at-spi2-common                    libblockdev-mdraid3                libheif1                     libstemmer0d
  at-spi2-core                      libblockdev-nvme3                  libhunspell-1.7-0            libsvtav1enc2
  baobab                            libblockdev-part3                  libhwy1t64                   libswresample5
  bc                                libblockdev-swap3                  libhyphen0                   libswscale8
  bluez-obexd                       libblockdev-utils3                 libibus-1.0-5                libsynctex2
  bubblewrap                        libblockdev3                       libical3t64                  libtag2
  clearlooks-phenix-sapphire-theme  libbluetooth3                      libice6                      libtalloc2
  colord                            libbluray2                         libidn12                     libtdb1
  colord-data                       libbrlapi0.8                       libiec61883-0                libtevent0t64
  cpp                               libbs2b0                           libieee1284-3t64             libthai-data
  cpp-14                            libbytesize-common                 libijs-0.35                  libthai0
  cpp-14-x86-64-linux-gnu           libbytesize1                       libimagequant0               libtheora0
  cpp-x86-64-linux-gnu              libcaca0                           libimath-3-1-29t64           libtheoradec1
  cups                              libcairo-gobject-perl              libimobiledevice-1.0-6       libtheoraenc1
  cups-client                       libcairo-gobject2                  libimobiledevice-glue-1.0-0  libtiff6
  cups-common                       libcairo-perl                      libinih1                     libtinysparql-3.0-0
  cups-core-drivers                 libcairo-script-interpreter2       libinireader0                libtotem-plparser-common
  cups-daemon                       libcairo2                          libinput-bin                 libtotem-plparser18
  cups-filters                      libcairomm-1.16-1                  libinput10                   libtotem0
  cups-filters-core-drivers         libcamel-1.2-64t64                 libinstpatch-1.0-2           libtracker-sparql-3.0-0
  cups-ipp-utils                    libcamera0.4                       libiptcdata0                 libtwolame0
  cups-ppdc                         libcanberra-gtk3-0                 libisl23                     libudfread0
  cups-server-common                libcanberra-pulse                  libjack-jackd2-0             libudisks2-0
  dconf-cli                         libcanberra0                       libjavascriptcoregtk-4.1-0   libunibreak6
  dconf-gsettings-backend           libcdio-cdda2t64                   libjavascriptcoregtk-6.0-1   libupower-glib3
  dconf-service                     libcdio-paranoia2t64               libjbig0                     liburiparser1
  deepsea-icon-theme                libcdio19t64                       libjbig2dec0                 libusbmuxd-2.0-7
  desktop-base                      libcdparanoia0                     libjpeg62-turbo              libv4l-0t64
  desktop-file-utils                libchromaprint1                    libjson-glib-1.0-0           libv4lconvert0t64
  dirmngr                           libcjson1                          libjson-glib-1.0-common      libva-drm2
  dmz-cursor-theme                  libcloudproviders0                 libjxl-gdk-pixbuf            libva-x11-2
  evince                            libcodec2-1.2                      libjxl0.10                   libva2
  evince-common                     libcolord-gtk4-1t64                libkpathsea6                 libvdpau1
  evolution-data-server             libcolord2                         libksba8                     libvisual-0.4-0
  evolution-data-server-common      libcolorhug2                       liblc3-1                     libvo-aacenc0
  folks-common                      libconfig++11                      liblcms2-2                   libvo-amrwbenc0
  fontconfig                        libcpuinfo0                        libldacbt-abr2               libvolume-key1
  fontconfig-config                 libcrack2                          libldacbt-enc2               libvorbis0a
  fonts-cantarell                   libcue2                            libldap2                     libvorbisenc2
  fonts-dejavu-core                 libcups2t64                        libldb2                      libvorbisfile3
  fonts-dejavu-mono                 libcupsfilters1t64                 liblerc4                     libvpl2
  fonts-urw-base35                  libcurl3t64-gnutls                 liblilv-0-0                  libvpx9
  fuse3                             libcurl4t64                        libllvm19                    libvte-2.91-0
  gcr                               libdatrie1                         liblouis-data                libvte-2.91-common
  gcr4                              libdav1d7                          liblouis20                   libvulkan1
  gdm3                              libdc1394-25                       liblrdf0                     libwacom-common
  geoclue-2.0                       libdca0                            libltc11                     libwacom9
  geocode-glib-common               libdconf1                          libltdl7                     libwavpack1
  ghostscript                       libde265-0                         liblttng-ust-common1t64      libwayland-client0
  gir1.2-accountsservice-1.0        libdecor-0-0                       liblttng-ust-ctl5t64         libwayland-cursor0
  gir1.2-adw-1                      libdeflate0                        liblttng-ust1t64             libwayland-egl1
  gir1.2-atk-1.0                    libdisplay-info2                   liblua5.4-0                  libwayland-server0
  gir1.2-atspi-2.0                  libdjvulibre-text                  liblzo2-2                    libwbclient0
  gir1.2-evince-3.0                 libdjvulibre21                     libmalcontent-0-0            libwebkit2gtk-4.1-0
  gir1.2-freedesktop                libdmapsharing-4.0-3t64            libmanette-0.2-0             libwebkitgtk-6.0-4
  gir1.2-gck-2                      libdnnl3.6                         libmediaart-2.0-0            libwebp7
  gir1.2-gcr-4                      libdotconf0                        libmjpegutils-2.1-0t64       libwebpdemux2
  gir1.2-gdesktopenums-3.0          libdrm-amdgpu1                     libmm-glib0                  libwebpmux3
  gir1.2-gdkpixbuf-2.0              libdrm-common                      libmodplug1                  libwebrtc-audio-processing-1-3
  gir1.2-gdm-1.0                    libdrm-intel1                      libmozjs-128-0               libwildmidi2
  gir1.2-geoclue-2.0                libdrm2                            libmp3lame0                  libwinpr3-3
  gir1.2-geocodeglib-2.0            libdv4t64                          libmpc3                      libwireplumber-0.5-0
  gir1.2-girepository-2.0           libdvdnav4                         libmpcdec6                   libwnck-3-0
  gir1.2-glib-2.0                   libdvdread8t64                     libmpeg2encpp-2.1-0t64       libwnck-3-common
  gir1.2-gnomebg-4.0                libebackend-1.2-11t64              libmpfr6                     libwoff1
  gir1.2-gnomebluetooth-3.0         libebook-1.2-21t64                 libmpg123-0t64               libx11-xcb1
  gir1.2-gnomedesktop-4.0           libebook-contacts-1.2-4t64         libmplex2-2.1-0t64           libx264-164
  gir1.2-graphene-1.0               libebur128-1                       libmsgraph-1-1               libx265-215
  gir1.2-gst-plugins-base-1.0       libecal-2.0-3                      libmtdev1t64                 libxaw7
  gir1.2-gstreamer-1.0              libedata-book-1.2-27t64            libmtp-common                libxcb-dri3-0
  gir1.2-gtk-3.0                    libedata-cal-2.0-2t64              libmtp9t64                   libxcb-glx0
  gir1.2-gtk-4.0                    libedataserver-1.2-27t64           libmutter-16-0               libxcb-present0
  gir1.2-gtksource-4                libedataserverui-1.2-4t64          libmysofa1                   libxcb-randr0
  gir1.2-gweather-4.0               libedataserverui4-1.0-0t64         libnautilus-extension4       libxcb-render0
  gir1.2-harfbuzz-0.0               libeditorconfig0                   libncurses6                  libxcb-res0
  gir1.2-ibus-1.0                   libegl-mesa0                       libneon27t64                 libxcb-shm0
  gir1.2-javascriptcoregtk-4.1      libegl1                            libnfs14                     libxcb-sync1
  gir1.2-json-1.0                   libeis1                            libnghttp3-9                 libxcb-util1
  gir1.2-mutter-16                  libenchant-2-2                     libngtcp2-16                 libxcb-xfixes0
  gir1.2-nm-1.0                     libepoxy0                          libngtcp2-crypto-gnutls8     libxcb-xkb1
  gir1.2-nma4-1.0                   libevdev2                          libnice10                    libxcomposite1
  gir1.2-notify-0.7                 libevdocument3-4t64                libnm0                       libxcursor1
  gir1.2-pango-1.0                  libevview3-3t64                    libnma-common                libxcvt0
  gir1.2-polkit-1.0                 libexempi8                         libnma-gtk4-0                libxdamage1
  gir1.2-rest-1.0                   libexif12                          libnotify4                   libxfixes3
  gir1.2-rsvg-2.0                   libexiv2-28                        libnpth0t64                  libxfont2
  gir1.2-secret-1                   libexiv2-data                      libnspr4                     libxft2
  gir1.2-shumate-1.0                libextutils-depends-perl           libnss3                      libxi6
  gir1.2-soup-3.0                   libfaad2                           libnuma1                     libxinerama1
  gir1.2-upowerglib-1.0             libffado2                          libnvme1t64                  libxkbcommon-x11-0
  gir1.2-webkit2-4.1                libfftw3-single3                   liboauth0                    libxkbcommon0
  gir1.2-wnck-3.0                   libflac14                          libogg0                      libxkbfile1
  gir1.2-xdp-1.0                    libflite1                          libonnx1t64                  libxkbregistry0
  gjs                               libfluidsynth3                     libonnxruntime1.21           libxml++2.6-2v5
  glib-networking                   libfolks-eds26                     libopenal-data               libxmlb2
  glib-networking-common            libfolks26                         libopenal1                   libxmu6
  glib-networking-services          libfontconfig1                     libopencore-amrnb0           libxnnpack0.20241108
  glycin-loaders                    libfontembed1t64                   libopencore-amrwb0           libxpm4
  gnome-backgrounds                 libfontenc1                        libopenexr-3-1-30            libxrandr2
  gnome-bluetooth-3-common          libfreeaptx0                       libopenfec1                  libxrender1
  gnome-bluetooth-sendto            libfreerdp-client3-3               libopenh264-8                libxres1
  gnome-calculator                  libfreerdp3-3                      libopenjp2-7                 libxshmfence1
  gnome-calendar                    libfuse3-4                         libopenmpt0t64               libxslt1.1
  gnome-characters                  libgav1-1                          libopenni2-0                 libxss1
  gnome-clocks                      libgbm1                            libopus0                     libxt6t64
  gnome-connections                 libgck-1-0                         liborc-0.4-0t64              libxtst6
  gnome-contacts                    libgck-2-2                         libosinfo-1.0-0              libxv1
  gnome-control-center              libgcr-4-4                         libosinfo-l10n               libxvidcore4
  gnome-control-center-data         libgcr-base-3-1                    libpackagekit-glib2-18       libxxf86vm1
  gnome-desktop3-data               libgcr-ui-3-1                      libpam-gnome-keyring         libyajl2
  gnome-disk-utility                libgd3                             libpango-1.0-0               libyaml-0-2
  gnome-extra-icons                 libgdata-common                    libpangocairo-1.0-0          libyelp0
  gnome-font-viewer                 libgdata22                         libpangoft2-1.0-0            libyuv0
  gnome-icon-theme                  libgdk-pixbuf-2.0-0                libpangomm-2.48-1t64         libz3-4
  gnome-keyring                     libgdk-pixbuf2.0-common            libpangoxft-1.0-0            libzbar0t64
  gnome-logs                        libgdm1                            libpaper2                    libzix-0-0
  gnome-maps                        libgee-0.8-2                       libparted2t64                libzvbi-common
  gnome-menus                       libgeoclue-2-0                     libpciaccess0                libzvbi0t64
  gnome-online-accounts             libgeocode-glib-2-0                libpeas-1.0-0                libzxing3
  gnome-session                     libgexiv2-2                        libpeas-common               loupe
  gnome-session-bin                 libgif7                            libphonenumber8              mesa-libgallium
  gnome-session-common              libgirepository-1.0-1              libpipewire-0.3-0t64         mutter-common
  gnome-settings-daemon             libgjs0g                           libpipewire-0.3-modules      mutter-common-bin
  gnome-settings-daemon-common      libgl1                             libpixman-1-0                nautilus
  gnome-shell                       libgl1-mesa-dri                    libplist-2.0-4               nautilus-data
  gnome-shell-common                libgles2                           libpoppler-cpp2              ocl-icd-libopencl1
  gnome-snapshot                    libglib-object-introspection-perl  libpoppler-glib8t64          orca
  gnome-software                    libglib-perl                       libpoppler147                osinfo-db
  gnome-software-common             libglib2.0-bin                     libportal-gtk4-1             p11-kit
  gnome-software-plugin-deb         libglibmm-2.4-1t64                 libportal1                   p11-kit-modules
  gnome-sushi                       libglibmm-2.68-1t64                libprotobuf32t64             packagekit
  gnome-system-monitor              libglvnd0                          libproxy1v5                  parted
  gnome-terminal                    libglx-mesa0                       libpthreadpool0              pinentry-curses
  gnome-terminal-data               libglx0                            libpulse-mainloop-glib0      pinentry-gnome3
  gnome-text-editor                 libgme0                            libpulse0                    pipewire
  gnome-user-docs                   libgnome-autoar-0-0                libpwquality-common          pipewire-alsa
  gnome-weather                     libgnome-bg-4-2t64                 libpwquality1                pipewire-audio
  gnupg                             libgnome-bluetooth-3.0-13          libpython3.13                pipewire-bin
  gnupg-l10n                        libgnome-bluetooth-ui-3.0-13       libqpdf29t64                 pipewire-pulse
  gpg                               libgnome-desktop-3-20t64           libqrencode4                 poppler-data
  gpg-agent                         libgnome-desktop-4-2t64            libraptor2-0                 poppler-utils
  gpgconf                           libgnome-rr-4-2t64                 libraqm0                     psmisc
  gpgsm                             libgoa-1.0-0b                      librav1e0.7                  python3-brlapi
  grilo-plugins-0.3                 libgoa-1.0-common                  libraw1394-11                python3-cairo
  gsettings-desktop-schemas         libgoa-backend-1.0-2               libre2-11                    python3-cups
  gstreamer1.0-gl                   libgom-1.0-0t64                    librest-1.0-0                python3-cupshelpers
  gstreamer1.0-gtk3                 libgomp1                           libroc0.4                    python3-dbus
  gstreamer1.0-gtk4                 libgpgme11t64                      librsvg2-2                   python3-distro
  gstreamer1.0-libcamera            libgpgmepp6t64                     librsvg2-common              python3-gi
  gstreamer1.0-packagekit           libgphoto2-6t64                    librtmp1                     python3-louis
  gstreamer1.0-pipewire             libgphoto2-port12t64               libsamplerate0               python3-speechd
  gstreamer1.0-plugins-bad          libgpm2                            libsane-common               python3-xdg
  gstreamer1.0-plugins-base         libgraphene-1.0-0                  libsane1                     samba-libs
  gstreamer1.0-plugins-good         libgraphite2-3                     libsasl2-2                   simple-scan
  gstreamer1.0-x                    libgrilo-0.3-0                     libsasl2-modules-db          sound-theme-freedesktop
  gtk-update-icon-cache             libgs-common                       libsbc1                      speech-dispatcher
  gtk2-engines                      libgs10                            libsdl2-2.0-0                speech-dispatcher-audio-plugins
  gvfs                              libgs10-common                     libsecret-1-0                ssl-cert
  gvfs-backends                     libgsf-1-114                       libsecret-common             system-config-printer-common
  gvfs-common                       libgsf-1-common                    libsensors-config            system-config-printer-udev
  gvfs-daemons                      libgsm1                            libsensors5                  tecla
  gvfs-fuse                         libgsound0t64                      libserd-0-0                  timgm6mb-soundfont
  gvfs-libs                         libgspell-1-3                      libsharpyuv0                 tinysparql
  heif-gdk-pixbuf                   libgspell-1-common                 libshine3                    totem
  heif-thumbnailer                  libgssdp-1.6-0                     libshout3                    totem-common
  hicolor-icon-theme                libgstreamer-gl1.0-0               libshumate-1.0-1             tracker-extract
  libaa1                            libgstreamer-plugins-bad1.0-0      libshumate-common            udisks2
  libabsl20240722                   libgstreamer-plugins-base1.0-0     libsigc++-2.0-0v5            upower
  libaccountsservice0               libgstreamer1.0-0                  libsigc++-3.0-0              usb.ids
  libadwaita-1-0                    libgtk-3-0t64                      libsm6                       webp-pixbuf-loader
  libao-common                      libgtk-3-common                    libsmbclient0                wireplumber
  libao4                            libgtk-4-1                         libsnappy1v5                 x11-common
  libaom3                           libgtk-4-common                    libsndfile1                  x11-xkb-utils
  libappstream5                     libgtk-vnc-2.0-0                   libsnmp-base                 x11-xserver-utils
  libarchive13t64                   libgtk3-perl                       libsnmp40t64                 xdg-dbus-proxy
  libaspell15                       libgtkmm-4.0-0                     libsord-0-0                  xdg-desktop-portal
  libass9                           libgtksourceview-4-0               libsoundtouch1               xdg-desktop-portal-gnome
  libassuan9                        libgtksourceview-4-common          libsoup-2.4-1                xdg-desktop-portal-gtk
  libasyncns0                       libgtksourceview-5-0               libsoup-3.0-0                xdg-user-dirs-gtk
  libatasmart4                      libgtksourceview-5-common          libsoup-3.0-common           xdg-utils
  libatk-adaptor                    libgtop-2.0-11                     libsoup2.4-common            xfonts-encodings
  libatk-bridge2.0-0t64             libgtop2-common                    libsoxr0                     xfonts-utils
  libatk1.0-0t64                    libgudev-1.0-0                     libspa-0.2-bluetooth         xkbset
  libatspi2.0-0t64                  libgupnp-1.6-0                     libspa-0.2-modules           xserver-common
  libaudio2                         libgupnp-igd-1.6-0                 libspandsp2t64               xwayland
  libavahi-client3                  libgusb2                           libspectre1                  yelp
  libavahi-common-data              libgvnc-1.0-0                      libspeechd-module0           yelp-xsl
  libavahi-common3                  libgweather-4-0t64                 libspeechd2                  zenity
  libavahi-glib1                    libgweather-4-common               libspeex1                    zenity-common
  libavc1394-0                      libgxps2t64                        libspeexdsp1
  libavcodec61                      libhandy-1-0                       libspelling-1-2

Suggested packages:
  adwaita-icon-theme-legacy    gnome                          libdv-bin                 opus-tools              fonts-nanum
  colord-sensor-argyll         gnome-color-manager            oss-compat                libparted-dev           python-dbus-doc
  cpp-doc                      gnome-initial-setup            libdvdcss2                libparted-i18n          python-pyxdg-doc
  gcc-14-locales               usbguard                       libenchant-2-voikko       pulseaudio              libttspico-utils
  cpp-14-doc                   gir1.2-malcontent-0            exiv2                     raptor2-utils           espeak
  cups-bsd                     gir1.2-telepathyglib-0.12      libfftw3-bin              libraw1394-doc          mbrola
  cups-pdf                     gir1.2-telepathylogger-0.2     libfftw3-dev              librsvg2-bin            speech-dispatcher-doc-cs
  foomatic-db-compressed-ppds  gnome-shell-extension-prefs    freerdp3-x11              avahi-daemon            speech-dispatcher-festival
  | foomatic-db                gnome-software-plugin-flatpak  libgd-tools               hplip                   speech-dispatcher-cicero
  smbclient                    gnome-software-plugin-snap     libxml-libxml-perl        lm-sensors              speech-dispatcher-flite
  antiword                     apt-config-icons-hidpi         gphoto2                   serdi                   speech-dispatcher-espeak
  docx2txt                     gstreamer1.0-libav             gpm                       snmp-mibs-downloader    fluid-soundfont-gm
  imagemagick                  pkexec                         libvisual-0.4-plugins     sordi                   gnome-codec-install
  gnome                        gpg-wks-server                 gstreamer1.0-tools        speex                   btrfs-progs
  | kde-standard               parcimonie                     libheif-plugin-ffmpegdec  libwacom-bin            f2fs-tools
  | xfce4                      xloadimage                     libheif-plugin-jpegdec    gstreamer1.0-alsa       nilfs-tools
  | wmaker                     scdaemon                       libheif-plugin-jpegenc    libwildmidi-config      reiserfsprogs
  dbus-user-session            frei0r-plugins                 libheif-plugin-j2kdec     python3-argcomplete     udftools
  tor                          samba-common                   libheif-plugin-j2kenc     opencl-icd              udisks2-btrfs
  nautilus-sendto              libsndio6.1                    libheif-plugin-kvazaar    brltty                  udisks2-lvm2
  unrar                        lrzip                          libheif-plugin-rav1e      parted-doc              xfsprogs
  evolution                    aspell                         libheif-plugin-svtenc     pinentry-doc            libspa-0.2-libcamera
  fonts-freefont-otf           nas                            libusbmuxd-tools          pulseaudio-utils        wireplumber-doc
  | fonts-freefont-ttf         libcuda1                       jackd2                    fonts-japanese-mincho   nickle
  fonts-texgyre                libnvcuvid1                    liblcms2-utils            | fonts-ipafont-mincho  cairo-5c
  libpam-fprintd               libnvidia-encode1              liblrdf0-dev              fonts-japanese-gothic   xorg-docs-core
  libpam-sss                   mdadm                          nvme-cli                  | fonts-ipafont-gothic
  libpam-pkcs11                libbluray-bdj                  libportaudio2             fonts-arphic-ukai
  texlive-binaries             libfont-freetype-perl          libsndio7.0               fonts-arphic-uming

Recommended packages:
  dbus-user-session               firefox-esr                        libaacs0                     | vdpau-driver
  gtk3-nooverlayscrollbar         | firefox                          libcamera-ipa                mesa-vulkan-drivers
  gtk3-nocsd                      | chromium                         libcanberra-gtk3-module      | vulkan-icd
  avahi-daemon                    | chromium-browser                 default-libdecor-0-plugin-1  gstreamer1.0-libav
  cups-browsed                    | epiphany-browser                 | libdecor-0-plugin-1        libmagickcore-7.q16-10-extra
  ipp-usb                         | gnome-www-browser                enchant-2                    xbrlapi
  liblouisutdml-bin               gnome-tour                         libgdk-pixbuf2.0-bin         packagekit-tools
  | liblouis-bin                  network-manager                    libgphoto2-l10n              systemd
  lynx                            rygel-playbin                      fonts-droid-fallback         rtkit
  xserver-xephyr                  rygel-tracker                      libgtk-3-bin                 speech-dispatcher-espeak-ng
  xserver-xorg                    low-memory-monitor                 libgtk-4-bin                 sound-icons
  iio-sensor-proxy                gnome-keyring-pkcs11               libgtk-4-media-gstreamer     python3-smbc
  modemmanager                    evolution-ews-core                 libheif-plugin-x265          gstreamer1.0-plugins-ugly
  fonts-noto-color-emoji          gnome-session-xsession             libheif-plugin-aomenc        totem-plugins
  cracklib-runtime                pkexec                             hunspell-en-us               dosfstools
  cups-pk-helper                  bolt                               | hunspell-dictionary        ntfs-3g
  fwupd                           gnome-browser-connector            | myspell-dictionary         exfatprogs
  gnome-remote-desktop            ibus                               usbmuxd                      libfile-mimeinfo-perl
  gnome-user-share                switcheroo-control                 libldap-common               libnet-dbus-perl
  libnss-myhostname               unzip                              libmtp-runtime               libx11-protocol-perl
  malcontent-gui                  gnome-software-plugin-fwupd        libpaper-utils               x11-utils
  mobile-broadband-provider-info  nautilus-extension-gnome-terminal  libpipewire-0.3-common       perl-tk
  nm-connection-editor            gnupg-utils                        sane-airscan                 xfonts-base
  | network-manager-gnome         gpg-wks-client                     sane-utils                   docbook-xml
  power-profiles-daemon           wsdd                               libsasl2-modules             fonts-dejavu
  realmd                          aspell-en                          va-driver-all
  rygel                           | aspell-dictionary                | va-driver
  | rygel-tracker                 | aspell6a-dictionary              vdpau-driver-all

Summary:
  Upgrading: 0, Installing: 787, Removing: 0, Not Upgrading: 0
  Download size: 455 MB
  Space needed: 1,790 MB / 220 GB available

Continue? [Y/n] y


root@m1330:~# pfetch 
    ___       os     Devuan GNU/Linux 6 (excalibur/ceres)
   (.· |      host   XPS M1330
   (<> |      kernel 6.12.17-amd64
  / __  \     uptime 20m
 ( /  \ /|    pkgs   1169
_/\ __)/_)    memory 172M / 7946M
\/-____\/

root@m1330:~# 


