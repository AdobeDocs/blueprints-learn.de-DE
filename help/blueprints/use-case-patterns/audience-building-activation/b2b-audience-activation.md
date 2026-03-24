---
title: B2B-Audience Activation
description: Erfahren Sie, wie Sie Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren.
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7611'
ht-degree: 0%

---

# B2B-Zielgruppenaktivierung

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für die Aktivierung Account-basierter B2B-Zielgruppen mit [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die Zielgruppen auf Kontoebene über Web-, E-Mail-, Werbe- und CRM-Kanäle erstellen, auswerten und aktivieren müssen.

Es deckt den gesamten Lebenszyklus ab, von der Vereinheitlichung von Account-Profilen über die Bewertung und Aktivierung von Audiences bis hin zu B2B-spezifischen Zielen wie [!DNL Marketo Engage]-, [!DNL LinkedIn]- und CRM-Systemen. Alle praktikablen Implementierungsansätze werden mit Kompromissen und Entscheidungshilfen präsentiert, die Sie bei der Auswahl des richtigen Pfads für Ihr Unternehmen unterstützen.

## Anwendungsfall - Übersicht

B2B-Marketing-Teams müssen Zielgruppen auf Kontoebene und nicht auf der Ebene einzelner Personen ansprechen und aktivieren. Im Gegensatz zur B2C-Zielgruppenaktivierung, bei der die Zielgruppenbestimmungseinheit ein einzelnes Kundenprofil ist, erfordert die B2B-Zielgruppenaktivierung, dass Sie die Beziehung zwischen Personen und den Konten, zu denen sie gehören, verstehen, die Zielgruppenzugehörigkeit auf der Grundlage von Attributen auf Kontoebene in Kombination mit Interaktionssignalen auf Personenebene bewerten und diese Zielgruppen an Ziele bereitstellen, die Account-basiertes Targeting unterstützen.

[!DNL RT-CDP] B2B edition erweitert die [!DNL Real-Time Customer Data Platform] um spezielle XDM-Klassen für Konten, Opportunitys und Kampagnen sowie eine B2B-Identitätsauflösung, die Person-zu-Account-Beziehungen zuordnet. Dadurch können Marketing-Experten Account-Zielgruppen erstellen, die firmografische Daten (Branche, Umsatz, Mitarbeiteranzahl), technische Daten (Technologie-Stack, Produktnutzung) und Verhaltensdaten (Web-Besuche, E-Mail-Interaktion, Ereignisteilnahme) der mit diesen Accounts verknüpften Personen kombinieren.

Die aktivierten Account-Zielgruppen ermöglichen Anwendungsfälle für die Nachfragegenerierung in funnel: Top-of-funnel-Awareness-Kampagnen zu [!DNL LinkedIn] und Display-Werbung, Mid-funnel-Nurture-Programme in [!DNL Marketo Engage] und funnel-Verkaufsförderung auf unterster Ebene durch CRM-Integration. Zielgruppen zur Kontounterdrückung verhindern verschwendete Ausgaben, indem bestehende Kunden, abgeschlossene Konten oder Konten, die sich bereits in aktiven Verkaufszyklen befinden, ausgeschlossen werden.

>[!NOTE]
>Wenn Ihr Anwendungsfall die Aktivierung von Zielgruppen auf Personenebene (B2C) statt auf Kontoebene beinhaltet, finden Sie weitere Informationen unter [Zielgruppenaktivierung für Ziele](audience-activation-to-destinations.md). Dieses Muster verwendet das standardmäßige RT-CDP-Datenmodell und erfordert keine B2B edition.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Lead-Generierung erhöhen

Generieren Sie durch Formulare, Ereignisse, Inhalte und kanalübergreifende Interaktionen besser qualifizierte Leads für die Vertriebs-Pipeline.

**KPIs:** Interessenten, Kosten pro Lead, Lead-Konversion

[Weitere Informationen zur Steigerung der Lead-Generierung](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Verbessern der Lead-Qualifizierung und -Konversion

Erhöhen Sie die Lead-Qualität und beschleunigen Sie den Pipeline-Fortschritt durch Bewertung, Pflege und personalisierte Nachverfolgung.

**KPIs:** Lead-Konversion, Interessenten-/Lead-Konversion, Effizienz

[Erfahren Sie mehr über die Verbesserung der Lead-Qualifizierung und -Konversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung.

**KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion

[Weitere Informationen über die Akquise von Neukunden](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung.

**KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen

[Erfahren Sie mehr über die Optimierung von Marketing-Ausgaben und ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie dieses Muster in der Praxis angewendet werden kann.

- **Account-based Advertising on[!DNL LinkedIn]** - Targeting von Accounts, die Ihrem Idealkundenprofil (ICP) entsprechen, mit gesponserten Inhalten und InMail-Kampagnen auf [!DNL LinkedIn], unter Verwendung von Account-Listen, die von [!DNL RT-CDP] B2B edition aktiviert werden
- Zielgruppenbestimmung **[!DNL Marketo Engage]Nurture-**: Aktivieren Sie Account-Zielgruppen, um [!DNL Marketo Engage] verknüpfte Leads und Kontakte basierend auf Qualifizierungskriterien auf Account-Ebene für die gezielte Pflege zu registrieren
- **Synchronisation der CRM-**: Übertragen von Listen qualifizierter Konten an [!DNL Salesforce] oder [!DNL Microsoft Dynamics], um die Sichtbarkeit des Vertriebsteams, die Gebietszuweisung und die Workflows für ausgehende Kundenakquise zu gewährleisten
- **Kontounterdrückung für bezahlte Medien** - Unterdrückt bestehende Kunden, abgeschlossene Konten oder Konten in aktiven Verkaufszyklen von Paid-Akquise-Kampagnen, um verschwendete Ausgaben zu reduzieren
- **Absichtsbasiertes Konto-Targeting** - Kombinieren Sie Absichtssignale von Drittanbietern mit Interaktionsdaten von Erstanbietern auf Kontoebene, um Zielgruppen von marktinternen Konten zu identifizieren und zu aktivieren
- **Produkt-Crosssell an vorhandene Konten** - Erstellen Sie Zielgruppen von Konten mit einer Produktlinie, aber nicht mit einer anderen, und aktivieren Sie dann E-Mail- und Werbekanäle für Crosssell-Kampagnen
- **Ereignis- und Webinar-Targeting** - Aktivieren Sie Konto-Zielgruppen für Werbe- und E-Mail-Kanäle, um die Ereignisregistrierung von Zielkonten aus zu fördern
- **Wettbewerbsverdrängungskampagnen** - Targeting von Accounts unter Verwendung von Produkten von Mitbewerbern mit maßgeschneidertem Messaging, das über Werbe- und E-Mail-Kanäle aktiviert wird
- **Mehrstufige Kontointeraktion** - Segmentieren Sie Konten in Interaktionsstufen (hoch, mittel, niedrig) basierend auf aggregierter Aktivität auf Personenebene und aktivieren Sie für jede Stufe differenzierte Kampagnen
- **Partner-Co-Marketing-Zielgruppen** - Teilen Sie Account-Zielgruppensegmente mit Channel-Partnern oder Co-Marketing-Programmen über Cloud-Speicher-Ziele

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Kontoreichweite | Anzahl der über Aktivierungskanäle hinweg erreichten Zielkonten | Tracking der pro Ziel aktivierten eindeutigen Konten |
| Kundeninteraktionsrate | Prozentsatz der aktivierten Konten mit Interaktionssignalen | Interaktion auf Personenebene aggregiert mit Konto messen |
| Pipeline-Einfluss | Umsatz-Pipeline, die Account-basierten Aktivierungskampagnen zugeordnet wurde | Verfolgen von mit aktivierten Account-Zielgruppen erstellten Opportunitys |
| Kosten pro engagiertem Konto | Marketingausgaben geteilt durch die Anzahl der Konten, die Interaktion anzeigen | Berechnung der Kosten für Werbung und E-Mail-Kanal |
| Lead-Konversionsrate | Prozentsatz der Leads von aktivierten Konten, die in Opportunities konvertiert wurden | Konversion von Lead zu Opportunity für aktivierte Zielgruppen verfolgen |
| Einsparungen bei der Zielgruppenunterdrückung | Durch Unterdrückung nicht förderfähiger Konten aus bezahlten Kampagnen vermiedene Kosten | Ausgabenreduzierung aus Unterdrückungszielgruppen messen |
| Account Coverage | Prozentsatz des gesamten adressierbaren Marktes (TAM), der von aktivierten Zielgruppen abgedeckt wird | Vergleichen aktivierter Konten mit dem gesamten ICP-Universum |

## Anwendungsfallmuster

**B2B-Zielgruppenaktivierung**

Account-basierte B2B-Zielgruppen über Web-, E-Mail- und Werbekanäle aktivieren.

**Funktionskette:** Kontoprofilanreicherung > Kontozielgruppenbewertung > Zielkonfiguration > Audience Activation > Überwachung

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Real-Time CDP]B2B edition** - Kernplattform für die Vereinheitlichung von Account-Profilen, B2B-Identitätsauflösung, Evaluierung der Account-Zielgruppe, B2B-spezifische Zielkonfiguration und Aktivierung der Account-Zielgruppe
- **[!DNL Adobe Experience Platform] (AEP)** - Grundlegende Infrastruktur für B2B-XDM-Datenmodellierung, Datenaufnahme aus CRM- und Marketing-Automatisierungsquellen, Identity Service und Governance
- **[!DNL Marketo Engage]** - Primäres B2B-Marketing-Automatisierungsziel für Lead-Nurture-Programme, Scoring und Kampagnenausführung, die von aktivierten Account-Zielgruppen gespeist werden

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Sandbox mit aktiviertem [!DNL RT-CDP] B2B edition bereitgestellt. Für B2B-Daten-Management, Zielgruppenerstellung und Zielaktivierung konfigurierte Rollen. ABAC-Richtlinien gelten, wenn Kontodaten eingeschränkte Felder enthalten. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | B2B-XDM-Schemata, die mit den Klassen XDM Business Account, XDM Business Opportunity, XDM Business Campaign und XDM Individual Profile konfiguriert wurden. B2B-Feldergruppen werden auf Kontoattribute, Personen-Konto-Beziehungen und Opportunity-Daten angewendet. Für jede B2B-Entität wurden Datensätze erstellt und für Profile aktiviert. Schemabeziehungen definiert zwischen Konto-, Personen-, Opportunity- und Kampagnenentitäten. | [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home), [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b) |
| Datenquellen und Sammlung | Erforderlich | Für CRM ([!DNL Salesforce], [!DNL Microsoft Dynamics]) und Marketing-Automatisierung ([!DNL Marketo Engage]) konfigurierte Source-Connectoren zur Aufnahme von Konto-, Personen-, Opportunity- und Kampagnendaten. Batch- oder Streaming-Aufnahme-Pipelines sind aktiv. Zuordnungen der Datenvorbereitung, die zum Transformieren von Quelldaten in B2B-XDM-Schemata konfiguriert sind. | [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home), [Marketo Engage-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identitäts- und Profilkonfiguration | Erforderlich | B2B-Identitäts-Namespaces, die für Kontokennungen (Konto-ID, CRM-Konto-ID) und Personenkennungen (E-Mail, CRM-Kontakt-ID, Marketo-Lead-ID) konfiguriert sind. Durch B2B-Identitätsauflösung aufgelöste Personen-Konto-Beziehungen. Für die Kontoprofilvereinheitlichung konfigurierte Zusammenführungsrichtlinien. | [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home), [B2B edition of Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Zielgruppendefinitionen auf Kontoebene, die mit Kontoattributen, Personenattributen und Aktivitätsdaten erstellt wurden. Für Konto-Zielgruppen konfigurierte Auswertungszeitpläne. Für den Ausschluss nicht auswählbarer Konten definierte Unterdrückungszielgruppen. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home), [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Aggregierte Interaktionswerte, Lebenszeitwert und Aktivitätsmetriken auf Kontoebene verbessern die Genauigkeit der Zielgruppe. Berechnete Attribute können Ereignisse auf Benutzerebene (E-Mail-Öffnungen, Web-Besuche, Inhalts-Downloads) zur Verwendung in der Segmentierung auf Kontoebene aggregieren. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | B2B-Richtlinien zur Datenaufbewahrung stellen sicher, dass veraltete Konto- und Opportunity-Daten bereinigt werden. Die Einverständnisverwaltung für B2B-Kontakte gewährleistet die Einhaltung von E-Mail-Marketing-Vorschriften. Richtlinien zur Datensatzgültigkeit verhindern die Akkumulation veralteter CRM-Synchronisierungsdaten. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Eingeschlossen | B2B-Kontodaten enthalten oft vertragliche Einschränkungen (Umsatzzahlen, Mitarbeiterzahlen von Drittanbietern). Datennutzungskennzeichnungen verhindern, dass eingeschränkte Kontoattribute für nicht autorisierte Ziele aktiviert werden. Governance-Richtlinien stellen sicher, dass PII-Felder aus Kontaktdatensätzen während der Aktivierung ordnungsgemäß verarbeitet werden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Durch die Überwachung der Datenflüsse von CRM und [!DNL Marketo Engage]-Quell-Connector wird sichergestellt, dass Kontodaten auf dem neuesten Stand bleiben. Die Zielaktivierungsüberwachung bestätigt, dass Zielgruppen erfolgreich an [!DNL LinkedIn]-, [!DNL Marketo]- und CRM-Ziele bereitgestellt werden. Warnhinweisregeln fangen Aufnahmefehler auf, die zu veralteten Kontodaten führen würden. | [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview), [Überwachen von Zieldatenflüssen](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations) |
| Reporting und Analyse | Empfohlen | [!DNL CJA] B2B edition bietet Analysen auf Kontoebene, einschließlich Audience-Reichweite, Interaktion und Pipeline-Einfluss. Die Account-basierte Attribution hilft bei der Messung der Auswirkungen von Aktivierungskampagnen auf den Verlauf von Opportunitys und den Umsatz. | [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kontoprofil-Vereinheitlichung | Phase 1: Anreicherung des Kontoprofils | Konsolidieren von Kontodaten aus CRM-, Marketing-Automatisierungs- und Drittanbieterquellen in einheitlichen Kontoprofilen mithilfe von B2B-XDM-Schemaklassen |
| B2B-Identitätsauflösung | Phase 1: Anreicherung des Kontoprofils | Lösen Sie Personen-zu-Konto-Beziehungen mithilfe primärer Kennungen, der Zuordnung von Kontakten und Leads zu den zugehörigen Konten auf |
| Evaluierung der Konto-Zielgruppe | Phase 2: Evaluierung der Kontenzielgruppe | Bewerten Sie die Segmentzugehörigkeit auf Kontoebene, indem Sie Kontoattribute, Personenattribute und Personenaktivitätsdaten kombinieren. |
| Kontozielkonfiguration | Phase 3: Zielkonfiguration | Konfigurieren von Verbindungen zu B2B-spezifischen Zielen ([!DNL Marketo Engage], [!DNL LinkedIn], CRM, Cloud-Speicher) mit Feld-Mapping auf Kontoebene |
| Account Audience Activation | Phase 4: Audience Activation | Kontobasierte Zielgruppen für konfigurierte Ziele zum Targeting, zur Unterdrückung oder zur CRM-Synchronisierung veröffentlichen |
| [!DNL Marketo Engage] Integration | Phase 3: Zielkonfiguration | Konfigurieren des bidirektionalen Datenflusses mit [!DNL Marketo Engage] mithilfe von nativen B2B-Quell- und Ziel-Connectoren |
| B2B-Data Governance | Phase 5: Governance und Überwachung | Durchsetzen von Datennutzungsrichtlinien und Einverständnis für die Aktivierung von B2B-Kontodaten, um die unbefugte Offenlegung von Daten zu verhindern |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — Standardfunktionen

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 2: Evaluierung der Kontenzielgruppe | Zugrunde liegende Auswertungs-Engine für Konto-Zielgruppen, die die Batch-Auswertung von Segmentdefinitionen auf Kontoebene unterstützt |
| Zielkonfiguration | Phase 3: Zielkonfiguration | Kernzielverbindungs-Infrastruktur, die von der B2B-spezifischen Zielkonfiguration verwendet wird |
| Zielgruppen-Aktivierung | Phase 4: Audience Activation | Zentrale Infrastruktur für den Datenfluss zur Aktivierung von Kontozielgruppen |
| Durchsetzung von Einverständnis und Governance | Phase 5: Governance und Überwachung | Erzwingen von Einverständnisvoreinstellungen und Datennutzungsrichtlinien zum Zeitpunkt der Aktivierung |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [ ] [!DNL RT-CDP] B2B edition-Lizenz für das Unternehmen bereitgestellt und aktiviert
- [ ] CRM-System ([!DNL Salesforce] oder [!DNL Microsoft Dynamics]), auf das über API-Anmeldeinformationen für die Konfiguration des Quell-Connectors zugegriffen werden kann
- [ ] mit API-Zugriff bereitgestellte [!DNL Marketo Engage]-Instanz (Munchkin-ID, Client-ID, Client-Geheimnis) bei Verwendung von [!DNL Marketo] als Ziel
- [ ] [!DNL LinkedIn] Campaign Manager-Konto mit Funktion für übereinstimmende Zielgruppen bei Verwendung von [!DNL LinkedIn] als Ziel
- [ ] von B2B-XDM-Schemata, die mit Konto-, Personen-, Opportunity- und Kampagnenklassen erstellt wurden (F2)
- [ ] Source-Connectoren konfiguriert und erfassen aktiv CRM- und Marketing-Automatisierungsdaten (F3)
- [ ] Identitätsbeziehungen zwischen Personen und Konten aufgelöst und Kontoprofile vereinheitlicht (F4)
- [ Für Zielgruppendefinitionen vereinbarte ]-Konventionen und -Taxonomie
- [ ] Data-Governance-Richtlinien, die für Klassifizierungen der Datensensibilität auf Kontoebene definiert wurden

## Implementierungsoptionen

Die folgenden Optionen beschreiben verschiedene Ansätze zur Implementierung dieses Anwendungsfallmusters. Überprüfen Sie jede Option und wählen Sie die aus, die Ihren Anforderungen am besten entspricht.

### Option A: Streaming-Zielgruppenaktivierung an [!DNL Marketo Engage]

**Am besten geeignet für:** Unternehmen, die [!DNL Marketo Engage] als ihre primäre B2B-Marketing-Automatisierungsplattform verwenden und nahezu in Echtzeit Aktualisierungen der Zielgruppenzugehörigkeit für Trigger-Nurture-Programme, die Aktualisierung der Lead-Bewertungen oder die Änderung der Kampagnenzugehörigkeit benötigen, da Konten qualifiziert oder disqualifiziert sind.

**Funktionsweise:**

Diese Option verwendet den Connector für native [!DNL Marketo Engage]-Ziele, [!DNL RT-CDP] Änderungen an der Konto-Zielgruppen-Zugehörigkeit direkt in [!DNL Marketo Engage] zu streamen. Wenn sich ein Konto für ein Zielgruppensegment qualifiziert oder daraus austritt, werden die zugehörigen Leads und Kontakte in [!DNL Marketo] mit Segmentzugehörigkeitsattributen aktualisiert. [!DNL Marketo] Smart-Kampagnen können dann auf der Grundlage dieser Mitgliedschaftsänderungen einen Trigger durchführen.

Das [!DNL Marketo Engage]-Ziel ist ein Streaming-Ziel, d. h. Änderungen der Zielgruppenzugehörigkeit werden inkrementell gesendet, wenn sie auftreten, und nicht in geplanten Batches. Dies ermöglicht eine schnellere Time-to-Action für Kampagnen, die auf Änderungen der Kontoqualifizierung reagieren müssen. Feldzuordnungen verbinden [!DNL RT-CDP] Profilattribute mit [!DNL Marketo] Lead-/Kontaktfeldern, sodass [!DNL Marketo] Datensätze mit Daten auf Kontoebene aus [!DNL RT-CDP] angereichert werden können.

**Wichtige Aspekte:**

- Aktives [!DNL Marketo Engage] mit API-Zugriff erforderlich
- Die Streaming-Aktivierung sendet inkrementelle Aktualisierungen, keine vollständigen Zielgruppen-Momentaufnahmen
- Datensätze auf Benutzerebene in [!DNL Marketo] werden aktualisiert, nicht direkt Datensätze auf Kontoebene
- [!DNL Marketo] Smart-Kampagnen müssen so konfiguriert sein, dass sie auf die Aktualisierungen des Segmentzugehörigkeitsfelds reagieren

**Vorteile:**

- Aktualisierungen der Zielgruppenzugehörigkeit in [!DNL Marketo] nahezu in Echtzeit
- Nativer bidirektionaler Connector vereinfacht die Integration
- Inkrementelle Aktualisierungen minimieren das Datenübertragungsvolumen
- [!DNL Marketo] können Trigger-Nurture-Programme sofort auf der Grundlage von Zielgruppenänderungen erstellen

**Einschränkungen:**

- Auf [!DNL Marketo Engage] als Aktivierungsziel beschränkt
- Für die zugrunde liegenden Zielgruppendefinitionen gelten Einschränkungen für die Berechtigung zur Streaming-Auswertung
- Erfordert die Zuordnung zwischen [!DNL RT-CDP]-Konto-Zielgruppen und [!DNL Marketo] Lead-/Kontakt-Datensätzen
- Möglicherweise sind komplexe [!DNL Marketo] Programmlogiken erforderlich, um Aktualisierungen auf Personenebene in Aktionen auf Kontoebene zu übersetzen

**Experience League:**

- [Marketo Engage-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Aktivieren von Zielgruppen für das Marketo Engage-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### Option B: Batch-Zielgruppenaktivierung auf Werbeplattformen

**Am besten geeignet für:** Account-basierte Werbekampagnen auf [!DNL LinkedIn], Display-Netzwerken oder anderen Werbeplattformen, bei denen eine tägliche Aktualisierung der Zielgruppe ausreicht und das primäre Ziel die Erreichbarkeit und Bekanntheit auf Konto-Ebene und nicht die Reaktion in Echtzeit ist.

**Funktionsweise:**

Mit dieser Option werden Konto-Zielgruppen für Werbeplattformziele ([!DNL LinkedIn] übereinstimmende Zielgruppen, [!DNL Google] Kundenabgleich, [!DNL Facebook] benutzerdefinierte Zielgruppen oder [!DNL The Trade Desk]) in einer geplanten Batch-Kadenz aktiviert. Der Aktivierungsdatenfluss exportiert Mitglieder der Konto-Zielgruppe mit zugeordneten Identitätsfeldern (in der Regel gehashte E-Mail-Adressen der zugehörigen Kontakte), die die Werbeplattform verwendet, um sie mit ihrer Benutzerbasis abzugleichen.

[!DNL LinkedIn] akzeptiert das Ziel [!DNL LinkedIn] übereinstimmende Zielgruppen neben der E-Mail-basierten Zuordnung auch den Firmennamen und die Domain-basierte Zuordnung, was ein echtes Targeting auf Kontoebene ermöglicht. Andere Werbeplattformen erfordern in der Regel Identifikatoren auf Personenebene (E-Mail, Telefon) von den Kontakten, die mit qualifizierten Konten verknüpft sind.

Die Batch-Aktivierung erfolgt nach einem konfigurierbaren Zeitplan (täglich, alle 6 Stunden usw.) und exportiert je nach Zieltyp entweder vollständige Zielgruppen-Momentaufnahmen oder inkrementelle Änderungen. Dieser Ansatz eignet sich gut für nachhaltige Sensibilisierungskampagnen, bei denen die Anforderungen an die Zielgruppenfrische in Stunden anstatt in Minuten gemessen werden.

**Wichtige Aspekte:**

- Die Zielgruppenaktualität hängt vom Batch-Zeitplan ab (normalerweise täglich)
- Advertising-Plattformen weisen ihre eigenen Einschränkungen hinsichtlich der Übereinstimmungsrate auf
- [!DNL LinkedIn] unterstützt den Abgleich auf Kontoebene. Für andere Plattformen sind Kennungen auf Personenebene erforderlich
- Dateiformate und Identitätsanforderungen für den Export variieren je nach Ziel

**Vorteile:**

- Unterstützt mehrere Werbeplattformen gleichzeitig
- Die Batch-Verarbeitung verarbeitet große Zielgruppenmengen effizient
- Zielgruppen zur Kontounterdrückung reduzieren Verschwendung von Werbeausgaben
- [!DNL LinkedIn] Matched Audiences ermöglichen das native Targeting auf Kontoebene

**Einschränkungen:**

- Zielgruppenaktualisierungen erfolgen nicht in Echtzeit; die Latenz hängt vom Batch-Zeitplan ab
- Die Übereinstimmungsraten variieren je nach Plattform und verfügbaren Identitätsfeldern
- Einige Plattformen unterstützen keinen echten Abgleich auf Kontoebene, sondern nur auf Personenebene
- Erfordert eine separate Zielkonfiguration für jede Werbeplattform

**Experience League:**

- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)
- [Ziel von Google Customer Match](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)

### Option C: Dateibasierte Aktivierung für den Cloud-Speicher

**Optimiert für:** Organisationen, die maximale Flexibilität bei der Nutzung von Account-Zielgruppen nachgelagert benötigen, einschließlich CRM-Importen, Data Warehouse-Anreicherung, Partnerdatenfreigabe oder benutzerdefinierten Integrationen, bei denen eine dateibasierte Übergabe bevorzugt wird.

**Funktionsweise:**

Diese Option exportiert Konto-Zielgruppen als CSV-, JSON- oder Parquet-Dateien zu einem geplanten Zeitpunkt in Cloud-Speicher-Ziele ([!DNL Amazon S3], [!DNL Azure Blob Storage], [!DNL Google Cloud Storage], SFTP). Der Export umfasst Kontoattribute, Felder auf Personenebene von zugehörigen Kontakten und Metadaten zur Zielgruppenzugehörigkeit. Nachgelagerte Systeme nutzen diese Dateien durch ihre eigenen Importprozesse.

Die dateibasierte Aktivierung bietet die größte Kontrolle über das Exportformat, die Feldauswahl und die Planung. Es unterstützt sowohl den vollständigen Export (vollständige Zielgruppen-Momentaufnahme jeder Ausführung) als auch den inkrementellen Export (nur Änderungen seit der letzten Ausführung). Dieser Ansatz wird häufig verwendet, wenn das Zielsystem keinen nativen [!DNL RT-CDP]-Ziel-Connector hat oder wenn das Unternehmen die Daten vorverarbeiten oder transformieren muss, bevor sie in das Zielsystem geladen werden.

**Wichtige Aspekte:**

- Erfordert eine Cloud-Speicherinfrastruktur ([!DNL S3], [!DNL Azure Blob], [!DNL GCS] oder SFTP)
- Nachgelagerte Importprozesse müssen aufgebaut und gepflegt werden
- Dateiformat (CSV, JSON, Parquet) muss den nachgelagerten Systemanforderungen entsprechen
- Die Exportplanung muss an nachgelagerte Verarbeitungsfenster angepasst werden

**Vorteile:**

- Maximale Flexibilität bei der Nutzung von Zielgruppendaten
- Unterstützt alle nachgelagerten Systeme, die Dateien lesen können
- Vollständige Kontrolle über Exportformat, Felder und Planung
- Kann mehrere nachgelagerte Verbraucher von einem einzigen Export aus bedienen
- Unterstützt vollständige und inkrementelle Exportmodi

**Einschränkungen:**

- Höchste Latenz aller Optionen (nur Batch)
- Erfordert das Erstellen und Verwalten nachgelagerter Import-Workflows
- Keine native Integration - zusätzlicher Entwicklungsaufwand erforderlich
- Die Dateiverwaltung (Bereinigung, Archivierung) muss separat erfolgen

**Experience League:**

- [Amazon S3-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Azure Blob Storage-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [Aktivieren von Zielgruppen für Batch-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### Option D: Streaming der Aktivierung an CRM-Systeme

**Am besten geeignet für:** Anwendungsfälle für die Ausrichtung von Vertrieb und Marketing, bei denen Änderungen an der Kontoqualifizierung im CRM ([!DNL Salesforce] oder [!DNL Dynamics]) nahezu in Echtzeit widergespiegelt werden müssen, um die Sichtbarkeit des Vertriebsteams, Gebietszuweisungsaktualisierungen oder automatisierte Verkaufs-Workflows zu gewährleisten.

**Funktionsweise:**

Diese Option verwendet Streaming-Ziel-Connectoren ([!DNL Salesforce] CRM, [!DNL Microsoft Dynamics]), um Änderungen an der Zugehörigkeit zur Konto-Zielgruppe direkt an CRM-Konto- oder Kontaktdatensätze zu übertragen. Wenn sich ein Konto für eine Zielgruppe qualifiziert oder diese verlässt, wird der CRM-Datensatz mit einem benutzerdefinierten Feld aktualisiert, das die Segmentzugehörigkeit angibt. Vertriebsteams können dann CRM-Berichte, -Ansichten und -Warnhinweise basierend auf diesen Feldern erstellen.

Der Streaming-Connector sendet inkrementelle Aktualisierungen, wenn Änderungen der Zielgruppenzugehörigkeit auftreten. Feldzuordnungen verbinden [!DNL RT-CDP] Konto- und Personenattribute mit CRM-Feldern und ermöglichen so die Anreicherung von CRM-Datensätzen mit einheitlichen Daten aus [!DNL RT-CDP]. Dieser Ansatz schließt den Kreis zwischen Marketing-Intelligenz (Kontoqualifizierung) und Verkaufsausführung (CRM-Workflows).

**Wichtige Aspekte:**

- Erfordert Zugriff auf die CRM-API mit entsprechenden Schreibberechtigungen
- Benutzerdefinierte CRM-Felder müssen erstellt werden, um Daten zur Zielgruppenzugehörigkeit zu erhalten
- Streaming-Volumen muss innerhalb der CRM-API-Ratenbeschränkungen liegen
- Die CRM-Workflow-Automatisierung muss für die Bearbeitung von Feldaktualisierungen konfiguriert werden

**Vorteile:**

- CRM-Updates nahezu in Echtzeit für die Sichtbarkeit des Vertriebsteams
- Aktiviert automatisierte CRM-Workflows, ausgelöst durch Zielgruppenänderungen
- CRM-Datensätze mit einheitlichen Kontodaten aus [!DNL RT-CDP] anreichert
- Unterstützt sowohl Feldaktualisierungen auf Kontoebene als auch auf Kontaktebene

**Einschränkungen:**

- CRM-API-Ratenbeschränkungen können Aktualisierungen mit hohem Volumen drosseln
- CRM anpassen (benutzerdefinierte Felder, Workflows)
- Auf [!DNL Salesforce] und [!DNL Microsoft Dynamics] als native Connectoren beschränkt
- Für die Streaming-Auswertung gelten Einschränkungen für die zugrunde liegenden Zielgruppen

**Experience League:**

- [Salesforce CRM-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### Vergleich von Optionen

In der folgenden Tabelle werden die wichtigsten Merkmale der einzelnen Implementierungsoptionen verglichen.

| Kriterien | Option A: [!DNL Marketo] Streaming | Option B: Advertising-Batch | Option C: Cloud-Speicher | Option D: CRM-Streaming |
| --- | --- | --- | --- | --- |
| Am besten geeignet für | Aktivierung des Nurture-Programms | Account-based Advertising | Flexible nachgelagerte Integration | Ausrichtung von Vertrieb und Marketing |
| Komplexität | Niedrig | Mittel | Medium-Hoch | Mittel |
| Latenz | Fast in Echtzeit (Minuten) | Batch (Stunden) | Batch (Stunden) | Fast in Echtzeit (Minuten) |
| Flexibilität | Niedrig (nur [!DNL Marketo]) | Medium (Werbeplattformen) | Hoch (beliebiges nachgelagertes System) | Niedrig (nur CRM) |
| Erfordert | [!DNL Marketo Engage] | Advertising Platform-Konten | Cloud-Speicherinfrastruktur | CRM-API-Zugriff |
| Targeting auf Kontoebene | Über Personendatensätze | Nur [!DNL LinkedIn] (auf der Ebene „Sonstige„) | Konfigurierbar | Über Konto-/Kontaktaufzeichnungen |
| Wartungsaufwand | Niedrig | Low-Medium | Hoch | Mittel |

### Wählen der richtigen Option

Verwenden Sie die folgenden Entscheidungshilfen, um den richtigen Aktivierungsansatz auszuwählen:

1. **Wenn Ihr Hauptziel die B2B-Lead-Pflege ist und Sie[!DNL Marketo Engage]** verwenden, wählen Sie Option A. Der native Streaming-Connector bietet die schnellste Time-to-Action für Marketing-Automatisierungs-Workflows.

2. **Wenn Ihr Hauptziel die Account-basierte Sensibilisierung und Nachfragegenerierung durch Werbung ist** wählen Sie Option B. [!DNL LinkedIn] Übereinstimmende Zielgruppen bieten die stärkste Zielgruppenbestimmung auf Kontoebene. Verwenden Sie andere Werbeplattformen für eine breitere Reichweite.

3. **Wenn Sie Konto-Zielgruppen an Systeme ohne native [!DNL RT-CDP]-Connectoren weiterleiten** oder maximale Kontrolle über das Datenformat und die nachgelagerte Verarbeitung benötigen, wählen Sie Option C. Dies ist auch die beste Wahl für Partner-Datenfreigabe oder Data Warehouse-Anreicherung.

4. **Wenn Ihr Hauptziel die Vertriebsunterstützung und CRM-Sichtbarkeit von Marketing-qualifizierten Konten ist** wählen Sie Option D. Dadurch wird die Übergabeschleife zwischen Marketing und Vertrieb geschlossen, indem CRM-Datensätze nahezu in Echtzeit aktualisiert werden.

Die meisten B2B-Unternehmen werden mehrere Optionen gleichzeitig implementieren, z. B. Option A für Nurture-Programme, Option B für [!DNL LinkedIn]-Werbung und Option D für CRM-Synchronisierung. Diese Optionen schließen sich nicht gegenseitig aus. Dieselbe Konto-Zielgruppe kann für mehrere Ziele gleichzeitig aktiviert werden.

## Implementierungsphasen

Die folgenden Phasen beschreiben den schrittweisen Prozess zur Implementierung dieses Anwendungsfallmusters.

### Phase 1: Anreicherung des Kontoprofils

In dieser Phase werden einheitliche Account-Profile erstellt, indem Daten aus CRM, Marketing-Automatisierung und Quellen Dritter konsolidiert werden.

**Anwendungsfunktion:** [!DNL RT-CDP] B2B: Kontoprofilvereinheitlichung, [!DNL RT-CDP] B2B: B2B-Identitätsauflösung

**Was Sie konfigurieren werden:** In dieser Phase werden einheitliche Account-Profile erstellt, indem Daten aus CRM, Marketing-Automatisierung und Quellen von Drittanbietern konsolidiert werden. Die B2B-Identitätsauflösung ordnet Beziehungen zwischen Personen und Konten zu, sodass Interaktionsdaten auf Personenebene (E-Mail-Öffnungen, Web-Besuche, Inhalts-Downloads) aggregiert und in der Zielgruppenbewertung auf Kontoebene verwendet werden können. Diese Phase baut auf den Grundfunktionen F2, F3 und F4 auf, die bereits vorhanden sein müssen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Strategie zur Kontokennung**
>
>Welche Kennung dient systemübergreifend als primärer Kontoschlüssel?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| CRM Konto-ID (z. B. [!DNL Salesforce] Konto-ID) | CRM ist das Aufzeichnungssystem für Konten | Häufigster Ansatz. Stellt die Abstimmung zwischen [!DNL RT-CDP] und CRM sicher. Alle Quellsysteme müssen auf dieselbe CRM-Konto-ID verweisen. |
>| Benutzerdefinierte Konto-ID | Mehrere CRM-Instanzen oder ein proprietärer Kundenstamm | Erfordert eine Zuordnungsebene zwischen Quellsystem-IDs und der kanonischen Konto-ID. Flexibler, aber komplexer. |
>| DUNS-Nummer oder -Domain | Die Anreicherung von Drittanbieterdaten ist die primäre Kontoquelle | Nützlich, wenn Anbieter firmografischer Daten die primäre Quelle sind. Erfordert möglicherweise Fuzzy Matching für die Domain-basierte Auflösung. |

>[!NOTE]
>**Entscheidung: Modell für eine Beziehung zwischen Person und Konto**
>
>Wie werden Personen (Leads, Kontakte) mit Konten verknüpft?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Eins-zu-eins (jede Person gehört zu einem Konto) | Einfaches B2B-Modell mit sauberen CRM-Daten | Einfache Auflösung. Am häufigsten für B2B im mittleren Marktsegment. |
>| Viele-zu-viele (Personen können mehreren Konten angehören) | Komplexe Unternehmensbeziehungen, Berater oder Partnernetzwerke | [!DNL RT-CDP] B2B edition unterstützt dies nativ. Erhöht die Komplexität der Zielgruppe, spiegelt jedoch die Beziehungen in der realen Welt genau wider. |

**Benutzeroberflächennavigation:** Platform > Profile > Durchsuchen (zum Überprüfen von einheitlichen Kontoprofilen)

**Wichtige Konfigurationsdetails:**

- Überprüfen, ob B2B-XDM-Schemas (XDM Business Account, XDM Business Person Account) in F2 vorhanden sind
- Bestätigen, dass CRM- und [!DNL Marketo]-Quell-Connectoren aktiv Konto- und Personendaten aus F3 aufnehmen
- Überprüfen, ob die Personen-Konto-Beziehungen im Identitätsdiagramm von F4 aufgelöst werden
- Prüfen der Vollständigkeit des Kontoprofils durch Durchsuchen von Beispielkontoprofilen

**Dokumentation zu Experience League:**

- [Übersicht über Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/crm/salesforce)

### Phase 2: Evaluierung der Kontenzielgruppe

In dieser Phase werden Zielgruppen auf Kontoebene definiert und ausgewertet, indem eine Kombination aus Kontoattributen, Personenattributen und Daten zur Personenaktivität verwendet wird.

**Anwendungsfunktion:** [!DNL RT-CDP] B2B: Konto-Zielgruppenbewertung, [!DNL RT-CDP]: Zielgruppenbewertung

**Was Sie konfigurieren werden:** In dieser Phase werden Zielgruppen auf Kontoebene mithilfe einer Kombination aus Kontoattributen, Personenattributen und Personenaktivitätsdaten definiert und ausgewertet. Mit Account-Zielgruppen in [!DNL RT-CDP] B2B edition können Sie Accounts sowohl auf der Grundlage firmografischer Merkmale (Branche, Umsatz, Mitarbeiteranzahl) als auch des Interaktionsverhaltens der mit diesen Accounts verknüpften Personen segmentieren.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Methode zur Zielgruppenauswertung**
>
>Wie schnell muss die Kontozielgruppenzugehörigkeit aktualisiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Batch-Auswertung (täglich) | Täglich aktualisierte Kampagnen-Audiences, dateibasierte Aktivierungen, Werbeplattform-Audiences | Die meisten Konto-Zielgruppen verwenden die Batch-Auswertung. Verarbeitet komplexe Abfragen mehrerer Entitäten, die Konto- und Personenattribute kombinieren. Ausreichend für die meisten B2B-Anwendungsfälle, in denen eine tägliche Aktualisierung akzeptabel ist. |
>| Streaming-Auswertung | [!DNL Marketo]- oder CRM-Aktivierung, wenn eine Qualifizierung nahezu in Echtzeit erforderlich ist | Konto-Zielgruppen sind für Streaming nur eingeschränkt geeignet. Für die Streaming-Auswertung kommen nur einfache Kontoattributbedingungen in Frage. Verhaltensbedingungen auf Personenebene erfordern in der Regel einen Batch. |

>[!NOTE]
>**Entscheidung: Ansatz zur Definition der Konto-Zielgruppe**
>
>Wie werden die Kriterien für die Konto-Zielgruppe definiert?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Kontoattribute | Einfaches firmographisches Targeting (Branche, Umsatz, Region) | Schnellste Implementierung. Auf Daten auf Kontoebene beschränkt. Für breit angelegtes Targeting verwenden. |
>| Konto- + Personenattribute | Zielgruppenbestimmungskonten, bei denen zugeordnete Personen bestimmten Kriterien entsprechen (Stellenbezeichnung, Abteilung) | Präzisere Zielgruppenerfassung. Kombiniert firmografische und demografische Daten. |
>| Konto + Personenattribute + Personenaktivität | Targeting von Konten mit interaktiven Kontakten (E-Mail-Öffnungen, Web-Besuche, Download von Inhalten) | Leistungsstark, aber am komplexesten. Erfordert verhaltensbezogene Ereignisdaten von F3. Erfordert in der Regel eine Batch-Auswertung. |
>| Audience-Komposition | Komplexe Zielgruppenlogik, die Rang-, Aufspaltungs-, Ausschluss- oder Anreicherungsvorgänge erfordert | Verwenden Sie die Arbeitsfläche für die visuelle Zielgruppenkomposition für abgeleitete Konto-Zielgruppen. Auf Batch-Auswertung beschränkt. |

>[!NOTE]
>**Entscheidung: Unterdrückungsstrategie für Zielgruppen**
>
>Welche Konten sollten von der Aktivierung ausgeschlossen werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Unterdrückung vorhandener Kunden | Akquise-Kampagnen für neue Konten | Ausschließen von Konten mit aktiven Abonnements oder abgeschlossenen Opportunities |
>| Aktive Verkaufszyklusunterdrückung | Vermeiden Sie es, Konten im aktiven Vertriebsgeschäft zu beeinträchtigen | Konten mit offenen Opportunities oberhalb eines bestimmten Stadiums ausschließen |
>| Kürzliche Interaktionsunterdrückung | Verhindern von Übermittlungen an kürzlich kontaktierte Konten | Ausschließen von Konten innerhalb eines Lookback-Fensters (z. B. 30 Tage) |
>| Keine Unterdrückung | Markenerkennungskampagnen, die auf alle qualifizierten Accounts abzielen | Mit Vorsicht verwenden; kann zu verschwendeten Ausgaben für nicht auswählbare Konten führen |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen (wählen Sie Konto als Zielgruppentyp aus)

**Wichtige Konfigurationsdetails:**

- Wählen Sie beim Erstellen einer neuen Zielgruppe in Segment Builder als Zielgruppentyp „Konto“ aus
- Kontoattribute werden im Abschnitt Konto in Segment Builder angezeigt (Branche, Umsatz, Kontostatus)
- Personenattribute und -aktivitäten können über die Beziehung „Personen“ in Account Audience Builder hinzugefügt werden
- Konfigurieren Sie den Batch-Auswertungszeitplan, falls noch kein solcher Zeitplan für die Sandbox existiert
- Erstellen von Zielgruppen für die Zielgruppenbestimmung (einzuschließende Konten) und Unterdrückungszielgruppen (auszuschließende Konten)

**Dokumentation zu Experience League:**

- [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience-Komposition](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)

### Phase 3: Zielkonfiguration

In dieser Phase werden authentifizierte Verbindungen zu den Ziel-Zielen hergestellt, an denen Konto-Zielgruppen bereitgestellt werden.

**Anwendungsfunktion:** [!DNL RT-CDP] B2B: Kontozielkonfiguration, [!DNL RT-CDP] B2B: [!DNL Marketo Engage]-Integration, [!DNL RT-CDP]: Zielkonfiguration

**Was Sie konfigurieren werden:** In dieser Phase werden authentifizierte Verbindungen zu den Zielgruppen hergestellt, an die Kontozielgruppen gesendet werden. Die Konfiguration umfasst das Auswählen des Ziels aus dem Katalog, das Bereitstellen von Authentifizierungsberechtigungen, das Konfigurieren von Feldzuordnungen auf Konto- und Personenebene und das Festlegen des Exportzeitplans. Jeder Zieltyp hat eindeutige Anforderungen und Funktionen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Zielauswahl**
>
>Welche Ziele erhalten die Zielgruppen des aktivierten Kontos?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | B2B-Lead-Pflege, -Bewertung und -Kampagnenausführung | Nativer Streaming-Connector. Aktualisiert Lead-/Kontaktaufzeichnungen. Erfordert [!DNL Marketo] API-Anmeldeinformationen (Munchkin-ID, Client-ID, Client-Geheimnis). |
>| Abgestimmte Zielgruppen [!DNL LinkedIn] | Account-based Advertising auf [!DNL LinkedIn] | Unterstützt den Abgleich von Firmennamen und Domain für das Targeting auf Kontoebene. Batch-Aktivierung. Zugriff auf [!DNL LinkedIn] Campaign Manager erforderlich. |
>| CRM [!DNL Salesforce] | Sales Enablement und Synchronisierung der CRM-Kontoliste | Der Streaming-Connector aktualisiert Konto- oder Kontakteinträge. Erfordert [!DNL Salesforce] API-Zugriff mit Schreibberechtigungen. |
>| [!DNL Microsoft Dynamics 365] | Vertriebsunterstützung für [!DNL Dynamics] Unternehmen | Streaming-Connector. Erfordert [!DNL Dynamics 365] API-Zugriff. |
>| Cloud-Speicher ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], SFTP) | Benutzerdefinierte Integrationen, Data Warehouse, Partner-Freigabe | Dateibasierter Batch-Export. Maximale Flexibilität, aber nachgelagerte Verarbeitung erforderlich. |
>| [!DNL Google] Kundenabgleich | Anzeigen und Suchen von Anzeigen-Targeting | Abgleich auf Personenebene über gehashte E-Mails. Batch-Aktivierung. |
>| [!DNL The Trade Desk] | Programmatische Anzeige- und Videowerbung | Abgleich auf Personenebene. Batch-Aktivierung. |

>[!NOTE]
>**Entscheidung: Feldzuordnungsstrategie**
>
>Welche Konto- und Personenfelder sollten dem Ziel zugeordnet werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Identitätsfelder | Advertising-Plattformen, die nur übereinstimmende Kennungen benötigen | Minimale Datenübertragung. Zielübereinstimmungen in E-Mail-Adresse oder Unternehmens-Domain. |
>| Identität + Core-Kontoattribute | CRM oder [!DNL Marketo], wo der Kontokontext das Targeting verbessert | beinhalten Branche, Umsatz, Mitarbeiteranzahl, Kontoebene. Anreicherung nachgelagerter Datensätze. |
>| Vollständiges Attribut festgelegt | Cloud-Speicher oder Data Warehouse-Exporte | Alle relevanten Konto- und Personenattribute einschließen. Größte Export-Payload. |

**Benutzeroberflächennavigation:** Verbindungen > Ziele > Katalog > Nach Ziel suchen > Konfigurieren

**Wichtige Konfigurationsdetails:**

- Navigieren Sie zum Zielkatalog und wählen Sie das Ziel aus
- Geben Sie für den Zieltyp spezifische Authentifizierungsdaten an
- Konfigurieren von Feldzuordnungen, die [!DNL RT-CDP] XDM-Felder mit Zielfeldern verbinden
- [!DNL Marketo Engage]: Geben Sie die Munchkin-ID, die Client-ID und das Client-Geheimnis an
- Zum [!DNL LinkedIn]: Über OAuth autorisieren und das [!DNL LinkedIn] Anzeigenkonto auswählen
- Für Cloud-Speicher: Geben Sie den Bucket-/Container-Namen, den Pfad, das Dateiformat und die Anmeldeinformationen an
- Für CRM: Instanz-URL, API-Anmeldedaten und Zielobjekttyp (Konto oder Kontakt) angeben

**Wo die Optionen unterschiedlich sind:**

**Für Option A ([!DNL Marketo Engage] Streaming):**

Navigieren Sie zu Ziele > Katalog > Adobe > [!DNL Marketo Engage]. Konfigurieren Sie die Munchkin-ID und API-Anmeldeinformationen. Ordnen Sie [!DNL RT-CDP] Identitätsfelder (E-Mail) und Profilattribute [!DNL Marketo] Lead-Feldern zu. Das -Ziel verarbeitet automatisch inkrementelle Streaming-Aktualisierungen.

**Für Option B (Advertising Platform-Batch):**

Navigieren Sie zu Ziele > Katalog > Advertising/Social > Plattform auswählen . Autorisieren Sie über OAuth. Konfigurieren Sie den Exportzeitplan (empfohlen: täglich). Ordnen Sie gehashte E-Mail-IDs und unterstützte übereinstimmende Felder zu. Ordnen Sie [!DNL LinkedIn] zusätzlich Felder für den Firmennamen und die Domain für den Abgleich auf Kontoebene zu.

**Für Option C (Cloud-Speicherdateibasiert):**

Navigieren Sie zu Ziele > Katalog > Cloud-Speicher > Wählen Sie einen Anbieter aus. Konfigurieren Sie den Bucket/Container, die Dateipfadvorlage und das Dateiformat (CSV, JSON oder Parquet). Legen Sie den Exportzeitplan fest und wählen Sie Vollständiger oder Inkrementeller Export. Ordnen Sie alle gewünschten Konto- und Personenattributfelder zu.

**Für Option D (CRM-Streaming):**

Navigieren Sie zu Ziele > Katalog > CRM und wählen Sie [!DNL Salesforce] oder [!DNL Dynamics] aus. Geben Sie API-Anmeldeinformationen und Instanz-URL an. [!DNL RT-CDP] Felder einem CRM-Konto oder Kontaktfeldern zuordnen. Stellen Sie sicher, dass im CRM benutzerdefinierte Felder vorhanden sind, um Daten zur Zielgruppenzugehörigkeit zu erhalten.

**Dokumentation zu Experience League:**

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Amazon S3-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### Phase 4: Zielgruppenaktivierung

In dieser Phase werden die ausgewerteten Konto-Zielgruppen in den konfigurierten Zielen veröffentlicht.

**Anwendungsfunktion:** [!DNL RT-CDP] B2B: Konto-Audience Activation, [!DNL RT-CDP]: Audience Activation

**Was Sie konfigurieren werden:** In dieser Phase werden die ausgewerteten Konto-Zielgruppen in den konfigurierten Zielen veröffentlicht. Activation erstellt den Datenfluss, der die Konto-Audience (Quelle) mit dem externen Ziel (Ziel) verbindet, wendet Attributzuordnungen an und initiiert den Export entsprechend dem konfigurierten Zeitplan oder Streaming-Verhalten. Sie werden auch Unterdrückungszielgruppen konfigurieren, um nicht infrage kommende Konten von der Aktivierung auszuschließen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Exporttyp**
>
>Soll die Aktivierung vollständige Zielgruppen-Momentaufnahmen exportieren oder nur inkrementelle Änderungen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Inkrementeller Export | Streaming-Ziele ([!DNL Marketo], CRM) oder Batch-Ziele, bei denen nachgelagerte Systeme Deltas verarbeiten | Geringeres Datenvolumen pro Export. Schnellere Verarbeitung. Erfordert, dass nachgelagerte Systeme den Status verwalten. Standard für Streaming-Ziele. |
>| Vollständiger Export | Batch-Ziele, bei denen das nachgelagerte System bei jeder Ausführung die vollständige Zielgruppe ersetzt | Größeres Datenvolumen, aber einfachere nachgelagerte Logik. Nützlich, wenn nachgelagerte Systeme den Status nicht aufrechterhalten. Verfügbar für dateibasierte Ziele. |

>[!NOTE]
>**Entscheidung: Aktivierungsbereich**
>
>Wie viele Zielgruppen sollten pro Ziel aktiviert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einzelne Zielgruppe pro Datenfluss | Einfache Aktivierung mit klarer Zuordnung von Zielgruppe zu Ziel | Einfachste Überwachung und Fehlerbehebung. Ein Zielgruppenfehler wirkt sich nicht auf andere aus. |
>| Mehrere Zielgruppen pro Datenfluss | Mehrere verwandte Zielgruppen gehen zum selben Ziel | Effizientere Nutzung von Zielverbindungen. Alle Zielgruppen verwenden dieselbe Feldzuordnung und denselben Zeitplan. |

**UI-Navigation:** Verbindungen > Ziele > Durchsuchen > Ziel auswählen > Zielgruppen aktivieren

**Wichtige Konfigurationsdetails:**

- Wählen Sie die Zielgruppe(n) aus der Liste Zielgruppe aus
- Überprüfen und bestätigen Sie die in Phase 3 konfigurierten Feldzuordnungen
- Für Batch-Ziele: Konfigurieren des Exportplans (Zeit, Häufigkeit)
- Für Streaming-Ziele: Die Aktivierung beginnt unmittelbar nach der Konfiguration
- Fügen Sie Unterdrückungszielgruppen optional mit der Ausschlussfunktion hinzu
- Trigger eines ersten Testaktivierungsdurchgangs zur Validierung des Datenflusses

**Wo die Optionen unterschiedlich sind:**

**Für Option A ([!DNL Marketo Engage] Streaming):**

Zu aktivierende Konto-Zielgruppen auswählen. Die Aktivierung beginnt sofort mit dem Streaming. Überprüfen Sie in [!DNL Marketo], ob Lead-/Kontaktdatensätze mit Feldern für die Segmentzugehörigkeit aktualisiert werden. Konfigurieren Sie [!DNL Marketo] Smart-Kampagnen für den Trigger auf der Grundlage dieser Feldänderungen.

**Für Option B (Advertising Platform-Batch):**

Konto-Zielgruppen auswählen und den täglichen Exportzeitplan konfigurieren. Überprüfen Sie nach Abschluss des ersten Exports in der Werbeplattform, ob die Zielgruppe angezeigt wird und eine ausgefüllte Mitgliederzahl aufweist. Die Plattform kann die ursprüngliche Zielgruppendatei innerhalb von 24-48 Stunden verarbeiten.

**Für Option C (Cloud-Speicherdateibasiert):**

Wählen Sie Konto-Zielgruppen aus und konfigurieren Sie den Exportzeitplan und das Dateiformat. Nach dem ersten Export werden die Dateien am Zielspeicherort mit dem erwarteten Format und Inhalt angezeigt. Bestätigen Sie, dass die exportierten Dateien erfolgreich von den nachgelagerten Importprozessen genutzt werden.

**Für Option D (CRM-Streaming):**

Zu aktivierende Konto-Zielgruppen auswählen. Die Aktivierung beginnt sofort mit dem Streaming. Überprüfen Sie im CRM, ob Konto- oder Kontaktdatensätze mit den zugeordneten Feldern aktualisiert werden. Konfigurieren Sie CRM-Berichte, Listenansichten oder Workflow-Automatisierung, um auf die aktualisierten Felder zu reagieren.

**Dokumentation zu Experience League:**

- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)

### Phase 5: Governance und Überwachung

In dieser Phase wird sichergestellt, dass die Aktivierung der Konto-Zielgruppe den Data-Governance-Richtlinien und den Voreinstellungen für das Einverständnis entspricht und dass die laufenden Aktivierungsdatenflüsse auf ihre Integrität überwacht werden.

**Anwendungsfunktion:** [!DNL RT-CDP] B2B: B2B-Data Governance, [!DNL RT-CDP]: Durchsetzung von Einverständnis und Governance

**Was Sie konfigurieren werden:** In dieser Phase wird sichergestellt, dass die Aktivierung der Konto-Zielgruppe den Data-Governance-Richtlinien und den Einverständnisvoreinstellungen entspricht und dass die Datenflüsse für die laufende Aktivierung auf ihre Integrität überwacht werden. B2B-Data Governance erzwingt Einschränkungen bei sensiblen Kontoattributen (Umsatz, Mitarbeiteranzahl von Drittanbietern), während die Durchsetzung der Einwilligung sicherstellt, dass bei der Kommunikation auf Personenebene die Opt-out-Voreinstellungen beachtet werden. Die Überwachung bestätigt, dass Aktivierungsdatenflüsse erfolgreich abgeschlossen werden.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Ebene der Durchsetzung der Governance**
>
>Wie streng sollte die Data Governance für B2B-Aktivierungen durchgesetzt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Vollständige Durchsetzung (bei Verstoß blockieren) | Produktions-Aktivierungen mit sensiblen Daten | Verhindert jede Aktivierung, die gegen Governance-Richtlinien verstößt. Möglicherweise sind iterative Anpassungen der Feldzuordnung erforderlich, um Verstöße zu beheben. |
>| Warnen und fortfahren | Entwicklungs- oder Testumgebungen | Ermöglicht die Aktivierung des Vorgangs, protokolliert jedoch Warnungen. Nützlich bei der Ersteinrichtung, um potenzielle Probleme zu identifizieren. |

>[!NOTE]
>**Entscheidung: Monitoring-Ansatz**
>
>Wie sollte der Aktivierungszustand überwacht werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Warnhinweisbasierte Überwachung | Produktionsumgebungen, in denen Fehler schnell erkannt werden müssen | Konfigurieren Sie Warnhinweise für Fehler bei der Zielaktivierung, Fehler im Quellfluss und Datenflussverzögerungen. Warnhinweis-Abonnement muss eingerichtet sein. |
>| Manuelle Überwachung | Entwicklung für Aktivierungen mit geringem Volumen | Überprüfen Sie die Datenflussausführungen regelmäßig in der Benutzeroberfläche „Ziele“. Weniger Aufwand, aber Risiko einer verzögerten Fehlererkennung. |
>| Beide | Produktionsumgebungen mit komplexer Aktivierung für mehrere Ziele | Warnhinweise für kritische Fehler sowie regelmäßige Dashboard-Überprüfungen der Trends. Empfohlen für die meisten B2B-Implementierungen. |

**Benutzeroberflächennavigation:** Datenschutz > Richtlinien (für Governance), Verbindungen > Ziele > Durchsuchen > Ziel auswählen > Datenflussausführungen (für die Überwachung)

**Wichtige Konfigurationsdetails:**

- Anwenden von Datennutzungskennzeichnungen auf B2B-Datensätze mit eingeschränkten Attributen
- Überprüfen Sie, ob Governance-Richtlinien durchgesetzt werden, indem Sie die Aktivierung mit der Ziel-Marketing-Aktion vergleichen.
- Konfigurieren von Warnhinweisen für Fehler bei der Zielaktivierung und beim Quell-Connector
- Überprüfen der Datenflussausführungsmetriken (exportierte Profile, fehlgeschlagene Datensätze) nach jedem Aktivierungszyklus
- Richten Sie eine Überprüfung des Lizenznutzungs-Dashboards ein, um das Kontoprofilvolumen im Vergleich zu Berechtigungen zu verfolgen.

**Dokumentation zu Experience League:**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Überwachen von Zieldatenflüssen](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)

## Überlegungen bei der Implementierung

Die folgenden Abschnitte enthalten zusätzliche Anleitungen für eine erfolgreiche Implementierung.

### Leitplanken und Beschränkungen

Überprüfen Sie die folgenden Platform-Leitplanken und -Beschränkungen, die für dieses Anwendungsfallmuster gelten.

- Maximal 4.000 Segmentdefinitionen pro Sandbox, einschließlich Konto-Zielgruppen — [Segmentierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- Konto-Zielgruppen werden hauptsächlich mithilfe einer Batch-Auswertung ausgewertet. Die Streaming-Eignung ist auf einfache Kontoattributbedingungen beschränkt
- Maximal 100 Datenflüsse pro Zielverbindung — [Leitplanken für Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)
- Batch-Ziele exportieren bis zu 5 Millionen Profile pro Dateisegment
- Für Streaming-Ziele gibt es vom Zielpartner festgelegte Durchsatzbeschränkungen pro Sekunde (z. B. [!DNL Marketo] API-Ratenbeschränkungen)
- Zusammengestellte Zielgruppen (aus der Zielgruppenkomposition) sind auf die Batch-Auswertung beschränkt und können kein Streaming verwenden
- Maximal 10 Kompositionsblöcke pro Arbeitsfläche für Zielgruppen-Komposition
- [!DNL LinkedIn] übereinstimmende Zielgruppen erfordern eine minimale Zielgruppengröße (normalerweise 300 Mitglieder) für die Aktivierung
- CRM-Streaming-Ziele unterliegen den API-Ratenbeschränkungen des CRM-Anbieters (z. B. [!DNL Salesforce] täglichen API-Massenbeschränkungen)
- [!DNL RT-CDP] B2B edition-Lizenz steuert die Gesamtzahl der Geschäftskontoprofile ([-CDP-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### Häufige Fehler

Beachten Sie die folgenden häufigen Probleme bei der Implementierung dieses Anwendungsfallmusters.

- **Unvollständige Zuordnung von Person zu Konto:** Wenn Personendatensätze (Leads, Kontakte) nicht ordnungsgemäß über die B2B-Identitätsauflösung mit Kontodatensätzen verknüpft sind, werden Account-Zielgruppen, die von Personenattributen oder -aktivitäten abhängen, die qualifizierten Konten unterzählt. Überprüfen Sie die Personen-zu-Konto-Beziehungen in F4, bevor Sie Konto-Zielgruppen erstellen.

- **Veraltete CRM-Daten, die zu Zielgruppenverschiebungen führen:** Wenn CRM-Quell-Connectoren nicht nach einem regulären Zeitplan ausgeführt werden oder im Hintergrund fehlschlagen, werden Kontoattribute (Branche, Umsatz, Status) veraltet. Dadurch schließen Audiences Konten ein, die nicht mehr qualifiziert sind, oder schließen Konten aus, die qualifiziert werden sollten. Überwachen des Zustands des Datenflusses des Quell-Connectors.

- **Erwartungen an die Übereinstimmungsrate der Advertising-Plattform:** Beim Aktivieren von Account-Zielgruppen für andere Werbeplattformen als [!DNL LinkedIn] hängt die Übereinstimmungsrate von gültigen Kennungen auf Personenebene (gehashte E-Mail) für Kontakte ab, die mit qualifizierten Konten verknüpft sind. Konten ohne verknüpfte Kontakte mit E-Mail-Adressen stimmen nicht überein. Überwachen Sie Übereinstimmungsraten und erwägen Sie, Kontaktdaten anzureichern.

- Fehlerhafte Ausrichtung der **[!DNL Marketo]-Feldzuordnung:** Beim Streaming an [!DNL Marketo Engage] muss die [!DNL RT-CDP]-Feldzuordnung vorhandene Lead- [!DNL Marketo] Kontaktfelder ansprechen. Wenn das zugeordnete [!DNL Marketo] nicht vorhanden ist, schlägt die Aktualisierung im Hintergrund fehl. Erstellen Sie alle Zielfelder in [!DNL Marketo] vorab, bevor Sie das Ziel konfigurieren.

- **Aktivierung durch Governance-Richtlinien blockieren** Datennutzungskennzeichnungen in Kontoattributfeldern (insbesondere firmografische Daten von Drittanbietern) können bei der Aktivierung für Werbeziele zu Triggern bei der Governance führen. Bewerten Sie die Governance-Compliance, bevor Sie Feldzuordnungen aktivieren, und passen Sie sie an, um bei Bedarf eingeschränkte Felder auszuschließen.

- **Konto-Zielgruppe, die Konto- und Personendaten mit einer Batch-Auswertung kombiniert:** Konto-Zielgruppen, die auf Verhaltensereignisse auf Personenebene verweisen (z. B. „Konten, in denen mindestens ein Kontakt in den letzten 30 Tagen eine E-Mail geöffnet hat„), erfordern eine Batch-Auswertung. Wenn im Anwendungsfall eine Echtzeit-Qualifizierung erwartet wird, kann diese Einschränkung zu unerwarteten Latenzen führen.

### Best Practices

Befolgen Sie diese Empfehlungen, um optimale Ergebnisse zu erzielen.

- Beginnen Sie mit einer kleinen Anzahl klar definierter Account-Zielgruppen (ICP-Ebene, Branche, vertikale Interaktionsstufe), bevor Sie sie auf komplexe Multi-Attribute-Definitionen erweitern
- Erstellen Sie dedizierte Unterdrückungszielgruppen für Bestandskunden, aktive Opportunitys und kürzlich interaktive Konten, um verschwendete Ausgaben und Kanalkonflikte zu vermeiden
- Verwenden Sie die Zielgruppenkomposition, um abgestufte Konto-Zielgruppen (hohe/mittlere/niedrige Interaktion) zu erstellen, indem Sie Konten nach aggregierten Interaktionsbewertungen ordnen
- Gleichzeitige Aktivierung derselben Konto-Audience für mehrere Ziele für koordinierte Multi-Channel-Kampagnen (z. B. [!DNL LinkedIn] für Werbung, [!DNL Marketo] für E-Mails, CRM für die Sichtbarkeit von Verkäufen)
- Implementieren Sie eine konsistente Namenskonvention für Konto-Zielgruppen, die die Zielgruppenkriterien und den vorgesehenen Kanal enthält (z. B. „B2B_ICP_Enterprise_Tech_LinkedIn“ oder „B2B_Suppression_ActiveOpps„)
- Planen Sie die Batch-Aktivierung außerhalb der Spitzenzeiten, um die Auswirkungen auf nachgelagerte Systeme zu minimieren und mit den Verarbeitungsfenstern der Werbeplattform abzugleichen
- Überwachen Sie die Übereinstimmungsraten pro Ziel nach der ersten Aktivierung und iterieren Sie bei Identitätsfeldzuordnungen, um den Abgleich zu verbessern
- Beibehaltung des bidirektionalen Datenflusses mit [!DNL Marketo Engage]: Aufnahme von Interaktionsdaten aus [!DNL Marketo] in [!DNL RT-CDP] (Quell-Connector) und Aktivierung von Zielgruppen zurück in [!DNL Marketo] (Ziel-Connector) für ein Closed-Loop-System

### Entscheidungen über Kompromisse

Beachten Sie bei Implementierungsentscheidungen die folgenden Kompromisse.

>[!NOTE]
>**Kompromiss: Zielgruppenfrische vs. Auswertungskomplexität**
>
>Account-Zielgruppen, die Account-Attribute mit Verhaltensdaten auf Personenebene kombinieren, bieten die präziseste Zielgruppenbestimmung, sind jedoch auf die Batch-Auswertung (tägliche Aktualisierung) beschränkt. Einfachere Zielgruppen, die nur auf Kontoattributen basieren, können sich für die Streaming-Bewertung mit nahezu in Echtzeit durchgeführten Aktualisierungen qualifizieren.
>
>- **Batch (komplexe Kriterien) favorisiert:** Targeting-Präzision, Kombination von firmografischen und verhaltensbezogenen Signalen, umfassende Kontobewertung
>- **Streaming (einfache Kriterien) bevorzugt:** Geschwindigkeit der Zielgruppen-Updates, Echtzeit-Reaktion auf Kontoänderungen, schnellere Time-to-Action in [!DNL Marketo] und CRM
>- **Empfehlung:** Verwenden Sie die Batch-Auswertung für die primäre Zielgruppe, bei der eine tägliche Aktualisierung akzeptabel ist (die meisten B2B-Anwendungsfälle). Reservieren Sie die Streaming-Auswertung für zeitkritische Trigger wie Kontostatusänderungen oder hochwertige Kontowarnungen.

>[!NOTE]
>**Kompromiss: Zentralisierte Aktivierung vs. zielspezifische Zielgruppen**
>
>Sie können ein einzelnes einheitliches Konto für mehrere Ziele aktivieren oder zielspezifische Zielgruppen erstellen, die auf die Funktionen und Anforderungen jedes Kanals zugeschnitten sind.
>
>- **Zentralisierte Zielgruppen-Gunst:** Konsistenz über verschiedene Kanäle hinweg, einfacheres Zielgruppen-Management, einheitliches Reporting
>- **Zielspezifische Zielgruppen bevorzugen:** optimierte Zielgruppenbestimmung pro Kanal (z. B. [!DNL LinkedIn] profitiert von Attributen auf Unternehmensebene, während [!DNL Marketo] Details auf Lead-Ebene benötigt), kanalspezifische Unterdrückungsregeln
>- **Empfehlung:** Sie mit zentralisierten Zielgruppen, um Konsistenz zu gewährleisten, und erstellen Sie dann nur dann zielspezifische Varianten, wenn die Kanalanforderungen erheblich voneinander abweichen (z. B. unterschiedliche Unterdrückungsfenster für Werbung vs. E-Mail).

>[!NOTE]
>**Kompromiss: Echtzeit-CRM-Synchronisation vs. Batch-CRM-Aktualisierungen**
>
>Das Streaming an CRM bietet sofortige Verkaufstransparenz, nutzt jedoch das CRM-API-Kontingent. Batch-Dateiexporte sind effizienter, führen jedoch zu einer Latenz.
>
>- **Streaming-CRM-Synchronisierungsfavoriten:** Reaktionsfähigkeit des Vertriebs, sofortige Kontowarnungen, Echtzeit-Pipeline-Sichtbarkeit
>- **Batch-CRM-Aktualisierungen bevorzugen:** API-Kontingenterhaltung, Massenaktualisierungseffizienz, Ausrichtung an CRM-Datenladefenstern
>- **Empfehlung:** Verwenden Sie die Streaming-CRM-Synchronisierung für Änderungen der Kontoqualifizierung mit hoher Priorität (z. B. Wechsel des Kontos zur „verkaufsbereiten“ Ebene). Verwenden Sie Batch-Dateiexporte für Massenaktualisierungen wie monatliche Kontobewertungs-Aktualisierungen oder Gebietszuweisungslisten.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzlichen Kontext und detaillierte Anleitungen für die in diesem Anwendungsfallmuster verwendeten Funktionen.

**[!DNL RT-CDP]B2B edition**

- [Übersicht über Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b)
- [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition - Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**Zielgruppenauswertung und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Audience-Komposition](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-composition)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)

**Ziele und Aktivierung**

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3-Ziel](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Aktivieren von Zielgruppen für Streaming-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Aktivieren von Zielgruppen für Batch-Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/guardrails)

**Datenquellen und Connectoren**

- [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
- [Marketo Engage-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/crm/salesforce)

**Datenmodellierung und Identität**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)

**Data Governance und Datenschutz**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Überwachung und Beobachtbarkeit**

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)
- [Überwachen von Zieldatenflüssen](https://experienceleague.adobe.com/de/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Überwachen von Quelldatenflüssen](https://experienceleague.adobe.com/de/docs/experience-platform/sources/api-tutorials/monitor)
- [Lizenznutzungs-Dashboard](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Reporting und Analysen**

- [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)
- [Verbindungen - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-connections/overview)
- [Übersicht über Datenansichten](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/data-views)

**Tutorials und Handbücher**

- [Erste Schritte mit Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Erstellen eines Schemas für B2B-Quellen](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b)
- [Sandbox-Tools](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
