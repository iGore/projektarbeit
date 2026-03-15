# Mögliche CLI-Fallbeispiele für die Projektarbeit

Diese Datei sammelt geeignete CLI-Tools in TypeScript oder Python, die sich als Fallbeispiel für eine KI-gestützte Code-Migration mit Reverse Engineering, Spezifikation und Re-Implementierung nach Go oder Rust eignen könnten.

## Auswahlkriterien

- echte CLI mit klaren Ein- und Ausgaben
- überschaubarer Umfang für einen Proof of Concept
- vorhandene Tests oder gut nachvollziehbares Soll-Verhalten
- nicht nur Boilerplate, sondern erkennbare Kernlogik
- möglichst gute Trennung von Parsing, Verarbeitung und Ausgabe
- realistisch, aber nicht so groß, dass der PoC überfrachtet wird

## Empfohlene Hauptkandidaten

### 1. `tox-dev/pipdeptree` (`Python`)

- beste Gesamtwahl für die Projektarbeit
- klare CLI-Semantik: Python-Umgebung einlesen, Abhängigkeiten auflösen, Baum darstellen
- reale Fachlogik mit Traversierung, Filterung und mehreren Ausgabeformaten
- gute Tests und aktive Pflege
- sehr gut in Go oder Rust re-implementierbar

Eignung:
- Reverse Engineering: hoch
- Spezifikation: hoch
- Re-Implementierung in Go: hoch
- Re-Implementierung in Rust: hoch
- Risiko für den PoC: niedrig bis mittel

### 2. `Textualize/rich-cli` (`Python`)

- guter Kandidat mit sichtbarem CLI-Verhalten
- klare Optionen, nachvollziehbare Ausgabeformate und Rendering-Logik
- nützlich, wenn Bedienlogik und Terminal-Output stärker im Fokus stehen sollen
- etwas darstellungsorientierter als `pipdeptree`

Eignung:
- Reverse Engineering: mittel bis hoch
- Spezifikation: hoch
- Re-Implementierung in Go: mittel bis hoch
- Re-Implementierung in Rust: mittel bis hoch
- Risiko für den PoC: mittel

### 3. `mcollina/borp` (`JavaScript` / Node.js)

- sinnvoll, wenn ein Node-/TypeScript-nahes Entwicklerwerkzeug bevorzugt wird
- CLI mit Flags, Dateisuche, Testausführung und Coverage-Optionen
- geeignet für einen Devtool-orientierten Migrationsfall
- stärker an das Node-Ökosystem gebunden als die ersten beiden Kandidaten

Eignung:
- Reverse Engineering: mittel
- Spezifikation: mittel bis hoch
- Re-Implementierung in Go: mittel
- Re-Implementierung in Rust: mittel
- Risiko für den PoC: mittel

## Weitere sinnvolle Kandidaten

### `httpie/cli` (`Python`)

- fachlich stark und sehr realistisches CLI
- gute Tests und klare Produktlogik
- für einen PoC aber vermutlich zu groß
- eher Referenzprojekt als Hauptkandidat

### `azat-io/todoctor` (`TypeScript`-lastig, aber gemischtes Repo)

- inhaltlich spannend: Git-Historie, TODO-Analyse und Reporting
- als Migrationsfall aber weniger sauber, weil das Repository bereits mehrere Technologien kombiniert
- eher interessant als Vergleichsfall, nicht als erste Wahl

## Weniger geeignet

- sehr große CLIs wie `httpie/cli`, wenn der Umfang klein bleiben soll
- stark framework- oder plattformspezifische Tools, deren Kernlogik schwer vom Ökosystem zu trennen ist
- gemischte Repositories mit bereits mehreren Implementierungssprachen
- Toy-CLIs ohne echte fachliche Tiefe

## Vergleich

| Projekt | Sprache | Scope | Kernlogik | Tests | Go/Rust-Re-Implementierung | PoC-Risiko | Einschätzung |
|---|---|---|---|---|---|---|---|
| `tox-dev/pipdeptree` | Python | klein bis mittel | Dependency-Analyse, Traversierung, Ausgabeformate | gut | sehr gut | niedrig bis mittel | beste Gesamtwahl |
| `Textualize/rich-cli` | Python | mittel | CLI-Optionen, Rendering, Formatierung | gut | gut | mittel | gut, aber stärker UI-/Output-lastig |
| `mcollina/borp` | JavaScript / Node.js | klein bis mittel | Testsuche, Ausführung, Coverage, Reporter | gut | mittel | mittel | gut für Devtool-Fokus |
| `httpie/cli` | Python | groß | HTTP-Requests, Sessions, Auth, Ausgabe | sehr gut | gut | hoch | eher Referenz als PoC |
| `azat-io/todoctor` | gemischt, TS-lastig | mittel | Git-Historie, Kommentar-Analyse, Reporting | vorhanden | mittel | mittel bis hoch | interessant, aber als Fallbeispiel unruhig |

## Empfehlung

### Beste Wahl

1. `tox-dev/pipdeptree`
2. `Textualize/rich-cli`
3. `mcollina/borp`

### Empfohlene Entscheidung

- `pipdeptree`, wenn ein methodisch sauberer und gut beherrschbarer Kern im Mittelpunkt stehen soll
- `rich-cli`, wenn Bedienlogik und Ausgabeformate stärker interessieren
- `borp`, wenn bewusst ein Node-/TypeScript-nahes Entwicklerwerkzeug gewählt werden soll

## Vorläufiges Fazit

Für die aktuelle Projektarbeit ist `tox-dev/pipdeptree` der stärkste Kandidat. Das Tool ist realistisch, klar abgegrenzt, fachlich verständlich und gut geeignet, um Reverse Engineering, Spezifikation und Re-Implementierung in Go oder Rust nachvollziehbar zu demonstrieren.
