# Keyboard Settings

## Make the CapsLock key work as another Ctrl key

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

Make sure the trigger is set: **On Login**.


## Set the Page Back & Page Forward as PgUp & PgDown buttons
