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

Also, make sure the trigger is set to: **On Login**.


## Set the Page Back & Page Forward as PgUp & PgDown buttons

The "old" Thinkpad keyboards has a Page Back and Page Forward buttons right by the arrow keys.  
I find those unbearable annoying and prone to cause disasters. 
Issuing the following, as root or via sudo, turns those keys onto a Page Up and Page Down buttons:  

``setkeycodes e049 159 e051 158 e069 109 e06a 104``

Add that entry onto root's crontab so it is executed everytime the box reboots, to avoid typing it, like this:  

``@reboot /usr/bin/setkeycodes e049 159 e051 158 e069 109 e06a 104``

This works for the keyboards of Thinkpads like the T43, T60, X220, T410, T420.