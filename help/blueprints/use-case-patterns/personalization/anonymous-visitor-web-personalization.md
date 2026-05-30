---
title: Web-Personalization für anonyme Besucher
description: Erfahren Sie, wie Sie nicht identifizierten Besuchern auf der Grundlage von Verhaltenssignalen während der Sitzung personalisierte Webinhalte bereitstellen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 4%

---

# Web-Personalisierung für anonyme Besucher

In diesem Handbuch wird das Anwendungsfallmuster für die Web-Personalisierung anonymer Besucher beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP) verwendet werden, um anonymen (nicht identifizierten) Besuchern personalisierte Web-Inhalte auf der Grundlage von Verhaltenssignalen während der Sitzung bereitzustellen. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Das Muster funktioniert mit begrenzten Daten - nur was in der aktuellen Sitzung beobachtet werden kann und alle anonymen Edge-Profile, die von vorherigen Besuchen mit demselben Gerät oder Cookie gesammelt wurden. Dadurch eignet er sich für die Top-of-funnel-Personalisierung, bei der der Besucher über kein Konto verfügt oder sich nicht authentifiziert hat.

## Anwendungsfallmuster

Im Folgenden werden das Kernmuster und der Ausführungsplan für diesen Anwendungsfall beschrieben.

**Web-Personalization für anonyme Besucher**

Bereitstellen personalisierter Inhalte, die auf sitzungsinternen Verhaltenssignalen für nicht identifizierte Besuchende basieren, über den AJO-Webkanal.

**Ausführungsplan:** Konfiguration der Web-Oberfläche > Bewertung von Verhaltensregeln > Inhaltsbereitstellung > Impression-Tracking > Berichterstellung

## Anwendungsfall - Übersicht

Die Web-Personalization für anonyme Besucher erfüllt die geschäftlichen Anforderungen, relevante, personalisierte Inhalte für Website-Besuchende bereitzustellen, die noch nicht identifiziert wurden - sie haben sich nicht angemeldet, haben keine bekannte Identität und können nicht in ein einheitliches Kundenprofil aufgelöst werden. Trotz dieser Einschränkung ist eine sinnvolle Personalisierung mithilfe von Verhaltenssignalen in der Sitzung erreichbar: angezeigte Seiten, Besuchszeit vor Ort, Bildlauftiefe, Verweisquelle, geografischer Standort, Gerätetyp und UTM-Kampagnenparameter.

Dieses Muster verwendet Web-Kanaloberflächen und Code-basierte Erlebnisse von AJO, um Seiteninhalte in Echtzeit zu ändern. Die Edge-Segmentierung ist die primäre Auswertungsmethode, da Entscheidungen mit einer Latenz von Untersekunden getroffen werden müssen, wenn der Besucher auf der Website navigiert. Der [!DNL Web SDK] erfasst Verhaltenssignale und sendet sie an den [!DNL AEP Edge Network], wo die von Edge ausgewerteten Zielgruppenregeln bestimmen, welche Inhaltsvariante bereitgestellt werden soll.

Im Gegensatz zur Web-/App-Personalisierung für bekannte Besucher, die das vollständige einheitliche Profil und die Segmentzugehörigkeit nutzt, ist dieses Muster auf Daten beschränkt, die in der aktuellen Sitzung beobachtet werden können, sowie auf alle anonymen Edge-Profile, die mit der ECID des Besuchers verknüpft sind ([!DNL Experience Cloud ID]). Diese Unterscheidung ist für die Implementierungsplanung von entscheidender Bedeutung: Die für die Personalisierung verfügbaren Verhaltenssignale sind auf das beschränkt, was der [!DNL Web SDK] erfasst und was über die Cookie-basierte ECID sitzungsübergreifend im Edge-Profilspeicher beibehalten wird.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Website-Interaktion steigern](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Verbesserung der Besuchszeit auf der Site, der Seiten pro Sitzung und der Interaktion mit Web-Inhalten durch relevante Erlebnisse, die auf anonyme Besuchersignale zugeschnitten sind.

| KPIs |
| --- |
| Time On (Web)-Seite |
| Interaktion |
| Konversionsraten |

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Vorlieben, Verhaltensweisen und Lebenszyklusphasen an - auch für Besuchende, die sich noch nicht identifiziert haben.

| KPIs |
| --- |
| Interaktion |
| Konversionsraten |
| Kundenzufriedenheit (CSAT) |

**[Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbessern Sie den Prozentsatz der Besucher und potenziellen Kunden, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen, indem Sie die relevantesten Inhalte basierend auf dem Verhaltenskontext präsentieren.

| KPIs |
| --- |
| Konversionsraten |
| Lead-Konversion |
| Kosten pro Lead |

## Beispiele für taktische Anwendungsfälle

Die folgenden Beispiele veranschaulichen spezifische Szenarien, in denen dieses Muster angewendet werden kann.

- **Überschriften-A/B-Test der Landingpage basierend auf der Empfehlungsquelle** - Testen Sie verschiedene Überschriften für Besucher, die aus Google, Social Media oder Direct Traffic kommen, um die Interaktion durch den Akquisekanal zu optimieren
- **Empfehlungen zur Kategorieaffinität basierend auf dem Durchsuchungsverhalten** — Anzeige von Produkt- oder Inhaltsempfehlungen basierend auf in der aktuellen Sitzung betrachteten Seiten, um die Erkennung und Konversion zu verbessern
- **Exitintent-Angebot für Besucher, die gerade die Website verlassen** — Präsentieren Sie ein Werbeangebot oder ein Lead-Erfassungsformular, wenn Verhaltenssignale darauf hindeuten, dass der Besucher die Website verlassen wird.
- **Geozielgerichtetes Werbebanner** - Zeigt standortspezifische Werbeaktionen, Store-Locator-Inhalte oder regionale Angebote basierend auf dem geografischen Standort des Besuchers an
- **Gerätespezifische Inhaltslayoutoptimierung** - Passen Sie das Inhaltslayout, die Bildgrößen und die CTA-Platzierung an, je nachdem, ob sich der Besucher auf dem Desktop, Tablet oder Mobilgerät befindet
- **Willkommensnachrichten für neue und wiederkehrende Besucher** — Differenzierung des Erlebnisses für Erst- und wiederkehrende anonyme Besucher mithilfe der ECID-Persistenz über Sitzungen hinweg
- **Inhaltsempfehlungen basierend auf angezeigten Seiten in der aktuellen Sitzung** - Dynamisches Aufdecken verwandter Artikel, Produkte oder Ressourcen basierend auf den Seiten, die der Besucher bereits angesehen hat
- **Dynamisches Hero-Banner basierend auf UTM-Kampagnenparametern** - Personalisieren Sie das Hero-Banner so, dass es der Botschaft oder dem Kreativen aus der verweisenden Kampagne entspricht.

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Personalization-Impressionsrate | Prozentsatz der zulässigen Seitenansichten, bei denen personalisierte Inhalte bereitgestellt wurden | AJO-Kampagnenbericht: Impressionen/Seitenansichten insgesamt |
| Clickthrough-Rate (CTR) | Prozentsatz der personalisierten Inhaltsimpressionen, die zu einem Klick führen | AJO-Kampagnenbericht: Klicks/Impressionen |
| Interaktionssteigerung | Verlängerung der Zeit auf der Seite, Seiten pro Sitzung oder Bildlauftiefe für personalisierte bzw. Standardinhalte | Vergleich von CJA Workspace: Personalisierte Kohorte vs. Kontrolle |
| Konversionsrate | Prozentsatz der Besucherinnen und Besucher, die personalisierten Inhalten ausgesetzt sind und eine gewünschte Aktion durchführen | CJA funnel Analysis: Impression > Interaction > Conversion |
| Absprungrate | Rückgang der Single Page Sessions für Besucher, die personalisierte Inhalte erhalten | CJA-Sitzungsanalyse: Delta der Absprungrate für personalisierte vs. standardmäßige Sitzungen |
| Erfolgsrate des Experiments | Prozentsatz der A/B-Tests, die einen statistisch signifikanten Gewinner ergeben | AJO-Experimentbericht: Experimente erreichen Konfidenzschwellenwert |

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Konfiguration der Web-Kanaloberfläche, Inhaltserstellung (Web- und Code-basierte Erlebnisse), Kampagnenausführung, Inhaltsexperimente (A/B-Tests), Entscheidungsfindung (dynamische Inhaltsauswahl) und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Edge-Segmentierung für die Echtzeit-Zielgruppenbewertung auf der Grundlage von Verhaltenssignalen in der Sitzung; Verwaltung anonymer Edge-Profile
- **[!DNL Adobe Experience Platform] (AEP)** - [!DNL Web SDK] für die Erfassung von Verhaltenssignalen, [!DNL Edge Network] für das Echtzeit-Datenrouting und die Bereitstellung von Personalisierung, Konfiguration des Datenstroms

## Architektur

Die folgende Referenzarchitektur veranschaulicht, wie anonyme Besuchersignale am Edge gesammelt, anhand von Zielgruppenregeln bewertet und zur Bereitstellung personalisierter Inhalte verwendet werden.

![Referenzarchitektur für die Aktivierung und Personalisierung anonymer Zielgruppen](/help/blueprints/audience-activation/assets/anonymous_activation.png)

## Verwandte Dokumentation

Die folgenden Experience League-Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

**Web-Kanal- und Code-basierte Erlebnisse**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-basierter Erlebniskanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-basierte Erlebniskonfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Zielgruppen und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization und Inhalte**

- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Inhaltsexperiment**

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische Berechnungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Entscheidungs-Management**

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Erstellen von Entscheidungsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Kampagnen**

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]und Datenerfassung**

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identität und Profil**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Datenmodellierung**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Reporting und Analysen**

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Data Governance und Datenschutz**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Leitplanken**

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
