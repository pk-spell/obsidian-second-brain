# obsync – Schneller Git-Sync für den Obsidian-Vault

  

`obsync` ist ein PowerShell-Alias für das Skript `ObsidianSync.ps1`.  

Damit kann ich meinen Obsidian-Vault **knowledge-db** mit einem einzigen Befehl mit GitHub synchronisieren.

  

---

  

## 1. Alias-Konfiguration

  

Der Alias wird im PowerShell-Profil hinterlegt.

  

Pfad des Profils anzeigen:

  

```powershell

$PROFILE

```

  

Beispiel (kann abweichen):

  

```text

C:\Users\kusch\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1

```

  

### 1.1 Profil-Datei und Ordner anlegen (falls noch nicht vorhanden)

  

Falls `notepad $PROFILE` meldet, dass der Pfad nicht gefunden wird, zuerst Ordner und Datei erstellen:

  

```powershell

# Profil-Ordner anlegen

$profDir = Split-Path -Parent $PROFILE

New-Item -ItemType Directory -Path $profDir -Force

  

# Profil-Datei anlegen

New-Item -ItemType File -Path $PROFILE -Force

  

# Profil in Notepad öffnen

notepad $PROFILE

```

  

### 1.2 Alias im Profil eintragen

  

In die geöffnete Profildatei folgendes eintragen und speichern:

  

```powershell

Set-Alias obsync "C:\Users\kusch\UsefulScripts\ObsidianSync.ps1"

```

  

Neue PowerShell starten, damit das Profil geladen wird.

  

---

  

## 2. Skript-Verhalten (`ObsidianSync.ps1`)

  

Das Skript führt im Wesentlichen folgende Schritte aus:

  

1. Wechsel in den Vault-Ordner:

  

   ```powershell

   C:\knowledge-db

   ```

  

2. `git pull`

3. `git add .`

4. `git commit -m "<Message>"`

5. `git push`

  

Der Vault ist mit dem Remote-Repo verknüpft:

  

```text

https://github.com/pk-spell/obsidian-second-brain.git

```

  

---

  

## 3. Verwendung von `obsync`

  

In einer neuen PowerShell-Session:

  

```powershell

obsync "Kurze Beschreibung der Änderungen"

```

  

Beispiele:

  

```powershell

obsync "Add notes for SAP backup concept"

obsync "Update Terraform snippets for RSV setup"

obsync "Document Obsidian + Git workflow"

```

  

Damit erledige ich den kompletten Git-Sync in einem Schritt, ohne die Einzelbefehle (`git pull`, `git add`, `git commit`, `git push`) jedes Mal neu eintippen zu müssen.