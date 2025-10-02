---
hidden: true
icon: binary
---

# Programa CJEXSV Securitate Cibernetică - 2024

Acest document respectă și este în deplină conformitate cu programa oficială pentru Olimpiada de Securitate Cibernetică, nivelul liceal, aprobată de Ministerul Educației pentru anul școlar 2023-2024. Conținutul acoperă toate domeniile de evaluare prevăzute în cadrul competiției.

***

### Cuprins

1. Criptografie și algoritmi de criptare, encodare sau hashing
2. Securitatea și exploatarea vulnerabilităților în aplicații web
3. Securitatea și exploatarea vulnerabilităților în aplicații mobile / desktop
4. Informațiile obținute pe baza tehnicilor și uneltelor de tip OSINT
5. Enumerarea și exploatarea serviciilor și sistemelor
6. Analiza jurnalelor electronice (logs)
7. Analiza traficului de rețea
8. Analiza capturilor de date, memorie sau hard disk (forensics)
9. Inginerie inversă pentru aplicații executabile, scripturi sau documente
10. Securitatea rețelelor wireless
11. Auditul codului sursă
12. Configurarea și securitatea sistemelor de operare și rețele
13. Programare și scripting pentru automatizarea rezolvării unor exerciții
14. Cunoștințe specifice pentru exercițiile de Attack & Defence
15. Dezvoltarea unor mecanisme de apărare a unui sistem sau rețele informatice
16. Monitorizarea unui sistem sau a unei rețele informatice pentru identificarea elementelor de securitate cibernetică
17. Identificarea și exploatarea unor vulnerabilități în sisteme informatice

***

### 1. Criptografie și algoritmi de criptare, encodare sau hashing <a href="#criptografie" id="criptografie"></a>

#### 1.1 Criptografie simetrică

**Algoritmi:**

* AES (Advanced Encryption Standard)
* DES (Data Encryption Standard)
* 3DES (Triple DES)

**Moduri de operare:**

* ECB (Electronic Codebook)
* CBC (Cipher Block Chaining)

**Implementări și vulnerabilități comune:**

* Padding oracle attacks
* Chosen-plaintext attacks
* Side-channel attacks

#### 1.2 Criptografie asimetrică

**RSA:**

* Principii fundamentale
* Implementare practică
* Considerații de securitate (e.g., padding schemes)

**Diffie-Hellman:**

* Protocolul de schimb de chei
* Aplicații practice
* Variante: Elliptic Curve Diffie-Hellman (ECDH)

**Infrastructura cu Chei Publice (PKI):**

* Certificate digitale
* Autorități de certificare
* Managementul certificatelor
* Certificate Transparency

#### 1.3 Funcții hash

**Tipuri de funcții hash:**

* MD5 (considerat nesigur)
* SHA-1 (depreciat)
* SHA-256
* SHA-3
* Blake2, Blake3

**Aspecte de securitate:**

* Coliziuni
* Atacuri cunoscute (e.g., length extension attacks)
* Best practices

**Aplicații practice:**

* Autentificare
* Verificarea integrității datelor
* Blockchain și criptomonede

#### 1.4 Encodare

**Metode de encodare:**

* Base64
* Hexadecimal
* URL encoding
* Unicode encoding

**Tehnici avansate:**

* Compresia datelor
* Steganografie
* Metode de ascundere a datelor
* Detectarea steganografiei
* Watermarking digital

***

### 2. Securitatea și exploatarea vulnerabilităților în aplicații web <a href="#vulnerabilitati-aplicatii-web" id="vulnerabilitati-aplicatii-web"></a>

#### 2.1 Vulnerabilități OWASP Top 10

**Injecții:**

* SQL Injection
* NoSQL Injection
* Command Injection
* XML Injection

**Cross-Site Scripting (XSS):**

* Reflected XSS
* Stored XSS
* DOM-based XSS
* XSS Filters Evasion

**Cross-Site Request Forgery (CSRF)**

**Broken Authentication:**

* Vulnerabilități comune
* Metode de prevenire
* Multi-factor authentication

**Broken Access Control**

**Security Misconfiguration**

**Sensitive Data Exposure**

**Insecure Deserialization**

**Using Components with Known Vulnerabilities**

**Insufficient Logging & Monitoring**

#### 2.2 Testarea securității Web

**Metodologii standardizate:**

* OWASP Testing Guide
* PTES (Penetration Testing Execution Standard)
* NIST SP 800-115

**Unelte esențiale:**

* Burp Suite (Professional/Community)
* OWASP ZAP
* Nikto
* SQLmap
* BeEF (Browser Exploitation Framework)

**Automatizarea:**

* Scanere de vulnerabilități
* Scripturi personalizate
* CI/CD pentru testare de securitate
* Integrarea securității în pipeline-ul de dezvoltare

#### 2.3 Securitatea aplicațiilor web

**Validarea și sanitizarea input-ului:**

* Practici de validare a datelor utilizatorului
* Biblioteci de sanitizare pentru diferite limbaje

**Managementul sesiunilor securizat:**

* Protecția sesiunilor și gestionarea acestora în siguranță
* Tokenuri de sesiune securizate

**HTTP Security Headers:**

* X-XSS-Protection
* X-Frame-Options
* X-Content-Type-Options
* Strict-Transport-Security (HSTS)
* Content Security Policy (CSP)

**Securizarea API-urilor web:**

* Autentificare și autorizare pentru API-uri
* Rate limiting și throttling

**HTTPS și TLS:**

* Configurare corectă a HTTPS
* Certificate SSL/TLS
* Perfect Forward Secrecy (PFS)

***

### 3. Securitatea și exploatarea vulnerabilităților în aplicații mobile / desktop <a href="#vulnerabilitati-aplicatii-mobile-desktop" id="vulnerabilitati-aplicatii-mobile-desktop"></a>

#### 3.1 Vulnerabilități mobile

* Stocarea nesigură a datelor
* Criptarea datelor locale
* Securizarea bazelor de date mobile
* Comunicarea nesigură client-server
* Certificate pinning
* Protecția împotriva atacurilor Man-in-the-Middle
* Reverse engineering aplicații mobile
* Decompilarea și analiza codului
* Protecția proprietății intelectuale

#### 3.2 Securitatea aplicațiilor desktop

* Buffer overflows
* Stack-based overflows
* Heap-based overflows

**Mitigări:**

* ASLR
* DEP
* Stack Canaries

**DLL injection:**

* Tehnici de injecție
* Detectarea și prevenirea injecțiilor

**Memory safety:**

* Use-after-free vulnerabilities
* Uninitialized memory usage

#### 3.3 Tehnici de protecție

* Code signing
* Verificarea integrității
* Anti-debugging
* Obfuscarea fluxului de execuție
* Balansarea între securitate și performanță

***

### 4. Informațiile obținute pe baza tehnicilor și uneltelor de tip OSINT <a href="#osint" id="osint"></a>

#### 4.1 Surse de informații

* Rețele sociale: Facebook, LinkedIn, Twitter, Instagram
* Registre publice: WHOIS, Registre de companii
* Motoare de căutare specializate: Google, Bing, DuckDuckGo, Shodan

#### 4.2 Tehnici de colectare

* Google dorks
* Operatorii de căutare avansați
* Metadata analysis
* Corelarea informațiilor din multiple surse
* Căutare avansată pe platforme sociale
* Utilizarea API-urilor pentru colectarea datelor

#### 4.3 Unelte OSINT

* Maltego
* Shodan
* theHarvester
* Recon-ng

***

### 5. Enumerarea și exploatarea serviciilor și sistemelor <a href="#enumerare-exploatare-servicii" id="enumerare-exploatare-servicii"></a>

#### 5.1 Reconnaissance

**Network scanning (Nmap):**

* Tehnici de scanare (SYN, TCP Connect, UDP)
* Evasiunea sistemelor de detectare
* Bypass Firewall/IDS

**Port scanning:**

* Identificarea serviciilor expuse
* Evaluarea riscurilor asociate porturilor deschise

#### 5.2 Exploatarea vulnerabilităților cunoscute

**Framework-uri:**

* Metasploit
* ExploitDB
* Searchsploit

### 7. Analiza traficului de rețea <a href="#analiza-trafic-retea" id="analiza-trafic-retea"></a>

#### 7.1 Capturarea și inspecția pachetelor

**Unelte utilizate:**

* Wireshark
* Tcpdump
* TShark

**Aspecte de analiză:**

* Filtrarea și sortarea pachetelor
* Interpretarea protocoalelor (e.g., TCP, HTTP, DNS)
* Identificarea comunicațiilor suspecte

#### 7.2 Detectarea atacurilor de rețea

* Atacuri de tip Denial-of-Service (DoS, DDoS)
* Spoofing (MAC, IP)
* Sniffing
* Man-in-the-Middle (MitM)

#### 7.3 Analiza protocolului

* TCP/IP fundamentals
* HTTP(S) analysis
* DNS analysis
* SSL/TLS handshake și identificarea problemelor de securitate

***

### 8. Analiza capturilor de date, memorie sau hard disk (forensics) <a href="#forensics" id="forensics"></a>

#### 8.1 Recuperarea și analiza datelor

* Imaging (copierea unui disc pentru analiză)
* Analiza sistemelor de fișiere (FAT, NTFS, EXT)
* Identificarea artefactelor critice (e.g., fișiere șterse, date criptate)

#### 8.2 Unelte de forensic

* Autopsy/Sleuth Kit
* FTK (Forensic Toolkit)
* EnCase
* Volatility (pentru analiza memoriei)

#### 8.3 Reconstrucția evenimentelor

* Timeline analysis
* Coroborarea artefactelor
* Identificarea exfiltrării de date

***

### 9. Inginerie inversă pentru aplicații executabile, scripturi sau documente <a href="#reverse-engineering" id="reverse-engineering"></a>

#### 9.1 Tehnici de inginerie inversă

* Decompilare
* Debugging
* Dynamic Analysis (e.g., executarea codului într-un mediu controlat)
* Static Analysis (e.g., interpretarea codului fără a-l rula)

#### 9.2 Unelte folosite

* Ghidra
* IDA Pro
* Radare2
* Binary Ninja
* OllyDbg

#### 9.3 Protecții împotriva ingineriei inverse

* Obfuscation
* Anti-debugging tehnici
* Encryption of executables

***

### 10. Securitatea rețelelor wireless <a href="#securitate-retele-wireless" id="securitate-retele-wireless"></a>

#### 10.1 Vulnerabilități specifice

* WEP (depreciat și considerat nesigur)
* WPA/WPA2-PSK
* Atacuri de tip Evil Twin
* Crackerea parolelor Wi-Fi (e.g., WPA handshake capture)

#### 10.2 Unelte pentru securitatea rețelelor wireless

* Aircrack-ng
* Kismet
* Wireshark (pentru rețele wireless)
* Reaver (pentru WPS)

***

### 11. Auditul codului sursă <a href="#audit-cod-sursa" id="audit-cod-sursa"></a>

#### 11.1 Metodologii de auditare

* Analiza manuală a codului
* Analiza statică automatizată

#### 11.2 Unelte pentru auditul codului

* SonarQube
* Semgrep
* Bandit (pentru cod Python)
* ESLint (pentru cod JavaScript)

#### 11.3 Vulnerabilități comune în cod

* SQL Injection
* Cross-Site Scripting (XSS)
* Buffer Overflow
* Race Conditions

***

### 12. Configurarea și securitatea sistemelor de operare și rețele <a href="#securitate-sisteme-operare-retele" id="securitate-sisteme-operare-retele"></a>

#### 12.1 Practici de configurare sigură

* Hardening (sisteme Linux, Windows)
* Dezactivarea serviciilor nefolosite
* Configurarea corectă a permisiunilor de fișiere

#### 12.2 Securitatea rețelelor

* Configurarea firewall-urilor
* Implementarea sistemelor de detecție și prevenire a intruziunilor (IDS/IPS)
* Segmentarea rețelelor

#### 12.3 Managementul patch-urilor

* Sisteme de actualizare automată
* Evaluarea vulnerabilităților și aplicarea corecțiilor

***

### 13. Programare și scripting pentru automatizarea rezolvării unor exerciții <a href="#programare-scripting" id="programare-scripting"></a>

#### 13.1 Limbaje de scripting utilizate frecvent

* Python
* Bash
* PowerShell
* Perl

#### 13.2 Automatizarea proceselor

* Automating network scans (e.g., Nmap scripts)
* Parsing logs și extragerea de informații utile
* Scripturi pentru atacuri automatizate (e.g., brute force, fuzzing)

***

### 14. Cunoștințe specifice pentru exercițiile de Attack & Defence <a href="#cunostinte-specifice-attack-defence" id="cunostinte-specifice-attack-defence"></a>

#### 14.1 Red Team

* **Planificarea atacurilor**:
  * Dezvoltarea strategiilor de atac
  * Crearea scenariilor de amenințări realiste
* **Tehnici de evasiune**:
  * Bypass-ul soluțiilor de securitate
  * Tehnici de obfuscare și anti-forensics
* **Raportare și documentare**:
  * Crearea rapoartelor detaliate de penetrare
  * Documentarea pas cu pas a atacurilor

#### 14.2 Blue Team

* **Strategii de apărare**:
  * Implementarea defense-in-depth
  * Hardening-ul sistemelor și aplicațiilor
* **Incident response**:
  * Crearea și testarea planurilor de răspuns la incidente
  * Tehnici de contenție și eradicare a amenințărilor
* **Threat hunting**:
  * Tehnici proactive de căutare a amenințărilor
  * Utilizarea OSINT pentru intelligence de securitate

#### 14.3 Purple Team

* **Threat emulation**:
  * Simularea atacurilor avansate persistente (APT)
  * Testarea eficacității controalelor de securitate
* **Validarea controalelor de securitate**:
  * Evaluarea continuă a posturii de securitate
  * Optimizarea măsurilor de securitate bazată pe rezultatele testelor
* **Îmbunătățirea continuă a securității**:
  * Implementarea ciclului de feedback pentru securitate
  * Actualizarea politicilor și procedurilor bazate pe lecțiile învățate

***

### Note finale

Acest curriculum este destinat să ofere o bază solidă în securitate cibernetică, combinând teoria cu practica intensivă. Se recomandă actualizarea constantă a conținutului pentru a reflecta evoluția rapidă a domeniului securității cibernetice.
