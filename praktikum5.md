# Praktikum 5 aruanne
Selles praksis tutvusin failiõigustega Linuxis. Mõningad käsud, mida õppisin: umask, chown, setuid, setgid. Samuti sain natuke rohkem teada ACL-st ja sticky bit-st.

### Ülesanne 5-1
a) Kataloogis /tmp/kaust oleva faili minufail.txt lugemiseks on kaustal vajalikud read ja execute õigused (chmod 500 /tmp/kaust) ning minufail.txt õigus peab olema read (chmod 400 /tmp/kaust/minufail.txt).
b) Kataloogis /tmp/kaust oleva faili minufail.txt kustutamiseks on kaustal vajalikud write ja execute õigused (chmod 300 /tmp/kaust) ning minufail.txt õigus peab olema write (chmod 200 /tmp/kaust/minufail.txt).
### Ülesanne 5-2 Seet
Chmod a=x skriptifail pole piisav õigus shelli skriptifaili käivitamiseks, sest ilma read õiguseta ei näe ta, mida ekraanile printida. Seetõttu tuleks sisestada a=rx, et skriptifaili käivitada.
### Ülesanne 5-3
Igal kasutajal on omanimeline grupp, sest nii on kergem kasutajaid organiseerida ja kaustasid kasutajate vahel jagada. Ehk selle asemel, et iga kasutaja peab ise chmod- ja umask-käskude abil õigusi muutma, saab seda teha ühtselt läbi grupi õiguste. 
### Ülesanne 5-4
Tavakasutaja minimaalsed õigused uusfail.txt sisu kuvamiseks on kaustas read ja execute ja failis read.
<img width="961" alt="image" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/de3f3b2d-e256-4465-87d0-111a32fe91a5">
### Ülesanne 5-5
<img width="961" alt="image" src="https://github.com/armeig/praktikumid_armei_grete/assets/145908210/ac1fbffa-50cf-437e-a549-2bc2939e2b24">
_Setuid_-õigust on vaja selleks, et kasutajale anda rohkem privileege. Kasutaja saab programmi käivitamiseks samad õigused, mis on faili omanikul.
### Ülesanne 5-6
Jah, _setuid_ võib vähendada süsteemi turvalisust kui programm pole ettevaatlikult disainitud, sest _setuid_ võib anda volituseta kõrgemad õigused kasutajale.
### Ülesanne 5-7
Yhiskaust-kataloogist saavad sticky bit-õigustega test1(ehk peeter)-kasutaja loodud faile kustutada root, test1 ja opetaja.
### Ülesanne 5-8
> test1@armei-U23:/home/opetaja/klass$ getfacl hinded.txt
> # file: hinded.txt
> # owner: opetaja
> # group: opetaja
> user::rw-
> group::---
> group:direktor:rw-
> mask::rw-
> other::---
### Ülesanne 5-9
Chattr +i-parameetriga faili sisu saab modifitseerida ainult root-kasutaja. Testfail-2 saab kustutada järgmiste käskudega:
> $ sudo chattr -i testfail-2
> $ rm testfail-2
