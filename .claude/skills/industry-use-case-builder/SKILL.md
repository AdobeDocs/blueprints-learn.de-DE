---
name: industry-use-case-builder
description: 'Anleitung zur Erstellung neuer branchenbezogener Anwendungsfälle für das Adobe Experience Platform Blueprints-Repository. Nutzen Sie diese Kenntnisse, wenn Sie einen neuen Anwendungsfall zu einer vertikalen Branche hinzufügen (Einzelhandel, Automobilindustrie, Gesundheitswesen, Finanzdienstleistungen, Versicherungen, Medien und Unterhaltung, Telekommunikation, Reisen und Gastgewerbe, B2B), wenn der/die Benutzende Geschäftsszenarien zu Branchenseiten hinzufügen möchte oder wenn er/sie den Anwendungsfallkatalog aktualisiert. Verarbeitet den gesamten Workflow: Erfassen von Anwendungsfalldetails, Bewerten des Reifegrads, Generieren von Inhalten, Aktualisieren der Branchen-Übersichtsseite und des Anwendungsfallkatalogs und Aufrufen der Anwendungsfall-Symbol-Generator-Fähigkeit zur Symbolerstellung.'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 1%

---


# Anwendungsfall-Builder für die Branche

Diese Fähigkeit leitet die Erstellung neuer branchenbezogener Anwendungsfälle für das Adobe Experience Platform Blueprints-Repository. Jede Phase der Reihe nach durchlaufen. Lesen Sie die Referenzdateien, bevor Sie beginnen:

- `references/use-case-template.md` - Exakte Vorlage für Anwendungsfall-Abschnitte
- `references/catalog-row-template.md` - Exaktes Format für Katalogtabellenzeilen
- `references/maturity-criteria.md` — Detaillierte Rubrik für die Laufzeitbewertung

## Phase 1: Informationssammlung

Führen Sie ein Interview mit dem Benutzer, um alle erforderlichen Details zu erfassen, bevor Sie Inhalte generieren.

### Erforderliche Felder

1. **Branche vertikal** — Muss eine der folgenden sein:
   - Automobil
   - B2B
   - Finanzdienstleistungen
   - Gesundheitswesen
   - Versicherung
   - Media-Entertainment
   - Einzelhandel
   - Telekommunikation
   - reisegastfreundschaft

2. **Name des Anwendungsfalls** - Ein klarer, beschreibender Titel (z. B. „E-Mail-Wiederherstellung bei Transaktionsabbruch“, „Kampagnen zur Einhaltung von Medikamenten„).

3. **Beschreibung** - 1-2 Sätze, die das Geschäftsszenario und seine Bedeutung beschreiben.

4. **Geschäftsauswirkungen** - Quantifizierte Ergebnisse mit bestimmten Metriken (z. B. „Anstieg der Klickraten um 20-30 %&quot;, „Verbesserung der Nachfüllraten um 15-25 %„).

5. **Anwendungsfallmuster** - Muss genau einem der folgenden vorhandenen Muster zugeordnet werden:
   - Audience Activation zu Zielen
   - Zielgruppen-Collaboration mit Segment Match
   - Ereignisweiterleitung
   - B2B-Audience Activation
   - Web-Personalization für anonyme Besucher
   - Web-/App-Personalization für bekannte Besucher
   - Offer Decisioning
   - Verhaltensempfehlung
   - Batch-Aktivierung ausgehender Nachrichten
   - Ereignisausgelöstes Messaging
   - Mehrstufige orchestrierte Journey
   - Cross-Channel-Journey mit Decisioning
   - Einkauf von gruppenbasiertem Marketing und Journey-Management
   - Generierung von Customer Analytics und Insight
   - B2B-Analyse
   - Brand Concierge - Gesprächserlebnis

6. **Technische Überlegungen** - 4-8 Aufzählungspunkte zu Datenanforderungen, Integrationen, Regulierungs-/Compliance-Anforderungen, Leistungsüberlegungen und Anmerkungen zur Architektur.

Vor dem Fortfahren nach fehlenden Feldern fragen. Gehen Sie keine Details von sich aus oder fertigen Sie sie nicht an.

## Phase 2: Reifegradbewertung

Lesen Sie `references/maturity-criteria.md` für die vollständige Rubrik. Einer von drei Reifegraden zuweisen:

- **Grundlegend** `[!BADGE Foundational]{type=Neutral}` - Einzelschritt- oder ereignisgesteuerte Muster (ereignisgesteuertes Messaging, Batch-Ausgang), unkomplizierte Datenanforderungen, minimale KI/ML, Standardintegrationen.
- **Emerging** `[!BADGE Emerging]{type=Informative}` - Mehrstufige Journey, Verhaltensdaten, Empfehlungsmodelle, Personalisierung bekannter Besucher, moderate Integrationskomplexität.
- **Erweitert** `[!BADGE Advanced]{type=Caution}` - Kanalübergreifende Entscheidungsfindung, KI-gestützte Prognose, Angebotsentscheidung, komplexe Orchestrierung, mehrere Systemintegrationen.

### Bewertungs-Workflow

1. Ermitteln Sie, welchem Anwendungsfallmuster der Anwendungsfall zugeordnet ist.
2. Überprüfen Sie die Liste „Typische Muster“ in den Reifekriterien auf eine schnelle Übereinstimmung.
3. Wenn das Muster keinen klaren Hinweis auf die Reife enthält, bewerten Sie die Datenkomplexität, die KI/ML-Anforderungen und den Integrationsbereich.
4. Übermitteln Sie die Bewertung dem Benutzer mit einer Begründung: „Aufgrund der Musterzuordnung ({pattern}) und der {key factors} würde ich dies {reasoning} als {level} klassifizieren.“
5. Warten Sie, bis der Benutzer dies bestätigt oder überschrieben hat, bevor Sie mit der Inhaltserstellung fortfahren.

## Phase 3: Inhaltserstellung

Inhalt in zwei Dateien generieren oder aktualisieren.

### A. Branchen-Übersichtsdatei

**Dateipfad:** `/help/blueprints/industry-use-cases/{industry}/{industry}-overview.md`

Lesen Sie zuerst die vorhandene Datei, um die aktuelle Struktur und den aktuellen Inhalt zu verstehen. Fügen Sie dann einen neuen Abschnitt hinzu, der der exakten Vorlage aus `references/use-case-template.md` folgt:

```markdown
## {Use Case Title}

{1-2 sentence description of the business scenario and why it matters}

### Business impact

{Quantified business outcomes, e.g., "Retailers typically see a 20-30% increase in click-through rates..."}

### How to implement

Use the [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) pattern. {1-2 sentence explanation of why this pattern applies}

### Technical considerations

- {4-8 bullet points covering data integration, regulatory, performance, or architectural considerations}
```

Platzieren Sie den neuen Abschnitt nach vorhandenen Anwendungsfallabschnitten, wobei die Formatierung konsistent bleibt.

### B. Anwendungsfallkatalog

**Dateipfad:** `/help/blueprints/industry-use-cases/use-case-catalog.md`

Lesen Sie zuerst die vorhandene Katalogdatei. Fügen Sie der richtigen Branchenregisterkarte eine neue Zeile hinzu. Der Katalog verwendet eine Struktur mit Registerkarten und `>[!TAB {Industry}]`. Jede Registerkarte enthält eine Tabelle mit diesen Spalten:

| Spalte | Inhalt |
| --- | --- |
| Symbol | `<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">` (leer lassen, wenn noch kein Symbol vorhanden ist) |
| Nutzungsszenario | `[{Use Case Title}]({industry}/{industry}-overview.md#{anchor})` Anker ist die Überschrift im Kebab-Fall |
| Beschreibung | Zusammenfassung mit einem Satz |
| Reife | Badge-Syntax für die zugewiesene Ebene |
| Muster | `[{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md)` |

**Platzierungsregel:** Auf jeder Branchenregisterkarte werden Zeilen nach Reife in der folgenden Reihenfolge gruppiert: „Grundlegend“, dann „Aufkommend“, dann „Erweitert“. Platzieren Sie die neue Zeile am Ende der richtigen Reifegruppe.

Die Pattern-Dateipfade sind:
- `audience-building-activation/audience-activation-to-destinations.md`
- `audience-building-activation/audience-collaboration-segment-match.md`
- `audience-building-activation/event-forwarding.md`
- `audience-building-activation/b2b-audience-activation.md`
- `personalization/anonymous-visitor-web-personalization.md`
- `personalization/known-visitor-web-app-personalization.md`
- `personalization/offer-decisioning.md`
- `personalization/behavioral-recommendation.md`
- `campaign-management-orchestration/batch-outbound-message-activation.md`
- `campaign-management-orchestration/event-triggered-messaging.md`
- `campaign-management-orchestration/multi-step-orchestrated-journey.md`
- `campaign-management-orchestration/cross-channel-journey-with-decisioning.md`
- `campaign-management-orchestration/buying-group-based-marketing.md`
- `analysis/customer-analytics-insight-generation.md`
- `analysis/b2b-analytics.md`
- `conversational-experience/brand-concierge-conversational-experience.md`

## Phase 4: Symbolerstellung

Nachdem der Inhalt erstellt wurde, rufen Sie die `use-case-icon-generator` auf, um eine Symbolspezifikation für den neuen Anwendungsfall zu generieren. Vermitteln Sie die Kenntnisse mit:
- Der Name des Anwendungsfalls
- Die vertikale Branche
- Eine kurze Beschreibung des Anwendungsfalls

Nachdem der Benutzer die Symboldatei generiert hat, aktualisieren Sie die Katalogzeile, um die Symbolreferenz einzuschließen:

```
<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">
```

## Phase 5: Validierung

Überprüfen Sie vor der Fertigstellung Folgendes:

1. **Vorlagenkompatibilität** Der Abschnitt „Branchenübersicht“ folgt der Vorlage genau (## Überschrift, Beschreibung, ### Geschäftsauswirkungen, ### Implementierung, ### technische Überlegungen).
2. **Katalogplatzierung** - Die Katalogzeile befindet sich auf der richtigen Branchenregisterkarte und in der richtigen Reifegruppe (Foundation, dann Emerging, dann Advanced).
3. **Gültigkeit von Musterverknüpfungen** - Die Musterverknüpfung im Überblick und im Katalog verwendet einen gültigen Musterdateipfad aus der obigen Liste.
4. **Ankerkonsistenz** - Der Anker im Kataloglink (z. B. `#abandoned-cart-email-recovery`) entspricht der `##` Überschrift in der Übersichtsdatei, die in den Kebab-Fall konvertiert wurde.
5. **Konventionen für Symbolpfade** - Der Symbolpfad folgt `assets/use-case-icons/{industry}/icon-{kebab-name}.png`.

Melden Sie alle während der Validierung gefundenen Probleme und beheben Sie diese, bevor Sie den Vorgang abschließen.
