# Top 5 Agentic Coding CLI Tools – Zusammenfassung für meinen Workflow

  

Quelle: *KDnuggets – “Top 5 Agentic Coding CLI Tools” (13.11.2025)*  

Link: https://www.kdnuggets.com/top-5-agentic-coding-cli-tools

  

Ziel dieser Notiz: Kurz festhalten, **welche CLI-Tools es gibt**, **wofür sie gut sind** und **wo sie in meinen Setup passen könnten** (ChatGPT, Claude, lokale LLMs, Ollama etc.).

  

---

  

## 1. Grundidee: Agentic Coding per CLI

  

Alle Tools im Artikel sind **agentische Coding-CLIs**:  

Du startest ein CLI, verbindest es mit einem oder mehreren LLMs, und das Tool kann dann z. B.:

  

- Code lesen und ändern

- Dateien erstellen / refactoren

- Tests schreiben / anpassen

- Shell-Kommandos ausführen (Build, Tests, Docker, etc.)

- Einen halb- oder vollautomatischen Coding-Flow fahren

  

Fast alle werden über `npm` global installiert und laufen im Terminal.

  

> Für mich interessant: Ich will eine Lösung, die **meine Codebase versteht** und direkt im Projekt arbeitet (nicht nur Copy/Paste aus dem Browser).

  

---

  

## 2. Claude Code

  

**Kategorie:** Agentic Coding CLI + VS Code Extension  

**Installation (Beispiel):**

  

```bash

npm install -g @anthropic-ai/claude-code

```

  

**Features laut Artikel:**

  

- Nutzt standardmäßig **Anthropic-Modelle (Claude)** über API-Key oder Subscription.

- Kann auf andere Provider / Modelle umgebogen werden (z. B. GLM 4.6, lokale Modelle).

- Gute Balance aus:

  - kurzen, präzisen Antworten,

  - niedriger Fehlerrate,

  - zuverlässigen Terminal-Kommandos.

- VS Code Extension ist dabei: direkt im Editor Fragen stellen, Code ändern lassen, Komponenten bauen.

  

**Einschätzung für mich:**

  

- Potenzieller **Haupt-KI-Assistent für Coding**.

- Passt zu meinem Ziel, Code direkt im Projekt/Editor bearbeiten zu lassen.

- Sehr interessant in Kombination mit Cursor oder VS Code (je nachdem, was ich am Ende nutze).

  

---

  

## 3. OpenCode

  

**Kategorie:** Open-Source-Alternative zu Claude Code  

**Installation:**

  

```bash

npm install -g opencode-ai@latest

```

  

**Features laut Artikel:**

  

- Voll **Open Source**, sehr flexibel.

- Kann quasi **jeden Modell-Provider** ansprechen (inkl. OpenRouter, diverse Cloud-LLMs und evtl. lokale Modelle).

- Eignet sich gut für:

  - Testen neuer Modelle,

  - Evaluieren von MCPs,

  - Bauen eigener Agenten / Workflows.

- Für Hardcore-Coder: extrem viel Feintuning möglich (Security, Design, Funktionen, Projekt-Setup).

  

**Einschätzung für mich:**

  

- Spannend, wenn ich meine **eigene Agenten-Logik** fahren will (z. B. Terraform-Agent, SAP-spezifische Checks).

- Gut für Experimente mit **verschiedenen LLMs** (lokal vs. Cloud, OpenRouter, etc.).

- Wahrscheinlich komplexer einzurichten, aber langfristig mächtig.

  

---

  

## 4. Droid (Factory AI)

  

**Kategorie:** Fokus auf Debugging & Automatisierung  

**Installation:**

  

```bash

curl -fsSL https://app.factory.ai/cli | sh

```

  

**Features laut Artikel:**

  

- Stark in **lokalen Problemen**:

  - Liest Docker-Logs,

  - schlägt Docker-Kommandos vor,

  - kann Probleme automatisch fixen.

- Sehr gut für **Debugging, Build-/Deploy-Probleme und Automatisierung**.

- Kostenloser Trial/Plan zum Start, Zugriff auf aktuelle Claude- & OpenAI-Modelle.

- Nachteil: schwach bei Custom-Models / externen Anbietern (stark auf eigenen Backend-Stack optimiert).

  

**Einschätzung für mich:**

  

- Könnte mein Tool für **„fix mal diesen Mist“** werden, wenn ein Container/Service spinnt.

- Interessant v. a. für Log-Analyse und schnelles Debugging in komplexeren Umgebungen (Docker, evtl. später K8s).

  

---

  

## 5. Codex CLI (OpenAI)

  

**Kategorie:** OpenAI / ChatGPT-basierte CLI  

**Installation:**

  

```bash

npm install -g @openai/codex

```

  

**Features laut Artikel:**

  

- Lässt sich direkt mit der **ChatGPT-Subscription** nutzen → macht das Abo deutlich wertvoller.

- Alternative: per OpenAI-Developer-API nutzen (falls kein Abo).

- Agentic Coding-Features:

  - Terminal- und Coding-Automatisierung,

  - VS Code / Cloud-Workflows.

- Kann auch auf andere Modelle (GLM, Minimax) umgestellt werden, aber:

  - Qualität leidet mit Fremd-APIs,

  - Tools/TAGs werden nicht immer sauber verstanden.

  

**Einschätzung für mich:**

  

- Da ich ChatGPT sowieso nutze, ist das quasi ein **No-Brainer zum Testen**.

- Sehr passend, um meinen bestehenden ChatGPT-Usecase (Browser) in CLI/Dev-Workflow zu ziehen.

- Gute Ergänzung zu meinem jetzigen Setup – besonders, wenn ich nicht direkt Claude als Haupttool nehme.

  

---

  

## 6. Gemini CLI (Google)

  

**Kategorie:** Google-Agentic-CLI (open-source)  

**Installation:**

  

```bash

npm install -g @google/gemini-cli

```

  

**Features laut Artikel:**

  

- Open-Source CLI, ähnlich wie Codex CLI / Copilot.

- Sehr anpassbar (MCP, Agents, Tools), aber in der Praxis:

  - Setup teilweise nervig,

  - MCPS / Agenten / externe Tools schwerer sauber zu konfigurieren.

- Vorsicht: Wenn aus Versehen **Gemini 2.5 Pro** genutzt wird, ist das Free-Tier mit einer Prompt quasi weg.

- Free Plan ist vorhanden und auto-renewed, aber:

  - Viel Friction, wenig Mehrwert laut Autor.

  

**Einschätzung für mich:**

  

- Eher „nice to test“, aber nicht als Haupttool.

- Könnte ich einmal durchspielen, um Gemini generell besser kennenzulernen.

- Für produktives Arbeiten eher nachrangig im Vergleich zu Claude Code / Codex CLI / OpenCode.

  

---

  

## 7. TL;DR des Artikels (für mich übersetzt)

  

Laut Autor (leicht umformuliert):

  

1. **Claude Code** → bestes Gesamtpaket, empfohlen als **Primär-Tool**.

2. **OpenCode** → top, wenn ich gerne an meinem Workflow schraube, eigene Agenten bauen will, viele Modelle testen möchte.

3. **Droid** → ideal für **Debugging, Logs, Builds, Automatisierung**.

4. **Codex CLI** → wird immer besser, ideal, wenn ich sowieso einen ChatGPT-Plan habe.

5. **Gemini CLI** → populär wegen Free-Tier, aber eher wenig Nutzen im Verhältnis zum Aufwand.

  

---

  

## 8. Konkreter Plan für meine Tests

  

### Phase 1 – „Quick Wins“

  

- [ ] **Codex CLI** installieren und mit meinem ChatGPT-Setup verbinden.

- [ ] **Claude Code** installieren und ein kleines Projekt testen (z. B. Flask-App oder Terraform-Modul).

- [ ] 1–2 reale Tasks damit durchführen (Fix für bestehendes Repo, neue kleine App).

  

### Phase 2 – „Tiefer einsteigen“

  

- [ ] **OpenCode** installieren und mit verschiedenen Modellen (Cloud + lokal) testen.

- [ ] **Droid** auf einer Umgebung testen, wo Docker/Container laufen (Debugging-Fokus).

- [ ] Entscheiden, welches Tool ich fest in meinen Workflow aufnehme.

  

### Phase 3 – „Nice to have“

  

- [ ] **Gemini CLI** einmal durchspielen (Install, 1–2 Tasks), um Gemini besser einzuordnen.

- [ ] Ergebnisse in `[[KI-Tools-Status]]` und `[[Template - KI-Experiment]]` pro Tool dokumentieren.