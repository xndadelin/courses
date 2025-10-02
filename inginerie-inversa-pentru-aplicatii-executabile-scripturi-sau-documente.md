---
hidden: true
icon: '0'
---

# Inginerie inversă pentru aplicații executabile, scripturi sau documente

❓ Intrebarile zilei&#x20;

* 🔰 Ce este ingineria inversa si care este scopul?&#x20;
* 🧰 Cum si cu ce instrumente putem pune in aplicare ingineria inversa

***

{% hint style="info" %}
Ingineria și dezvoltarea tehnologiilor în general este o industrie foarte versatilă, care devine mereu creativă. Folosind creativitatea și inovația, inginerii creează produse nemaivăzute, de care beneficiază comunitățile lor.
{% endhint %}

### **Inginerie inversa**

* Ingineria inversa implica dezasamblarea unui produs pentru a intelege cum functioneaza, facand posibila intelegerea modului de lucru si a structurii sistemelor studiate. In contextul dezvoltarii software, ingineria inversa presupunu luarea unui sistem software si analizarea acestuia pentru a reproduce informatiile originale de proiectare si implementare.

#### **Concepte de inginerie inversa**

* Tehnicile de inginerie inversa sunt in general folosite pentru a:
  * I**nțelege** **comportamentul** **unor** **aplicații** **malițioase** (**malware**) ce au încercat sa anonimeze serviciile cu care comunica, sau capabilitatile pe care le are o astfel de unealtă
  * **Recupera** **codul** **sursă** în situația în care acesta a fost obfuscat / mascat pentru a proteja comportamentul real al acestuia
  * **Identifica** **vulnerabilitati** într-o aplicație ce a fost compilată (de eg. C/C++, C#, Java etc) prin recuperarea partiala sau integrala a codului sursa inițial folosind unelte de compilare, aplicații de debugging.

#### **Procesul de decompilare**

{% hint style="info" %}
Decompilarea este procesul de analiză a unui cod executabil sau de cod binar și de a scoate cod sursă într-un limbaj de programare precum C. Procesul implică traducerea unui fișier de la un nivel scăzut de abstractizare la un nivel mai ridicat de abstractizare, decompilator.
{% endhint %}

Software-ul poate fi inversat și decompilat. O mulțime de alte lucruri (cum ar fi hardware-ul) pot fi proiectate invers, dar nu decompilate, deoarece software-ul / firmware-ul lor este scris în limbaj de nivel scăzut (cod masina), fără o reprezentare de nivel superior sau, mai radical, nu au firmware în primul rând.

**Analiza dinamica a unui program**

{% hint style="info" %}
Analiza dinamica este analiza a software-ului de calculator care se realizează prin executarea de programe pe un procesor real sau virtual. Pe de altă parte, implică executarea programului și necesită instrumentarea blocurilor de bază, cum ar fi buclele, funcțiile etc. Informațiile colectate după analiză sunt de obicei utilizate pentru a optimiza aplicația efectuând derularea buclei cu un factor de derulare adecvat.
{% endhint %}

Cateva instrumente folosite pentru analiza dinamică (sistem de operare Windows):

* **Immunity** **debugger**.
* **Ollydbg**.
* **WinDBG**
* **X64dbg**
* **dnSpy** (.**NET**)
* **Cheat** **Engine**

Cateva instrumente folosite pentru analiza dinamica (sistem de operare Linux):

* **GNU** **Debugger** sau **gdb**.
* **edb**-**debugge**r e un fel de immunity debugger doar ca pe sistemul Linux.

#### **Analiza statica a unui program**

Analiza statică este analiza a software-ului de calculator care se realizează fără a executa de fapt programul, practic este opusul analizei dinamice. Se bazează în principal pe găsirea de modele, numărarea referințelor de memorie iar în majoritatea cazurilor, analiza se efectuează pe o versiune a codului sursă, iar în celelalte cazuri, pe o formă a codului obiect. Cateva instrumente folosite pentru analiza statică (sistem de operare Windows):

* **Ida** **Pro**
* **Ghidra**
* **dnspy** - acest tool este folosit pentru decompilarea aplicațiilor create în tehnologia .NET.
* **jd**-**gui** - este o aplicație pentru decompilat executabile create in limbajul de programare Java.

Cateva instrumente folosite pentru analiza statică (sistem de operare Linux):

* **Ida** **Pro**
* **Ghidra**
* **jd**-**gui**
* **radar2** **sau** **r2**
* **dex2jar**
* **Apktool** (**Android**)

### Introducere în dezasamblarea codului sursa

```cpp
#include <iostream>

int main(){
    char sir_de_caractere[20]="Salut tuturor";
    int variabila_int=200;
    bool variabila_boolean=true;
    char variabila_char='D';
    double variabila_double=3.1415;
    float variabila_flotanta=2.5;
    char vector[]={'a','b','c','d'};
    std::cout << "Inginerie Inversa 101" << '\n';
    return 0;
}
```

```cpp
undefined8 main(void)

{
  basic_ostream *pbVar1;
  
  pbVar1 = std::operator<<((basic_ostream *)std::cout,"Inginerie Inversa 101");
  std::operator<<(pbVar1,'\n');
  return 0;
}
```

{% hint style="info" %}
**Ce este endiannessul?**

Reprezinta ordinea in care octetii unor date sunt transmise pe un mediu de comunicatii. Asta inseamna ca in memoria calculatorului, aceste date sunt citite intr-o ordine anume. Fiecare "celula" de memorie are un index sau o adresa.&#x20;

Fiecare octet poate stoca un numar de 8 biti (i.e. intre 0x00 si 0xff), deci ar trebuie sa rezervi mai mult de un singur octet pentru a stoca un numar mai mare.&#x20;

De departe, **little-endian** este cea mai comuna metoda de ordonare a octetilor dintr-un numar. (btw, asta este folosita pe toate procesoarele Intel, arhitectura x86).

**Little-endian** inseamna stocarea octetilor în ordinea de la cel mai puțin la cel mai semnificativ.&#x20;

Analog, **big-endian** este ordinea opusa. De obicei, se mai regaseste si sub denumirea de **network byte order**, deorece standardele de internet stocau data in big-endian.
{% endhint %}

Registrii x64

| **RAX** | Accumulator for arithmetic operations            | 64-bit |
| ------- | ------------------------------------------------ | ------ |
| **RBX** | Base register (often used for data storage)      | 64-bit |
| **RCX** | Counter register for loops and shifts            | 64-bit |
| **RDX** | Data register, often for multiplication/division | 64-bit |
| **RSP** | Stack Pointer (points to the top of the stack)   | 64-bit |
| **RBP** | Base Pointer (points to the current stack frame) | 64-bit |
| **RSI** | Source index for string operations               | 64-bit |
| **RDI** | Destination index for string operations          | 64-bit |

***

| **Instruction** | **Explanation**                                                |
| --------------- | -------------------------------------------------------------- |
| **PUSH**        | Push a value onto the stack (decreases RSP)                    |
| **MOV**         | Copy data from one register or memory location to another      |
| **SUB**         | Subtract a value from a register                               |
| **ADD**         | Add a value to a register                                      |
| **XOR**         | Perform bitwise XOR between two registers                      |
| **RET**         | Return from a function (pop the return address from the stack) |
| **MOVDQU**      | Move 128-bit data to/from a SIMD XMM register                  |
| **CMP**         | Compare two values and set flags                               |
| **JMP**         | Unconditional jump to a specified memory address               |
| **CALL**        | Call a function (push return address onto the stack)           |

Computerele timpurii aveau memorie limitată, adesea împărțită în secțiuni diferite:

* **Segmentul de cod:** Aici erau stocate instrucțiunile programului.
* **Segmentul de date:** Aici se aflau variabilele globale/statice.
* **Heap-ul:** Folosit pentru alocarea dinamică a memoriei (crește în sus).
* **Stiva:** Pentru apeluri de funcții și variabile locale (crește în jos).

Prin faptul că **heap-ul creștea în sus** și **stiva creștea în jos**, acestea puteau să împartă aceeași zonă de memorie într-un mod eficient, fără a se ciocni, cu excepția cazului în care memoria se epuiza. Aceasta maximiza utilizarea memoriei.

Pe sistemele pe 64 de biți, alinierea memoriei se face de obicei la granițele de 8 octeți. Aceasta înseamnă că anumite tipuri de date, în special cele mai mari (cum ar fi numere întregi de 64 de biți, pointeri și valori duble), trebuie plasate la adresele de memorie care sunt divizibile cu 8. Sistemul va completa memoria pentru a se asigura că această aliniere este respectată.&#x20;

CPU-urile moderne sunt proiectate pentru a accesa memoria în bucăți de 64 de biți (sau 8 octeți) simultan. Acest lucru se datorează faptului că CPU poate citi sau scrie date mai eficient atunci când este aliniat la dimensiunea cuvântului său nativ. De exemplu, pe un sistem pe 64 de biți, procesorul este optimizat pentru a funcționa cu bucăți de date de 64 de biți (sau 8 octeți).

<figure><img src=".gitbook/assets/Pasted image 20250203185531.png" alt=""><figcaption></figcaption></figure>

### Operatii matematice

| `add reg1, reg2` | Adună `reg2` la `reg1` | `reg1 = reg1 + reg2` |
| ---------------- | ---------------------- | -------------------- |

| `sub reg1, reg2` | Scade `reg2` din `reg1` | `reg1 = reg1 - reg2` |
| ---------------- | ----------------------- | -------------------- |

| `imul reg1, reg2` | Înmulțește `reg1` cu `reg2` | `reg1 = reg1 * reg2` |
| ----------------- | --------------------------- | -------------------- |

| `imul reg, reg, imm` | Înmulțire cu valoare constantă | `reg = reg * imm` |
| -------------------- | ------------------------------ | ----------------- |

| `div reg` | Împarte `rdx:rax` la `reg` (fără semn) | `rax = cat, rdx = rest` |
| --------- | -------------------------------------- | ----------------------- |

| `idiv reg` | Împarte `rdx:rax` la `reg` (cu semn) | `rax = cat, rdx = rest` |
| ---------- | ------------------------------------ | ----------------------- |

| `inc reg` | Incrementare (adaugă 1) | `reg = reg + 1` |
| --------- | ----------------------- | --------------- |

| `dec reg` | Decrementare (scade 1) | `reg = reg - 1` |
| --------- | ---------------------- | --------------- |

| `neg reg` | Negativul valorii din registru | `reg = -reg` |
| --------- | ------------------------------ | ------------ |

| `xor reg1, reg2` | XOR bitwise între registre | `reg1 = reg1 ^ reg2` |
| ---------------- | -------------------------- | -------------------- |

| `and reg1, reg2` | AND bitwise între registre | `reg1 = reg1 & reg2` |
| ---------------- | -------------------------- | -------------------- |

| `or reg1, reg2` | OR bitwise între registre | \`reg1 = reg1 |
| --------------- | ------------------------- | ------------- |

| `not reg` | Complementul pe biți al registrului | `reg = ~reg` |
| --------- | ----------------------------------- | ------------ |

| `shl reg, imm` | Deplasare la stânga | `reg = reg << imm` |
| -------------- | ------------------- | ------------------ |

| `shr reg, imm` | Deplasare la dreapta | `reg = reg >> imm` |
| -------------- | -------------------- | ------------------ |

### Introducere în deobfuscarea codului sursa

{% hint style="info" %}
Deobfuscarea este tehnica prin care un ethical hacker decodeaza sau decripteaza informațiile pe care un atacator intenționează sa le folosească. De obicei, un atacator folosește tehnica de obfuscare în scopul de a face cat mai greu citibil codul sursa a unei aplicații pe care o executa în scop malițios sau pentru a trece de anumite protectii cum sunt cele de firewall sau de antivirus.
{% endhint %}

exp:

```javascript
var _0x5377=["\x48\x65\x6C\x6C\x6F\x20\x57\x6F\x72\x6C\x64\x21"];var a=_0x5377[0];function MsgBox(_0x82a8x3){alert(_0x82a8x3);};MsgBox(a);
```

> https://deobfuscate.io/

```js
var a = "Hello World!";
function MsgBox(_0x82a8x3) {
  alert(_0x82a8x3);
}
;
MsgBox(a);
```

**ltrace** și **strace** sunt două utilitare Linux folosite pentru depanarea și analiza comportamentului aplicațiilor:

* **ltrace:** Monitorizează apelurile către bibliotecile dinamice și afișează funcțiile apelate de un proces, împreună cu parametrii acestora. Este util pentru a înțelege cum interacționează un program cu bibliotecile externe.
* **strace:** Monitorizează apelurile de sistem și semnalele gestionate de un proces. Este util pentru a urmări operațiuni precum accesul la fișiere, comunicarea prin rețea și gestionarea proceselor.

Pe scurt: **ltrace** se concentrează pe apeluri de bibliotecă, iar **strace** pe apeluri de sistem.

### Analiza malware

| **Aplicație**        | **Ce face**                                                                           | **Cum o folosești**                                                                                     | **Link**                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **Cuckoo Sandbox**   | Analizează comportamentele malware-ului într-un mediu izolat.                         | Importezi fișierul de malware, îl execuți și obții un raport detaliat despre fișiere, procese și rețea. | [Cuckoo Sandbox](https://cuckoosandbox.org/index.html)                                       |
| **Any.Run**          | Sandbox interactiv pentru analiza malware-ului în timp real.                          | Uploadezi malware-ul și poți interacționa cu acesta pentru a urmări comportamentele detaliate.          | [Any.Run](https://any.run/)                                                                  |
| **Hybrid Analysis**  | Oferă o analiză detaliată a malware-ului, incluzând indicatori de compromitere (IoC). | Uploadezi fișierul pe platformă și primești un raport complet despre comportamentele malware-ului.      | [Hybrid Analysis](https://www.hybrid-analysis.com/)                                          |
| **Wireshark**        | Analizor de pachete de rețea pentru a captura și analiza traficul generat de malware. | Rulezi Wireshark pentru a captura pachetele de rețea și le analizezi pentru conexiuni suspecte.         | [Wireshark](https://www.wireshark.org/)                                                      |
| **Tcpdump**          | Capturarea pachetelor de rețea pe linia de comandă.                                   | Rulezi Tcpdump pentru a captura traficul de rețea și analizezi pentru comunicări suspecte.              | [Tcpdump](https://www.tcpdump.org/)                                                          |
| **Procmon**          | Monitorizează activitățile fișierelor și proceselor în timp real.                     | Rulezi Procmon pentru a observa modificările fișierelor, registrelor și procesele lansate de malware.   | [Procmon](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon)                   |
| **Process Explorer** | Arată procesele active și fișierele/ resursele folosite de acestea.                   | Rulezi Process Explorer pentru a observa procesele și fișierele accesate de malware.                    | [Process Explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer) |
| **IDA Pro**          | Dezvăluie codul din fișierele binare, ajutând la analiza malware-ului.                | Încarci fișierul binar în IDA Pro pentru a-l descompune și a înțelege comportamentul malware-ului.      | [IDA Pro](https://www.hex-rays.com/ida-pro/)                                                 |
| **x64dbg**           | Debugger pentru fișierele binare care permite analizarea detaliată a codului.         | Încarci malware-ul în x64dbg, îl execuți pas cu pas și identifici flag-uri sau comportamente suspecte.  | [x64dbg](https://x64dbg.com/)                                                                |
| **CyberChef**        | Instrument pentru manipularea și decriptarea datelor.                                 | Importi datele criptate în CyberChef și aplici tehnici de criptografie pentru a descifra flag-ul.       | [CyberChef](https://gchq.github.io/CyberChef/)                                               |

#### **Identificarea Indicatorilor de Compromis (IoC)**

* **Fișiere**: Verifică dacă malware-ul creează fișiere noi sau le modifică pe cele existente. De obicei, flag-ul poate fi stocat într-un fișier care este creat sau modificat de malware.
* **Registri**: Căută în registrii Windows pentru intrări noi sau modificate. Malware-ul poate modifica anumite chei pentru a ascunde activitățile sale sau pentru a salva flag-ul.
* **Procese**: Dacă există procese suspecte sau noi care sunt lansate, acestea pot fi relevante pentru flag. Uneori, un fișier malware poate să-ți lase un proces care generează flag-ul sau care comunică cu servere externe pentru a-l furniza.
