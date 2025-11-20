# 📧 E-Mail-Vorlage — So entschlüsselst und benutzt du sie

In diesem Repository liegt eine **passwortgeschützte HTML-E-Mail-Vorlage**.
Damit nicht jede Person im Internet sie sehen kann, ist die Datei verschlüsselt.
Hier erfährst du Schritt für Schritt, wie du die Datei öffnest und die E-Mail benutzen und ändern kannst.

---

# 🖥️ 0. Wie öffne ich PowerShell, Bash oder das Terminal?

Bevor du Git oder Befehle benutzen kannst, musst du wissen, wie du ein Terminal öffnest. Hier steht’s ganz einfach erklärt:

## 🔹 Windows

### **PowerShell öffnen:**

1. Drücke die **Windows-Taste**.
2. Tippe **PowerShell** ein.
3. Klicke auf **Windows PowerShell**.

### **Git Bash öffnen (falls installiert):**

1. Drücke die **Windows-Taste**.
2. Tippe **Git Bash** ein.
3. Klicke auf **Git Bash**.

---

## 🔹 macOS

### **Terminal öffnen:**

Option A:

1. Drücke **Cmd + Leertaste** (Spotlight).
2. Tippe **Terminal** ein.
3. Öffne es.

Option B:

* Apps → Dienstprogramme → **Terminal**

---

## 🔹 Linux (Ubuntu / Debian / Mint etc.)

### **Terminal öffnen:**

1. Drücke **Ctrl + Alt + T**
   (funktioniert bei vielen Linux-Distributionen)

ODER:

* Öffne das App-Menü
* Suche nach **Terminal** oder **Konsole** (bei KDE)

---

# 🛠️ 0. Git installieren (für komplette Anfänger)

Falls du Git noch **nie** benutzt hast, musst du es zuerst installieren.

## 🔹 Windows

1. Öffne diese Seite: [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Lade den Installer herunter.
3. Starte ihn und klicke dich mit den Standard-Einstellungen durch.
4. Nach der Installation kannst du Git Bash oder PowerShell verwenden.

## 🔹 macOS

Git ist meistens schon installiert. Du kannst testen:

```sh
git --version
```

Wenn Git nicht installiert ist, kannst du es über **Homebrew** installieren:

```sh
brew install git
```

Oder direkt über Xcode Command Line Tools:

```sh
xcode-select --install
```

## 🔹 Linux (Ubuntu / Debian)

```sh
sudo apt update
sudo apt install git
```

## 🔹 Linux (Fedora / CentOS / RHEL)

```sh
sudo dnf install git
```

---

# 🛠️ 1. Repository herunterladen

## 🔹 Linux / macOS

```sh
git clone https://github.com/dontwonderhow/iriemember.git
cd iriemember
```

## 🔹 Windows (PowerShell oder Git Bash)

```powershell
git clone https://github.com/dontwonderhow/iriemember.git
cd iriemember
```

---

# 🔐 2. Die Vorlage entschlüsseln

Die verschlüsselte Datei findest du hier:

```
email/20251120_template.html.enc
```

Du brauchst dafür das Passwort, das dir gegeben wurde.

---

## ✔️ Linux / macOS

Führe diesen Befehl im Repository-Ordner aus:

```sh
openssl aes-256-cbc -d -salt -pbkdf2 \
  -in email/20251120_template.html.enc \
  -out email/20251120_template.html
```

Gib das Passwort ein, wenn du gefragt wirst.

Wenn alles funktioniert hat, erscheint die entschlüsselte Datei:

```
email/20251120_template.html
```

---

## ✔️ Windows

### 🔸 Option 1 — Git Bash (einfachste Variante)

Falls du Git Bash hast, gib Folgendes ein:

```sh
openssl aes-256-cbc -d -salt -pbkdf2 \
  -in email/20251120_template.html.enc \
  -out email/20251120_template.html
```

### 🔸 Option 2 — Wenn OpenSSL extra installiert wurde

In PowerShell oder der Eingabeaufforderung:

```powershell
openssl aes-256-cbc -d -salt -pbkdf2 -in email/20251120_template.html.enc -out email/20251120_template.html
```

Gib das Passwort ein.

---

# 🌐 3. Die HTML-Datei im Browser öffnen

Nach dem Entschlüsseln kannst du die Datei einfach doppelklicken:

```
email/20251120_template.html
```

### macOS

```sh
open email/20251120_template.html
```

### Linux

```sh
xdg-open email/20251120_template.html
```

### Windows

→ Rechtsklick → **Öffnen mit → Browser auswählen**
(Chrome, Firefox, Edge … alles funktioniert.)

---

# 📋 4. Inhalt der E-Mail kopieren und einfügen

Die meisten E-Mail-Programme erlauben kein direktes HTML-Importieren.
Deshalb macht man es so:

1. Öffne die HTML-Datei im Browser.
2. Drücke

    * **Cmd+A** (Mac) oder **Ctrl+A** (Windows/Linux) → alles markieren
3. Drücke

    * **Cmd+C** (Mac) oder **Ctrl+C** (Windows/Linux) → kopieren
4. Öffne dein E-Mail-Programm (Gmail, Outlook, Apple Mail usw.)
5. Erstelle eine neue E-Mail.
6. Drücke **Cmd+V** / **Ctrl+V** → einfügen

Jetzt sollte die komplette formattierte E-Mail im Editor erscheinen.

---

# 🔁 5. (Optional) Datei wieder verschlüsseln

Wenn du etwas in der HTML-Datei geändert hast und sie wieder verschlüsseln möchtest:

```sh
openssl aes-256-cbc -salt -pbkdf2 \
  -in email/20251120_template.html \
  -out email/20251120_template.html.enc
```

Wichtig:

* In das Repository darf **nur** die `.enc`-Datei hochgeladen werden
* Die entschlüsselte `.html` niemals committen

---

# ✅ Fertig!