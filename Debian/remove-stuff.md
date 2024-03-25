**Deleting stuff from Debian 12 Stable**

Remove unnecessary packages from Debian 12 "Bookworm".

* "Anthy Dictionary editor"
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
