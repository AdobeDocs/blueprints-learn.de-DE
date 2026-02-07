---
name: blueprint-document-reference
description: Referenz zum Erstellen und Bearbeiten von Adobe Digital Experience Blueprint-Dokumenten. Wird verwendet, wenn neue Blueprints erstellt, Blueprint-Seiten hinzugefügt oder Fragen zur Blueprint-Struktur, zu Abschnitten, Vorlagen oder zum Verweisen auf Adobe Experience League gestellt werden.
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---


# Blueprint-Dokumentreferenz

Verwenden Sie diese Fähigkeit beim Erstellen oder Bearbeiten von Blueprint-Dokumenten in diesem Repository. Blueprints sind wiederholbare Implementierungen, die etablierte Geschäftsprobleme beheben und Architekturdiagramme, technische Überlegungen und Links zur Adobe Experience League-Dokumentation enthalten.

## Anwendungszeitpunkt

- Erstellen eines neuen Blueprint-Dokuments oder einer neuen Blueprint-Übersichtsseite
- Hinzufügen oder Neustrukturieren von Abschnitten in einem vorhandenen Blueprint
- Verknüpfen mit oder Zitat aus der Adobe Experience League-Dokumentation
- Ausrichten neuer Inhalte mit Blueprint-Konventionen (Schriftarten, Überschriften, Diagramme)

## Kurzübersicht

1. **Dokumentzweck**: Blueprints bieten eine System- und Datenflussarchitektur, die zeigt, wie Adobe Experience Platform und Programme integriert sind. Sie sind visuell und technisch, nicht im Marketing.
2. **Abschnitte**: Verwenden Sie die Standardabschnitte aus der Vorlage; lassen Sie nur weg, wenn sie nicht anwendbar sind (siehe [reference.md](reference.md)).
3. **Experience League**: Verknüpfen Sie Produktdokumente, APIs, Leitplanken und Tutorials lieber mit Experience League. Verwenden Sie vollständige URLs; siehe [reference.md](reference.md) für URL-Muster und -Formatierungen.
4. **Repo-Struktur**: Blueprints live unter `help/blueprints/`. `help/blueprints/TOC.md` beim Hinzufügen oder Verschieben von Blueprint-Seiten aktualisieren.

## Dokumentvorlage

Jede Blueprint-Seite sollte dieser Struktur folgen. Nur zutreffende Abschnitte einschließen.

```markdown
---
title: [Short descriptive title]
description: "[One sentence: what this blueprint shows and why it matters.]"
solution: [Product name, e.g. Real-Time Customer Data Platform, Journey Optimizer]
exl-id: [UUID - leave blank if new, this will be auto-generated as part of the Experience League publishing flow]
---
# [H1 - same as title or expanded]

[1–3 paragraphs: what the blueprint covers, key capabilities, and who it’s for.]

## Applications

* [Product 1]
* [Product 2]

## Use cases

* [Use case 1]
* [Use case 2]

## Prerequisites

[Bullets or short paragraphs: required products, config, or setup.]

## Architecture Diagram

<img src="[path to SVG/image]" alt="[Descriptive alt]" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Guardrails

[Link to Experience League guardrails and any blueprint-specific limits.]

## Implementation patterns

[Optional: named patterns with bullets.]

## Implementation steps

1. [Step with link to Experience League where relevant]
2. ...

## Implementation considerations

[Optional: identity, performance, security, etc.]

## Related documentation

[Grouped links to Experience League: product docs, APIs, tutorials.]
```

Verwenden Sie für Übersichts- oder Hub-Seiten eine kürzere Struktur: Einführung, Anwendungsfälle (oder Registerkarten), Bildarchitektur, Szenario/Mustertabelle, Voraussetzungen, Leitplanken, zugehörige Dokumentation. Beispiele finden Sie in den vorhandenen Übersichten in `help/blueprints/` .

## Titelei

| Feld | Erforderlich | Hinweise |
|-------|----------|--------|
| `title` | Ja | Kurz; `[!DNL Product Name]` für Produktnamen nach Adobe-Stil verwenden |
| `description` | Ja | Ein Satz; wird bei Suche und Karten verwendet |
| `solution` | Ja | Primäres Produkt (z. B. Real-Time Customer Data Platform, Journey Optimizer) |
| `exl-id` | Ja | UUID; Leer lassen für neue Seiten |
| `doc-type` | Für Übersichten | `overview-page` für die wichtigsten Blueprint-Übersichtsseiten verwenden |
| `kt` | optional | ID des Wissensdatenbankartikels, falls verknüpft |

## Verweisen auf Adobe Experience League

- **Wann eine Verknüpfung erstellt**: Verknüpfung zu Experience League für Produktdokumentation, API-Referenzen, Leitplanken, Tutorials und Konfigurationsschritte. Keine langwierigen Verfahren duplizieren; zusammenfassen und verknüpfen.
- **URL-**: Verwenden Sie vollständige URLs. Bevorzugen Sie `https://experienceleague.adobe.com/docs/...` oder `https://experienceleague.adobe.com/en/docs/...`. Für Entwicklerdokumente ist `https://developer.adobe.com/...` ebenfalls gültig.
- **Verknüpfungstext**: Verwenden Sie einen beschreibenden Text (z. B. &quot;[Schemata erstellen](url) und nicht „Hier klicken„). Für Produktnamen im Link-Text verwenden Sie gegebenenfalls `[!DNL Product Name]`.
- **Abschnitt zur zugehörigen Dokumentation**: Beenden Sie Blueprints mit dem Abschnitt „Verwandte Dokumentation“, in dem Links nach Kategorie gruppiert sind (z. B. Zielkonfigurationen, SDK-Dokumentation, Profil und Segmentierung, Tutorials).

Ausführliche URL-Muster, Linkgruppierung und Beispiele finden Sie unter [reference.md](reference.md).

## Checkliste vor dem Absenden

- [ ] Frontmatter hat `title`, `description`, `solution`, `exl-id`
- [ ] H1 entspricht dem Titel oder erweitert ihn entsprechend.
- [ ] Architekturdiagramm vorhanden und Alternativtext beschreibend
- [ ] Implementierungsschritte sind mit Experience League verknüpft, in dem Verfahren ausgeführt werden
- [ ] Abschnitt zu Leitplanken verweist auf offizielle Dokumente zu Experience League-Leitplanken
- [ ] Abschnitt Zugehörige Dokumentation enthält relevante Experience League-Links
- [ ] Neue oder verschobene Seiten werden in `help/blueprints/TOC.md` angezeigt

## Weitere Ressourcen

- Vollständige Vorlagen- und Abschnittshinweise: [reference.md](reference.md)
- Bestehende Blueprints: `help/blueprints/` (z. B. `audience-activation/real-time-lookup.md`, `customer-journeys/journey-optimizer/journey-optimizer-overview.md`)
- Inhaltsverzeichnis und Navigation: `help/blueprints/TOC.md`
