## tmpfs on /etc/fstab

Setup tmpfs for /tmp and other flags for /

       # <file system>									<mount point>	<type>	<options>								<dump>	<pass>
        /dev/mapper/hpenvy--vg-root                                    /               ext4    relatime,discard,errors=remount-ro      0       1
