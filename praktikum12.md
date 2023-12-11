# Praktikum 12 aruanne
Kaheteistkümnendas praksis tegelesime skriptide loomisega Linuxis.

### Ülesanne 3:

##### skript:
```
#!/bin/sh
echo "Sisesta oma nimi:"
read nimi
echo "Sisesta oma eriala:"
read eriala
echo "Sisesta oma matriklinumber:"
read number
echo "$nimi, $eriala ja $number"
```
##### ekraanivaade:

![image](https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/cd49ca95-d6a6-43a7-820c-e1f007fd1fcf)

### Ülesanne 4:

##### skript:
```
#!/bin/bash
laiend1=$1
laiend2=$2
for i in $(ls); do
    fail=$i   
    if [ ${i##*.} = $1 ]; then   
        mv $i ${fail/$1/$2}      
    fi 
done
```
##### ekraanivaade:

<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/d8e8a007-f3ff-4479-8015-52f7cc51264f">

### Ülesanne 5:

##### skript:
```
#!/bin/bash
nimi=$1
IFS=$'\n'
for rida in $(ps aux | grep "$nimi" | grep -v grep); do
    pid=$(echo $rida | tr -s ' ' | cut -d ' ' -f2)
    echo "$nimi - $pid"
done
```
##### ekraanivaade:

<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/670b75d6-191f-4c59-a461-ab5a52eda6f0">

### Ülesanne 6

##### skript:
```
#!/bin/bash
astenda () {
    if [ $2 -eq 0 ]; then
        echo 1
    elif [ $2 -ge 1 ]; then
        a=$(($1 * $(astenda $1 $(($2 - 1)))))
        echo $a
    fi
}

x=$(astenda 9 5)
echo "$x"
```
##### ekraanivaade:

<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/d35f1771-22b2-4c5a-b796-cc37185716a1">

### Ülesanne 7
##### ekraanivaated:
<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/da5e2cc5-5b8c-49c2-994b-9542da337eda">
<img width="961" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/314e3692-f5d7-4d0f-97c4-e12249f2dfc9">





