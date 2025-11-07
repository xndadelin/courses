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

Cifrul **Vigenère** este o metodă de **criptare polialfabetică**, ceea ce înseamnă că fiecare literă din textul clar este cifrată cu un alt alfabet, determinat de o **cheie formată din litere**. Fiecare literă a cheii definește un **decalaj diferit** aplicat asupra textului clar.

Spre deosebire de cifrul Caesar (care folosește o singură deplasare pentru întreg textul), cifrul Vigenère aplică **deplasări diferite** pentru fiecare poziție, în funcție de literele cheii.

1. Se scrie textul clar sub cheie, repetând cheia până acoperă tot textul.
2. Fiecărei litere i se aplică o deplasare corespunzătoare literei din cheie (A = 0, B = 1, C = 2 etc.).
3. Rezultatul este textul cifrat.

#### 5.3. Exemplu practic — Cifrul Vigenère

**Text clar:**\
DEFENDTHEEASTWALL

**Cheie:**\
FORTIFICATION

***

**1. Scriem cheia repetată sub textul clar**

Text :   DEFENDTHEEASTWALL\
Cheie: FORTIFICATIONFORT

***

**2. Cifrare pas cu pas**

| Literă cheie | Deplasare | Literă clară | Literă cifrată |
| ------------ | --------- | ------------ | -------------- |
| F            | +5        | D            | I              |
| O            | +14       | E            | S              |
| R            | +17       | F            | W              |
| T            | +19       | E            | X              |
| I            | +8        | N            | Q              |
| F            | +5        | D            | H              |
| I            | +8        | T            | B              |
| C            | +2        | H            | J              |
| A            | +0        | E            | E              |
| T            | +19       | E            | X              |
| I            | +8        | A            | I              |
| O            | +14       | S            | G              |
| N            | +13       | T            | G              |
| F            | +5        | W            | B              |
| O            | +14       | A            | O              |
| R            | +17       | L            | C              |
| T            | +19       | L            | E              |

***

**3. Textul cifrat final**

ISWXQHJBJEXIGGBOCE

***

**Observații**

* Fiecare literă a cheii definește o deplasare diferită în alfabet (A=0, B=1, …, Z=25).
* Când cheia se termină, se repetă automat.
* Cifrul este mai sigur decât Caesar, dar dacă cheia e scurtă și se repetă, poate fi spart prin analiză a frecvențelor.

```python
def vigenere_encrypt(plaintext, key):
    ciphertext = ""
    key = key.upper()
    key_index = 0

    for caracter in plaintext:
        if caracter.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            if caracter.isupper():
                ciphertext += chr((ord(caracter) - ord('A') + shift) % 26 + ord('A'))
            else:
                ciphertext += chr((ord(caracter) - ord('a') + shift) % 26 + ord('a'))
            key_index += 1
        else:
            ciphertext += caracter
    
    return ciphertext
```

***

#### 5.3. Alți algoritmi clasici

| Tip                     | Descriere                                         | Exemple                       |
| ----------------------- | ------------------------------------------------- | ----------------------------- |
| **Simple substitution** | Înlocuiește fiecare literă cu alta fixă.          | A → M, B → Q                  |
| **Playfair cipher**     | Folosește o matrice 5×5 pentru perechi de litere. | Bazat pe digrame              |
| **Transpoziție**        | Reordonează caracterele.                          | Rail Fence, Scytale, Columnar |
| **Beaufort cipher**     | Bazat pe _Tabula Recta_ (Trithemius, 1508).       | Variante de Vigenère          |

***

### 6. Vulnerabilități și atacuri clasice

{% hint style="danger" %}
Cifrurile clasice nu mai oferă siguranță în contextul modern.
{% endhint %}

**Vulnerabilități:**

* Repetiția cheii în Vigenère → analiză de frecvență.
* Determinism → aceleași litere produc aceleași rezultate.

**Atacuri comune:**

* Kasiski Examination
* Friedman Test
* Frequency analysis

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

{% hint style="info" %}
Hashingul este utilizat în securitate pentru verificare, autentificare și protejarea datelor.
{% endhint %}

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

{% hint style="success" %}
Poți experimenta encodare și decodare cu instrumentul online [CyberChef](https://gchq.github.io/CyberChef/).
{% endhint %}

### 9. Introducere în Python pentru criptografie

{% hint style="success" %}
Python este un limbaj de programare interpretat, de nivel înalt, utilizat frecvent în domenii precum analiza datelor și securitatea informatică.
{% endhint %}

***

#### 9.1 Ce este Python?

Python este un limbaj open-source, portabil și multi-paradigmă. Oferă suport pentru programare procedurală, orientată pe obiecte și funcțională.&#x20;

{% hint style="info" %}
Python poate fi descărcat gratuit de la [python.org](https://www.python.org/downloads/). Pe Linux este, de obicei, instalat implicit.
{% endhint %}

***

#### 9.2 Configurarea mediului

1. Instalează Python 3.10+
2. Creează un mediu virtual pentru izolarea dependențelor:

```bash
python3 -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows
.venv\Scripts\activate
```

3. Instalează pachetele de bază:

```bash
pip install cryptography hashlib base64
```

{% hint style="info" %}
Mediile virtuale previn conflictele între pachete și facilitează portabilitatea proiectelor.
{% endhint %}

***

#### 9.3 Structura de bază a unui program Python

Un fișier Python (`.py`) conține instrucțiuni, funcții și clase.

```python
def salut():
    print("Salut, lume!")

salut()
```

Rezultat:

```
Salut, lume!
```

***

#### 9.4 Variabile și tipuri de date

Python utilizează tipuri dinamice — tipul variabilei este determinat automat la execuție.

```python
nume = "Alice"        # string
varsta = 20           # int
temperatura = 21.5    # float
este_student = True   # bool
```

Verificarea tipului:

```python
print(type(nume))  # <class 'str'>
```

***

#### 9.5 Structuri de control

**Instrucțiuni condiționale**

```python
x = 10
if x > 0:
    print("Număr pozitiv")
elif x == 0:
    print("Zero")
else:
    print("Număr negativ")
```

**Bucle**

```python
for i in range(5):
    print(i)

while x > 0:
    x -= 1
```

***

#### 9.6 Funcții

Funcțiile definesc blocuri de cod reutilizabile.

```python
def suma(a, b):
    return a + b

print(suma(3, 4))  # 7
```

***

#### 9.7 Șiruri de caractere (strings)

```python
text = "criptografie"
print(text.lower())   # criptografie
print(text.upper())   # CRIPTOGRAFIE
print(text[::-1])     # eifargoTPirc
```

Conversie între string și bytes:

```python
b = text.encode("utf-8")
text_back = b.decode("utf-8")
```

***

#### 9.8 Liste, tuple și dicționare

**Liste (`list`)**

Listele sunt structuri ordonate și modificabile.

```python
fructe = ["mere", "pere", "banane"]
fructe.append("cirese")
print(fructe[0])       # mere
print(len(fructe))     # 4
```

**Tuple (`tuple`)**

Tuplele sunt similare listelor, dar **imutabile** (nu pot fi modificate după creare).

```python
coordonate = (10.5, 20.3)
x, y = coordonate
print(f"x = {x}, y = {y}")
```

**Dicționare (`dict`)**

Dicționarele conțin perechi cheie–valoare.\
Sunt foarte utile în criptografie pentru mapări între litere, substituții sau tabele.

```python
alfabet = {"A": "D", "B": "E", "C": "F"}
print(alfabet["B"])  # E

# Parcurgere
for litera, cod in alfabet.items():
    print(litera, "->", cod)
```

***

#### 9.9 Module utile pentru criptografie

| Modul          | Scop                                 | Exemplu                               |
| -------------- | ------------------------------------ | ------------------------------------- |
| `hashlib`      | Funcții hash (MD5, SHA-1, SHA-256)   | `hashlib.sha256(b"data").hexdigest()` |
| `base64`       | Encodare și decodare                 | `base64.b64encode(b"text")`           |
| `cryptography` | Criptare simetrică și asimetrică     | `AESGCM`, `Fernet`                    |
| `secrets`      | Generare de chei și valori aleatoare | `secrets.token_hex(16)`               |

***

#### 9.10 Exemplu practic:&#x20;

```python
import hashlib, base64

text = "cryptoo"
hash_value = hashlib.sha256(text.encode()).hexdigest()
encoded = base64.b64encode(text.encode()).decode()

print("Text original:", text)
print("SHA-256:", hash_value)
print("Base64:", encoded)
```

***

