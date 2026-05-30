---
title: Offer Decisioning
description: Erfahren Sie, wie Sie mit zentralisierter Entscheidungslogik das nächstbeste Angebot oder den nächstbesten Inhalt für ein Profil kanalübergreifend auswählen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 5%

---

# Offer Decisioning

In diesem Handbuch wird das Anwendungsfallmuster für Offer Decisioning beschrieben, das mithilfe von [!DNL Adobe Journey Optimizer] (AJO) Decisioning und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) eine zentralisierte Angebotsauswahllogik implementiert, die kanalübergreifend das nächstbeste Angebot für jedes Kundenprofil bestimmt. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Das Muster entkoppelt die Entscheidung, was angezeigt werden soll, von der Kanallogik, wo es angezeigt werden soll, und ermöglicht eine konsistente, optimierte Angebotsauswahl über E-Mail, Web, Mobile App und jeden anderen Touchpoint. AJO Decisioning verwaltet den gesamten Angebotslebenszyklus: die Angebotserstellung und -katalogverwaltung, Eignungsregeln (wer die einzelnen Angebote sehen kann), Rangfolgestrategien (wie die Auswahl unter geeigneten Angeboten erfolgt), Platzierungen (wo Angebote angezeigt werden) und Entscheidungsrichtlinien (die alles miteinander verbinden).

## Anwendungsfallmuster

In diesem Abschnitt werden der Ausführungsplan und die Musterdefinition für Offer Decisioning beschrieben.

**Offer Decisioning**

Verwenden Sie eine zentralisierte Entscheidungslogik, um kanalübergreifend das nächstbeste Angebot oder den nächstbesten Inhalt für ein Profil auszuwählen.

**Ausführungsplan:** Zielgruppenbewertung > Angebotseignung > Rangfolgestrategie > Entscheidungsausführung > Versand > Reporting

## Anwendungsfall - Übersicht

Unternehmen müssen häufig jedem Kunden zum Zeitpunkt der Interaktion das relevanteste Angebot, die relevanteste Promotion oder den relevantesten Anreiz unterbreiten. Unabhängig davon, ob die Interaktion in einer E-Mail-Kampagne, auf einer Website-Homepage, in einer Mobile App oder an einem Entscheidungspunkt innerhalb einer mehrstufigen Journey stattfindet, ist die Herausforderung dieselbe: Wählen Sie aus einem Katalog verfügbarer Optionen das optimale Angebot aus, je nachdem, wer der Kunde ist, für was er sich qualifiziert und welches Angebot am ehesten das gewünschte Ergebnis erzielt.

Offer Decisioning löst dieses Problem, indem es die gesamte Angebotsauswahllogik in der Entscheidungs-Management-Engine von AJO zentralisiert. Anstatt die Angebotszuweisungen in einzelne Kampagnen oder Kanäle zu hartcodieren, wertet die Entscheidungs-Engine die Attribute jedes Profils, die Zielgruppenzugehörigkeit und kontextuelle Signale aus, um das beste Angebot in Echtzeit zu ermitteln. Durch diese Zentralisierung wird sichergestellt, dass derselbe Kunde konsistente, optimierte Angebote erhält, unabhängig davon, über welchen Kanal er interagiert.

Dieses Muster unterscheidet sich vom Umfang der Web-/App-Personalisierung bekannter Besucher - die Angebotsentscheidung ist kanalunabhängig und zentralisiert, während die Personalisierung bekannter Besucher sich auf die Personalisierung digitaler Oberflächen konzentriert. Sie unterscheidet sich von Verhaltensempfehlungen im Katalogmodell - verwenden Sie Offer Decisioning , wenn der geeignete Elementsatz durch Geschäftsregeln, Eignungsbegrenzungen oder regulatorische Anforderungen (Promotions, Finanzprodukte, Incentives) geregelt ist. Verwenden Sie eine Verhaltensempfehlung, wenn der Elementsatz groß ist und sich ständig ändert und die Auswahl durch Ähnlichkeits- oder Affinitätssignale (Produktkataloge, Inhaltsbibliotheken) gesteuert wird.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.
**KPIs:** Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT)

**[Umsatz durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.
**KPIs:** Upsell/Crosssell %, Inkrementeller Umsatz, Kundenlebenszeitwert

**[Steigerung der Kundentreue und des Lebenszeitwerts](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Vertiefung der Kundenbeziehungen und Maximierung des langfristigen Nutzens durch Treueprogramme, Prämien und personalisierte Interaktion.
**KPIs:** Kundenlebenszeitwert, Kundenbindung, Upsell/Crosssell %

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie Offer Decisioning in der Praxis angewendet werden kann.

- Nächstbestes Angebot in E-Mail-Kampagnen — Wählen Sie die zum Sendezeitpunkt relevanteste Promotion pro Empfänger aus.
- Werbebanner in Echtzeit auf Website - Decisioning wählt das Angebot beim Laden der Seite auf der Grundlage des Besucherprofils aus
- Personalisierte In-App-Karte mit dem besten Anreiz für die Lebenszyklusphase des Benutzers
- Kanalübergreifende Angebotskonsistenz - Dieselbe Entscheidungslogik dient E-Mail, Web und Push, damit der Kunde ein einheitliches Angebotserlebnis sieht
- Dynamische Gutschein- oder Rabattauswahl auf Basis der Kundenwertstufe (z. B. erhalten hochwertige Kunden ein Premium-Angebot)
- Auswahl von Angeboten für Produktaktualisierungen oder Upsell-Angebote auf Basis der aktuellen Abonnementebene
- Personalisierung des Treueprämienangebots basierend auf der Stufe und dem Aktivitätsverlauf

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität einer Offer-Decisioning-Implementierung gemessen werden.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Annahmerate | Prozentsatz der bereitgestellten Angebote, die zu einem Klick, einer Einlösung oder einer Konversion führen | Klicks auf Angebote oder Einlösungen / Insgesamt bereitgestellte Angebote |
| Verteilung der Angebotsauswahl | Anteil jedes ausgewählten Angebots an allen Entscheidungen | Anzahl pro Angebot/Gesamtzahl der gerenderten Entscheidungen |
| Fallback-Rate | Prozentsatz der Entscheidungen, bei denen kein personalisiertes Angebot qualifiziert und das Fallback bereitgestellt wurde | Fallback-Impressions/Entscheidungen insgesamt |
| Konversionsrate | Prozentsatz der Angebotsempfänger, die die gewünschte Aktion abgeschlossen haben (Kauf, Anmeldung, Einlösung) | Konversionen/Angebots-Impressionen |
| Inkrementeller Umsatz | Umsatz, der entscheidungsausgewählten Angeboten gegenüber einer Kontrollgruppe oder einem Fallback zugeschrieben wird | Umsätze durch personalisierte Angebote - Umsätze durch Fallback/Kontrolle |
| Kanalübergreifende Konsistenzbewertung | Prozentsatz der Profile, die dasselbe Angebot über mehrere Kanäle innerhalb eines definierten Fensters erhalten | Konsistente Angebote/Gesamtzahl der Multi-Channel-Impressions |
| Klickrate des Angebots | Prozentsatz der Angebots-Impressionen, die zu einem Klick führen | Angebotsklicks/Angebots-Impressionen |

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Entscheidungs-Management-Engine für die Angebotserstellung, Eignungsregeln, Ranking-Strategien, Platzierungen und Entscheidungsrichtlinien; Kanalkonfiguration und Nachrichtenbearbeitung für den Versand von Angeboten; Kampagnen und Journey-Ausführung
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung für Angebotseignungssegmente; Profildaten und berechnete Attribute, die in Eignung und Ranking verwendet werden
- **[!DNL Adobe Experience Platform] (AEP)** - Einheitlicher Profilspeicher, Identitätsauflösung und Data Foundation, die sowohl AJO als auch RT-CDP unterstützen

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den Komponenten, die in diesem Anwendungsfallmuster verwendet werden.

### Entscheidungs-Management

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Erstellen von Entscheidungsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Erstellen von Sammlungsqualifizierern](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Angebotsversand

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Unterbreiten von Angeboten mithilfe der Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Kampagnen und Journey

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Inhaltsexperiment

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profil und Identität

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Datenmodellierung und -erfassung

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Reporting und Analysen

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Data Governance und Lebenszyklus

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutorials

- [Entscheidungs-Management-API - Erste Schritte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
