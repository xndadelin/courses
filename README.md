---
icon: key-skeleton
---

# Criptografie și algoritmi de criptare, encodare sau hashing

* **Introducere în criptografie**
  * Definiția criptografiei și importanța ei în securitatea informației
  * Concepte de bază: text clar, text cifrat, cheie, cifrare, decifrare
  * Principiile fundamentale ale criptografiei: confidențialitate, integritate, autentificare
* **Criptografie clasică**
  * Cifrul Caesar: explicație, exemplu practic, dezavantaje
  * Cifrul de substituție monoalfabetică și polialfabetică: concept, exemplu, vulnerabilități
  * Cifrul Vigenère: explicație, demonstrație practică
* **Noțiuni de bază despre hashing**
  * Ce este o funcție hash și care sunt proprietățile ei
  * Exemple de funcții hash comune (MD5, SHA-1, SHA-256)
  * Utilizări ale funcțiilor hash în securitate (stocarea parolelor, verificarea integrității)
* **Introducere în encodare**
  * Diferența dintre cifrare și encodare
  * Base64 encoding: concept și utilizări practice
  * Demonstrație practică de encodare și decodare
* **Introducere în Python pentru criptografie**
  * Configurarea mediului Python
  * Variabile și tipuri de date în Python, instrucțiuni
  * Implementarea unui cifru Caesar simplu în Python
  * Alte noțiuni ale limbajului Python

***

### 1. Criptografia

{% hint style="info" %}
Criptografia este știința transformării informației într-o formă inaccesibilă persoanelor neautorizate.
{% endhint %}

Scopurile principale:

* Protejarea datelor împotriva accesului neautorizat.
* Asigurarea integrității și autenticității informațiilor.
* Prevenirea manipulării și falsificării datelor.

***

### 2. Principiile fundamentale ale criptografiei

| Principiu             | Descriere                                               | Exemple                  |
| --------------------- | ------------------------------------------------------- | ------------------------ |
| **Confidențialitate** | Informația este accesibilă doar celor autorizați.       | Criptare simetrică (AES) |
| **Integritate**       | Datele nu sunt modificate neautorizat.                  | Funcții hash (SHA-256)   |
| **Autentificare**     | Verifică identitatea expeditorului și a destinatarului. | Certificate digitale     |
| **Non-repudiere**     | Previne negarea unei acțiuni realizate.                 | Semnături digitale       |

***

### 3. Terminologie de bază

* **Plaintext:** textul original, necriptat.
* **Ciphertext:** textul rezultat după criptare, neinteligibil fără cheie.
* **Cheie:** secretul utilizat în criptare și decriptare.
* **Cifrare:** procesul de transformare a textului clar în text cifrat.
* **Decriptare:** procesul invers, de recuperare a textului clar.

***

### 4. Metode criptografice

{% hint style="info" %}
Criptografia se clasifică în funcție de utilizarea cheilor și a algoritmilor.
{% endhint %}

* **Criptografie simetrică** – folosește aceeași cheie pentru criptare și decriptare.
* **Criptografie asimetrică** – folosește o pereche de chei (publică și privată).
* **Hashing** – transformă datele într-o amprentă unică, nereversibilă.

***

### 5. Criptografia clasică

#### Tipuri de cifruri

* **Monoalfabetice:** o substituție fixă pe întregul text.
* **Polialfabetice:** substituții multiple, bazate pe o cheie.
* **Transpoziție:** reordonează caracterele fără a le schimba.

***

#### 5.1. Cifrul Caesar

Cifrul Caesar este unul dintre cele mai simple și cunoscute algoritmi de criptare.\
Fiecare literă din textul clar este deplasată cu un număr fix de `k`  poziții în alfabet.

$$
C = (P + k) \mod 26 \\
P = (C - k) \mod 26
$$

| Literă | Cod | Calcul `(P + 3) mod 26` | Literă cifrată |
| ------ | --- | ----------------------- | -------------- |
| H      | 7   | 10                      | K              |
| E      | 4   | 7                       | H              |
| L      | 11  | 14                      | O              |
| L      | 11  | 14                      | O              |
| O      | 14  | 17                      | R              |

{% hint style="warning" %}
**Dezavantaj:** are doar 25 de chei posibile și poate fi spart prin "forță brută".
{% endhint %}

***

#### 5.2. Cifrul Vigenère

Cifrul Vigenère este o formă de criptare polialfabetică.\
Folosește o cheie alcătuită din litere, fiecare definind un decalaj diferit.

**Exemplu:**

CIPHER + KEY → MQLRI...

Avantaj: mai rezistent decât Caesar.\
Vulnerabilități: repetarea cheii permite analiza frecvenței.

***

#### 5.3. Alți algoritmi clasici

| Tip                     | Descriere                                         | Exemple                       |
| ----------------------- | ------------------------------------------------- | ----------------------------- |
| **Simple Substitution** | Înlocuiește fiecare literă cu alta fixă.          | A → M, B → Q                  |
| **Playfair Cipher**     | Folosește o matrice 5×5 pentru perechi de litere. | Bazat pe digrame              |
| **Transpoziție**        | Reordonează caracterele.                          | Rail Fence, Scytale, Columnar |
| **Beaufort Cipher**     | Bazat pe _Tabula Recta_ (Trithemius, 1508).       | Variante de Vigenère          |

***

### 6. Vulnerabilități și atacuri clasice

> \[!IMPORTANT] Cifrurile clasice nu mai oferă siguranță în contextul modern.

**Vulnerabilități:**

* Repetiția cheii în Vigenère → analiză de frecvență.
* Determinism → aceleași litere produc aceleași rezultate.

**Atacuri comune:**

* Kasiski Examination
* Friedman Test
* Frequency Analysis

***

### 7. Hashing

Funcțiile hash (sau de dispersie) transformă datele într-o valoare unică și fixă (_digest_).\
Sunt **unidirecționale** și **deterministe**.

**Exemple de funcții hash:**

* MD2, MD4, MD5
* SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* SHA-3, RIPEMD, WHIRLPOOL, CRC32

***

#### Proprietăți ale funcțiilor hash

| Proprietate                   | Descriere                                             |
| ----------------------------- | ----------------------------------------------------- |
| **Determinism**               | Aceeași intrare produce același rezultat.             |
| **Lungime fixă**              | Indiferent de dimensiunea datelor de intrare.         |
| **Difuzie (Avalanșă)**        | O mică modificare schimbă complet rezultatul.         |
| **Rezistență la coliziuni**   | Două mesaje diferite nu trebuie să aibă același hash. |
| **Rezistență la pre-imagine** | Nu se poate deduce inputul din hash.                  |

***

#### Aplicații practice

> \[!TIP] Hashingul este utilizat în securitate pentru verificare, autentificare și protejarea datelor.

* **Stocarea parolelor:** parolele sunt hash-uite și, eventual, “salted”.
* **Verificarea integrității:** hash-ul fișierului confirmă că datele nu au fost alterate.
* **Semnături digitale:** identifică autenticitatea și integritatea mesajelor.

***

#### Vulnerabilități și atacuri

* **Coliziuni:** două intrări diferite pot genera același hash.
* **Atacuri de pre-imagine:** găsirea unui input care produce un hash dat.
* **Atacuri “birthday”:** exploatează probabilitatea coliziunilor.

***

### 8. Encodare

Encodarea transformă datele într-un format standard pentru transmitere și stocare.\
Scopul ei este **compatibilitatea**, nu securitatea.

| Encodare            | Descriere                                     | Utilizare                   |
| ------------------- | --------------------------------------------- | --------------------------- |
| **Base64**          | Transformă date binare în text ASCII.         | Transfer date, e-mail, JSON |
| **URL Encoding**    | Înlocuiește caracterele speciale din URL-uri. | HTTP requests               |
| **Hex Encoding**    | Reprezentare hexazecimală a datelor binare.   | Debugging, low-level        |
| **UTF-8 / ASCII**   | Codificare text standard.                     | Documente text              |
| **Base32 / Base16** | Variante simplificate de Base64.              | Sisteme compacte            |

> \[!TIP] Poți experimenta encodare și decodare cu instrumentul online [CyberChef](https://gchq.github.io/CyberChef/).

***

### 9. Introducere în Python pentru criptografie

> \[!NOTE] Python oferă un ecosistem bogat pentru lucrul cu algoritmi criptografici și funcții hash.

* Configurarea mediului Python.
* Variabile și tipuri de date.
* Instrucțiuni de bază.
* Implementarea unui **cifru Caesar** simplu.
* Explorarea librăriilor `hashlib`, `base64`, `cryptography`.

**Exemplu simplu – cifru Caesar:**

```python
def caesar(text, shift):
    result = ""
    for ch in text:
        if ch.isalpha():
            offset = 65 if ch.isupper() else 97
            result += chr((ord(ch) - offset + shift) % 26 + offset)
        else:
            result += ch
    return result

print(caesar("HELLO", 3))  # KHOOR
```
