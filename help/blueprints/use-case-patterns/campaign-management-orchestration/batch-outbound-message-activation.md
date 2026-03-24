---
title: Batch-Aktivierung ausgehender Nachrichten
description: Erfahren Sie, wie Sie eine Audience auswerten und eine geplante ausgehende Nachricht in einer einzigen Batch-Ausführung versenden.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 1%

---

# Batch-Aktivierung ausgehender Nachrichten

Dieses Handbuch bietet eine vollständige Implementierungsreferenz für den Versand von geplanten ausgehenden Nachrichten an definierte Zielgruppensegmente mithilfe von [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die alle praktikablen Implementierungsansätze, die Entscheidungsüberlegungen für jede Wahl und Informationen zur [!DNL Adobe Experience League] verstehen müssen.

Die Aktivierung ausgehender Batch-Nachrichten ist das grundlegende Kampagnenmuster für 1:n-ausgehende Nachrichten. Es umfasst den gesamten Lebenszyklus von der Zielgruppendefinition über den Nachrichtenversand bis hin zur Leistungsanalyse. Dieses Handbuch stellt drei Implementierungsoptionen vor - Geplante Kampagne, zielgruppengesteuertes Journey und API-ausgelöste Kampagne - und bietet strukturierte Entscheidungshilfen zur Auswahl des richtigen Ansatzes für jeden Anwendungsfall.

Es bietet Implementierungsoptionen, Zielgruppenanalysen, Benutzeroberflächen-Navigationspfade und [!DNL Experience League] Dokumentationsreferenzen.

## Anwendungsfall - Übersicht

Unternehmen müssen häufig eine einzelne Nachricht an ein bekanntes Zielgruppensegment zu einem bestimmten Zeitpunkt oder als Reaktion auf ein Systemereignis senden. Dieses Muster erfüllt diese Anforderung, indem es die Zielgruppenauswertung in [!DNL RT-CDP] mit der Nachrichtenbearbeitung und der Kampagnenausführung in [!DNL Journey Optimizer] kombiniert.

Das Geschäftsszenario ist einfach: Definieren Sie, wer die Nachricht erhalten soll, erstellen Sie den Nachrichteninhalt mit Personalisierung, binden Sie die Audience und Nachricht in eine Kampagne oder Journey und führen Sie den Versand nach einem Zeitplan, über die Audience-Qualifizierung oder über einen System-Trigger aus. Das Ergebnis ist eine zugestellte Nachricht mit vollständigen Berichten zu Versand-, Interaktions- und Konversionsmetriken.

Dieses Muster gilt immer dann, wenn ein Geschäftsziel durch den Versand einer einzelnen Nachricht an eine bekannte Zielgruppe in einer Ausführung vorangebracht werden kann. Sie unterscheidet sich von ereignisgesteuertem Messaging, das auf Echtzeit-Verhaltensereignisse reagiert, und von mehrstufig orchestrierten Journey, die Profile im Laufe der Zeit durch mehrere Touchpoints führen. Die Batch-Aktivierung ist das einfachste Kampagnenmuster und der häufigste Ausgangspunkt für Anwendungsfälle für ausgehende Nachrichten.

## Wichtige Geschäftsziele

In diesem Abschnitt werden die primären Geschäftsziele identifiziert, die die Aktivierung von Batch-ausgehenden Nachrichten unterstützt.

### E-Mail- und Kampagneninteraktion steigern

**Beschreibung:** Verbessern Sie Öffnungsraten, Clickthrough-Raten und die allgemeine Kampagnenreaktion durch optimierte Inhalte und Zielgruppenbestimmung.

**KPIs:** Öffnungsraten, Interaktion, Konversionsraten

### Umsatz und Umsatz steigern

**Beschreibung:** Steigern Sie Ihren Umsatz durch optimierte Digitalkanäle, Kampagnen und Journey.

**KPIs:** Konversionsraten, inkrementeller Umsatz, durchschnittlicher Bestellwert

**Verwandtes Geschäftsziel:** [Umsatz und Umsatz steigern](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Kampagnenausführung optimieren

**Beschreibung:** Verkürzen Sie die Erstellungszeit einer Kampagne und vereinfachen Sie den Versand über mehrere Kanäle mithilfe von Vorlagen, Automatisierung und standardisierten Prozessen.

**KPIs:** Markteinführungsgeschwindigkeit, Effizienz, termingerechte Fertigstellung %

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen gängige Anwendungen der Aktivierung von Batch-ausgehenden Nachrichten.

- **Verkaufsankündigung oder Werbe-E-Mail** Explosion - Senden eines Werbeangebots an ein Segment zugelassener Kunden an einem geplanten Datum
- **Push-Benachrichtigung zur Produkteinführung** - Interessierte Kunden per Push über die Verfügbarkeit eines neuen Produkts informieren
- **Newsletter oder Digest-E-**: Bereitstellen periodischer Inhaltszusammenfassungen für Abonnenten-Zielgruppen
- **Einladung zur Veranstaltungsregistrierung** - Laden Sie qualifizierte Interessenten zu Webinaren, Konferenzen oder persönlichen Veranstaltungen ein.
- **E-Mail zur Abonnementverlängerung** - Erinnert Kunden, die sich dem Verlängerungsdatum nähern, Maßnahmen zu ergreifen
- **Meilenstein-Benachrichtigung zum Treueprogramm** - Gratulieren Sie Mitgliedern, die Treuestufen oder Punkteschwellenwerte erreichen
- **Spezifische call-to-action-E** Mail - Fördern einer zielgerichteten Aktion, z. B. Abschluss eines Kaufs, Aktualisieren von Voreinstellungen oder Registrierung für ein Programm
- **SMS-Kampagne für Flash-Verkauf oder zeitlich begrenztes Angebot** — Senden Sie dringende, zeitlich begrenzte Promotions per SMS an angemeldete Zielgruppen

## Wichtige Performance-Indikatoren

In der folgenden Tabelle sind die KPIs zur Messung der Kampagneneffektivität aufgeführt.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Zustellrate | Prozentsatz der erfolgreich an Empfänger zugestellten Nachrichten | Zugestellt/gesendet x 100 |
| Öffnungsrate | Prozentsatz der zugestellten Nachrichten, die von Empfängern geöffnet wurden | Einzelöffnungen/Lieferung x 100 |
| Clickthrough-Rate (CTR) | Prozentsatz der zugestellten Nachrichten, auf die auf einen Link geklickt wurde | Einzelklicks/Zugestellt x 100 |
| Clickto-Open-Rate (CTOR) | Prozentsatz der geöffneten Nachrichten, bei denen auf einen Link geklickt wurde | Einzelklicks/Einzelöffnungen x 100 |
| Konversionsrate | Prozentsatz der Empfängerinnen und Empfänger, die die gewünschte Aktion abgeschlossen haben | Konversionen/Geliefert x 100 |
| Abmelderate | Prozentsatz der Empfängerinnen und Empfänger, die sich nach Erhalt der Nachricht abgemeldet haben | Abmeldungen/Zustellungen x 100 |
| Bounce-Rate | Prozentsatz der Nachrichten, die nicht zugestellt werden konnten | Bounces/Sent x 100 |
| Umsatz pro gesendeter E-Mail | Der der Kampagne zugewiesener Umsatz dividiert durch die gesendeten Nachrichten | Gesamtumsatz/Gesendet |

## Anwendungsfallmuster

**Batch-Aktivierung ausgehender Nachrichten**

Bewerten Sie eine Audience und senden Sie dann eine geplante ausgehende Nachricht (E-Mail, SMS, Push) an alle qualifizierten Profile in einer einzigen Batch-Ausführung.

**Funktionskette:** Zielgruppenauswertung > Nachrichtenbearbeitung > Kampagnenausführung > Berichterstellung

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Muster zu implementieren.

- **[!DNL Adobe Journey Optimizer](AJO)** - Nachrichtenbearbeitung, Kanalkonfiguration, Kampagnenausführung, Journey-Orchestrierung, Inhaltsexperimente, Häufigkeitsregeln und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — Zielgruppenbewertung, Einverständnis und Durchsetzung der Governance
- **[!DNL Adobe Experience Platform](AEP)** - Profilspeicher, Identity Service, Schemata, Datensätze, Datenerfassung

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit einer aktiven Kanalkonfiguration bereitgestellt. Senden der delegierten Subdomain, des zugewiesenen IP-Pools und des Abschlusses der IP-Aufwärmung. Benutzerrollen mit Berechtigungen für die Kampagnen-/Journey-Erstellung zugewiesen. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Schema für individuelles XDM-Profil mit Attributen, die für die Segmentierung und Personalisierung verwendet werden (z. B. Name, E-Mail, Voreinstellungen, Ebene). XDM ExperienceEvent-Schema, das die Zielkonversionsaktion (z. B. `commerce.purchases`, `web.webInteraction`) für das Konversionstracking nach der Kampagne erfasst. Profilaktivierte Datensätze für beide Schemata. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Web SDK- oder Analytics-Tagging auf dem CTA-Ziel muss aktiv sein, um Konversionsereignisse zu erfassen. Streaming- oder Batch-Aufnahme-Pipelines für Profilattribute müssen funktionsfähig sein. | [Web SDK - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identitäts- und Profilkonfiguration | Angenommen an Ort und Stelle | Identity-Namespaces für E-Mails (und alle geräteübergreifenden Kennungen) konfiguriert. Für Personalisierung erforderliche Profilattribute, die zum Sendezeitpunkt zugeordnet, aufgenommen und aufgelöst werden. Zusammenführungsrichtlinie konfiguriert. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | In RT-CDP definierte Zielgruppe unter Verwendung von Segment Builder oder Zielgruppenkomposition. Zielgruppe, die mit einer Population ungleich null veröffentlicht und ausgewertet wird. In der Implementierungsphase 1 über die RT-CDP-Zielgruppenbewertung behandelt. | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie die Tage seit dem letzten Kauf, die Anzahl der lebenslangen Bestellungen oder der Interaktionswert verbessern die Genauigkeit der Zielgruppe und ermöglichen eine umfassendere Personalisierung der Nachricht. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Richtlinien zur Datenaufbewahrung (Gültigkeit) sollten für Ereignis-Datensätze vorhanden sein, die das Konversions-Tracking fördern. Felder des Einverständnisschemas müssen für die Durchsetzung von Opt-in/Opt-out auf Kanalebene konfiguriert werden. | [Advanced Data Lifecycle Management - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Feldergruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für PII-Felder, die bei der Personalisierung verwendet werden, stellen die Einhaltung der Vorschriften während der Aktivierung sicher. Verhindert die unbefugte Verwendung sensibler Profildaten in Nachrichteninhalten oder Zielgruppenexporten. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Die Überwachung des Echtzeit-Versands ist Teil der Reporting-Phase. Warnhinweise auf Plattformebene zu Aufnahmefehlern oder zur Lizenznutzung bieten eine betriebliche Sichtbarkeit, die über die Metriken auf Kampagnenebene hinausgeht. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting und Analyse | Eingeschlossen | Kampagnen- und Journey-Berichte werden in der Reporting-Phase behandelt. Für eine tiefer gehende kanalübergreifende Analyse bietet die CJA-Integration über die integrierten Berichte von AJO hinaus funnel-Analysen, Attributionsmodelle und Kohortenanalysen. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kanalkonfiguration | Phase 2: Kanalkonfiguration | Konfigurieren oder validieren Sie die Kanaloberfläche (E-Mail, SMS oder Push) einschließlich Subdomain, IP-Pool, Absendereinstellungen und Unterdrückungsliste |
| Verfassen von Nachrichten | Phase 3: Nachrichtenbearbeitung | Erstellen von Nachrichteninhalten mit Vorlagen, der E-Mail-Designer, Personalisierungsausdrücken, bedingten Inhaltsbausteinen und Inhaltsfragmenten |
| Kampagnenausführung | Phase 4: Erstellung von Kampagnen oder Journey | Erstellen, konfigurieren und aktivieren Sie eine geplante oder durch eine API ausgelöste Kampagne, die Zielgruppe, Nachricht und Ausführungsplan bindet |
| Inhaltsexperiment | Phase 4: Erstellung von Kampagnen oder Journey | Konfigurieren Sie optional A/B- oder multivariate Inhaltsexperimente, um die Nachrichtenleistung zu optimieren |
| Häufigkeits- und Geschäftsregeln | Phase 4: Erstellung von Kampagnen oder Journey | Optional können Sie Regeln zur Frequenzlimitierung anwenden, um eine Übernachrichtenüberlastung über gleichzeitige Kampagnen hinweg zu verhindern |
| Konflikt- und Prioritätenmanagement | Phase 4: Erstellung von Kampagnen oder Journey | Prioritätswerte zuweisen und Konfliktlösung konfigurieren, wenn mehrere Kampagnen auf sich überschneidende Audiences abzielen |
| Reporting und Leistungsanalyse | Phase 5: Reporting und Leistungsanalyse | Überwachen von Versandmetriken über Live-Berichte während der Ausführung und Analysieren der Kampagnenleistung über historische Berichte nach Abschluss |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 1: Evaluierung der Zielgruppe | Definieren Sie Zielgruppenregeln mit Segment Builder oder Zielgruppenkomposition, wählen Sie die Auswertungsmethode (Batch, Streaming oder Edge) aus und validieren Sie die Zielgruppenpopulation |
| Durchsetzung von Einverständnis und Governance | Phase 1: Evaluierung der Zielgruppe | Erzwingen von Einverständnisvoreinstellungen und Datennutzungsrichtlinien, um sicherzustellen, dass nur Profile mit Einverständnis die Kampagnennachricht erhalten |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [ ] AJO-Sandbox ist bereitgestellt und aktiv
- [ ] Senden der Subdomain wird delegiert und überprüft (SPF, DKIM, DMARC konfiguriert)
- [ ] IP-Pool wird zugewiesen und für das Produktions-Sendevolumen aufgewärmt
- [ ] Mindestens eine aktive Kanaloberfläche (E-Mail, SMS oder Push) ist vorhanden
- [ ] Benutzerkonten verfügen über Berechtigungen zum Erstellen von Kampagnen/Journey und zum Erstellen von Inhalten
- [ ] XDM-Profilschema enthält Attribute, die für die Zielgruppensegmentierung und Nachrichtenpersonalisierung benötigt werden
- [ ] XDM-Ereignisschema erfasst Konversionsereignisse für die Nachverfolgung nach einer Kampagne
- [ ] Profildaten werden über Identity Service aufgenommen und vereinheitlicht
- [ ] Tagging mit Web SDK oder Analytics ist auf der CTA-Zielseite aktiv, um Konversionsereignisse zu erfassen
- [ ] Einverständnisfelder werden in Profilen für den Ziel-Messaging-Kanal ausgefüllt
- [ ] Content-Assets (Bilder, Logos, Markenrichtlinien) stehen für die Nachrichtengestaltung zur Verfügung.

## Implementierungsoptionen

In diesem Abschnitt werden drei Implementierungsoptionen für die Aktivierung von Batch-ausgehenden Nachrichten sowie ein Vergleich und eine Entscheidungshilfe beschrieben.

### Option A: Geplante Kampagne (einmaliger Batch-Versand)

**Am besten geeignet für:** Sendungen mit Datumsverankerung - Verkaufsankündigungen, Produkteinführungen, Fristen für die Veranstaltungsregistrierung, Verlängerungserinnerungen, Newsletter-Explosionen und alle Sendungen, bei denen das Ausführungsdatum im Voraus bekannt ist.

**Funktionsweise:**

Eine geplante Kampagne ist die einfachste Variante einer Batch-ausgehenden Nachricht. Der Marketing-Experte definiert die Zielgruppe, verfasst den Nachrichteninhalt, legt ein Sendedatum und eine Sendezeit fest und aktiviert die Kampagne. Zur geplanten Ausführungszeit bewertet AJO die Zielgruppe, um die aktuelle qualifizierte Population zu ermitteln, und sendet die Nachricht dann an alle qualifizierten Profile in einem einzigen Batch.

Die gesamte Konfiguration erfolgt in der Benutzeroberfläche von AJO Campaign - es gibt keine Journey-Arbeitsfläche, keine Verzweigungslogik und keine Warteschritte. Dadurch lassen sich geplante Kampagnen am schnellsten konfigurieren und am einfachsten verwalten. Die Kampagne kann für die sofortige Ausführung, ein bestimmtes Datum/eine bestimmte Uhrzeit in der Zukunft oder einen wiederkehrenden Zeitplan (täglich, wöchentlich, monatlich) festgelegt werden.

**Wichtige Aspekte:**

- Die Zielgruppe wird zur Ausführungszeit ausgewertet, sodass Profile einbezogen werden, die sich für die Planung und Ausführung eignen
- Keine Verzweigungs-, Warte- oder Bedingungslogik verfügbar — die Nachricht wird an alle qualifizierten Profile gesendet
- Unterstützt Inhaltsexperimente (A/B-Tests) direkt innerhalb der Kampagnenkonfiguration
- Zu den Kampagneneigenschaften gehört ein Prioritätswert für die Konfliktlösung mit anderen Kampagnen

**Vorteile:**

- Einfache Konfiguration mit geringstem Aufwand
- Schnellste Time-to-Launch für unkomplizierte Batch-Sendungen
- Integrierte Unterstützung für wiederkehrende Zeitpläne
- Nativ unterstützte Inhaltsexperimente
- Zielgruppe zur Ausführungszeit neu bewertet, um Frische zu gewährleisten

**Einschränkungen:**

- Keine Warteschritte, Bedingungen oder Verzweigungen vor dem Versand
- Profilverhalten kann zwischen Planung und Ausführung nicht beeinflusst werden
- Nur eine Nachrichtenaktion - keine Multi-Touch-Sequenzen
- Kann nach der Aktivierung nicht mehr bearbeitet werden (muss duplizieren und ändern)

**Experience League:**

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B: Zielgruppengesteuertes Journey

**Am besten geeignet für:** Verhaltensgesteuerte Sendungen - Transaktionsbenachrichtigungen, Erinnerungen an den Ablauf von Testsendungen, Meilensteinfeiern, auf Qualifizierung basierende Kontaktaufnahme und alle Sendungen, bei denen der Trigger Zielgruppenqualifizierung oder ein Geschäftsereignis anstelle eines Kalenderdatums ist.

**Funktionsweise:**

Eine von einer Zielgruppe ausgelöste Journey verwendet die Journey-Arbeitsfläche, um eine Nachricht zu senden, wenn ein Profil sich für eine definierte Zielgruppe qualifiziert oder ein qualifizierendes Ereignis auslöst. Der Journey-Eintrag wird durch Änderungen der Zielgruppenzugehörigkeit (Profile, die in die Zielgruppe eintreten) und nicht durch einen festen Zeitplan ausgelöst. Die Journey-Arbeitsfläche ermöglicht optionale Warteschritte, Bedingungsverzweigungen und Unterdrückungslogik vor der Nachrichtenaktion und bietet so mehr Flexibilität als eine geplante Kampagne.

Die Journey wird in der Benutzeroberfläche von AJO Journey mit dem Eintrittsereignis „Zielgruppe lesen“ konfiguriert. Wenn sich Profile für die Zielgruppe qualifizieren, geben sie die Journey ein und durchlaufen die Arbeitsflächenknoten. Eine einfache Implementierung kann nur einen einzigen E-Mail-Aktionsknoten enthalten, wodurch sie einer geplanten Kampagne funktional ähnelt, jedoch mit einem auf der Zielgruppen-Qualifizierung basierenden Einstiegszeitpunkt. Komplexere Implementierungen können Warteknoten (z. B. 24 Stunden nach der Qualifizierung warten), Bedingungsknoten (z. B. Überprüfen, ob das Profil eine frühere E-Mail geöffnet hat) oder Unterdrückungslogik vor dem Nachrichtenversand hinzufügen.

**Wichtige Aspekte:**

- Der Journey-Eintrag wird durch die Zielgruppen-Qualifizierung ausgelöst, nicht durch ein Kalenderdatum
- Die Journey-Arbeitsfläche unterstützt Warte-, Bedingungs- und Split-Knoten für die Logik vor dem Versand
- Regeln für den erneuten Eintritt von Journey steuern, ob Profile mehrmals auf die Journey zugreifen können
- Journey-Schlichtungseinstellungen bestimmen das Verhalten, wenn sich ein Profil bereits auf einer konkurrierenden Journey befindet

**Vorteile:**

- Flexible Einstiegszeiten basierend auf der Zielgruppen-Qualifizierung statt auf einem festen Zeitplan
- Warte- und Bedingungsknoten ermöglichen die Logik vor dem Versand (z. B. Verzögerung, Prüfung, Unterdrückung)
- Eingabefelder verhindern doppelte Sendungen an dasselbe Profil
- Kann zu einem mehrstufigen Journey erweitert werden, wenn sich der Anwendungsfall weiterentwickelt
- Unterstützt Reporting auf Journey-Ebene mit Metriken auf Eintritts-, Austritts- und Knotenebene

**Einschränkungen:**

- Mehr Konfigurationsaufwand als eine geplante Kampagne
- Journey-Arbeitsfläche erhöht die Komplexität auch bei Anwendungsfällen mit einer einzigen Nachricht
- Journey muss veröffentlicht sein und kann nicht live bearbeitet werden (neue Version erstellen)
- Die Eintrittsobergrenze kann die Anzahl der Profile begrenzen, die innerhalb eines Zeitfensters eintreten

**Experience League:**

- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Zielgruppen-Journey lesen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Option C: API-ausgelöste Kampagne

**Am besten geeignet für:** Systeminitiierte Sendungen - Bestellbestätigungen mit Upsell-Inhalten, Support-Ticket-Auflösungs-Follow-ups, Transaktionsbenachrichtigungen mit Marketing-Inhalten und alle Sendungen, bei denen das auslösende Ereignis zu einem bestimmten Zeitpunkt von einem externen System stammt.

**Funktionsweise:**

Eine von einer API ausgelöste Kampagne wird über einen REST-API-Aufruf aktiviert, sobald ein Systemereignis ausgelöst wird. Die Kampagne ist in AJO mit Nachrichteninhalt und Kanaleinstellungen vorkonfiguriert, aber anstatt eine vordefinierte Zielgruppe zu binden, gibt der API-Aufruf die Empfängerprofile an und kann kontextuelle Daten übergeben, die dynamische Nachrichtenparameter ausfüllen.

Diese Variante eignet sich optimal, wenn der Versandzeitpunkt durch ein externes System (z. B. ein Auftragsverwaltungssystem, einen CRM-Workflow oder eine Support-Plattform) und nicht durch eine Zielgruppenbewertung oder einen Kalenderplan bestimmt wird. In der API-Trigger-Payload übergebene kontextuelle Daten - wie Bestelldetails, Ticketnummern oder Produktnamen - können den Nachrichteninhalt mithilfe von kontextuellen Attributen personalisieren, die nicht im Profil gespeichert sind.

**Wichtige Aspekte:**

- Es ist keine vorgebundene Zielgruppe erforderlich. In der API-Empfängeranfrage werden die Empfängerinnen und Trigger angegeben.
- Kontextbezogene Daten in der Trigger-Payload ermöglichen eine dynamische Personalisierung über Profilattribute hinaus.
- Die Kampagne muss vom Typ „API-ausgelöst“ sein und muss aktiviert werden, bevor sie Trigger-Anfragen empfangen kann
- Jede API-Trigger-Anfrage unterstützt bis zu 20 Profilempfänger
- Zielgruppenauswertung (Phase 1) kann übersprungen werden, da die Empfänger vom API-Aufruf stammen

**Vorteile:**

- Echtzeit-Auslösung durch externe Systeme zum Zeitpunkt des Ereignisses
- Kontextuelle Personalisierung mit nicht im Profil gespeicherten Daten (Bestelldetails, Ticketinformationen)
- Kein Mehraufwand für die Zielgruppenbewertung - Empfänger werden direkt angegeben
- Unterstützt hybrides Messaging für Transaktionsnachrichten und Marketing

**Einschränkungen:**

- Externe Systemintegration erforderlich, um den API-Trigger zu senden
- Maximal 20 Empfänger pro API-Trigger-Anfrage
- Keine integrierte Zielgruppenbewertung - das aufrufende System muss die Empfänger bestimmen
- Höhere technische Komplexität aufgrund der Anforderungen an die API-Integration
- Inhaltsexperimente werden für API-ausgelöste Kampagnen nicht unterstützt

**Experience League:**

- [API-ausgelöste Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Trigger-Kampagnen mit APIs](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: Geplante Kampagne | Option B: Zielgruppengesteuertes Journey | Option C: API-ausgelöste Kampagne |
| --- | --- | --- | --- |
| Am besten geeignet für | Versand mit Datumsverankerung (Promotions, Launches, Newsletter) | Verhaltensgesteuerte Sendungen (Qualifizierungsereignisse, Meilensteine) | Vom System initiierte Sendungen (Auftragsbestätigungen, Transaktionen) |
| Komplexität | Niedrig | Mittel | Medium-Hoch |
| Trigger-Typ | Kalenderdatum/-uhrzeit oder wiederkehrender Zeitplan | Zielgruppen-Qualifizierung oder Geschäftsereignis | API-Aufruf für externes System |
| Logik vor dem Versand | Ohne | Warten, Bedingung, geteilte Knoten verfügbar | Keine (Logik im aufrufenden System) |
| Zielgruppenbindung | Vordefinierte RT-CDP-Zielgruppe | Vordefinierte RT-CDP-Zielgruppe | In der API-Payload angegebene Empfänger |
| Kontextbezogene Daten | Nur Profilattribute | Nur Profilattribute | Profilattribute + API-Payload-Daten |
| Inhaltsexperiment | Unterstützt | Unterstützt (bei Nachrichtenaktion) | Nicht unterstützt |
| Frequenzbegrenzung | Unterstützt | Unterstützt | Unterstützt |
| Wiedereintrittskontrolle | Nicht zutreffend (einmalige Ausführung) | Konfigurierbare Regeln für den Wiedereintritt | Nicht zutreffend (pro Anfrage) |
| Konfigurationsoberfläche | AJO-Kampagnen | Journey von AJO | AJO-Kampagnen + externes System |
| Erfordert | Zielgruppe, Kanaloberfläche, Nachricht | Zielgruppe, Kanaloberfläche, Nachricht, Journey-Arbeitsfläche | Kanaloberfläche, Nachricht, API-Integration |

### Wählen der richtigen Option

Verwenden Sie den folgenden Entscheidungsfluss, um die entsprechende Implementierungsoption auszuwählen:

1. **Wird der Versand durch ein externes Systemereignis ausgelöst (z. B. aufgegebene Bestellung, aufgelöstes Ticket)?** Wenn ja, wählen Sie **Option C: API-ausgelöste Kampagne**. Dies ist die einzige Option, die systeminitiierte Trigger mit kontextuellen Payload-Daten unterstützt.

2. **Ist der Versand an einem bestimmten Kalenderdatum oder einem wiederkehrenden Zeitplan verankert?** Wenn ja, wählen Sie **Option A: Geplante Kampagne**. Dies ist die einfachste und schnellste Konfiguration für datumsgesteuerte Sendungen.

3. **Muss der Versand auf die Zielgruppen-Qualifizierung reagieren oder erfordert er eine Logik vor dem Versand (Warten, Bedingung, Unterdrückung)?** Wenn ja, wählen Sie **Option B: Zielgruppen-ausgelöstes Journey**. Die Journey-Arbeitsfläche bietet die Flexibilität für eine verhaltensgesteuerte Einstiegs- und Entscheidungslogik vor der Bereitstellung.

4. **Sendet der Sender eine einfache Übertragung an eine bekannte Zielgruppe ohne spezielle Timing- oder Logikanforderungen?** Wählen Sie **Option A: Geplante Kampagne** für den geringsten Konfigurationsaufwand.

## Implementierungsphasen

In diesem Abschnitt werden die einzelnen Implementierungsphasen detailliert beschrieben, einschließlich Entscheidungspunkten und optionenspezifischen Leitlinien.

### Phase 1: Auswerten der Audience

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung

In dieser Phase wird das Zielgruppensegment definiert und ausgewertet, das die Kampagnennachricht erhält. Sie bestimmt anhand von Profilattributen, Verhaltenssignalen und Unterdrückungsregeln, welche Profile für den Versand qualifiziert sind.

>[!NOTE]
>Bei Option C (API-ausgelöste Kampagne) kann diese Phase übersprungen werden, wenn die Empfänger vollständig in der Payload des API-Triggers angegeben sind. Allerdings profitieren auch API-ausgelöste Kampagnen von einer Unterdrückungszielgruppe, die Profile herausfiltert, die keine Nachrichten erhalten sollten.

#### Entscheidung: Zielgruppenkriterien

Welche Bedingungen definieren die Zielgruppe? Welche Unterdrückungsregeln sollten Profile ausschließen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Auf Profilattributen basierende Zielgruppe | Die Zielgruppe wird durch demografische Attribute, Präferenzen oder Statusattribute definiert | Einfachste Erstellung; unterstützt alle Auswertungsmethoden |
| Verhaltensbezogene ereignisbasierte Zielgruppe | Die Zielgruppe wird durch Aktionen definiert, die innerhalb eines Zeitfensters ausgeführt (oder nicht ausgeführt) werden | Erfordert die Aufnahme von Ereignisdaten; Zeitfensterregeln können die Streaming-Berechtigung einschränken |
| Audience-Komposition (abgeleitete Audience) | Zielgruppe erfordert Rangfolgen-, Aufspaltungs-, Ausschluss- oder Anreicherungsvorgänge für mehrere Quell-Zielgruppen | Leistungsfähigere, aber nur Batch-Auswertung; auf 10 Kompositionen pro Sandbox beschränkt |

#### Entscheidung: Auswertungsmethode

Wie schnell muss die Zielgruppe aktualisiert werden, um neue qualifizierte oder disqualifizierte Profile widerzuspiegeln?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch-Auswertung | Geplante Kampagnen, bei denen die Aktualisierung der Zielgruppe innerhalb eines Tages akzeptabel ist; große, komplexe Zielgruppen | Standard für die meisten Segmenttypen; Prozesse auf täglicher Basis oder bei Bedarf; unterstützt alle Segmentregelfunktionen |
| Streaming-Auswertung | Zielgruppengesteuerte Journey, in denen Profile nahezu in Echtzeit eintreten müssen, sobald sie sich qualifizieren | Automatisch für geeignete Segmentregelausdrücke; nicht alle Segmenttypen sind für Streaming qualifiziert; nahezu in Echtzeit auftretende Latenz (Sekunden bis Minuten) |
| Edge-Auswertung | Nicht typisch für dieses Muster (wird für die Personalisierung derselben Seite verwendet) | Eingeschränkte Segmentregelunterstützung; Millisekunden-Latenz; nur relevant bei Kombination mit Web-Personalisierungsmustern |

#### Entscheidung: Zusammenführungsrichtlinie

Welche Zusammenführungsrichtlinie sollte die Zielgruppe verwenden, um Profilfragmente aufzulösen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Standard-Zusammenführungsrichtlinie (Zeitstempel geordnet) | Häufigste Anwendungsfälle für Batch-Kampagnen | Zuletzt gewonnener Attributwert; Standard für ausgehende Nachrichten |
| Benutzerdefinierte Zusammenführungsrichtlinie (Datensatzpriorität) | Wann eine bestimmte Datenquelle Priorität für Schlüsselattribute haben soll | Nützlich, wenn CRM-Daten Web-erfasste Daten für bestimmte Felder überschreiben sollen |

#### Navigation in der Benutzeroberfläche

Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

#### Wichtige Konfigurationsdetails

- Definieren der Zielgruppe mithilfe von Segment Builder mit Segmentregeln für Profilattribute, Verhaltensereignisse und Segmentzugehörigkeit
- Wenden Sie Unterdrückungsregeln an, um Profile auszuschließen, die bereits konvertiert sind, kürzlich eine ähnliche Nachricht erhalten haben oder sich abgemeldet haben
- Stellen Sie sicher, dass die Zielgruppe eine Population ungleich null aufweist, bevor Sie fortfahren
- Stellen Sie bei Batch-Kampagnen sicher, dass ein Zeitplan für die Segmentauswertung aktiv ist oder dass der Trigger eine On-Demand-Auswertung durchführt
- Einverständnisfelder bestätigen (`consents.marketing.email.val`, `consents.marketing.sms.val` usw.) werden ausgefüllt und durchgesetzt

#### Wo die Optionen auseinander gehen

**Für Option A (geplante Kampagne):**

Die Batch-Auswertung ist typisch. Die Zielgruppe wird bei der Kampagnenausführung neu ausgewertet, sodass die aktuelle qualifizierte Population angesprochen wird. Definieren Sie die Audience, überprüfen Sie deren Population und fahren Sie dann mit der Kampagnenerstellung fort.

**Für Option B (zielgruppengesteuertes Journey):**

Die Streaming-Auswertung wird bevorzugt, sodass Profile nach ihrer Qualifizierung in die Journey eintreten. Stellen Sie sicher, dass der Segmentregelausdruck für Streaming geeignet ist (einfache Ereignis-Trigger, Attributvergleiche, begrenzte Zeitfenster). Konfigurieren Sie die Zielgruppe und überprüfen Sie, ob die Streaming-Qualifizierung aktiv ist.

**Für Option C (API-ausgelöste Kampagne):**

Die Zielgruppenauswertung kann vollständig übersprungen werden. Erstellen Sie bei Verwendung eine Unterdrückungszielgruppe, um Profile zu filtern, die die Nachricht nicht erhalten sollen (z. B. kürzlich abgemeldete oder bereits konvertierte Profile). Das aufrufende System bestimmt die primären Empfänger.

#### Dokumentation zu Experience League

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Audience-Komposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Konfigurieren des Kanals

**Anwendungsfunktion:** AJO: Kanalkonfiguration

In dieser Phase wird die Kanaloberfläche (Voreinstellung) validiert oder erstellt, die die Versandinfrastruktur für die Nachricht definiert - Subdomain, IP-Pool, Absenderidentität, Antwortadresse und Abmeldeeinstellungen. Es muss eine gültige Kanaloberfläche vorhanden sein, bevor Nachrichteninhalte verfasst oder Kampagnen aktiviert werden können.

#### Entscheidung: Target-Kanal

Welcher Messaging-Kanal wird die Kampagnennachricht senden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| E-Mail | Die meisten Kampagnentypen - Newsletter, Promotions, Benachrichtigungen, Erneuerungen | Erfordert delegierte Subdomain, erwärmten IP-Pool, Absenderidentität und Abmeldekonfiguration |
| SMS | Zeitkritische oder kurze Nachrichten - Flash-Verkäufe, Terminerinnerungen, OTP-Codes | Erfordert SMS-Provider-Anmeldedaten (Sinch, Twilio oder Infobip); höhere Kosten pro Nachricht; strengere Zustimmungsanforderungen |
| Push-Benachrichtigung | Zielgruppen, die für Mobilgeräte interagieren - App-Aktualisierungen, standortbasierte Angebote, In-App-Funktionsankündigungen | Erfordert APNs (iOS)- und/oder FCM (Android)-Anmeldeinformationen. Für die Benutzer muss eine App mit erteilten Push-Berechtigungen installiert sein |

#### Entscheidung: Auswahl der Kanaloberfläche

Gibt es bereits eine geeignete Kanaloberfläche in der Sandbox, oder muss eine neue erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Vorhandene Oberfläche wiederverwenden | Eine verifizierte, aktive Oberfläche entspricht der erforderlichen Subdomain, Absenderidentität und dem Kanaltyp | Schnellster Pfad; keine DNS- oder Aufwärmkonfiguration erforderlich |
| Neue Oberfläche erstellen | Keine vorhandene Oberfläche entspricht den Anforderungen oder es ist eine neue Subdomain/Absenderidentität erforderlich | Subdomain-Zuweisung, DNS-Überprüfung, IP-Pool-Zuweisung und möglicherweise IP-Aufwärmung erforderlich (2-4 Wochen für neue IPs) |

#### Entscheidung: Handhabung von Abmeldungen

Wie sollte das Opt-out auf der Kanaloberfläche verwaltet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Kopfzeile für Ein-Klick-Liste-Abo | Standard für alle Marketing-E-Mails; von wichtigen ISPs (Gmail, Yahoo) zur Zustellbarkeit erforderlich | Fügt eine Mailto:- oder URL-basierte Abmelde-Kopfzeile hinzu, die von ISPs als Schaltfläche „Abmelden“ angezeigt wird |
| Abmelde-Link im E-Mail-Text | Erforderlich als Fallback für E-Mail-Clients, die keine Kopfzeilen zur Abmeldung von einer Liste unterstützen | Fügen Sie einen Abmelde-Link in die E-Mail-Fußzeile neben der Kopfzeile zur Abmeldung von der Liste ein |
| Beide (empfohlen) | Best Practice für alle Marketing-E-Mails | Maximale Compliance und bestes Zustellbarkeitsprofil |

#### Navigation in der Benutzeroberfläche

Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen (oder vorhandene auswählen)

#### Wichtige Konfigurationsdetails

- Für E-Mails: Binden Sie die sendende Subdomain, den IP-Pool, den Absendernamen, die Absender-E-Mail, die Antwortadresse und die BCC-Adresse (wenn eine Prüfkopie erforderlich ist)
- Für SMS: Konfigurieren der Anmeldeinformationen des SMS-Anbieters und der Einstellungen für Kurz- oder Langcode
- Für Push-Benachrichtigungen: Konfigurieren von APNs und/oder FCM-Anmeldeinformationen mit dem Zertifikat oder Server-Schlüssel der App
- Stellen Sie sicher, dass die Kanaloberfläche den Status „Aktiv“ aufweist, bevor Sie fortfahren
- Überprüfen Sie, ob die DNS-Einträge (SPF, DKIM, DMARC) für die sendende Subdomain korrekt konfiguriert sind
- Überprüfen der Unterdrückungsliste auf veraltete Einträge; bereinigen vor der Aktivierung

#### Dokumentation zu Experience League

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Phase 3: Verfassen der Nachricht

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung

In dieser Phase wird der Nachrichteninhalt erstellt, der an die Audience gesendet wird. Dazu gehört die Auswahl oder Erstellung einer Inhaltsvorlage, das Design des Nachrichten-Layouts, das Hinzufügen einer Personalisierung mithilfe von Profilattributen, das Konfigurieren von bedingten Inhaltsbausteinen für zielgruppenspezifische Varianten, das Erstellen wiederverwendbarer Inhaltsfragmente und das Anzeigen einer Vorschau/Testen der Nachricht mit Beispielprofilen.

#### Entscheidung: Content-Ansatz

Wie sollte der Nachrichteninhalt erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Mit vorhandener Vorlage beginnen | Von der Marke genehmigte Vorlagen sind vorhanden und stimmen mit dem Nachrichtentyp (Werbe-, Transaktions-, Newsletter) überein. | Schnellster Authoring-Pfad; stellt Markenkonsistenz sicher; Vorlagen sind Sandbox-spezifisch |
| Von Grund auf gestalten | Keine geeignete Vorlage vorhanden oder die Nachricht erfordert ein eindeutiges Layout | Mehr Flexibilität, aber mehr Aufwand; Speichern als Vorlage zur Wiederverwendung in Betracht ziehen |
| HTML importieren | Der Nachrichtenentwurf wurde extern erstellt (z. B. in einem Design-Tool) und HTML ist bereit zum Importieren | Behält das externe Design bei; muss möglicherweise zwecks AJO-Kompatibilität und Personalisierungs-Token angepasst werden |

#### Entscheidung: Personalization-Tiefe

Welche Profilattribute sollen die Nachricht personalisieren, und sind bedingte Inhaltsbausteine erforderlich?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Grundlegende Personalisierung (Name, Begrüßung) | Einfache Kampagnen, bei denen allgemeine Inhalte mit einer personalisierten Anrede ausreichend sind | Geringer Aufwand; minimales Risiko von Rendering-Problemen; verwendet standardmäßige Profilattribute |
| Attributbasierte Personalisierung | Der Nachrichteninhalt variiert je nach Profilattributen (Ebene, Voreinstellung, Ort) | Erfordert verifizierte XDM-Pfade; testet mit mehreren Profilen, um sicherzustellen, dass alle Varianten korrekt gerendert werden |
| Bedingte Inhaltsbausteine | Verschiedene Inhaltsabschnitte müssen verschiedenen Zielgruppensegmenten in derselben Nachricht angezeigt werden | Komplexere Inhaltserstellung; für jede Bedingung ist ein standardmäßiges Fallback erforderlich; alle Permutationen werden getestet |
| Kontextuelle Personalisierung (nur Option C) | API-ausgelöste Kampagnen müssen Daten rendern, die in der Trigger-Payload übergeben werden (Bestelldetails, Ticket-Informationen) | Kontextattribute werden nicht im Profil gespeichert. Definieren Sie Platzhalter in der Nachricht und ordnen Sie sie Payload-Feldern zu. |

#### Entscheidung: Fragmentstrategie

Sollten freigegebene Inhaltsbausteine als wiederverwendbare Fragmente erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Wiederverwendbare Fragmente | Kopfzeilen, Fußzeilen, Haftungsausschlüsse oder Abmeldeblöcke werden in mehreren Kampagnen gemeinsam genutzt | Änderungen an einem Fragment werden auf alle Nachrichten übertragen, die darauf verweisen (Live und Entwurf). Es können maximal 30 Fragmente pro Nachricht übertragen werden. |
| Inline-Inhalt | Einmalige Nachricht ohne freigegebene Elemente in anderen Kampagnen | Einfachere Verwendung von Einweginhalten, kein Verbreitungsrisiko |

#### Navigation in der Benutzeroberfläche

Kampagnen > Kampagne auswählen > Inhalt bearbeiten > E-Mail-Designer (oder SMS-/Push-Editor)

#### Wichtige Konfigurationsdetails

- Entwerfen Sie das Nachrichten-Layout mithilfe von Inhaltskomponenten per Drag-and-Drop (Text, Bild, Schaltfläche, Trennlinie, Spalten)
- Legen Sie die Eigenschaften des E-Mail-Headers fest: Betreffzeile, Text des Preheaders und Absenderoberfläche
- Einfügen von Personalisierungsausdrücken mithilfe der Handlebars-Syntax (z. B. `{{profile.person.name.firstName}}`)
- Konfigurieren von Hilfsfunktionen für die Formatierung (Datum, Zahl, Zeichenfolgenmanipulation)
- Fügen Sie bedingte Inhaltsregeln hinzu, um unterschiedliche Inhalte basierend auf Profilattributen oder der Segmentzugehörigkeit anzuzeigen
- Standardinhalt für Fallback konfigurieren, wenn keine Bedingungen erfüllt sind
- Für SMS muss der Nachrichtentext unter Berücksichtigung der Zeichenbeschränkung erstellt werden
- Konfigurieren Sie für Push Titel, Textkörper, Bild und Aktion (Deep-Link oder URL)
- Vorschau der Nachricht mit Beispielprofilen zur Überprüfung des Personalisierungs-Renderings
- Testversand-E-Mails zur Überprüfung an interne Stakeholder senden
- Testen des Renderings auf allen E-Mail-Clients mit der E-Mail-Rendering-Funktion

#### Dokumentation zu Experience League

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Verwenden von Inhaltskomponenten von Email Designer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [E-Mail-Testsendungen durchführen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Email Rendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [Erstellen einer SMS-Nachricht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Gestalten einer Push-Benachrichtigung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Phase 4: Erstellen der Kampagne oder Journey

**Anwendungsfunktion:** AJO: Kampagnenausführung (Optionen A und C) oder AJO: Journey Orchestration (Option B)

In dieser Phase wird die Kampagne oder die Journey erstellt, die die Zielgruppe, die Nachricht und den Ausführungsmechanismus in einer Einheit für die Zustellbarkeit verbindet. Hier weichen die drei Implementierungsoptionen am deutlichsten voneinander ab.

#### Entscheidung: Inhaltsexperiment

Soll die Kampagne einen A/B-Test oder ein Multivarianz-Experiment zur Optimierung der Nachrichtenleistung enthalten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Kein Experiment | Einzelne Nachrichtenvariante mit hoher Konfidenz bei der Inhaltseffektivität | Einfachste Konfiguration, schnellste Aktivierung |
| A/B-Test (2 Varianten) | Testen von Betreffzeilen, CTAs oder Inhalts-Layouts mit einer klaren Hypothese | Traffic-Aufteilung 50/50 oder mit einer gewichteten Zuordnung; erfordert eine ausreichende Zielgruppengröße für die statistische Signifikanz |
| Multivarianz-Test (3+ Varianten) | Gleichzeitiges Testen mehrerer Inhaltselemente | Erfordert größere Zielgruppen; längere Dauer bis zum Erreichen des Konfidenzschwellenwerts; maximal 10 Behandlungen pro Experiment |

#### Entscheidung: Frequenzlimitierung

Sollte diese Kampagne die globalen Regeln zur Frequenzlimitierung einhalten, um Übernachrichten zu verhindern?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Häufigkeitsregeln anwenden | Campaign ist Teil eines umfassenderen Messaging-Programms mit mehreren gleichzeitigen Sendungen | Verhindert Kundenmüdigkeit. Profile, die die Obergrenze überschreiten, werden vom Versand unterdrückt |
| Von der Begrenzung ausgenommen | Campaign ist zeitkritisch oder transaktional und muss unabhängig vom aktuellen Nachrichtenverlauf alle qualifizierten Profile erreichen | Sparsam verwenden; wenn Sie Kampagnen von den Häufigkeitsregeln ausnehmen, besteht die Gefahr einer Überbotschaft |

#### Entscheidung: Prioritätswert

Welche Prioritätsstufe sollte diese Kampagne im Vergleich zu anderen aktiven Kampagnen haben?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Hohe Priorität (75-100) | Kritische Kampagnen - große Produkteinführungen, zeitlich begrenzte Angebote, Benachrichtigungen zu Vorschriften | hat Vorrang vor Kampagnen mit niedrigerer Priorität, wenn Konflikte auftreten |
| Medium-Priorität (25-74) | Standard-Marketing-Kampagnen - Newsletter, Interaktionskampagnen, allgemeine Werbeaktionen | Im Vergleich zu anderen Kampagnen. Kann unterdrückt werden, wenn eine Kampagne mit höherer Priorität in Konflikt steht. |
| Niedrige Priorität (0-24) | Nice-to-have-Sendungen - Aktualisierungen zu Informationszwecken, sekundäre Werbeaktionen | Wird zugunsten von Kampagnen mit höherer Priorität unterdrückt |

#### Wo die Optionen auseinander gehen

**Für Option A (geplante Kampagne):**

**UI-Navigation:** Kampagnen > Kampagne erstellen > Geplant > Marketing

1. Erstellen einer neuen geplanten Marketing-Kampagne
2. Wählen Sie in der Zielgruppenauswahl die Zielgruppe aus
3. Wählen Sie die Kanaloberfläche aus und verknüpfen Sie den Inhalt der erstellten Nachricht
4. Konfigurieren der Ausführungsplanung: Sofort, bestimmtes Datum/bestimmte Uhrzeit oder wiederkehrend
5. Optional Inhaltsexperimente aktivieren und Abwandlungsvarianten definieren
6. Konfigurieren Sie optional die Frequenzlimitierung und Prioritätsbewertung.
7. Überprüfen der vollständigen Kampagnenkonfiguration
8. Kampagne aktivieren

**Für Option B (zielgruppengesteuertes Journey):**

**UI-Navigation:** Journey > Journey erstellen

1. Erstellen Sie eine neue Journey mit dem Eintrittsereignis „Zielgruppe lesen“
2. Auswählen der Zielgruppe als Einstiegsquelle
3. Konfigurieren Sie die Regeln für den erneuten Eintritt (Erneute Eingabe erlauben, Einmalige Eingabe oder Erneute Eingabe nach Wartezeit)
4. Optional Warteknoten hinzufügen (z. B. 24 Stunden nach Qualifizierung warten)
5. Optional können Sie Bedingungsknoten hinzufügen (z. B. um zu überprüfen, ob das Profil zusätzliche Kriterien erfüllt)
6. Fügen Sie den Aktionsknoten der Nachricht hinzu und wählen Sie die Kanaloberfläche und den erstellten Inhalt aus
7. Ausstiegskriterien konfigurieren (z. B. Profilkonvertierungen, Profilabmeldungen)
8. Optional Inhaltsexperiment für die Nachrichtenaktion aktivieren
9. Journey überprüfen und veröffentlichen

**Für Option C (API-ausgelöste Kampagne):**

**UI-Navigation:** Kampagnen > Kampagne erstellen > API-ausgelöst

1. Erstellen einer neuen API-ausgelösten Kampagne
2. Wählen Sie die Kanaloberfläche aus und verknüpfen Sie den Inhalt der erstellten Nachricht
3. Konfigurieren von kontextuellen Personalisierungs-Token für Daten, die in der API-Trigger-Payload übergeben werden
4. Kampagne überprüfen und aktivieren
5. Notieren Sie die Kampagnen-ID zur Verwendung in der API-Trigger-Integration des externen Systems
6. Das aufrufende System sendet Trigger-Anfragen mit Empfängerprofilen und kontextuellen Daten an den Campaign-Endpunkt

#### Dokumentation zu Experience League

- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [API-ausgelöste Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Zielgruppen-Journey lesen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 5: Reporting und Leistung analysieren

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse

In dieser Phase werden Versandmetriken während der Ausführung über Live-Berichte überwacht und die Kampagnenleistung nach Abschluss über historische Berichte analysiert. Konfigurieren Sie optional die CJA-Integration für eine tiefer gehende kanalübergreifende Analyse.

#### Entscheidung: Berichtsmethode

Welches Reporting ist für diese Kampagne erforderlich?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native AJO-Berichte | Standardmäßige Versand- und Interaktionsmetriken sind ausreichend (gesendet, zugestellt, Öffnungen, Klicks, Bounces) | Keine zusätzliche Konfiguration; Berichte sind in die Benutzeroberfläche von Campaign/Journey integriert |
| Native Berichte in AJO + CJA-Analyse | Eine kanalübergreifende Wirkungsanalyse, Attributionsmodellierung oder funnel-Analyse ist über die Versandmetriken hinaus erforderlich | Erfordert eine CJA-Verbindung und eine Datenansicht, die mit AJO-Datensätzen verknüpft sind; bietet tiefere Analysefunktionen |
| Programmatische Berichterstellung für CJA | Für Stakeholder ist die Bereitstellung automatisierter Dashboards oder terminierter Berichte erforderlich | Erfordert die Integration der CJA Reporting-API; nützlich für Executive-Dashboards und wiederkehrende Leistungszusammenfassungen |

#### Entscheidung: Konversionsverfolgung

Wie wird der Kampagnenerfolg über die Versand- und Interaktionsmetriken hinaus gemessen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Kein Konversions-Tracking | Kampagnenziel ist die Sensibilisierung oder Interaktion (Öffnungen, Klicks) ohne spezifische nachgelagerte Aktion | Einfach; keine zusätzliche Ereignisverfolgung erforderlich |
| Webkonversionsverfolgung | Campaign CTA verweist auf eine Web-Seite, auf der Konversionsereignisse (Kauf, Registrierung, Formularübermittlung) verfolgt werden | Erfordert Tagging mit Web SDK oder Analytics auf der Zielseite. Ereignisse müssen in AEP-Datensätzen erfasst werden |
| Benutzerdefiniertes Konversionsereignis | Der Kampagnenerfolg wird anhand eines geschäftsspezifischen Ereignisses gemessen, das nicht im Internet erfasst wird (z. B. Kauf in einem Geschäft, Interaktion mit einem Callcenter) | Erfordert, dass das benutzerspezifische Ereignis in AEP aufgenommen und in Reporting-Datensätze aufgenommen wird |

#### Navigation in der Benutzeroberfläche

- Live-Berichte: Kampagnen > Kampagne auswählen > Live-Bericht (oder Journey > Journey auswählen > Live-Bericht)
- Verlaufsberichte: Kampagnen > Kampagne auswählen > Alle Zeitberichte (oder Journey > Journey auswählen > Alle Zeitberichte)

#### Wichtige Konfigurationsdetails

- Zugreifen auf Live-Berichte während der Kampagnenausführung zur Überwachung von Versand und Interaktion in Echtzeit
- Überprüfen der Schlüsselmetriken: gesendet, zugestellt, Bounces, Öffnungen, Klicks, Abmeldungen (E-Mail); gesendet, zugestellt, Klicks, Fehler (SMS); gesendet, zugestellt, Öffnungen, Aktionen (Push)
- Greifen Sie nach Abschluss der Kampagne auf historische Berichte (alle Zeiten) zu, um eine umfassende Analyse zu erhalten
- Analysieren Sie den Versand funnel: Zielgruppe > Gesendet > Zugestellt > Öffnungen > Klicks
- Überprüfen der Fehler- und Ausschlussgründe, um Versandprobleme zu identifizieren
- Wenn das Inhaltsexperiment aktiviert war, überprüfen Sie die Ergebnisse des Experiments und warten Sie auf statistische Konfidenz, bevor Sie einen Gewinner bestimmen
- Überprüfen Sie für die CJA-Integration, ob die AJO-Datenansicht die entsprechenden AJO-Datensätze enthält (Nachrichten-Feedback-Ereignisdatensatz, E-Mail-Tracking-Erlebnisereignis-Datensatz)

#### Dokumentation zu Experience League

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Überlegungen bei der Implementierung

In diesem Abschnitt werden Leitplanken, allgemeine Fallstricke, Best Practices und Entscheidungen zu Kompromissen behandelt.

### Leitplanken und Beschränkungen

- Maximal 500 aktive Live-Kampagnen pro Sandbox - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximal 10 Kanaloberflächen pro Kanaltyp pro Sandbox
- API-ausgelöste Kampagnen unterstützen bis zu 20 Profilempfänger pro Trigger-Anfrage
- Kampagnen können nicht mehr bearbeitet werden, sobald sie aktiviert wurden - stattdessen duplizieren und ändern
- Live-Berichte werden alle 60 Sekunden aktualisiert und zeigen die Daten der letzten 24 Stunden an
- Es kann bis zu 2 Stunden dauern, bis historische Berichte nach Abschluss der Kampagne vollständig ausgefüllt sind
- Maximal 10 Behandlungen (Varianten) pro Inhaltsexperiment
- Maximal 10 Begrenzungskonfigurationen pro Sandbox
- Maximal 30 Inhaltsfragmente pro Nachricht
- Für eine optimale Zustellbarkeit wird eine maximale E-Mail-Größe von 100 KB empfohlen
- IP-Aufwärmpläne sollten das Volumen für neue IPs schrittweise über 2-4 Wochen steigern
- Unterdrückungslisteneinträge werden für einen konfigurierbaren Zeitraum beibehalten (standardmäßig 14 Tage für Softbounces)

### Häufige Fehler

- **Senden vor Abschluss der IP-Aufwärmung:** neue IP-Adressen, die große Mengen sofort senden, werden von den ISPs gekennzeichnet, was zu schlechter Zustellbarkeit und potenzieller Blockierungsauflistung führt. Schließen Sie immer einen IP-Aufwärmplan ab, bevor die Produktion neue IPs sendet.

- **Personalisierung nicht über mehrere Profile hinweg testen:** Personalization-Token, die für ein Testprofil funktionieren, können für andere fehlschlagen, wenn der referenzierte XDM-Pfad nicht vorhanden ist oder für einige Profile null ist. Zeigen Sie immer eine Vorschau mit mehreren Testprofilen an, die unterschiedliche Datenvollständigkeitsstufen darstellen.

- **Überprüfung der Unterdrückungsliste überspringen:** Veraltete Unterdrückungslisteneinträge können den Versand an gültige Adressen blockieren, während fehlende Einträge zu einem Versand an ungültige Adressen führen können, die Bounces verursachen. Überprüfen und bereinigen Sie die Unterdrückungsliste vor wichtigen Kampagnen.

- **Ignorieren der Frequenzlimitierung für Werbekampagnen:** Senden einer Werbekampagne ohne Frequenzlimitierung, während andere Kampagnen ebenfalls aktiv sind, kann dazu führen, dass Profile innerhalb eines kurzen Zeitraums mehrere Nachrichten erhalten, was zu Abmeldungen und Spam-Beschwerden führen kann.

- **Kampagnen planen, ohne die Zielgruppen-Population zu verifizieren:** Aktivieren einer Kampagne vor der Bestätigung, dass die ausgewertete Zielgruppen-Population ungleich null ist, führt dies zu null gesendeten Nachrichten. Überprüfen Sie die Zielgruppengröße immer vor der Aktivierung.

- **Verwenden der Batch-Auswertung für zielgruppenausgelöste Journey** Wenn die Journey den Eintrag „Zielgruppe lesen“ mit der Batch-Auswertung verwendet, treten Profile nicht nahezu in Echtzeit ein. Verwenden Sie die Streaming-Auswertung für die Zielgruppe, wenn ein nahezu in Echtzeit erfolgender Journey-Eintrag erforderlich ist.

- **Keine Konfiguration der Einverständnisdurchsetzung:** Senden von Nachrichten an Profile ohne gültige Marketing-Einwilligung verletzt Vorschriften und schädigt die Reputation der Zustellbarkeit. Stellen Sie sicher, dass Einverständnisfelder auf der Ebene der Kanaloberfläche ausgefüllt und durchgesetzt werden.

### Best Practices

- Beginnen Sie mit Option A (Geplante Kampagne) für einfache Broadcast-Anwendungsfälle und wechseln Sie nur dann zu Option B (Zielgruppen-ausgelöstes Journey), wenn die Vorversandlogik oder ein verhaltensgesteuertes Timing erforderlich ist
- Geben Sie für maximale Compliance immer sowohl einen 1-Klick-Listenabmelde-Header als auch einen Abmelde-Link in den E-Mail-Textkörper ein
- Erstellen Sie wiederverwendbare Inhaltsfragmente für Kopfzeilen, Fußzeilen und Haftungsausschlüsse, um die Konsistenz über Kampagnen hinweg sicherzustellen
- Legen Sie vor der Aktivierung von Kampagnen Regeln zur Frequenzlimitierung fest, um zu verhindern, dass in allen gleichzeitigen Sendungen übermäßig viele Nachrichten versendet werden
- Verwenden von Inhaltsexperimenten zur Optimierung von Betreffzeilen und CTAs, beginnend mit A/B-Tests, bevor mit multivariaten Experimenten fortgefahren wird
- Weisen Sie allen aktiven Kampagnen Prioritätswerte zu, um eine konsistente Konfliktbewältigung zu gewährleisten.
- Planen Sie die Batch-Zielgruppenauswertung, damit sie vor der Kampagnenausführungszeit abgeschlossen wird, um neue Zielgruppendaten sicherzustellen
- Testversand-E-Mails senden und vor der Aktivierung die E-Mail-Rendering-Funktion verwenden, um zu überprüfen, ob die Nachricht auf allen E-Mail-Clients korrekt angezeigt wird
- Überwachen Sie den Live-Bericht sofort nach der Kampagnenaktivierung, um Versandprobleme frühzeitig zu erkennen
- Archivieren Sie Kampagnenkonfigurationen und Experimentergebnisse für zukünftige Referenzen und kontinuierliche Optimierung.

### Entscheidungen über Kompromisse

Die folgenden Kompromisse sollten bei der Auswahl der Implementierung bewertet werden.

#### Einfachheit vs. Flexibilität

Geplante Kampagnen (Option A) bieten die einfachste Konfiguration, aber keine Vorversandlogik. Zielgruppengesteuerte Journey (Option B) bieten eine Vorversandlogik, erhöhen jedoch die Konfigurationskomplexität.

- **Option A bevorzugt:** Geschwindigkeit der Markteinführung, einfache Bedienung, Self-Service für Marketing-Experten
- **Option B bevorzugt:** Verhaltenszielgruppenbestimmung, bedingte Unterdrückung, Erweiterbarkeit auf mehrstufige Journeys
- **Empfehlung:** Beginnen Sie mit Option A für einfache Sendungen. Nur dann auf Option B verschieben, wenn der Anwendungsfall vor dem Versand tatsächlich eine Logik des Wartens, der Bedingung oder der Verzweigung erfordert. Vermeiden Sie die Verwendung der Journey-Arbeitsfläche für einfache Batch-Sendungen, die nicht von Orchestrierungsfunktionen profitieren.

#### Audience-Aktualität im Vergleich zu Auswertungskosten

Die Streaming-Auswertung bietet nahezu in Echtzeit Aktualisierungen für Zielgruppen, unterliegt jedoch Einschränkungen bei Segmentregeln. Die Batch-Auswertung unterstützt alle Segmentregelfunktionen, wird jedoch nach einem täglichen Zeitplan ausgewertet.

- **Streaming-Vorteile:** Zeitnähe, verhaltensgesteuerte Genauigkeit, zielgruppengesteuerter Journey-Eintrag
- **Batch-Vorteile:** Komplexe Zielgruppenlogik, große Populationen, geringerer Evaluierungsaufwand
- **Empfehlung** Verwenden Sie die Batch-Auswertung für geplante Kampagnen (Option A), wenn die tägliche Frische ausreicht. Verwenden Sie die Streaming-Auswertung für durch eine Zielgruppe ausgelöste Journey (Option B), bei denen Profile so eingeben müssen, wie sie qualifiziert sind. Wenn der Regelausdruck für Zielgruppensegmente nicht für Streaming geeignet ist, strukturieren Sie die Regeln neu oder akzeptieren Sie Latenzen auf Batch-Ebene.

#### Personalization-Tiefe im Vergleich zur Authoring-Komplexität

Eine tiefergehende Personalisierung (bedingte Inhaltsbausteine, dynamische Abschnitte) verbessert die Interaktion, erhöht jedoch den Autoren- und Testaufwand.

- **Tiefe Personalisierungsvorteile:** Höhere Interaktionsraten, ein relevanteres Kundenerlebnis, bessere Konversion
- **Einfache Personalisierung begünstigt:** Schnellere Startzeit, geringerer Testaufwand, geringeres Risiko von Rendering-Fehlern
- **Empfehlung** Beginnen Sie mit der grundlegenden Personalisierung (Vorname, relevante Produktkategorie) und fügen Sie die Ebene in bedingte Inhaltsbausteine ein, die auf gemessenen Leistungssteigerungen basieren. Testen Sie vor der Aktivierung immer alle Inhaltsvarianten über mehrere Testprofile hinweg.

#### Häufigkeitskontrolle vs. Reichweite der Nachricht

Eine strikte Frequenzlimitierung verhindert Übernachrichten, kann jedoch den Kampagnenversand an Profile unterdrücken, die kürzlich andere Nachrichten erhalten haben.

- **Strenge Begrenzungsvorteile:** Kundenerlebnisqualität, niedrigere Abmelderaten, Markenreputation
- **Lockere Begrenzungsfavoriten:** Maximale Reichweite von Nachrichten, höhere Gesamtimpressionen, Kampagnenabdeckung
- **Empfehlung:** Sie die Frequenzlimitierung für Marketing-Kampagnen immer an. Legen Sie kanalspezifische Begrenzungen fest (z. B. 3-5 E-Mails pro Woche, 1-2 SMS pro Woche). Nur wirklich zeitkritische oder Transaktionsnachrichten von Begrenzungsregeln ausnehmen.

## Verwandte Dokumentation

Dieser Abschnitt enthält Links zu [!DNL Experience League] Dokumentation, die nach Themen geordnet ist.

### Kampagnen

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API-ausgelöste Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Journeys

- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Zielgruppen-Journey lesen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Verwenden von Inhaltskomponenten von Email Designer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Importieren oder Codieren von E-Mail-Inhalt](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Content-Management

- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [E-Mail-Testsendungen durchführen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [Email Rendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Inhaltsexperiment

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische Berechnungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Häufigkeits- und Konfliktmanagement

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Erste Schritte mit Konflikt- und Prioritätsverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience-Komposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Berichterstellung

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Datenmodellierung und Identität

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorials und Erste Schritte

- [Erste Schritte mit Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Erstellen Ihrer ersten Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erstellen Ihrer ersten Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
