---
name: use-case-pattern-builder
description: 'Handbuch zur Erstellung neuer Anwendungsfall-Musterinhalte für das Adobe Experience Platform Blueprints-Repository. Verwenden Sie diese Fähigkeit, wenn Sie ein neues Anwendungsfallmuster hinzufügen, Inhalte für Implementierungshandbücher erstellen oder wenn der/die Benutzende das Hinzufügen von Mustern zur Blueprints-Site erwähnt. Übernimmt den gesamten Workflow: das Erfassen von Musterinformationen, das Generieren der Markdown-Datei mit der richtigen Vorlagenstruktur und das Aktualisieren aller Querverweisseiten (TOC.md, overview.md).'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---


# Anwendungsfall - Mustergenerator

Diese Fähigkeit leitet die Erstellung eines neuen Anwendungsfallmusters für das Adobe Experience Platform Blueprints-Repository. Es übernimmt den gesamten Workflow: das Erfassen von Musterinformationen der Benutzenden, das Generieren der Markdown-Inhaltsdatei mit der richtigen Vorlagenstruktur und das Aktualisieren aller Querverweisseiten, sodass das neue Muster auffindbar ist.

Bevor Sie beginnen, lesen Sie die folgenden Referenzdateien für die vollständige Vorlagenstruktur und die Checkliste der zu aktualisierenden Seiten:

- `references/pattern-template.md` - Die vollständige Markdown-Vorlage mit Platzhalterwerten
- `references/pages-to-update.md` - Die Checkliste der Seiten, die beim Hinzufügen eines Musters aktualisiert werden müssen

## Phase 1: Informationssammlung

Befragen Sie den Benutzer, um alle erforderlichen Informationen zu sammeln, bevor Sie Dateien generieren. Fragen Sie nach Folgendem und fahren Sie erst mit der Inhaltserstellung fort, wenn jedes Element bereitgestellt oder explizit zurückgestellt wird.

### Erforderliche Informationen

1. **Mustername** - Der für Menschen lesbare Titel (z. B. „Ereignis-ausgelöstes Messaging„).

2. **Kategorie** — Genau eine der folgenden Eigenschaften:
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **Beschreibung der Primären Funktionen** - Ein einziger Satz, der beschreibt, was dieses Muster bewirkt (wird in der Übersichtstabelle und in der Beschreibung der Frontend-Komponente verwendet).

4. **Zentrale Adobe-Lösungen** - Die Adobe-Produkte sind von zentraler Bedeutung für dieses Muster. Wählen Sie je nach Bedarf aus Journey Optimizer, Real-Time Customer Data Platform, Experience Platform, Customer Journey Analytics, Brand Concierge, Journey Optimizer B2B edition, Real-Time CDP B2B edition oder anderen.

5. **Funktionskettenschritte** - 3-6 sequenzielle Phasen, die den Ausführungsfluss des Musters beschreiben, getrennt durch `>`. Beispiel: „Ereignisaufnahme > Journey-Eintrag > Bedingungsauswertung > Nachrichtenversand > Reporting“.

6. **Unterstützte Geschäftsziele** - Ein oder mehrere Geschäftsziele aus dem bestehenden Satz unter `/help/blueprints/business-objectives/`. Jede sollte den Zielnamen, den Unterordner der Kategorie und den Dateinamen enthalten. Stellen Sie sicher, dass die referenzierten Dateien vorhanden sind, bevor Sie Inhalte generieren.

7. **Beispiel für taktische Anwendungsfälle** - 6-10 Szenarien mit Aufzählungszeichen, die beschreiben, wie dieses Muster auf verschiedene Geschäftskontexte angewendet werden kann. Jeder sollte einen fett gedruckten Szenarionamen gefolgt von einer Beschreibung haben.

8. **KPIs** - Eine Tabelle mit drei Spalten: KPI (Name), Beschreibung (was sie misst), Messung (Formel oder Ansatz).

9. **Implementierungsoptionen** - 2-4 Implementierungsoptionen. Für jede Option Folgendes erfassen:
   - Optionsname
   - Am besten geeignet für (wenn diese Option verwendet wird)
   - Funktionsweise (2-4 Absätze)
   - Wichtige Aspekte (Aufzählung)
   - Vorteile (Aufzählung)
   - Einschränkungen (Aufzählung)
   - Links zu Experience League (URLs zur entsprechenden Dokumentation)

### Optional, aber empfohlen

- Absätze zur Übersicht über Anwendungsfälle (3-5 Absätze; wenn nicht angegeben, entwerfen Sie sie aus den anderen Informationen.)
- Anwendungsliste mit Beschreibungen der Rollen der einzelnen Adobe-Anwendungen
- Grundlegende Funktionstabelle (Funktion, Status, Was muss vorhanden sein, Experience League-Referenz)
- Tabelle der unterstützenden Funktionen (Funktion, Status, warum es wichtig ist, Experience League-Referenz)
- Anwendungstabellen (eine pro Anwendung, mit Funktion, Implementierungsphase, Beschreibung)
- Checkliste mit Voraussetzungen

Wenn der/die Benutzende die optionalen Elemente nicht bereitstellt, generieren Sie angemessene Standardwerte basierend auf der Musterkategorie, den Lösungen und der Funktionskette.

## Phase 2: Inhaltserstellung

Erzeugen Sie die Muster-Markdown-Datei unter dem folgenden Pfad:

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

Für den Dateinamen muss die Groß-/Kleinschreibung des Musters verwendet werden. Beispielsweise wird „Ereignis-ausgelöstes Messaging“ `event-triggered-messaging.md`.

Verwenden Sie die Vorlage aus `references/pattern-template.md` und füllen Sie alle Platzhalterwerte mit den erfassten Informationen aus. Die generierte Datei muss alle Abschnitte in der Vorlage enthalten:

1. **YAML frontmatter** - Titel, Beschreibung, Lösung (kommagetrennt), exl-id (UUID-Platzhalter wie `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` generieren - das Veröffentlichungs-Team weist den echten zu).

2. **Eröffnungsabschnitt** - `# {Pattern name}` Überschrift, gefolgt von einem einführenden Absatz und der „Verwenden Sie dieses Handbuch, um zu verstehen…“ Satz.

3. **Übersicht über Anwendungsfälle** - 3-5 Absätze, die den Musterbereich beschreiben, wann er gilt, was er tut und was nicht, und wer die typischen Stakeholder sind.

4. **Wichtige Geschäftsziele** - Jedes Ziel ist eine verknüpfte Überschrift mit einer kurzen Beschreibung und einer Zusammenfassungszeile für KPIs.

5. **Beispiel für taktische Anwendungsfälle** - Aufzählung von 6-10 Szenarien.

6. **Key Performance Indicators** — Tabelle mit KPI, Beschreibung, Messspalten.

7. **Anwendungsfallmuster** — Beschreibungsabsatz und die Funktionskette.

8. **Programme** - Liste der Adobe-Programme mit `[!DNL ...]` Formatierung und Beschreibungen.

9. **Grundlegende Funktionen** - Tabelle mit Spalten: Grundlegende Funktion, Status, Was muss vorhanden sein, Experience League-Referenz. Statuswerte: Erforderlich, An Ort und Stelle angenommen, Nicht zutreffend.

10. **Unterstützende Funktionen** - Tabelle mit Spalten: Unterstützende Funktion, Status, Warum es wichtig ist, Experience League-Referenz. Statuswerte: Empfohlen, enthalten, nicht anwendbar.

11. **Anwendungsfunktionen** - Eine Tabelle pro Anwendung mit Spalten: Funktion, Implementierungsphase, Beschreibung.

12. **Voraussetzungen** - Checkliste mit `- [ ]` Syntax.

13. **Implementierungsoptionen** - 2-4 detaillierte Optionen, jeweils mit Best for-, Funktionsweise-, wichtigen Überlegungen, Vorteilen, Einschränkungen und Experience League-Links.

14. **Optionsvergleich** - Zusammenfassende Vergleichstabelle am Ende.

## Phase 3: Aktualisierungen von Querverweisen

Aktualisieren Sie nach dem Generieren der Pattern-Datei die folgenden Dateien. `references/pages-to-update.md` finden Sie die detaillierte Checkliste.

### Inhaltsverzeichnis.md

**Datei:** `/help/blueprints/TOC.md`

Fügen Sie einen neuen Eintrag unter dem richtigen Kategorieabschnitt hinzu. Die Kategorien sind diesen Inhaltsverzeichnisabschnitten zugeordnet:

| Kategorie-Slug | Inhaltsverzeichnis-Abschnittsüberschrift |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

Das Eingabeformat lautet:

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

Fügen Sie den neuen Eintrag nach dem letzten vorhandenen Eintrag im Abschnitt Übereinstimmung hinzu. Bewahren Sie den genauen Einzug (vier Leerzeichen vor dem `+`).

### Übersichtsseite

**Datei:** `/help/blueprints/use-case-patterns/overview.md`

Fügen Sie der richtigen Kategorietabelle eine neue Zeile hinzu. Das Format lautet:

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

Fügen Sie die neue Zeile nach der letzten vorhandenen Zeile in der entsprechenden Kategorietabelle hinzu.

## Phase 4: Validierung

Nachdem alle Dateien erstellt und aktualisiert wurden, überprüfen Sie Folgendes:

1. **Geschäftsziel-Links** - Jeder Geschäftsziel-Link in der Musterdatei verweist auf eine vorhandene Datei unter `/help/blueprints/business-objectives/`. Verwenden Sie global oder read , um zu bestätigen, dass jede Zieldatei vorhanden ist.

2. **Inhaltsverzeichniseintrag-Platzierung** - Der neue Inhaltsverzeichniseintrag befindet sich im richtigen Kategorieabschnitt und verwendet die richtigen Einzüge und das richtige Pfadformat.

3. **Übersichtstabellenzeile** - Die neue Übersichtszeile befindet sich in der richtigen Kategorietabelle und folgt demselben Spaltenformat wie vorhandene Zeilen.

4. **Dateibenennung** — Der Dateiname des Musters verwendet kebab-case und entspricht dem Pfad, auf den sowohl in TOC.md als auch in overview.md verwiesen wird.

5. **Vollständigkeit von Frontend** - Die Musterdatei enthält Titel, Beschreibung, Lösung und exl-id in der YAML-Schriftart.

6. **Experience League-Links** - Überprüfen Sie vor Ort, ob Experience League-URLs plausibel sind (beginnen Sie mit `https://experienceleague.adobe.com/`).

Melden Sie etwaige Validierungsfehler dem Benutzer und beheben Sie diese, bevor Sie die Aufgabe als abgeschlossen betrachten.

## Notizen

- Verwenden Sie immer `[!DNL ...]` Syntax für Adobe-Produktnamen in Tabellen und im Textkörper, wobei die Konvention der vorhandenen Musterdateien befolgt wird.
- Die `exl-id` in frontmatter sollte eine Platzhalter-UUID sein. Die Veröffentlichungs-Pipeline weist den tatsächlichen Wert zu.
- Wenn der/die Benutzende mehrere Muster gleichzeitig erstellen möchte, wiederholen Sie die Phasen 2-4 für jedes Muster, aber sammeln Sie alle Informationen in Phase 1.
- Wenn eine neue Kategorie benötigt wird, die in der obigen Liste nicht vorhanden ist, warnen Sie den Benutzer, dass TOC.md und overview.md neue Abschnitte erstellen müssen, und behandeln Sie dies als einen separaten Schritt.
