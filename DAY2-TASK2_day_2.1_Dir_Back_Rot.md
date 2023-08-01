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
