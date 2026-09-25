---
name: architecture-diagram-category-builder
description: 'Anleitung zur Erstellung einer brandneuen Kategorie der obersten Ebene (Unterabschnitt) unter „Architekturdiagramme und Blueprints“ im Adobe Experience Platform Blueprints-Repository. Verwenden Sie diese Fähigkeit, wenn ein vorgeschlagenes Architekturdiagramm nicht zu einer der bestehenden Kategorien passt (Architekturübersichten, Zielgruppen- und Profilaktivierung, B2B-Aktivierung und -Marketing, Kundeneinblicke, Kunden-Journey) und ein neues benötigt wird. Verarbeitet den gesamten Workflow: Bestätigung, dass eine neue Kategorie tatsächlich gerechtfertigt ist, Erzwingen von Benennungskonventionen für Ordner/Anker, Erstellen der Ordnerstruktur und der Landingpage overview.md, Hinzufügen des Unterabschnitts „toc.md“ und Aktualisieren des Kartenrasters „architecture-diagrams“. Um eine Seite zu einer *vorhandenen* Kategorie hinzuzufügen, verwenden Sie stattdessen architecture-diagram-page-builder .'
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%
---

# Architekturdiagramm für Kategorie Builder

Diese Fähigkeit leitet die Erstellung einer neuen Kategorie der obersten Ebene unter `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` in `/help/blueprints/TOC.md`. Eine Kategorie ist ein Ordner wie `customer-insights/` oder `b2b-activation-marketing/` - eine Gruppe verwandter Architekturdiagrammseiten mit einer eigenen `overview.md` Landingpage und einem eigenen Inhaltsverzeichnis.

**Dies ist eine seltene Operation.** Heute gibt es fünf Kategorien. Eine sechste sollte nur hinzugefügt werden, wenn eine wirklich neue Domain der Architekturinhalte zu keiner vorhandenen Domain passt - nicht als Abkürzung, um die Organisation einer Seite unter einer vorhandenen Kategorie zu vermeiden.

## Pflichtlektüre vor dem Start

- `./references/naming-conventions.md` - Die Benennungsregel für Ordner/Anker/Beschriftungen und warum sie wichtig ist. Lesen Sie dies vollständig durch. Es ist die zentrale Datenquelle für die Benennung von Kategorien.
- `./references/category-overview-template.md` - Die genaue Struktur, die für die `overview.md` der neuen Kategorie erforderlich ist.
- Falls noch nicht geschehen, überspringen Sie auch `../architecture-diagram-page-builder/SKILL.md` - sobald die Kategorie vorhanden ist, werden einzelne Seiten innerhalb dieser Kategorie mithilfe dieser Fähigkeit hinzugefügt, nicht mit dieser.

## Phase 1: Bestätigen, dass eine neue Kategorie tatsächlich benötigt wird

Bevor Sie etwas Anderes tun, listen Sie die fünf vorhandenen Kategorien und deren Umfang für den Benutzer auf:

| Kategorie | Ordner | Umfang |
| --- | --- | --- |
| Architekturübersichten | `architecture-overviews/` | Experience Cloud-/Experience Platform-Architektur der obersten Ebene, Leitplanken, Bereitstellungs-SDKs |
| Aktivierung von Zielgruppen und Profilen | `audience-profile-activation/` | Erstellung und Aktivierung von Audiences/Profilen über Real-Time CDP, Audience Manager |
| B2B-Aktivierung und Marketing | `b2b-activation-marketing/` | Account-Based Activation, Buying-Group Journey, Marketo/Workfront |
| Customer Insights | `customer-insights/` | Customer Journey Analytics und seine Integrationen |
| Kunden-Journey | `customer-journeys/` | Journey Optimizer, Entscheidungs-Management, Campaign v7/v8 |

Bitten Sie den Benutzer zu bestätigen, dass der vorgeschlagene Inhalt zu keinem dieser Elemente passt. Wenn es eine knappe Anpassung aufweist (z. B. ein neues B2B-Diagramm oder ein neues Personalisierungsdiagramm), leiten Sie zu `architecture-diagram-page-builder` für diese bestehende Kategorie um, anstatt eine neue zu erstellen. Fahren Sie nur dann mit Phase 2 fort, wenn der Benutzer bestätigt, dass eine wirklich neue Kategorie gerechtfertigt ist.

## Phase 2: Sammeln von Kategorieinformationen

Verwenden Sie ein Frageformular, um in einer Runde Folgendes zu erfassen:

1. **Kategorielabel** - die vollständige, für Menschen lesbare Inhaltsverzeichnisbeschriftung (z. B. &quot;Commerce Architecture“, keine Abkürzung). 2-3 vorgeschlagene Formulierungen plus „Sonstige“.
2. **Ein-Satz-Beschreibung** - Was diese Kategorie für die `overview.md` und Landingpage-Karte abdeckt.
3. **Primäre Adobe-Lösung(en** — für das `solution` Frontend.
4. **Anfangsseiten** - Verfügt der Benutzer bereits über 1+ Seiten, die in dieser Kategorie platziert werden können, oder ist dies nur die Strukturvorlage der Kategorie für Seiten, die später folgen sollen?

Leiten Sie den Ordnernamen und den Anker über die Kategoriekennzeichnung mithilfe der Slug-Regel in `./references/naming-conventions.md` ab (Kleinbuchstaben, `&`, Bindestriche, keine Abkürzung). Zeigen Sie dem Benutzer den abgeleiteten Ordner/Anker an und bestätigen Sie ihn, bevor Sie fortfahren - dies ist ein Detail, das später aufwändig zu beheben ist.

## Phase 3: Ordnerstruktur erstellen

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

Generieren von `overview.md` mithilfe von `./references/category-overview-template.md`. Wenn der/die Benutzende die Anfangsseiten fertig hat, listen Sie sie jetzt in der Tabelle auf (mithilfe von `architecture-diagram-page-builder`, um diese Seitendateien selbst zu generieren - diese Fähigkeit erstellt nur die Kategoriestruktur und die Übersichtsseite, nicht einzelne Diagrammseiten). Wenn noch keine Seiten vorhanden sind, kann die Tabelle leer sein oder weggelassen werden, bis die erste Seite hinzugefügt wird - beachten Sie dies für den Benutzer, anstatt Platzhalterzeilen zu erfinden.

Der `assets/` Ordner kann bei der Erstellung leer sein. Er ist vorhanden, sodass die erste Diagrammseite, die der Kategorie hinzugefügt wird, Platz für die Bilder hat.

## Phase 4: Hinzufügen des Unterabschnitts „Inhaltsverzeichnis.md“

Fügen Sie die neue Kategorie als Eintrag der obersten Ebene unter `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` ein, der hinter der letzten vorhandenen Kategorie positioniert ist, es sei denn, der Benutzer gibt etwas Anderes an:

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

Regeln:

- 2-Leerzeichen Einzug für die Kategorieüberschrift, passend zu den anderen fünf.
- Der `{#{folder-slug}}` muss exakt mit dem Ordnernamen übereinstimmen (siehe „naming-Conventions.md„).
- `+ [Overview]` ist immer der erste Eintrag bei einem Einzug mit vier Leerzeichen vor den Inhaltsseiten.
- Bewahren Sie die bestehende Reihenfolge und den Inhalt aller anderen Inhaltsverzeichniseinträge auf - fügen Sie nur nicht verwandte Abschnitte ein, ordnen Sie sie niemals neu an oder schreiben Sie sie um.

## Phase 5: Aktualisieren der Landingpage für Architekturdiagramme und Blueprints

Fügen Sie eine neue Karte zu `help/blueprints/architecture-diagrams/overview.md` hinzu, in demselben `<table style="table-layout:fixed; width:100%;">`, das von den anderen fünf Karten verwendet wird. Die neue Karte:

- Links zu `{new-folder}/overview.md`.
- Verwendet eine repräsentative Diagrammminiaturansicht aus `{new-folder}/assets/` (oder einen neutralen Platzhalterhinweis, falls noch kein Diagramm vorhanden ist - markieren Sie dies dem Benutzer, anstatt einen Bildpfad zu erfinden).
- Verwendet denselben Inline-Stilblock wie die vorhandenen Karten (`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;` auf dem Bild, `min-height:100px;` auf dem Textdiv).

**Berechnen Sie das Rasterlayout neu.** Die vorhandenen fünf Karten füllen ein 3-spaltiges Raster (zwei Zeilen, eine hintere leere Zelle). Durch Hinzufügen einer sechsten Karte wird diese leere Zelle exakt gefüllt - keine Layout-Änderung erforderlich. Wenn dies die Kategorie 7., 8. usw. ist, fügen Sie eine neue `<tr>` mit der/den neuen Karte(n) hinzu und füllen Sie alle verbleibenden leeren Zellen in dieser Zeile mit leeren `<td style="width:33%; ...;"></td>`, damit die Zeile nicht zerlegt wird.

## Phase 6: Validierung

Bestätigen Sie Ihre Eingaben und melden Sie sie dem Benutzer:

1. **Benennungskonsistenz** - Ordnername, Inhaltsverzeichnisanker und Kategoriebeschriftungs-Slug sind identisch (per naming-Conventions.md).
2. **overview.md structure** — stimmt mit `category-overview-template.md` überein (Intro + zweispaltige `Diagram | Description`, keine eingebetteten Bilder oder verschachtelten Listen in der Tabelle).
3. **TOC.md placement** — neue Unterabschnitte unter Architekturdiagramme und Blueprints, `+ [Overview]` zuerst, Einzug ist korrekt, keine anderen Einträge wurden geändert.
4. **Landingpage-Karte** - An der richtigen Rasterposition hinzugefügt, verwendet den standardmäßigen Kartenstil und enthält Links zum neuen `overview.md`.
5. **Umleitungen** - Wenn diese Kategorie Inhalte konsolidiert oder umbenennt, die zuvor an anderer Stelle gelebt haben (selten für eine brandneue Kategorie, aber überprüfen), fügen Sie Einträge zu `redirects.csv` hinzu, die dem vorhandenen `source,dest`-Format entsprechen, das für frühere Umbenennungen von Architekturdiagrammen verwendet wurde.

Beheben Sie etwaige Validierungsprobleme, bevor Sie die Aufgabe als abgeschlossen betrachten.

## Notizen

- Wenn der Benutzer später eine Kategorie umbenennt (Beschriftung, Ordner oder Anker), handelt es sich um einen Umbenennungsvorgang und nicht um einen Vorgang mit einer neuen Kategorie - befolgen Sie die Regel „naming-Conventions.md“ für den neuen Namen, aktualisieren Sie jeden internen Link (TOC.md, beide Übersichtsseiten, gleichrangige relative Links, Qualifikationsdokumente) und fügen Sie Umleitungseinträge hinzu. Behandeln Sie Kategorienamen so, wie sie zuvor in diesem Repository behandelt wurden: `git mv` Sie den Ordner, dann eine repo-weite Suche und Ersetzung der alten Pfadformulare, niemals eine blinde globale Zeichenfolge ersetzen, die mit nicht verwandten externen URLs kollidieren könnte (z. B. Links zu `experienceleague.adobe.com/docs/experience-platform/...` Produktdokumenten).
- Halten Sie diese Kenntnisse und `architecture-diagram-page-builder` synchron: Wenn die Unterabschnitt-Zuordnungstabelle in der `references/toc-placement.md` von `architecture-diagram-page-builder` die neue Kategorie noch nicht auflistet, fügen Sie sie auch dort hinzu.
