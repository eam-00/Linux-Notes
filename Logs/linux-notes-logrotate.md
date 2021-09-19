# Logs
## Logrotate

Edit the file /etc/logrotate.conf:

        compress
        dateext

Uncomment the 'compress' entry and add the 'dateext' one in order to have the rotated log files compresssed and the date of the rotation appended to the file name of the log.  
The resulting file will be renamed, after logrotate excution, like this:

``syslog-20210909.gz``

## Limit disk usage of /var/log/journal

* List disk usage:  

``sudo journalctl --disk-usage``

Example output from the above command:  

``Archived and active journals take up 1.5G in the file system.``

* Clearing everything older than 30 days:
