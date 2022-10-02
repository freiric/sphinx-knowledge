Backup
======

rsync
-----

.. code-block::

   rsync -azvvPe ssh --bwlimit=30 source user@domain:target 

   --bwlimit=KBPS          limit I/O bandwidth; KBytes per second


   -P                          same as --partial --progress

   -H, --hard-links            preserve hard links

   -a preserves the date and times, and permissions of the files (same as -rlptgoD).

     With this option rsync will:
     Descend recursively into all directories (-r),

     - copy symlinks as symlinks (-l),

     - preserve file permissions (-p),

     - preserve modification times (-t),

     - preserve groups (-g),

     - preserve file ownership (-o), and

     - preserve devices as devices (-D).

   -e specify the remote shell to use

Some other solutions: 
based on rsync:

 - unison, rdiffbackup, rsnapshot
   
professional

 - Bacula, amanda

