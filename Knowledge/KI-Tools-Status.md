# KI-Tools – Übersicht & Status

Kurzer Überblick über alle relevanten KI-Tools, die ich nutze, getestet habe oder testen will.

---

## 1. Web-LLMs

| Tool       | Kategorie     | Status           | Haupt-Usecase      | Erfahrung / Notizen                                                    |
|-----------|---------------|------------------|--------------------|------------------------------------------------------------------------|
| Kimi K2   | Web-LLM       | **Getestet**     | Coding             | Gut im Coding, aber Kontextfenster schnell voll → schlecht für größere Apps. |
| ChatGPT   | Web-LLM       | **Im Einsatz**   | Coding, Erklärungen, Architekturen | Kontextlimit praktisch noch nicht gespürt, gut für komplexere Projekte.     |
| Claude    | Web-LLM       | **Geplant**      | Coding, CLI/Code Assist | Noch nicht getestet. Fokus auf Codequalität & Kontextgröße.              |
| Jules     | Google (KI)   | **Getestet**     | Coding             | Einfache Aufgaben ok, komplexere Web-App-Aufgaben mehrfach gescheitert → Test abgebrochen. |
| Gemini    | Web-LLM       | **Geplant**      | Coding, evtl. Multimodal | Noch nicht ausprobiert.                                                |

---

## 2. Lokale / Plattform-LLMs

| Tool / Stack      | Typ              | Status         | Plattform | Erfahrung / Notizen                                        |
|-------------------|------------------|----------------|-----------|------------------------------------------------------------|
| Ollama            | Lokaler LLM-Host | **Im Einsatz** | macOS     | Soweit gut, geeignet für lokale Experimente.               |
| MS Foundry        | Plattform        | **Getestet**   | Azure     | Zu wenig unterstützte LLMs für meinen Bedarf.             |
| „OpenLLM“ (?)     | Lokaler Manager  | **Geplant**    | macOS/Win | Tool zum Start/Stop von LLMs lokal testen.                |
| Lokales Training  | Pipeline         | **In Arbeit**  | macOS     | Möglichkeiten recherchiert, erste Tests, aber noch nicht fertig. |

---

## 3. KI-Browser

| Tool       | Typ        | Status      | Usecase                  | Notizen                                   |
|------------|------------|------------|--------------------------|-------------------------------------------|
| Perplexity | KI-Browser | **Geplant**| Recherche + Code-Kontext | Noch nicht getestet.                      |
| Atlas      | KI-Browser | **Geplant**| Recherche, Wissensaufbau | Noch nicht getestet.                      |

---

## 4. IDEs & Editor-Integrationen

| Tool      | Typ                  | Status        | Usecase                            | Notizen                                               |
|-----------|----------------------|--------------|------------------------------------|-------------------------------------------------------|
| VS Code   | Editor               | **Im Einsatz**| Standard-Dev, Copy/Paste aus LLM  | Bisher primär Code in Web-LLM, dann rüberkopieren.    |
| Cursor    | Editor mit LLM-Integration | **Geplant**   | LLM direkt im Editor, versteht Repo | Erwartung: versteht App-Struktur und Codebase.        |

---

## 5. CLI-Tools (Code / KI-Assistenten)

| Tool                 | Typ        | Status      | Usecase                         | Link / Notizen                       |
|----------------------|-----------|------------|---------------------------------|--------------------------------------|
| Claude Code CLI      | CLI-Tool  | **Geplant**| Lokale Files, Refactoring, Code | Link-Liste noch einfügen.           |
| Weitere CLI-Tools    | CLI-Tool  | **Geplant**| Vergleich & Best-of auswählen   | `[Link hier einfügen]`              |

---

## 6. Offene Punkte / Nächste Experimente

Siehe auch `[[Template - KI-Experiment]]` für strukturierte Test-Notizen.

- [ ] Claude im Browser testen (komplexe Coding-Tasks).
- [ ] Claude Code CLI: Test mit realem Projekt (z. B. Terraform-Repo oder Flask-App).
- [ ] Cursor: Setup + erstes Testprojekt.
- [ ] Perplexity vs. Atlas bei typischer SAP-on-Azure-/Terraform-Recherche.
- [ ] Gemini Test (Coding / Web-App-Architektur).
- [ ] OpenLLM-ähnliches Tool für lokalen LLM-Start testen.
- [ ] Lokale Trainingspipeline auf dem Mac dokumentieren und weiter ausbauen.
