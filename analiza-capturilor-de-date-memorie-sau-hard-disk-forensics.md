---
hidden: true
icon: binary-circle-check
---

# Analiza capturilor de date, memorie sau hard disk (forensics)

## Notiuni introductive

Criminalistica digitală (forensics) și securitatea cibernetică merg mână în mână; securitatea cibernetică nu ar fi la fel de importantă dacă nu ar fi informațiile furnizate de criminalistică digitală.

{% hint style="info" %}
Stiai ca?

Pentru a da o definiție formală, criminalistica digitală (denumită și criminalistică informatică sau cyber-criminalistică) este practica colectării, analizei și raportării informațiilor găsite pe computere și rețele, în așa fel încât acest proces să fie considerat admisibil într-un context juridic - fie ca dovadă într-o anchetă penală sau civilă, fie ca dovadă documentară într-un cadru comercial sau privat.
{% endhint %}

Securitatea cibernetică preia informațiile pe care criminalistica digitală le-a găsit în diferite cazuri și creează modalități de prevenire a incidentelor de securitate.

Securitatea cibernetică este în esență proactivă în vreme ce criminalistica digitala este reactiva.

### Ce poate fi investigat într-un incident informatic? <a href="#ce-poate-fi-investigat-intr-un-incident-informatic" id="ce-poate-fi-investigat-intr-un-incident-informatic"></a>

**Orice** **aplicație** **sau** **activitate** **realizata** **pe** **un** **sistem** **informatic** **lasa** **urme**, mai ales cand sunt              realizate îmbunătățiri ale capacității de detecție sau jurnalizare a activităților suspecte sau malițioase.

Intr-un incident informatic este foarte important sa colectezi si sa documentezi cat mai detaliat dovezile care vor ajuta la alcătuirea unei naratiuni pentru eveniment, ce va include elemente cu privire la modul în care s-a declanșat incidentul, care au fost consecintele, dacă amenințarea încă exista samd.

Aceste dovezi pot fi obtinute in mai multe moduri:

* Prin analiza unei capturi de memorie volatilă (de eg. RAM)
* Prin analiza unei capturi de trafic de rețea
* Prin analiza unei capturi a sistemelor de stocare (eg. HDD, USB samd)
* Prin analiza unor jurnale (logs) generate de sisteme de operare, aplicatii samd

#### Ce este criminalistica digitală? <a href="#ce-este-criminalistica-digitala" id="ce-este-criminalistica-digitala"></a>

<mark style="color:blue;">Criminalistica digitală este definită ca procesul de conservare, identificare, extragere și documentare a dovezilor computerizate care pot fi utilizate de instanța de judecată.</mark>

Criminalistica digitală este știința găsirii dovezilor din media digitală, cum ar fi un computer, telefon mobil, server sau rețea.

## Obiectivele criminalisticii computerizate <a href="#obiectivele-criminalisticii-computerizate" id="obiectivele-criminalisticii-computerizate"></a>

Printre obiectivele esențiale ale utilizării criminalisticii computerizate, putem enumera:

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

* Ajută la recuperarea, analiza și conservarea computerelor și a materialelor conexe în așa fel încât ajută echipa anchetatoare să le prezinte ca probe în instanță de judecată.
* Proiectarea procedurilor la locul suspectat al incidentului care vă ajută să vă asigurați că dovezile digitale obținute nu sunt corupte.
* Achiziționarea și duplicarea datelor: recuperarea fișierelor șterse și partițiilor șterse de pe suportul digital pentru a extrage dovezile și a le valida.
* Vă ajută să identificați rapid dovezile și, de asemenea, vă permite să estimați impactul potențial al activității dăunătoare asupra victimei
* Realizarea unui raport criminalistic computerizat care oferă o perspectivă completă asupra procesului de investigație.
* Conservarea probelor urmărind lanțul de custodie.

## Pașii procesului de criminalistică digitală <a href="#pasii-procesului-de-criminalistica-digitala" id="pasii-procesului-de-criminalistica-digitala"></a>

Procesul de criminalistică digitală presupune următorii pași:

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

**Identificare**

* Este primul pas în procesul criminalistic.
* Procesul de identificare include în principal lucruri precum:
  * ce dovezi sunt prezente
  * unde sunt stocate
  * cum sunt stocate (în ce format).
* Mediile de stocare electronice pot fi calculatoare personale, telefoane mobile, PDA-uri etc.

**Conservare**

* În această fază, datele sunt izolate, securizate și conservate.
* Acest pas de asemeni presupune și împiedicarea utilizării dispozitivului digital, astfel încât dovezile digitale să nu fie modificate.

**Analiză**

* În această etapă, agenții de investigație reconstituie fragmente de date și trag concluzii pe baza dovezilor găsite.

**Documentație**

* În acest moment, se realizează o înregistrare a tuturor datelor vizibile pentru o revizuire cât mai exactă asupra evenimentelor din timpul crimei.

**Prezentare**

* În acest ultim pas, se construiesc concluziile bazate pe informațiile adunate în etapele anterioare.

## Tipuri de criminalistică digitală <a href="#tipuri-de-criminalistica-digitala" id="tipuri-de-criminalistica-digitala"></a>

Putem enumera mai multe tipuri principale de criminalistică digitală:

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## 1. Disk Forensics

**Disk forensics** se ocupă cu extragerea datelor din mediile de stocare prin căutarea fișierelor active, modificate sau șterse. Dispozitivele digitale sunt baza multor operații din viața noastră, iar dovezile digitale sunt din ce în ce mai utilizate în investigații.

#### Caracteristici importante ale dovezilor digitale

* Pot fi ușor deteriorate sau distruse, adesea neintenționat.
* Exemplu: În timpul restaurării unei rețele după un incident, personalul tehnic poate afecta sursa validă a dovezilor.

#### Tipuri de copii legale

1. **Copiere de tip „drive to drive”**
   * Datele sunt transferate de pe un hard disk pe altul.
2. **Copiere de tip „drive în fișier”**
   * Datele sunt transferate într-un fișier situat pe altă unitate.
   * Creează o copie sector-pe-sector a hard disk-ului.
   * Formate comune: **DD (RAW)** sau **Encase (E01)**.

***

## 2. Networking Forensics

**Networking forensics** este o subcategorie a criminalisticii digitale, care analizează traficul din rețea pentru colectarea de dovezi legale.

#### Obiective principale

* Investigarea traficului suspect pentru depistarea malware-ului sau a atacurilor cibernetice.
* Identificarea comunicărilor umane, manipularea fișierelor și utilizarea anumitor cuvinte-cheie.

#### Utilizări

* Investigatori legali urmăresc comunicațiile și stabilesc cronologii.
* Organizațiile detectează anomalii, tentative de atac și alte incidente.

#### Știai că?

* Analiza traficului este mai dificilă decât criminalistica digitală computerizată, deoarece datele din rețea sunt adesea pierdute după transmisie.
* Legile privind confidențialitatea pot restricționa urmărirea și analiza activă a traficului.

***

## 3. Wireless Forensics

**Wireless forensics** este o subdiviziune a network forensics, care se concentrează pe analiza datelor din rețelele wireless.

#### Provocări

* Creșterea utilizării rețelelor wireless a dus la mai multe vulnerabilități și incidente.
* Evoluția rapidă a tehnologiei wireless face din acest domeniu o provocare continuă.

#### Pașii unui proces de forensics pentru wireless

1. **Captura**
   * Colectarea traficului Wi-Fi pentru studiu.
2. **Identificare**
   * Filtrarea pachetelor pe baza orei și datei.
3. **Analiză**
   * Clasificarea și reconstituirea pachetelor pe baza antetelor.

***

## 4. Criminalistica Digitală a Bazelor de Date

Această ramură studiază bazele de date și metadatele acestora.

#### Scopuri principale

* Determinarea succesiunii acțiunilor unui utilizator.
* Identificarea tranzacțiilor frauduloase.

***

## 5. Criminalistică Digitală pentru Malware

**Această ramură investighează codurile malițioase pentru înțelegerea structurii și impactului lor.**

#### Tipuri de malware

* Backdoor, Botnet, Downloader, Rootkit, Scareware, Worm/Virus, etc.

#### Simptomele unui sistem infectat

* Performanță scăzută a sistemului.
* Executabile necunoscute instalate.
* Trafic de rețea neașteptat.
* Setări modificate sau pop-up-uri neautorizate.

#### Metode de infiltrare

* Dispozitive detașabile, e-mailuri nesecurizate, site-uri de torrente, etc.

***

## 6. Criminalistică Digitală pentru Servicii de Tip E-mail

Se ocupă cu recuperarea și analiza e-mailurilor, inclusiv cele șterse, calendarelor și contactelor.

***

## 7. Criminalistică Digitală pentru Memorie

**Criminalistica memoriei** colectează și analizează date din memoria sistemului (RAM, cache, etc.).

#### Avantaje

* Informații despre procesele și conexiunile recente.
* Date critice precum chei de criptare, mesaje de chat și istoricul navigării.

#### Știai că?

Un **dump de memorie** capturează datele stocate în RAM la un moment specific, fiind util în investigarea incidentelor.

***

## 8. Criminalistică Digitală pentru Dispozitivele Mobile

**Se ocupă cu examinarea și analiza datelor din telefoanele mobile.**

#### Exemple de date recuperabile

* Contacte telefonice, jurnale de apeluri, SMS-uri, fișiere audio și video.

***

## 9. Criminalistică Digitală pentru Rețele de Calculatoare

Analizează informații precum istoricul browserului și loguri de sistem.

#### Proceduri standard

1. **Izolarea fizică** a dispozitivului.
2. **Crearea unei copii digitale** a mediului de stocare.
3. **Analiza pe copia digitală** folosind tehnici și aplicații software.

Criminalistica digitală computerizată a evoluat semnificativ, susținând investigațiile legate de rețelele de calculatoare.

## Provocări cu care se confruntă criminalistica digitală

În ziua de azi, criminalistica digitală se confruntă cu următoarele provocări:

* **Creșterea numărului de PC-uri** deținute de persoane fizice, companii și extinderea accesului la internet.
* **Disponibilitatea instrumentelor de hacking** ce pot fi descărcate gratuit din diferite surse publice.
* **Lipsa dovezilor fizice** îngreunează urmărirea penală.
* **Cantitatea mare de spațiu de stocare** în terabytes îngreunează activitatea de investigație.
* **Schimbările tehnologice rapide** necesită o actualizare constantă a metodelor de operare utilizate în criminalistica digitală.

***

## Exemple de utilizare a criminalisticii digitale

În ultima perioadă, organizațiile comerciale au folosit criminalistica digitală pentru identificarea și analiza următoarelor cazuri:

* **Furt de proprietate intelectuală**
* **Spionaj industrial**
* **Conflicte din spațiul locului de muncă**
* **Anchete de fraudă**
* **Utilizarea necorespunzătoare a internetului și a emailului la locul de muncă**
* **Probleme legate de falsuri**
* **Investigații falimentare**

***

## Avantajele criminalisticii digitale

Printre avantajele criminalisticii digitale, putem enumera:

* **Asigură integritatea sistemului computerizat.**
* Poate obține **probe valide**, care, aduse în instanță, pot duce la pedepsirea vinovatului.
* Ajută companiile să capteze informații importante despre **sistemele sau rețelele compromise**.
* Urmărește în mod eficient **criminalii cibernetici** de oriunde din lume.
* Ajută la **protejarea datelor și bunurilor unei organizații**.
* Permite **extragerea, procesarea și interpretarea probelor de fapt**, astfel încât să demonstreze acțiunea atacului cibernetic în instanță.

***

### 1. Instrumente Utilizate în Forensics

#### 1.1 Instrumente Populare

**Autopsy**

* **Descriere**: Un software open-source pentru analiza sistemelor de fișiere și a artefactelor post-mortem.
* **Funcționalități**:
  * Analiza completă a sistemului de fișiere (NTFS, FAT, ext).
  * Detectarea fișierelor șterse.
  * Crearea de timeline-uri pentru evenimentele sistemului.
  * Identificarea fișierelor bazată pe hash-uri cunoscute.
* **Descărcare**: [Autopsy](https://www.sleuthkit.org/autopsy/)

**Volatility**

* **Descriere**: Un framework open-source pentru analiza memoriei RAM.
* **Funcționalități**:
  * Extracția informațiilor despre procese și conexiuni.
  * Detectarea modulelor de kernel modificate.
  * Analiza malware din memorie.
* **Comenzi Utile**:
  * Listare procese: `volatility -f mem_dump.raw pslist`.
  * Conexiuni de rețea: `volatility -f mem_dump.raw netscan`.
  * Detectare artefacte malware: `volatility -f mem_dump.raw malfind`.
* **Descărcare**: [Volatility](https://www.volatilityfoundation.org/)

**FTK Imager**

* **Descriere**: Software gratuit pentru crearea de imagini forensic ale dispozitivelor.
* **Funcționalități**:
  * Creare imagini de disc în formate precum `.E01`, `.dd`.
  * Generare hash-uri MD5 și SHA-1 pentru verificarea integrității.
  * Vizualizarea directă a fișierelor și metadatelor.
* **Descărcare**: [FTK Imager](https://accessdata.com/product-download/ftk-imager-version-4-5)

#### 1.2 Configurare și Utilizare

**Configurarea Autopsy**

1. **Instalare**: Descărcați și instalați versiunea compatibilă cu sistemul de operare.
2. **Crearea unui caz**:
   * Selectați "New Case".
   * Adăugați o sursă de date (imagine de disc, fișiere individuale etc.).
3. **Analize posibile**:
   * Fișiere șterse: Folosiți modulul "File Analysis".
   * Hash-uri: Configurați "Hash Lookup" pentru detectarea fișierelor cunoscute (malware, documente sensibile).

**Utilizarea Volatility**

1. **Pregătirea imaginii de memorie**:
   * Capturați RAM folosind instrumente precum `DumpIt` (Windows) sau `dd` (Linux).
2. **Comenzi frecvente**:
   * Listează procese active: `volatility -f dump.mem pslist`.
   * Conexiuni rețea: `volatility -f dump.mem netscan`.
   * DLL-uri injectate: `volatility -f dump.mem malfind`.

**Configurarea FTK Imager**

1. **Capturarea imaginii**:
   * Alegeți sursa (dispozitiv fizic, partiție, fișier).
   * Selectați formatul imaginii și activați generarea de hash-uri.
2. **Vizualizare și export**:
   * Examinați structura fișierelor.
   * Exportați fișierele pentru analize suplimentare.

***

### 2. Procesul de Analiză Forensics

#### 2.1 Colectarea Dovezilor

* **Utilizare write-blocker**: Prevenirea modificării mediilor originale.
* **Captură de date**:
  * RAM: `DumpIt`, `Belkasoft RAM Capturer`.
  * Discuri: `FTK Imager`, `dd`.

#### 2.2 Păstrarea Integrității

* **Calcularea hash-urilor**:
  * Exemplu: `sha256sum image.dd > hash.txt`.
* **Documentare**:
  * Folosiți un lanț de custodie digital (Chain of Custody).

***

### 3. Analiza Capturilor de Date

#### 3.1 Trafic de Rețea

* **Instrumente recomandate**:
  * **Wireshark**: Captură și analiză pachete. Descărcare: [Wireshark](https://www.wireshark.org/)
  * **NetworkMiner**: Reconstrucția sesiunilor și fișierelor. Descărcare: [NetworkMiner](https://www.netresec.com/?page=NetworkMiner)
* **Analiză**:
  * Identificare IP-uri și porturi suspecte.
  * Decodarea sesiunilor criptate dacă sunt disponibile chei.

#### 3.2 Protocoale Specifice

* **HTTP**:
  * Reconstrucția cererilor și răspunsurilor.
* **DNS**:
  * Detectarea domeniilor suspecte sau necunoscute.

***

### 4. Analiza Memoriei

#### 4.1 Extracție și Analiză

* **Captură**:
  * Windows: `DumpIt`.
  * Linux: `dd if=/dev/mem of=mem_dump.raw`.
* **Comenzi Volatility**:
  * Detectarea proceselor ascunse: `volatility -f mem_dump.raw psscan`.
  * Analiza conexiunilor: `volatility -f mem_dump.raw netscan`.

#### 4.2 Detectare Artefacte

* **Malfind**: Identificare malware injectat.
* **Ldrmodules**: Detectare module ascunse.

***

### 5. Analiza Hard Disk-ului

#### 5.1 Structura Fișierelor

* **Instrumente recomandate**:
  * **The Sleuth Kit**: Suite de utilitare pentru analiza fișierelor. Descărcare: [The Sleuth Kit](https://www.sleuthkit.org/).
  * **Autopsy**: Detectarea fișierelor șterse și analiza artefactelor.

#### 5.2 Recuperare Date

* **Metode**:
  * Carving de date: Folosind `Autopsy` sau `Foremost`.
  * Analiza jurnalelor de sistem pentru modificări și ștergeri recente.

***

### Resurse și Link-uri Utile

* **Autopsy**: [https://www.sleuthkit.org/autopsy/](https://www.sleuthkit.org/autopsy/)
* **Volatility**: [https://www.volatilityfoundation.org/](https://www.volatilityfoundation.org/)
* **FTK Imager**: [https://accessdata.com/product-download/ftk-imager-version-4-5](https://accessdata.com/product-download/ftk-imager-version-4-5)
* **Wireshark**: [https://www.wireshark.org/](https://www.wireshark.org/)
* **NetworkMiner**: [https://www.netresec.com/?page=NetworkMiner](https://www.netresec.com/?page=NetworkMiner)
* **The Sleuth Kit**: [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
