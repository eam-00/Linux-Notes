# Keyboard Settings

Miscelaneous notes & tips for keyboard on XFCE

## Make the CapsLock key work as another Ctrl key

Edit the file ``/etc/default/keyboard``:  

        XKBMODEL="pc105"
        XKBLAYOUT="us"
        XKBVARIANT="alt-intl"
        XKBOPTIONS="ctrl:nocaps" # Some people prefer "ctrl:swapcaps"

In order for the changes to take effect (on X Window) without rebooting:

``setxkbmap -option ctrl:nocaps``

Another option, on XFCE, would be to add an entry on:

Settings > Session and Startup > Application Autostart > Add Application

Name it whatever you like, same for the description, but be sure to set the command to be:

``/usr/bin/setxkbmap -option ctrl:nocaps``

I had to give the full path to ``setxkbmap``, otherwise it failed.  
Also, make sure the trigger is set to: **On Login**.

![XFCE Sessino and Startup](Pics/rsz_screenshot_2021-09-27_21-40-54.jpg)

## Set the Page Back & Page Forward as PgUp & PgDown buttons

The "old" Thinkpad keyboards have a Page Back and Page Forward buttons right by the arrow keys.  
I find those unbearable annoying and prone to cause disasters.  
Issuing the following, as root or via sudo, turns those keys onto a Page Up and Page Down buttons:  

``setkeycodes e049 159 e051 158 e069 109 e06a 104``

Add the following entry onto root's crontab so it is executed everytime the box reboots, to avoid having to type it every time:  

``@reboot /usr/bin/setkeycodes e049 159 e051 158 e069 109 e06a 104``

This works for keyboards on Thinkpads like the T43, T60, X220, T410, T420.

## Emacs Keybindings on XFCE

Launch XFCE's **"Settings Edditor"**.  
Select  the Channel **"xsettings"** and then the Property **"KeyThemeName"**.  
Add the value to the string **"Emacs"** (without quotes).  
That's it you are done.

If the Property isn't there, simply create a new one (be sure to be on the right Channel).  
Use **"String"** as Type, just like in the screenshot below:

![XFCE Settings Editor](Pics/Screenshot_2021-09-24_20-01-20.jpg)

*Caveat Emptor*:  
Be aware that not all of Emacs keybinds will work and certainly the ones that will work won't work on the whole system, but it is nice to be able to type Ctrl + E and Ctrl + A now and then to go there fast.

## XFCE Window Manager Keyboard Shortcuts

Goto > Settings > Window Manager > Keyboard:

| XFCE Option | Keyboard Combo |
| ----------- | -------------- |
| Show Desktop | Super+D |
| Maximize Window | Super+X |
| Maximize Window Horizontally | Super+H |
| Maximize Window Vertically | Super+V |
| Move Window | Super+M |
| Resize Window | Super+R |
| Toggle Fullscreen | F11 |
| Tile Window to the top | Super+Up |
| Tile Window to the bottom | Super+Down |
| Tile Window to the right | Super+Right |
| Tile Window to the left | Super+Left |
| Close Window | Super+Q |
| Move Window to the Previous Workspace | Shift+Super+Left |
| Move Window to the Next Workspace | Shift+Super+Right |
| Left Workspace | Ctrl+Alt+Left |
| Right Workspace | F6 |
| Workspace 1 | Super+1 |
| Workspace 2 | Super+2 |
| Workspace 3 | Super+3 |
| Workspace 4 | Super+4 |

## XFCE Keyboard Shortcuts for Launching Applications

Goto > Settings > Keyboard > Application Shortcuts

| XFCE Option | Keyboard Combo |
| ----------- | -------------- |
| xfce4-terminal | Super+Enter |
| thunar | Super+T |
| xfce4-popup-applicationsmenu | Super+W |

## Links

Other keyboard resources

* [GNOME Keyboard Shortcuts](https://github.com/eam-00/Linux-Notes/blob/main/Desktop-Environments/desktop-environments-index.md#keyboard-shortcuts)
* [GNOME Keyboard Layout](https://github.com/eam-00/Linux-Notes/blob/main/Desktop-Environments/desktop-environments-index.md#keyboard-layout)

