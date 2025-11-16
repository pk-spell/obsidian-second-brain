# Projekt: KI-Tooling für Coding & Dev-Workflow

## 1. Zielbild

Ich will KI-Tools so in meinen Dev-Workflow integrieren, dass:

- sie **direkt beim Coden** helfen (nicht nur Copy/Paste aus dem Browser),
- sie **meine App / mein Repo verstehen** (Codebase-Kontext, nicht nur einzelne Snippets),
- ich **komplexe Web- / App-Projekte** damit bauen kann, ohne dass das Kontextfenster sofort platzt,
- ich sowohl **Cloud-LLMs** (ChatGPT, Claude, etc.) als auch **lokale LLMs** (Ollama & Co.) sinnvoll nutze.

Langfristig soll das Setup:

- für **Terraform/SAP-on-Azure**,
- für **lokale Python-/Web-Tools**,
- und für **Experimente mit lokalen LLMs auf dem Mac**

stabil funktionieren.

---

## 2. Bisher getestete KI-Tools (high level)

### 2.1 Web-LLMs

- **Kimi K2**
  - **Einsatz**: primär Coding.
  - **Erfahrung**: gut im Coding, aber:
    - Kontextfenster relativ schnell voll.
    - Für größere Apps / komplexere Projekte dadurch unpraktisch.
- **ChatGPT**
  - **Einsatz**: Coding, Erklärungen, Troubleshooting.
  - **Erfahrung**:
    - Kontextlimit bisher nicht praktisch erreicht.
    - Gut geeignet, um **größere Aufgaben / Apps** schrittweise zu bauen.
- **Google Jules**
  - **Einsatz**: Coding-Tests (Web-App / komplexere Aufgaben).
  - **Erfahrung**:
    - Einfache Aufgaben: ok.
    - Mehrere Versuche bei komplexeren Web-App-Aufgaben: gescheitert → Test abgebrochen nach 3–4 Versuchen.
- **Gemini**
  - Noch **nicht** getestet.
- Cloude
	- noch nicht getestet

### 2.2 Lokale / hybride LLM-Stacks

- **Ollama**
  - Bereits genutzt.
  - Eindruck: „soweit ganz gut“, Lokales LLM-Setup funktioniert.
- **Microsoft Foundry**
  - Getestet.
  - Problem: für mich **zu wenige LLMs** offiziell supported.
- **Lokales Training auf dem Mac**
  - Verschiedene Möglichkeiten recherchiert.
  - Erste Tests / Skripte vorhanden, aber noch **nicht abgeschlossen**.
- **Tool zum lokalen Start/Stop von LLMs (vermutlich „OpenLLM“ o. ä.)**
  - Noch **nicht** getestet.
  - Ziel: LLMs komfortabel lokal via App/GUI oder CLI starten/stoppen.

### 2.3 KI-Browser

- **Atlas** – geplant zu testen.
- **Perplexity** – geplant zu testen.

Ziel: rausfinden, ob sie **Recherche + Coding-Kontext** besser kombinieren als normale Web-Suche + LLM.

### 2.4 IDE / Editor & KI

- **VS Code**
  - Aktueller Standard-Editor.
  - Typischer Workflow bisher:
    - Code von LLM-Webapps generieren lassen.
    - Manuell nach VS Code kopieren.
- **Cursor**
  - Geplant zu testen.
  - Erwartung:
    - LLM integriert direkt im Editor.
    - Versteht das Repo / Projektkontext.
    - Kann Code direkt im Editor generieren/ändern.
- Weitere IDEs: noch offen.

### 2.5 CLI-Tools (KI-Assistenten in der Konsole)

- Geplanter Test von:
  - **Claude Code CLI**
  - weiteren CLI-Tools nach Liste (Link noch einfügen).
- Link mit zu testenden Tools:
  - `[Link zu Artikel/Repo hier einfügen]`

---

## 3. Offene Fragen / ToDos

- Welches Setup ist für mich **dauerhaft** sinnvoll?
  - Browser-LLM + Copy/Paste?
  - Editor-Integration (Cursor / VSCode-Plugin)?
  - Kombination aus lokalem LLM (Ollama) + Cloud-LLM?
- Wie skaliert das für **größere Projekte** (z. B. Flask-Webapp, Terraform-Agent, SAP-Automation)?

---

## 4. Nächste Schritte (Experiment-Backlog)

Siehe auch: `[[KI-Tools-Status]]` und `[[Template - KI-Experiment]]`.

Kurzliste:

- [ ] **Claude** im Browser testen (Coding-Fähigkeiten, Kontext im Vergleich zu ChatGPT/Kimi).
- [ ] **Claude Code CLI** ausprobieren (lokale Files, Refactoring, Tests).
- [ ] **Cursor** installieren und Testprojekt durchführen:
  - [ ] Kleines Web-App-Projekt mit LLM-Unterstützung durchspielen.
- [ ] **Perplexity** & **Atlas** als KI-Browser vergleichen:
  - [ ] Typische Recherche: SAP-on-Azure-Topic + Terraform-Beispiele + Fehlermeldung.
- [ ] **Gemini** testen (Fokus: Coding + Web-App-Komplexität).
- [ ] Lokale LLM-Trainings-Pipeline auf dem Mac weiterführen (bisherige Scripts dokumentieren).
- [ ] „OpenLLM“ oder vergleichbares Tool testen (lokale LLMs starten/stoppen).
