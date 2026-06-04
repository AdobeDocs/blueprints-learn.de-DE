---
name: architecture-diagram-page-builder
description: 'Handbuch zur Erstellung neuer Architekturdiagrammseiten für das Adobe Experience Platform Blueprints-Repository. Verwenden Sie diese Fähigkeit, wenn Sie ein neues Architekturdiagramm der obersten Ebene, eine Seite zur Integrationsarchitektur oder eine Übersicht über die Anwendungsarchitektur hinzufügen. Architekturseiten behandeln AEP- und Anwendungsarchitekturen der obersten Ebene und primäre Integrationspunkte - keine detaillierten Anwendungsfälle (diese gehören zum Anwendungsfall-Muster-Builder). Übernimmt den gesamten Workflow: das Erfassen von Seiteninformationen, das Generieren der Markdown-Datei, das Platzieren im richtigen Themenordner und das Aktualisieren von TOC.md.'
source-git-commit: 4d236750286c28a8b8eb53a5bdec0645cc0e3e91
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 1%

---


# Architekturdiagramm für Page Builder

Diese Kenntnisse leiten die Erstellung neuer Architekturdiagrammseiten für das Adobe Experience Platform Blueprints-Repository. Architekturdiagrammseiten bieten visuelle Verweise auf höchster Ebene dafür, wie AEP- und Adobe-Anwendungen zusammenpassen, welche primären Datenflüsse zwischen ihnen fließen und welche Integrationspunkte Autorinnen und Autoren beim Entwerfen von Lösungen beachten müssen.

## Umfang

Architekturdiagrammseiten sind **fokussierte Seiten im Referenzstil** - in der Regel 40-100 Markdown-Zeilen -, die Folgendes enthalten:

- Ein oder mehrere Architekturdiagramme mit kurzen Erläuterungen zum Zweck jedes Diagramms
- Links zu Anwendungsfallmustern, die die Architektur unterstützt (die Architekturseite dupliziert diesen Inhalt nicht)
- Eine kurze Liste der primären Datenflüsse und Integrationspunkte (Abbildung)
- Links zu Experience League für weitere Informationen zur Anwendungs-Domain

Sie sind **nicht** der Ort für ausführliche Anwendungsfallinhalte. KPIs, Geschäftsziele, taktische Anwendungsfallbeispiele, Funktionen und persönliche Erzählungen gehören stattdessen zu den Seiten mit Anwendungsfallmustern - die über die `use-case-pattern-builder` Kenntnisse generiert werden. Siehe `references/scope-guardrails.md` für die vollständigen Leitplanken.

## Pflichtlektüre vor dem Start

Lesen Sie die folgenden Referenzdateien für Vorlagen und Regeln:

- `references/diagram-template.md` - Die vollständige Markdown-Vorlage mit Platzhalterwerten
- `references/toc-placement.md` — die Unterabschnitt-Zuordnungstabelle und das Eintragsformat für TOC.md
- `references/scope-guardrails.md` - Regeln dafür, was auf eine Architekturseite im Vergleich zu einer Anwendungsfall-Musterseite gehört

## Phase 1: Informationssammlung

**Formulare verwenden, kein lineares Interview.** Sammeln Sie alle erforderlichen Informationen, indem Sie `AskUserQuestion` Formulare in logischen Runden in Batches präsentieren, anstatt jeweils nur eine Frage zu stellen. Dadurch bleibt das Erlebnis für den Benutzer schnell und überschaubar.

### AskUserQuestion-Einschränkungen

- Maximal **4 Fragen** pro `AskUserQuestion`.
- Maximal **4 Optionen** pro Frage
- Wenn eine Frage mehr als vier plausible Optionen hat, teilen Sie sie auf zwei Aufrufe auf (stellen Sie z. B. die ersten vier Optionen und folgen Sie dann mit einem Ja/Nein beim fünften).
- Verwenden Sie `multiSelect: true` für Fragen, für die mehrere Antworten zutreffen (Lösungen, Muster, Datenflüsse).

### Runde 1 - Core-Seiteninformationen (ein AskUserQuestion-Aufruf, bis zu 4 Fragen)

Fordern Sie alles Folgende in einem einzigen Formular an:

1. **Seitentitel** - 2-3 Variantenvorschläge, abgeleitet von dem, was der Benutzer Ihnen bereits gesagt hat, plus eine „Sonstige“ Notluke.
2. **Themenordner** - präsentieren Sie die 5 gültigen Ordner als Optionen; empfehlen Sie den wahrscheinlichsten Ordner basierend auf der Eingabe des Benutzers.
3. **Adobe-Lösungen** - Mehrfachauswahl; schlägt je nach Thema der Seite die wahrscheinlichsten Kandidaten vor.
4. **Diagrammanzahl** - Wie viele Diagramme wird die Seite enthalten (1 / 2 / 3 / 4+).

### Runde 2 — Diagrammdetails (ein AskUserQuestion-Aufruf, bis zu 4 Fragen)

Fragen Sie nach dem Dateinamen des Diagramms und dem Zweck der Seite in einem Formular:

- Stellen Sie für jedes Diagramm (bis zu 2 in einer Formularrunde) die Frage **Bilddateiname** als Frage mit 2-3 vorgeschlagenen Dateinamen (abgeleitet vom Seitentitel) plus einer „Sonstige“-Option.
- Stellen Sie die Frage **Zweck der Seite** (Beschreibung in 1-2 Sätzen) als Frage mit 2-3 vorgeschlagenen Formulierungen plus „Sonstige“.
- Frage, ob ein **`>[!MORELIKETHIS]`-** benötigt wird (Ja/Nein). Wenn ja, erfassen Sie die URL und den Link-Text in einer Folgenachricht.

> **Abschnittstitel und Alternativtext:** Wenn der Dateiname des Bildes beschreibend ist (z. B. `fac-architecture.svg`, `fac-dataflow.svg`), leiten Sie den H2-Abschnittstitel und den Alternativtext daraus ab - Sie müssen den Benutzer nicht fragen. Verwenden Sie den Dateinamenstamm, der großgeschrieben und humanisiert ist, als Abschnittstitel (z. B. `Architecture diagram`, `Data flow diagram`). Fragen Sie nur, ob der Dateiname mehrdeutig ist.

### Runde 3 - Anwendungsfallmuster (Frage nach dem Scannen stellen)

Bevor Sie dieses Formular **,`/help/blueprints/use-case-patterns/`** und identifizieren Sie 3-5 wahrscheinliche übereinstimmende Muster basierend auf dem Seitentitel, dem Zweck und den Lösungen. Vergewissern Sie sich, dass jede Datei vorhanden ist, bevor Sie sie vorschlagen.

Stellen Sie die vier besten Kandidaten als `multiSelect` Frage vor. Wenn es einen starken fünften Kandidaten gibt, folgen Sie mit einem separaten Ja/Nein-Frage für diesen. Laden Sie den Benutzer auch ein, ein Muster zu benennen, das Sie verpasst haben.

Nur Muster einschließen, deren Vorhandensein bestätigt wird. Musternamen nicht halluzinieren.

### Runde 4 - Datenflüsse und Experience League-Links (ein AskUserQuestion-Aufruf)

**Datenflüsse:** Sie 3-5 vorab geschriebene Aufzählungszeichen für den Datenfluss als `multiSelect` Frage vor (abgeleitet aus dem Seitenthema). Der Benutzer wählt aus, welches zutrifft. Behalten Sie jede Option für einen kurzen Satz bei. Wenn der/die Benutzende benutzerdefinierte Flüsse benötigt, die nicht in Ihrer Liste enthalten sind, kann er/sie diese in einer Nachverfolgung bereitstellen.

**Experience League-Links:** Stellen Sie nach dem Formular eine Markdown-Tabelle mit 4-6 vorgeschlagenen Links mit Artikeltitel, URL und einer einzeiligen Begründung vor. Markieren Sie jede URL als **nicht verifiziert**. Bitten Sie den Benutzer, (a) zu akzeptieren, (b) durch eine verifizierte URL zu ersetzen oder (c) eine eigene hinzuzufügen. Verwenden Sie eine `AskUserQuestion` mit bis zu vier Optionen, wenn die Liste lang ist. Andernfalls akzeptieren Sie die Bestätigung im Klartext.

Erfinde nie URLs, die du nicht abgerufen hast. Wenn Sie unsicher sind, schlagen Sie den Artikeltitel vor und lassen Sie den Benutzer die URL angeben.

### Wenn alle Runden abgeschlossen sind

Bestätigen Sie den vollständigen Informationssatz mit dem Benutzer, bevor Sie Dateien generieren. Wenn ein erforderliches Element immer noch fehlt oder als „Sonstige“ ohne Wert markiert ist, fragen Sie danach, bevor Sie fortfahren. Erstellen Sie keine Diagramme, Muster oder Links.

## Phase 2: Überprüfung des Umfangs

Lesen Sie vor dem Generieren die Diagrammbeschreibungen der Benutzenden, Datenflussaufzählungszeichen und alle Entwurfsprosa erneut. Wenden Sie die Leitplanken über `references/scope-guardrails.md` an.

Wenn einer der folgenden Punkte im geplanten Inhalt angezeigt wird, warnen Sie den Benutzer und bieten Sie an, diesen Abschnitt zu einer Anwendungsfall-Musterseite umzuleiten (oder ihn von der Architekturseite aus zu kürzen):

- KPIs oder Messformeln
- Geschäftsziele oder Narrative zu Geschäftsauswirkungen
- Taktische Anwendungsfälle (spezifische Personalisierungsszenarien, Kampagnenbeispiele usw.)
- Funktionen (`A > B > C > D`)
- Personalisierte storytelling

Wenn der geplante Inhalt im architekturspezifischen Seitenbereich bleibt (Architektur der obersten Ebene, Systemdatenfluss, Integrationspunkte, Bereitstellungstopologie, Edge vs. Hub), bestätigen Sie dies mit dem Benutzer und fahren Sie mit Phase 3 fort.

## Phase 3: Inhaltserstellung

Erstellen Sie die Seite unter:

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

Verwenden Sie `references/diagram-template.md` als Quellvorlage. Füllen Sie alle Platzhalterwerte mit den erfassten Informationen aus. Die generierte Datei muss Folgendes enthalten:

1. **YAML-**: `title`, `description`, `solution`.
   - **`exl-id`** NICHT einschließen - Die Veröffentlichungs-Pipeline weist sie automatisch zu.
   - **UMFASST NICHT** `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` oder `thumbnail` — diese werden ebenfalls automatisch ausgefüllt.

2. **H1 Überschrift** - der Seitentitel.

3. **Eröffnungsabsatz** - 1-2 Sätze, abgeleitet von der seitenbezogenen Eingabe.

4. **Optionaler `>[!MORELIKETHIS]`-Block** - nur, wenn der Benutzer einen Link mit verwandten Inhalten bereitgestellt hat.

5. **Ein H2-Abschnitt pro Diagramm** — in der Reihenfolge, in der sie vom Benutzer angegeben wurden. Jeder Abschnitt enthält:
   - Der Abschnittstitel als Überschrift H2
   - 1-2 Sätze, die den Zweck des Diagramms erklären
   - Die Bildeinbettung erfolgt gemäß der Standardkonvention:

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** — Aufzählungsliste. Jede Aufzählung:

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** — Aufzählungsliste mit 3-7 Fluss-/Integrationselementen.

8. **`## Further reading`** - Aufzählungsliste der Experience League-Links:

   ```
   - [{Article title}]({Experience League URL})
   ```

Verwenden Sie `[!DNL ...]` Syntax für Adobe-Produktnamen in Textkörpern und Aufzählungszeichen, die der Konvention bestehender Seiten entsprechen.

## Phase 4: Querverweis-Updates

Aktualisieren Sie **`/help/blueprints/TOC.md`** , um die neue Seite zur Navigation hinzuzufügen. Dies ist die einzige Querverweisseite, die aktualisiert wird.

Lesen Sie `references/toc-placement.md` für die vollständige Unterabschnitt-Zuordnungstabelle und die Regeln. Zusammenfassung:

| Themenordner | Inhaltsverzeichnis-Unterabschnitt |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` (Unterabschnitt „Architekturübersichten„) |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

Eingabeformat (4-Leerzeichen-Einzug + `+`):

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

Hängen Sie den neuen Eintrag als letztes Element im entsprechenden Unterabschnitt an, es sei denn, der Benutzer gibt eine andere Position an. Bewahren Sie die exakte Einrückung mit vier Leerzeichen auf - die Analyse des Inhaltsverzeichnisses hängt davon ab.

**Prüfen Sie vor der Platzierung auf verschachtelte Untergruppen.** Einige Unterabschnitte (insbesondere `Audience & Profile Activation`) enthalten verschachtelte Gruppierungen (z. B. `Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}`). Lesen Sie den betroffenen Unterabschnitt von toc.md vor der Bearbeitung. Neue Architekturseiten der obersten Ebene gehören zur Ebene des Einzugs mit vier Leerzeichen des Unterabschnitts - **nicht** innerhalb einer verschachtelten Untergruppe (die den Einzug mit sechs Leerzeichen verwendet). Platzieren Sie den neuen Eintrag nach dem letzten verschachtelten Untergruppeneintrag und vor der nächsten Überschrift des Unterabschnitts der obersten Ebene.

## Phase 5: Validierung

Nachdem alle Dateien erstellt und aktualisiert wurden, überprüfen Sie Folgendes und melden Sie dem Benutzer etwaige Fehler:

1. **Vorhandensein von Bild-Assets** - Überprüfen Sie für jedes Diagramm, ob `/help/blueprints/{topic-folder}/assets/{filename}` vorhanden ist. **Warn** wenn fehlt; nicht blockieren (der Benutzer erstellt möglicherweise parallel zum Diagrammdesign). Zeigen Sie eine klare Liste fehlender Dateien an, damit der Benutzer weiß, was hinzuzufügen ist.

2. **Verknüpfungen für Anwendungsfälle** - Jeder Musterlink in der Datei verweist auf eine vorhandene Markdown-Datei unter `/help/blueprints/use-case-patterns/`. Verwenden Sie `Read` oder Globus, um zu bestätigen, dass jedes Ziel vorhanden ist.

3. **Experience League-Links** - Überprüfen Sie vor Ort, ob jede URL im `## Further reading` mit `https://experienceleague.adobe.com/de` beginnt.

4. **TOC-**: Der neue Eintrag befindet sich im richtigen Unterabschnitt, verwendet eine Einrückung mit vier Leerzeichen und der Pfad stimmt genau mit dem Speicherort der generierten Datei überein.

5. **Dateibenennung** - Der Dateiname der Seite ist kebab-case und entspricht dem Pfad, auf den in TOC.md verwiesen wird.

6. **Vollständigkeit von** - Die Seite enthält `title`, `description` und `solution`. Sie darf **nicht** `exl-id`, `product_v2`, `feature_v2`, `role_v2`, `topic_v2`, `TQID`, `kt` oder `thumbnail` umfassen.

Beheben Sie etwaige Validierungsprobleme, bevor Sie die Aufgabe als abgeschlossen betrachten.

## Notizen

- Verwenden Sie immer `[!DNL ...]` Syntax für Adobe-Produktnamen im Textkörper und in Aufzählungszeichen, entsprechend der Konvention vorhandener Seiten.
- Architekturdiagramme sind in der Regel SVG (bevorzugt für Schärfe und Skalierung), PNG ist jedoch für Rasterquellen-Grafiken akzeptabel.
- Die `<img>`-Einbettungs-Inline-Styling-Zeichenfolge (`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`) und die `class="modal-image"` sind erforderlich - sie ermöglichen die Experience League-Interaktion mit modalem Zoom.
- Wenn der/die Benutzende eine Seite für einen brandneuen Themenordner erstellt, der noch nicht vorhanden ist, warnt er/sie, dass TOC.md einen neuen Unterabschnitt auf oberster Ebene unter `+ Architecture Diagrams and Blueprints{#architecture-diagrams}` benötigt. Behandeln Sie dies als separaten Schritt mit der expliziten Genehmigung des Benutzers.
- Wenn das Architekturdiagramm einen *-Anwendungsfall vollständig dokumentiert (mit*, Geschäftszielen, Funktionen), leiten Sie den Benutzer zu `use-case-pattern-builder` weiter - dies ist keine Architekturseite.
