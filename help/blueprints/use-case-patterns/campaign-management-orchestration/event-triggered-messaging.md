---
title: Ereignisausgelöstes Messaging
description: Erfahren Sie, wie Sie kontextbezogene Echtzeit-Nachrichten als Reaktion auf Verhaltens- oder Systemereignisse versenden können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 5%

---

# Ereignisausgelöstes Messaging

In diesem Handbuch wird das Anwendungsfallmuster für ereignisgesteuertes Messaging beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP) verwendet werden, um kontextuelle Echtzeitnachrichten als Reaktion auf Verhaltens- oder Systemereignisse bereitzustellen. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Dieses Muster deckt den gesamten Lebenszyklus von der Ereignisaufnahme und Journey-Erstellung bis hin zum Nachrichtenversand und Leistungsberichten ab.

## Anwendungsfallmuster

In diesem Abschnitt werden das Kernmuster und der Ausführungsplan beschrieben, die das ereignisgesteuerte Messaging unterstützen.

**Ereignisausgelöstes Messaging**

Achten Sie auf ein Echtzeit-Verhaltens- oder Systemereignis und senden Sie dann eine kontextuelle Nachricht an das auslösende Profil.

**Ausführungsplan:** Ereignisaufnahme > Journey-Eintrag > Bedingungsauswertung > Nachrichtenversand > Berichterstellung

## Anwendungsfall - Übersicht

Ereignisausgelöstes Messaging liefert eine kontextuelle Nachricht als Reaktion auf ein Echtzeit-Verhaltens- oder Systemereignis. Im Gegensatz zur Aktivierung ausgehender Batch-Nachrichten, die zu einem bestimmten Zeitpunkt an eine vorausgewertete Audience gesendet wird, überwacht dieses Muster ein qualifizierendes Ereignis, z. B. einen Warenkorbabbruch, eine Durchsuchsitzung, eine Formularübermittlung oder eine Systemstatusänderung, und gibt das auslösende Profil sofort auf eine Journey ein, die die Bedingungen auswertet und eine Nachricht sendet.

Das Muster basiert auf dem Echtzeit-Ereignis-Streaming in AEP (über Web SDK, Mobile SDK oder serverseitige API), einer Journey mit einem unitären Ereigniseintrag in AJO und einer Bedingungsauswertungslogik, die bestimmt, ob und was gesendet wird. Die Nachricht wird normalerweise innerhalb von Minuten nach dem auslösenden Ereignis gesendet, was dieses Muster ideal für zeitabhängige, kontextuell relevante Nachrichten macht.

Unternehmen verwenden dieses Muster, um auf Kundenaktionen in Echtzeit zu reagieren, wodurch die Relevanz steigt und im Vergleich zur geplanten Batch-Kommunikation höhere Interaktions- und Konversionsraten erzielt werden. Häufige Szenarien sind die Wiederherstellung bei Transaktionsabbruch, die Nachverfolgung nach dem Kauf, Willkommensnachrichten nach der Registrierung und zeitkritische Benachrichtigungen wie Zahlungsausfälle oder Warnhinweise bei Preisrückgängen.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Wiederherstellen von Transaktionsabbrüchen und Journey](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Erneutes Ansprechen von Benutzern, die während des Kaufs, der Bewerbung oder der Registrierung abgebrochen sind, durch zeitnahe, personalisierte Folgemaßnahmen.

| KPIs |
| --- |
| Konversionsraten, inkrementeller Umsatz, Interaktion |

**[Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbessern Sie den Prozentsatz der Besucher und Interessenten, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen.

| KPIs |
| --- |
| Konversionsraten, Lead-Konversion, Kosten pro Lead |

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.

| KPIs |
| --- |
| Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT) |

**[Verbessern des Kunden-Onboarding](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Verkürzen Sie die Amortisierungszeit für neue Kunden mit optimierten, personalisierten Willkommens- und Aktivierungs-Journey.

| KPIs |
| --- |
| Interaktion, Kundenbindung, Konversionsraten |

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie ereignisgesteuertes Messaging auf verschiedene Geschäftskontexte angewendet werden kann.

- **E-Mail oder SMS zu Warenkorbabbruch** - Senden Sie eine Erinnerungsnachricht, wenn ein Kunde Artikel zu seinem Warenkorb hinzufügt, den Kauf jedoch nicht innerhalb eines bestimmten Zeitfensters abschließt
- **Follow-up bei Abbruch durchsuchen** - Erneutes Ansprechen von Besucherinnen und Besuchern, die Produkte oder Inhalte angesehen, aber keine Konversionsaktion durchgeführt haben
- **Dankeschön oder Crosssell nach dem Kauf** — Geben Sie sofort nach einem Kaufereignis eine Bestätigung und eine Crosssell-Empfehlung ab
- **Testablauf-Erinnerung** - Benachrichtigen Sie Benutzer, die sich dem Ende einer kostenlosen Testversion nähern, mit einer Nachricht zur Verlängerung oder Konversion
- **Willkommensnachricht nach der Registrierung** - Senden Sie eine sofortige Onboarding-Nachricht, wenn sich ein neuer Benutzer registriert oder ein Konto erstellt
- **Formularübermittlungsbestätigung** - Bestätigt Formularübermittlungen (Kontaktanfragen, Bewerbungen, Registrierungen) mit einer kontextuellen Bestätigung
- **Benachrichtigung bei Zahlungsausfällen** — Benachrichtigung der Kunden, wenn eine wiederkehrende Zahlung fehlschlägt, und Aufforderung, die Zahlungsinformationen zu aktualisieren
- **App-Deinstallation einer Win-Back-Push-Benachrichtigung** - Trigger erhält eine Win-back-Nachricht, wenn ein Benutzer eine Mobile App deinstalliert
- **Buchung oder Terminbestätigung** — Senden Sie sofort eine Bestätigung, nachdem eine Buchung, Reservierung oder ein Termin geplant ist
- **Warnhinweis bei Preisverfall für Artikel auf der Wunschliste** - Benachrichtigen Sie Kunden, wenn ein Produkt auf ihrer Wunschliste im Preis sinkt

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität von ereignisgesteuerten Messaging-Implementierungen gemessen werden.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Konversionsrate | Prozentsatz der ausgelösten Nachrichtenempfänger, die die gewünschte Aktion abgeschlossen haben (Kauf, Anmeldung, Verlängerung) | Konversionen/Zugestellte Nachrichten * 100 |
| Inkrementeller Umsatz | Zusätzliche Einnahmen, die durch ereignisgesteuerte Nachrichten im Vergleich zu Kontrollgruppen ohne Versand erzielt werden können | Umsatz aus ausgelösten Sendungen - Baseline der Kontrollgruppe |
| Öffnungsrate | Prozentsatz der zugestellten Nachrichten, die von Empfängern geöffnet wurden | Öffnungen/Geliefert * 100 |
| Clickthrough-Rate (CTR) | Prozentsatz der zugestellten Nachrichten, die mindestens einen Klick generiert haben | Klicks/Zugestellt * 100 |
| Zeit bis zur Konversion | Durchschnittliche Zeit zwischen Nachrichtenversand und Konversionsereignis | AVG(Konversions-Zeitstempel - Versand-Zeitstempel) |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die die Journey betreten und den Nachrichtenversand-Schritt erreichen (nicht durch Bedingungen oder Ausstiege verworfen) | Profile, die den Versand erreichen / Profile, die in den Journey eintreten * 100 |
| Unterdrückungsrate der Nachricht | Prozentsatz der qualifizierten Profile, die aufgrund von Häufigkeitsbegrenzungen, Einverständnis oder Bedingungsauswertung unterdrückt wurden | Unterdrückte Profile/Gesamtzahl der qualifizierten Profile * 100 |
| Bounce-Rate | Prozentsatz der Nachrichten, die aufgrund von Hard- oder Softbounces nicht zugestellt werden konnten | Bounces/Gesendet * 100 |

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer](AJO)** - Journey-Orchestrierung mit unitärer Ereigniseingabe, Bedingungsauswertung, Warteschritten, Nachrichtenbearbeitung, Kanalkonfiguration, Frequenzverwaltung und Versandberichten
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** - Zielgruppenbewertung für bedingungsbasierte Filterung innerhalb von Journeys, Durchsetzung von Einverständnis und Governance, Profilanreicherung
- **[!DNL Adobe Experience Platform](AEP)** - Echtzeit-Ereignisaufnahme über Web SDK, Mobile SDK oder Server-seitige API; Datenmodellierung; Identitätsauflösung; Edge Network

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in dieser Implementierung verwendeten Funktionen.

### Journey-Orchestrierung

- [Erste Schritte mit Journeys](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Erstellen einer SMS-Nachricht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Gestalten einer Push-Benachrichtigung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Häufigkeits- und Geschäftsregeln

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Begrenzungs-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Konflikt- und Prioritätenmanagement

- [Erste Schritte mit Konflikt- und Prioritätsverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Reporting und Leistung

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Datenerfassung und -aufnahme

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über die Streaming-Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Datenmodellierung und Schemata

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentierung und Audiences

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Berechnete Attribute

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Überwachung und Beobachtbarkeit

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorials und Handbücher

- [Journey-Tutorial erstellen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
