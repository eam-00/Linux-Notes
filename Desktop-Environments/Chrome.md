# Chrome

## Install

## Set Chrome browser startup options

Edit (create) the file ``~/.config/chrome-flags.conf`` and add this:

``--disk-cache-dir=/some/dir/here``

Alternatively:

``cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/``

And then search on the file for the string and edit it like this:

``Exec=/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --enable-smooth-scrolling --force-dark-mode %U``

Also to set a dark Chrome, you can go to:  

``chrome://flags/``

and look for the entry called *Auto Dark Mode for Web Contents* and set it to **Enabled**.

Other startup flags:

``/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --use-gl=desktop --force-device-scale-factor=2.5 --enable-smooth-scrolling --force-dark-mode %U``

This are the flags currently using on the HP Envy:

``/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --use-gl=desktop --force-device-scale-factor=2.2 --force-dark-mode %U``

## Disable Tab Hover Previews in Chrome

Launch Chrome and open: ``chrome://flags/#tab-hover-card-images``

Set it to: *Disabled*

Relaunch Chrome for the changes to make it work.

## Delete "All Bookmarks" from the Bookmarks Bar

Open: ``chrome://flags/#power-bookmarks-side-panel``

Set it to: *Disabled*



