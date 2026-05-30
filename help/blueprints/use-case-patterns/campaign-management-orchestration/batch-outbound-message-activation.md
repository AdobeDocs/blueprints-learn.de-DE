---
title: Batch-Aktivierung ausgehender Nachrichten
description: Erfahren Sie, wie Sie eine Audience auswerten und eine geplante ausgehende Nachricht in einer einzigen Batch-Ausführung versenden.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1701'
ht-degree: 4%

---

# Batch-Aktivierung ausgehender Nachrichten

In diesem Handbuch wird das Anwendungsfallmuster für die Aktivierung von Batch-ausgehenden Nachrichten beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) verwendet werden, um geplante ausgehende Nachrichten an definierte Zielgruppensegmente zu senden. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Die Aktivierung ausgehender Batch-Nachrichten ist das grundlegende Kampagnenmuster für 1:n-ausgehende Nachrichten. Es umfasst den gesamten Lebenszyklus von der Zielgruppendefinition über den Nachrichtenversand bis hin zur Leistungsanalyse.

## Anwendungsfallmuster

**Batch-Aktivierung ausgehender Nachrichten**

Bewerten Sie eine Audience und senden Sie dann eine geplante ausgehende Nachricht (E-Mail, SMS, Push) an alle qualifizierten Profile in einer einzigen Batch-Ausführung.

**Ausführungsplan:** Zielgruppenbewertung > Nachrichtenbearbeitung > Kampagnenausführung > Berichterstellung

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

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Muster zu implementieren.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Nachrichtenbearbeitung, Kanalkonfiguration, Kampagnenausführung, Journey-Orchestrierung, Inhaltsexperimente, Häufigkeitsregeln und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Zielgruppenbewertung, Einverständnis und Durchsetzung der Governance
- **[!DNL Adobe Experience Platform] (AEP)** - Profilspeicher, Identity Service, Schemata, Datensätze, Datenerfassung

## Verwandte Dokumentation

Dieser Abschnitt enthält Links zu [!DNL Experience League] Dokumentation, die nach Themen geordnet ist.

### Kampagnen

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API-ausgelöste Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Journeys

- [Erste Schritte mit Journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
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
