#!/usr/bin/bash

if [ $# -ne 2 ]
then
      echo "Usage: backupscript.sh <source_directory> <target_directory>"
      echo "try again."
      exit 1
fi

if ! command -v rsync > /dev/null 2>&1
then
      echo "This script requires rsync to be installed."
      echo "please use your distrubution's package manager to install it and try again."
      exit 3
fi

date=$(date +%T_%Y-%m-%d)


rsync_options="-av --delete"

$(which rsync) $rsync_options $1  $2/$date.backup >> backup_$current_date.log

if [ $? -eq 0 ]
then
    tar -cf $2/$date.backup.tar $2/$date.backup && rm -r $2/$date.backup
fi
