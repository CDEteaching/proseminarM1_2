# KI-Begleitgespräch zur Themendisposition
### Proseminar «Einführung in wissenschaftliches Arbeiten für eine Nachhaltige Entwicklung»
Centre for Development and Environment (CDE), Universität Bern

---

Dieses Tool unterstützt Studierende dabei, eigenständig eine wissenschaftliche Fragestellung für ihre Themendisposition zu entwickeln. Es simuliert ein Gespräch mit einer/einem anspruchsvollen Hochschullehrenden, die/der kritische Fragen stellt – ohne fertige Antworten zu liefern.

Das Ziel ist nicht, den Studierenden die Arbeit abzunehmen, sondern sie durch gezielte Fragen dazu zu bringen, selbst zu denken, zu argumentieren und ihre Fragestellung schrittweise zu schärfen. Das Tool kennt alle Seminar-Themen und Schlüsseltexte des jeweiligen Semesters und kann gezielt darauf eingehen.

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

**Kriterien einer guten wissenschaftlichen Fragestellung:**
- **Präzision** – klar und eindeutig formuliert
- **Überprüfbarkeit** – empirisch oder analytisch beantwortbar
- **Relevanz** – Bezug zur Literatur und zu NE-Debatten
- **Eingrenzung** – sinnvoll begrenzt (zeitlich, räumlich, thematisch)
- **Herleitung** – ergibt sich logisch aus dem Schlüsseltext und der Problemstellung

---

## Für Lehrpersonen

### Pädagogische Idee

Das Tool basiert auf dem Prinzip des **problemorientierten Lernens** und ergänzt die bestehende Seminarstruktur. Es soll die Studierenden zwischen den Präsenzsitzungen beim eigenständigen Denken begleiten – ähnlich wie ein Gespräch in der Sprechstunde, aber jederzeit verfügbar.

Die KI übernimmt die Rolle einer/eines kritischen Hochschullehrenden, die/der:
- Kohärenz zwischen den Antworten prüft
- Vage Antworten nicht akzeptiert, sondern nachfragt
- Keine fertige Fragestellung vorschlägt, solange die Studierenden keinen eigenen Entwurf eingebracht haben
- Erst nach einem eigenen Vorschlag der Studierenden einen Verbesserungshinweis gibt
- Die Seminar-Themen und Schlüsseltexte kennt und gezielt darauf eingeht

### Einbettung im Seminar

Das Tool eignet sich besonders **zwischen diesen Seminarphasen**:
- Nach der Einführung in den Schlüsseltext 
- Vor dem «Meet the Expert»-Termin
- Zur Vorbereitung des Research Pitch

### Literaturliste jedes Semester aktualisieren

Die Seminar-Themen und Schlüsseltexte sind in einer separaten Datei gespeichert:

```
proseminarM1_2/
├── index.html          ← bleibt immer gleich, nie anfassen
└── data/
    └── literatur.json  ← wird jedes Semester aktualisiert
```

**So aktualisieren Sie die Literaturliste für ein neues Semester:**

1. Öffnen Sie `data/literatur.json` im Repository
2. Klicken Sie auf das Stift-Icon (Edit)
3. Passen Sie `"semester"`, `"thema"`, `"experte"` und `"literatur"` an
4. Klicken Sie auf *Commit changes*

Das Format der JSON-Datei:

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

Die `index.html` muss dabei **nicht** verändert werden.

### Technischer Aufbau

```
Studierende (Browser)
    │
    ▼
GitHub Pages (index.html)
    │  lädt beim Start: data/literatur.json
    │
    ▼
Cloudflare Worker (Proxy, versteckt den API-Key)
    │
    ▼
Anthropic API (Claude claude-sonnet-4-5)
```

Der API-Key ist serverseitig im Cloudflare Worker hinterlegt und für Studierende nicht sichtbar. Die Kosten pro Gespräch (ca. 15–20 Nachrichten) betragen erfahrungsgemäss wenige Rappen.

### Anpassungen am Gesprächsverhalten

Das Verhalten der KI (Rolle, Ton, Schlüsselbereiche) ist im `buildSystemPrompt()`-Abschnitt der `index.html` definiert. Dort können Sie bei Bedarf:
- Den Ton strenger oder wohlwollender gestalten
- Weitere Schlüsselbereiche hinzufügen
- Semesterspezifische Hinweise einbauen

---

## Datenschutz

- Es werden keine Gesprächsdaten gespeichert
- Jede Sitzung beginnt ohne Gedächtnis an frühere Gespräche
- Der API-Key ist nur im Cloudflare Worker hinterlegt und nie im Browser sichtbar

---

*Entwickelt für das Proseminar Nachhaltige Entwicklung, Modul 1 – Centre for Development and Environment (CDE), Universität Bern, Herbstsemester 2025*
