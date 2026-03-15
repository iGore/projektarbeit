# Entwicklung eines Multi-Agenten-Systems zur automatisierten Code-Migration
## Ein Ansatz mittels Spec-Driven Development und Agentic Workflow Orchestration

### 1. Ausgangslage und Motivation
Die Modernisierung von Legacy-Codebasen stellt eine der zentralen Herausforderungen der zeitgenössischen Softwareentwicklung dar. Etablierte Systeme stoßen im Lebenszyklus oft an technologisch bedingte Grenzen hinsichtlich ihrer Performance, Wartbarkeit oder Skalierbarkeit. Ein Wechsel auf moderne Sprachen und Architekturen verspricht hierbei signifikante Vorteile, insbesondere durch verbesserte Typsicherheit, Ressourceneffizienz und nativen Concurrency-Support. In der Praxis scheitert die Migration komplexer Systeme jedoch häufig an der hohen kognitiven Last für die Entwickler, einer unzureichenden Dokumentation des Bestands sowie den fundamentalen Paradigmenwechseln zwischen Quell- und Zieltechnologie.

### 2. Problemstellung
Bestehende Migrationsansätze, die primär auf direkter Transpilierung basieren, versagen oft bei der Übertragung architektonischer Intentionen und produzieren infolgedessen schwer wartbaren Code. Während das Spec-Driven-Development (SDD) eine theoretische Abstraktionsebene bietet, stoßen monolithische Large Language Models (LLMs) bei großflächigen Codebasen an ihre Kontext-Limits. Zudem stellt die Tendenz von LLMs zu Halluzinationen ein erhebliches Risiko für die Korrektheit der Migration dar. Es mangelt somit an einer orchestrierten Toolchain, die den Migrationsprozess durch ein strukturiertes, semantisches Code-Verständnis automatisiert und den Zugriff auf Code-Informationen so skaliert, dass Kontext-Limits (Token-Limits) gewahrt bleiben.

### 3. Zielsetzung der Projektarbeit
Das Ziel dieser Projektarbeit ist die Konzeption und prototypische Implementierung einer automatisierten Migrations-Pipeline auf Basis eines orchestrierten Multi-Agenten-Systems (MAS). Der Fokus liegt auf der methodischen Umsetzung des SDD-Ansatzes. Das System soll aus bestehendem Quellcode präzise technische Spezifikationen in Markdown extrahieren und diese als verifizierte Grundlage für die Code-Generierung in der Zielsprache nutzen. Technisch wird hierfür das Model Context Protocol (MCP) eingesetzt, um den Agenten einen gezielten, bedarfsorientierten Zugriff auf Analyse-Tools und Code-Repräsentationen zu ermöglichen und so das Kontext-Management effizient zu gestalten.

### 4. Methodik
Die methodische Umsetzung adaptiert das Horseshoe-Modell für die KI-gestützte Migration, wobei die textuelle SDD-Spezifikation die zentrale Abstraktionsebene bildet. Der Prozess wird durch einen orchestrierten Schwarm spezialisierter Agenten realisiert, die über MCP auf einen Code Knowledge Graph zugreifen:

- Analyse-Rollen: Extraktion der Geschäftslogik und Struktur mittels statischer Analyse-Tools (z. B. Tree-sitter).
- Spec-Writer-Rollen: Generierung detaillierter technischer Spezifikationen (SDD).
- Verifier-Rollen: Validierung der Specs gegen den ursprünglichen Code-Kontext zur Vermeidung von Halluzinationen.
- Builder-Rollen: Implementierung in der Zielsprache auf Basis der finalisierten Spezifikation.

Durch die Entkopplung von Tooling und Agenten via MCP wird sichergestellt, dass Informationen just-in-time abgefragt werden, was die Analyse umfangreicher Codebasen innerhalb begrenzter Kontext-Fenster ermöglicht.

### 5. Evaluation und Ausblick auf die Bachelorarbeit
Die Validierung erfolgt durch statische Code-Analyse zur Messung der Komplexität sowie eine Prüfung der funktionalen Vollständigkeit (Feature Parity) am Beispiel eines repräsentativen Quell-Moduls.

Ausblick auf die Bachelorarbeit: Darauf aufbauend soll das Framework wissenschaftlich erweitert werden. Ein zentraler Aspekt wird die Transformation zum hybriden Ansatz sein, bei dem textuelle Specs um visuelle Modelle (MDD) ergänzt werden, um strukturelle Abhängigkeiten noch präziser zu erfassen. Zudem sollen Forschungsfragen zur Skalierung des Wissenszugriffs mittels MCP in Großprojekten sowie zur automatisierten Bewertung der idiomatischen Code-Qualität ("Idiomatic Score") adressiert werden.
