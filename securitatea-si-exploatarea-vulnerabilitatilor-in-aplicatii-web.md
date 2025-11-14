---
description: 15.11.2025
icon: spider-web
---

# Securitatea și exploatarea vulnerabilităților în aplicații web

## 1. Introducere în arhitectura web

### Modelul client-server

* Clientul (browser) trimite cereri HTTP/HTTPS către server
* Serverul web (Apache, Nginx) procesează cererea
* Serverul de aplicație (PHP, Python, Node.js) execută logica business
* Baza de date stochează informațiile
* Fiecare componentă poate fi ținta unui atac

### Protocoalele HTTP și HTTPS

**Structura unei cereri HTTP**

{% code overflow="wrap" %}
```
GET /login.php HTTP/1.1 
Host: www.example.com 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) 
Accept: text/html,application/xhtml+xml 
Cookie: session_id=abc123xyz; user_pref=dark 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 45
username=admin&password=secret123
```
{% endcode %}

**Componente principale:**

* Request line: metodă HTTP + URL + versiune protocol
* Headers: metadata despre cerere (autentificare, cookies, tip conținut)
* Body: datele trimise (pentru POST, PUT, PATCH)

**Metode HTTP și utilizarea lor**

| Metodă | Descriere            | Utilizare comună                  |
| ------ | -------------------- | --------------------------------- |
| GET    | Solicită resurse     | Încărcare pagini, obținere date   |
| POST   | Trimite date         | Login, formular, upload           |
| PUT    | Actualizează resursă | Editare profil, modificare setări |
| DELETE | Șterge resursă       | Ștergere cont, mesaje             |
| PATCH  | Modifică parțial     | Actualizare câmp specific         |

**Coduri de status HTTP detaliate**

| Cod | Semnificație          | Utilizare tipică           |
| --- | --------------------- | -------------------------- |
| 200 | OK                    | Cerere procesată cu succes |
| 301 | Moved Permanently     | Redirecționare permanentă  |
| 302 | Found                 | Redirecționare temporară   |
| 400 | Bad Request           | Cerere malformată          |
| 401 | Unauthorized          | Necesită autentificare     |
| 403 | Forbidden             | Acces interzis             |
| 404 | Not Found             | Resursă inexistentă        |
| 500 | Internal Server Error | Eroare server              |

### Cookies și sesiuni

* **Cookies**: date stocate în browser, trimise automat la fiecare cerere
* **Sesiuni**: date stocate pe server, asociate cu un session ID
* **Session ID**: stocat de obicei într-un cookie
* **Vulnerabilități**: session hijacking, session fixation, cross-site request forgery

## 2. HTML și CSS de bază

### Structura unui document HTML&#x20;

```html
<!DOCTYPE html>
<html>
<head>
  <title>exemplu</title>
</head>
<body>
  <h1>hello</h1>
</body>
</html>
```

### Elemente HTML critice pentru securitate

* **Formulare**: `<form>`, `<input>`, `<textarea>`, `<select>`
* **Scripting**: `<script>`, `<noscript>`
* **Multimedia**: `<img>`, `<video>`, `<audio>`
* **Iframe**: `<iframe>` pentru încorporare conținut extern

### CSS și implicațiile de securitate

* **Selectori CSS**: permit targetarea elementelor specifice
* **Proprietăți riscante**: `expression()`, `url()`, `behavior`
* **Keylogger CSS**: tehnici avansate de capturare a tastaturii

### HTML injection și CSS injection

* **HTML injection**: injectarea de tag-uri HTML prin inputuri nevalidate
* **CSS injection**: exploitarea proprietăților CSS pentru atacuri
* **Impact**: defacing, phishing, keylogging

## 3. Introducere în limbaje de programare web

### JavaScript - partea de client

**Manipularea DOM (Document Object Model):**&#x20;

<pre class="language-javascript" data-title="script.js" data-line-numbers><code class="lang-javascript"><strong>const element = document.getElementById('myElement'); 
</strong><strong>const elements = document.querySelectorAll('.myClass');
</strong><strong>
</strong>element.innerHTML = 'Noul conținut'; 
element.textContent = 'Text sigur';

element.setAttribute('src', 'newimage.jpg'); 
const value = element.getAttribute('data-custom');

button.addEventListener('click', function(event) { 
    event.preventDefault(); console.log('Buton apăsat'); 
});

form.addEventListener('submit', function(event) { 
    const input = document.getElementById('username'); 
    if (input.value.length &#x3C; 3) { 
        alert('Numele trebuie să aibă minim 3 caractere'); 
        event.preventDefault(); 
    } 
});
</code></pre>

### Python Flask - framework web

{% code title="app.py" %}
```python
from flask import Flask, request, session, render_template_string, redirect, url_for

app = Flask(__name__)
app.secret_key = 'cheie-secreta-foarte-complexa'

@app.route('/')
def index():
    return 'Pagina principală'

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        # Verificare credențiale
        if username == 'admin' and password == 'secret':
            session['logged_in'] = True
            session['username'] = username
            return redirect(url_for('dashboard'))
    return '''
    <form method="post">
        <input type="text" name="username" placeholder="Utilizator">
        <input type="password" name="password" placeholder="Parolă">
        <button type="submit">Login</button>
    </form>
    '''

@app.route('/dashboard')
def dashboard():
    if not session.get('logged_in'):
        return redirect(url_for('login'))
    return f'Bun venit, {session["username"]}!'
```
{% endcode %}

### PHP - procesare server-side

{% code title="server.php" %}
```php
<?php
session_start();

header('Content-Type: text/html; charset=utf-8');

if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['login'])) {
    $username = $_POST['username'];
    $password = $_POST['password'];
    
    if (!empty($username) && !empty($password)) {
        if ($username === 'admin' && $password === 'secret123') {
            $_SESSION['user_id'] = 1;
            $_SESSION['username'] = $username;
            $_SESSION['logged_in'] = true;
            header('Location: dashboard.php');
            exit;
        } else {
            $error = 'Credențiale invalide';
        }
    } else {
        $error = 'Completați toate câmpurile';
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Login</title>
</head>
<body>
    <?php if (isset($error)): ?>
        <div style="color: red;"><?php echo htmlspecialchars($error); ?></div>
    <?php endif; ?>
    
    <form method="post">
        <input type="text" name="username" placeholder="Utilizator" required>
        <input type="password" name="password" placeholder="Parolă" required>
        <button type="submit" name="login">Autentificare</button>
    </form>
</body>
</html>
```
{% endcode %}

## 4. Vulnerabilități web comune (OWASP Top 10)

| Poziție | Vulnerabilitate                                 | Descriere Scurtă                         | Impact                                    |
| ------- | ----------------------------------------------- | ---------------------------------------- | ----------------------------------------- |
| 1       | **Injection**                                   | Interogări SQL, NoSQL, OS, LDAP nesigure | Pierdere date, execuție cod la distanță   |
| 2       | **Broken Authentication**                       | Gestionare defectuoasă a autentificării  | Preluare conturi, acces neautorizat       |
| 3       | **Sensitive Data Exposure**                     | Expunere date sensibile necriptate       | Furt date personale, financiare           |
| 4       | **XML External Entities (XXE)**                 | Procesare nesigură a fișierelor XML      | Acces la sistem de fișiere, scanare rețea |
| 5       | **Broken Access Control**                       | Control acces insuficient                | Acces neautorizat la funcționalități      |
| 6       | **Security Misconfiguration**                   | Configurație nesigură                    | Diverse vulnerabilități de securitate     |
| 7       | **Cross-Site Scripting (XSS)**                  | Execuție cod JavaScript malitios         | Furt sesiuni, defacing                    |
| 8       | **Insecure Deserialization**                    | Deserializare nesigură a obiectelor      | Execuție cod la distanță                  |
| 9       | **Using Components with Known Vulnerabilities** | Componente cu vulnerabilități cunoscute  | Diverse atacuri în funcție de componentă  |
| 10      | **Insufficient Logging & Monitoring**           | Logging și monitorizare insuficiente     | Detectare întârziată a incidentelor       |

#### A01:2021 - Injection

**SQL Injection - Exemplu vulnerabil:**

```php
// COD VULNERABIL - concatenare directă în query
$user = $_POST['username'];
$pass = $_POST['password'];
$query = "SELECT * FROM users WHERE username = '$user' AND password = '$pass'";
$result = mysqli_query($conn, $query);
```

**Prevenire - Prepared statements:**

```php
// COD SECURIZAT - folosire prepared statements
$stmt = $conn->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
$stmt->bind_param("ss", $user, $pass);
$stmt->execute();
```

#### A02:2021 - Broken Authentication

**Autentificare vulnerabilă:**

```php
// COD VULNERABIL - parolă stocată plain text
$password = $_POST['password']; // "secret123"
$sql = "INSERT INTO users (username, password) VALUES ('$user', '$password')";
```

**Prevenire - Hash + Salt:**

```php
// COD SECURIZAT - hash cu salt
$password_hash = password_hash($_POST['password'], PASSWORD_DEFAULT);
$stmt = $conn->prepare("INSERT INTO users (username, password) VALUES (?, ?)");
$stmt->bind_param("ss", $user, $password_hash);
```

#### A03:2021 - Sensitive Data Exposure

**Date expuse:**

```php
// COD VULNERABIL - conexiune HTTP, date necriptate
<form action="http://site.com/login" method="post">
    <input type="text" name="credit_card" value="4111-1111-1111-1111">
</form>
```

**Prevenire - HTTPS + Encryptare:**

```php
// COD SECURIZAT - forțare HTTPS
if (!isset($_SERVER['HTTPS'])) {
    header("Location: https://" . $_SERVER['HTTP_HOST'] . $_SERVER['REQUEST_URI']);
    exit();
}
```

#### A07:2021 - Cross-Site Scripting (XSS)

**XSS Reflected vulnerabil:**

```php
// COD VULNERABIL - output neescapat
$search = $_GET['q'];
echo "Rezultate pentru: " . $search; // <script>alert('XSS')</script>
```

**Prevenire - Escapare output:**

```php
// COD SECURIZAT - escapare HTML
$search = $_GET['q'];
echo "Rezultate pentru: " . htmlspecialchars($search, ENT_QUOTES, 'UTF-8');
```

#### A05:2021 - Broken Access Control

**Control acces lipsă:**

```php
// COD VULNERABIL - fără verificare rol
$user_id = $_GET['user_id'];
$sql = "DELETE FROM users WHERE id = $user_id";
// Orice utilizator poate șterge orice cont!
```

**Prevenire - Verificare autorizare:**

```php
// COD SECURIZAT - verificare permisiuni
session_start();
$user_id = $_GET['user_id'];
if ($_SESSION['user_id'] == $user_id || $_SESSION['role'] == 'admin') {
    $stmt = $conn->prepare("DELETE FROM users WHERE id = ?");
    $stmt->bind_param("i", $user_id);
    $stmt->execute();
}
```

#### A06:2021 - Security Misconfiguration

**Configurație vulnerabilă:**

```php
// COD VULNERABIL - error reporting enabled în production
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);
// Afișează informații sensibile în erori!
```

**Prevenire - Configurație secure:**

```php
// COD SECURIZAT - error reporting disabled
ini_set('display_errors', 0);
ini_set('display_startup_errors', 0);
error_reporting(0);
// Log errors într-un fișier secure
```

#### A08:2021 - Software and Data Integrity Failures

**Dependințe vulnerabile:**

```json
// package.json cu versiuni vulnerabile
{
  "dependencies": {
    "express": "4.16.0", // Versiune cu vulnerabilități cunoscute
    "lodash": "4.17.10"
  }
}
```

**Prevenire - Versiuni actualizate:**

```json
// package.json cu versiuni sigure
{
  "dependencies": {
    "express": "4.18.0", // Versiune actualizată
    "lodash": "4.17.21"
  }
}
```

#### A10:2021 - Server-Side Request Forgery (SSRF)

**SSRF vulnerabil:**

```php
// COD VULNERABIL - cereri server-side nevalidate
$url = $_GET['url']; // http://internal-server:8080/admin
$content = file_get_contents($url);
echo $content; // Acces la rețea internă!
```

**Prevenire - Validare URL:**

```php
// COD SECURIZAT - whitelist domain-uri
$allowed_domains = ['api.site.com', 'cdn.site.com'];
$url = $_GET['url'];
$domain = parse_url($url, PHP_URL_HOST);

if (in_array($domain, $allowed_domains)) {
    $content = file_get_contents($url);
    echo $content;
} else {
    http_response_code(403);
    echo "Domain nepermis!";
}
```

## 5. Unelte pentru testarea securității web

### Browser Developer Tools - funcționalități avansate

**Network Tab:**

* Monitorizare cereri/respunse HTTP
* Inspectare headere și cookies
* Analiză timpi de răspuns
* Export date de network

**Console:**

* Executare cod JavaScript
* Testare payload-uri XSS
* Debugging aplicații

**Application Tab:**

* Vizualizare și editare cookies
* Inspectare localStorage/sessionStorage
* Clear site data

**Sources:**

* Debugging cod JavaScript
* Setare breakpoints
* Editare cod în timp real

### Burp Suite Community Edition - ghid de utilizare

**Setup proxy:**

1. Configurează browserul să folosească proxy (127.0.0.1:8080)
2. Instalează certificate Burp pentru interceptare HTTPS
3. Activează interceptarea în tab-ul Proxy

**Funcționalități cheie:**

* **Proxy**: Interceptare și modificare trafic în timp real
* **Repeater**: Retrimitere și manipulare cereri individuale
* **Intruder**: Atacuri automate (brute force, fuzzing)
* **Decoder**: Codificare/decodare Base64, URL, HTML
* **Comparer**: Comparare vizuală a răspunsurilor

**Workflow tipic:**

1. Interceptează cererea de login
2. Trimite la Repeater
3. Modifică parametrii și testează SQLi/XSS
4. Utilizează Intruder pentru atacuri automate

### Scannere de directoare și resurse

**Dirsearch:** dirsearch -u https://target.com -e php,html,js,txt -w common.txt -t 20

**Gobuster:** gobuster dir -u https://target.com -w /usr/share/wordlists/dirb/common.txt -x php,html -t 50

**FFUF (Fast Web Fuzzer):** ffuf -u https://target.com/FUZZ -w wordlist.txt -mc 200,301,302

### OWASP ZAP (Zed Attack Proxy)

**Caracteristici principale:**

* Scanare automată vulnerabilități
* Spider pentru maparea aplicației
* Fuzzer pentru testare inputuri
* Scripting support (JavaScript, Zest)
* Rapoarte detaliate

**Workflow ZAP:**

1. Configurează scope-ul țintei
2. Rulează Spider pentru a descoperi toate URL-urile
3. Execută scanare activă
4. Analizează rezultatele
5. Exportă raportul

#### Unelte specializate

**SQLMap pentru SQL injection:** sqlmap -u "https://site.com/page?id=1" --dbs sqlmap -u "https://site.com/page?id=1" -D database --tables sqlmap -u "https://site.com/page?id=1" -D database -T users --dump

**Nikto pentru scanare server web:** nikto -h https://target.com -output results.html

**Nmap pentru enumerare:** nmap -sV -sC target.com nmap --script http-enum target.com

## 6. Bune practici de securitate comprehensive

### Validarea input-urilor - strategii multi-nivel

**Validare pe client (UX):**

* Feedback imediat pentru utilizator
* Prevenirea unor erori evidente
* NU se bazează doar pe aceasta pentru securitate

**Validare pe server (Security):**

* Whitelist în loc de blacklist
* Validare bazată pe tipul așteptat
* Sanitizare specifică contextului

**Exemplu validare complexă:** function validateUserInput($input, $rules) { $errors = \[];

```
if (isset($rules['min_length']) && strlen($input) < $rules['min_length']) {
    $errors[] = "Input prea scurt";
}

if (isset($rules['pattern']) && !preg_match($rules['pattern'], $input)) {
    $errors[] = "Format invalid";
}

if (isset($rules['type'])) {
    switch($rules['type']) {
        case 'email':
            $input = filter_var($input, FILTER_SANITIZE_EMAIL);
            break;
        case 'string':
            $input = htmlspecialchars($input, ENT_QUOTES, 'UTF-8');
            break;
    }
}

return ['value' => $input, 'errors' => $errors];
```

}

#### Gestionarea autentificării și autorizării

**Stocare parole:** // Hash cu salt $password\_hash = password\_hash($password, PASSWORD\_DEFAULT);

// Verificare if (password\_verify($input\_password, $stored\_hash)) { // Autentificare reușită }

**Mecanisme de protecție:**

* Limitare încercări de login
* Lockout automat după X încercări eșuate
* Session timeout
* Reautentificare pentru acțiuni critice

**Autentificare multi-factor:**

* Token-uri temporare (TOTP)
* SMS codes
* Biometrică
* Hardware tokens

#### Securizarea comunicării și a datelor

**Configurație HTTPS corectă:**

* Certificate SSL/TLS valide
* Redirectare HTTP to HTTPS
* HSTS (HTTP Strict Transport Security)
* Cipher suites sigure

**Headere de securitate:** Strict-Transport-Security: max-age=31536000; includeSubDomains X-Content-Type-Options: nosniff X-Frame-Options: DENY Content-Security-Policy: default-src 'self' X-XSS-Protection: 1; mode=block

#### Monitorizare, logging și răspuns la incidente

**Logging comprehensiv:**

* Autentificări (succes/eșec)
* Acțiuni administrative
* Erori de aplicație
* Activitate suspectă

**Monitorizare în timp real:**

* Alertă pentru multiple login failures
* Detectare pattern-uri de atac
* Analiză trafic anormal

**Plan de răspuns la incidente:**

* Proceduri de izolare
* Notificare părți afectate
* Analiză post-incident
* Îmbunătățiri de securitate
