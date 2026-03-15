# Entwicklung eines Multi-Agenten-Systems zum KI-gestützten Software-Re-Engineering
## Ein Ansatz zur automatisierten Code-Migration mittels Spec-Driven Development und Agentic Workflow Orchestration

### 1. Ausgangslage und Motivation
Die Modernisierung von Legacy-Codebasen stellt eine der zentralen Herausforderungen der zeitgenössischen Softwareentwicklung dar. Im Lebenszyklus gewachsener Systeme entstehen technologisch bedingte Grenzen hinsichtlich Performance, Wartbarkeit und Skalierbarkeit, sodass ein Wechsel auf moderne Sprachen und Architekturen erhebliche Vorteile verspricht. Dazu zählen insbesondere verbesserte Typsicherheit, höhere Ressourceneffizienz und nativer Concurrency-Support. In der Praxis scheitert eine solche Migration jedoch häufig an der hohen kognitiven Last für Entwickler, einer lückenhaften Dokumentation des Bestands sowie an fundamentalen Paradigmenwechseln zwischen Quell- und Zieltechnologie.

Vor diesem Hintergrund wird die Arbeit als Beitrag zum KI-gestützten Software-Re-Engineering verstanden. Der etablierte Begriff des Re-Engineering bildet den fachlichen Rahmen, während der Einsatz spezialisierter Agenten und textueller Spezifikationen eine neue Automatisierungsstufe für Analyse, Rekonstruktion und Umsetzung verspricht.

### 2. Problemstellung
Bestehende Migrationsansätze, die primär auf direkter Transpilierung basieren, versagen häufig bei der Übertragung architektonischer Intentionen und produzieren infolgedessen schwer wartbaren Zielcode. Zwar bietet Spec-Driven Development (SDD) eine theoretische Abstraktionsebene, monolithische Large Language Models (LLMs) stoßen bei umfangreichen Codebasen jedoch schnell an Kontext-Limits. Hinzu kommt die Tendenz zu Halluzinationen, wodurch die Korrektheit generierter Artefakte gefährdet wird.

Es fehlt somit an einer orchestrierten Toolchain, die semantisches Code-Verständnis, skalierbaren Zugriff auf Code-Kontext und eine kontrollierte Überführung in technische Spezifikationen in einem konsistenten Migrationsprozess vereint.

### 3. Zielsetzung der Projektarbeit
Das Ziel dieser Projektarbeit ist die Konzeption und prototypische Implementierung einer automatisierten Migrations-Pipeline auf Basis eines orchestrierten Multi-Agenten-Systems (MAS). Der Fokus liegt auf der methodischen Umsetzung des SDD-Ansatzes sowie auf einer klaren Scope-Abgrenzung, damit aus der Projektarbeit kein unkontrolliert wachsender Gesamtansatz entsteht. Daher wird ein prototypischer Proof of Concept für ein repräsentatives Quell-Modul angestrebt, an dem der grundlegende Durchstich durch Analyse, Spezifikation, Verifikation und Generierung nachvollziehbar demonstriert werden kann.

Das System soll aus bestehendem Quellcode präzise technische Spezifikationen in Markdown extrahieren und diese als verifizierte Grundlage für die Code-Generierung in der Zielsprache nutzen. Technisch wird hierfür das Model Context Protocol (MCP) eingesetzt, um den Agenten einen gezielten, bedarfsorientierten Zugriff auf Analyse-Tools und Code-Repräsentationen zu ermöglichen und so das Kontext-Management effizient zu gestalten.

### 4. Methodik
Die methodische Umsetzung adaptiert das Horseshoe-Modell für die KI-gestützte Migration, wobei die textuelle SDD-Spezifikation die zentrale Abstraktionsebene bildet. Der Prozess wird durch einen orchestrierten Schwarm spezialisierter Agenten realisiert, die über MCP auf einen Code Knowledge Graph zugreifen.

- Analyse-Rollen: Extraktion der Geschäftslogik und Struktur mittels statischer Analyse-Tools (z. B. Tree-sitter).
- Spec-Writer-Rollen: Generierung detaillierter technischer Spezifikationen (SDD).
- Verifier-Rollen: Validierung der Specs gegen den ursprünglichen Code-Kontext zur Vermeidung von Halluzinationen.
- Builder-Rollen: Implementierung in der Zielsprache auf Basis der finalisierten Spezifikation.

Durch die Entkopplung von Tooling und Agenten via MCP wird sichergestellt, dass Informationen just-in-time abgefragt werden, was die Analyse umfangreicher Codebasen innerhalb begrenzter Kontext-Fenster ermöglicht.

### 5. Evaluation und Ausblick auf die Bachelorarbeit
Die Validierung erfolgt am Beispiel eines repräsentativen Quell-Moduls. Im Mittelpunkt stehen funktionale Vollständigkeit im Sinne von Feature Parity, die Qualität der erzeugten Artefakte, die Nachvollziehbarkeit der Migrationsentscheidungen sowie die Kosteneffizienz des gewählten Vorgehens.

Ausblick auf die Bachelorarbeit: Darauf aufbauend soll das Framework wissenschaftlich erweitert werden. Ein zentraler Aspekt wird die Transformation zum hybriden Ansatz sein, bei dem textuelle Specs um visuelle Modelle (MDD) ergänzt werden, um strukturelle Abhängigkeiten noch präziser zu erfassen. Zudem sollen Forschungsfragen zur Skalierung des Wissenszugriffs mittels MCP in Großprojekten sowie zur automatisierten Bewertung der idiomatischen Code-Qualität ("Idiomatic Score") adressiert werden.
