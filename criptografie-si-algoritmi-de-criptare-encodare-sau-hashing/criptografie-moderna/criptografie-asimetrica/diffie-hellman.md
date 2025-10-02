---
description: Advanced Encryption System
icon: file-lock
---

# Diffie-Hellman

Diffie-Hellman (DH) este un algoritm matematic asimetric care permite două computere să genereze un secret partajat identic fără să fi comunicat înainte. Noua cheie partajată nu este niciodată schimbată între emițător și destinatar. Cu toate acestea, deoarece ambele părți îl cunosc, cheia poate fi utilizată de un algoritm de criptare pentru a cripta traficul dintre cele două sisteme.

Iată două exemple de cazuri când DH este utilizat în mod obișnuit:

* Schimbul de date se face folosind un VPN IPsec&#x20;
* Se fac schimb de date SSH

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Culorile din figură vor fi folosite în locul numerelor lungi complexe pentru a simplifica procesul de acord cu cheia DH. Schimbul de chei DH începe cu Alice și Bob căzând de acord asupra unei culori comune arbitrare care nu trebuie să fie ținută secretă. Culoarea convenită în exemplul nostru este galben.

Apoi, Alice și Bob vor selecta fiecare o culoare secretă. Alice a ales roșu, în timp ce Bob a ales albastru. Aceste culori secrete nu vor fi niciodată împărtășite cu nimeni. Culoarea secretă reprezintă cheia privată secretă aleasă de fiecare parte.

Alice și Bob amestecă acum culoarea comună comună (galben) cu culoarea lor secretă respectivă pentru a produce o culoare publică. Prin urmare, Alice va amesteca galbenul cu culoarea roșie pentru a produce o culoare publică de portocaliu. Bob va amesteca galbenul și albastrul pentru a produce o culoare publică de verde.

Alice îi trimite lui Bob culoarea publică (portocalie), iar Bob îi trimite lui Alice culoarea publică (verde).

Alice și Bob amestecă fiecare culoarea primită cu propria lor culoare secretă originală (roșu pentru Alice și albastru pentru Bob.). Rezultatul este un amestec final de culoare maro care este identic cu amestecul final de culoare al partenerului. Culoarea maro reprezintă cheia secretă partajată între Bob și Alice.

Securitatea DH se bazează pe faptul că folosește numere foarte mari în calculele sale. De exemplu, un număr DH de 1024 de biți este aproximativ egal cu un număr zecimal de 309 cifre. Având în vedere că un miliard este de 10 cifre zecimale (1.000.000.000), ne putem imagina cu ușurință complexitatea lucrului cu nu unul, ci mai multe numere zecimale de 309 cifre.

Diffie-Hellman folosește diferite grupuri DH pentru a determina puterea cheii care este utilizată în procesul de acordare a cheii. Numerele de grup mai mari sunt mai sigure, dar necesită timp suplimentar pentru a calcula cheia. Următoarele identifică grupurile DH acceptate de software-ul Cisco IOS și valoarea numărului prim asociată acestora:

* Grupa DH 1: 768 de biți&#x20;
* Grupa DH 2: 1024 biți&#x20;
* Grupa DH 5: 1536 biți&#x20;
* Grupa DH 14: 2048 biți&#x20;
* Grupa DH 15: 3072 biți&#x20;
* Grupa DH 16: 4096 biți

Notă: Un acord de cheie DH se poate baza, de asemenea, pe criptografia cu curbă eliptică. Grupurile DH 19, 20 și 24, care se bazează pe criptografia cu curbe eliptice, sunt, de asemenea, acceptate de software-ul Cisco IOS.

Din păcate, sistemele de chei asimetrice sunt extrem de lente pentru orice tip de criptare în bloc. Acesta este motivul pentru care este obișnuit să criptezi cea mai mare parte a traficului folosind un algoritm simetric, cum ar fi 3DES sau AES și să folosești algoritmul DH pentru a crea chei care vor fi utilizate de algoritmul de criptare.
