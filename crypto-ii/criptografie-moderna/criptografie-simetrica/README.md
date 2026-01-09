---
icon: key-skeleton
---

# Criptografie simetrica

Algoritmii simetrici folosesc aceeași cheie pre-partajată pentru a cripta și decripta datele. O cheie pre-partajată, numită și cheie secretă, este cunoscută de expeditor și destinatar înainte ca orice comunicare criptată să poată avea loc.

Pentru a ilustra modul în care funcționează criptarea simetrică, luați în considerare un exemplu în care Alice și Bob locuiesc în locații diferite și doresc să facă schimb de mesaje secrete între ei prin intermediul sistemului de e-mail. În acest exemplu, Alice vrea să-i trimită un mesaj secret lui Bob.

În figură, Alice și Bob au chei identice pentru un singur lacăt. Aceste chei au fost schimbate înainte de trimiterea oricăror mesaje secrete. Alice scrie un mesaj secret și îl pune într-o cutie mică pe care o încuie folosind lacătul cu cheia ei. Ea îi trimite cutia prin poștă lui Bob. Mesajul este blocat în siguranță în interiorul cutiei, pe măsură ce cutia își face drum prin sistemul oficiului poștal. Când Bob primește cutia, își folosește cheia pentru a debloca lacătul și a prelua mesajul. Bob poate folosi aceeași cutie și lacăt pentru a trimite un răspuns secret înapoi lui Alice.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Astăzi, algoritmii de criptare simetrică sunt utilizați în mod obișnuit cu traficul VPN. Acest lucru se datorează faptului că algoritmii simetrici folosesc mai puține resurse CPU decât algoritmii de criptare asimetrică. Acest lucru permite criptarea și decriptarea datelor să fie rapide atunci când utilizați un VPN. Când utilizați algoritmi de criptare simetrică, ca orice alt tip de criptare, cu cât cheia este mai lungă, cu atât va dura mai mult ca cineva să descopere cheia. Majoritatea cheilor de criptare sunt între 112 și 256 de biți. Pentru a vă asigura că criptarea este sigură, trebuie utilizată o lungime minimă a cheii de 128 de biți. Utilizați o cheie mai lungă pentru comunicații mai sigure.

Algoritmii de criptare simetrică sunt uneori clasificați fie ca un cifru bloc (block cipher), fie ca un cifru flux (stream cipher).

<details>

<summary>Block cipher</summary>

Cifrurile bloc transformă un bloc de text simplu cu lungime fixă ​​într-un bloc comun de text cifrat de 64 sau 128 de biți. Cifrurile bloc comune includ DES cu o dimensiune de bloc de 64 de biți și AES cu o dimensiune de bloc de 128 de biți.

</details>

<details>

<summary>Stream cipher</summary>

Cifrurile în flux criptează textul simplu câte un octet sau un bit. Cifrurile de flux sunt practic un cifr de bloc cu o dimensiune de bloc de un octet sau bit. Cifrurile în flux sunt de obicei mai rapide decât cifrurile bloc, deoarece datele sunt criptate continuu. Exemple de coduri de flux includ RC4 și A5, care este folosit pentru a cripta comunicațiile GSM ale telefonului mobil.

</details>

| Algoritmi de criptografie simetrică                     | Descriere                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standardul de criptare a datelor (DES)                  | Acesta este un algoritm de criptografie simetrică vechi. Folosește o lungime scurtă a cheii, ceea ce îl face nesigur pentru majoritatea utilizărilor actuale.                                                                                                                                         |
| 3DES (Triple DES)                                       | Acesta este înlocuitorul pentru DES și repetă procesul algoritmului DES de trei ori. Ar trebui evitat dacă este posibil, deoarece este programat pentru a fi retras în 2023. Dacă este implementat, folosiți durate foarte scurte ale cheii.                                                          |
| Standardul avansat de criptare (AES)                    | AES este un algoritm de criptografie simetrică popular și recomandat. Oferă combinații de chei de 128, 192 sau 256 biți pentru a cripta blocuri de date de 128, 192 sau 256 biți.                                                                                                                     |
| Algoritmul de criptare optimizat pentru software (SEAL) | SEAL este o alternativă mai rapidă la algoritmul AES. SEAL este un cifru de flux care folosește o cheie de criptare de 160 biți și are un impact mai mic asupra CPU-ului comparativ cu alte algoritmi bazate pe software.                                                                             |
| Algoritmii din seria Rivest ciphers (RC)                | Acest algoritm a fost dezvoltat de Ron Rivest. Au fost dezvoltate mai multe variații, dar RC4 a fost cea mai utilizată. RC4 este un cifru de flux care a fost folosit pentru a securiza traficul web. S-au descoperit mai multe vulnerabilități, ceea ce l-a făcut nesigur. RC4 nu ar trebui folosit. |

## Diferențe între AES și DES

| Caracteristică             | DES (Data Encryption Standard)                                                  | AES (Advanced Encryption Standard)                                                   |
| -------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Lungimea cheii**         | 56 biți                                                                         | 128, 192 sau 256 biți                                                                |
| **Lungimea blocului**      | 64 biți                                                                         | 128 biți                                                                             |
| **Structura algoritmului** | Algoritm pe bază de runde (16 runde)                                            | Algoritm pe bază de runde (10, 12 sau 14 runde)                                      |
| **Funcția de criptare**    | Utilizează permutări și funcția F cu S-box-uri                                  | Utilizează substituția byte-urilor, mutarea rândurilor și amestecarea coloanelor     |
| **Securitate**             | Considerat nesigur pentru utilizările actuale din cauza lungimii scurte a cheii | Considerat sigur și utilizat pe scară largă, acceptat ca standard de criptare modern |
| **Performanță**            | Performanță mai lentă din cauza structurii sale simple                          | Performanță mai bună, optimizat pentru hardware modern                               |
| **Standardizate**          | Standardizat de către NIST în 1977, retras în 2005                              | Standardizat de către NIST în 2001                                                   |

* **Securitate**: AES este considerat mai sigur decât DES datorită lungimii cheii mai mari și a structurii sale mai complexe.
* **Performanță**: AES are o performanță mai bună și este mai eficient pe hardware modern comparativ cu DES.
* **Standardizare**: DES a fost retras din utilizare datorită vulnerabilităților sale, în timp ce AES rămâne standardul de facto pentru criptarea simetrică.

În competitii de tip CTF, cum este și Unbreakable, OSC, ROCSC, DefCamp sunt prezentate aplicații ce au algoritmi criptografici moderni ce sunt implementate greșit, au vulnerabilitati cunoscute ce permit recuperarea mesajului original într-un termen rezonabil sau sunt reimplementari ale unor algoritmi consacrați, dar care au probleme de securitate.
