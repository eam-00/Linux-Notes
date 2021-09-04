Some notes and tips that I found useful while setting up & running Manjaro.

- Fix “Unable to lock database” error:  
``sudo rm /var/lib/pacman/db.lck``

- The Plain Vanilla Update:  
``sudo pacman -Syu``

- Remove cache packages:  
``sudo pacman -Sc``

- Remove all files from the cache, use the clean switch twice, this is the most aggressive approach and will leave nothing in the cache folder: 
