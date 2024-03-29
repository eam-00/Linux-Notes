# Log Management

## Logrotate

Edit the configuration file ``/etc/logrotate.conf``:

        compress
        dateext

Uncomment the '**compress**' entry and add the '**dateext**' one in order to have the rotated log files compressed and the date of the rotation appended to the file name of the log.  
The resulting file will be renamed, after a successful logrotate execution, like this:

``syslog-20210909.gz``

Another example snip from the ``logrotate.conf`` file:  

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

