---
title: Mehrstufige orchestrierte Journey
description: Erfahren Sie, wie Sie ein Profil durch einen verzweigten Multi-Touch-Journey mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen im Laufe der Zeit führen.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 5%

---

# Mehrstufige orchestrierte Journey

In diesem Handbuch wird das mehrstufige Anwendungsfallmuster für orchestrierte Journey beschrieben, bei dem [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Real-Time Customer Data Platform] (RT-CDP) verwendet werden, um verzweigte Multi-Touch-Journey-Kundinnen und -Kunden zu orchestrieren, die im Laufe der Zeit mehrere Nachrichten senden. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

## Anwendungsfallmuster

**Mehrstufige orchestrierte Journey**

Führen Sie ein Profil durch einen verzweigenden Multi-Touch-Journey mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen im Laufe der Zeit.

**Ausführungsplan:** Zielgruppenauswertung > Journey-Ausführung (mehrere Knoten) > Bedingungsverzweigung > Nachrichtenversand (xN) > Beendigungskriterien > Berichte

## Anwendungsfall - Übersicht

Mehrstufige orchestrierte Journey befassen sich mit Geschäftsszenarien, in denen eine einzige Nachricht nicht ausreicht, um das gewünschte Kundenergebnis zu erzielen. Anstelle eines einmaligen Versands führt der Journey jedes Profil durch eine Sequenz von Touchpoints - E-Mails, SMS-Nachrichten, Push-Benachrichtigungen oder In-App-Nachrichten - im Abstand von Tagen oder Wochen, mit einer Verzweigungslogik, die den Pfad basierend auf Profilattributen, Verhaltenssignalen oder Ereignisdaten anpasst.

Diese Journey sind die komplexesten Kampagnenmuster in AJO. Sie kombinieren zielgruppen- oder ereignisbasierte Eingabe mit einer Arbeitsfläche aus Aktionsknoten (Nachrichten), Bedingungsknoten (Verzweigungslogik), Warteknoten (Zeitverzögerungen) und Beendigungskriterien (Konversionsereignisse oder Zeitüberschreitungen). Jedes Profil durchläuft die Journey unabhängig in seinem eigenen Tempo und erhält bei jedem Schritt kontextbezogene Inhalte.

Dieses Muster fasst die einfacheren Muster zusammen - Aktivierung ausgehender Batch-Nachrichten für Kampagnen mit einem Versand und ereignisausgelöstes Messaging für Antworten mit einem Ereignis. Verwenden Sie dieses Muster, wenn der Anwendungsfall die Pflege eines Profils durch mehrere Interaktionen im Laufe der Zeit erfordert.

>[!NOTE]
>Wenn für Ihren Journey eine dynamische Auswahl des optimalen Angebots, Inhalts oder Kanals an einzelnen Entscheidungspunkten erforderlich ist, finden Sie weitere Informationen unter [Kanalübergreifendes Journey mit Entscheidungsfindung](cross-channel-journey-with-decisioning.md). Dieses Muster erweitert dieses mit der AJO Decisioning-Integration.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Verbesserung der Kundenbindung

Halten Sie bestehende Kundinnen und Kunden durch wertorientierte Erlebnisse und kontinuierliche Pflege von Beziehungen in Kontakt und erneuern Sie diese.

**KPIs:**, Kundenlebenszeitwert, Interaktion

[Weitere Informationen zur Verbesserung der Kundenbindung](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Verbessern des Kunden-Onboarding

Verkürzen Sie die Amortisierungszeit für neue Kunden mit optimierten, personalisierten Willkommens- und Aktivierungs-Journey.

**KPIs:** Interaktion, Kundenbindung, Konversionsraten

[Weitere Informationen zur Verbesserung des Onboarding von Kunden](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Erneute Interaktion mit inaktiven Kunden

Gewinnen Sie inaktive oder abgelaufene Kunden mit zielgerichteten Reaktivierungskampagnen zurück, die auf Verhaltenssignalen basieren.

**KPIs:** Interaktion, Kundenbindung, Konversionsraten

[Weitere Informationen zur Verbesserung der Kundenbindung](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Wiederherstellen von Transaktionsabbrüchen und Journey

Erneutes Ansprechen von Benutzern, die während des Kaufs, der Bewerbung oder der Registrierung abgebrochen sind, durch zeitnahe, personalisierte Folgemaßnahmen.

**KPIs:** Konversionsraten, inkrementeller Umsatz, Interaktion

[Erfahren Sie mehr über die Wiederherstellung von Transaktionsabbrüchen und Journey](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen gängige Anwendungen des mehrstufigen orchestrierten Journey-Musters.

- **Onboarding-Serie** - Willkommens-E-Mail, gefolgt von Funktionsschulung und einer Aktivierungsaufforderung in den ersten 14 Tagen nach der Registrierung
- **Drip-Kampagne zur erneuten Interaktion** - eine Erinnerungs-E-Mail, dann ein Incentive-Angebot und schließlich eine letzte Benachrichtigung für abgelaufene Kundinnen und Kunden über einen Zeitraum von drei Wochen
- **Meilenstein-Journey zum Treueprogramm** - Benachrichtigung zur Aktualisierung der Stufe, gefolgt von einem Exklusivangebot und einer Verlängerungserinnerung zum bevorstehenden Mitgliedschaftsjubiläum
- **Win-Back-Sequenz** - E-Mail „Wir vermissen Sie“, dann ein Rabattangebot per E-Mail, dann eine abschließende SMS-Erinnerung für abgelaufene Käufer
- **Journey zur Produktakzeptanz** - Testwillkommen, Tipps zur Nutzung und eine Upgrade-Eingabeaufforderung im Verlauf des Testzeitraums
- **Sequenz der Abonnementverlängerung** - 30-Tage-Benachrichtigung, 7-Tage-Erinnerung, dann eine Nachricht zum Ablauf des Tages für bevorstehende Abonnementverlängerungen
- **Pflege nach dem Kauf** - Dankeschön-E-Mail, Benutzerhandbuch, Crosssell-Empfehlung und eine Überprüfungsanfrage über 30 Tage nach dem Kauf

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität Ihrer mehrstufigen orchestrierten Journey-Implementierung zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die das vollständige Journey ohne vorzeitiges Beenden abschließen | Journey-Bericht: Beendet (abgeschlossen)/Eingetreten |
| Schrittkonversionsrate | Prozentsatz der Profile, die von einem Schritt zum nächsten wechseln | Metriken pro Knoten im Journey-Bericht |
| Kanalinteraktionsrate | Öffnungsraten, Clickthrough-Raten und Reaktionsraten an jedem Touchpoint | Versand- und Interaktionsmetriken pro Nachricht |
| Konversionsrate der Ausstiegskriterien | Prozentualer Anteil der Profile, die vor dem Journey-Timeout den Trigger des Beendigungsereignisses (z. B. Kauf, Anmeldung) vornehmen | Ausstiegskriterien Trefferanzahl / Gesamtzahl eingegeben |
| Zeit bis zur Konversion | Durchschnittliche Dauer vom Journey-Eintritts- zum Ausstiegskriterienereignis | Journey Analytics: Zeitstempel des Eintrags zum Konversionsereignis-Zeitstempel |
| Journey-Abfallrate | Prozentsatz der Profile, die bei jedem Schritt nicht mehr interagieren (Fallout-Analyse) | CJA Fallout-Visualisierung über Journey-Schritte hinweg |
| Bindungsgrad/Rückgewinnungsrate | Prozentsatz der Zielgruppenprofile, die zum aktiven Status zurückkehren | Verhaltensanalyse nach dem Journey in CJA |

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Journey-Orchestrierungs-Engine, Nachrichtenbearbeitung, Kanalkonfiguration, Inhaltsexperiment, Häufigkeit und Konfliktmanagement sowie Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung und -definition für Journey-Einstiegs-Zielgruppen, Profildaten für die Personalisierung und Bedingungsverzweigung
- **[!DNL Adobe Experience Platform] (AEP)** - Profilspeicher, Identity Service, Ereignisdatenaufnahme und grundlegende Dateninfrastruktur

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in dieser Implementierung verwendeten Funktionen.

### Journeys

- [Erste Schritte mit Journeys](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Journeys testen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Journey-Aktivitäten

- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Endaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Konfigurieren einer benutzerdefinierten Aktion](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Einreise- und Ausreiseverwaltung

- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Verwenden von Inhaltskomponenten von Email Designer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Inhaltsexperiment

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische Berechnungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Häufigkeit, Konflikt und Priorität

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Erste Schritte mit Konflikt- und Prioritätsverwaltung](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioritätswerte](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/api/edge-segmentation)

### Reporting und Analysen

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)

### Einverständnis und Governance

- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Datengrundlage

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)
