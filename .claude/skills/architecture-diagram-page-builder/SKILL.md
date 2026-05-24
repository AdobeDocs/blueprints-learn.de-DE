---
name: architecture-diagram-page-builder
description: 'Handbuch zur Erstellung neuer Architekturdiagrammseiten für das Adobe Experience Platform Blueprints-Repository. Verwenden Sie diese Fähigkeit, wenn Sie ein neues Architekturdiagramm der obersten Ebene, eine Seite zur Integrationsarchitektur oder eine Übersicht über die Anwendungsarchitektur hinzufügen. Architekturseiten behandeln AEP- und Anwendungsarchitekturen der obersten Ebene und primäre Integrationspunkte - keine detaillierten Anwendungsfälle (diese gehören zum Anwendungsfall-Muster-Builder). Übernimmt den gesamten Workflow: das Erfassen von Seiteninformationen, das Generieren der Markdown-Datei, das Platzieren im richtigen Themenordner und das Aktualisieren von TOC.md.'
source-git-commit: e79d9d6490e4f50c4611dd879b53f0e63a90cd65
workflow-type: tm+mt
source-wordcount: '1393'
ht-degree: 2%

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

Befragen Sie den Benutzer, um alle erforderlichen Informationen zu sammeln, bevor Sie Dateien generieren. Fahren Sie mit der Inhaltserstellung erst fort, wenn jedes erforderliche Element bereitgestellt oder explizit zurückgestellt wird.

### Erforderliche Informationen

1. **Seitentitel** - Der für Menschen lesbare Titel (z. B. `Adobe Journey Optimizer architecture diagrams`).

2. **Themenordner** - Wo die Seite lebt. Wählen Sie genau eine aus, die auf der primären Domain des Diagramms basiert:
   - `experience-platform/` - AEP auf oberster Ebene, Multi-App- oder Platform-Diagramme
   - `customer-journeys/` - AJO, Campaign, Journey-Orchestrierung
   - `customer-journey-analytics/` - CJA-Architekturen
   - `audience-activation/` - RTCDP, Audience und Profilaktivierung
   - `b2b/` - B2B-spezifische Architekturen

3. **Dateiname** — Groß-/Kleinschreibung, abgeleitet vom Seitentitel (z. B. `Journey Optimizer architecture` -> `journey-optimizer-architecture.md`). Bestätigen Sie mit dem Benutzer.

4. **Zweck der Seite** - 1-2 Sätze, die beschreiben, was die Diagramme zusammen veranschaulichen. Wird für das Feld &quot;`description`&quot; und den ersten Absatz verwendet.

5. **Adobe-Lösungen** - Eine kommagetrennte Liste von Adobe-Produkten, die zentral auf der Seite sind. Wird für das Feld &quot;`solution` frontmatter“ verwendet. Beispiele: `Experience Platform, Journey Optimizer, Customer Journey Analytics`.

6. **Diagramme** - Ein oder mehrere Diagramme. Für jedes Diagramm erfassen Sie:
   - **Bilddateiname** (z. B. `aep_data_flow.svg`). SVG bevorzugt; PNG akzeptabel.
   - **Abschnittstitel** - wird zur H2-Überschrift für das Diagramm (z. B. `Data flow diagram`, `Detailed architecture diagram`).
   - **Zweckerklärung** - 1-2 Sätze, die beschreiben, was das Diagramm zeigt.
   - **Alt-Text** — kurze barrierefreie Beschreibung.

7. **Anwendungsfallmuster werden unterstützt** - 2-5 vorhandene Muster, die diese Architektur ermöglicht.

   **Empfehlen Sie Kandidaten zuerst.** Bevor Sie den Benutzer auffordern, Muster anzugeben, scannen Sie `/help/blueprints/use-case-patterns/` und schlagen Sie 3-6 mögliche Übereinstimmungen vor, die auf dem Seitentitel, dem Seitenzweck und den oben erfassten Adobe-Lösungen basieren. Geben Sie für jeden Vorschlag Folgendes an:
   - Mustername (mit verknüpftem Pfad)
   - Ein Satz, der erklärt, warum es zu dieser Architektur passt

   Zeigen Sie die Vorschläge als nummerierte Auswahlliste an und bitten Sie den Benutzer, (a) alle zu akzeptieren, (b) alle zu verwerfen und (c) verpasste Muster hinzuzufügen. Generieren Sie nur Vorschläge, die auf echte -Dateien verweisen - glob/read zur Bestätigung vor dem Vorschlag. Musternamen nicht halluzinieren.

   Erfassen Sie für jedes akzeptierte Muster die Kategorie und den Dateinamen. Überprüfen Sie vor dem Generieren, ob jede Datei unter `/help/blueprints/use-case-patterns/{category}/{pattern-file}.md` vorhanden ist.

8. **Primäre Datenflüsse/Integrationspunkte** — 3-7 Aufzählungszeichen, die wichtige Flüsse und Integrationsgrenzen beschreiben, die in den Diagrammen angezeigt werden (z. B. `Real-time event ingestion from Web SDK to Edge Network`, `Profile synchronization between Experience Platform Hub and Edge`).

9. **Experience League-Links** - 3-6 Links zu relevanten Experience League-Dokumentationen, die Sie weiter lesen können. Jede muss mit `https://experienceleague.adobe.com/` beginnen.

   **Empfehlen Sie Kandidaten zuerst.** Basierend auf den Adobe-Lösungen und dem Seitenzweck schlagen Sie vier bis acht plausible Experience League-Artikel vor (z. B. die kanonischen Landingpages oder Übersichtsseiten für jede benannte Lösung, wichtige Integrationshandbücher, Bereitstellungsreferenzen). Geben Sie für jeden Vorschlag Folgendes an:
   - Artikeltitel
   - URL
   - Einzeilige Begründung, warum es auf die Seite passt

   Markieren Sie **Vorschläge als**, es sei denn, Sie haben die URL tatsächlich abgerufen - der Benutzer muss jeden bestätigen oder ersetzen, bevor er in die generierte Datei gelangt. Bitten Sie den Benutzer, (a) zu akzeptieren, (b) jede URL durch eine verifizierte zu ersetzen, die er bereits hat, und (c) seine eigene hinzuzufügen. Erfinden Sie niemals URLs, die Sie nicht gesehen haben. Wenn Sie unsicher sind, schlagen Sie den Artikeltitel vor und lassen Sie den Benutzer die URL angeben.

### optional

- **Callout für verwandte Inhalte** - Ein einzelner Link, der oben auf der Seite als `>[!MORELIKETHIS]` Block dargestellt wird. Nützlich, wenn es ein Handbuch zur gleichrangigen Integration oder Konfiguration auf Experience League gibt, das der Leser kennen sollte.

Wenn der Benutzer nicht alle erforderlichen Elemente bereitstellt, fragen Sie nach den fehlenden Elementen, bevor Sie fortfahren. Erstellen Sie keine Diagramme, Muster oder Links.

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

## Phase 5: Validierung

Nachdem alle Dateien erstellt und aktualisiert wurden, überprüfen Sie Folgendes und melden Sie dem Benutzer etwaige Fehler:

1. **Vorhandensein von Bild-Assets** - Überprüfen Sie für jedes Diagramm, ob `/help/blueprints/{topic-folder}/assets/{filename}` vorhanden ist. **Warn** wenn fehlt; nicht blockieren (der Benutzer erstellt möglicherweise parallel zum Diagrammdesign). Zeigen Sie eine klare Liste fehlender Dateien an, damit der Benutzer weiß, was hinzuzufügen ist.

2. **Verknüpfungen für Anwendungsfälle** - Jeder Musterlink in der Datei verweist auf eine vorhandene Markdown-Datei unter `/help/blueprints/use-case-patterns/`. Verwenden Sie `Read` oder Globus, um zu bestätigen, dass jedes Ziel vorhanden ist.

3. **Experience League-Links** - Überprüfen Sie vor Ort, ob jede URL im `## Further reading` mit `https://experienceleague.adobe.com/` beginnt.

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
