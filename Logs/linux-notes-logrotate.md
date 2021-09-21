# Logs
## Logrotate

Edit the file /etc/logrotate.conf:

        ccompress
        dateext

Uncomment the 'compress' entry and add the 'dateext' one in order to have the rotated log files compresssed and the date of the rotation appended to the file name of the log.  
The resulting file will be renamed, after logrotate excution, like this:

``syslog-20210909.gz``

Another example of logrotate.conf:  

        /var/log/cisco.log {
                weekly
                rotate 4
                notifempty
                copytruncate
        }


## Limit disk usage of /var/log/journal

* List disk usage:  

``sudo journalctl --disk-usage``

Example output from the above command:  

``Archived and active journals take up 1.5G in the file system.``

* Clearing everything older than 30 days:

``sudo journalctl --vacuum-time=30d``

* Keep only 2GB worth of logs, clearing everything that exceeds that limit:  

``sudo journalctl --vacuum-size=2G``

