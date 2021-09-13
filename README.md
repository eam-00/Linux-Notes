- [Manjaro](/Manjaro/linux-notes-manjaro.md)
- [Keyboard Settings](/Keyboard/linux-notes-keyboard.md)
- [Logrotate](/Logs/linux-notes-logrotate.md)


**Manjaro**  
*Some notes and tips that I found useful while setting up & running Manjaro.*



 









**Logrotate**  

Edit the file /etc/logrotate.conf

        compress
        dateext

Uncomment the 'compress' entry and add the 'dateext' one in order to have the rotated log files compresssed and the date of the rotation appended to the file name of the log.

