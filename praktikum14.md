# Praktikum 14 aruanne
Neljateistkümnendas praksis tutvusime Microsoft Azure keskkonnaga, seadsime üles virtuaalmasina ja kasutasime WSL-i, et leida kadunud paroole.

Ülesanne 1: 
![image](https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/c7b02ae7-a22b-4bb3-be43-7bd821559d14)

Ülesanne 2: 
![image](https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/ac1c1d4c-58e2-45ac-954b-98cb715ca2cd)

Ülesanne 3:
![image](https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/1b8c4454-56d0-46a0-b5aa-3f5b3cfb4d64)

Ülesanne 4:
<img width="960" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/2b3530d7-d4be-4d43-af3c-69ad8cfc9c74">

Ülesanne 5:
<img width="960" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/0fcb87d6-1ac6-429f-a7b5-2414f4325388">

Ülesanne 6:
<img width="960" alt="image" src="https://github.com/armeig/opsys_praktikumid_armei_grete/assets/145908210/24dc423f-584d-4288-a3fa-e181db6ffbff">

Kõigepealt oli mul vaja teha kindlaks, millised failid üldse sisaldavad infot ehk siis kasutasin käsku __ls -l | awk '$5 != 0'__ , sest see ütleb, et näita mulle faile, mille viies veerg ehk failisuuruse veerg ei võrduks nulliga. Seejärel vaatasin kõik antud väljundid ükshaaval kasutades käsku __cat__ läbi ning leidsin, et mõistlik oleks otsida käsuga __find . -type f -size +0 -exec grep -l 'parool' {} +__ , millised failid sisaldavad sõna parool ning lõpuks leidsin käsu __find . -type f -size +0 -exec grep -q 'parool' {} \; -exec grep -H 'parool' {} \;__ abil iga faili nime ja tema sisu. Mul polnud õrna aimu, kas ma oleks pidanud kasutama kuidagi seda ostechnix.secret faili, aga kuna see on krüpteeritud ja ma ei oska seda dekrüpteerida siis ma jätsin ta sinna paika. Kuigi praegune lahendus tunudb vale.


