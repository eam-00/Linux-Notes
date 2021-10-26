# Some Miscellaneous SEP Notes:

- Donwload the latest Virus Definitions by hand:  
``wget http://definitions.symantec.com/defs/static/symcdefs-unix.sh``

- Check the version of the installed client:  
``/opt/Symantec/symantec_antivirus/sav info -p``

    - Output:  
``14.3 (14.3 XXX) build XXXX (XX.X.XXXX.XXXX)``

- List status:  
``/opt/Symantec/symantec_antivirus/sav info -a``

    - Output:
 ``Enabled``

- Update Virus Definitions:  
``/opt/Symantec/symantec_antivirus/sav liveupdate -u``

- List Update Status:  
``/opt/Symantec/symantec_antivirus/sav liveupdate -v``

   - Output:  
    Frquency:                       Hourly

- Run a scan:  
``/opt/Symantec/symantec_antivirus/sav manualscan -s /var``

- For the newest SEP release:  
``cd /usr/lib/symantec/``  
And issue:   
``./status.sh``


   
   
