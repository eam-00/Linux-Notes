# Logs
## Logrotate

Edit the file /etc/logrotate.conf:

        compress
        dateext

Uncomment the 'compress' entry and add the 'dateext' one in order to have the rotated log files compresssed and the date of the rotation appended to the file name of the log.  

syslog-20210909.gz

## Control your /var/log/journal

List disk usage:

Archived and active journals take up 1.5G in the file system.

