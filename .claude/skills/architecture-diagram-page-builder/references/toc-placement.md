---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---
# TOC.md-Platzierungsreferenz

Wenn die Kenntnis eine neue Architekturdiagrammseite generiert, muss sie einen Eintrag zu `/help/blueprints/TOC.md` hinzufügen, damit die Seite in der Site-Navigation auffindbar ist. Dieses Dokument definiert genau, wo und wie dieser Eintrag geht.

## Übergeordneter Abschnitt

Alle Seiten des Architekturdiagramms sind im Abschnitt `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` der obersten Ebene in TOC.md verfügbar. In diesem Abschnitt werden Seiten in mehreren Unterabschnitten nach Thema gruppiert.

## Unterabschnitt-Zuordnung

Wählen Sie den Unterabschnitt aus, der dem Themenordner der neuen Seite entspricht:

| Themenordner | Überschrift Unterabschnitt Inhaltsverzeichnis |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (ein innerhalb von `Architecture overviews` verschachtelter Unterabschnitt) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

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

`+ Architecture overviews{#architecture-overview}` enthält einen verschachtelten `+ Deployment{#deployment}` für SDK-Seiten. Wenn sich die neue Seite unter `experience-platform/deployment/` befindet, platzieren Sie den Eintrag in `Deployment` mit **sechs** Einzügen:

```
      + [{Page title}](/help/blueprints/experience-platform/deployment/{filename}.md)
```

Andere Unterabschnitte (`Audience & Profile Activation`, `B2B activation & marketing` usw.) Kann auch verschachtelte Gruppierungen enthalten - Überprüfen Sie den Abschnitt, bevor Sie den Eintrag platzieren. Wenn eine verschachtelte Gruppierung vorhanden ist und die neue Seite dazu gehört, ziehen Sie zwei zusätzliche Leerzeichen ein. Andernfalls platzieren Sie den Eintrag auf der obersten Ebene des Unterabschnitts.

## Beispiele für Bearbeitung

### Beispiel 1: AEP-Seite der obersten Ebene

- Themenordner: `experience-platform/`
- Dateiname: `mix-modeler-integration.md`
- Seitentitel: `Adobe Mix Modeler integration with Experience Platform`

Eintritt:

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/experience-platform/mix-modeler-integration.md)
```

Platziert unter `+ Architecture overviews{#architecture-overview}`.

### Beispiel 2 - AJO Journey-Architektur

- Themenordner: `customer-journeys/`
- Dateiname: `cross-channel-journey-architecture.md`
- Seitentitel: `Cross-channel journey architecture`

Eintritt:

```
    + [Cross-channel journey architecture](/help/blueprints/customer-journeys/cross-channel-journey-architecture.md)
```

Platziert unter `+ Customer journeys{#customer-journeys}`.

### Beispiel 3: Seite &quot;SDK-Bereitstellung“

- Themenordner: `experience-platform/deployment/`
- Dateiname: `mobile-sdk-architecture.md`
- Seitentitel: `Mobile SDK deployment architecture`

Eingabe (beachten Sie den sechseckigen Einzug):

```
      + [Mobile SDK deployment architecture](/help/blueprints/experience-platform/deployment/mobile-sdk-architecture.md)
```

Platziert unter `+ Deployment{#deployment}` in `+ Architecture overviews{#architecture-overview}`.

## Verifizierung

Lesen Sie nach der Bearbeitung von TOC.md den betroffenen Unterabschnitt erneut durch und bestätigen Sie:

1. Der neue Eintrag verwendet genau vier Leerzeichen (oder sechs, wenn unter `Deployment` verschachtelt).
2. Das Link-Ziel stimmt mit dem Dateipfad auf der Festplatte überein - einschließlich der `.md`.
3. Der Eintrag ist innerhalb des richtigen Unterabschnitts gruppiert - er kann nicht zwischen Unterabschnitten verschoben werden.
4. Es wurden keine vorhandenen Einträge neu angeordnet oder geändert.
