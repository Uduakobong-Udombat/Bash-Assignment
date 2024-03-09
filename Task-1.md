
#!/usr/bin/bash

second=8

if [[ $1 == "-n" && $2=~^[0-9]+$ ]]
then
  second2=$2
  shift 2
sudo du -h $1 | sort -rh | head -$second2

elif [[ $1 == "-d" ]]
  then
  shift 1
sudo du -h -all $1 | sort -rh | head -$second2

else
        sudo du -h $1 | sort -rh | head -$second2
fi
