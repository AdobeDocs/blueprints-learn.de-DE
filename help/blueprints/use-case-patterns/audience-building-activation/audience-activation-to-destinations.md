---
title: Zielgruppenaktivierung für Ziele
description: Erfahren Sie, wie Sie Zielgruppensegmente mithilfe von Adobe Real-Time CDP für das Targeting oder die Unterdrückung auswerten und für externe Ziele veröffentlichen können.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '7005'
ht-degree: 1%

---


# Zielgruppenaktivierung für Ziele

Dieses Handbuch bietet eine vollständige Implementierungsreferenz für das Aktivieren von Zielgruppen von Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) für externe Ziele. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die Zielgruppensegmente bewerten und auf Anzeigenplattformen, Cloud-Speicher, CRM-Systemen oder Datenpartnern veröffentlichen müssen, um Targeting, Unterdrückung, Lookalike-Modellierung oder Analytics-Anreicherung durchzuführen.

Es stellt alle praktikablen Implementierungsoptionen mit Zielgruppenanalysen, Entscheidungshilfen, Benutzeroberflächennavigationspfaden und Experience League-Dokumentationsreferenzen vor.

Das Handbuch deckt den gesamten Lebenszyklus der Zielgruppenaktivierung ab - von der Definition und Bewertung von Zielgruppensegmenten über die Konfiguration von Zielverbindungen und die Veröffentlichung von Zielgruppen bis hin zur Überwachung des Aktivierungszustands und zur Durchsetzung der Governance-Compliance.

## Anwendungsfall - Übersicht

Unternehmen müssen Zielgruppendaten an externe Systeme senden, um Kampagnen mit bezahlten Medien zu unterstützen, CRM-Datensätze anzureichern, Daten mit Partnern auszutauschen oder nachgelagerte Analysen zu nutzen. Audience Activation to Destinations ist das grundlegende Aktivierungsmuster in RT-CDP: Es bewertet, welche Profile für eine Zielgruppe qualifiziert sind, stellt eine Verbindung zu einem oder mehreren externen Zielen her, ordnet Profilattribute zielspezifischen Feldern zu und veröffentlicht die Zielgruppe für die nachgelagerte Nutzung.

Dieses Muster gilt immer dann, wenn das Ziel darin besteht, Zielgruppendaten zum richtigen Zeitpunkt in einem externen System im richtigen Format abzurufen. Sie umfasst keinen Nachrichtenversand, keine Personalisierung vor Ort und keine Analysen. Es ist der häufigste Ausgangspunkt für RT-CDP-Implementierungen und dient als Baustein, den andere Muster aufbauen.

Zu den typischen Stakeholdern gehören Teams für digitales Marketing, die bezahlte Medien verwalten, Daten-Teams, die Warehouses anreichern, CRM-Teams, die Kontaktlisten für Kampagnen vorbereiten, und Datenschutz-Teams, die die Einhaltung von Governance-Richtlinien bei ausgehenden Datenflüssen sicherstellen.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden mit diesem Anwendungsfallmuster erreicht.

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung.

**KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion

[Weitere Informationen über die Akquise von Neukunden](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduzierung der Kosten für die Kundenakquise

Verbessern Sie die Targeting-Effizienz, unterdrücken Sie Bestandskunden von Akquise-Kampagnen und optimieren Sie die Medienausgaben.

**KPIs:** Kosten für Kundenakquise, Kosten pro Lead, Effizienz

[Erfahren Sie mehr über die Reduzierung der Kundenakquisitionskosten](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung.

**KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen

[Erfahren Sie mehr über die Optimierung von Marketing-Ausgaben und ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

- **Zielgruppen-Targeting der Anzeigenplattform** — Pushen Sie qualifizierte Segmente auf Paid-Media-Plattformen für das Kampagnen-Targeting
- **Bezahlte Medienunterdrückung bestehender Kunden** - Schließen Sie bekannte Kunden von Akquise-Kampagnen auf Werbeplattformen aus, um verschwendete Ausgaben zu vermeiden.
- **Lookalike-Seed-Zielgruppen** - Übertragen Sie hochwertige Kundensegmente als Seed-Zielgruppen für die Lookalike-Erweiterung an Facebook, Google Ads oder The Trade Desk
- **CRM-Synchronisation für die Sales-Aktivierung** — Aktivieren Sie Zielgruppen mit hohen Absichten oder hohem Wert, damit Vertriebsteams die Kontaktaufnahme priorisieren können
- **Audience-Freigabe durch Datenpartner** — Teilen Sie qualifizierte Audience-Segmente mit Datenpartnern für das Co-op-Targeting oder die Messung
- **Cloud-Speicherexport zur Data Warehouse-Anreicherung** - Exportieren Sie Zielgruppenzugehörigkeit und Profilattribute für nachgelagerte Analysen in Amazon S3, Azure Blob, Google Cloud Storage oder SFTP
- **Aktivierung der Retargeting-Zielgruppe** — Aktivieren Sie Website-Besucher, die nicht zu Retargeting-Plattformen konvertiert wurden
- **Synchronisierung der Kontaktliste mit E-Mail-**: Pushen der Zielgruppenzugehörigkeit auf E-Mail-Plattformen von Drittanbietern, um eine koordinierte Kontaktaufnahme zu ermöglichen

## Wichtige Performance-Indikatoren

| KPI | Beschreibung | Messanleitung |
| --- | --- | --- |
| Kosten für Kundenakquise (CAC) | Kosten für die Akquise eines neuen Kunden über aktivierte Zielgruppen | Gesamtausgaben für Medien/neue Kunden, die aktivierten Zielgruppen zugeordnet wurden |
| Übereinstimmungsrate der Zielgruppe | Prozentsatz der aktivierten Profile, die am Ziel erfolgreich abgeglichen wurden | Am Ziel übereinstimmende Profile/aus RT-CDP exportierte Profile |
| Einsparungen durch Unterdrückung | Medienausgaben werden vermieden, indem Bestandskunden von Akquise-Kampagnen unterdrückt werden | Geschätzte Größe von CPM x unterdrückter Zielgruppe |
| Aktivierungsrate | Prozentsatz der erfolgreich an das Ziel zugestellten Profile | Bereitgestellte Profile/Profile in der Quell-Audience |
| Zeit bis zur Aktivierung | Verstrichene Zeit von der Zielgruppendefinition bis zum ersten Versand am Ziel | Messung von der Segmenterstellung bis zur ersten bestätigten Datenflussausführung |
| Genauigkeit der Zielgruppenpopulation | Abstimmung zwischen erwarteten und tatsächlichen Zielgruppengrößen am Ziel | Ziel-Zielgruppengröße/RT-CDP-Zielgruppengröße |

## Anwendungsfallmuster

**Audience Activation für Ziele** — Auswerten und Veröffentlichen eines Zielgruppensegments für externe Ziele zum Targeting oder zur Unterdrückung.

**Funktionskette:** Zielgruppenauswertung > Zielkonfiguration > Audience Activation > Überwachung

## Programme

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung, Zielverwaltung, Zielgruppenaktivierung, Einverständnis und Durchsetzung der Governance
- **Adobe [!DNL Experience Platform] (AEP)** - Profilspeicher, Identity Service, Segmentierungs-Engine, Data Governance

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | RT-CDP-Sandbox bereitgestellt und aktiv. Berechtigungen für die Zielverwaltung und -aktivierung, die Implementierungsrollen zugewiesen sind. Für die Zielplattformen verfügbare Anmeldedaten für Zielkonten. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Profilschema muss Attribute enthalten, die Zielfeldern zugeordnet werden (z. B. E-Mail, Telefon, Hash-Kennungen, demografische Attribute). Das Schema muss profilaktiviert sein, wobei Datensätze aktiv Daten empfangen. | [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Profildaten, die die Zielgruppenauswertung ermöglichen, müssen aufgenommen und aktuell sein. Batch- und/oder Streaming-Aufnahme-Pipelines sind betriebsbereit. Web SDK, Quell-Connectoren oder Batch-Aufnahme, die Daten in profilaktivierte Datensätze liefern. | [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home), [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | Identity-Namespaces für den Zielabgleich müssen konfiguriert sein (z. B. gehashte E-Mail für benutzerdefinierte Facebook-Zielgruppen, Google Ads-Kundenabgleich). Zusammenführungsrichtlinien müssen einheitliche Profile mit allen erforderlichen Attributen für die Aktivierung erzeugen. | [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Mit Segment Builder, Audience-Komposition oder Federated Audience-Komposition definierte Zielgruppe. Auswertungsmethode (Batch, Streaming oder Edge) basierend auf den Anforderungen an die Aktivierungslatenz ausgewählt. Diese Funktion wird in Phase 1 dieses Plans ausgeübt. | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie Lebenszeitwert, Interaktionswert oder Tendenzwert verbessern die Genauigkeit der Zielgruppe und bieten Anreicherungsattribute für die Zuordnung zu Zielen. Dies ist besonders nützlich, wenn Ziele von einer wertbasierten oder Score-basierten Zielgruppensegmentierung profitieren. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Richtlinien zur Datensatz- und Profilgültigkeit gewährleisten die Aktualität und Einhaltung von Daten. Die Konfiguration des Einverständnisschemas stellt sicher, dass nur einverstandene Profile aktiviert werden. Kritisch für die Einhaltung von Vorschriften beim Export von Daten in externe Systeme. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen und -Richtlinien verhindern die Aktivierung eingeschränkter Daten für nicht autorisierte Ziele (z. B. personenbezogene Daten für Anzeigenplattformen, sensible Segmente für Datenpartner). Dies ist besonders wichtig für die Zielgruppenaktivierung auf externe Drittanbietersysteme. | [Data Governance - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Die Aktivierungsüberwachung ist Teil der Funktionskette (Phase 5). Behandelt die Überwachung der Datenflussausführung, Versandstatus-Warnhinweise, die Verfolgung der Zielgruppenpopulation und die Sichtbarkeit der Lizenznutzung. | [Überwachen von Zieldatenflüssen](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations), [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview) |
| Reporting und Analyse | Empfohlen | Die CJA-Analyse der Effektivität der Zielgruppenaktivierung ermöglicht die Messung der Leistung für aktivierte Zielgruppen (z. B. Steigerung der Konversionsrate durch Unterdrückung, ROAS von Lookalike-Zielgruppen). | [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 1: Evaluierung der Zielgruppe | Definieren Sie Zielgruppenregeln und bewerten Sie die Segmentzugehörigkeit mithilfe von Batch-, Streaming- oder Edge-Auswertungsmethoden |
| Audience-Komposition | Phase 1: Evaluierung der Zielgruppe | Erstellen Sie optional abgeleitete Zielgruppen über die Vorgänge Anreichern, Rangfolge, Aufspaltung, Ausschließen und Zusammenführen für komplexe Zielgruppenlogiken |
| Zielkonfiguration | Phase 2: Zielkonfiguration | Konfigurieren authentifizierter Verbindungen zu externen Zielen mit Feldzuordnungs- und Zeitplanparametern |
| Zielgruppen-Aktivierung | Phase 3: Audience Activation | Veröffentlichen ausgewerteter Zielgruppen an konfigurierten Zielen mit Attributzuordnung und Exportplanung |
| Durchsetzung von Einverständnis und Governance | Phase 4: Governance-Validierung | Erzwingen von Einverständnisvoreinstellungen und Datennutzungsrichtlinien vor und während der Zielgruppenaktivierung für externe Systeme |

## Voraussetzungen

- [ ] RT-CDP-Lizenz ist mit Berechtigungen zur Zielgruppenaktivierung aktiv
- [ ] Target-Sandbox ist bereitgestellt und für das Implementierungs-Team zugänglich
- [ ] Benutzerrollen umfassen Berechtigungen für die Zielverwaltung und Zielgruppenaktivierung
- [ ] Authentifizierungsdaten für jedes Ziel sind verfügbar (OAuth-Token, API-Schlüssel, S3-Zugriffsschlüssel oder Anmeldedaten für Service-Konten)
- [ ] Profilschema enthält alle Attribute, die Zielfeldern zugeordnet werden müssen
- [ ] für den Zielabgleich erforderlichen Identity-Namespaces werden konfiguriert (z. B. gehashte E-Mail, Telefon-, Geräte-IDs)
- [ ] Datenaufnahme-Pipelines sind funktionsfähig und Profile füllen den Profilspeicher auf
- [ ] Data Governance-Beschriftungen und -Richtlinien werden auf die aktivierten Attribute überprüft (insbesondere für externe Ziele).
- [ ] Einverständnisfelder werden in Profilen ausgefüllt, wenn eine einverständnisbasierte Filterung erforderlich ist

## Implementierungsoptionen

Für dieses Anwendungsfallmuster sind die folgenden Implementierungsoptionen verfügbar. Überprüfen Sie jede Option und die Vergleichstabelle, um den besten Ansatz für Ihre Anforderungen zu ermitteln.

### Option A: Streaming-Zielaktivierung

**Best for:** Echtzeit-Aktualisierungen der Zielgruppenzugehörigkeit zu Anzeigenplattformen oder Partnersystemen - Facebook Custom Audiences, Google Ads Customer Match, LinkedIn Matched Audiences, The Trade Desk und ähnliche Streaming-API-basierte Ziele.

**Funktionsweise:**

Die Streaming-Zielaktivierung führt nahezu in Echtzeit zu Änderungen der Zielgruppenzugehörigkeit am Ziel, da Profile für das Segment qualifiziert oder nicht qualifiziert sind. Wenn sich ein Profilattribut ändert oder ein Verhaltensereignis auftritt, das dazu führt, dass ein Profil in eine Zielgruppe eintritt oder diese verlässt, wird die Aktualisierung der Mitgliedschaft innerhalb von Minuten an das Ziel gestreamt.

Dieser Ansatz erfordert einen Streaming-Ziel-Connector (die meisten wichtigen Anzeigenplattformen unterstützen dies) und eine Methode zur Bewertung von Streaming- oder Edge-Zielgruppen. Die Zielgruppenauswertung überwacht kontinuierlich nach qualifizierten Profiländerungen, und der Aktivierungsdatenfluss sendet Aktualisierungen sofort nach dem Auftreten. Das Ziel erhält inkrementelle Mitgliedschaftsänderungen anstelle vollständiger Zielgruppen-Momentaufnahmen.

Die Streaming-Aktivierung ist die Standardeinstellung für die meisten Werbeplattformziele im RT-CDP-Katalog. Der Ziel-Connector verarbeitet die API-Authentifizierung, Ratenbegrenzung und Wiederholungslogik automatisch.

**Wichtige Aspekte:**

- Bei der Zielgruppenauswertung müssen Streaming- oder Edge-Auswertungen verwendet werden (Batch-Audiences können keine Streaming-Ziele in Echtzeit befüllen)
- Nicht alle Segmentausdrücke sind für die Streaming-Auswertung qualifiziert - komplexe Aggregationen, Abfragen mit mehreren Entitäten und bestimmte zeitbasierte Funktionen erfordern einen Batch
- Limits für die API-Rate von Zielpartnern können den Durchsatz bei großen Zielgruppen-Qualifizierungsereignissen beeinträchtigen
- Aktualisierungen von Profilattributen werden zusammen mit Mitgliedschaftsänderungen gesendet, sodass die Zieldaten auf dem neuesten Stand bleiben

**Vorteile:**

- Zielgruppenfrische nahezu in Echtzeit am Ziel (Minuten, nicht Stunden)
- Inkrementelle Aktualisierungen reduzieren das Datenübertragungsvolumen im Vergleich zu vollständigen Exporten
- Automatische Handhabung von Qualifikations- und Disqualifikationsereignissen
- Die meisten Anzeigenplattformziele unterstützen nativ Streaming

**Einschränkungen:**

- Für Streaming geeignete Segmentdefinitionen erforderlich (eingeschränkter Funktionssatz für Segmente)
- Keine Kontrolle über Dateiformat oder Exportstruktur - Datenformat vom Ziel-Connector bestimmt
- Exportieren in dateibasierte Speicherziele (S3, Azure Blob, SFTP) nicht möglich
- Limits für API-Zielraten können Änderungen mit hohem Volumen drosseln

**Experience League:**

- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Streaming-Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)

### Option B: Batch-Zielaktivierung (Dateiexport)

**Optimiert für:** Geplante Audience-Exporte in Cloud-Speicher, Data Warehouses oder Systeme, die dateibasierte Importe nutzen - Amazon S3, Azure Blob Storage, Google Cloud Storage, SFTP, Data Landing Zone.

**Funktionsweise:**

Die Batch-Zielaktivierung bewertet die Zielgruppen in einer geplanten Kadenz und exportiert die Ergebnisse als Dateien (CSV, JSON oder Parquet) in das konfigurierte -Speicherziel. Der Export kann vollständige Momentaufnahmen der Zielgruppe oder inkrementelle Änderungen (neue Qualifikationen und Disqualifikationen seit dem letzten Export) enthalten.

Die Implementierung umfasst die Konfiguration einer dateibasierten Zielverbindung mit Speicheranmeldeinformationen, Dateiformatvoreinstellungen (Trennzeichen, Komprimierung, Namenskonvention) und einem Exportplan (täglich, alle 3 Stunden, alle 6 Stunden usw.). Bei jedem Exportvorgang werden Dateien generiert, die die Zielgruppenzugehörigkeit und alle zugeordneten Profilattribute enthalten.

Dieser Ansatz unterstützt die breiteste Palette nachgelagerter Verbraucher, da der dateibasierte Datenaustausch universell unterstützt wird. Es ist auch die einzige Option für Anwendungsfälle von Cloud-Speicher und Data Warehouse-Anreicherung.

**Wichtige Aspekte:**

- Die Zielgruppenauswertung kann jede Methode verwenden (Batch, Streaming oder Edge) - der Export selbst wird unabhängig davon nach einem Zeitplan ausgeführt
- Die Konventionen für Dateiformat, Komprimierung und Benennung sind pro Ziel konfigurierbar
- Unterstützt sowohl inkrementelle Exporte (nur Änderungen) als auch vollständige Exporte (vollständige Zielgruppen-Momentaufnahme)
- Die Granularität der Exportplanung liegt zwischen allen 3 Stunden und täglich.

**Vorteile:**

- Vollständige Kontrolle über das Exportdateiformat (CSV, JSON, Parquet), Komprimierung und Benennung
- Kompatibel mit jedem nachgelagerten System, das Dateien verarbeiten kann
- Unterstützt sowohl den inkrementellen als auch den vollständigen Exportmodus
- Kann Zielgruppen mit jeder Auswertungsmethode exportieren (einschließlich reine Batch-Segmente mit komplexer Segmentierungslogik)
- Unterstützt Ad-hoc-Exporte (auf Anfrage) außerhalb des regulären Zeitplans

**Einschränkungen:**

- Die Latenz ist von Natur aus höher - Zielgruppendaten gelangen auf einem Zeitplan am Ziel an, nicht in Echtzeit
- Dateibasierte Exporte erfordern, dass das Zielsystem die Dateien verarbeitet und aufnimmt
- Speicherkosten am Ziel für exportierte Dateien
- Größere Datenmengen pro Export im Vergleich zu inkrementellen Streaming-Aktualisierungen

**Experience League:**

- [Aktivieren von Zielgruppen für Batch-Profil-Exportziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Dateibasierter Zielkatalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### Option C: Aktivierung für mehrere Ziele

**Am besten geeignet für:** Sie dieselbe Zielgruppe gleichzeitig für mehrere Ziele aktivieren, z. B. indem Sie eine Unterdrückungsliste an alle Anzeigenplattformen senden, ein hochwertiges Segment mit sowohl CRM- als auch Anzeigenplattformen synchronisieren oder die Reichweite der Zielgruppe über mehrere Medienpartner hinweg koordinieren.

**Funktionsweise:**

Die Aktivierung für mehrere Ziele ist kein separater technischer Mechanismus, sondern eine Komposition von Optionen A und B, die über mehrere Zielverbindungen hinweg auf dieselbe Zielgruppe angewendet werden. Dieselbe Zielgruppe wird für zwei oder mehr Ziele mit jeweils einer eigenen Verbindungskonfiguration, Feldzuordnung und Planung aktiviert.

Jede Zielverbindung funktioniert unabhängig voneinander - eine Streaming-Aktivierung an Facebook und ein Batch-Export in S3 können gleichzeitig von derselben Quell-Zielgruppe ausgeführt werden. Feldzuordnungen werden pro Ziel konfiguriert, sodass verschiedene Attribute an verschiedene Systeme gesendet werden können, je nachdem, was jedes Ziel erfordert und welche Governance-Richtlinien zulässig sind.

Dies ist ein gängiges Produktionsmuster für Organisationen, die über mehrere Anzeigenplattformen hinweg arbeiten, die CRM-Synchronisierung zusammen mit der Medienaktivierung aufrechterhalten oder Zielgruppendaten sowohl an operative als auch an analytische Systeme verteilen müssen.

**Wichtige Aspekte:**

- Jedes Ziel verfügt über unabhängige Feldzuordnungen, Zeitpläne und Governance-Bewertungen
- Governance-Richtlinien werden pro Ziel durchgesetzt. Für verschiedene Zieltypen können unterschiedliche Attribute zulässig sein
- Eine einzelne Zielgruppe kann gleichzeitig für eine Mischung aus Streaming- und Batch-Zielen aktiviert werden
- Das Hinzufügen eines neuen Ziels erfordert keine Änderungen an vorhandenen Aktivierungen

**Vorteile:**

- Koordinierte Zielgruppenverteilung über alle externen Systeme von einer einzigen Zielgruppendefinition aus
- Die unabhängige Konfiguration pro Ziel ermöglicht optimierte Zuordnungen und Zeitpläne
- Die Durchsetzung der Governance pro Ziel stellt die Compliance über verschiedene Zieltypen hinweg sicher
- Zentralisiert die Verwaltung von Audiences und unterstützt gleichzeitig die verteilte Aktivierung

**Einschränkungen:**

- Mehr Zielverbindungen zum Konfigurieren, Authentifizieren und Verwalten
- Die Komplexität der Überwachung steigt mit jedem Ziel - Aktivierungsfehler müssen pro Ziel verfolgt werden
- Die Lizenznutzung (aktivierte Profile) kann je nach Berechtigungen pro Ziel zählen
- Die Pflege der Feldzuordnung über mehrere Ziele hinweg erfordert die Koordinierung

**Experience League:**

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)

### Vergleich von Optionen

| Kriterien | Option A: Streaming | Option B: Batch (Dateiexport) | Option C: Mehrere Ziele |
| --- | --- | --- | --- |
| Am besten geeignet für | Targeting und Unterdrückung von Echtzeit-Anzeigenplattformen | Data Warehouse-Anreicherung, dateibasierte Systemintegration | Koordinierte plattformübergreifende Zielgruppen-Verteilung |
| Komplexität | Niedrig | Mittel | Hoch |
| Latenz | Minuten (nahezu in Echtzeit) | Stunden (geplant) | Mischung aus Minuten und Stunden pro Ziel |
| Dateiformatsteuerung | Keine (Ziel bestimmt Format) | Vollständig (CSV, JSON, Parquet, Komprimierung, Benennung) | Pro Ziel |
| Zielgruppenauswertung | Streaming oder Edge erforderlich | Beliebige Methode (Batch, Streaming, Edge) | Anforderungen pro Ziel |
| Erfordert | Streaming-Ziel-Connector, für Streaming geeignetes Segment | Dateibasierter Ziel-Connector, Speicheranmeldeinformationen | Mehrere Ziel-Connectoren und Anmeldeinformationen |
| Governance | Auswertung eines einzelnen Ziels | Auswertung eines einzelnen Ziels | Evaluierung vor dem Ziel |

### Wählen der richtigen Option

Verwenden Sie die folgende Entscheidungslogik, um den richtigen Implementierungsansatz auszuwählen:

1. **Wie viele Ziele benötigen Sie?** Wenn Sie dieselbe Zielgruppe für zwei oder mehr Ziele aktivieren müssen, implementieren Sie Option C (die die Optionen A und B pro Ziel zusammensetzt). Fahren Sie mit den Fragen 2 und 3 für jedes Ziel fort.

2. **Unterstützt das Ziel Streaming?** Wenn das Ziel eine Anzeigenplattform (Facebook, Google Ads, LinkedIn, The Trade Desk) oder eine Partnerintegration mit einer Streaming-API ist, verwenden Sie Option A für dieses Ziel. Wenn das Ziel Cloud-Speicher (S3, Azure Blob, GCS, SFTP) oder ein System ist, das Dateien verbraucht, verwenden Sie Option B.

3. **Wie schnell muss die Zielgruppe am Ziel ankommen?** Wenn die Zielgruppenzugehörigkeit innerhalb von Minuten am Ziel widerspiegeln muss (z. B. Echtzeitunterdrückung während aktiver Kampagnen), verwenden Sie Option A. Wenn die tägliche oder mehrstündige Bereitstellung ausreicht (z. B. wöchentliche Data Warehouse-Aktualisierung, CRM-Batch-Synchronisierung), verwenden Sie Option B.

4. **Verwendet Ihre Zielgruppe eine komplexe Segmentierungslogik?** Wenn die Zielgruppendefinition Aggregationen mit mehreren Ereignissen, große Zeitfenster oder Funktionen enthält, die nicht für die Streaming-Auswertung qualifiziert sind, verwenden Sie Option B (Batch-Ziele) oder stellen Sie sicher, dass Option A-Ziele auch Batch-bewertete Zielgruppen nach einem Zeitplan empfangen.

## Implementierungsphasen

Die Implementierung folgt diesen Phasen. Jede Phase enthält Konfigurationsdetails, Entscheidungspunkte und Links zur Experience League-Dokumentation.

### Phase 1: Evaluierung der Zielgruppe

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung, RT-CDP: Zielgruppenkomposition

**Was Sie konfigurieren werden:** Definieren Sie die Zielgruppe, die für Ziele aktiviert wird. Dazu gehört die Angabe der Zielgruppenkriterien (welche Profile qualifiziert sind), die Auswahl der Auswertungsmethode (wie schnell die Mitgliedschaft aktualisiert wird) und die Validierung der Zielgruppenpopulation. Dies ist der Ausgangspunkt für jede Aktivierung - ohne eine definierte und ausgewertete Zielgruppe gibt es nichts zu aktivieren.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Methode zur Zielgruppenerstellung**
>
>Wie sollte die Zielgruppe definiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Segment Builder (regelbasiert) | Standardmäßige Zielgruppendefinition mit Profilattributen, Verhaltensereignissen und Bedingungen für die Segmentzugehörigkeit | Flexibelste Regeldefinition; unterstützt Streaming und Edge-Auswertung für geeignete Ausdrücke; ideal für Audiences mit nur einer Bedingung oder mäßig komplexen Audiences |
>| Audience-Komposition | Zielgruppe muss kombiniert, sortiert, aufgeteilt oder vorhandene Zielgruppen ausgeschlossen werden | Visuelle Arbeitsfläche für sequenzielle Vorgänge; Ergebnisse werden nur per Batch ausgewertet; maximal 10 Kompositionsblöcke pro Arbeitsfläche |
>| Federated Audience-Komposition | Zielgruppenkriterien müssen anhand von Daten in externen Data Warehouses bewertet werden, ohne sie in AEP aufzunehmen | Direkte Abfrage externer Datenbanken; Vermeidung von Datenduplizierung; Erfordert Federated Audience Composition-Lizenz |

>[!NOTE]
>
>**Entscheidung: Auswertungsmethode**
>
>Wie schnell müssen Profile in die Audience eintreten und sie verlassen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Batch | Geplante Kampagnen, tägliche Zielgruppenaktualisierungen oder komplexe Segmentierungslogik, die nicht für das Streaming qualifiziert ist | Verarbeitet bis zu 24 Millionen Profile pro Auftrag; alle Segmentierungsfunktionen werden unterstützt; wird nach einem Zeitplan ausgeführt (täglicher standardmäßiger oder benutzerdefinierter Cron-Zeitplan) |
>| Streaming | Änderungen der Zielgruppenzugehörigkeit in Echtzeit, die für die Aktivierung des Streaming-Ziels oder ereignisgesteuerte Anwendungsfälle erforderlich sind | Fast in Echtzeit (Sekunden bis Minuten); Eingeschränkte Segmentierungsfunktion festgelegt - einfache Ereignisse, Attributvergleiche und begrenzte Zeitfenster; keine Abfragen mehrerer Entitäten |
>| Edge | Personalisierung derselben Seite oder sofortige Zielgruppen-Qualifizierung, die am Edge erforderlich ist | Millisekunden-Latenz; restriktivster Regelsatz - Profilattribute und nur einfache Segmentzugehörigkeitsprüfungen; wird hauptsächlich für die Personalisierung vor Ort verwendet (weniger häufig für die Zielaktivierung) |

>[!NOTE]
>
>**Entscheidung: Zusammenführungsrichtlinie**
>
>Welche Zusammenführungsrichtlinie sollte die Zielgruppenbewertung verwenden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Zeitstempel geordnet (Standard) | Die meisten Anwendungsfälle - Aktuelle Daten sollten bei Konflikten mit Profilfragmenten Vorrang haben | Häufigste; verwendet den zuletzt aktualisierten Attributwert |
>| Datensatzpriorität | Bestimmte Datenquellen sollten andere unabhängig vom Zeitstempel überschreiben | Erfordert die Definition einer Datensatz-Prioritätsreihenfolge. Nützlich, wenn ein CRM-Aufzeichnungssystem stets die im Web erfassten Daten überschreiben soll |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen (für Segment Builder) oder Zielgruppe erstellen (für Zielgruppenkomposition)

**Wichtige Konfigurationsdetails:**

- Definieren von Zielgruppenkriterien basierend auf dem Anwendungsfall - Profilattribute, Verhaltensereignisse, Segmentzugehörigkeit oder zeitbasierte Bedingungen
- Wenden Sie Unterdrückungsregeln an, um Profile auszuschließen, die nicht aktiviert werden sollen (z. B. kürzlich konvertierte, global abgemeldete Profile)
- Überprüfen Sie die Größe der Zielgruppenpopulation, bevor Sie mit der Aktivierung fortfahren.
- Bestätigen Sie, dass die Auswertungsmethode dem in Phase 2 ausgewählten Zieltyp entspricht

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Streaming-Zielaktivierung):**
Die Zielgruppe muss Streaming oder Edge-Auswertung verwenden, um Mitgliedschaftsaktualisierungen in Echtzeit bereitzustellen. Überprüfen Sie, ob der Segmentregelausdruck für die Streaming-Auswertung geeignet ist - vermeiden Sie zeitbasierte Aggregationsfunktionen, Abfragen mehrerer Entitäten und `inSegment()` auf Segmente, die nur Batch sind.

**Für Option B (Batch-Zielaktivierung):**
Jede Auswertungsmethode funktioniert. Die Batch-Auswertung ist die häufigste Wahl, da der Export selbst nach einem Zeitplan ausgeführt wird. Bestätigen, dass in der Sandbox ein Batch-Auswertungszeitplan vorhanden ist, oder erstellen Sie einen.

**Für Option C (Aktivierung für mehrere Ziele):**
Die Auswertungsmethode sollte das anspruchsvollste Ziel berücksichtigen. Wenn für ein Ziel Streaming erforderlich ist, sollte die Zielgruppe die Streaming-Auswertung verwenden. Wenn alle Ziele Batch-Verarbeitung sind, ist eine Batch-Auswertung ausreichend.

**Dokumentation zu Experience League:**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Auswertungsmethoden](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home#evaluation-methods)


### Phase 2: Zielkonfiguration

**Anwendungsfunktion:** RT-CDP: Zielkonfiguration

**Was Sie konfigurieren werden:** Stellen Sie authentifizierte Verbindungen zu den externen Zielen her, an denen Zielgruppen veröffentlicht werden. Dazu gehört die Auswahl des Ziels im Katalog, die Bereitstellung von Authentifizierungsberechtigungen und die Konfiguration zielspezifischer Parameter wie Dateiformat, Speicherort und Exportplanung. Jedes Ziel erfordert eine eigene Verbindungskonfiguration.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Zieltyp**
>
>Wo sollten Zielgruppen bereitgestellt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Advertising-Ziel (Streaming) | Targeting oder Unterdrückung auf Anzeigenplattformen (Facebook, Google Ads, LinkedIn, The Trade Desk usw.) | Streaming-Connectoren; Mitgliedschaftsaktualisierungen nahezu in Echtzeit; Identitätsabgleich über gehashte E-Mail-, Telefon- oder Geräte-IDs |
>| Cloud-Speicher-Ziel (Batch) | Exportieren in S3, Azure Blob, GCS, SFTP oder Data Landing Zone zur Data Warehouse-Anreicherung | Dateibasierter Export; konfigurierbares Format (CSV, JSON, Parquet); geplante Kadenz |
>| CRM-Ziel | Synchronisieren von Zielgruppen mit Salesforce, Microsoft Dynamics oder HubSpot zur Unterstützung des Verkaufs | Normalerweise für Streaming; CRM-spezifische Feldzuordnung erforderlich; möglicherweise CRM-Administratorberechtigungen erforderlich |
>| Ziel des Datenpartners | Audiences-Daten für Mess- oder Zielgruppenbestimmungspartner freigeben | Variiert je nach Partner; Auswirkungen der externen Datenfreigabe auf die Governance überprüfen |
>| Benutzerdefiniertes Ziel (Destination SDK) | Zielsystem nicht im Katalog verfügbar | Erfordert das Erstellen eines benutzerdefinierten Ziels mithilfe der Destination SDK; höherer Implementierungsaufwand |

>[!NOTE]
>
>**Entscheidung: Authentifizierungsmethode**
>
>Welche Anmeldeinformationen benötigt das Ziel?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| OAuth 2.0 | Werbeplattformen und SaaS-Ziele (Facebook, Google, Salesforce) | Erfordert anfänglichen Autorisierungsfluss; Token werden automatisch aktualisiert; am häufigsten für Streaming-Ziele |
>| Zugriffsschlüssel/Geheimschlüssel | Cloud-Speicher (S3, Azure Blob) | Statische Anmeldeinformationen; Rotation sollte geplant werden; geeignet für dateibasierte Ziele |
>| Dienstkonto/API-Schlüssel | Partner-APIs und benutzerdefinierte Integrationen | Bereitstellung der Anmeldeinformationen vom Zielpartner erforderlich |
>| Verbindungszeichenfolge | Azure-basierte Ziele | Einzelne Zeichenfolge, die alle Verbindungsparameter enthält |

>[!NOTE]
>
>**Entscheidung: Exporttyp (nur Batch-Ziele)**
>
>Wie sollten Zielgruppendaten für den Export verpackt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Inkrementeller Export | Nur neue Qualifikationen und Disqualifikationen seit letztem Export | Kleinere Dateigrößen, schnellere Verarbeitung am Ziel, Erfordert, dass das Zielsystem den Status beibehält |
>| Vollständiger Export | Zielgruppen-Snapshot bei jeder Ausführung abschließen | Größere Dateien; Ziel erhält jedes Mal ein vollständiges Bild; einfacher für Systeme, die einen vollständigen Ersatz durchführen |

**UI-Navigation:** Verbindungen > Ziele > Katalog > [Ziel auswählen] > Konfigurieren

**Wichtige Konfigurationsdetails:**

- Durchsuchen Sie den Zielkatalog und wählen Sie das Ziel aus
- Geben Sie Authentifizierungsdaten an und testen Sie die Verbindung
- Für Batch-Ziele: Konfigurieren des Dateiformats (CSV, JSON, Parquet), der Komprimierung, der Dateibenennungsvorlage und des Exportzeitplans
- Für Streaming-Ziele: Die Verbindung wird normalerweise über den OAuth-Autorisierungsfluss hergestellt
- Stellen Sie sicher, dass der Status der Zielverbindung als aktiv angezeigt wird, bevor Sie mit der Aktivierung fortfahren

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Streaming-Zielaktivierung):**
Wählen Sie ein Streaming-Ziel aus dem Katalog aus (Advertising- oder Social-Media-Kategorien). Schließen Sie den OAuth-Autorisierungsfluss ab. Die Verbindung ist bereit zur Aktivierung, sobald die Autorisierung bestätigt wurde.

**Für Option B (Batch-Zielaktivierung):**
Wählen Sie ein dateibasiertes Ziel aus dem Katalog (Kategorie Cloud-Speicher) aus. Konfigurieren Sie den Speicherpfad, das Dateiformat, die Komprimierung, die Benennungskonvention und den Exportzeitplan. Testen Sie die Verbindung, indem Sie den Schreibzugriff auf den Speicherort überprüfen.

**Für Option C (Aktivierung für mehrere Ziele):**
Wiederholen Sie diese Phase für jedes Ziel. Jede Verbindung ist unabhängig - Sie können eine Mischung aus Streaming- und Batch-Zielen haben. Dokumentieren Sie die Authentifizierung und Konfiguration jeder Verbindung als betriebliche Referenz.

**Dokumentation zu Experience League:**

- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Aktivieren von Zielgruppen für Batch-Profil-Exportziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Übersicht über Destination SDK](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/destination-sdk/overview)
- [Destination SDK-Konfigurationsoptionen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### Phase 3: Zielgruppenaktivierung

**Anwendungsfunktion:** RT-CDP: Audience Activation

**Was Sie konfigurieren werden:** Veröffentlichen Sie die ausgewertete Zielgruppe im konfigurierten Ziel, indem Sie den Aktivierungsdatenfluss erstellen. Dazu gehört die Auswahl der zu aktivierenden Zielgruppen, die Zuordnung von Profilattributen zu Zielfeldern und die Konfiguration des Exportplans. Der Aktivierungsdatenfluss verbindet die Quell-Audience mit dem Ziel und verwaltet die fortlaufende Datenbereitstellung.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Attributzuordnung**
>
>Welche Profilattribute sollen in die Aktivierung einbezogen werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Identitätsfelder | Das Ziel muss nur Profilen entsprechen (z. B. Zielgruppenzugehörigkeit in Werbeplattformen) | Minimale Datenübertragung; am meisten datenschutzsicher; typisch für Anzeigenplattform-Targeting und -Unterdrückung |
>| Identität + Profilattribute | Ziel benötigt Anreicherungsattribute für Personalisierung oder Segmentierung (z. B. CRM-Synchronisierung, Partnerfreigabe) | Mehr Daten werden übertragen; erfordert eine Überprüfung der Governance für jedes Attribut; überprüft die Datennutzungskennzeichnungen anhand der Ziel-Marketing-Aktion |
>| Identität + berechnete Attribute | Zielvorteile aus abgeleiteten Scores oder Aggregationen (z. B. Lebensdauerwert-Stufe, Tendenzwert für Partner-Targeting) | Erfordert die Konfiguration berechneter Attribute; Anreicherung mit hohem Wert für nachgelagerte Systeme |

>[!NOTE]
>
>**Entscheidung: Exportplanung (nur Batch-Ziele)**
>
>Wie oft sollten Zielgruppendaten exportiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Täglich | Standard-Aktualisierungskadenz; die meisten Batch-Anwendungsfälle | Ermöglicht einen Ausgleich zwischen Frische und Verarbeitungskosten; die häufigste Standardeinstellung |
>| Alle 3-6 Stunden | Häufigere Anwendungsfälle wie die Optimierung von Intra-Day-Kampagnen | Häufigere Dateigenerierung, höhere Speicher- und Verarbeitungslast am Ziel |
>| On-Demand (Ad-hoc) | Einmaliger Export oder dringende Aktivierung außerhalb des Zyklus | Manueller Zeitplan für Trigger-Umgehungen; nützlich für Tests oder dringende Kampagnenanforderungen |

**UI-Navigation:** Verbindungen > Ziele > Durchsuchen > [Ziel auswählen] > Zielgruppen aktivieren

**Wichtige Konfigurationsdetails:**

- Eine oder mehrere Zielgruppen auswählen, die für das Ziel aktiviert werden sollen
- Zuordnen von Profilattributen und Identitätsfeldern zu zielspezifischen Feldern
- Für Streaming-Ziele: Bestätigung der Identity-Namespace-Zuordnung (z. B. gehashte E-Mail an die extern_id von Facebook)
- Für Batch-Ziele: Konfigurieren Sie den Exportplan, wählen Sie den inkrementellen oder vollständigen Exportmodus aus und legen Sie das erste Exportdatum fest
- Überprüfen Sie vor der Veröffentlichung die Aktivierungszusammenfassung, um alle Zuordnungen und Zeitpläne zu bestätigen

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Streaming-Zielaktivierung):**
Wählen Sie die Zielgruppen aus und ordnen Sie Identity-Namespaces Ziel-Identitätsfeldern zu. Die Aktivierung beginnt unmittelbar nach der Veröffentlichung — Änderungen der Zielgruppenzugehörigkeit werden nahezu in Echtzeit an das Ziel gestreamt. Es ist kein Exportzeitplan erforderlich; die Aktivierung ist kontinuierlich.

**Für Option B (Batch-Zielaktivierung):**
Wählen Sie die Zielgruppen aus, ordnen Sie Profilattribute zu und konfigurieren Sie den Exportzeitplan. Wählen Sie zwischen dem inkrementellen und dem vollständigen Exportmodus. Optional können Sie einen Ad-hoc-Export für einen sofortigen Versand außerhalb des regulären Triggers erstellen.

**Für Option C (Aktivierung für mehrere Ziele):**
Wiederholen Sie den Aktivierungs-Workflow für jedes Ziel. Dieselbe Zielgruppe kann für mehrere Ziele mit unterschiedlichen Attributzuordnungen pro Ziel aktiviert werden. Senden Sie beispielsweise nur gehashte E-Mails an Anzeigenplattformen, aber fügen Sie dem CRM demografische Attribute hinzu.

**Dokumentation zu Experience League:**

- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Profil-Exportziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Zielgruppen bei Bedarf für Batch-Ziele aktivieren](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)


### Phase 4: Governance-Validierung

**Anwendungsfunktion:** RT-CDP: Durchsetzung von Einverständnis und Governance

**Was Sie konfigurieren werden:** Überprüfen Sie, ob Governance-Richtlinien und Einverständnisvoreinstellungen vor und während der Aktivierung korrekt durchgesetzt werden. In dieser Phase wird sichergestellt, dass eingeschränkte Daten (personenbezogene Daten, vertrauliche Attribute) nicht an nicht autorisierte Ziele gesendet werden und dass Profile ohne gültiges Einverständnis von der Aktivierung ausgeschlossen werden. Die Durchsetzung der Governance erfolgt automatisch zum Zeitpunkt der Aktivierung, aber die proaktive Validierung verhindert blockierte Aktivierungen und Compliance-Verstöße.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Governance-Durchsetzungsansatz**
>
>Wann sollte die Einhaltung der Governance-Regeln validiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Proaktiv (vor der Aktivierung) | Empfohlen für alle Implementierungen, insbesondere bei der Aktivierung für externe Drittanbietersysteme | Überprüfen Sie Datennutzungsbeschriftungen und -richtlinien, bevor Sie Feldzuordnungen konfigurieren. Verhindert Aktivierungsfehler und stellt die Einhaltung von Anfang an sicher |
>| Reaktiv (zum Zeitpunkt der Aktivierung) | Wenn die Governance-Richtlinien bereits fest etabliert sind und das Team auf die Einhaltung der Richtlinien vertraut | Platform erzwingt bei der Aktivierung automatisch Richtlinien; Verstöße blockieren die Aktivierung oder schließen eingeschränkte Attribute aus; kann zu unerwarteten Fehlern führen, wenn Richtlinien nicht gut verstanden werden |

>[!NOTE]
>
>**Entscheidung: Einverständnisfilterung**
>
>Wie sollten sich Einverständnisvoreinstellungen auf die Aktivierung auswirken?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einverständnisdurchsetzung aktiviert | Erforderlich bei der Aktivierung für Werbe- oder Marketing-Ziele, für die die Einwilligung gesetzlich vorgeschrieben ist | Profile ohne gültiges Einverständnis (consents.marketing.{channel}.val = &#39;y&#39;) werden automatisch von der Aktivierung ausgeschlossen; erfordert die Aufnahme von Einverständnisdaten |
>| Keine Einverständnisfilterung | Interne Analyseziele oder -exporte, bei denen die Zustimmung nicht für die Datenübertragung gilt | Nur angemessen, wenn die Verwendung der Daten keine Marketing-Aktion darstellt, die eine Einwilligung erfordert; konsultieren Sie das Legal/Privacy-Team |

**UI-Navigation:** Datenschutz > Richtlinien > Einverständnisrichtlinien (zur Überprüfung des Einverständnisses); Data Governance > Richtlinien (zur Überprüfung der Datennutzungsrichtlinien)

**Wichtige Konfigurationsdetails:**

- Überprüfen Sie die Datennutzungsbeschriftungen, die auf die Datensätze und Schemafelder angewendet werden, die aktiviert werden
- Überprüfen Sie, ob Governance-Richtlinien für die mit dem Ziel verknüpfte Marketing-Aktion aktiv sind (z. B. „Export an Dritte“ für Anzeigenplattformen)
- Bestätigen Sie, dass die Einverständnisfelder in Profilen ausgefüllt werden und dass die Einverständnisdurchsetzung für die entsprechenden Kanäle aktiviert ist
- Wenn Richtlinienverletzungen erkannt werden, beheben Sie diese, indem Sie eingeschränkte Felder aus der Zielzuordnung entfernen oder ein alternatives Ziel auswählen

**Dokumentation zu Experience League:**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/enforcement/overview)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Durchsetzung von Einverständnisrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/policies/user-guide)


### Phase 5: Überwachung und Validierung

**Anwendungsfunktion:** Monitoring &amp; Observability

**Was Sie konfigurieren werden** Richten Sie die fortlaufende Überwachung für Aktivierungsdatenflüsse ein, konfigurieren Sie Warnhinweise für Fehler, validieren Sie die Zielgruppenpopulation an Zielen und verfolgen Sie die Lizenznutzung. Die Überwachung ist bei Produktionsaktivierungen von entscheidender Bedeutung, wenn sich Versandfehler direkt auf die Kampagnenleistung und die Medienausgaben auswirken.

**Wichtige Konfigurationsdetails:**

- Überprüfen Sie den Ausführungsstatus des Datenflusses für jedes aktive Ziel, um zu bestätigen, dass die Zielgruppen erfolgreich bereitgestellt werden
- Konfigurieren von Warnhinweisen für Fehler bei der Zielaktivierung, Datenflussverzögerungen und Anomalien der Zielgruppenpopulation
- Tracking exportierter Profile im Vergleich zu fehlgeschlagenen Profilen pro Datenflussausführung
- Überwachen der Übereinstimmungsraten der Zielgruppen am Ziel (sofern Zielberichte verfügbar sind)
- Lizenznutzung überprüfen, um das aktivierte Profilvolumen anhand von Berechtigungen zu verfolgen

**Benutzeroberflächennavigation:** Verbindungen > Ziele > Durchsuchen > [Ziel auswählen] > Datenflussausführungen (für die Aktivierungsüberwachung); Warnhinweise > Warnhinweisregeln > Abonnieren (für die Warnhinweiskonfiguration); Administration > Lizenznutzung (für die Lizenzverfolgung)

**Dokumentation zu Experience League:**

- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home)
- [Lizenznutzungs-Dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## Überlegungen bei der Implementierung

Beachten Sie die folgenden Überlegungen vor und während der Implementierung.

### Leitplanken und Beschränkungen

- **Segmentdefinitionslimit:** Maximal 4.000 Segmentdefinitionen pro Sandbox — [Segmentierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- **Datenflüsse pro Ziel:** Maximal 100 Datenflüsse pro Zielverbindung — [Leitplanken für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- **Größe der Batch-Exportdatei:** Dateibasierte Ziele haben maximale Dateigrößenbeschränkungen für den Export; große Zielgruppen werden automatisch auf mehrere Dateien aufgeteilt
- **Streaming-Zieldurchsatz:** Durchsatzbeschränkungen pro Sekunde werden von jedem Zielpartner festgelegt; Änderungen an großen Zielgruppen können gedrosselt werden
- **Batch-Auswertungskapazität:** bis zu 24 Millionen Profile pro Segmentauswertungsauftrag
- **Zielgruppenkomposition:** Maximal 10 Kompositionsblöcke pro Arbeitsfläche; zusammengesetzte Zielgruppen werden nur per Batch ausgewertet
- **Identitätsdiagramm:** Maximal 50 Identitäten pro Diagramm - [Identity Service-Leitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/identity/guardrails)
- **Berechnete Attribute:** Maximal 25 berechnete Attribute pro Sandbox - [Leitplanken für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Übersicht über Aktivierungsleitplanken:** [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)

### Häufige Fehler

- **Streaming-Segment mit nicht auswählbarer Regellogik:** Definieren einer Zielgruppe mit komplexen Aggregationsfunktionen oder Abfragen mehrerer Entitäten und Erwartung einer Streaming-Auswertung. Diese Segmente kehren im Hintergrund zur Batch-Auswertung zurück, was zu unerwarteter Latenz führt. Vorbeugung: Überprüfen Sie die Streaming-Eignungsanforderungen, bevor Sie die Zielgruppe definieren.

- **Aufgrund der Einverständnisfilterung wurden keine Profile exportiert:** Alle Profile in der Zielgruppe verfügen nicht über gültige Einverständniswerte, sodass die gesamte Zielgruppe zum Zeitpunkt der Aktivierung herausgefiltert wird. Vorbeugung: Überprüfen Sie, ob die Aufnahme von Einverständnisdaten funktionsfähig ist und dass die Einverständnisfelder vor der Aktivierung ausgefüllt werden.

- **Governance-Richtlinie blockiert unerwartete Aktivierung:** Datennutzungskennzeichnungen in Schemafeldern Trigger-Richtlinienverletzungen, die eine Aktivierung verhindern. Prävention: Bewerten Sie die Governance-Compliance proaktiv (Phase 4), bevor Sie Feldzuordnungen konfigurieren. Überprüfen Sie, welche Kennzeichnungen vom Schema übernommen werden.

- **Gültigkeit der Zielberechtigungen:** laufen OAuth-Token oder API-Schlüssel ab, was zu Aktivierungsfehlern ohne sofortigen Warnhinweis führt. Prävention: Konfigurieren von Warnhinweisen für Fehler bei der Zielaktivierung und Erstellen eines Zeitplans für die Rotation der Anmeldeinformationen.

- **Nicht übereinstimmende Identitäts-Namespaces:** Der in der Aktivierungszuordnung konfigurierte Identitäts-Namespace stimmt nicht mit den Erwartungen des Ziels überein (z. B. Senden von E-Mail-Nachrichten im Klartext, wenn das Ziel eine SHA-256-Hash-E-Mail erfordert). Prävention: Prüfen Sie die Zieldokumentation auf die erforderlichen Identitätsformate, bevor Sie die Zuordnung konfigurieren.

- **Feldzuordnungsfehler, die Exportfehler verursachen:** Zuordnen eines Profilattributs zu einem Zielfeld mit einem inkompatiblen Datentyp oder Format. Prävention: Testen Sie die Aktivierung zuerst mit einer kleinen Zielgruppe und überprüfen Sie die Details der Datenflussausführung auf Zuordnungsfehler, bevor Sie sie auf Produktions-Zielgruppen skalieren.

- **Zielgruppenpopulation drift zwischen RT-CDP und Ziel:** Die Zielgruppengröße in RT-CDP stimmt aufgrund von Unterschieden beim Identitätsabgleich, der Deduplizierungslogik des Ziels oder des Timings nicht mit der Anzahl am Ziel überein. Dies ist das erwartete Verhalten — Prävention: Dokumentieren Sie die erwarteten Übereinstimmungsraten-Benchmarks pro Ziel und überwachen Sie auf signifikante Abweichungen.

### Best Practices

- **Mit einer Test-Audience beginnen** Aktivieren Sie für jedes neue Ziel eine kleine, wohlverstandene Test-Audience, bevor Sie Produktions-Audiences aktivieren. Validieren von Feldzuordnungen, Identitätsabgleich und Versandmetriken mit der Testzielgruppe.

- **Frühzeitige Schicht-Governance** Wenden Sie Datennutzungskennzeichnungen an und konfigurieren Sie Governance-Richtlinien, bevor Sie Zielaktivierungen konfigurieren. Dadurch werden blockierte Aktivierungen verhindert und die Compliance von Anfang an sichergestellt.

- **Verwenden inkrementeller Exporte für Batch-Ziele:** Inkrementelle Exporte reduzieren Dateigrößen, beschleunigen die Verarbeitung am Ziel und minimieren die Speicherkosten. Verwenden Sie vollständige Exporte nur, wenn das Zielsystem einen vollständigen Austausch der Zielgruppe erfordert.

- **Benennungskonventionen standardisieren** Legen Sie eine konsistente Benennung für Zielgruppen, Zielverbindungen und Datenflüsse im gesamten Unternehmen fest. Schließen Sie den Anwendungsfall, das Ziel und die Auswertungsmethode in Namen ein (z. B. „Suppression_ExistingCustomers_Facebook_Streaming„).

- **Übereinstimmungsraten überwachen:** Verfolgen Sie das Verhältnis der von RT-CDP exportierten Profile zu den Profilen, die bei jedem Ziel abgeglichen werden. Signifikante Rückgänge der Übereinstimmungsrate können auf Probleme bei der Identitätsauflösung, Berechtigungsprobleme oder Änderungen der Ziel-API hinweisen.

- **Unterdrückung über Ziele hinweg koordinieren:** Wenn Sie Unterdrückungszielgruppen verwenden (z. B. vorhandene Kundinnen und Kunden von Akquise-Kampagnen ausschließen), aktivieren Sie die Unterdrückungszielgruppe gleichzeitig auf allen relevanten Anzeigenplattformen, um die Konsistenz zu gewährleisten.

- **Überprüfen und Bereinigen von inaktiven Aktivierungen:** Überprüfen Sie regelmäßig Zieldatenflüsse und deaktivieren Sie nicht mehr benötigte Zielgruppen. Inaktive Aktivierungen beanspruchen Lizenzkapazität und verursachen zusätzlichen Überwachungsaufwand.

### Entscheidungen über Kompromisse

>[!NOTE]
>
>**Kompromiss: Zielgruppenfrische vs. Segmentierungsflexibilität**
>
>Die Streaming-Auswertung liefert nahezu in Echtzeit Aktualisierungen für Zielgruppen, schränkt jedoch die Segmentregelfunktionen ein, die Sie verwenden können. Die Batch-Auswertung unterstützt den vollständigen Regelsatz für Segmente, führt jedoch zu einer Latenz (Stunden statt Minuten).
>
>- **Streaming-Vorteile:** Echtzeit-Anwendungsfälle, bei denen die Zielgruppenzugehörigkeit innerhalb von Minuten am Ziel widerspiegeln muss (aktive Kampagnenunterdrückung, Echtzeit-Retargeting)
>- **Batch-Vorteile:** Komplexe Zielgruppenlogik, die Aggregationsfunktionen, Abfragen mit mehreren Entitäten oder Bedingungen mit großen Zeitfenstern (Lebensdauerwertstufen, Multi-Touch-Verhaltenssegmente) erfordert
>- **Empfehlung:** Verwenden Sie die Streaming-Auswertung für Zielgruppen, die für Streaming-Ziele aktiviert sind, bei denen eine Echtzeit-Frische den Geschäftswert steigert. Verwenden Sie die Batch-Auswertung für komplexe Zielgruppen, die für dateibasierte Ziele aktiviert wurden oder wenn eine tägliche Aktualisierung ausreicht. Für Zielgruppen, die beide benötigen, sollten Sie zwei Versionen erstellen: ein vereinfachtes Streaming-Segment für die Echtzeit-Aktivierung und ein umfassendes Batch-Segment für die periodische Anreicherung.

>[!NOTE]
>
>**Kompromiss: Minimaler Datenexport vs. Rich-Attribut-Zuordnung**
>
>Der reine Export von Identitätsfeldern (gehashte E-Mail, Geräte-ID) minimiert die Gefährdung der Daten und vereinfacht die Governance. Der Export zusätzlicher Profilattribute (Demografie, Wertestufe, Interaktionswert) bereichert das Ziel, erhöht jedoch die Komplexität der Governance und die Haftung für Daten.
>
>- **Minimale Exportvorteile:** Ansatz „Datenschutz zuerst“; geringeres Governance-Risiko; einfachere Feldzuordnung; ausreichend für die meisten Anwendungsfälle für das Targeting und die Unterdrückung von Anzeigenplattformen
>- **Rich-Export-Vorteile:** nachgelagerte Personalisierung am Ziel; CRM-Anreicherung; Partnerdatenfreigabe, die Details auf Attributebene erfordert
>- **Empfehlung:** Standardeinstellung ist „Nur minimale Identitätsexporte“ für Werbeziele. Fügen Sie Profilattribute nur dann hinzu, wenn der Zielanwendungsfall dies speziell erfordert und die Governance-Überprüfung die Einhaltung der Vorgaben bestätigt. Verwenden Sie berechnete Attribute, um aggregierte, weniger empfindliche Anreicherungswerte anstelle von rohen PII bereitzustellen.

>[!NOTE]
>
>**Kompromiss: Eine Zielgruppe pro Ziel und konsolidierte Datenflüsse mit mehreren Zielgruppen**
>
>Die Aktivierung jeder Audience als separaten Datenfluss bietet Isolation und granulare Überwachung. Die Aktivierung mehrerer Zielgruppen über einen einzelnen Datenfluss zu einem Ziel vereinfacht die Verwaltung, reduziert jedoch die Isolation.
>
>- **Separate Datenflüsse begünstigen** Unabhängige Überwachung, einfachere Fehlerbehebung, Möglichkeit, individuelle Zielgruppenaktivierungen anzuhalten, ohne andere zu beeinflussen
>- **Konsolidierte Datenflüsse begünstigen** Weniger Verbindungen zu verwalten, vereinfachtes Berechtigungsverwaltung, geringerer Betriebsaufwand
>- **Empfehlung:** Sie konsolidierte Datenflüsse, wenn Sie mehrere verwandte Zielgruppen für dasselbe Ziel aktivieren (z. B. alle Unterdrückungssegmente für Facebook). Verwenden Sie separate Datenflüsse, wenn Zielgruppen unterschiedliche SLAs, unterschiedliche Attributzuordnungen oder eine Fehlerisolierung aufweisen.

## Verwandte Dokumentation

**Ziele**

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Profil-Exportziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Zielgruppen bei Bedarf für Batch-Ziele aktivieren](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Leitplanken für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- [Übersicht über Destination SDK](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/destination-sdk/overview)

**Zielgruppen und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)

**Identität und Profil**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)

**Datenmodellierung und Schemata**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition)

**Data Governance**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Data Governance-Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/policies/overview)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/enforcement/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Überwachung und Beobachtbarkeit**

- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home)
- [Lizenznutzungs-Dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Berechnete Attribute**

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/ui)

**Datenerfassung und Quellen**

- [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)

**Administration**

- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)
- [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home)
- [Attributbasierte Zugriffssteuerung](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/abac/overview)

**Leitplanken**

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/guardrails)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/de/docs/experience-platform/ingestion/guardrails)
