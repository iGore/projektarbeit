---
name: akademisches-schreiben
description: >
  Use this skill when writing, reviewing or improving a German academic CS paper
  (Projektarbeit, Bachelorarbeit). It captures concrete writing principles
  derived from iterative quality reviews of a real thesis. Load it before drafting
  new sections or running a quality pass on existing text.
---

# Akademisches Schreiben — Qualitätsleitfaden

## Zweck

Dieser Skill enthält destillierte Schreibprinzipien aus der iterativen Überarbeitung
einer deutschen Informatik-Projektarbeit. Er ersetzt kein inhaltliches Urteil,
gibt aber konkrete Anweisungen für häufige Schwachstellen.

---

## 1. Belegpflicht und Zitationsqualität

### Kernregel
Jede wichtige Behauptung braucht entweder eine Quelle oder eine logische Herleitung
aus bereits belegtem Text. „Bietet Vorteile", „ist effizienter", „ermöglicht" ohne
Quelle sind angreifbar.

### Quellenhierarchie
- **Peer-reviewed Papers / Konferenzbeiträge** → `\parencite{}` — bevorzugt
- **Technische Dokumentation / Blog (Fowler, Böckeler)** → `\parencite{}` akzeptabel wenn zitierbar
- **GitHub-Scripts / Sprachwebseiten (go.dev)** → `\footnote{\url{...}}` — nicht als Wissenschaftszitat
- **Newsletter / nicht-peer-reviewed Webquellen** → sparsam, klar als Praxisquelle markieren

### Häufige ungestützte Claims — immer belegen
- „reduziert die Kontextlast" → kontextuiere mit Context Engineering Literatur
- „bietet bessere Nachvollziehbarkeit" → ChatDev / SWE-agent Vergleich
- „ermöglicht Parallelisierung" → Planning Agents Survey
- Laufzeiteigenschaften von Programmiersprachen → spezifische Sprachdoku oder Benchmark

### Mehrfachzitation
Nur wenn beide Quellen denselben Sachverhalt aus unterschiedlichen Perspektiven
belegen. Keine mechanische Wiederholung desselben Keys ohne inhaltlichen Mehrwert.

---

## 2. Abgrenzung — Geplantes vs. Geleistetes

### Das wichtigste Prinzip
Der Leser muss jederzeit wissen: Wurde das bereits gemacht, oder ist es geplant?

### Modalformen für Entwurfsziele und Designintentionen
- ❌ „Die Spezifikation beschreibt das Verhalten vollständig"
- ✅ „Das Entwurfsziel ist, dass die Spezifikation das Verhalten vollständig beschreibt"
- ✅ „Ob dieses Ziel erreicht wird, ist eine der zentralen empirischen Fragen"

### Evaluationsergebnisse
- Tabellen mit „zu prüfen"-Spalten als **geplante Struktur** kennzeichnen, nicht als Ergebnis präsentieren
- Im Fazit „legt nahe" / „deutet darauf hin" statt „zeigt" / „beweist" wenn der Evaluationsschritt noch aussteht
- Phasen als ausgeführt beschreiben darf man, aber den I/O-Vergleich als ausstehend ausweisen

### Präsens in Konzeptionskapiteln
Kapitel 3 (Konzeption) darf Präsens nutzen — es beschreibt einen Entwurf.
Kapitel 4 (Implementierung / Durchführung) muss Vergangenheitsform nutzen
wenn es abgeschlossene Handlungen beschreibt.

---

## 3. Roter Faden

### Kapitelübergänge
Jedes Kapitel braucht:
1. **Eröffnungssatz**: „Dieses Kapitel beschreibt..." (1 Satz)
2. **Abschlusssatz**: Vorwärtslink auf das nächste Kapitel, z.B.
   „Wie diese Grundlagen in einer konkreten Pipeline-Konzeption operationalisiert werden, beschreibt Kapitel~\ref{konzeption}."

### Konzeption vs. Implementierung — strenge Arbeitsteilung
- **Konzeptionskapitel (K3)**: Was, Warum — keine Konfigurationsdetails
- **Implementierungskapitel (K4)**: Wie konkret — neue Details die K3 nicht hat
  (Parameter wie `steps: 10`, `temperature: 0.1`, konkrete Dateinamen)
- Überlapp auflösen durch: K4 beginnt mit Brückensatz der explizit sagt
  „K3 = Was/Warum, dieses Kapitel = Wie"

### Querverweise
- Abschnitte die anderswo ausgeführt werden: `(vgl. Abschnitt~\ref{...})`
- Abbildungen im Fließtext ankern: mindestens einmal `(vgl. Abbildung~\ref{fig:...})`
- Neue Konzepte die später verwendet werden: beim ersten Auftreten erklären

---

## 4. Terminologiekonsistenz

### Einführungspflicht
Jeden Fachbegriff, jede Abkürzung, jeden Dateinamen **beim ersten Vorkommen** erklären.
Beispiel: Wenn `SPEC.md` ab Kapitel 3 als selbstverständlich gilt, muss es dort
beim ersten Auftreten eingeführt werden: „...überführt; das Ergebnis wird als
`SPEC.md` festgehalten, dem kanonischen Spezifikationsartefakt im Markdown-Format."

### Synonymvermeidung
Einmal gewählter Begriff bleibt. Häufige Probleme:
- **PoC vs. Prototyp**: Einen Begriff wählen, explizit gleichsetzen
- **SPEC.md vs. Spezifikationsartefakt vs. textuelle Spezifikation**: alle drei sind ok
  als Variation, aber `SPEC.md` muss zuerst eingeführt sein
- **Phase 1 / Rekonstruktion**: beide parallel ok wenn konsistent verwendet

### Em-Dashes vermeiden
Em-Dashes (—) sind im deutschen akademischen Stil unüblich.
Alternativen je nach Kontext:
- Einschub → Komma oder Klammern: `(Agentenprofile, Skills, AGENTS.md und MCPs)`
- Erläuterung → Doppelpunkt: `umgesetzt wurden: mit welchem Werkzeug`
- Kontrast → Semikolon: `er koordiniert nichts; er berichtet nur`
- Apposition → Komma: `ergänzt um den Verifier als unabhängige Prüfinstanz,`

---

## 5. Zitationsformat

### parencite vs. textcite
- `\parencite{key}` → parenthetisch am Satzende: „...erhöhen (Midolo et al., 2026)."
- `\textcite{key}` → integriert im Satz: „Midolo et al. (2026) zeigen, dass..."
  Nur wenn der Autor selbst Subjekt des Satzes ist.

### Fußnoten für schwache Quellen
```latex
\footnote{\url{https://github.com/...}}
```
GitHub-Links, Sprachwebseiten und ähnliche Quellen als Fußnote,
nicht als `\parencite{}` im Literaturverzeichnis.

---

## 6. Häufige Fallen

| Muster | Problem | Lösung |
|---|---|---|
| „Die Arbeit zeigt, dass X" | Überschreitet bewiesenen Nachweis | „Die Arbeit legt nahe, dass X" |
| „stellt sicher, dass Y" (Designaussage) | Präsens für ungepüfte Designannahme | „soll sicherstellen, dass Y" |
| Tabelle mit „zu prüfen" als Ergebnis präsentiert | Methodisch irreführend | Als „geplante Struktur" kennzeichnen |
| Term aus Kap. 4 der in Kap. 3 verwendet wird ohne Einführung | Terminologielücke | Bei Ersterwähnung in K3 einführen |
| K3 und K4 beschreiben dasselbe ohne neuen Inhalt | Redundanz, schwacher roter Faden | K4 muss echte Implementierungsdetails liefern |
| Rückverfolgbare Behauptung ohne Quelle | Akademisch angreifbar | Quelle nachrecherchieren oder Satz umformulieren |

---

## 7. Bewertungskriterien (Selbst-Check)

Vor dem Abgeben gegen diese sechs Kriterien prüfen:

1. **Argumentation & Belegpflicht**: Jede Kernaussage belegt oder hergeleitet?
2. **Zitierweise**: Paraphrasiert statt direkt zitiert? Mehrfachbelege sinnvoll?
3. **Roter Faden**: Jedes Kapitel mit Einleitungs- und Übergangssatz?
4. **Abgrenzung**: Klar zwischen Geleisteten und Geplantem getrennt?
5. **Terminologiekonsistenz**: Neue Begriffe eingeführt, keine Synonymvariation?
6. **Querverweise**: Abbildungen im Text verankert, Kapitelverweise gesetzt?
