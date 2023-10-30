# Praktikum 6 aruanne
Praksis tutvusin protsesside ja nende signaalidega.
## Ülesanne 1
<img width="962" alt="praks6 1" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/ba7180dd-bc5f-46c9-bd1c-860d6d907e70">

## Ülesanne 2
<img width="961" alt="praks6 2" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/948f8667-6b33-4cdd-896f-40c437c328a3">

## Ülesanne 3
<img width="961" alt="praks6 3 1" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/72c5a9ce-39f7-49d8-b90f-efe648295e10">
ps -axu | grep daemon | awk '{print $11, $12, $13}' | sort | tr -d ' '

## Ülesanne 4
<img width="961" alt="image" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/afd01984-be3b-4bb3-9a96-aa7289d4ced0">
ip a | grep 'inet ' | cut -d ' ' -f6 | tail -n1 | cut -d / -f1
ip a | grep 'inet ' | cut -d ' ' -f6 | tail -n1 | cut -d / -f1 >> ipaddress.txt


