# Chrome

## Install

## Set Chrome browser startup options

Edit (create) the file ``~/.config/chrome-flags.conf`` and add this:

``--disk-cache-dir=/some/dir/here``

Alternatively:

``cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications/``

And then search on the file for the string and edit it like this:

``Exec=/usr/bin/google-chrome-stable --disk-cache-dir=/some/dir/here --enable-smooth-scrolling --force-dark-mode %U``

## Disable Tab Hover Previews in Chrome

