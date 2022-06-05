
# Tips for Desktop Environments
## Budgie
### Themes
Should be on ~/.local/share/themes/. Also, it can be an alias to the ~/.themes/.  

``ln -s ~/.themes/ ~/.local/share/themes/``

## GNOME
### Keyboard Shortcuts
- Make Alt + Tab cycle thru all the windows:  

Settings > Keyboard > View and Customize Shortcuts > Navigation > Switch Windows > Alt Tabs

Additionally, if the Alt key is not recognized, do this:  

Tweaks > Keyboad & Mouse > Additional Layout Options > Alt and Win behavior > Alt and Meta are on Alt

- Make Caps Lock a Ctrl key:  

Tweaks > Keyboad & Mouse > Additional Layout Options > Caps Lock behavior > Make Caps Lock an additional Ctrl

Additionally:

Tweaks > Keyboad & Mouse > Additional Layout Options > Caps Lock behavior > Caps Lock is also a Ctrl

- Emacs Keybindings:  

Tweaks > Keyboad & Mouse > Emacs Input

- Circle thru windows on all Virtual desktops:  

``gsettings set org.gnome.shell.window-switcher current-workspace-only false``

## Mouse
- Resize and move windows with Alt + Mouse buttons  

Tweaks > Windows 

Resize with Secondary-Click Check  
Window Action Key Alt 

## Startup Programs on Login

~/.config/autostart/dropbox.desktop

## Chrome
- Set Chrome browser startup options:

Edit (create) the file ``~/.config/chrome-flags.conf`` and add this:

``--disk-cache-dir=/some/dir/here``

Alternatively:

``cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/``

Edit the file like this:

``Exec=/usr/bin/google-chrome-stable --disk-cache-dir=/tmp/cache-chrome --enable-smooth-scrolling %U``

## xrandr
Set the screen brightness thru xrandr.  
Get the screen info:

        xrandr --current --verbose

ID your display and then issue:

        xrandr --output YOUR-DISPLAY --brightness 0.8
