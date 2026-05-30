---
title: Web-/App-Personalization für bekannte Besucher
description: Erfahren Sie, wie Sie auf der Grundlage von Echtzeit-Profil- und Segmentzugehörigkeit personalisierte Inhalte, Angebote oder Promotions für identifizierte Besucher bereitstellen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 4%

---

# Web-/App-Personalisierung für bekannte Besucher

In diesem Handbuch wird das Anwendungsfallmuster für die Web-/App-Personalisierung beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) verwendet werden, um identifizierten Besuchern personalisierte Inhalte über digitale Oberflächen hinweg bereitzustellen. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Die Web-/App-Personalisierung bekannter Besucher ist das primäre Personalisierungsmuster für authentifizierte digitale Erlebnisse. Im Gegensatz zur anonymen Besucherpersonalisierung, die ausschließlich auf Verhaltenssignalen in der Sitzung beruht, nutzt dieses Muster das gesamte einheitliche Profil: historische Verhaltensdaten, Segmentzugehörigkeit, Treuestufe, Kaufverlauf, Lebenszyklusstadium, berechnete Attribute und Tendenzwerte. Es unterstützt die Personalisierung auf allen Web-Seiten (über den AJO-Web-Kanal), in mobilen In-App-Nachrichten und Inhaltskarten.

## Anwendungsfallmuster

In diesem Abschnitt werden das Kernmuster und der Ausführungsplan beschrieben.

**Web-/App-Personalisierung für bekannte Besucher**

Stellen Sie einem identifizierten Besucher auf der Grundlage von Echtzeit-Profil und Segmentzugehörigkeit personalisierte Inhalte, Angebote oder Angebote auf Web-, Mobile-In-App- und Inhaltskartenoberflächen bereit.

**Ausführungsplan:** Zielgruppenbewertung > Personalization Decisioning > Oberflächen-/Kanalkonfiguration > Inhaltsbereitstellung > Impression-Tracking > Berichterstellung

## Anwendungsfall - Übersicht

Unternehmen mit authentifizierten digitalen Eigenschaften - E-Commerce-Websites, Bankportale, Abonnement-Services, Treueprogramme, mobile Apps - müssen personalisierte Erlebnisse bereitstellen, die die Beziehung jedes Kunden zur Marke widerspiegeln. Wenn sich ein Besucher anmeldet oder durch Identitätsauflösung erkannt wird, kann die Plattform auf sein gesamtes Profil zugreifen und Inhalte bereitstellen, die auf seine spezifischen Attribute, Verhaltensweisen und Vorlieben zugeschnitten sind.

Dieses Muster behandelt das Szenario, in dem ein identifizierter Besucher über eine Web-Eigenschaft ankommt oder eine Mobile App öffnet, und das System muss den optimalen Inhalt, das optimale Angebot oder die optimale Promotion ermitteln, die basierend auf Echtzeit-Profildaten und der Zielgruppenzugehörigkeit angezeigt werden soll. Die Personalisierungsentscheidung findet am Edge in Millisekunden statt und ermöglicht die Bereitstellung von Inhalten in Subsekunden ohne merkliche Latenz.

Das Muster unterstützt sowohl deterministische Personalisierung (bei der bestimmte Inhalte bestimmten Zielgruppensegmenten zugeordnet sind) als auch dynamische Entscheidungsfindung (bei der AJO Decisioning Eignungsregeln und Rangfolgestrategien bewertet, um den optimalen Inhalt pro Profil auszuwählen). Es umfasst mehrere digitale Oberflächen - Web-Seiten, mobile In-App-Nachrichten und Inhaltskarten - und ermöglicht so eine konsistente Personalisierung auf allen digitalen Journey-Seiten des Kunden.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Bereitstellen personalisierter Kundenerlebnisse

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an. Weitere Informationen finden Sie unter [Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

**KPIs:** Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT)

### Website-Interaktion steigern

Verbesserung der Besuchszeit auf der Site, der Seiten pro Sitzung und der Interaktion mit Web-Inhalten durch relevante Erlebnisse. Weitere Informationen finden Sie unter [Website-Interaktion &#x200B;](../../business-objectives/acquisition-growth/increase-website-engagement.md).

**KPIs:** Besuchszeit pro Seite (Web), Interaktion, Konversionsraten

### Erhöhen der Interaktion mit Mobile Apps

Fördern Sie die tägliche aktive Nutzung, die Aktivierung von Funktionen und In-App-Konversionen durch personalisierte In-App-Erlebnisse.

**KPIs:** Interaktion, Kundenbindung, Konversionsraten

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie häufige taktische Implementierungen dieses Musters:

- Startseiten-Personalisierung nach Treuestufe oder Lebenszyklusstufe - Zeigen Sie verschiedene Hero-Banner an, je nachdem, ob der Kunde neu, aktiv, gefährdet oder VIP ist
- Produktempfehlungskarussell basierend auf dem Kaufverlauf - zeigt relevante Produktvorschläge basierend auf früheren Kaufdaten und Produktaffinitätswerten auf
- Personalisiertes Werbebanner nach Kundensegment - zeigt verschiedene Angebote für hochwertige, risikobehaftete und neue Kundensegmente an.
- In-App-Nachricht für mobile Benutzer basierend auf der Aktivierung von Funktionen - führt Benutzer zu selten genutzten Funktionen basierend auf ihren Nutzungsmustern
- Inhaltskarte mit personalisiertem Angebot im Konto-Dashboard - beständige, ausgeschlossene Angebote, die auf das Kundenprofil zugeschnitten sind
- Personalisierte Preis- oder Rabattanzeige auf Basis der Kundenebene - Anzeige stufenspezifischer Preise oder exklusiver Rabatte für Mitglieder des Treueprogramms
- Crosssell-Empfehlungs-Widget basierend auf eigenen Produkten — schlagen ergänzende Produkte oder Services basierend auf aktuellem Portfolio vor
- Personalisierte Navigation oder Inhaltsreihenfolge auf der Grundlage von Interessen - Sortieren Sie Inhaltsmodule oder Navigationselemente basierend auf demonstrierten Voreinstellungen neu

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität dieses Anwendungsfallmusters gemessen werden.

| KPI | Messansatz | Benchmark-Leitlinien |
| --- | --- | --- |
| Interaktionsrate für Personalization | Klicks und Interaktionen mit personalisierten Inhaltselementen, unterteilt durch Impressionen | Personalisierte Inhalte sollten die Standardinhalte um 20-50 % übertreffen |
| Steigerung der Konversionsrate | Konversionsrate personalisierter Erlebnisse im Vergleich zu Kontroll-/Standarderlebnissen | 10-30 % Steigerung gegenüber nicht personalisierten Erlebnissen |
| Clickthrough-Rate (CTR) | Klicks auf personalisierte CTAs, Angebote und Recommendations dividiert durch Impressionen | Monitor pro Oberfläche (Web, In-App, Inhaltskarte) und pro Segment |
| Umsatz pro Besuch | Einnahmen, die Sitzungen mit personalisierten Erlebnissen zugeordnet werden | Vergleich der Kohorten personalisierter und nicht personalisierter Besucher |
| Interaktionsrate der Inhaltskarte | Klicks auf und Abweisungen von Inhaltskarten in Bezug auf Impressions | Tracking nach Kartentyp und Zielgruppensegment |
| In-App-Nachrichteninteraktion | In-App-Nachrichteninteraktionen (CTA-Klicks, Abweisungen) in Bezug auf Impressionen | Vergleichen von Zielgruppensegmenten und Nachrichtentypen |
| Zeit auf Seite | Durchschnittliche Zeit, die auf Seiten mit personalisierten Inhalten verbracht wurde, im Vergleich zum Standard | Personalisierte Seiten sollten eine längere Verweilzeit aufweisen |
| Annahmerate | Prozentsatz der entscheidungsausgewählten Angebote, die zu einem Konversionsereignis führen | Tracking pro Angebot, pro Platzierung und pro Rangfolgestrategie |

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Web-Kanalkonfiguration, In-App-Kanalkonfiguration, Konfiguration des Inhaltskarten-Kanals, Entscheidungsfindung (Angebotsauswahl und Rangfolge), Nachrichtenbearbeitung (Erstellung personalisierter Inhalte), Kampagnenausführung, Inhaltsexperimentierung und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung (Edge, Streaming und Batch), Echtzeit-Profilsuche über Edge Network, Profilanreicherung mit berechneten Attributen und Tendenzwerten
- **[!DNL Adobe Experience Platform] (AEP)** - Profilspeicher, Identity Service, Web SDK, Mobile SDK, Datenstromkonfiguration, Edge Network-Bereitstellung

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten weitere Details zu den Technologien und Konfigurationen, auf die in diesem Handbuch verwiesen wird.

### Web-Kanal-Personalisierung

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/create-web)
- [Konfiguration des Web-Kanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### In-App- und Inhaltskarten-Kanäle

- [In-App-Kanal - Übersicht](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Voraussetzungen für In-App-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Erstellen von In-App-Nachrichten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Inhaltskarten-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Konfiguration der Inhaltskarte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Erstellen von Inhaltskarten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Entscheidungs-Management

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Erstellen von Entscheidungsregeln](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization und Inhalte

- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)

### Datenerfassung und SDK

- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/install/overview)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/de/docs/experience-platform/edge-network-server-api/overview)

### Kampagnen und Experimente

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Berechnete Attribute und Anreicherung

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/ui)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting und Analysen

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/home)

### Governance und Datenschutz

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/guardrails)
