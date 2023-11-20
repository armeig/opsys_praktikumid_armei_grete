# Praktikum 9 aruanne
Küsimus | Linux | Linuxis kasutatud käsklus | Windows | Windowsis kasutatud tööriist
--- | --- | --- | --- | ---
Mitu protsessi kokku arvutis käib? | 216 | ps -aux &#124; wc -l | 143 | Task Manager -> Performance -> Processes
Milline on kõige esimesena käivitatud protsess? (lisalugemine: init vs systemd) | /sbin/init splash | ps axo pid,cmd,comm,etime | smss.exe | Process Explorer -> Start Time
Milliste kasutajate protsesse arvutis käib? (arvesta ka süsteemiprotsesse, mitte ainult sisse logitud kasutajaid) | avahi, colord, grete, kernoops, messagebus, root, rtkit, syslog, systemd-oom, systemd-resolve, systemd-timesync, USER | ps -eo user &#124; sort -u | ARMEI-W11\Grete, Font Driver Host\UMFD-0, Font Driver Host\UMFD-2, NT AUTHORITY\LOCAL SERVICE, NT AUTHORITY\NETWORK SERVICE, NT AUTHORITY\SYSTEM, Window Manager\DWM-2 | Process Explorere -> User Name
Kui kaua on arvuti järjest töötanud (up time)? (Alternatiivselt võib vastata ka, millal (kuupäev ja kellaaeg) arvuti viimati käima pandi.) | 48min | uptime | 1h 2min 28s | Task Manager -> Performance -> Up time
Milline protsess käivitati kõige hiljem (viimasena)? (Mitte võtta arvesse programmi, millega seda infot otsida.) | [kworker/u4:2] | ps axo pid,cmd,comm,etime | svchost.exe | Task Manager -> Performance -> Start Time
Milline on kõige rohkem protsessoriaega võttev protsess? | gnome-shell | top | Microsoft Windows Malicious Software Removal Tool | Task Manager -> Processes -> CPU
Milline on kõige rohkem virtuaalmälu (aadressiruumi, commit, Virtual Size) võttev protsess? | /usr/bin/gnome-shell | htop -> F6 -> M_VIRT | msedge.exe | Process Explorer -> Virtual Size
Milline on kõige rohkem füüsilist mälu (working set) võttev protsess? | /usr/bin/gnome-shell | htop -> F6 -> M_RESIDENT | explorer.exe | Process Explorer -> Working Set
Kui palju füüsilisest mälust (Physical Memory) on vaba? | 298Mi | free -h | 1.4GB | Task Manager -> Performance -> Memory -> Available
Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt? | 7,7GB 37% | df -h -> Avail ja 100%-Use% | 31.56GB 50% | Disk Management -> Free Space/%Free
Milline on kõige suurem kõvakettal olev fail ja kõige suurem alamkaust? | /usr ja /var/lib/snapd/snaps/gnome-42-2204_141.snap | sudo du -a / &#124; sort -n -r &#124; head -n 2 ja sudo find / -type f -exec du -h {} + &#124; sort -rh &#124; head -n | Windows,  | 
12) Võrrelge terminali käskude: (sha1sum /dev/zero &#124; sha1sum /dev/zero) ja (sha1sum /dev/urandom &#124; sha1sum /dev/urandom) protsessori kasutust. Võrdluseks avage teine terminaliaken ja top samaaegseks käivitamiseks. Uurige, millisele CPU alamtegevusele us, sy, id, wa, st jne kulub enim protsessori aega ja mitu protsenti kulub kummagi käsu korral. (Ainult Linuxis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit. 
13) Windows
    1. Milline protsess kõige rohkem salvestusseadmele kirjutab?
    2. Millisesse faili eelmise küsimuse protsess kõige rohkem kirjutab?
    3. Milline protsess kõige rohkem salvestusseadmelt loeb? 
    4. Millisest failist eelmise küsimuse protsess kõige rohkem loeb?
14) Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga? Vali antud protsessi poolt kasutatavatest ühendustest üks ning kirjuta välja järgnev: kohalik IP-aadress, kohalik port, ühenduse teise poole IP-aadress, port, latents ja antud ühenduse poolt kasutatav võrguliikluse kogumaht. (Ainult Windowsis) Lisa ka ekraanipilt aruande juurde näiteks pärast tabelit.
15) Sõber kurdab, et tema arvuti on oluliselt aeglasemaks muutunud. Milliseid konkreetseid programme või käsureakäske kasutad põhjustaja tuvastamiseks. Mõlemal juhul kirjuta, mida konkreetselt jälgid (nt mis aken, veerud, numbrid jne). (Vali Linuxis või Windowsis)
