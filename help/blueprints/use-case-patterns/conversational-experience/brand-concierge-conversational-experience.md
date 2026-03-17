---
title: Brand Concierge - Gesprächserlebnis
description: Erfahren Sie, wie Sie digitale Eigenschaften in KI-gestützte, markensichere Gesprächserlebnisse umwandeln können, die die Kundenfindung leiten.
solution: Experience Platform, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---


# Brand Concierge-Gesprächserlebnis

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für KI-gestützte Konversationserlebnisse unter Verwendung von [!DNL Adobe Brand Concierge], die in [!DNL Adobe Experience Platform] (AEP) und [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) integriert sind. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die markensichere Agenten für digitale Eigenschaften bereitstellen müssen.

Es behandelt alle praktikablen Ansätze für die Bereitstellung von Gesprächserlebnissen, von Produktberatungs-Chatbots bis hin zu vollständigen Site-Navigationsassistenten, mit Anleitungen dazu, wann jede Option ausgewählt werden sollte. Der Plan behandelt die Agentenkonfiguration, die Markenverwaltung, die Inhaltsintegration, Bereitstellungsstrategien, die Profilanreicherung durch Gesprächssignale und die Analytics-Optimierung.

[!DNL Brand Concierge] ermöglicht es Marken, intelligente Gesprächspartner bereitzustellen, die Markensprache verstehen, auf freigegebene Produktkataloge und Inhalte zugreifen, personalisierte Empfehlungen auf der Grundlage von Echtzeit-Profildaten bereitstellen und Absichts- und Sentiment-Signale zurück in das einheitliche Kundenprofil erfassen. Das Ergebnis ist ein Gesprächserlebnis, das sich natürlich und markenbezogen anfühlt und gleichzeitig das Verständnis des Unternehmens für jeden Kunden erweitert.

## Anwendungsfall - Übersicht

Unternehmen versuchen zunehmend, statische digitale Erlebnisse in dynamische, KI-gestützte Gespräche umzuwandeln, die Kunden durch Entdeckungs-, Produktauswahl- und Kaufentscheidungen führen. [!DNL Adobe Brand Concierge] Dies wird behoben, indem eine KI-Ebene für konversationelle Gespräche bereitgestellt wird, die auf vorhandenen digitalen Eigenschaften aufbaut und von AEP Agent Orchestrator unterstützt wird.

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

**KPIs:** Upsell/Crosssell %, Inkrementeller Umsatz, Kundenlebenszeitwert

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
- **[!DNL Adobe Experience Platform](AEP)** - Unified Data Foundation mit XDM-Schemata, Identitätsauflösung, Echtzeit-Kundenprofilen und einer Datenerfassungs-Infrastruktur für Gesprächssignale
- **[!DNL Real-Time CDP]([!DNL RT-CDP])** - Kundendatenplattform, die Echtzeit-Profilsuche für personalisierte Unterhaltungen, Zielgruppensegmentierung aus Gesprächssignalen und Profilanreicherung mit Intent- und Sentiment-Daten bietet

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Sandbox mit aktivierter [!DNL Brand Concierge]; Rollen, die für Erlebnisadministratoren, Content-Manager und Analytics-Benutzer von Conversational Experience Manager konfiguriert sind; ABAC-Richtlinien für Konversationsdaten, die personenbezogene Daten oder vertrauliche Kundensignale enthalten | [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | XDM-Schemata für Konversationsereignisse (ExperienceEvent-Klasse mit konversationsspezifischen Feldergruppen, die Absichten, Sentiment, Produktinteraktionen und Übergabeereignisse erfassen); Profilschema, das mit Präferenz- und Absichtsattributen für Konversationen erweitert wurde; Produktkatalogsuchschema für Erstellungsempfehlungen | [XDM-System - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Datenquellen und Sammlung | Erforderlich | [!DNL Web SDK] oder [!DNL Mobile SDK] konfiguriert mit Datenströmen, die Konversationsereignisdaten an AEP-Datensätze weiterleiten; [!DNL Edge Network]-Integration für die Echtzeit-Ereigniserfassung während Konversationen; Produktkatalogdaten, die über Quell-Connectoren oder die Batch-Aufnahme aufgenommen werden | [Web SDK - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | Identity-Namespaces, die für die Besucheridentifizierung konfiguriert wurden (ECID für anonyme Kontakte, CRM-ID oder E-Mail für authentifizierte Kontakte); Zusammenführungsrichtlinien, die mit Edge-Aktivierung für die Echtzeit-Profilsuche während Konversationen konfiguriert wurden; Regeln zur Identitätsverknüpfung für die Kontinuität geräteübergreifender Konversationen | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Zielgruppendefinition und Segmentierung | Angenommen an Ort und Stelle | Zielgruppen, die nicht für die Core Conversational Deployment erforderlich sind, aber für personalisierte Konversationsstrategien benötigt werden (z. B. erhalten hochwertige Kundensegmente unterschiedliche Konversationsflüsse); Streaming oder Edge-Evaluierung werden für die Echtzeit-Konversation und Personalisierung empfohlen | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Fassen Sie Gesprächssignale in Profilebenen-Attributen (z. B. Gesamtunterhaltungen, dominante Produktinteressen, durchschnittlicher Sentiment-Wert) zur Verwendung in nachgelagerten Segmentierungs- und Personalisierungsbereichen zusammen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Konfigurieren Sie Aufbewahrungsrichtlinien für Daten zu Konversationsereignissen, verwalten Sie Einverständniserklärungen für die Gesprächsaufzeichnung und -profilerstellung und unterstützen Sie Datenschutzlöschanfragen für Gesprächstranskripte | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Kennzeichnen von dialogorientierten Datenfeldern, die PII-, Sentiment- oder Intent-Signale enthalten; Durchsetzen von Governance-Richtlinien, die verhindern, dass sensible konversative Daten nicht autorisierte Ziele erreichen | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | Pipelines für die Aufnahme von Konversationsereignissen überwachen, Erfolgsraten der Profilanreicherung verfolgen und vor Datenflussfehlern warnen, die die Qualität der Konversationspersonalisierung beeinträchtigen könnten | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Analysieren Sie die Konversationsleistung, das Kunden-Feedback, die Konversionszuordnung und die Effektivität des Agenten mithilfe [!DNL Brand Concierge] integrierten Analysen und [!DNL CJA] für eine kanalübergreifende Konversationsfolgenanalyse | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Brand Concierge]

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Agent-Konfiguration | Phase 1: Agentenkonfiguration | Konfigurieren Sie den [!DNL Brand Concierge] Agent Orchestrator mit Agentenspezialisierungen (Produktberater, Site-Beratung) und Einstellungen für das Basisverhalten. |
| Einrichten der Brand Governance | Phase 2: Einrichtung der Markenverwaltung | Definieren Sie Markensprache, Ton, Leitplanken für Messaging, genehmigte Inhaltsgrenzen und verbotene Themen, die alle Gesprächsinteraktionen prägen |
| Content-Integration | Phase 3: Inhaltsintegration | Verbinden von markengeprüften Inhaltsquellen, einschließlich AEM-Inhalten, Produktkatalogen, Wissensdatenbanken und anderen vertrauenswürdigen Daten, um Antworten auf die Erdung zu erhalten |
| Konfiguration von Product Advisor | Phase 3: Inhaltsintegration | Konfigurieren Sie die Product Advisor Agent für personalisierte Produktempfehlungen, angeleitete Vergleiche und markenorientierte Antwortbereitstellung |
| Site Advisory-Konfiguration | Phase 3: Inhaltsintegration | Konfigurieren Sie den Site Advisory-Agenten, um die Navigation durch die Anpassung von Interaktionen auf der Grundlage des Besucherverhaltens und von Absichtssignalen zu verbessern |
| Bereitstellung von konversativen Erlebnissen | Phase 4: Bereitstellung von Erlebnissen im Gespräch | Bereitstellen von Konversationserlebnissen über unterstützte Kanäle (Web, Mobile App, benutzerdefinierte SDK) mit Text- und Sprachinteraktionsunterstützung |
| Low-Code-Flussmanagement | Phase 4: Bereitstellung von Erlebnissen im Gespräch | Marketing-Teams können mithilfe von Low-Code-Konfigurations-Tools den Gesprächston, Flüsse und Inhalte aktualisieren |
| Anreicherung von Dialogprofilen | Phase 5: Profilanreicherung | Anreicherung von AEP-Kundenprofilen mit Intent-, Sentiment-, Produktaffinitäts- und Verhaltenssignalen, die in Gesprächen erfasst werden |
| Konversationsanalytik | Phase 6: Analyse und Optimierung | Überwachen Sie Interaktionsmetriken, Kunden-Feedback, Konversionsdaten und die Konversationsqualität über integrierte Analyse-Dashboards. |
| Übergabe von Live-Agenten | Phase 4: Bereitstellung von Erlebnissen im Gespräch | Konfigurieren der nahtlosen Übergabe an Live-Vertriebs- oder Support-Agenten unter Beibehaltung des vollständigen Konversationskontexts |

### [!DNL Real-Time CDP]

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Echtzeit-Profilsuche | Phase 4: Bereitstellung von Erlebnissen im Gespräch | Zugriff auf Echtzeit-Kundenprofilattribute und Segmentzugehörigkeiten, um Gesprächsantworten basierend auf bekannten Kundendaten zu personalisieren |
| Profilanreicherung | Phase 5: Profilanreicherung | Profile mit berechneten Attributen anreichern, die aus Konversationsereignissen abgeleitet wurden (Intent Scores, Sentiment-Trend, Produktaffinität) |
| Zielgruppenauswertung | Phase 5: Profilanreicherung | Bewerten der Zielgruppenzugehörigkeit auf der Grundlage von Gesprächssignalen, um das nachgelagerte Targeting interaktiver Gesprächssegmente zu ermöglichen |

## Voraussetzungen

Die folgenden Elemente müssen vor Beginn der Implementierung vorhanden sein.

- [!DNL Adobe Brand Concierge] Berechtigung ist für die Organisation aktiv
- AEP- und [!DNL RT-CDP]-Lizenzen verfügen über ausreichende Berechtigungen für Profil- und Ereignisvolumen
- In den Branding-Richtlinien sind Dokumente zu Sprache, Ton, genehmigten Werbeaussagen und verbotenen Themen enthalten
- Produktkatalog oder Inhalts-Repository für die Integration vorbereitet (AEM-Assets, PIM-Daten oder strukturierter Produkt-Feed)
- Web-Eigenschaften für Bereitstellung von konversativen Erlebnissen mit technischem Zugriff für die SDK-Integration identifiziert
- Bei Übergabe verfügbare Live-Agent-Infrastruktur (Contact Center-Plattform, CRM-Integration)
- Ein Framework für die Einverständnisverwaltung für die dialogorientierte Datenerfassung und Profilerstellung ist vorhanden
- [!DNL Web SDK] oder [!DNL Mobile SDK] bereits in den Zieleigenschaften bereitgestellt (oder für gleichzeitige Bereitstellung geplant)
- Ausrichtung der Stakeholder am Umfang der Konversation (nur Produktberatung, Site-Navigation oder beides)
- Datenschutz und rechtliche Überprüfung für KI-gestützte Datenerfassung und -nutzung abgeschlossen

## Implementierungsoptionen

In den folgenden Abschnitten werden verschiedene Ansätze zur Implementierung dieses Anwendungsfallmusters beschrieben.

### Option A: Bereitstellung von Produktberatern

**Am besten geeignet für:** E-Commerce- und Einzelhandelsorganisationen konzentrieren sich auf geführte Produkterkennungs-, Vergleichs- und Empfehlungserlebnisse, die Konversionen und den durchschnittlichen Bestellwert fördern.

**Funktionsweise:**

Die Product Advisor Agent ist als primäre Konversationsspezialisierung konfiguriert. Es stellt eine Verbindung zum Produktkatalog her, versteht Produktattribute und -beziehungen und führt Kunden durch den natürlichen Dialog, um zu personalisierten Empfehlungen zu gelangen. Der Agent verwendet Leitplanken für die Markenverwaltung, um sicherzustellen, dass die Empfehlungen mit den Geschäftsprioritäten übereinstimmen (z. B. Förderung von Lagerartikeln, Hervorhebung von Produkten, die eine Gewinnspanne begünstigen).

Product Advisor kann mit dem Echtzeit-Kundenprofil integriert werden, um auf Kaufverlauf, Browser-Verhalten und Präferenzdaten zuzugreifen. So werden Empfehlungen ermöglicht, die berücksichtigen, was der Kunde bereits besitzt, zuvor in Betracht gezogen hat oder wahrscheinlich benötigt. Konversationen werden erfasst, wenn Erlebnisereignisse und Absichtssignale zur nachgelagerten Verwendung zurück in das Profil fließen.

**Wichtige Aspekte:**

- Erfordert einen gut strukturierten Produktkatalog mit umfangreichen Attributdaten für effektive Empfehlungen
- Produktdaten müssen auf dem neuesten Stand gehalten werden, um zu vermeiden, dass nicht vorrätige oder eingestellte Artikel empfohlen werden
- Die Markenverwaltung muss definieren, wie der Agent mit Erwähnungen und Preisvergleichen von Wettbewerbsprodukten umgeht

**Vorteile:**

- Direkte Steigerung der messbaren Umsatzauswirkungen durch geführte Kaufkonversionen
- Reduziert die Rückgaberaten von Produkten durch fundiertere Kaufentscheidungen
- Erfasst hochwertige Produktaffinität und Intent-Signale für die nachgelagerte Personalisierung
- Natürliche Erweiterung bestehender E-Commerce-Erlebnisse

**Einschränkungen:**

- Erfordert die fortlaufende Wartung und Synchronisierung des Produktkatalogs
- Beschränkung auf produktzentrierte Konversationen; Fragen zur Website-Navigation werden möglicherweise nicht berücksichtigt
- Die Effektivität hängt von der Qualität und Vollständigkeit der Katalogdaten ab

**Experience League:**

- [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge-Produktberater](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### Option B: Site Advisory-Bereitstellung

**Am besten geeignet für:** Organisationen mit komplexen digitalen Eigenschaften (Medien, Finanzdienstleistungen, Gesundheitswesen, Technologie), in denen Besucher Navigationsunterstützung benötigen, um relevante Inhalte, Ressourcen oder Self-Service-Tools zu finden.

**Funktionsweise:**

Der Site Advisory Agent ist als primäre Konversationsspezialisierung konfiguriert. Sie indiziert die Inhaltsstruktur der Site, versteht Seitenbeziehungen und Inhaltskategorien und passt ihre Anleitung auf der Grundlage von Besucherverhaltenssignalen und angegebener Absicht an. Wenn ein Besucher interagiert, interpretiert der Agent seine Anforderungen und leitet sie an die relevantesten Inhalte, Tools oder Ressourcen weiter.

Site Advisory nutzt Echtzeit-Verhaltenssignale (aktuelle Seite, Empfehlungsquelle, Navigationspfad) kombiniert mit Profildaten (frühere Besuche, Inhaltsvoreinstellungen, Kundenebene), um kontextbezogene, relevante Navigationshilfe zu bieten. Dies ist besonders nützlich auf Sites mit tiefen Inhaltshierarchien, mehreren Produktlinien oder komplexen Self-Service-Workflows.

**Wichtige Aspekte:**

- Crawlen Erfordert eine umfassende Inhaltsindizierung und regelmäßige Neuindizierung bei Änderungen des Site-Inhalts
- Am effektivsten auf Websites mit großer Inhaltsbreite, auf denen Besuchende häufig Schwierigkeiten haben, das zu finden, was sie benötigen
- Die Markenverwaltung sollte Bereichsgrenzen definieren (zu welchen Site-Bereichen der Agent navigieren kann)

**Vorteile:**

- Verringert Bounce-Raten und verbessert die Auffindbarkeit von Inhalten auf komplexen Sites
- Erfasst Navigationszielsignale, die Inhaltslücken und Probleme mit dem Benutzererlebnis offenlegen
- Geringere Implementierungskomplexität als bei Produktberatern (keine Produktkatalogintegration erforderlich)
- Bietet Analyseeinblicke darüber, was Besucher suchen, aber nicht finden können

**Einschränkungen:**

- Weniger direkt an die Umsatzkonversion gebunden als produktorientierte Gespräche
- Erfordert, dass Inhalte gut strukturiert und regelmäßig aktualisiert werden, um präzise Anleitungen zu bieten
- Möglicherweise sind bei einer Weiterentwicklung der Site-Struktur häufige Umschulungen erforderlich

**Experience League:**

- [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge Site Advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### Option C: Kombinierter Produktberater und Site Advisory-Bereitstellung

**Am besten geeignet für:** Unternehmen, die ein umfassendes Gesprächserlebnis wünschen, das sowohl die Produkterkennung als auch die Navigation auf der Site umfasst, in der Regel große Einzelhandels- oder B2C-Marken mit umfangreichen digitalen Eigenschaften und unterschiedlichen Besucherabsichten.

**Funktionsweise:**

Sowohl der Product Advisor Agent- als auch der Site Advisory-Agent werden im [!DNL Brand Concierge] Orchestrator konfiguriert. Der Agent Orchestrator verwendet die Absichtserkennung, um Konversationen an die entsprechende Spezialisierung weiterzuleiten. Produktbezogene Abfragen gehen an den Produktberater, während Navigations- und Inhaltssuchabfragen an den Site-Ratgeber weitergeleitet werden. Der Orchestrierende verwaltet nahtlose Übergänge zwischen Spezialisierungen innerhalb eines einzigen Gesprächs.

Dieser Ansatz bietet die umfassendste Gesprächserfahrung und deckt die gesamte Bandbreite der Besucheranforderungen ab, von „Hilfe bei der Produktsuche“ bis „Wo kann ich meinen Bestellstatus überprüfen?“ Die Brand Governance-Leitplanken gelten in beiden Spezialisierungen einheitlich, sodass unabhängig vom Gesprächsthema eine konsistente Markendarstellung gewährleistet ist.

**Wichtige Aspekte:**

- Höhere Implementierungskomplexität, die sowohl eine Integration von Produktkatalog als auch Inhalten erfordert
- Die Absichtsweiterleitung zwischen Spezialisierungen muss gut abgestimmt sein, um fehlgeleitete Gespräche zu vermeiden
- Die Einrichtung der Brand Governance ist umfangreicher, um sowohl Produkt- als auch Navigationskontexte abzudecken

**Vorteile:**

- Bietet das umfassendste Gesprächserlebnis für Besucher
- Ein einziger Einstiegspunkt für die Bearbeitung unterschiedlicher Besucherinteressen, ohne dass separate Schnittstellen erforderlich sind
- Spezialisierungsübergreifende Gespräche (z. B. Produktfragen, die zur Unterstützung der Navigation führen) werden natürlich gehandhabt
- Reichste Profilanreicherung durch vielfältige Gesprächssignale

**Einschränkungen:**

- Höchster Implementierungsaufwand und laufende Wartung
- Erfordert die Koordinierung zwischen Produktkatalog und Inhalts-Teams
- Komplexere Anforderungen an Tests und Qualitätssicherung
- Die Konfiguration der Brand Governance ist stärker involviert

**Experience League:**

- [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Vergleich von Optionen

| Kriterien | Option A: Produktberater | Option B: Site Advisory | Option C: Kombiniert |
| --- | --- | --- | --- |
| Am besten geeignet für | E-Commerce, produktgesteuerte Konversion | Umfangreiche Websites, Self-Service-Navigation | Umfassendes digitales Erlebnis |
| Komplexität | Mittel | Low-Medium | Hoch |
| Time-to-Value | 4-6 Wochen | 3-5 Wochen | 6-10 Wochen |
| Auswirkungen auf den Umsatz | Hoch (direkter Konversionseinfluss) | Medium (indirekt über Interaktion) | Höchste (sowohl Konversion als auch Interaktion) |
| Inhaltsanforderungen | Produktkatalog mit umfangreichen Attributen | Site-Inhaltsindex | Produktkatalog und Inhaltsindex |
| Profilanreicherung | Produktaffinität, Kaufabsicht | Navigationsziel, Inhaltsvoreinstellungen | Volles Signalspektrum |
| Wartungsaufwand | Synchronisierung des Produktkatalogs | Neuindizierung von Inhalten | Beide laufen noch |

### Wählen der richtigen Option

Beginnen Sie mit der Bewertung Ihres primären Geschäftsziels und der Merkmale des digitalen Eigentums:

1. **Wenn Ihr primäres Ziel die Förderung der** ist und Ihr digitales Eigentum auf den Handel ausgerichtet ist, wählen Sie **Option A (Product Advisor)**. Dies ist der häufigste Ausgangspunkt für Einzelhandels- und E-Commerce-Marken.

2. **Wenn Ihr Hauptziel die Verbesserung der** ist und Ihre Site tiefe Inhaltshierarchien oder komplexe Self-Service-Workflows aufweist, wählen Sie **Option B (Site Advisory)**. Dies ist ideal für Medien-, Finanzdienstleistungs-, Gesundheits- und Technologieunternehmen.

3. **Wenn Sie eine umfassende Abdeckung** und sowohl Produkt-Commerce- als auch Inhaltsnavigationsanforderungen haben, wählen Sie **Option C (kombiniert)**. Erwägen Sie, mit einer Spezialisierung zu beginnen und die zweite hinzuzufügen, nachdem die erste stabil und optimiert ist.

Für die meisten Unternehmen wird ein stufenweiser Ansatz empfohlen: zuerst eine Spezialisierung bereitstellen, die Leistung überprüfen und Erkenntnisse sammeln und dann auf die kombinierte Bereitstellung erweitern.

## Implementierungsphasen

In den folgenden Phasen wird der empfohlene Implementierungsablauf beschrieben.

### Phase 1: Agentenkonfiguration

**Anwendungsfunktion:** [!DNL Brand Concierge]: Agentenkonfiguration

Konfigurieren Sie den Core [!DNL Brand Concierge] Agent Orchestrator, einschließlich der Auswahl von Agentenspezialisierungen (Produktberater, Site-Ratgeber oder beides), der Konfiguration des Basis-Agenten-Verhaltens und der Herstellung einer Verbindung zwischen [!DNL Brand Concierge] und AEP für den Profilzugriff und die Ereigniserfassung.

#### Entscheidung: Auswahl der Agentenspezialisierung

Legen Sie fest, welche Agentenspezialisierungen für diese Bereitstellung aktiviert werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Produktberater | Commerce-fokussierte Bereitstellung, die auf die Produkterkennung und -konvertierung abzielt | Integration des Produktkatalogs erforderlich; schnellster Weg zur Umsatzsteigerung |
| Nur Site-Beratung | Content- und navigationsorientierte Bereitstellung | Geringere Integrationskomplexität; am besten geeignet für Websites, die nicht für den Handel bestimmt sind |
| Beide Spezialisierungen | Umfassende Berichterstattung über Produkt und Inhalt | Höhere Komplexität; schrittweiser Rollout ab einer |

#### Entscheidung: Modell zur Konversationsinitiation

Legen Sie fest, wie Konversationen mit der digitalen Eigenschaft beginnen sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Besucherinitiiert (passiv) | Standardansatz, bei dem das Chat-Widget verfügbar ist, aber nicht proaktiv interagiert | Geringeres Unterbrechungsrisiko; stützt sich auf die Besucherwahrnehmung der Chat-Option |
| Proaktive Interaktion (ausgelöst) | Agent initiiert Konversation auf der Grundlage von Verhaltenssignalen (z. B. verlängerte Verweilzeit, wiederholte Seitenbesuche, Warenkorbzögerung) | Höhere Interaktionsraten, aber auch das Risiko von Besucherärgernissen, wenn die Trigger zu aggressiv sind. Erfordert eine Abstimmung der verhaltensbezogenen Trigger |
| Hybrid (passiv mit kontextuellen Eingabeaufforderungen) | Das Chat-Widget ist passiv, zeigt jedoch kontextuelle Eingabeaufforderungen basierend auf dem Seiteninhalt oder dem Besucherverhalten an. | Ausgewogener Ansatz; Anleitung ohne erzwungene Interaktion |

#### Konfigurieren des Agenten

**UI-Navigation:** [!DNL Experience Platform] > KI-Assistent > [!DNL Brand Concierge] > Agentenkonfiguration

Wichtige Konfigurationsdetails:

- Den Namen und die Beschreibung des Agenten definieren, die in der Konversationsoberfläche angezeigt werden
- Wählen Sie aus, welche AEP-Sandbox das Kundenprofil und die Ereignisdaten enthält, auf die der Agent zugreifen soll
- Konfigurieren Sie den Agenten-Orchestrator, um Abfragen basierend auf der Absichtserkennung zwischen Spezialisierungen zu leiten.
- Parameter für Unterhaltungssitzungen festlegen (Zeitüberschreitungsdauer, maximale Unterhaltungsdauer, Begrenzungen für gleichzeitige Sitzungen)
- Echtzeit-Profilsuchintegration aktivieren, damit der Agent während Konversationen auf Besucherprofildaten zugreifen kann

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Produktberater):**
Aktivieren Sie die Produktberaterspezialisierung und konfigurieren Sie deren Verbindung zur Produktkatalog-Datenquelle. Festlegen von Produktempfehlungsparametern, einschließlich maximaler Empfehlungen pro Antwort, Voreinstellungen für die Anzeige von Produktattributen und Regeln für die Vergleichsbehandlung.

**Für Option B (Site Advisory):**
Aktivieren Sie die Site Advisory-Spezialisierung und konfigurieren Sie deren Verbindung zum Site-Inhaltsindex. Legen Sie Navigationsparameter fest, einschließlich der Begrenzungen des Inhaltsbereichs, der Handhabung von Seitenkategorien und der Voreinstellungen für die Erzeugung von Deep-Links.

**Für Option C (kombiniert):**
Aktivieren Sie beide Spezialisierungen und konfigurieren Sie die Intent-Routing-Logik des Orchestrierers. Definieren Sie Routing-Regeln, die bestimmen, wann eine Konversation von einem Produktberater oder einer Site-Beratung gehandhabt werden soll und wie Übergänge zwischen Spezialisierungen innerhalb einer einzigen Konversation verwaltet werden sollen.

**Dokumentation zu Experience League:**

- [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Überblick über den KI-Assistenten](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Phase 2: Einrichtung der Markenverwaltung

**Anwendungsfunktion:** [!DNL Brand Concierge]: Einrichtung der Markenverwaltung

Konfigurieren Sie die Brand Governance-Leitplanken, die alle dialogorientierten Interaktionen formen. Dazu gehören Markensprache- und -tondefinitionen, genehmigte Inhaltsgrenzen, verbotene Themen, Richtlinien für den Antwortstil und Eskalationsregeln. Brand Governance stellt sicher, dass jede KI-generierte Antwort mit den Markenstandards übereinstimmt.

#### Entscheidung: Strenge der Governance

Legen Sie fest, wie stark die Leitplanken für die Markenführung die dialogischen Reaktionen einschränken sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Strenge Governance | Hochreglementierte Branchen (Finanzdienstleistungen, Gesundheitswesen, Versicherungen) oder Premiummarken, die eine präzise Tonkontrolle erfordern | Begrenzt die Flexibilität im Gespräch; kann zu häufigeren Antworten auf „Ich kann da nicht helfen“ führen; höchste Markensicherheit |
| Moderate Regierungsführung | Die meisten Verbrauchermarken, bei denen es auf die Markenkonsistenz ankommt, aber eine gewisse Flexibilität im Gespräch akzeptabel ist | Gutes Gleichgewicht zwischen Markensicherheit und konversativer Natürlichkeit; empfohlener Ausgangspunkt für die meisten Implementierungen |
| Flexible Governance | Gelegenheits- oder Lifestyle-Marken, bei denen dialogorientierte Persönlichkeit und Interaktion priorisiert werden | Die meisten natürlichen Gesprächsbewegungen erfordern eine kontinuierliche Überwachung der markenfremden Reaktionen |

#### Entscheidung: Off-Topic Handling-Strategie

Legen Sie fest, wie der Agent Fragen außerhalb seines konfigurierten Bereichs behandeln soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Zu Umfang umleiten | Agent quittiert die Frage und leitet zu Themen weiter, bei denen er helfen kann | Behält die Interaktion bei, kann jedoch Besucherinnen und Besucher mit legitimen Off-Topic-Anforderungen frustrieren |
| Übergabe an den Live Agent | Agent-Angebote für die Verbindung des Besuchers mit einem menschlichen Agenten bei Fragen zu anderen Themen | Bestes Kundenerlebnis, erfordert jedoch eine Live Agent-Infrastruktur und Personal. |
| Anmutiger Rückgang mit Ressourcen | Agent erklärt, dass er bei diesem Thema nicht helfen kann und stellt Links zu relevanten Ressourcen oder Support-Kanälen bereit | Ausweichlösung mit geringer Reibung; keine Verfügbarkeit von Live-Agenten erforderlich |

#### Konfigurieren von Brand Governance

**UI-Navigation:** [!DNL Experience Platform] > KI-Assistent > [!DNL Brand Concierge] > Brand Governance

Wichtige Konfigurationsdetails:

- Markenattribute definieren: Markenname, Slogan, Mission, Werte und Persönlichkeitsmerkmale, die den Gesprächston beeinflussen
- Festlegen von Klangparametern: Formalitätsstufe, Humortoleranz, Einfühlungsvermögen und Durchsetzungsvermögen für Produktempfehlungen
- Konfigurieren genehmigter Inhaltsgrenzen: Themen, zu denen der Agent berechtigt ist, sowie Themen, die ausdrücklich verboten sind
- Definieren von Richtlinien für das Antwortformat: maximale Antwortlänge, Verwendung von Listen versus Prosa, Emoji-Richtlinie und Linkformatierung
- Eskalations-Trigger festlegen : Bedingungen, die eine Konversation automatisch an einen Live-Agenten weiterleiten sollen (z. B. Beschwerdeerkennung, wiederholte Unzufriedenheitssignale, hochwertige Kundenidentifizierung)
- Konfigurieren der wettbewerbsorientierten Erwähnungsverarbeitung: Wie der Agent reagieren soll, wenn Besucher nach Produkten von Mitbewerbern fragen
- Haftungsausschluss und rechtliche Hinweise definieren: Obligatorische Offenlegungen für regulierte Branchen

**Dokumentation zu Experience League:**

- [Brand Concierge Brand Governance](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [KI-Assistent - operative Erkenntnisse](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

### Phase 3: Inhaltsintegration

**Anwendungsfunktion:** [!DNL Brand Concierge]: Inhaltsintegration, Konfiguration von Produktberatern, Site Advisory-Konfiguration

Konfigurieren Sie die Inhaltsquellen, die die Gesprächsantworten in korrekten, markenbestätigten Informationen leiten. Dazu gehören die Integration des Produktkatalogs, AEM-Inhaltsverbindungen, Wissensdatenbankimporte und Zeitpläne für die Aktualisierung von Inhalten.

#### Entscheidung: Integrationsmethode für Produktkatalog

Legen Sie fest, wie Produktdaten an Product Advisor Agent bereitgestellt werden sollen. (Nur Optionen A und C)

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| AEP-Datensatzintegration | Der Produktkatalog wird bereits über Quell-Connectoren als Lookup-Datensatz in AEP aufgenommen | Nutzt die vorhandene Dateninfrastruktur, synchronisiert Produktdaten mit Profildaten und erfordert eine grundlegende Datenmodellierung und -erfassung, um den Produktkatalog einzuschließen |
| Direkte Feed-Integration | Der Produktkatalog ist auf einer PIM- oder Commerce-Plattform vorhanden, die einen strukturierten Feed bereitstellen kann | Bietet möglicherweise mehr Echtzeit-Inventar- und Preisdaten; erfordert Feed-Konfiguration und -Planung |
| AEM-Inhaltsintegration | Produktinhalte werden in AEM verwaltet und sollten als maßgebliche Produktdatenquelle dienen | Optimiert für Marken, bei denen AEM der Materialien-Hub ist und die Konsistenz zwischen Web-Inhalten und Gesprächsreaktionen sicherstellt |

#### Entscheidung: Häufigkeit der Inhaltsaktualisierung

Legen Sie fest, wie oft die Inhaltswissensdatenbank des Agenten aktualisiert werden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Echtzeit / nahezu Echtzeit | Häufige Änderungen bei Produktverfügbarkeit, Preisen oder Inhalten (z. B. Flash-Verkäufe, inventarabhängige Einzelhandelsaktivitäten) | Höchste Genauigkeit, aber höhere Infrastrukturlast; kritisch für inventarabhängige Empfehlungen |
| Tägliche Aktualisierung | Inhaltsänderungen sind geplant und geplant (z. B. redaktionelle Kalender, wöchentliche Werbeaktionen) | Gutes Gleichgewicht zwischen Genauigkeit und Leistung; geeignet für die meisten Implementierungen |
| Aktualisierung bei Bedarf | Inhaltsänderungen sind selten und können manuell ausgelöst werden, wenn Aktualisierungen vorgenommen werden | Niedrigster Overhead; geeignet für statische Produktkataloge oder stabile Inhaltswebsites |

#### Konfigurieren von Inhaltsquellen

**UI-Navigation:** [!DNL Experience Platform] > KI-Assistent > [!DNL Brand Concierge] > Inhaltsquellen

Wichtige Konfigurationsdetails:

- Verbinden Sie Produktkatalog-Datenquellen mit der Feldzuordnung für Produktname, Beschreibung, Attribute, Preise, Verfügbarkeit, Bilder und Kategoriehierarchie
- Konfigurieren der Inhaltsindizierung für Website-Seiten, Wissensdatenbank-Artikel, FAQ-Inhalte und Support-Dokumentation
- Festlegen von Grenzen des Inhaltsbereichs, die definieren, auf welche Inhalte der Agent verweisen kann und welche ausgeschlossen sind
- Konfigurieren Sie das Fallback-Verhalten von Inhalten, wenn der Agent für die Beantwortung einer Frage keine relevanten Inhalte finden kann
- Einrichten von Inhaltsqualitätsregeln: Mindestschwellenwert für die Konfidenz von Inhalten für die Aufnahme in Antworten, Zitationsanforderungen und Quellattribution

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Produktberater):**
Konzentrieren Sie sich auf die Produktkatalogintegration mit umfangreicher Produktattributzuordnung. Konfigurieren Sie die Empfehlungslogik von Product Advisor Agent, einschließlich der Anzahl der vorzuschlagenden Produkte, des Umgangs mit nicht vorrätigen Artikeln, der Präsentation von Produktvergleichen und der Integration von Kundenprofildaten (Kaufverlauf, Suchverhalten) in das Empfehlungs-Ranking.

**Für Option B (Site Advisory):**
Konzentration auf die Indizierung von Site-Inhalten mit Seitenhierarchiezuordnung. Konfigurieren Sie die Navigationslogik des Site Advisory-Agenten, einschließlich der Interpretation der Besucherabsicht, der zu priorisierenden Inhaltskategorien, der Handhabung mehrdeutiger Navigationsanfragen und der Anpassung von Vorschlägen basierend auf dem aktuellen Seitenkontext und dem Sitzungsverhalten des Besuchers.

**Für Option C (kombiniert):**
Konfigurieren Sie sowohl Produktkatalog- als auch Site-Inhaltsquellen. Stellen Sie sicher, dass die Content-Routing-Logik Inhalte korrekt der entsprechenden Spezialisierung zuordnet und dass Querverweise zwischen Produktinhalten und Website-Navigationsinhalten ordnungsgemäß zugeordnet sind.

**Dokumentation zu Experience League:**

- [Brand Concierge-Inhaltskonfiguration](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge-Produktberater](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge Site Advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

### Phase 4: Bereitstellung von Erlebnissen im Gespräch

**Anwendungsfunktion:** [!DNL Brand Concierge]: Bereitstellung von Erlebnissen im Gespräch, Verwaltung von Flüssen mit niedrigem Code, Übergabe von Live-Agenten; [!DNL RT-CDP]: Echtzeit-Profilsuche

Stellen Sie das Gesprächserlebnis auf digitalen Zieleigenschaften bereit, einschließlich Kanalkonfiguration, Widget-Anpassung, Profilsuchintegration für die Personalisierung, Regeln für die Übergabe von Live-Agenten und Low-Code-Tools für das laufende Content-Management.

#### Entscheidung: Bereitstellungskanal

Legen Sie fest, für welche Kanäle das Gesprächserlebnis bereitgestellt werden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Web (eingebettetes Widget) | Primäre Web-Eigenschaft ist der wichtigste Kunden-Touchpoint | Häufigster Ausgangspunkt; erfordert [!DNL Web SDK] Integration; unterstützt sowohl anonyme als auch authentifizierte Besucher |
| Mobile App (SDK-Integration) | Die Mobile App ist ein wichtiger Kanal für die Kundeninteraktion | Erfordert [!DNL Mobile SDK] Integration. Berücksichtigen Sie Einschränkungen bei Bildschirmimmobilien für die Konversations-Benutzeroberfläche |
| Benutzerdefinierte SDK-Bereitstellung | Das Gesprächserlebnis muss in ein benutzerdefiniertes Programm, einen Kiosk oder eine nicht standardmäßige digitale Eigenschaft eingebettet werden | Maximale Flexibilität; erfordert mehr Entwicklungsaufwand; geeignet für Kiosks in Geschäften oder proprietäre Plattformen |
| Multi-Channel-Bereitstellung | Erforderliches Gesprächserlebnis über Web-, Mobil- und andere Kanäle gleichzeitig | Höchste Reichweite; erfordert eine konsistente Markenführung über alle Kanäle hinweg; der Konversationskontext sollte möglichst kanalübergreifend bestehen bleiben |

#### Entscheidung: Personalization-Tiefe für Konversationen

Legen Sie fest, wie viele Kundenprofildaten der Agent zum Personalisieren von Konversationen verwenden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur anonym (Sitzungskontext) | Ansatz „Datenschutz zuerst“ oder wenn die meisten Besucher nicht identifiziert werden | Verwendet nur Verhaltenssignale während der Sitzung, keine Profilsuche erforderlich, geeignet für die anonyme Produkterkennung |
| Profil-bewusst (authentifizierte Besucher) | Besucher werden in der Regel angemeldet und erhalten personalisierte Empfehlungen, die auf dem zusätzlichen Verlaufswert basieren | Erfordert Echtzeit-Profilsuche über [!DNL RT-CDP]; deutlich bessere Empfehlungsqualität für bekannte Kunden |
| Progressive Personalisierung | Mischung aus anonymer und authentifizierter Kommunikation mit progressiver Profilerstellung während des Gesprächs | Beginnt mit dem Sitzungskontext; wird angereichert, wenn der Besucher Informationen bereitstellt oder sich authentifiziert; bringt Datenschutz und Personalisierung in Einklang |

#### Entscheidung: Übergabe der Live Agent-Konfiguration

Stellen Sie fest, ob Konversationen auf lebende menschliche Agenten skalierbar sein sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Keine Übergabe (nur Self-Service) | KI-Agent kann alle erwarteten Konversationstypen verarbeiten, oder Live-Agenten sind nicht verfügbar | Einfachste Bereitstellung; kann Besucher mit komplexen Anforderungen frustrieren; geeignet für risikoarme Szenarien mit Produktsuche |
| Regelbasierte Übergabe | Spezifische Trigger sollten an Live-Agenten eskalieren (z. B. Reklamationserkennung, hochwertige Kundenanfrage, komplexe Anfrage) | Vorhersehbares Eskalationsverhalten; erfordert die Definition von Eskalationsregeln und Triggern; erfordert die Integration der Live Agent-Plattform |
| Von einem Besucher angeforderte Übergabe | Besucher können einen Live-Agenten zu einem beliebigen Zeitpunkt im Gespräch anfordern | Bestes Kundenerlebnis; erfordert immer verfügbare Agentenbesetzung oder Warteschlangenverwaltung; Konversationskontext muss übertragen werden |

#### Bereitstellen des Gesprächserlebnisses

**UI-Navigation:** [!DNL Experience Platform] > KI-Assistent > [!DNL Brand Concierge] > Bereitstellung

Wichtige Konfigurationsdetails:

- Konfigurieren Sie das Erscheinungsbild des dialogorientierten Widgets: Position, Farbschema, Avatar, Willkommensnachricht und Interaktionsstil (Text, Stimme oder beides)
- Integration mit [!DNL Web SDK] oder [!DNL Mobile SDK] zur Ereigniserfassung und Profilauflösung
- Konfigurieren Sie die Echtzeit-Profilsuche, um während Konversationen auf Kundenattribute, Segmentzugehörigkeiten und aktuelle Aktivitäten zuzugreifen
- Einrichten der Live-Agent-Übergabeintegration mit der Contact Center-Plattform, einschließlich Context Transfer Protocol, Warteschlangen-Routing und Agent-Benachrichtigung
- Ermöglichen Sie Low-Code-Fluss-Management-Tools für Marketing-Teams, um Konversationsstarter, Werbenachrichten, saisonale Inhalte und Fluss-Varianten ohne Beteiligung von Entwicklern zu aktualisieren
- Persistenzregeln für Konversationssitzungen konfigurieren: Wie lange der Konversationsverlauf aufbewahrt wird, ob Konversationen sitzungsübergreifend fortgesetzt werden können und geräteübergreifende Konversationskontinuität

**Dokumentation zu Experience League:**

- [Brand Concierge-Bereitstellung](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Profil-API-Entitäten-Endpunkt](https://experienceleague.adobe.com/en/docs/experience-platform/profile/api/entities)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Phase 5: Profilanreicherung

**Anwendungsfunktion:** [!DNL Brand Concierge]: Konversative Profilanreicherung; [!DNL RT-CDP]: Profilanreicherung, Zielgruppenbewertung

Konfigurieren Sie die Erfassungs- und Anreicherungs-Pipeline, die Konversationssignale zurück in das einheitliche AEP-Kundenprofil leitet. Dazu gehören die Zuordnung von Konversationsereignissen zu XDM, das Extrahieren von Absichts- und Sentiment-Signalen, das Erstellen berechneter Attribute aus Konversationsdaten und das Erstellen von Zielgruppen basierend auf Konversationsverhalten.

#### Entscheidung: Umfang der Erfassung von Gesprächssignalen

Legen Sie fest, welche Gesprächssignale erfasst und in das Kundenprofil geschrieben werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Core-Interaktionssignale | Minimale Profilanreicherung; Erfassen von Gesprächsbeginn, -ende, -dauer und -abschlussstatus | Niedrigstes Datenvolumen, ausreichend für grundlegende Analysen, begrenzter Personalisierungswert |
| Absichts- und Präferenzsignale | Abgeleitete Produktinteressen, festgelegte Voreinstellungen und Themenkategorien erfassen, die besprochen werden | Hoher Personalisierungswert; mäßiges Datenvolumen; am häufigsten empfohlen |
| Vollständige Signalerfassung | Erfassen von Absichten, Sentiment, Produktinteraktionen, Empfehlungsantworten, Übergabeereignissen und Feedback-Bewertungen | Größte Profilanreicherung; höchstes Datenvolumen; ermöglicht erweiterte Analysen und ML-gesteuerte Personalisierung |

#### Entscheidung: Erstellung einer Audience aus Gesprächsdaten

Legen Sie fest, ob Zielgruppen basierend auf Gesprächsverhalten für die nachgelagerte Aktivierung erstellt werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Keine konversativen Zielgruppen | Konversationsdaten werden nur für Analysen verwendet, nicht für die Aktivierung von Zielgruppen | Einfachster Ansatz; geeignet, wenn Gespräche die bestehenden Interaktionskanäle ergänzen |
| Absichtsbasierte Zielgruppen | Erstellen Sie Zielgruppen basierend auf angegebenen Produktinteressen oder Navigationsabsichten aus Konversationen | Ermöglicht das Retargeting von Besucherinnen und Besuchern, die Interesse bekundet, aber nicht konvertiert haben. Hoher Wert für Commerce |
| Verhaltens-Zielgruppen | Zielgruppen basierend auf Gesprächsinteraktionsmustern erstellen (z. B. hohe Interaktion, Gesprächsabbruch, wiederholte Besuche) | Ermöglicht konversationsinformierte Journey-Orchestrierung und kanalübergreifende Nachverfolgung |

#### Konfigurieren der Profilanreicherung

**UI-Navigation:** [!DNL Experience Platform] > Kunde > Profile > Berechnete Attribute (für abgeleitete Signale); Kunde > Zielgruppen > Zielgruppe erstellen (für Konversationszielgruppen)

Wichtige Konfigurationsdetails:

- Zuordnen von Konversationsereignissen zu XDM ExperienceEvent-Schemafeldern zur Erfassung von Konversations-ID, Nachrichtenanzahl, behandelten Themen, referenzierten Produkten, Sentiment-Bewertungen und Auflösungsstatus
- Konfigurieren [!DNL Brand Concierge] Profilanreicherung, um Absicht- und Präferenzsignale in das einheitliche Profil zu schreiben
- Berechnete Attribute aus Ereignisdaten der Konversation erstellen: Gesamtunterhaltungen (Lebensdauer), Interesse an der dominanten Produktkategorie (30 Tage), durchschnittlicher Sentiment-Wert (90 Tage), Konversionsrate von Konversation zu Kauf
- Definieren Sie Streaming- oder Batch-Zielgruppensegmente basierend auf Gesprächssignalen für die nachgelagerte Aktivierung (z. B. „Besucher, die in den letzten 7 Tagen über Produktkategorie X diskutiert, aber keinen Kauf getätigt haben„)
- Validieren der Profilanreicherung durch Nachschlagen von Beispielprofilen, um zu bestätigen, dass Dialogfeldattribute ausgefüllt werden

**Dokumentation zu Experience League:**

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Phase 6: Analyse und Optimierung

**Anwendungsfunktion:** [!DNL Brand Concierge]: Conversational Analytics

Richten Sie Analytics-Dashboards und -Berichte ein, um die Leistung von konversativen Erlebnissen zu messen, Optimierungsmöglichkeiten zu identifizieren und KPIs zu verfolgen. Dazu gehören [!DNL Brand Concierge] integrierte Analyse, die optionale Integration von [!DNL CJA] für kanalübergreifende Konversationswirkungsanalysen und laufende Optimierungs-Workflows.

#### Entscheidung: Analytics-Tiefe

Bestimmen Sie, welcher Grad von konversativer Analyse erforderlich ist.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Integrierte [!DNL Brand Concierge] Analytics | Standardberichte zu Gesprächsvolumen, Interaktion, Zufriedenheit und Konversion sind ausreichend | Schnellste Aktivierung; deckt Kern-KPIs ab; begrenzte Cross-Channel-Korrelation |
| Integration von [!DNL Brand Concierge] und [!DNL CJA] | Eine Cross-Channel-Analyse ist erforderlich, um zu verstehen, wie Konversationen breitere Kunden-Journey beeinflussen | Erfordert [!DNL CJA] Einrichtung der Verbindung und der Datenansicht; ermöglicht eine Attributionsanalyse über Konversationen und andere Kanäle hinweg |
| Vollständiger Analytics-Stack ([!DNL Brand Concierge] + [!DNL CJA] + benutzerdefinierte Dashboards) | Reporting auf Führungsebene, erweiterte Attributionsmodellierung und benutzerdefinierte Zielgruppenerstellung aus Analytics Insights | Höchste Analysefähigkeit; erfordert [!DNL CJA] Expertise; ermöglicht datengesteuerte Konversationsoptimierung |

#### Konfigurieren von Analysen und Optimierung

**UI-Navigation:** [!DNL Experience Platform] > KI-Assistent > [!DNL Brand Concierge] > Analytics; [!DNL Analytics Platform] > Workspace (für [!DNL CJA])

Wichtige Konfigurationsdetails:

- Überprüfen [!DNL Brand Concierge] integrierten Analyse-Dashboards: Trends des Gesprächsvolumens, Interaktionsrate, Abschlussrate, CSAT-Bewertungen, Akzeptanzrate von Empfehlungen und Häufigkeit der Übergabe
- Konfigurieren Sie [!DNL CJA] Verbindung, um Datensätze mit Konversationsereignissen für eine kanalübergreifende Analyse einzuschließen (bei Auswahl [!DNL CJA] Integration).
- Erstellen Sie [!DNL CJA] Workspace-Analyse für die Attribution von Konversation zu Konversion, um zu ermitteln, welche Konversationsthemen mit dem Kaufverhalten korrelieren
- Einrichten der Überwachung der Konversationsqualität: Verfolgen Sie Themen, bei denen sich der Agent abstrampelt, häufig unbeantwortete Fragen und Sentiment-Trends im Zeitverlauf
- Optimierungs-Workflows definieren: Regelmäßiger Überprüfungsintervall für Brand Governance-Updates, Trigger zur Inhaltsaktualisierung und Verbesserungen des Unterhaltungsflusses auf der Grundlage von Analytics Insights

**Dokumentation zu Experience League:**

- [Brand Concierge Analytics](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Übersicht über CJA Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen oder Bearbeiten einer CJA-Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Erstellen oder Bearbeiten einer CJA-Datenansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)

## Überlegungen bei der Implementierung

In den folgenden Abschnitten werden Leitplanken, häufige Fallstricke, Best Practices und Kompromissentscheidungen behandelt, die bei der Implementierung zu beachten sind.

### Leitplanken und Beschränkungen

- [!DNL Brand Concierge] Konversationserlebnisse unterliegen Beschränkungen der Generierungsrate von KI-Antworten. Die Kapazität gleichzeitiger Konversationen hängt von der Berechtigungsstufe ab
- Die Echtzeit-Profilsuche während Konversationen unterliegt den Profil-API-Ratenbeschränkungen pro Sandbox [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Die Aufnahme von Daten über Konversationsereignisse folgt den standardmäßigen Streaming-Aufnahmebeschränkungen von AEP [Aufnahme-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- Die Größe des Produktkatalogs und das Inhaltsindexvolumen unterliegen [!DNL Brand Concierge] Beschränkungen für die Inhaltsintegration
- Maximal 25 berechnete Attribute pro Sandbox gelten für dialogorientierte Signalaggregationen - [Leitplanken für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Für konversative Zielgruppen gelten maximal 4.000 Segmentdefinitionen pro Sandbox - [Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Häufige Fehler

- **Unzureichende Definition der Marken-Governance:** Bereitstellung ohne gründliche Konfiguration der Marken-Governance führt zu markenfremden Reaktionen, die das Vertrauen der Kunden beschädigen. Investieren Sie vor der Bereitstellung viel Zeit in Phase 2, um Ton, Grenzen und Eskalationsregeln zu definieren.
- **Veraltete Produktkatalogdaten:** Empfehlungen von Produktberatern, die auf veralteten Inventar-, Preis- oder Verfügbarkeitsdaten basieren, frustrieren Kunden und untergraben das Vertrauen. Automatisierte Pipeline zur Aktualisierung von Inhalten mit Validierungsprüfungen einrichten.
- **Überaggressive proaktive Interaktions-Trigger:** Sie Verhaltens-Trigger zu aggressiv festlegen (z. B. eine Konversation nach 3 Sekunden auf der Seite auslösen), verärgert Besuchende und erhöht die Absprungraten. Beginnen Sie mit konservativen Triggern und optimieren Sie sie auf der Grundlage von Interaktionsdaten.
- **Vernachlässigung des anonymen Besuchererlebnisses** Wenn die Personalisierung nur auf authentifizierte Besucher konzentriert wird, wird der Großteil des Traffics ignoriert. Entwerfen Sie Gesprächsflüsse, die anonymen Besuchern einen Wert bieten, indem Sie Verhaltenssignale während der Sitzung verwenden.
- **Konfiguration der Profilanreicherung wird übersprungen** Durch die Bereitstellung von Konversationen ohne Rückerfassung von Signalen an das Profil werden wertvolle Intent- und Präferenzdaten verschwendet. Konfigurieren Sie die Profilanreicherung parallel zur Bereitstellung und nicht im Nachhinein.
- **Ignorieren des Live-Handoff-Erlebnisses für Agenten:** Schlechte Handoff-Erlebnisse (verlorener Kontext, wiederholte Fragen, lange Wartezeiten) beschädigen das gesamte Gesprächserlebnis mehr, als überhaupt keine Handoff-Angebote zu unterbreiten. Testen Sie den gesamten Übergabestrom von Anfang bis Ende, bevor Sie starten.

### Best Practices

- Beginnen Sie mit einer einzigen Agentenspezialisierung (Produktberater oder Site-Beratung) und erweitern Sie diese nach der Festlegung der Grundleistung.
- Abhaltung von Workshops zur Markenverwaltung mit Marketing-, Rechts- und Kundenerlebnis-Stakeholdern vor der Konfiguration von Leitplanken.
- Progressive Personalisierung verwenden: Gespräche mit sitzungskontextbasierten Antworten beginnen und die Personalisierung vertiefen, wenn der Besucher Informationen bereitstellt oder sich authentifiziert.
- Implementieren Sie A/B-Tests von Gesprächsstartern, Eingabeaufforderungen und Empfehlungspräsentationsformaten mit den Low-Code-Fluss-Management-Tools.
- Planen Sie eine regelmäßige (wöchentliche oder zweiwöchentliche) Überprüfung der Konversationsanalyse, um Inhaltslücken, häufige Fehlerpunkte und Optimierungsmöglichkeiten zu identifizieren.
- Erstellen Sie eine Feedback-Schleife zwischen der konversativen Analyse und den Aktualisierungen der Markenführung - verwenden Sie Konversationsdaten, um den Ton zu verfeinern, neue genehmigte Themen hinzuzufügen und Eskalationsregeln anzupassen.
- Überwachen Sie Konversations-Sentiment-Trends als Frühwarnsystem für Produktprobleme, Site-Probleme oder Veränderungen der Markenwahrnehmung.
- Entwerfen Sie Konversationsflüsse, die auf natürliche Weise profilanreichernde Signale erfassen, ohne die Interaktion wie ein Verhör zu fühlen.

### Entscheidungen über Kompromisse

>[!NOTE]
>Die folgenden Entscheidungen sollten auf der Grundlage der spezifischen Anforderungen und Einschränkungen Ihres Unternehmens bewertet werden.

**Konversationspersonalisierungstiefe im Vergleich zu Datenschutz und Einfachheit**

Eine tiefere Profilintegration ermöglicht personalisiertere und effektivere Gespräche, erhöht jedoch die Komplexität der Datenerfassung, die Einverständnisanforderungen und den Aufwand für die Einhaltung von Datenschutzbestimmungen.

- **Tiefe Personalisierung begünstigt:** Höhere Konversionsraten, bessere Empfehlungsqualität, umfangreichere Profilanreicherung und ansprechendere Gespräche für wiederkehrende Kunden
- **Einfachheit des Datenschutzes:** schnellere Bereitstellung, einfachere Einverständnisverwaltung, geringeres Risiko durch Vorschriften und eine Markenpositionierung „Privacy-First“
- **Empfehlung:** Beginnen Sie mit der progressiven Personalisierung, die für anonyme Besucher gut funktioniert und profilbasierte Personalisierung für authentifizierte Sitzungen hinzufügt. Dies bietet einen Mehrwert auf allen Identifizierungsebenen und sorgt gleichzeitig für eine verwaltbare Einhaltung der Datenschutzbestimmungen. Implementieren Sie die Einverständniserfassung für die Erstellung von Profilen im Gespräch, die mit den vorhandenen Einverständnis-Frameworks abgestimmt sind.

**Strenge Markenführung vs. dialogorientierte Natürlichkeit**

Strenge Leitplanken für die Markenführung stellen sicher, dass jede Reaktion mit den Markenstandards übereinstimmt, aber übermäßig starre Einschränkungen sorgen dafür, dass Gespräche sich roboterhaft anfühlen und die Interaktion verringern.

- **Strenge Governance begünstigt:** Markensicherheit, Einhaltung behördlicher Auflagen, konsistentes Messaging und vorhersehbares Agentenverhalten
- **Flexible Governance:** natürlicher Gesprächsfluss, höhere Interaktion, bessere Kundenzufriedenheit und die Möglichkeit, eine breitere Palette von Fragen zu bearbeiten
- **Empfehlung:** Beginnen Sie mit moderater Governance und straffen oder lockern Sie sie basierend auf Konversationsanalysen. Überwachen Sie die Anzahl der Antworten mit „Ich kann dabei nicht helfen“ als Indikator für eine Überrestriktion. Verwenden Sie die Flow Management-Tools mit wenig Code, um schnell und ohne Beteiligung von Entwicklern die Governance-Einstellungen zu durchlaufen.

**Inhaltsaktualisierung in Echtzeit im Vergleich zur Systemleistung**

Die Echtzeit-Inhaltssynchronisierung stellt sicher, dass der Agent immer über aktuelle Produkt- und Inhaltsdaten verfügt, aber eine kontinuierliche Aktualisierung verbraucht mehr Infrastrukturressourcen und kann zu Latenzen führen.

- **Vorteile von Echtzeit-Aktualisierungen:** Genauigkeit für inventarabhängige Empfehlungen, zeitabhängige Promotions und sich schnell ändernde Inhalte
- **Geplante Aktualisierungen:** Systemstabilität, vorhersehbarer Ressourcenverbrauch und niedrigere Infrastrukturkosten
- **Empfehlung:** Verwenden Sie die tägliche Inhaltsaktualisierung als Standard, mit nahezu in Echtzeit stattfindenden Aktualisierungen nur für Bestandsverfügbarkeits- und Preisdaten, die sich wesentlich auf das Kundenerlebnis auswirken. Überwachen Sie die Metriken zur Inhaltsgenauigkeit, um festzustellen, ob die Aktualisierungshäufigkeit angemessen ist.

**Umfassende Signalerfassung vs. Datenverwaltungsaufwand**

Die Erfassung jedes Gesprächssignals bietet die umfassendste Profilanreicherung und -analyse, erhöht jedoch das Datenvolumen, die Speicherkosten und die Komplexität der Governance.

- **Vollständige Signalerfassung bevorzugt:** Erweiterte Analyse, ML-Modellschulung, umfassende Profilanreicherung und maximaler nachgelagerter Personalisierungswert
- **Selektive Erfassung begünstigt** Niedrigere Speicherkosten, einfachere Data Governance, schnellere Profilsuchleistung und einfachere Einhaltung von Datenminimierungsgrundsätzen
- **Empfehlung:** Beginnen Sie mit der Intent- und Präferenzsignalerfassung (im mittleren Bereich) und erweitern Sie die Signalerfassung erst dann auf die vollständige Signalerfassung, nachdem Sie validiert haben, dass die zusätzlichen Daten einen messbaren nachgelagerten Wert erzeugen. Wenden Sie Richtlinien zur Datensatzgültigkeit auf Daten zu Gesprächen an, um das Speicherwachstum zu managen.

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten zusätzliche Informationen zur Implementierung dieses Anwendungsfallmusters.

**[!DNL Brand Concierge]**

- [Übersicht über Brand Concierge](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge-Produktberater](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge Site Advisor](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Überblick über den KI-Assistenten](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [Übersicht über AEP](https://experienceleague.adobe.com/en/docs/experience-platform/landing/home)
- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Datenerfassung und -integration**

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)

**Identität und Profil**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

**Zielgruppen und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

**Data Governance und Datenschutz**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Übersicht über Privacy Service](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Überwachung und Beobachtbarkeit**

- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

**Analysen und Reporting**

- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über CJA Connections](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Übersicht über CJA-Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

**Leitplanken**

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
