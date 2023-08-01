TASK2 DAY2
Your task is to create a bash script that takes a directory path as a command-line argument and performs a backup of the directory. 
The script should create timestamped backup folders and copy all the files from the specified directory into the backup folder.
Additionally, the script should implement a rotation mechanism to keep only the last 3 backups. 
This means that if there are more than 3 backup folders, the oldest backup folders should be removed to ensure only the most recent backups are retained.
...................................................................................................................................................................
#!/bin/bash

src_dir=$1

curr_time=$(date +"%y-%m-%d_%H-%m-%S")

backupFile=$curr_time.tgz

echo "$curr_time"

tar czf $backupFile --absolute-names $src_dir

echo "backup done"

#count no of file

#ls -l | wc -l

#take only 3 latest file, remove others
rm -f $(ls -1t *.tgz | tail -n +3)
