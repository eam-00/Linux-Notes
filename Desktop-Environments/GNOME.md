## GNOME

### Theming

Check icon theme:  
`gsettings get org.gnome.desktop.interface icon-theme`

Set icon theme:  
`gsettings set org.gnome.desktop.interface icon-theme 'Papirus'`

Go back to the default theme:  
`gsettings set org.gnome.desktop.interface icon-theme 'Adwaita'`

Set GTK theme:  
`gsettings set org.gnome.desktop.interface gtk-theme 'adw-gtk3-dark'`

Set mouse theme:  
`gsettings set org.gnome.desktop.interface cursor-theme 'my-Adwaita'`

Include the day of the week on the date:  
`gsettings set org.gnome.desktop.interface clock-show-weekday true`

### Keyboard

Move windows by pressing Alt + Left mouse button:   
`gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier '<Alt>'`

`gsettings set org.gnome.desktop.wm.preferences resize-with-right-button true`


### Gnome Extensions

#### Activities Workspace Name

Link: https://github.com/ahmafi/gnome-activities-workspace-name

Set Workspaces first:
```
gsettings set org.gnome.desktop.wm.preferences workspace-names "['1', '2', '3']"
```
* Download the extension
* cd $DONWLOADS
* `unzip gnome-activities-workspace-name-main.zip`
* `cd gnome-activities-workspace-name`
* `mkdir -p ~/.local/share/gnome-shell/extensions/activitiesworkspacename@ahmafi.ir`
* `cp -r src/* ~/.local/share/gnome-shell/extensions/activitiesworkspacename@ahmafi.ir`
* Re start (X11) or logout (Wayland) from GNOME.
* `gnome-extensions enable activitiesworkspacename@ahmafi.ir`


#### WorkspaceSwitcherWrapAround

Link: https://github.com/theychx/WorkspaceSwitcherWrapAround/tree/master

* Download the extension
* cd $DONWLOADS
* `unzip WorkspaceSwitcherWrapAround-master.zip`
* `cd WorkspaceSwitcherWrapAround-master/`
* `mkdir -p ~/.local/share/gnome-shell/extensions/workspace-switch-wraparound@theychx.org`
* `cp -r src/* ~/.local/share/gnome-shell/extensions/workspace-switch-wraparound@theychx.org`
* Re start (X11) or logout (Wayland) from GNOME.
* `gnome-extensions enable workspace-switch-wraparound@theychx.org`

#### Executor

Link: https://github.com/raujonas/executor

Should be used with the [GenMon Plugin scripts](https://github.com/eam-00/Util-scripts/tree/master/Genmon).


#### Manually install extensions

- Download the extension
- Extract the zip file
- cd onto the extracted directory   
  On the directory there is a file named "metadata.json".  
  Do a less on the file and look for the value on the "uuid" variable.
- Rename the directory of the Gnome extension:  
  Go up one directory and then rename the directory with the value that the "uuid" variable has.
- Copy the renamed directory to your user’s GNOME extension directory:  
``~/.local/share/gnome-shell/extensions/``

#### Debug extensions

```
journalctl -S "2025-01-07" -g extension
```
