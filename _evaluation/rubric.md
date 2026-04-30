---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---
# Blueprint-Bewertungsthema

Diese Rubrik wird auf alle Dokumente im Abschnitt „Architekturdiagramme und Blueprints“ angewendet
von [TOC.md](../help/blueprints/TOC.md) (Zeilen 76-133), um zu empfehlen, ob jede Blueprint eine
**Anwendungsfallmuster**, ein **Architekturdiagramm**, beide (**Aufspaltung**) oder als gekennzeichnet
**Duplizieren** eines vorhandenen Musters.

Die Ausgabe der Anwendung dieser Rubrik ist [blueprint-audit.md](blueprint-audit.md).

## Definitionen

- **Anwendungsfallmuster** — ein Dokument, das ein bestimmtes geschäftliches oder technisches Ziel beschreibt, und
mögliche Ansätze und Überlegungen zur Umsetzung darzulegen, um dieses Ziel zu erreichen;
Kanonische Form: `.claude/skills/use-case-pattern-builder/references/pattern-template.md`.
- **Architekturdiagramm** - Ein visuelles Diagramm, das die Funktionalität eines Systems darstellt, das
-Integrationen und Datenflüsse. Minimale Erzählung; das Diagramm ist das Artefakt.
Kanonisches Beispiel: [platform-data-flow.md](../help/blueprints/experience-platform/platform-data-flow.md).

## Scoring

Jeder Blueprint wird durchgehend gelesen und mit acht binären Signalen bewertet. Jedes Signal trägt bei
+1 auf entweder den Musterwert oder den Diagrammwert.

### Mustersignale (jedes = +1 Muster)

1. **Business Objective Framing** - Frames für Umsatz, Kundenbindung, Akquise, Lead-Generierung, Kosten
Reduzierung, Kundenerlebnis oder ähnliche Geschäftsergebnisse.
2. **KPIs oder Erfolgsmetriken** - Benennt Metriken, Konversionsraten, Übereinstimmungsraten, ROI oder
Ähnliche Ergebniskennzahlen.
3. **Mehrere Implementierungsoptionen oder Laufzeitstufen** — präsentiert Option A / Option B, Standard vs.
Erweiterte oder vergleichbare Alternativen, zwischen denen der Leser wählen kann.
4. **Checkliste „Voraussetzungen oder Bereitschaft** - Listet auf, was vor der Implementierung vorhanden sein muss.
5. **Erzählende Implementierungsschritte > ~30 Zeilen** — inhaltliche Anleitungen zur Implementierung, nicht
Nur ein kurzer Überblick.

### Diagrammsignale (je = +1 Diagramm)

&#x200B;6. **Architektur/Datenflussbild vorhanden** — `.svg`, `.png` oder `.jpg` mit Systemtopologie,
Datenfluss oder Integrationspfeile.
&#x200B;7. **Topologie der System-zu-System-Integration, Bereitstellungsform oder Leitplanken** - beschreibt, wie
Verbindungen zwischen Komponenten, in denen Daten leben, Bereitstellungsmodelle (Edge vs. Hub) oder Kapazitätsbeschränkungen.
&#x200B;8. **Zielgruppe sind Lösungsarchitekten** - Framing verwendet Bereitstellung, SDK, Edge, Hub oder Ähnliches
Architektenorientierte Terminologie statt marketerorientierter Framing (Kampagnen, Journey,
Zielgruppen).

## Empfehlungslogik

Überschreiben Sie Regeln zuerst. Wenn keine Überschreibung erfolgt, leiten Sie die Empfehlung aus den Bewertungen ab.

### Regeln überschreiben (höchste Priorität)

1. **Die Datei heißt`overview.md`** → Recommendation = `Navigation`. von der Migration ausgeschlossen;
Eine Seite ist eine Landingpage im Stil eines Inhaltsverzeichnisses, die nach dem Ausgleichen der untergeordneten Dateien überarbeitet wird.
2. **Ein entsprechendes Muster ist bereits in`help/blueprints/use-case-patterns/`** → vorhanden
Empfehlung = `Duplicate`. Die Migrationsaktion dient dazu, den Blueprint auf eine reine
Architekturdiagramm und fügen Sie einen Querlink „Anwendungsfallmuster“ zum vorhandenen Muster hinzu.
Zeichnen Sie den vorhandenen Musterpfad in der Spalte `duplicate_of` auf.
3. **Datei ist in `experience-platform/` und hat kein Business Objective Signal (#1)** →
   `Diagram` unabhängig von anderen Scores. Dieser Ordner ist die Architekturübersichtsebene.

### Bewertungsbasierte Empfehlung (wenn keine Überschreibung ausgelöst wird)

| Punktzahl für Muster | Diagrammbewertung | Empfehlung | Überlegung |
| --- | --- | --- | --- |
| ≥ 3 | ≤ 1 | `Pattern` | Starke Mustersignale, schwache Diagrammsignale → zum Muster migrieren. |
| ≤ 1 | ≥ 2 | `Diagram` | Schwache Mustersignale, dominanter visueller/topologischer Fokus → als Diagramm beibehalten. |
| ≥ 3 | ≥ 2 | `Split` | Sowohl Rich-Muster-Inhalte als auch ein aussagekräftiges Diagramm extrahieren → Muster, reduzieren das Original auf Diagramm, vernetzen. |
| 2 | 2 | `Split` | Die Krawatte ist mäßig stark → gespalten. |
| 2 | ≤ 1 | `Pattern` | Musterleerung, kein signifikanter Diagrammwert. |
| ≤ 1 | ≤ 1 | `Diagram` | Thin Overall - wahrscheinlich eine vorhandene Seite mit minimaler Architektur. |

## Anwenden der Rubrik

Für jede Blueprint-Markdown-Datei im Umfang:

1. Lesen Sie die vollständige Datei von Anfang bis Ende.
2. Markieren Sie jedes der acht vorhandenen/nicht vorhandenen Signale.
3. Überschreiben Sie die Regeln in der richtigen Reihenfolge. Wenn man schießt, ist das die Empfehlung.
4. Andernfalls werden Musterwert und Diagrammwert berechnet und die Empfehlung nachgeschlagen.
5. Für `Pattern` und `Split` Empfehlungen schlagen Sie vor:
   - `proposed_pattern_category` — eines von:
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`, `conversational-experience` oder eine neue Kategorie mit der Bezeichnung `(new) <name>`.
   - `proposed_pattern_title` — Ein kurzer, aktionsorientierter Titel, der dem bestehenden Muster folgt
Benennungsstil
6. Für `Diagram` und `Split` Empfehlungen schlagen Sie vor:
   - `proposed_diagram_title` - Normalerweise der bestehende Titel, der beim Business-Framing gekürzt wurde.
7. Erfassen Sie alle Duplikate, die gefunden werden, indem Sie den Umfang des Blueprints mit dem vorhandenen Musterkatalog vergleichen
in `duplicate_of`.
8. Notieren Sie offene Fragen, einzigartige technische Inhalte, die beibehalten werden sollten, oder Migrationsrisiken in `notes`.

## Musterkatalog für vorhandene Anwendungsfälle (zur Erkennung von Duplikaten)

| Kategorie | Muster |
| --- | --- |
| audience-building-activation | Audience-Activation-to-destinations, Audience-Collaboration-Segment-Match, B2B-Audience-Activation, Ereignisweiterleitung |
| Personalisierung | anonymous-visitor-web-personalization, known-visitor-web-app-personalization, offer-decisioning, behavior-recommendation |
| campaign-management-orchestration | batch-outbound-message-activation, event-trigger-messaging, multi-step-orchestered-Journey, cross-channel-Journey-with-decisioning, purchase-group-based-marketing |
| Analyse | customer-analytics-insight-generation, b2b-analytics |
| Dialogerlebnis | brand-concierge-conversion-experience |
