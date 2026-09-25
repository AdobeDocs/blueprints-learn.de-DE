---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
# Benennungskonventionen: Architekturdiagramme und Blueprints

Dieses Dokument ist die Quelle der Wahrheit für die Benennung der Kategorien unter `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`. Sowohl die `architecture-diagram-category-builder` (neue Kategorien) als auch die `architecture-diagram-page-builder` (neue Seiten innerhalb vorhandener Kategorien) müssen diese Regeln befolgen.

## Die Regel

**Ordnername = TOC-Anker-Slug = Keebab-Case der vollständigen TOC-Kennzeichnung.** Alle drei müssen exakt übereinstimmen, ohne Abkürzung oder Kürzung.

| Titel des Inhaltsverzeichnisses | Anker | Ordner |
| --- | --- | --- |
| Architekturübersichten | `#architecture-overviews` | `architecture-overviews/` |
| Aktivierung von Zielgruppen und Profilen | `#audience-profile-activation` | `audience-profile-activation/` |
| B2B-Aktivierung und Marketing | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| Customer Insights | `#customer-insights` | `customer-insights/` |
| Kunden-Journey | `#customer-journeys` | `customer-journeys/` |

Dies ist der aktuelle, korrigierte Status aller fünf Kategorien (Stand: 2026-09-16). Zuvor in der Geschichte dieses Repositorys wurden einige davon abgekürzt (`architecture-overview`, `audience-activation`, `b2b-activation`) - diese Inkonsistenz wurde behoben. Für neue oder vorhandene Kategorien dürfen keine abgekürzten Ordner-/Ankernamen wieder eingeführt werden.

## Warum das wichtig ist

- **Vorhersagbarkeit.** Mitwirkende (Mensch oder Agent) sollten den Ordnerpfad anhand der Inhaltsverzeichnisbeschriftung erraten können und umgekehrt, ohne die Datei TOC.md öffnen zu müssen.
- **Sichere Automatisierung.** Kenntnisse und Skripte, die Pfade aus Beschriftungen (oder Beschriftungen aus Pfaden) generieren, funktionieren nur dann zuverlässig, wenn die Zuordnung exakt und mechanisch ist (Kebab-Fall, keine Abkürzung).
- **Umleitungshygiene.** Für jede Umbenennung sind neue Einträge in `redirects.csv` erforderlich. Wenn Namen von Anfang an stabil und vollständig beschreibend sind, wird eine wiederholte Umbenennungsabwanderung vermieden.

## So leiten Sie einen Slug von einer Kennzeichnung ab

1. Die Kennzeichnung in Kleinbuchstaben schreiben.
2. `&` ablegen und die umgebenden Wörter mit einem Bindestrich verbinden (z. B. `Audience & Profile Activation` -> `audience-profile-activation`).
3. Ersetzen Sie Leerzeichen durch Bindestriche.
4. Interpunktion abziehen von Bindestrichen.
5. Wörter dürfen nicht gekürzt, gekürzt oder aus dem Etikett entfernt werden (kein `b2b-activation` für „B2B-Aktivierung und -Marketing“ — `b2b-activation-marketing` verwenden).

## Erforderliche Assets pro Kategorie

Jeder Kategorieordner direkt unter `help/blueprints/architecture-diagrams/` muss Folgendes enthalten:

1. **`overview.md`** - Eine Landingpage für die Kategorie. Siehe `./category-overview-template.md` für die erforderliche Struktur. Jede Kategorieübersichtsseite muss gleich aussehen: Einführungsabsätze und dann eine einzelne `| Diagram | Description |`, in der jede Seite der Kategorie in der Inhaltsverzeichnisreihenfolge aufgelistet wird. Verwenden Sie keine verschachtelten `<ul><li>`, eingebetteten Diagrammbilder oder eine dritte Spalte - stimmen Sie mit den vorhandenen fünf Kategorien genau überein.
2. **`assets/`** - Ordner für Diagrammbilder, auch wenn er bei der Erstellung leer ist (erstellen Sie ihn, wenn das erste Diagramm hinzugefügt wird).

## Anforderungen für TOC.md

- Der `+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)` Eintrag der Kategorie ist immer der **erste** Eintrag unter der Kategorieüberschrift, vor allen Inhaltsseiten.
- Die Kategorieüberschrift und ihr Anker befinden sich unmittelbar unter `+ Architecture Diagrams and Blueprints{#architecture-diagrams}`, und zwar auf derselben Ebene mit zwei Einzügen wie die anderen fünf Kategorien.
- Inhaltsseiten sind 4 Leerzeichen eingerückt (`+` mit vier vorangestellten Leerzeichen versehen). Verschachtelte Untergruppierungen (z. B. RTCDP-Gruppierung unter Zielgruppe und Profilaktivierung) werden mit 6 Leerzeichen eingerückt.

## Landingpage-Anforderungen

`help/blueprints/architecture-diagrams/overview.md` (die Landingpage für Architekturdiagramme und Blueprints der obersten Ebene) muss genau eine Karte pro Kategorie in der Reihenfolge des Inhaltsverzeichnisses haben. Jede Karte:

- Links zum `overview.md` der Kategorie (keine Inhaltsseite).
- Verwendet ein repräsentatives Diagrammbild aus dem `assets/`-Ordner dieser Kategorie als Miniatur, formatiert mit der Standard-CSS-Karte (`background-color:#ffffff; border:1px solid #d3d3d3;` plus die gemeinsamen Größenregeln/Abstände, die sich bereits in der Datei befinden).
- Enthält den Kategorienamen (fett/stark) und eine Beschreibung in einem Satz, die mit dem Intro in der Kategorieübersicht übereinstimmt.

Wenn die Anzahl der Kategorien ein Vielfaches von 3 ist, wird die Tabelle als vollständige Zeilen gerendert (3-Spalten, `table-layout:fixed`, `width:33%` pro Zelle). Wenn es kein Vielfaches von 3 ist, fügen Sie in der letzten Zeile einen leeren `<td>` pro fehlendem Slot hinzu (lassen Sie die Tabelle nicht zerlegt/unformatiert).
