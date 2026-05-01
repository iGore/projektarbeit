# Entwicklung einer subagent-basierten Pipeline zur KI-gestützten Code-Migration
## Ein spec-getriebener Ansatz für Reverse Engineering, Re-Implementierung und Agentenorchestrierung

### 1. Ausgangslage und Motivation
Das Reverse Engineering und die Re-Implementierung bestehender Codebasen stellen eine der zentralen Herausforderungen der zeitgenössischen Softwareentwicklung dar. Im Lebenszyklus gewachsener Systeme entstehen technologisch bedingte Grenzen hinsichtlich Performance, Wartbarkeit und Skalierbarkeit, sodass ein Wechsel auf moderne Sprachen und Architekturen erhebliche Vorteile verspricht. Dazu zählen insbesondere verbesserte Typsicherheit, höhere Ressourceneffizienz und nativer Concurrency-Support. In der Praxis scheitert eine solche Migration jedoch häufig an der hohen kognitiven Last für Entwickler, einer lückenhaften Dokumentation des Bestands sowie an fundamentalen Paradigmenwechseln zwischen Quell- und Zieltechnologie.

Vor diesem Hintergrund wird die Arbeit als Beitrag zum KI-gestützten Software-Re-Engineering verstanden. Der etablierte Begriff des Re-Engineering bildet den fachlichen Rahmen, während der Einsatz spezialisierter Agenten und textueller Spezifikationen eine neue Automatisierungsstufe für Analyse, Rekonstruktion und Umsetzung verspricht.

### 2. Problemstellung
Bestehende Migrationsansätze, die primär auf direkter Transpilierung basieren, versagen häufig bei der Übertragung architektonischer Intentionen und produzieren infolgedessen schwer wartbaren Zielcode. Zwar bietet Spec-Driven Development (SDD) eine theoretische Abstraktionsebene, monolithische Large Language Models (LLMs) stoßen bei umfangreichen Codebasen jedoch schnell an Kontext-Limits. Hinzu kommt die Tendenz zu Halluzinationen, wodurch die Korrektheit generierter Artefakte gefährdet wird.

Es fehlt somit an einer orchestrierten Toolchain, die semantisches Code-Verständnis, skalierbaren Zugriff auf Code-Kontext und eine kontrollierte Überführung in technische Spezifikationen in einem konsistenten Migrationsprozess vereint.

### 3. Zielsetzung der Projektarbeit
Das Ziel dieser Projektarbeit ist die Konzeption und prototypische Implementierung einer automatisierten Migrations-Pipeline auf Basis orchestrierter Subagents. Der Fokus liegt auf der methodischen Umsetzung eines spec-getriebenen Ansatzes, der Reverse Engineering, Spezifikation, Transformationsplanung und Re-Implementierung verbindet, sowie auf einer klaren Scope-Abgrenzung. Daher wird ein prototypischer Proof of Concept für ein repräsentatives Quell-Modul angestrebt, an dem der grundlegende Durchstich durch Analyse, Spezifikation, Planung und Generierung nachvollziehbar demonstriert werden kann.

Das System soll aus bestehendem Quellcode präzise technische Spezifikationen in Markdown extrahieren und diese als belastbare Grundlage für die Code-Generierung in der Zielsprache nutzen. Technisch wird hierfür das Model Context Protocol (MCP) eingesetzt, um den Agenten einen gezielten, bedarfsorientierten Zugriff auf Analyse-Tools und Code-Repräsentationen zu ermöglichen und so das Kontext-Management effizient zu gestalten.

### 4. Methodik
Die methodische Umsetzung adaptiert das Horseshoe-Modell für die KI-gestützte Migration, wobei die textuelle SDD-Spezifikation die zentrale Abstraktionsebene bildet. Der Prozess wird durch einen orchestrierten Schwarm spezialisierter Agenten realisiert, die über MCP auf eine strukturierte Repository-Kontextbasis und Code-Intelligence-Werkzeuge zugreifen. Ergänzend wird Context Engineering genutzt, um den Wissenszugriff für die einzelnen Rollen gezielt zu steuern und relevante Informationen nur bedarfsorientiert bereitzustellen.

- Analyse-Rollen: Extraktion der Geschäftslogik und Struktur mittels statischer Analyse-Tools (z. B. Tree-sitter) sowie Zerlegung in einzelne Funktionalitäten mit Evidenzbezug.
- Spec-Writer-Rollen: Generierung detaillierter technischer Spezifikationen (SDD) pro Funktionalität oder Use Case.
- Orchestrator-Rolle: Koordination der Artefakt-Übergaben und Fan-out von Spec-Writer-Läufen pro identifizierter Funktionalität.
- Builder-Rollen: Implementierung in der Zielsprache auf Basis der finalisierten Spezifikation.

Durch die Entkopplung von Tooling und Agenten via MCP wird sichergestellt, dass Informationen just-in-time abgefragt werden, was die Analyse umfangreicher Codebasen innerhalb begrenzter Kontext-Fenster ermöglicht. Auf dieser Grundlage soll der Prototyp im Fallbeispiel zeigen, ob sich der Ansatz nicht nur konzeptionell, sondern auch praktisch als konsistenter Migrationsprozess umsetzen lässt.

### 5. Evaluation und Ausblick auf die Bachelorarbeit
Die Validierung erfolgt am Beispiel eines repräsentativen Quell-Moduls. Im Mittelpunkt stehen Vollständigkeit im Sinne von Feature Parity, Qualität und Wartbarkeit der erzeugten Artefakte sowie die Nachvollziehbarkeit der Migrationsentscheidungen.

Ausblick auf die Bachelorarbeit: Eine Erweiterung zum hybriden Ansatz aus Spec-Driven Development (SDD) und Model-Driven Development (MDD) soll das Framework wissenschaftlich vertiefen. Textuelle Spezifikationen werden dabei um visuelle Modelle ergänzt, um strukturelle Abhängigkeiten noch präziser zu erfassen. Zudem sollen Forschungsfragen zur Skalierung des Wissenszugriffs mittels MCP in Großprojekten sowie zur automatisierten Bewertung der idiomatischen Code-Qualität ("Idiomatic Score") adressiert werden.
