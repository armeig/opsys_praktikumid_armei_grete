# Praktikum 7 aruanne
Seitsmendas praktikumis õppisin,  kuidas lokaalseid ja võrgukettaid Windowsi ja Linuxi keskkonnas kasutada.

1) Andmekandjat tuleb lähtestada, et eelnevad ebavajalikud andmed saaksid kustutatud ja andmekandja puhastatud, et seda saaks uuesti kasutada.
2) GPT toetab rohkem partitsioone(sadu) ilma, et oleks vaja laiendatud partitisioone (extended partitions), kui MBR(4 primaarset partitisooni).
   MBR ei halda tõhusalt üle 2TB, aga GPT haldab.
   GPT on kaasaegsem tehnoloogia ja saab hakkama uuemate arvutisüsteemide ja operatsioonisüsteemidega. MBR pärineb ajast, kui kõvaketaste maht oli palju väiksem.
   GPT-l on primaarse GPT päise ja partitsiooni varukoopiat, mis kaitseb kettal olevaid andmeid paremini.
   GPT kasutab tsüklilist kontrollsummat selleks, et kindlustada, et andmed ei ole muutunud ega kahjustunud edastamise või salvestamise ajal.
   GPT ühildub UEFI-ga, MBR ei ühildu.
3) https://kodu.ut.ee/~armei/hdd.png
4) ![image](https://github.com/armeig/praktikumid_armei_grete/assets/145908210/78f7686b-7533-4c11-ba0c-b783c04d9451)

5) -o ro - ro tähendab read only ja seega saab andmekandjalt ainult andmeid lugeda, neid ei saa muuta, lisada ega kustutada. -t auto hõlbustab automaatselt tuvastada andmekandja failisüsteemi tüübi ja haakida selle vastavalt. "auto" väärtus tähendab, et süsteem peaks ise otsustama, milline failisüsteem andmekandjal on.
6) Ubuntu asendas auto-parameetri väärtusega read-only ehk andmekandjalt on võimalik andmeid ainult lugeda.
7) ![image](https://github.com/armeig/praktikumid_armei_grete/assets/145908210/e074f924-b2b9-412a-8c1d-8856feff26d9)
