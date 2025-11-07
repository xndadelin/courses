---
icon: key-skeleton
---

# Criptografie asimetrica

Algoritmii asimetrici, numiți și algoritmi cu cheie publică, sunt proiectați astfel încât cheia utilizată pentru criptare să fie diferită de cheia utilizată pentru decriptare, așa cum se arată în figură. Cheia de decriptare nu poate fi calculată, într-o perioadă rezonabilă de timp, din cheia de criptare și invers.

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Algoritmii asimetrici folosesc o cheie publică și o cheie privată. Ambele chei sunt capabile de procesul de criptare, dar cheia pereche complementară este necesară pentru decriptare. Procesul este, de asemenea, reversibil. Datele care sunt criptate cu cheia publică necesită cheia privată pentru decriptare. Algoritmii asimetrici obțin confidențialitate și autenticitate prin utilizarea acestui proces.

Deoarece niciuna dintre părți nu are un secret comun, trebuie utilizate chei de lungimi foarte mari. Criptarea asimetrică poate folosi lungimi de cheie între 512 și 4.096 de biți. Lungimile cheilor mai mari sau egale cu 2.048 de biți pot fi de încredere, în timp ce lungimile cheilor de 1.024 sau mai scurte sunt considerate insuficiente.

Exemple de protocoale care utilizează algoritmi de cheie asimetrică includ:

* Internet Key Exchange (IKE) - Aceasta este o componentă fundamentală a VPN-urilor IPsec.
* Secure Socket Layer (SSL) - Acesta este acum implementat ca standard IETF Transport Layer Security (TLS).&#x20;
* Secure Shell (SSH) - Acest protocol oferă o conexiune sigură de acces la distanță la dispozitivele din rețea. Pretty Good Privacy&#x20;
* (PGP) - Acest program de calculator oferă confidențialitate criptografică și autentificare. Este adesea folosit pentru a crește securitatea comunicațiilor prin e-mail.

Algoritmii asimetrici sunt substanțial mai lenți decât algoritmii simetrici. Proiectarea lor se bazează pe probleme de calcul, cum ar fi factorizarea numerelor extrem de mari sau calcularea logaritmilor discreti de numere extrem de mari.

Deoarece sunt lenți, algoritmii asimetrici sunt utilizați de obicei în mecanismele criptografice cu volum redus, cum ar fi semnăturile digitale și schimbul de chei. Cu toate acestea, managementul cheilor algoritmilor asimetrici tinde să fie mai simplu decât algoritmii simetrici, deoarece de obicei una dintre cele două chei de criptare sau decriptare poate fi făcută publică.

| Algoritm de Criptare Asimetrică                                                  | Lungime Cheie               | Descriere                                                                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Diffie-Hellman (DH)                                                              | 512, 1024, 2048, 3072, 4096 | Algoritmul Diffie-Hellman permite două părți să convină asupra unei chei pe care o pot folosi pentru a cripta mesajele pe care doresc să și le trimită reciproc. Securitatea acestui algoritm se bazează pe presupunerea că este ușor să ridici un număr la o anumită putere, dar dificil să calculezi ce putere a fost folosită având numărul și rezultatul.                     |
| Standardul de Semnătură Digitală (DSS) și Algoritmul de Semnătură Digitală (DSA) | 512 - 1024                  | DSS specifică DSA ca algoritm pentru semnături digitale. DSA este un algoritm de cheie publică bazat pe schema de semnătură ElGamal. Viteza de creare a semnăturii este similară cu RSA, dar este de 10 până la 40 de ori mai lentă pentru verificare.                                                                                                                            |
| Algoritmii de criptare Rivest, Shamir și Adleman (RSA)                           | 512 până la 2048            | RSA este pentru criptografie cu cheie publică bazată pe dificultatea actuală de factorizare a numerelor foarte mari. Este primul algoritm cunoscut ca fiind potrivit atât pentru semnare, cât și pentru criptare. Este folosit pe scară largă în protocoalele de comerț electronic și este considerat sigur dacă se folosesc chei suficient de lungi și implementări actualizate. |
| ElGamal                                                                          | 512 - 1024                  | Un algoritm de criptare cu cheie asimetrică pentru criptografie cu cheie publică bazat pe acordul de cheie Diffie-Hellman. Un dezavantaj al sistemului ElGamal este că mesajul criptat devine foarte mare, aproximativ de două ori dimensiunea mesajului original și din acest motiv este folosit doar pentru mesaje mici, cum ar fi cheile secrete.                              |
| Tehnici de curbă eliptică                                                        | 224 sau mai mare            | Criptografia pe bază de curbă eliptică poate fi folosită pentru a adapta multe algoritmi criptografici, cum ar fi Diffie-Hellman sau ElGamal. Principalul avantaj al criptografiei pe bază de curbă eliptică este că cheile pot fi mult mai mici.                                                                                                                                 |
