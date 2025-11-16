# Knowledge-DB – Setup, Git-Workflow & Skript

  

Dieses Dokument fasst zusammen:

  

1. Wie der Obsidian-Vault **knowledge-db** auf Windows eingerichtet wurde.

2. Wie du denselben Stand auf **macOS** nutzen kannst.

3. Wie dein **Git-Workflow** aussieht.

4. Wie du ein PowerShell-Skript `git-sync.ps1` verwenden kannst, um `pull + add + commit + push` in einem Schritt auszuführen.

  

---

  

## 1. Setup auf Windows

  

### 1.1 Obsidian-Vault anlegen

  

1. Ordner erstellt:

   - `C:\knowledge-db`

2. Obsidian gestartet.

3. In Obsidian: **"Open folder as vault"** gewählt und `C:\knowledge-db` als Vault geöffnet.

  

Damit ist `C:\knowledge-db` der Obsidian-Vault.

  

---

  

### 1.2 Git-Repository initialisieren

  

Im PowerShell-Terminal:

  

```powershell

cd C:\knowledge-db

  

# Git-Repo initialisieren

git init

  

# Falls noch nicht vorhanden: .gitignore anlegen (siehe unten)

  

# Dateien zum ersten Commit hinzufügen

git add .

  

# Erster Commit

git commit -m "Initial Obsidian vault"

```

  

Eine einfache `.gitignore`-Datei könnte z. B. so aussehen:

  

```gitignore

# OS

.DS_Store

Thumbs.db

  

# Obsidian Cache & Workspace

.obsidian/workspace.json

.obsidian/workspace-mobile.json

.obsidian/cache/

  

# Optional: mobile-only Zeug

.obsidian/plugins/obsidian-mobile/

```

  

---

  

### 1.3 Remote-Repo auf GitHub verknüpfen

  

Auf GitHub wurde ein privates Repo erstellt, z. B.:

  

- `https://github.com/pk-spell/obsidian-second-brain.git`

  

Dann in PowerShell:

  

```powershell

cd C:\knowledge-db

  

# Remote hinzufügen

git remote add origin https://github.com/pk-spell/obsidian-second-brain.git

  

# Branch von master -> main umbenennen

git branch -M main

  

# Erster Push

git push -u origin main

```

  

Ab jetzt ist `C:\knowledge-db` mit dem GitHub-Repo verbunden.

  

---

  

## 2. Setup auf macOS

  

Ziel: Den gleichen Inhalt wie auf Windows auf dem Mac nutzen.

  

### 2.1 Voraussetzungen

  

- Git installiert (Xcode Command Line Tools oder Homebrew):

  - `xcode-select --install`  

  - oder `brew install git`

- Obsidian installiert.

  

---

  

### 2.2 Repo klonen

  

1. Zielordner anlegen, z. B.:

  

```bash

mkdir -p ~/knowledge-db

cd ~/knowledge-db

```

  

2. Repo klonen:

  

```bash

git clone https://github.com/pk-spell/obsidian-second-brain.git .

```

  

Wichtig: Das `.` am Ende sorgt dafür, dass direkt in `~/knowledge-db` geklont wird und nicht ein Unterordner angelegt wird.

  

Danach liegt der Vault auf dem Mac in:

  

- `~/knowledge-db`

  

---

  

### 2.3 Vault in Obsidian öffnen (macOS)

  

1. Obsidian starten.

2. **"Open folder as vault"** auswählen.

3. Ordner `~/knowledge-db` auswählen.

  

Jetzt nutzen Windows und macOS denselben Obsidian-Inhalt über Git.

  

---

  

## 3. Git-Workflow für knowledge-db

  

Dieses Kapitel beschreibt, wie du Git für den Obsidian-Vault **knowledge-db** verwendest.

  

### 3.1 Status prüfen

  

```powershell

git status

```

  

Zeigt an, welche Dateien geändert, neu oder gelöscht sind.

  

---

  

### 3.2 Änderungen vom Remote holen (pull)

  

Bevor du anfängst zu arbeiten:

  

```powershell

git pull

```

  

Damit stellst du sicher, dass dein lokaler Stand aktuell ist.

  

---

  

### 3.3 Änderungen zum Commit vormerken (add)

  

Alle Änderungen im Repo vormerken:

  

```powershell

git add .

```

  

Punkt `.` = alle geänderten/neu erstellten Dateien im aktuellen Ordner.

  

---

  

### 3.4 Commit erstellen

  

```powershell

git commit -m "Kurzbeschreibung der Änderung"

```

  

Beispiele für Messages:

  

- `"Add notes for SAP backup config"`

- `"Update LLM experiments readme"`

- `"Fix typo in Terraform naming notes"`

  

---

  

### 3.5 Änderungen hochladen (push)

  

```powershell

git push

```

  

Damit landen deine Commits im Remote-Repo (z. B. GitHub).

  

---

  

### 3.6 Typischer Ablauf (manuell)

  

1. **Vor dem Arbeiten**:

  

   ```powershell

   git pull

   ```

  

2. In Obsidian arbeiten / neue Notes erstellen / bestehende anpassen.

  

3. **Nach dem Arbeiten**:

  

   ```powershell

   git status

   git add .

   git commit -m "Beschreibung deiner Änderungen"

   git push

   ```

  

---

  

## 4. PowerShell-Skript `git-sync.ps1` (Windows)

  

Um den Ablauf zu vereinfachen, kannst du ein Skript nutzen, das:

  

1. `git pull` ausführt,

2. alle Änderungen staged (`git add .`),

3. nur dann commitet, wenn es wirklich Änderungen gibt,

4. anschließend `git push` aufruft.

  

### 4.1 Skript erstellen

  

Datei im Repo-Root anlegen:

  

- Pfad: `C:\knowledge-db\git-sync.ps1`

  

Inhalt:

  

```powershell

param(

    [Parameter(Mandatory = $true)]

    [string]$Message

)

  

Write-Host "[i] Git Sync gestartet..."

  

# Sicherstellen, dass wir im Repo sind

if (-not (Test-Path ".git")) {

    Write-Host "[!] Dieser Ordner scheint kein Git-Repository zu sein (.git fehlt)." -ForegroundColor Red

    exit 1

}

  

# 1) Aktuellen Stand vom Remote holen

Write-Host "[i] git pull..."

git pull

if ($LASTEXITCODE -ne 0) {

    Write-Host "[!] git pull ist fehlgeschlagen. Abbruch." -ForegroundColor Red

    exit $LASTEXITCODE

}

  

# 2) Änderungen zum Commit vormerken

Write-Host "[i] git add ."

git add .

if ($LASTEXITCODE -ne 0) {

    Write-Host "[!] git add ist fehlgeschlagen. Abbruch." -ForegroundColor Red

    exit $LASTEXITCODE

}

  

# 3) Prüfen, ob es überhaupt Änderungen gibt

git diff --cached --quiet

$noChanges = ($LASTEXITCODE -eq 0)

  

if ($noChanges) {

    Write-Host "[i] Keine Änderungen zum Commit. Es wird nichts committed oder gepusht."

    exit 0

}

  

# 4) Commit mit übergebener Message

Write-Host "[i] git commit -m `"$Message`""

git commit -m "$Message"

if ($LASTEXITCODE -ne 0) {

    Write-Host "[!] git commit ist fehlgeschlagen. Abbruch." -ForegroundColor Red

    exit $LASTEXITCODE

}

  

# 5) Push zum Remote

Write-Host "[i] git push..."

git push

if ($LASTEXITCODE -ne 0) {

    Write-Host "[!] git push ist fehlgeschlagen." -ForegroundColor Red

    exit $LASTEXITCODE

}

  

Write-Host "[✓] Git Sync erfolgreich abgeschlossen." -ForegroundColor Green

```

  

---

  

### 4.2 Skript verwenden

  

In PowerShell:

  

```powershell

cd C:\knowledge-db

  

# Beispielaufruf:

.\git-sync.ps1 "Update notes for SAP backup and LLM tests"

```

  

Das Skript:

  

- erwartet eine Commit-Message als ersten Parameter,

- bricht ab, wenn keine Message angegeben ist,

- führt `pull`, `add`, `commit` (falls nötig) und `push` aus.

  

---

  

## 5. Empfohlene einfache Ordnerstruktur im Vault

  

Für den Start kann eine einfache Struktur helfen:

  

```text

01_Inbox/

02_Projects/

03_Systems/

04_Knowledge/

99_Archive/

```

  

- `01_Inbox` – schnelle Notizen, die du später einordnest.

- `02_Projects` – z. B. „SAP-on-Azure-Blueprint“, „Terraform-Agent“, „LLM-Playground“.

- `03_Systems` – pro SAP-System / Workload Zone eine Seite.

- `04_Knowledge` – Howtos, Cheatsheets, LLM, Git, etc.

- `99_Archive` – alte Notes, die du nicht löschen möchtest.

  

Diese Struktur ist nur ein Vorschlag und kann jederzeit angepasst werden.