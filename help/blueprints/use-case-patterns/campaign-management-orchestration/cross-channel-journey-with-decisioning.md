---
title: Cross-Channel-Journey mit Decisioning
description: Erfahren Sie, wie Sie eine mehrstufige Journey mit Echtzeit-Entscheidungsfindung orchestrieren können, um optimale Kanäle, Inhalte oder Angebote auszuwählen.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 5%

---

# Cross-Channel-Journey mit Decisioning

In diesem Handbuch wird das Anwendungsfallmuster „Cross-Channel Journey with Decisioning“ beschrieben, das mithilfe von [!DNL Adobe Journey Optimizer] und [!DNL Adobe Real-Time Customer Data Platform] mehrstufige Multi-Channel-Journeys orchestriert, die Echtzeit-Entscheidungsfindung auf einem oder mehreren Journey-Knoten beinhalten. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Cross-Channel-Journey mit Decisioning ist das komplexeste Kampagnenorchestrierungsmuster im [!DNL Adobe Experience Platform]. Es erweitert mehrstufig orchestrierte Journey durch Einbeziehung der Echtzeit-Entscheidungsfindung - mithilfe von [!DNL AJO] Decisioning, um den aktuellen Kontext eines Profils zu bewerten und an einem oder mehreren Entscheidungspunkten auf der Journey-Arbeitsfläche dynamisch den optimalen Kanal, Inhalt oder das Angebot auszuwählen.

## Anwendungsfallmuster

**Cross-Channel-Journey mit Decisioning**

Orchestrieren Sie eine mehrstufige Multi-Channel-Journey, die Echtzeit-Entscheidungsfindung an einem oder mehreren Knoten beinhaltet, um den optimalen Kanal, Inhalt oder Angebot auszuwählen.

**Ausführungsplan:** Zielgruppenbewertung > Journey-Ausführung > Entscheidungsknoten > Kanalauswahl > Nachrichtenversand > Berichte

## Anwendungsfall - Übersicht

Unternehmen müssen zunehmend adaptive, personalisierte Kunden-Journey bereitstellen, die dynamisch auf den Echtzeit-Kontext jedes Einzelnen reagieren, anstatt eine feste, vorab festgelegte Abfolge einzuhalten. Der bevorzugte Kanal eines Kunden, sein Interaktionsverlauf, seine Treuestufe, sein prognostizierter Lebensdauerwert und seine aktuellen Produktinteressen fließen in die Frage ein, welche Aktion an jedem Touchpoint die nächstbeste sein sollte.

Das Cross-Channel-Journey mit Entscheidungsfindung erfüllt diese Anforderungen, indem zwei leistungsstarke [!DNL AJO] kombiniert werden: Journey-Orchestrierung (die den mehrstufigen Fluss, die Zeitplanung, die Bedingungen und die Kanalbereitstellung verwaltet) und Entscheidungsfindung (die Eignungsregeln bewertet, Rangfolgestrategien anwendet und an jedem Entscheidungspunkt die optimale Angebots- oder Inhaltsvariante auswählt).

Dieses Muster ist geeignet, wenn:

- Die Journey muss sich dynamisch an den Echtzeitstatus jedes Profils anpassen, anstatt einem festen Kanal oder einer festen Inhaltssequenz zu folgen
- Mehrere Angebote, Inhaltsvarianten oder Kanäle sind auf einem oder mehreren Journey-Knoten möglich. Die beste Option sollte auf der Grundlage des Profilkontexts ausgewählt werden
- Um die Angebotsauswahl auf der gesamten Journey zu optimieren, ist ein KI-unterstütztes oder formularbasiertes Ranking erforderlich
- Das Unternehmen möchte die Kanalauswahllogik und das Angebotsmanagement in einem zentralisierten Entscheidungs-Framework konsolidieren, anstatt eine komplexe Verzweigungslogik beizubehalten

Die Zielgruppe umfasst Marketing-Fachleute für die Verwaltung von Lebenszyklusprogrammen, Treue-Journey, Win-Back-Sequenzen und Onboarding-Flüssen, bei denen eine skalierbare Personalisierung an jedem Touchpoint eine automatisierte Entscheidungsfindung erfordert.

>[!NOTE]
>Wenn für Ihren Journey keine dynamische Entscheidungsfindung an einzelnen Knoten erforderlich ist - z. B. ein Nurture- oder Onboarding-Programm mit fester Sequenz -, lesen Sie [Mehrstufiges orchestriertes Journey](multi-step-orchestrated-journey.md). Dieses Muster ist einfacher zu konfigurieren und erfordert keine AJO-Entscheidungsfindung.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.
**KPIs:** Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT)

**[Steigerung der Kundentreue und des Lebenszeitwerts](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Vertiefung der Kundenbeziehungen und Maximierung des langfristigen Nutzens durch Treueprogramme, Prämien und personalisierte Interaktion.
**KPIs:** Kundenlebenszeitwert, Kundenbindung, Upsell/Crosssell %

**[Verbesserung der Kundenbindung](../../business-objectives/customer-experience/improve-customer-retention.md)**
Halten Sie bestehende Kundinnen und Kunden durch wertorientierte Erlebnisse und kontinuierliche Pflege von Beziehungen in Kontakt und erneuern Sie diese.
**KPIs:**, Kundenlebenszeitwert, Interaktion

**[Umsatz durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.
**KPIs:** Upsell/Crosssell %, Inkrementeller Umsatz, Kundenlebenszeitwert

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie Cross-Channel-Journey mit Decisioning in der Praxis angewendet werden kann.

- **Adaptives Win-Back-Journey** - Ein mehrstufiges Journey, bei dem Decisioning den Kanal (E-Mail, Push oder SMS) auf der Grundlage des Interaktionsverlaufs jedes Profils auswählt und dynamisch das beste Incentive-Angebot auf der Grundlage des prognostizierten Lebenszeitwerts auswählt
- **Next-best-action-Lifecycle-Journey** - Die Entscheidungsfindung bestimmt, was in jeder Phase des Kundenlebenszyklus kommuniziert werden soll. Dabei wird zwischen Onboarding-Inhalten, Crosssell-Angeboten, Treueprämien oder Kundenbindungsanreizen ausgewählt
- **Personalisiertes Onboarding mit dynamischer Inhaltsauswahl** - Onboarding-Journey für neue Kunden, bei der jeder Touchpoint mithilfe von Entscheidungsfindung die relevantesten Produktschulungsinhalte, Tipps oder Aktivierungsangebote auswählt
- **Cross-Channel-Treueprogramm-Journey mit personalisierten Prämien** - Mitglieder des Treueprogramms entwickeln eine Journey, auf der Decisioning personalisierte Prämienangebote basierend auf der Stufe, dem Kaufverlauf und der Kategorieaffinität auswählt
- **Dynamische Rückgewinnung mit Kanal- und Anreizoptimierung** — Ruhende Rückgewinnung von Kunden, wobei sowohl der Outreach-Kanal als auch der Anreiz dynamisch ausgewählt werden, um die Reaktionswahrscheinlichkeit zu maximieren
- **Customer Lifecycle Nurture mit KI-bewerteten Inhaltsempfehlungen** - Fortlaufendes Nurture-Journey, bei dem KI-bewertete Entscheidungen die relevantesten Inhalte oder Produktempfehlungen an jedem Touchpoint auswählen

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die den vollständigen Journey abschließen | Journey-Bericht: abgeschlossen/eingegeben |
| Annahmerate | Prozentsatz der entscheidungsausgewählten Angebote, mit denen interagiert wird (angeklickt, eingelöst) | Entscheidungsbericht: Angebotsklicks/Angebots-Impressionen |
| Kanalinteraktionsrate | Öffnungs- und Klickraten für jeden auf der Journey verwendeten Kanal | Versandmetriken pro Kanal im Journey-Bericht |
| Konversionsrate | Prozentualer Anteil der Journey-Teilnehmer, die die Zielkonversionsaktion abgeschlossen haben | Journey-Exitevent-Tracking oder CJA funnel Analysis |
| Fallback-Angebotsrate | Prozentsatz der Entscheidungsanfragen, die das Fallback-Angebot anstelle eines personalisierten Angebots zurückgeben | Entscheidungsbericht: Fallback-Auswahl/Gesamtauswahl |
| Auswirkungen auf den Kundenlebenszeitwert | Veränderung der CLV für Journey-Teilnehmer vs. Kontrollgruppe | CJA-Kohortenanalyse mit Holdout-Vergleich |
| Crosssell-/Upsell-Umsatz | Inkrementeller Umsatz, der den durch die Entscheidungsfindung ausgewählten Angeboten zugeordnet wird | CJA-Attributionsanalyse zu angebotsgesteuerten Konversionen |
| Effektivität der Entscheidungsrangliste | Leistungsunterschied zwischen KI-bewerteten Angeboten und zufälliger/prioritätsbasierter Auswahl | A/B-Experiment zum Vergleich von Rangfolgestrategien |

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** - Journey-Orchestrierung (mehrstufiges Canvas-Design, Einstiegsbedingungen, Wartezeiten, Bedingungen, Ausstiegskriterien), Nachrichten-Authoring kanalübergreifend, Kanaloberflächenkonfiguration, Konflikt- und Prioritätsverwaltung
- **[!DNL Adobe Journey Optimizer]Decisioning** - Verwaltung von Angeboten und Inhaltselementen, Eignungsregeln, Rangfolgestrategien (Priorität, Formel, KI), Entscheidungsrichtlinien, Platzierungen, Fallback-Angebote
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** - Zielgruppenbewertung für Journey-Eintritts- und Angebotseignungssegmente, Profilanreicherung mit berechneten Attributen und Tendenzwerten, Einverständnis- und Governance-Durchsetzung
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Echtzeit-Kundenprofilspeicher, Identity Service für Cross-Channel-Auflösung, Datenmodellierung und Aufnahmeinfrastruktur

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

### Journey-Orchestrierung

- [Erste Schritte mit Journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Konflikt-, Prioritäts- und Frequenzverwaltung

- [Übersicht über Konflikt- und Prioritätsmanagement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience-Komposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Reporting und Analysen

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profil und Identität

- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
