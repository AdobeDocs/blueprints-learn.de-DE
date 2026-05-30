---
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 48%

---
# Vorlage für Anwendungsfallmuster

Diese Datei enthält die vollständige Markdown-Vorlage für eine Anwendungsfall-Musterseite. Ersetzen Sie beim Generieren eines neuen Musters alle `{{placeholder}}` Werte durch den tatsächlichen Inhalt.

---

## Vorlage

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

---

## Hinweise zur Verwendung dieser Vorlage

- **YAML frontmatter:** Die `exl-id` sollte eine Platzhalter-UUID sein (z. B. `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`). Die Veröffentlichungs-Pipeline weist den tatsächlichen Wert zu.
- **Abschnittsreihenfolge:** Der `Use case pattern` Abschnitt wird unmittelbar nach der Einleitung und vor dem `Use case overview` angezeigt. Er bietet Lesern eine klare, einzeilige Definition und den allgemeinen Ausführungsplan im Voraus.
- **Adobe-Produktnamen:** Verwenden Sie immer `[!DNL ...]` Syntax für Adobe-Produktnamen im Textkörper und in Tabellen (z. B. `[!DNL Journey Optimizer]`). Dies ist eine Experience League-Konvention, die die Übersetzung von Produktnamen verhindert.
- **Verknüpfungen zu Geschäftszielen:** Verwenden Sie relative Pfade von der Musterdatei zum Verzeichnis „Geschäftsziele“: `../../business-objectives/{{category}}/{{filename}}.md`.
- **Dateinamen in Kebab-Schreibweise:** Der Dateiname des Musters muss in Kebab-Schreibweise aus dem Mustertitel abgeleitet werden. Beispiel: „Ereignisausgelöstes Messaging“ wird `event-triggered-messaging.md`.
- **Ausführungsplan:** Verwenden Sie ` > ` (Leerzeichen, größer als, Leerzeichen) als Trennzeichen zwischen den Schritten. Halten Sie das Etikett genau `**Execution plan:**`.
- **Sachbezogene Dokumentation:** Gruppieren Sie Referenzlinks unter beschreibenden `###` Unterüberschriften (z. B. nach Anwendung oder Funktionsbereich). Dies sind die Experience League-Referenzen für die im Muster verwendeten Programme und Funktionen.
- **Architektur (optional):** Wenn ein Muster von einem Referenzarchitekturdiagramm profitiert, kann ein optionaler `## Architecture` zwischen `Applications` und `Related documentation` platziert werden.
- **Umfang:** Diese Vorlage schließt absichtlich detaillierte Implementierungsabschnitte (grundlegende/unterstützende/Anwendungsfunktionen, Voraussetzungen, Implementierungsoptionen und schrittweise Implementierungsschritte) aus. Diese Details finden Sie in der Experience League-Dokumentation, auf die von `Related documentation` verlinkt ist.