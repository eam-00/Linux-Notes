**MBP WiFi**:

Configure the WiFi card on the Macbook Pro Mid 2012 ([MacBookPro9,2 1.0](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-i5-2.5-13-mid-2012-unibody-usb3-specs.html)) on Debian 12 "Bookworm".
____

Chipset: `BCM4331`  
Link: https://wiki.debian.org/wl

____

Add to the bottom of `/etc/apt/sources.list`: 

```
deb http://deb.debian.org/debian bookworm main contrib non-free-firmware non-free
```
Issue as root or via sudo:
```
apt-get update
apt-get install linux-image-$(uname -r|sed 's,[^-]*-[^-]*-,,') linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms
modprobe -r b44 b43 b43legacy ssb brcmsmac bcma
modprobe wl
```
