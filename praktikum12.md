# Praktikum 12 aruanne

### Ülesanne 3:

##### skript:

#!/bin/sh

echo "Sisesta oma nimi:"

read nimi

echo "Sisesta oma eriala:"

read eriala

echo "Sisesta oma matriklinumber:"

read number

echo "$nimi, $eriala ja $number"

##### ekraanivaade:

![image](https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/cd49ca95-d6a6-43a7-820c-e1f007fd1fcf)

### Ülesanne 4:

##### skript:

#!bin/bash

laiend1=$1

laiend2=$2

for i in $(ls); do

    fail=$i
    
    if [ ${i##*.} = $1 ]; then
    
        mv $i ${fail/$1/$2}
        
    fi
    
done

##### ekraanivaade:

<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/d8e8a007-f3ff-4479-8015-52f7cc51264f">

### Ülesanne 5:

