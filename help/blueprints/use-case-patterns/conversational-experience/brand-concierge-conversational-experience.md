---
title: Brand Concierge - Gesprächserlebnis
description: Erfahren Sie, wie Sie digitale Eigenschaften in KI-gestützte, markensichere Gesprächserlebnisse umwandeln können, die die Kundenfindung leiten.
solution: Experience Platform, Real-Time Customer Data Platform
exl-id: a9545328-316d-446a-9308-18af61c58d1c
source-git-commit: fe4353cfe34855ad91ccb5698e30030322246c08
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Brand Concierge-Gesprächserlebnis

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für KI-gestützte Konversationserlebnisse unter Verwendung von [!DNL Adobe Brand Concierge], die in [!DNL Adobe Experience Platform] (AEP) und [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) integriert sind. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die markensichere Agenten für digitale Eigenschaften bereitstellen müssen.

Es behandelt alle praktikablen Ansätze für die Bereitstellung von Gesprächserlebnissen, von Produktberatungs-Chatbots bis hin zu vollständigen Site-Navigationsassistenten, mit Anleitungen dazu, wann jede Option ausgewählt werden sollte. Der Plan behandelt die Agentenkonfiguration, die Markenverwaltung, die Inhaltsintegration, Bereitstellungsstrategien, die Profilanreicherung durch Gesprächssignale und die Analytics-Optimierung.

[!DNL Brand Concierge] ermöglicht es Marken, intelligente Gesprächspartner bereitzustellen, die Markensprache verstehen, auf freigegebene Produktkataloge und Inhalte zugreifen, personalisierte Empfehlungen auf der Grundlage von Echtzeit-Profildaten bereitstellen und Absichts- und Sentiment-Signale zurück in das einheitliche Kundenprofil erfassen. Das Ergebnis ist ein Gesprächserlebnis, das sich natürlich und markenbezogen anfühlt und gleichzeitig das Verständnis des Unternehmens für jeden Kunden erweitert.

## Anwendungsfall - Übersicht

Unternehmen versuchen zunehmend, statische digitale Erlebnisse in dynamische, KI-gestützte Gespräche umzuwandeln, die Kunden durch Entdeckungs-, Produktauswahl- und Kaufentscheidungen führen. [!DNL Adobe Brand Concierge] bietet dazu eine KI-Ebene für konversationelle Gespräche, die auf vorhandenen digitalen Eigenschaften aufbaut und von AEP Agent Orchestrator unterstützt wird.

Dieses Muster unterscheidet sich von herkömmlichen Chatbot-Implementierungen, da es nativ in das einheitliche AEP-Profil integriert ist, Leitplanken für die Markenverwaltung verwendet, um sicherzustellen, dass jede Antwort mit den Markenstandards übereinstimmt, und Gesprächssignale zurück in die Kundendatenplattform zur nachgelagerten Personalisierung und Aktivierung leitet.

Die Zielgruppe umfasst Teams für digitale Erlebnisse, E-Commerce-Manager, Inhaltsstrategen und Marketing-Techniker, die intelligente Konversationserlebnisse bereitstellen müssen, die Interaktion, Konversion und Profilanreicherung fördern.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Bereitstellen personalisierter Kundenerlebnisse

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.

**KPIs:** Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT)

[Weitere Informationen über die Bereitstellung personalisierter Kundenerlebnisse](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Verbessern der Kundeninteraktion

Erhöhen Sie die Interaktionsfrequenz und -tiefe auf allen digitalen und physischen Touchpoints.

**KPIs:** Interaktion, Besuchszeit pro Seite (Web), Öffnungsraten

[Weitere Informationen zur Verbesserung der Kundeninteraktion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Erhöhung der Konversionsraten

Verbessern Sie den Prozentsatz der Besucher und Interessenten, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen.

**KPIs:** Konversionsraten, Lead-Konversion, Kosten pro Lead

[Erfahren Sie mehr über die Erhöhung der Konversionsraten](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung.

**KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion

[Weitere Informationen über die Akquise von Neukunden](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie dieses Muster in der Praxis angewendet werden kann.

- **Produkterkennungsassistent** - Stellen Sie auf Produktlistenseiten einen Gesprächsagenten bereit, der qualifizierte Fragen stellt und Produktempfehlungen auf der Grundlage von Kundenanforderungen, Voreinstellungen und Budget eingrenzt
- **Geführter Vergleichsberater** - Unterstützen Sie Kunden beim direkten Vergleich von Produkten im Rahmen eines natürlichen Dialogs, indem Sie Unterschiede hervorheben, die für ihre angegebenen Prioritäten relevant sind
- **Größe und Passform Concierge** - Führen Sie Kleidung oder Schuheinkäufer durch die Größenauswahl mit Fragen und Antworten zu Gesprächen, reduzieren Sie die Renditen und erhöhen Sie das Kaufvertrauen
- **Abonnement- oder Planauswahl** - Führen Sie Kundinnen und Kunden durch die Optionen der Service-Stufe oder des Abonnementplans mit personalisierten Empfehlungen, die auf Nutzungsmustern und angegebenen Anforderungen basieren
- **Site-Navigationsassistent** - Helfen Sie Besuchenden, relevante Inhalte, Support-Ressourcen oder Produktkategorien basierend auf ihrer angegebenen Absicht zu finden, um die Absprungraten auf komplexen Websites zu reduzieren
- **Beratung vor dem Kauf** - Bereitstellung einer umfassenden Kaufanleitung (z. B. Elektronik, Finanzprodukte, Versicherungen) durch Gespräche, die auf eine Empfehlung ausgerichtet sind
- **Concierge für das Treueprogramm** - Helfen Sie den Mitgliedern des Treueprogramms, Belohnungen zu entdecken, die Vorteile der Stufe zu verstehen und Einlösungsmöglichkeiten durch konversative Interaktion zu finden
- **Konversation zur erneuten Interaktion** - Initiieren Sie eine proaktive Gesprächsrunde mit wiederkehrenden Besuchern, die auf dem vorherigen Navigationsverlauf oder abgebrochenen Artikeln des Warenkorbs basiert.
- **Live-Agent-Eskalation mit Kontext** - Nahtlose Übergabe komplexer Anfragen an Live-Vertriebs- oder Support-Mitarbeiter unter Beibehaltung des vollständigen Konversationskontexts und der Kundenprofildaten
- **Support nach dem Kauf und Upsell** - Wenden Sie sich nach dem Kauf mit Einrichtungsunterstützung, ergänzenden Produktvorschlägen und Zufriedenheits-Check-ins über Dialogkanäle an Kunden

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Gesprächsrate | Prozentsatz der Besucherinnen und Besucher, die eine Konversation initiieren und aufrechterhalten | Gestartete Konversationen/geeignete Seitenansichten |
| Gesprächsabschlussrate | Prozentsatz der Konversationen, die eine sinnvolle Lösung erreichen | Abgeschlossene Unterhaltungen/Gespräche gestartet |
| Konversionsrate | Prozentsatz der Konversationen, die zu einer gewünschten Aktion führen (Kauf, Anmeldung, Lead-Formular) | Konversionen aus Konversation/Gesamtunterhaltungen |
| Durchschnittliche Gesprächstiefe | Anzahl der Umdrehungen pro Konversation, die die Interaktionsqualität angibt | Durchschnittliche Nachrichtenanzahl pro Sitzung |
| Kundenzufriedenheit (CSAT) | Bewertung der Zufriedenheit nach Gesprächen aus In-Experience-Feedback | Umfrageantworten oder Thumbs-up/Down-Bewertungen |
| Annahmerate für Empfehlungen | Prozentsatz der akzeptierten oder angeklickten Produktempfehlungen | Auf Empfehlungen reagierte/bereitgestellte Empfehlungen |
| Übergaberate für Live Agent | Prozentsatz der an Live-Agenten eskalierten Konversationen | Übergaben/Gesamtgespräche |
| Anreicherungsrate des Profils | Prozentsatz der Konversationen, die neue Absichts- oder Präferenzsignale ergeben | Angereicherte Profile/Konversationen insgesamt |
| Umsatz beeinflusst durch Konversation | Umsatz aus Käufen, bei denen der Konversion ein [!DNL Brand Concierge] vorangegangen ist | Attributionsanalyse bei Journey-zu-Kauf-Konversation |
| Zeit bis zur Lösung | Durchschnittliche Dauer vom Gesprächsbeginn bis zur Auflösung oder Übergabe | Zeitstempelanalyse über Konversationsereignisse hinweg |

## Anwendungsfallmuster

**Brand Concierge-Gesprächserlebnis**

Wandeln Sie digitale Eigenschaften in KI-gestützte, markensichere Gesprächserlebnisse um, die die Kundenfindung durch natürlichen Dialog leiten, Profile mit Intent- und Sentiment-Signalen anreichern und personalisierte Produktempfehlungen liefern.

**Funktionskette:** Agentenkonfiguration > Brand Governance-Einrichtung > Inhaltsintegration > Bereitstellung von konversativen Erlebnissen > Profilanreicherung > Analysen und Optimierung

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Brand Concierge]** - KI-gestützte Anwendung für konversatives Erlebnis, die den Agenten-Orchestrator, Product Advisor Agent, Site Advisory Agent, Brand Governance und konversative Analysen bereitstellt
- **[!DNL Adobe Experience Platform] (AEP)** - Unified Data Foundation mit XDM-Schemata, Identitätsauflösung, Echtzeit-Kundenprofilen und einer Datenerfassungs-Infrastruktur für Gesprächssignale
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** - Kundendatenplattform, die Echtzeit-Profilsuche für personalisierte Unterhaltungen, Zielgruppensegmentierung aus Gesprächssignalen und Profilanreicherung mit Intent- und Sentiment-Daten bietet

## Verwandte Dokumentation

Implementierungshandbücher und weitere Informationen finden Sie in der [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/brand-concierge/content/documentation/overview) auf Adobe Experience League.
