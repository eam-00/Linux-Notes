
# Tips for Desktop Environments
## Budgie
### Themes
Should be on ~/.local/share/themes/. Also, it can be an alias to the ~/.themes/.  

``ln -s ~/.themes/ ~/.local/share/themes/``

## GNOME
### Keyboard Shortcuts
Make Alt + Tab cycle thru all the windows:  

Settings > Keyboard > View and Customize Shortcuts > Navigation > Switch Windows > Alt Tabs

Make Caps Lock a Ctrl key:  

Tweaks > Keyboad & Mouse > Additional Layout Options > Caps Lock behavior > Make Caps Lock an additional Ctrl

Emacs Keybindings:  

Tweaks > Keyboad & Mouse > Emacs Input

## Chrome
Set Chrome startup options:

Edit (create) the file ``~/.config/chrome-flags.conf``:

--disk-cache-dir=/some/dir/here
