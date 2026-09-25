---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%
---
# TOC.md-Platzierungsreferenz

Wenn die Kenntnis eine neue Architekturdiagrammseite generiert, muss sie einen Eintrag zu `/help/blueprints/TOC.md` hinzufügen, damit die Seite in der Site-Navigation auffindbar ist. Dieses Dokument definiert genau, wo und wie dieser Eintrag geht.

## Übergeordneter Abschnitt

Alle Seiten des Architekturdiagramms sind im Abschnitt `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` der obersten Ebene in TOC.md verfügbar. In diesem Abschnitt werden Seiten in mehreren Unterabschnitten nach Thema gruppiert.

Ordnernamen, Inhaltsverzeichnisanker und Inhaltsverzeichnisbeschriftungen für diese Unterabschnitte müssen der Benennungsregel in `../../architecture-diagram-category-builder/references/naming-conventions.md` entsprechen. Sehen Sie sich diese Datei an, wenn Sie jemals eine neue Kategorie benötigen (verwenden Sie dazu die `architecture-diagram-category-builder` Kenntnisse, nicht diese).

## Unterabschnitt-Zuordnung

Wählen Sie den Unterabschnitt aus, der dem Themenordner der neuen Seite entspricht:

| Themenordner | Überschrift Unterabschnitt Inhaltsverzeichnis |
| --- | --- |
| `architecture-diagrams/architecture-overviews/` | `+ Architecture overviews{#architecture-overviews}` |
| `architecture-diagrams/audience-profile-activation/` | `+ Audience & Profile Activation{#audience-profile-activation}` |
| `architecture-diagrams/b2b-activation-marketing/` | `+ B2B activation & marketing{#b2b-activation-marketing}` |
| `architecture-diagrams/customer-insights/` | `+ Customer Insights{#customer-insights}` |
| `architecture-diagrams/customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Wenn der/die Benutzende einen Themenordner vorschlägt, der nicht in dieser Tabelle enthalten ist, behandeln Sie diesen als neuen Unterabschnitt auf oberster Ebene und halten Sie an - fragen Sie den/die Benutzende(n), ob er/sie ihn erstellen soll. Erfinden Sie keinen neuen Unterabschnitt im Hintergrund.

## Eingabeformat

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Regeln:

- **Einzug:** genau vier Leerzeichen, dann `+ `. Der Inhaltsverzeichnis-Parser hängt davon ab. Durch Registerkarten oder unterschiedliche Abstände wird die Navigation unterbrochen.
- **Link-Text:** den Seitentitel an, der genau mit der `title`-Schriftart übereinstimmt. `[!DNL ...]` nur verwenden, wenn vorhandene gleichrangige Elemente im selben Unterabschnitt ihn verwenden - entspricht der lokalen Konvention.
- **Verknüpfungsziel:** absoluter Pfad, der mit `/help/blueprints/` beginnt. Schließen Sie immer die `.md` Erweiterung ein.
- **Position:** wird als letzter Eintrag im entsprechenden Unterabschnitt angehängt, es sei denn, der Benutzer gibt eine andere Position an. Beibehalten der vorhandenen Reihenfolge aller gleichrangigen Einträge.

## Verschachtelte Unterabschnitte

`+ Architecture overviews{#architecture-overviews}` hat keine verschachtelten Gruppierungen. Alle Seiten unter `architecture-diagrams/architecture-overviews/` (einschließlich der SDK-Bereitstellungsseiten, z. B. `websdk.md`, `appsdk.md`) befinden sich auf derselben Einzugsebene mit vier Leerzeichen. Andere Unterabschnitte (`Audience & Profile Activation`, `B2B activation & marketing` usw.) Kann noch verschachtelte Gruppierungen enthalten - Überprüfen Sie den Abschnitt , bevor Sie den Eintrag platzieren. Wenn eine verschachtelte Gruppierung vorhanden ist und die neue Seite dazu gehört, ziehen Sie zwei zusätzliche Leerzeichen ein. Andernfalls platzieren Sie den Eintrag auf der obersten Ebene des Unterabschnitts.

## Beispiele für Bearbeitung

### Beispiel 1: AEP-Seite der obersten Ebene

- Themenordner: `architecture-diagrams/architecture-overviews/`
- Dateiname: `mix-modeler-integration.md`
- Seitentitel: `Adobe Mix Modeler integration with Experience Platform`

Eintritt:

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/architecture-diagrams/architecture-overviews/mix-modeler-integration.md)
```

Platziert unter `+ Architecture overviews{#architecture-overviews}`.

### Beispiel 2 - AJO Journey-Architektur

- Themenordner: `architecture-diagrams/customer-journeys/`
- Dateiname: `cross-channel-journey-architecture.md`
- Seitentitel: `Cross-channel journey architecture`

Eintritt:

```
    + [Cross-channel journey architecture](/help/blueprints/architecture-diagrams/customer-journeys/cross-channel-journey-architecture.md)
```

Platziert unter `+ Customer journeys{#customer-journeys}`.

### Beispiel 3: SDK-Bereitstellungsseite

- Themenordner: `architecture-diagrams/architecture-overviews/`
- Dateiname: `mobile-sdk-architecture.md`
- Seitentitel: `Mobile SDK deployment architecture`

Eintrag (gleicher vierzeiliger Einzug wie bei anderen Übersichtsseiten zur Architektur):

```
    + [Mobile SDK deployment architecture](/help/blueprints/architecture-diagrams/architecture-overviews/mobile-sdk-architecture.md)
```

Platziert unter `+ Architecture overviews{#architecture-overviews}`.

## Verifizierung

Lesen Sie nach der Bearbeitung von TOC.md den betroffenen Unterabschnitt erneut durch und bestätigen Sie:

1. Der neue Eintrag verwendet genau vier Leerzeichen im Einzug (oder sechs, wenn sie unter einer unterabschnittsspezifischen Gruppierung verschachtelt sind, z. B. der RTCDP-Gruppierung von `Audience & Profile Activation`).
2. Das Link-Ziel stimmt mit dem Dateipfad auf der Festplatte überein - einschließlich der `.md`.
3. Der Eintrag ist innerhalb des richtigen Unterabschnitts gruppiert - er kann nicht zwischen Unterabschnitten verschoben werden.
4. Es wurden keine vorhandenen Einträge neu angeordnet oder geändert.
