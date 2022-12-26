# Upgade from Buster to Bullseye

## To start with

    optiplex-755-usff:~/$ date
    Sun 25 Dec 2022 02:00:54 AM -03
    optiplex-755-usff:~/$ ./pfetch 
      _____      eam-00@optiplex-755-usff
     /  __ \     os     Debian GNU/Linux 10 (buster)
    |  /    |    host   3113BS3 ThinkPad X201 Tablet
    |  \___-     kernel 4.19.0-23-amd64
    -_           uptime 1h 12m
      --_        pkgs   1557
             memory 681M / 7774M


sudo apt update
sudo apt upgrade 

optiplex-755-usff:~/Local/Scripts$ date
Sun 25 Dec 2022 02:37:22 AM -03
optiplex-755-usff:~/Local/Scripts$ ./pfetch 
  _____      epsilon-alpha-mu@optiplex-755-usff
 /  __ \     os     Debian GNU/Linux 11 (bullseye)
|  /    |    host   3113BS3 ThinkPad X201 Tablet
|  \___-     kernel 4.19.0-23-amd64
-_           uptime 1h 48m
  --_        pkgs   1614
             memory 727M / 7774M

sudo apt full-upgrade




