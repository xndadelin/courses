# 🏛️ Criptografie clasica

{% hint style="info" %}
Spre deosebire de criptografia modernă care lucrează cu date binare, metodele clasice de criptografie au fost dezvoltate folosind doar cifre și litere.
{% endhint %}

## Tipuri de cifruri

### Cifre monoalfabetice

Cifrele monoalfabetice utilizează o substituție fixă pe întregul mesaj.

### Cifre polialfabetice

Cifrele polialfabetice folosesc o serie de substituții diferite pe întregul mesaj.

***

### Algoritmi criptografici clasici

#### Cifrul Caesar

Aceasta este una dintre cele mai simple metode de criptare, cunoscut și ca cifru prin substituție sau mutare/transpoziție (cunoscut în engleză ca _shifted cipher_), deoarece pentru a-l utiliza pe un mesaj, o literă este înlocuită/mutată cu alta bazată pe un număr fix de la 0 la 25 (numărul total de litere în alfabetul englez).

**Exemplu:** Mihai și Maria sunt pasionați de jocuri și vor să-și ascundă parola serverului privat de gaming. Decid să folosească cifrul Caesar cu o cheie de 5. Astfel, parola lor „LEVELUP” devine „QJAJQZU”.

#### Cifrul de substituție simplă

Este un alt cifru monoalfabetic. Principala diferență între cifrul Caesar și acesta este că algoritmul „Simple substitution Cipher” acceptă mai mult decât o singură unitate de mutare.

Se poate extrapola la litere duble, triplete de litere și așa mai departe.

#### Cifrul Playfair

Este un algoritm ce folosește o matrice de 5x5 pentru a înlocui fiecare literă din alfabet.

#### Cifrul Vigenère

Este o variantă îmbunătățită a algoritmului Caesar, ce are câteva abordări, printre care Vernam cipher sau One-time pad cipher.

***

### Algoritmi de transpunere

Aceste algoritmi reordonează literele fără a le înlocui:

* **Rail Fence Cipher**
* **Scytale Cipher**
* **Route Cipher**
* **Columnar Transposition**
* **Double Transposition**
* **Disrupted Transposition**
* **Beaufort Cipher**: Este o tehnică ce se bazează pe Tabula Recta, inventată în 1508 de Johannes Trithemius.

{% file src="../.gitbook/assets/_lk-6.pdf" %}



## Criptarea XOR

### Ce este XOR?

XOR (Exclusive OR) este o operație logică folosită în criptografie pentru a cripta și decripta datele. Este o metodă eficientă și simplă care funcționează pe baza unui principiu de bază:

* Dacă bitul de intrare este 0 și bitul cheii este 0, rezultatul este 0.
* Dacă bitul de intrare este 0 și bitul cheii este 1, rezultatul este 1.
* Dacă bitul de intrare este 1 și bitul cheii este 0, rezultatul este 1.
* Dacă bitul de intrare este 1 și bitul cheii este 1, rezultatul este 0.

### Cum funcționează?

1. **Textul original (plaintext)**: Mesajul care trebuie criptat.
2. **Cheia**: O secvență de biți care trebuie să fie la fel de lungă ca textul original pentru a obține criptarea optimă.
3. **Funcția XOR**: Textul original este combinat cu cheia prin aplicarea operației XOR pe fiecare bit.

## Proprietăți ale XOR

1. **Comutativitate**:
   * A + B = B + A\
     (Ordinea operandilor nu afectează rezultatul.)
2. **Asociativitate**:
   * (A + B) + C = A + (B + C)\
     (Gruparea operandilor nu afectează rezultatul.)
3. **Identitate**:
   * A + 0 = A\
     (Orice bit XOR cu 0 rămâne neschimbat.)
4. **Complement**:
   * A + A = 0\
     (Orice bit XOR cu el însuși devine 0.)
5. **Inversibilitate**:
   * A + B + B = A\
     (Aplicarea XOR cu aceeași cheie de două ori restabilește valoarea inițială.)
6. **Diverse valori**:
   * XOR poate produce doar două rezultate: 0 sau 1, ceea ce îl face util în criptografie și logică digitală.
7. **Distribuție**:
   * XOR nu este distributiv față de AND sau OR, dar este utilizat împreună cu aceste operații în multe aplicații.

***



***
