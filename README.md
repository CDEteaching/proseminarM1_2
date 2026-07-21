# KI-Begleitgespräch zur Themendisposition
### Proseminar «Einführung in wissenschaftliches Arbeiten für eine Nachhaltige Entwicklung»
Centre for Development and Environment (CDE), Universität Bern

---

Dieses Tool unterstützt Studierende dabei, eigenständig eine wissenschaftliche Fragestellung für ihre Themendisposition zu entwickeln. Es simuliert ein Gespräch mit einer/einem anspruchsvollen Hochschullehrenden, die/der kritische Fragen stellt – ohne fertige Antworten zu liefern.

Das Tool kennt:
- alle **Seminar-Themen und Schlüsseltexte** des jeweiligen Semesters
- die **Inhalte des Begleitskripts** zum Online-Lernmodul (Kriterien für Forschungsfragen, Themenpyramide, SPSS-Methode, Gütekriterien, Bezug zu NE usw.)

Das Ziel ist nicht, den Studierenden die Arbeit abzunehmen, sondern sie durch gezielte Fragen dazu zu bringen, selbst zu denken, zu argumentieren und ihre Fragestellung schrittweise zu schärfen. 

---

## Für Studierende

**So nutzen Sie das Tool:**

1. Öffnen Sie den Link, den Ihre Betreuungsperson geteilt hat
2. Lesen Sie Ihren Schlüsseltext, bevor Sie beginnen
3. Beantworten Sie die Fragen der KI in Ihren eigenen Worten
4. Die KI wird Ihre Antworten hinterfragen – das ist so gewollt
5. Bringen Sie immer zuerst Ihren eigenen Vorschlag ein, bevor Sie nach Feedback fragen

**Was das Tool nicht tut:**
- Es liefert Ihnen keine fertige Fragestellung
- Es stimmt Ihnen nicht einfach zu
- Es macht Ihnen die Arbeit nicht ab

**Die sieben Bereiche des Gesprächs:**

| # | Bereich | Was wird geklärt? |
|---|---|---|
| 1 | Themengebiet | Worum geht es im Schlüsseltext? Was ist die Relevanz? |
| 2 | Begriffsklärung | Sind die zentralen Begriffe klar definiert? |
| 3 | Problemstellung | Welches Problem wird untersucht? Welche Erklärungsansätze gibt es? |
| 4 | Bezug NE | Wie hängt das Thema mit Nachhaltiger Entwicklung zusammen? |
| 5 | Fragestellung | Wie lautet die präzise, überprüfbare Forschungsfrage? |
| 6 | Eingrenzung | Was ist Teil der Arbeit – und was nicht? |
| 7 | Forschungsstand | Welche Literatur und Theorien sind relevant? |

**Kriterien einer guten wissenschaftlichen Fragestellung** (aus dem Begleitskript):
- **Präzise und spezifisch** – klar und eindeutig formuliert, auch für Dritte erkennbar
- **Operationalisierbar** – empirisch oder analytisch beantwortbar; genügend Literatur vorhanden
- **Originalität** – schafft einen wissenschaftlichen Mehrwert (neue Perspektive, Zielgruppe, Verknüpfung)
- **W-Fragen bevorzugen** – Was, Wie, Warum, Welche, Inwiefern; offen formuliert ohne Vorannahmen
- **Eingrenzung** – zeitlich, räumlich, nach Personengruppen oder Disziplinen
- **Bezug zu NE** – Bezug zu den drei Dimensionen (Umwelt, Gesellschaft, Wirtschaft) und/oder SDGs
- **Herleitung** – ergibt sich logisch aus dem Schlüsseltext und einer Forschungslücke

---

## Für Lehrpersonen

### Pädagogische Idee

Das Tool basiert auf dem Prinzip des **problemorientierten Lernens** und ergänzt die bestehende Seminarstruktur. Es soll die Studierenden zwischen den Präsenzsitzungen beim eigenständigen Denken begleiten – ähnlich wie ein Gespräch in der Sprechstunde, aber jederzeit verfügbar.

Die KI übernimmt die Rolle einer/eines kritischen Hochschullehrenden und:
- prüft Kohärenz zwischen den Antworten
- akzeptiert vage Antworten nicht, sondern fragt nach
- verweist bei Bedarf gezielt auf Inhalte des Begleitskripts (Themenpyramide, SPSS-Methode, W-Fragen, Gütekriterien)
- schlägt keine fertige Fragestellung vor, solange Studierende keinen eigenen Entwurf eingebracht haben
- kennt alle Seminar-Themen und Schlüsseltexte des laufenden Semesters

### Einbettung im Seminar

Das Tool eignet sich besonders **zwischen diesen Seminarphasen**:
- Nach der Einführung in den Schlüsseltext 
- Vor dem «Meet the Expert»-Termin
- Zur Vorbereitung des Research Pitch

## Ressourcen pflegen: der `data/`-Ordner
 
Alle inhaltlichen Ressourcen liegen im Ordner `data/`. Die `index.html` muss **nie** verändert werden.
 
```
proseminarM1_2/
├── index.html           ← nie anfassen
└── data/
    ├── literatur.json   ← jedes Semester aktualisieren
    └── skript.json      ← bei inhaltlicher Überarbeitung des Lernmoduls aktualisieren
```
 
---
 
### `literatur.json` – Semesterthemen und Schlüsseltexte
 
Diese Datei enthält alle Themen, Expert*innen und Schlüsseltexte des laufenden Semesters. Sie wird **jedes Semester** aktualisiert.
 
**So bearbeiten:**
1. Datei `data/literatur.json` im Repository öffnen
2. Stift-Icon (Edit) klicken
3. `"semester"`, `"thema"`, `"experte"` und `"literatur"` anpassen
4. *Commit changes* klicken
**Format:**
```json
{
  "semester": "Herbstsemester 2026",
  "themen": [
    {
      "thema": "Titel des Themas",
      "experte": "Name der Expert*in",
      "literatur": [
        "Vollständige Literaturangabe inkl. DOI"
      ]
    }
  ]
}
```
 
---
 
### `skript.json` – Inhalte des Begleitskripts
 
Diese Datei enthält die für das Gespräch relevanten Kerninhalte des Online-Lernmoduls: Kriterien für Forschungsfragen, Themenpyramide, SPSS-Methode, Gütekriterien, Bezug zu NE, Ziele von Forschungsfragen und den Rahmen des Proseminars.
 
Sie muss nur aktualisiert werden, wenn das **Begleitskript inhaltlich überarbeitet** wird.
 
**Format:**
```json
{
  "quelle": "Quellenangabe des Skripts",
  "inhalt": "Freitext mit den relevanten Inhalten..."
}
```
 
---
 
## Technischer Aufbau
 
```
Studierende (Browser)
    │
    ▼
GitHub Pages (index.html)
    │  lädt beim Start parallel:
    │  ├── data/literatur.json
    │  └── data/skript.json
    │
    ▼
Cloudflare Worker (Proxy, versteckt den API-Key)
    │
    ▼
Anthropic API (Claude claude-sonnet-4-5)
```
 
Der API-Key ist serverseitig im Cloudflare Worker hinterlegt – für Studierende nicht sichtbar. Die Kosten pro Gespräch betragen erfahrungsgemäss wenige Rappen.
 
### Verhalten der KI anpassen
 
Das Gesprächsverhalten (Rolle, Ton, Schlüsselbereiche) ist in der Funktion `buildSystemPrompt()` in der `index.html` definiert. Dort können bei Bedarf Anpassungen vorgenommen werden – ohne dass `literatur.json` oder `skript.json` betroffen sind.
 
---
 
## Datenschutz
 
- Es werden keine Gesprächsdaten gespeichert
- Jede Sitzung beginnt ohne Gedächtnis an frühere Gespräche
- Der API-Key ist nur im Cloudflare Worker hinterlegt und nie im Browser sichtbar
---
 
*Entwickelt für das Proseminar Nachhaltige Entwicklung, Modul 1 – Centre for Development and Environment (CDE), Universität Bern, Herbstsemester 2025*
