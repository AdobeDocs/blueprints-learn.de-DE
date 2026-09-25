---
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%
---
# Architekturdiagramm-Seitenvorlage

Dies ist die vollständige Markdown-Vorlage für eine Architekturdiagrammseite. Ersetzen Sie alle `{placeholder}` durch den Wert, der in Phase 1 des Qualifikations-Workflows erfasst wurde. Entfernen Sie alle optionalen Abschnitte, die nicht anwendbar sind (z. B. den `>[!MORELIKETHIS]` Block) - lassen Sie keine leeren Platzhalter in der generierten Datei.

---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

![{Alt text for diagram 1}](assets/{filename-1}){width="1000" zoomable="yes"}

## {Diagram 2 section title}

{1-2 sentence explanation.}

![{Alt text for diagram 2}](assets/{filename-2}){width="1000" zoomable="yes"}

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

---

## Regeln der Frontend-Materie

- **Erforderliche Felder:** `title`, `description`, `solution`.
- **Verbotene Felder** (zum Zeitpunkt der Veröffentlichung automatisch zugewiesen): `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt`, `thumbnail`. Schließen Sie diese nicht in neu erstellten Dateien ein.

## Konventionen für Textkörper

- **One H1** - der Seitentitel. Genau mit der `title`-Schriftart übereinstimmen.
- **Ein H2 pro Diagramm.** Keine H3 innerhalb der Diagrammabschnitte; halten Sie sie zu einem 1-2 Satz Intro plus Bild.
- **Markdown image embed** - Geben Sie einen beschreibenden ALT-Text an und verwenden Sie `{width="1000" zoomable="yes"}` für Diagramme.
- **Bildpfad** - Immer `assets/{filename}` (relativ zum Themenordner der Seite). Verwenden Sie keine absoluten Pfade.
- **Adobe-Produktnamen** - `[!DNL ...]` in Textkörper und Aufzählungszeichen einschließen. Beispiel: `[!DNL Real-Time CDP]`, `[!DNL Journey Optimizer]`, `[!DNL Experience Platform]`.
- **Links für Anwendungsfälle** - Verwenden Sie immer das absolute `/help/blueprints/use-case-patterns/{category}/{file}.md` Formular, damit der Link von jeder Seite aufgelöst wird, die diesen Inhalt enthält.
- **Experience League-Links** - absolute URLs, die mit `https://experienceleague.adobe.com/` beginnen. Die kanonische Dokument-URL einer lokalisierten Variante vorziehen.

## Abschnittsreihenfolge

Halten Sie die Reihenfolge auf allen Architekturseiten konsistent, damit die Leser vorhersehbar scannen können:

1. Titelei
2. H1 + Absatz öffnen
3. (Optional) `>[!MORELIKETHIS]`
4. Ein H2 pro Diagramm (in benutzerdefinierter Reihenfolge)
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## Längenerwartungen

40-100 Markdown-Zeilen sind typisch. Wenn die Seite 150 Zeilen überschreitet, ist der Inhalt wahrscheinlich in das Anwendungsfall-Muster-Gebiet abgedriftet - überprüfen Sie `scope-guardrails.md` erneut und erwägen Sie eine Aufspaltung.
