---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 7%

---
# Blueprint-Prüfung und -Empfehlungen

Diese Prüfung wendet die [Bewertungsrubrik](rubric.md) auf jedes Dokument unter dem
Abschnitt „Architekturdiagramme und Blueprints“ von [TOC.md](../help/blueprints/TOC.md) (Zeilen 76-133) und
empfiehlt, dass jede Blueprint zu einem Anwendungsfall (**)** Architektur wird
**Diagramm**, beide (**Aufspaltung**) oder als **Duplikat** eines vorhandenen Musters gekennzeichnet werden.

Dies ist nur eine Prüfung - es wurde kein Inhalt verschoben. Der Migrationsrückstand (Batch-A-D-Aktionen)
wird als gesonderter Folgeplan erstellt, sobald die Empfehlungen überprüft worden sind.

## Zusammenfassung

**Insgesamt geprüfte Dokumente:** 43

| Empfehlung | Count | Aktion |
| --- | --- | --- |
| Muster | 8 | Erstellen Sie ein neues Anwendungsfallmuster; trimmen Sie das Original auf ein Diagramm. |
| Duplizieren | 9 | Vorhandenes Muster deckt den Umfang ab; vereinfachen Sie Blueprint zu einem Diagramm und vernetzen Sie. |
| Aufspalten | 2 | Musterinhalt extrahieren, Original auf Diagramm reduzieren, beide verknüpfen |
| Diagramm | 16 | Als Architekturdiagramm beibehalten; ggf. Erzählung kürzen. |
| Navigation | 8 | Abschnitt Landingpage (overview.md oder nur Links); nach der Landung der Migrationen erneut aufrufen. |

### Kalibrierung der Kontrollgruppe

Alle 6 `experience-platform/` Dateien bewerteten Muster = 0, Diagramm = 3 → einstimmig **Diagramm**.
Die Rubrik ist kalibriert; Ergebnisse aus den anderen Unterbereichen können als Score vertrauenswürdig eingestuft werden.

### Neue Anwendungsfall-Musterkategorie: B2B-Aktivierung und Marketing

Eine neue Kategorie `use-case-patterns/b2b/` (Anzeigebezeichnung **B2B-Aktivierung und Marketing**, Inhaltsverzeichnisanker
vorgeschlagene `{#b2b-patterns}`) werden alle B2B-spezifischen Muster enthalten. Die Bezeichnung spiegelt die vorhandene
Unterabschnitt „B2B-Aktivierung und -Marketing“ im Bereich „Architektur-Diagramme“ von [TOC.md](../help/blueprints/TOC.md),
Den Lesern wird eine visuelle Symmetrie zwischen den beiden Abschnitten geboten.

Wenn vollständig ausgefüllt, enthält die Kategorie **7 Muster**:

| Entstehung | Aktion | Zielpfad |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **Vorhandenes Muster** verschieben“ | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **Vorhandenes Muster** verschieben“ | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **Vorhandenes Muster** verschieben“ | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **Neu erstellen** (Zeile mit Audit-Muster) | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **Neu erstellen** (Zeile mit Audit-Muster) | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **Neu erstellen** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **Neu erstellen** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **Anfänglicher Übergangsstatus — Writer-Coordination-Gate.** Die bestehende „B2B-Aktivierung und -Marketing“> Unterabschnitt im Bereich Architecture-Diagrams von [TOC.md](../help/blueprints/TOC.md) (Zeilen 95-106) **bleibt intakt> Während der Umstellung**. Jede Blueprint-Konversion und jedes Verschieben vorhandener Muster erfordert> Abnahme vom Eigentümer des Verfassers, bevor der Inhalt migriert wird. Das neue Anwendungsfallmuster für `b2b/`> Abschnitt ist neben dem vorhandenen Blueprint-Abschnitt vorhanden, während Migrationen Seite für Seite erfolgen, mit> Querverbindungen zwischen ihnen.

Wenn die Verlagerungen und neuen Muster alle gelandet sind:

- [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns` Abschnitt erhält eine `B2B Activation & Marketing{#b2b-patterns}`
Unterabschnitt (Platzierung TBD mit dem Autor).
- [use-case-patterns/overview.md](../help/blueprints/use-case-patterns/overview.md) erhält eine B2B-Kategorietabelle.
- Die verschobenen Muster werden aus `audience-building-activation` entfernt.
  `campaign-management-orchestration` und `analysis` Übersichtstabellen; ihre alten URLs werden beibehalten
Live über Weiterleitungen in [migration-redirects.csv](migration-redirects.csv).

### Identifizierte Duplikate (9)

Der Blueprint-Umfang wird bereits von einem vorhandenen Anwendungsfallmuster abgedeckt. Migrationsaktion ist
**Vereinfachung der Architekturgrafik + Vernetzung**.

| Blueprint | Vorhandenes Muster |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> Hinweis: `decision-management-edge.md` und `decision-management-hub.md` sind beide derselben Zuordnung zugeordnet> Vorhandenes `offer-decisioning.md`. Erwägen Sie, beide Blueprints zu einem einzigen zu konsolidieren> Bereitstellungsoptionendiagramm oder Erweiterung des vorhandenen Musters durch Edge-vs-Hub-Bereitstellung> Varianten. Flag für Autorenüberprüfung.

### Muster für Autor (8 neue + 2 aus Aufspaltungen = insgesamt 10)

| Source-Blueprint | Vorgeschlagene Kategorie | Titel des vorgeschlagenen Musters |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | Echtzeit-Profilsuche für Support und Vertrieb |
| `audience-activation/data-science.md` | audience-building-activation | Datenwissenschaftsmodellaufnahme zur Profilanreicherung |
| `audience-activation/real-time-lookup.md` | Personalisierung | Edge-Profilzugriff für Web/Mobile Personalization |
| `b2b/b2b-journeys-with-marketo.md` | **B2B** (neu) | B2B-Account-Journey mit Marketo-Datenintegration |
| `b2b/ajo-b2b-paid-media-controller.md` | **B2B** (neu) | Orchestrierung bezahlter B2B-Medien über die Waterfall-Split-Path-Logik |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **B2B** (neu) | Aufnahme von Kampagnenanfragen und automatisierte Programmerstellung |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **B2B** (neu) | Workflow für Überprüfung und Genehmigung von Campaign-Assets |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Batch-Orchestrierung und Transaktionsnachrichten in Campaign v8 |
| `audience-activation/rtcdp-target.md` *(Aufspaltung)* | Personalisierung | Freigabe von Zielgruppen in Echtzeit mit Adobe Target |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *(Aufspaltung)* | campaign-management-orchestration | Integration von Drittanbieternachrichten mit Journey Optimizer |

### Vorgeschlagene neue Musterkategorie

- **`b2b/`** (Anzeigebezeichnung **B2B-Aktivierung und Marketing**) - siehe den entsprechenden Abschnitt oben. Die
Marketo- und Workfront-Muster (`intake-and-create`, `review-and-approve-blueprint`) werden weitergeleitet
hier anstelle einer separaten `marketing-resource-management`, da sie Folgendes darstellen
B2B-Marketing-Vorgänge in der Praxis. Die neue Kategorie fasst 7 Muster zusammen: 3 umgesiedelt
aus vorhandenen Kategorien und 4 neu aus Blueprints erstellt.

### Umleitungen zur Migration

Jede URL-Änderung, die durch diese Migration eingeführt wird, fügt eine Zeile zur kanonischen hinzu
[`redirects.csv`](../redirects.csv) im Repository-Stammverzeichnis (Format: `source,dest`). Bestätigt
Weiterleitungen werden in [migration-redirects.csv](migration-redirects.csv) gestaffelt und in der
Kanonische Datei, da jede entsprechende Verschiebung tatsächlich geschieht.

**Bestätigt (3 Einträge, gestaffelt):** vorhandene Muster werden nach `b2b/` verschoben. Siehe
[migration-redirects.csv](migration-redirects.csv).

**Ausstehend - Wird hinzugefügt, wenn ein Blueprint *gelöscht* (nicht, wenn er auf das vorhandene Diagramm reduziert wird):** Wenn ein
Der Blueprint der Zeilen „Muster“, „Aufspaltung“ oder „Duplizieren“ wird später vollständig entfernt. Fügen Sie eine Umleitung aus der
Blueprint-URL zur kanonischen Muster-URL. Standardmäßiger Migrationsansatz (vereinfachte Darstellung)
Behält die Blueprint-URL bei und **erfordert keine** diese Umleitungen. Unten aufgeführt für
Vollständigkeit, wenn ein Blueprint vollständig eingestellt wurde:

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

Wenn Sie einen der oben genannten Werte in aktive Umleitungszeilen konvertieren, formatieren Sie ihn als kommagetrennte Zeilen `source,dest`
mit vollständigen `/en/docs/...`-Pfaden (kein `.html` Suffix), die mit dem vorhandenen Muster in
[`redirects.csv`](../redirects.csv).

### Richtlinie zur Umleitungs-Erstellung (dauerhafte Regel)

Befolgen Sie für jeden Migrationsschritt die folgenden Regeln:

1. **Datei verschoben oder umbenannt** → Umleitung von der alten URL zur neuen URL hinzufügen.
2. **Datei gelöscht** (Blueprint ersetzt; kein Diagramm beibehalten) → Umleitung von gelöschter URL zu
Kanonische Ersatz-URL.
3. **Datei im Kontext vereinfacht** (URL unverändert) → keine Umleitung.
4. **Inhaltsverzeichnisanker umbenannt** (z. B. durch Änderung der Abschnittsüberschrift), → Umleitungen für jede Seite unter hinzuzufügen
Dieser Anker, da sich die URL ändert.

### Offene Fragen für den Autor

1. **Entscheidungs-Management-Edge vs. -Hub** - beide werden derselben vorhandenen zugewiesen `offer-decisioning.md`
Muster. Konsolidierung in einem einzigen Diagramm mit Bereitstellungsvarianten oder separate Behandlung
Diagramme, die beide auf dasselbe Muster verweisen?
2. **Journey Optimizer-Journey im Vergleich zu ereignisgesteuertem Messaging** - Agent hat dieses Duplikat gekennzeichnet
Einstufung als unsicher. Überprüfen Sie die Bereichsausrichtung, bevor Sie den Blueprint reduzieren.
3. **`customer-journey-analytics/analysis.md`** - Inhalte drehen sich eigentlich um Experience Platform
Query Service, nicht CJA. Ziehen Sie eine Verlagerung in `experience-platform/` Ordner in Betracht. (Eine Umleitung
würde hinzugefügt, wenn dies der Fall ist - siehe [migration-redirects.csv](migration-redirects.csv).)
4. **Campaign v7 (veraltet)** - drei veraltete v7-Dateien wurden als Diagramm klassifiziert
Navigation. Bestätigen, ob überhaupt migriert werden soll, unverändert bleiben oder vollständig aus dem Inhaltsverzeichnis entfernen soll.
5. **`customer-success-stories.md`** — Referenzseite nur für Links (keine `overview.md`).
Klassifiziert als Navigation. Bestätigen oder neu klassifizieren.
6. **B2B-Abschnitt TOC Anker** — vorgeschlagene `{#b2b-patterns}`. Andere verwendete Muster - Unterabschnitte
   `-patterns` Suffix (`{#personalization-patterns}`, `{#analysis-patterns}`,
   `{#campaign-orchestration-patterns}`). Bestätigen oder wählen Sie einen anderen Anker, bevor Sie Umleitungen erstellen.
7. **B2B-Abschnittsplatzierung im Inhaltsverzeichnis** — vorgeschlagen unter `+ Use Case Patterns{#use-case-patterns}`.
Reihenfolge unter gleichrangigen Elementen (Zielgruppenerstellung und -aktivierung, Personalization, Kampagnenverwaltung)
Orchestrierung und Analyse, B2B-Aktivierung und Marketing, Conversational Experience) ist die
Der Anruf des Autors.
8. **Owning-Writer-Koordination** - jede Blueprint-Konversion und jede Verschiebung vorhandener Muster
Der Autor muss vor dem Verschieben des Inhalts abzeichnen. Die Audittabelle ist der Zielstatus, nicht eine
Sequenzierungsplan; die Sequenzierung erfolgt nach der Koordinierung in einem Folgemigrationsplan.

## Audit-Tabelle

| Pfad | Anrede | Zusammenfassung | dominanter_type | Empfehlung | recommended_pattern_category | recommended_pattern_title | recommended_diagram_title | duplicate_of | pattern_score | diagram_score | Notizen |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Architekturdiagramme zu Adobe Experience Cloud | Unternehmensarchitektur, die zeigt, wie Experience Cloud-Programme und -Services in AEP Foundation integriert werden. | Diagramm | Diagramm |  |  | Überblick über die Experience Cloud-Architektur |  | 0 | 3 | Überschreibung 3 (kein Geschäftsziel). Drei komplementäre Diagramme (Marktarchitektur, Integration, Unternehmenslandschaft). Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/experience-platform/platform-applications.md | Architekturdiagramme für Adobe Experience Platform und Programme | Architekturdiagramme, die zeigen, wie Experience Platform mit anderen Experience Cloud-Anwendungen in Beziehung steht. | Diagramm | Diagramm |  |  | AEP- und Anwendungsarchitektur |  | 0 | 3 | Überschreiben Sie 3. Zwei Übersichts-/Detaildiagramme, keine Implementierungsanleitung. Verknüpfungen zu Integrationen - Erfahren Sie mehr über Dokumente. Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/experience-platform/platform-data-flow.md | Architekturdiagramme zum Datenfluss in Adobe Experience Platform | Diagramm zur Datenflussarchitektur mit Aufnahme- und Ausgangspfaden in und aus Experience Platform. | Diagramm | Diagramm |  |  | AEP-Datenflussarchitektur |  | 0 | 3 | Überschreiben Sie 3. Einzelnes Datenflussdiagramm mit Verweis auf Datenerfassungsdokumente. Reines Architekturartefakt. Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/experience-platform/guardrails.md | Leitlinien für Experience Platform und Anwendungen | Systemeinschränkungen, Leistungserwartungen und Latenzwägelungen für AEP und Programme. | Diagramm | Diagramm |  |  | Leitplanken und Latenzen für AEP und Programme |  | 0 | 3 | Überschreiben Sie 3. Latenzdiagramm plus Referenztabellen. Architektenorientiert (Edge vs. Hub). Dokumentation zu Einschränkungen, keine Anleitung. Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/experience-platform/deployment/websdk.md | Architekturdiagramm für Experience Platform Web SDK und Edge Network | Bereitstellungsarchitektur von Web SDK und Edge Network mit Datenerfassungsflüssen. | Diagramm | Diagramm |  |  | Bereitstellung von Web SDK und Edge Network |  | 0 | 3 | Überschreiben Sie 3. Zwei Diagramme (Ablauf und Ablauf). Verweist auf Tutorials, aber keine Anleitungen im Dokument. Architektenorientiert. Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/experience-platform/deployment/appsdk.md | Architekturdiagramm zur anwendungsspezifischen SDK-Bereitstellung | Anwendungsspezifische SDK-Integrationspfade und Datenerfassungsarchitekturdiagramm. | Diagramm | Diagramm |  |  | Anwendungsspezifische SDK-Bereitstellung |  | 0 | 3 | Überschreiben Sie 3. Einzelnes Bereitstellungsdiagramm mit minimaler Darstellung. Reines Architekturartefakt. Kontrollgruppe: erwartungsgemäß. |
| help/blueprints/audience-activation/advertising-activation.md | Audience Activation zu Social-Media- und Advertising-Zielen | Aktivieren Sie Zielgruppen für Facebook- und Google-Werbenetzwerke über RTCDP mit Identitätskonfiguration und Ziel-Setup. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | Vorhandenes Muster deckt diesen Bereich ab. Doppelte Überschreibung. Aktion: Vereinfachen auf reines Diagramm und Vernetzen. |
| help/blueprints/audience-activation/audience-manager.md | Gerätebasiert - Anonymes Audience-Targeting mit Audience Manager | Anonyme Zielgruppenaktivierung mithilfe von Audience Manager oder RTCDP für gerätebasiertes Targeting kanalübergreifend. | Diagramm | Diagramm |  |  | Anonymes gerätebasiertes Zielgruppen-Targeting |  | 1 | 2 | Minimale Erzählung. Architekturdiagramm vorhanden, Systemtopologie angezeigt. Kein Business Objective-Framing, Bereitstellungs-SDKs und Hub-/Edge-Konzepte. |
| help/blueprints/audience-activation/customer-activity.md | Echtzeit-Profilzugriff für Support- und Vertriebsszenarien | Support- und Vertriebsmitarbeiter können Echtzeit-Kundenkontext über die Profilsuche-API aktivieren. | Muster | Muster | audience-building-activation | Echtzeit-Profilsuche für Support und Vertrieb |  |  | 3 | 1 | Rahment das Geschäftsergebnis (Agentenkontext). Hat Checkliste mit Voraussetzungen; Implementierungsschritte > 30 Zeilen. Eindeutiger Anwendungsfall: Hub-Profilzugriff (nicht Edge-Personalisierung). sich von vorhandenen Personalisierungsmustern unterscheiden. |
| help/blueprints/audience-activation/data-science.md | Blueprint: Benutzerdefinierte Datenwissenschaft zur Profilanreicherung | Nehmen Sie maschinelle Lernmodellbewertungen in RTCDP auf, um Profile für Personalisierung und Segmentierung anzureichern. | Muster | Muster | audience-building-activation | Datenwissenschaftsmodellaufnahme zur Profilanreicherung |  |  | 3 | 1 | Frames für Geschäftsergebnisse (Anreicherung zur Personalisierung). Hat Anwendungsfälle und Überlegungen zur Implementierung; Überlegungen zur Implementierung >30 Zeilen. Konzentrieren Sie sich auf datenwissenschaftliche Workflows, nicht auf Messaging/Aktivierung. |
| help/blueprints/audience-activation/enterprise-destinations.md | Zielgruppen- und Profilaktivierung für Unternehmensziele | Streamen oder Batch-Profil- und Zielgruppenänderungen an Cloud-Speicher und Enterprise-Apps für Vertrieb, Support und Analysen. | Diagramm | Diagramm |  |  | Enterprise-Zielgruppe und Profilaktivierung |  | 1 | 2 | Kein Business Objective-Framing. Eine spärliche Anleitung zur Implementierung. Architekturdiagramm + Systemtopologie für Cloud-Speicher-/Unternehmens-Apps. Visuell-dominant. |
| help/blueprints/audience-activation/real-time-lookup.md | Echtzeit-Edge-Profilzugriff für Web- und Mobile-Personalization | Zugriff auf ein einheitliches Profil am Edge in Millisekunden für Echtzeit-Web- und Mobile-Personalisierung. | Muster | Muster | Personalisierung | Edge-Profilzugriff für Web/Mobile Personalization |  |  | 5 | 2 | Starkes Business-Framing (Personalisierung mit niedriger Latenz). Zwei Implementierungsmuster (Web SDK vs. Edge API). Umfassende Voraussetzungen und Schritte (>30 Zeilen). Implizierte KPIs (Latenz, Durchsatz). |
| help/blueprints/audience-activation/rtcdp-target.md | Bekannte Kunden-Personalization mit Target | Geben Sie RTCDP-Zielgruppen und -Profile für die Personalisierung für Web- und Mobilgeräte für bekannte Besucher frei. | Gemischt | Aufspalten | Personalisierung | Freigabe von Zielgruppen in Echtzeit mit Adobe Target | Architektur der Target-Integration | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | Überschneidet sich mit vorhandenem Muster bekannter Besucher, aber engerer Umfang (nur Target). Drei Integrationsmuster. Architekturdiagramme und Edge-Bereitstellung werden berücksichtigt. Musterinhalt + Diagramm, beide erheblich → Aufspaltung. |
| help/blueprints/audience-activation/segment-match.md | Zielgruppen-Collaboration mit Segment Match | Ermöglichen Sie die sichere Zusammenarbeit mit Partner-Zielgruppen über Segment Match mit Datenschutzkontrollen. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | Vorhandenes Muster deckt dies genau ab. Doppelte Überschreibung. Eindeutige Inhalte, die im Diagramm beibehalten werden sollen: detaillierte RBAC-/Einverständnis-/Governance-Konfiguration und programmatischer Anzeigenworkflow. |
| help/blueprints/b2b/overview.md | B2B-Analytics-, Aktivierungs- und Marketing-Blueprints | Navigationsseite mit einer Auflistung von B2B-Analysen, Zielgruppenaktivierung, Einkaufsgruppe, Marketo und Workfront-Blueprints. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: Datei mit dem Namen overview.md. Von der Migration ausgeschlossen. |
| help/blueprints/b2b/b2bactivation.md | Blueprint: B2B – Aktivierung von Zielgruppen und Profilen | Aktivieren Sie Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle mithilfe von Account- und Profildaten. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | Überschreibung 2: Entsprechendes Muster ist vorhanden. Blueprint ist eine auf die engere Architektur fokussierte Teilmenge. |
| help/blueprints/b2b/b2b-account-activation.md | B2B-Kontoaktivierung für Advertising-Ziele und Dateiziele | Targeting von B2B-Konten über LinkedIn und Cloud-Speicher-Ziele mithilfe der Erstellung und Aktivierung von Konto-Audience. | Diagramm | Diagramm |  |  | B2B-Konto-Audience Activation |  | 1 | 2 | Minimales Business-Framing, keine KPIs, minimale Erzählung. Architekturdiagramm vorhanden; LinkedIn/Cloud-Speicher-Topologie beschrieben. Als Diagramm beibehalten. |
| help/blueprints/b2b/b2b-buying-group-journeys.md | Kaufen von gruppenbasiertem Marketing und Journey-Management-Blueprint | Journey für das Konto entwerfen, die Leads zu Einkaufsgruppen mit definierten Rollen und Lösungsinteressen qualifizieren. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | Überschreibung 2: Entsprechendes Muster ist vorhanden. Blueprint enthält umfangreiche Musterinhalte, das vorhandene Muster ist jedoch umfassender. |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | B2B-Journey, die Marketo Data Blueprint verwenden | Stellen Sie Journey Optimizer B2B edition mit Marketo-Daten bereit, um die Journey von Einkaufsgruppen und die Kontointeraktion zu orchestrieren. | Muster | Muster | B2B | B2B-Account-Journey mit Marketo-Datenintegration |  |  | 4 | 1 | Starkes Business-Framework. Aufgeführte KPIs; mehrere Implementierungsoptionen; umfassende Überlegungen (>30 Zeilen). Unterschieden von bestehenden Mustern durch die Marketo-Datenintegrationstiefe (XDM-Konfiguration, Identitätszuordnung, Feldblockierung). Routen zur neuen b2b/-Kategorie |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B - Account Journey Orchestration - Paid Media Controller | Orchestrieren Sie B2B-Kampagnen mit bezahlten Medien mithilfe der Wasserfalllogik, um Kampagnen Konten zuzuweisen und sie für Ziele zu aktivieren. | Muster | Muster | B2B | Orchestrierung bezahlter B2B-Medien über die Waterfall-Split-Path-Logik |  |  | 4 | 2 | Starkes Business-Framework. Explizite KPIs; mehrere Implementierungsoptionen; Voraussetzungen; Erzählung > 30 Zeilen. Anders als bei bestehenden Einkaufsgruppenmustern (konzentriert sich auf die Priorisierung bezahlter Medien, nicht auf die Pflege). Routen zur neuen b2b/-Kategorie |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Blueprint-Übersicht: Integration von Marketo Engage und Workfront | Überblick über die Kampagnenplanung bis zur Automatisierung der Ausführung mithilfe von Marketo Engage und Workfront mit Fusion. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: Datei mit dem Namen overview.md. Von der Migration ausgeschlossen. |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | Blueprint: Annahme und Erstellung | Automatisieren Sie den Eingang von B2B-Marketing-Kampagnenanfragen zur Erstellung mithilfe von Workfront Forms- und Marketo Engage-Programmvorlagen. | Muster | Muster | B2B | Aufnahme von Kampagnenanfragen und automatisierte Programmerstellung |  |  | 4 | 1 | Starkes Business-Framework zur Kampagnengeschwindigkeit. Implizite KPIs (Fehler/Rework-Reduktion); Workflow-Schritte >30 Zeilen; Checkliste für die Bereitschaft. Routen zu neuen B2B-/-Kategorien (Marketo+Workfront-Ops sind überwiegend B2B). |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | Blueprint überprüfen und genehmigen | Integrieren von Workfront-Proofing- und -Genehmigungs-Workflows mit Marketo Engage-E-Mail-Assets mithilfe der Fusion-Automatisierung. | Muster | Muster | B2B | Workflow für Überprüfung und Genehmigung von Campaign-Assets |  |  | 3 | 2 | Starker geschäftlicher Rahmen für Compliance und Genauigkeit; implizite KPIs (Validierungsgeschwindigkeit); Erzählung >30 Zeilen; Abschnitt „Workflow-Planung“. Routen zur neuen b2b/-Kategorie |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | Erfolgsgeschichten von Kunden | Links zu Fallstudien und Webinaren von Kunden, in denen die Ergebnisse der Integration von Marketo und Workfront vorgestellt werden. | Navigation | Navigation |  |  |  |  |  |  | Minimaler Inhalt (6 Hyperlinks). Kein Business Framing, KPIs, Architektur oder Narrativ. Als Navigation behandelt. Der Autor sollte bestätigen. |
| help/blueprints/customer-journey-analytics/overview.md | Customer Journey Analytics Blueprints | Vereinheitlichen und analysieren Sie Kundendaten und -verhalten aus verschiedenen Kanälen, um Journey-basierte Ansichten zu erstellen. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: overview.md. Inhaltsverzeichnis-artige Landingpage Von der Migration ausgeschlossen. |
| help/blueprints/customer-journey-analytics/b2b-cja.md | B2B-Customer Journey Analytics-Blueprint | Account-basierte CJA-Berichterstellung und -Analyse für B2B-Organisationen, die das Konto als Primärdatenmodell verwenden. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | Überschreibung 2: Das äquivalente Muster behandelt Analysen auf B2B-Kontoebene mit CJA B2B edition. Aktion: Vereinfachen des Diagramms, Querverknüpfen. |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | Blueprint zu Customer Journey Analytics mit Real-time Customer Data Platform | Erstellen und veröffentlichen Sie Zielgruppen aus CJA in RTCDP für Targeting und Personalisierung. | Diagramm | Diagramm |  |  | Integration der Veröffentlichung von CJA in RTCDP-Zielgruppen |  | 1 | 3 | Starker Architekturfokus (System-zu-System-Integration, Bereitstellungsform). Minimale Erzählung. Eindeutige Inhalte: Leitplanken für die Latenz bei der Veröffentlichung von CJA-Zielgruppen. |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Customer Journey Analytics mit Journey Optimizer Blueprint | Analyse der Versand- und Interaktionsdaten von AJO in CJA; Veröffentlichung von CJA-Zielgruppen in AJO. | Diagramm | Diagramm |  |  | Integration und Analyse zwischen CJA und AJO |  | 1 | 3 | Starker Architekturfokus. Minimale Erzählung. Eindeutiger Inhalt: bidirektionales Datenfreigabemuster zwischen CJA und AJO. |
| help/blueprints/customer-journey-analytics/analysis.md | Blueprint: Datenanalyse und Datenintelligenz | Verwenden Sie den Abfrage-Service von Experience Platform für die explorative Analyse der Data Lake-Daten. | Diagramm | Diagramm |  |  | Integration von Experience Platform Query Service und BI-Tool |  | 1 | 3 | Behandelt Query Service, NICHT CJA-spezifisch. im CJA-Ordner verlegt sein könnte; ziehen Sie einen Wechsel zu experience-platform/ in Betracht. Starke Architekturzielgruppe (PostgreSQL, BI-Tools). |
| help/blueprints/customer-journeys/overview.md | Customer-Journey-Blueprints | Moderne Marketing-Plattformen unterstützen ereignisgesteuerte Journey und markeninitiierte Kampagnen kanalübergreifend. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: overview.md. Inhaltsverzeichnis für Journey-Unterkategorien; beschreibt die Positionierung von Journey Optimizer und Campaign. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Journey Optimizer Blueprints | Ereignisgesteuerte 1::1-Orchestrierung und zielgruppenbasierte Markenkommunikation über verschiedene Kanäle hinweg. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: overview.md. Landingpage mit Anwendungsfall-Registerkarten und Integrationsmustern. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer - Ausgelöstes Messaging und Adobe Experience Platform Blueprint | Ereignisgesteuerte Workflows in Echtzeit, die basierend auf Kundenverhalten personalisierte mehrstufige Erlebnisse bieten. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | 2 mit Einschränkung überschreiben: Agent wird als wahrscheinlich dupliziert, aber unsicher gekennzeichnet. Überprüfen Sie die Bereichsausrichtung vor dem Reduzieren. Überlegungen zur Architektur können einzigartig sein (Profilfrische, Zeitpunkt der Segmentqualifizierung) und sollten im Diagramm beibehalten werden. |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer - Kampagnenorchestrierung | Geplante zielgruppenbasierte mehrstufige Kommunikation über ausgehende Kanäle: E-Mail, SMS, Push, Briefpost. | Muster | Duplizieren |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | Überschreibung 2: Entsprechendes Muster. Diagramme mit mehreren Architekturen; als Diagramm beibehalten. Eindeutiger Inhalt: Details zur relationalen Datenbank-/Zielgruppenportal-/dünnen Profilarchitektur. |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Blueprint: Journey Optimizer - Drittanbieter-Messaging | Demonstriert die Integration von Journey Optimizer mit Messaging-Systemen von Drittanbietern für orchestrierte Kommunikation. | Gemischt | Aufspalten | campaign-management-orchestration | Integration von Drittanbieternachrichten mit Journey Optimizer | Messaging-Architektur von Drittanbietern |  | 2 | 2 | Gebundene Scores → aufgeteilt. Diagramm (System-zu-System-Topologie) plus Musterinhalt (Implementierungsschritte, Integrationsbeschränkungen: Bearer-Authentifizierung, keine statischen IPs, Ratenbeschränkungen). Beides ist es wert, erhalten zu werden. |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | Blueprints: Entscheidungs-Management | Stellen Sie über eine zentrale Angebotsbibliothek und eine Entscheidungs-Engine personalisierte Angebote für alle Kunden-Journey bereit. | Navigation | Navigation |  |  |  |  |  |  | Überschreibung 1: overview.md. Beschreibt Entscheidungs-Management-Komponenten und Ansätze für die Bereitstellung von Edge- und Hub-Servern. |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | Blueprint: Entscheidungs-Management im Edge | Stellen Sie personalisierte Angebote in Echtzeit für Web- und mobile Erlebnisse mit einer Latenz von unter zwei Sekunden im Edge Network bereit. | Gemischt | Duplizieren |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Überschreibung 2: ist Offer Decisioning zugeordnet. Edge-Bereitstellungsvariante - Ziehen Sie die Konsolidierung mit dem Hub-Blueprint in einem einzigen Bereitstellungsoptionendiagramm in Betracht. |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | Blueprint: Entscheidungs-Management auf dem Hub | Stellen Sie personalisierte Angebote kanalübergreifend bereit, einschließlich Kiosks, agentengestützte Erlebnisse und ausgehende Sendungen. | Gemischt | Duplizieren |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | Überschreibung 2: ist Offer Decisioning zugeordnet. Hub-Bereitstellungsvariante - Eine Konsolidierung mit Edge-Blueprint in einem einzigen Bereitstellungsoptionendiagramm wird in Betracht gezogen. |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Campaign v8 - Blueprint, Campaign und Plattform | Batch-Kampagnen-Management-Plattform der nächsten Generation mit ETL-, Segmentierungs- und Transaktionsnachrichten-Funktionen. | Muster | Muster | campaign-management-orchestration | Batch-Orchestrierung und Transaktionsnachrichten in Campaign v8 | Bereitstellungsmodelle für die Architektur von Campaign v8 |  | 4 | 3 | Unterschiedlicher technischer Ansatz (Campaign v8 nativ, nicht AJO). Diagramme mit mehreren Architekturen; Business Framing; in Leitplanken implizierte KPIs (20 Mio. msg/h batch, 1 Mio./h in Echtzeit). Keine Entsprechung im vorhandenen Musterkatalog. Hinweis: Werte gelten auch als aufgeteilt — Muster vorschlagen, aber der Autor möchte das Diagramm möglicherweise beibehalten. |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Muster für die Integration von Real-Time CDP mit Adobe Campaign v8 | Zeigt die RTCDP-Zielgruppen- und Profilintegration mit Campaign v8 für personalisierte Konversationen. | Diagramm | Diagramm |  |  | RTCDP - Zielgruppen- und Profilaustausch mit Campaign v8 |  | 1 | 2 | Blueprint für Integrations-Connector, kein eigenständiger Anwendungsfall. Diagramm + kurze Voraussetzungen/Leitlinien. Architektenorientiert. |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Blueprint: Journey Optimizer mit Adobe Campaign v8 | Demonstriert die AJO-Orchestrierung mit Campaign v8-Transaktionsnachrichten für 1:1-Erlebnisse. | Diagramm | Diagramm |  |  | Integration von Journey Optimizer mit Transaktionsnachrichten in Campaign v8 |  | 1 | 2 | Integrations-Connector. Abbildung + Implementierungsschritte + technische Einschränkungen (4.000 msg/5min Drosselung, nur ereignisinitiiert). Verknüpfen mit AJO- und Campaign v8-Mustern. |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Blueprint: Campaign v7 | Veraltet: Batch-basiertes Messaging, Onboarding, Remarketing, Briefpost, einfache Transaktionsnachrichten. | Navigation | Navigation |  |  |  |  |  |  | VERALTETES PRODUKT (Frontend-Links zu v8). Minimaler Inhalt (nur Architekturdiagramm). Nicht migrieren. |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Integrationsmuster von Real-Time CDP mit Campaign v7 und Campaign Standard | Zeigt die Integration von RTCDP- und Echtzeit-Kundenprofilen mit Campaign v7/Standard für personalisierte Konversationen. | Diagramm | Diagramm |  |  | RTCDP - Campaign v7/Standard-Zielgruppe und Profilaustausch |  | 1 | 2 | VERALTET. Integrations-Connector. Diagramm + umfassende Implementierungsschritte. Nicht zu einem neuen Muster migrieren, sondern unverändert lassen. |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Blueprint: Journey Optimizer mit Adobe Campaign v7 | Demonstriert die AJO-Orchestrierung mit Campaign v7-Transaktionsnachrichten für 1:1-Erlebnisse. | Diagramm | Diagramm |  |  | Journey Optimizer - Integration von Transaktionsnachrichten in Campaign v7 |  | 1 | 2 | VERALTET. Integrations-Connector. Diagramm + Implementierungsschritte + Einschränkungen. Nicht migrieren, sondern unverändert lassen. |
