
# Tips for Desktop Environments
## Budgie
### Themes
Should be on ~/.local/share/themes/. Also, it can be an alias to the ~/.themes/.  

``ln -s ~/.themes/ ~/.local/share/themes/``

## GNOME
### Keyboard Shortcuts
- Make Alt + Tab cycle thru all the windows:  

On Debian Bullseye {GNOME 3.38.5}  
Settings > Keyboard Shortcuts > Switch Windows > Alt Tab

Select "*Replace*" if the shortcut is already in use.

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

### Keyboard Layout

Change the layout from the traditional US to the convenient "English (US, alt. intl.)"  

Settings > Region & Language > Input Sources > Click on the *+* below "English" > Then click on English

Then scroll until you find "English (US, alt. intl.)"

### Set a Solid Color as Desktop

gsettings set org.gnome.desktop.background picture-uri none
gsettings set org.gnome.desktop.background primary-color '#BF4040'
gsettings set org.gnome.desktop.background color-shading-type 'solid'

### Mouse
- Resize and move windows with Alt + Mouse buttons  

Tweaks > Windows 

Enable the option:  
Resize with Secondary-Click
Window Action Key Alt 

- Tap to Click

Settings > Mouse & Touchpad > Touchpad > Touch to Click

### Disable Touchpad When A Mouse Is Plugged

``gsettings set org.gnome.desktop.peripherals.touchpad send-events disabled-on-external-mouse``

To revert it:

``gsettings set org.gnome.desktop.peripherals.touchpad send-events enabled``

### Start Programs Automagically upon Login

Create the file on the ``~/.config/autostart/`` directory.  
With the ".desktop" extension:  

``~/.config/autostart/dropbox.desktop``

Here is an example of the start script for Dropbox:

        [Desktop Entry]
        Type=Application
        Exec=/home/eam-00/.dropbox-dist/dropboxd
        Hidden=false
        X-GNOME-Autostart-enabled=true
        Name=Dropbox
        Comment=Online Backups


## Chrome
- Set Chrome browser startup options:

Edit (create) the file ``~/.config/chrome-flags.conf`` and add this:

``--disk-cache-dir=/some/dir/here``

Alternatively:

``cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/``

Edit the file like this:

``Exec=/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --enable-smooth-scrolling --force-dark-mode %U``

Also to set a dark Chrome, you can go to:  

``chrome://flags/``  
and look for the entry called *Auto Dark Mode for Web Contents* and set it to **Enabled**.

Other startup flags:

``/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --use-gl=desktop --force-device-scale-factor=2.5 --enable-smooth-scrolling --force-dark-mode %U``

This are the flags currently using on the HP Envy:

``/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --use-gl=desktop --force-device-scale-factor=2.2 --force-dark-mode %U``

## xrandr
Set the screen brightness thru xrandr.  
Get the screen info:

        xrandr --current --verbose

ID your display and then issue:

        xrandr --output YOUR-DISPLAY --brightness 0.8
