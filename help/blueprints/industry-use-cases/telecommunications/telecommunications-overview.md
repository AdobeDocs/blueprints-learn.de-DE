---
title: Telekommunikations-Anwendungsfälle
description: Erfahren Sie, wie Telekommunikationsunternehmen Adobe Experience Platform nutzen, um Abwanderung zu reduzieren, Geräte-Upgrades zu fördern und die Kundeninteraktion zu verbessern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2295'
ht-degree: 1%

---


# Telekommunikations-Anwendungsfälle

Telekommunikationsunternehmen nutzen Adobe Experience Platform, um eine einheitliche Sicht auf jeden Abonnenten zu schaffen und personalisierte Erlebnisse bereitzustellen, die die Abwanderung reduzieren, Planungs- und Geräte-Upgrades erhöhen und langfristige Kundenbeziehungen stärken. Durch die Verbindung von Netznutzungsdaten, Abrechnungsinformationen und Kundeninteraktionen können Telekommunikationsanbieter die Bedürfnisse der Teilnehmer antizipieren und sie zum richtigen Zeitpunkt über ihre bevorzugten Kanäle ansprechen.

## Empfehlungen für Geräte-Upgrades

Ermitteln Sie Kunden, die für Geräte-Upgrades infrage kommen, und präsentieren Sie personalisierte Geräteempfehlungen und Upgrade-Angebote basierend auf Nutzungsmustern und -präferenzen. Durch die Analyse von Vertragslaufzeiten, Gerätealter und individuellem Surfverhalten können Telekommunikationsanbieter jedem Teilnehmer die relevantesten Geräte und Finanzierungsoptionen präsentieren.

### Auswirkung auf den Betrieb

Unternehmen, die Empfehlungen für Geräte-Upgrades implementieren, verzeichnen in der Regel einen Anstieg der Upgrade-Konversionsraten um 30-40 %, indem sie das richtige Angebot zur richtigen Zeit über den bevorzugten Kanal des Kunden bereitstellen.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Upgrade-Journey zu orchestrieren, die die Eignung, Gerätevoreinstellungen und Kanalaffinität jedes Abonnenten bewerten, um personalisierte Upgrade-Angebote für E-Mail, App-Benachrichtigungen und In-Store-Erlebnisse bereitzustellen.

### Technische Überlegungen

- Integrieren Sie Geräte-Inventar- und Preissysteme, um sicherzustellen, dass die Empfehlungen die aktuelle Verfügbarkeit und die Werbepreise widerspiegeln.
- Verbinden Sie Vertragsverwaltungsdaten, um die Upgrade-Eignungsfenster und frühzeitige Upgrade-Angebote genau zu identifizieren.
- Integrieren Sie Telemetrie zur Gerätenutzung (Speicherkapazität, Akkuzustand, Leistungsmetriken), um die Relevanz der Empfehlungen zu erhöhen.
- Koordinieren Sie sich mit Einzelhandels- und E-Commerce-Plattformen, um ein konsistentes Upgrade-Erlebnis über digitale und In-Store-Kanäle hinweg aufrechtzuerhalten.


## Optimierungskampagnen planen

Analysieren Sie die Nutzungsmuster Ihrer Kunden und empfehlen Sie optimale Planänderungen, um Geld zu sparen oder je nach tatsächlichen Anforderungen bessere Funktionen zu erhalten. Durch die proaktive Kontaktaufnahme mit Planempfehlungen wird Vertrauen aufgebaut und das Risiko verringert, dass Abonnentinnen und Abonnenten gegenüber Mitbewerbern mit einfacheren Preisen ausscheiden.

### Auswirkung auf den Betrieb

Kampagnen zur Planoptimierung führen in der Regel zu einer Steigerung der Planänderungsraten um 25-35 %, wodurch die Kundenzufriedenheit verbessert wird, während gleichzeitig der durchschnittliche Umsatz pro Benutzer gesteigert wird, wenn Abonnenten zu Plänen wechseln, die besser zu ihrem Verbrauch passen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um eine Multi-Touch-Kampagne zu erstellen, die Diskrepanzen zwischen Nutzung und Plan erkennt, Abonnentinnen und Abonnenten über bessere Optionen informiert und sie durch den Planänderungsprozess mit zeitnahen Folgemaßnahmen führt.

### Technische Überlegungen

- Nehmen Sie Echtzeit- und historische Nutzungsdaten (Sprachminuten, Datennutzung, internationale Anrufe) auf, um Planabweichungen genau zu identifizieren.
- Verbinden Sie Daten aus dem Abrechnungssystem, um potenzielle Einsparungen oder Funktionsgewinne für jede empfohlene Planänderung zu berechnen.
- Berücksichtigen Sie bei der Erstellung von Planempfehlungen die Preisregeln und vertraglichen Verpflichtungen für Werbeaktionen.
- Integration mit Self-Service-Portalen, damit Abonnentinnen und Abonnenten Planänderungen direkt über Campaign-Touchpoints abschließen können.


## Abwanderungsprävention für hochwertige Kunden

Identifizieren Sie hochwertige Kunden, bei denen das Risiko einer Abwanderung besteht, und interagieren Sie mit personalisierten Aufbewahrungsangeboten und proaktivem Kundenservice. Durch die Kombination von Verhaltenssignalen wie abnehmender Nutzung, wiederholten Service-Aufrufen und wettbewerbsorientiertem Browsen mit Lebenszeitwertdaten können Anbieter eingreifen, bevor ein Abonnent entscheidet zu gehen.

### Auswirkung auf den Betrieb

Programme zur Verhinderung von Abwanderungen, die sich an Abonnentinnen und Abonnenten mit hohem Wert richten, erreichen in der Regel eine Verringerung der Abwanderung um 20-30 %, schützen signifikante wiederkehrende Umsätze und senken die Kosten für die Akquise von Ersatzkunden.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Abwanderungsrisikosignale in Echtzeit zu überwachen, das beste Aufbewahrungsangebot für jeden Abonnenten zu ermitteln und personalisierte Kontaktaufnahme über digitale Kanäle und das Callcenter zu orchestrieren.

### Technische Überlegungen

- Tendenzwerte zur Abwanderung erstellen, indem Nutzungstrends, der Verlauf von Service-Interaktionen und Sentiment-Daten aus Callcenter-Transkripten kombiniert werden.
- Integrieren Sie Callcenter- und Einzelhandelssysteme, damit Kundendienstmitarbeiter Einblick in bereits über digitale Kanäle unterbreitete Aufbewahrungsangebote erhalten.
- Verbinden Sie Daten zu Wettbewerbsinformationen (Port-Out-Anfragen, Vergleiche von Wettbewerbsplänen), um die Risikobewertung und Angebotsstrategien zu verfeinern.
- Legen Sie Governance-Regeln fest, um zu verhindern, dass gefährdete Abonnentinnen und Abonnenten übermäßig kontaktiert werden, was die Abwanderung beschleunigen kann, anstatt sie zu verhindern.


## Onboarding-Journey für neue Kunden

Automatisieren Sie eine personalisierte Onboarding-Journey für neue Kunden mit Begrüßungsinformationen, Anleitungen zur Kontoeinrichtung und Funktions-Tutorials. Ein strukturiertes Onboarding hilft Abonnentinnen und Abonnenten, den vollen Nutzen aus ihrem Plan und ihren Services zu ziehen, und schafft die Grundlage für eine langfristige Bindung.

### Auswirkung auf den Betrieb

Gut konzipierte Onboarding-Journey erhöhen in der Regel die Funktionsaktivierungsraten um 50-60 %, was zu höheren Zufriedenheitswerten und einer geringeren Abwanderung in der Kindheit bei neuen Abonnenten führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um ein sequenzielles Onboarding-Erlebnis zu erstellen, das sich basierend auf dem Plantyp, dem Gerät und der Interaktion jedes Abonnenten mit vorherigen Onboarding-Schritten anpasst.

### Technische Überlegungen

- Integrieren Sie Kontobereitstellungssysteme, um die Onboarding-Journey sofort nach der Aktivierung in Trigger zu nehmen, und passen Sie Inhalte an den spezifischen Plan und das Gerät des Abonnenten an.
- Verbinden Sie App-Interaktionsdaten, um zu verfolgen, welche Funktionen der Abonnent untersucht hat, und passen Sie die nachfolgenden Onboarding-Nachrichten entsprechend an.
- Stimmen Sie sich mit der Support-Plattform des Kunden ab, um sicherzustellen, dass Kundendienstmitarbeiter über die Onboarding-Phase eines Abonnenten informiert sind, wenn sie sich bei Fragen melden.
- Unterstützung mehrerer Onboarding-Pfade für verschiedene Kundensegmente, z. B. einzelne Abonnenten, Familienplanadministratoren und Geschäftskonten.


## Warnhinweise und Empfehlungen zur Datennutzung

Senden Sie personalisierte Warnhinweise, wenn Kunden Datenbeschränkungen erreichen und basierend auf Nutzungsmustern Upgrades oder Daten-Add-ons planen. Rechtzeitige, hilfreiche Benachrichtigungen verwandeln ein potenziell frustrierendes Erlebnis in einen Moment vertrauensbildender Interaktion.

### Auswirkung auf den Betrieb

Proaktive Warnhinweise zur Datennutzung bewirken in der Regel einen Anstieg der Käufe von Add-ons zu Daten um 40-50 %. Gleichzeitig reduzieren sie die Kosten für Schocks und verbessern die Kundenzufriedenheit insgesamt.

### Implementieren

Verwenden Sie das [Ereignisgesteuerte Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um bei Überschreiten von Nutzungsschwellen Echtzeitwarnungen zu senden, mit personalisierten Empfehlungen, die auf den historischen Verbrauchsmustern und Plandetails des Abonnenten basieren.

### Technische Überlegungen

- Stellen Sie eine Verbindung zu Netzwerk-Nutzungsdaten-Feeds her, die nahezu in Echtzeit Verbrauchsaktualisierungen zu Trigger-Warnhinweisen bei aussagekräftigen Schwellenwerten bereitstellen (75 %, 90 %, 100 % der Planzahlen).
- Integrieren Sie Abrechnungs- und Planverwaltungssysteme, um genaue Zusatzpreise anzuzeigen und Einkäufe mit nur einem Fingertipp direkt aus der Warnmeldung zu ermöglichen.
- Berücksichtigen Sie freigegebene Datenpools in Familienplänen, indem Sie sowohl den einzelnen Benutzer als auch den Planadministrator benachrichtigen.
- Implementieren Sie eine Frequenzlimitierung, um eine Warnhinweisermüdung für Abonnentinnen und Abonnenten zu vermeiden, die in jedem Abrechnungszyklus durchgängig hohe Datenmengen verwenden.


## Service-Ausfallbenachrichtigungen

Proaktive Benachrichtigung von Kunden über Service-Ausfälle, Wartungs- oder Netzwerkprobleme in ihrem Bereich mit personalisierten Updates und Kompensationsangeboten. Die Kontaktaufnahme mit Kundinnen und Kunden, bevor diese frustriert sind, zeigt die Verantwortlichkeit und reduziert das Volumen des eingehenden Supports erheblich.

### Auswirkung auf den Betrieb

Proaktive Ausfallbenachrichtigungen erreichen in der Regel eine Benachrichtigungsbestätigungsrate von 60-70 % und reduzieren das Callcenter-Volumen während Service-Unterbrechungen erheblich. Dies senkt die Support-Kosten und verbessert die Wahrnehmung durch den Kunden.

### Implementieren

Verwenden Sie das [Ereignisgesteuerte Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um Netzwerkereignisse zu erkennen und betroffene Abonnentinnen und Abonnenten sofort über ihre bevorzugten Kanäle mit relevanten Details, geschätzten Auflösungszeiten und angemessener Kompensation zu benachrichtigen, falls dies gerechtfertigt ist.

### Technische Überlegungen

- Integration mit netzwerkbetrieblichen Überwachungssystemen, um Echtzeit-Ausfall- und Wartungsereignisdaten mit Informationen über den geografischen Umfang zu erhalten.
- Nutzt die Adressen- und Standortdaten der Abonnenten, um betroffene Kunden genau zu identifizieren und zu vermeiden, dass Kunden außerhalb des betroffenen Gebiets benachrichtigt werden.
- Stellen Sie eine Verbindung zum Abrechnungs- und Gutschriftsystem her, um die Leistungspunktangebote für längere Ausfälle auf der Grundlage des Plans des Abonnenten und der Dauer der Störung zu automatisieren.
- Koordinieren Sie das Messaging über verschiedene Kanäle hinweg, um konsistente Statusaktualisierungen zu bieten und den Versand widersprüchlicher Informationen im Zuge der Entwicklung der Situation zu vermeiden.


## Familienplanverwaltung

Personalisieren Sie die Kommunikation und Angebote für Familienplanadministratoren auf der Grundlage von Familiennutzungsmustern und individuellen Bedürfnissen der Mitglieder. Familienpläne stellen wertvolle mehrzeilige Konten dar, bei denen die Interaktion mit dem Planadministrator die Kundenbindung über alle Linien hinweg vorantreibt.

### Auswirkung auf den Betrieb

Personalisierte Mitteilungen über die Verwaltung von Familienplänen erhöhen die Interaktion mit Familienplänen in der Regel um 30-40 %, was zu einer höheren Leitungsbindung und einem höheren Lebensdauerwert pro Konto führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um die Nutzung durch alle Familienmitglieder zu analysieren, Möglichkeiten wie das Hinzufügen von Zeilen oder die Anpassung individueller Limits zu identifizieren und dem Planadministrator maßgeschneiderte Empfehlungen zu geben.

### Technische Überlegungen

- Modellieren Sie Familienkontenhierarchien, um zwischen Planadministrator und einzelnen Mitgliedern zu unterscheiden, wobei die Berechtigungsebenen für Kommunikationen und Kontoänderungen zu beachten sind.
- Aggregieren Sie Nutzungsdaten über alle Kontozeilen hinweg, um Muster und Möglichkeiten auf Familienebene zu identifizieren, z. B. nicht ausgelastete freigegebene Daten oder unregelmäßige Geräte-Upgrade-Zyklen.
- Integration von Kindersicherung und Inhaltsfiltersystemen zur Unterstützung familienspezifischer Funktionen bei der Personalisierung.
- Stellen Sie sicher, dass Datenschutzkontrollen vorhanden sind, sodass individuelle Nutzungsdetails auf der Grundlage von Kontoberechtigungen ordnungsgemäß mit dem Planadministrator geteilt werden.


## 5G-Upgrade-Kampagnen

Kunden, die für 5G-Netzaktualisierungen infrage kommen, erhalten auf der Grundlage ihres Standorts und ihrer Nutzungsmuster personalisierte Angebote und Vorteile. Mit zunehmender 5G-Abdeckung beschleunigt die Anbindung von Abonnentinnen und Abonnenten in neu abgedeckten Gebieten mit relevanter Nachrichtenübermittlung die Akzeptanz und erhöht die Netzauslastung.

### Auswirkung auf den Betrieb

Gezielte 5G-Upgrade-Kampagnen führen in der Regel zu einem Anstieg der 5G-Akzeptanzraten bei den geeigneten Abonnenten um 25-35 %, was die Rendite von Netzinvestitionen und die Wettbewerbsdifferenzierung unterstützt.

### Implementieren

Verwenden Sie das [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)-Muster, um Abonnentinnen und Abonnenten auf der Grundlage der Verfügbarkeit der 5G-Abdeckung, der Gerätekompatibilität und der Planeignung zu segmentieren, und führen Sie dann personalisierte Upgrade-Kampagnen durch, die die Vorteile hervorheben, die für das Nutzungsprofil der einzelnen Abonnentinnen und Abonnenten am relevantesten sind.

### Technische Überlegungen

- Netzabdeckungskarten integrieren, um Abonnenten in Gebieten mit aktiven 5G-Diensten genau zu identifizieren und Upgrades zu vermeiden, in denen die Abdeckung noch nicht verfügbar ist.
- Verbinden Sie Gerätekompatibilitätsdaten, um zu bestimmen, welche Abonnenten ein neues Gerät benötigen, im Vergleich zu denen, die bereits über 5G-fähige Hardware verfügen.
- Abstimmung mit Einzelhandelsinventarsystemen, um sicherzustellen, dass beworbene Geräte und Pläne im bevorzugten Geschäft des Abonnenten oder online verfügbar sind.
- Segmentieren Sie das Messaging nach Nutzungsprofil, sodass Benutzer mit umfangreichen Datenmengen leistungsorientierte Vorteile erhalten, während gelegentliche Benutzer Nachrichten zur Abdeckung und Zuverlässigkeit erhalten.


## Erinnerungen für Rechnungszahlungen

Senden Sie personalisierte Erinnerungen zu Rechnungszahlungen über bevorzugte Kanäle mit Zahlungsoptionen und Kontostandsinformationen. Pünktliche, praktische Erinnerungen reduzieren Zahlungsverzug und damit verbundene Inkassokosten und halten die Kundenbeziehung positiv.

### Auswirkung auf den Betrieb

Personalisierte Erinnerungen zu Rechnungszahlungen verbessern in der Regel die pünktlichen Zahlungsraten um 20-30 %, reduzieren die Inkassokosten und minimieren Service-Aussetzungen, die die Kundenzufriedenheit erhöhen.

### Implementieren

Verwenden Sie [&#x200B; Muster „Ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md), um Erinnerungen zu optimalen Zeiten vor dem Fälligkeitsdatum zu senden, die mit dem Kontostand des Abonnenten, der bevorzugten Zahlungsmethode und einem direkten Link personalisiert sind, um die Zahlung abzuschließen.

### Technische Überlegungen

- Integration mit der Abrechnungsplattform für Zugriff auf Echtzeit-Kontostände, Fälligkeitsdaten und den Zahlungsverlauf für genaue Erinnerungsinhalte.
- Verbinden Sie sich mit Zahlungsverarbeitungssystemen, um eine Zahlung mit einem Tippen oder einem Klick direkt aus der Erinnerungsnachricht zu ermöglichen.
- Implementieren Sie eine Eskalationslogik, die die Dringlichkeit und Häufigkeit von Erinnerungen an den Fälligkeitszeitpunkt anpasst und dabei die Kommunikationsvoreinstellungen berücksichtigt.
- Unterstützen Sie mehrere Zahlungsmethoden (automatische Registrierung, digitale Brieftasche, Banküberweisung) und personalisieren Sie die präsentierten Optionen basierend auf der Historie des Abonnenten.


## Add-on-Service-Empfehlungen

Empfehlen Sie relevante Add-on-Services wie Geräteversicherung, Cloud-Speicher und Streaming-Pakete basierend auf dem Plan, der Verwendung und den Voreinstellungen des Kunden. Kontextuelle Empfehlungen steigern den Wert, den Abonnentinnen und Abonnenten aus ihrer Beziehung zum Anbieter erhalten, während der durchschnittliche Umsatz pro Benutzerin bzw. Benutzer steigt.

### Auswirkung auf den Betrieb

Personalisierte Add-on-Service-Empfehlungen steigern in der Regel die Akzeptanzraten von Add-ons um 15-25 % und erhöhen damit den Umsatz aus dem bestehenden Abonnentenstamm, ohne dass Kosten für die Akquise neuer Kunden anfallen.

### Implementieren

Verwenden Sie das [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)-Muster, um das Profil, die aktuellen Services und die Verhaltenssignale jedes Abonnenten zu bewerten, um das relevanteste Add-on-Angebot zu ermitteln und es über den optimalen Kanal und Zeitpunkt darzustellen.

### Technische Überlegungen

- Stellen Sie eine Verbindung zum aktuellen Servicekatalog des Abonnenten her, um zu vermeiden, ihm bereits vorhandene Services zu empfehlen, und um natürliche Ergänzungen zu seinem bestehenden Plan zu identifizieren.
- Integrieren Sie Partner- und Drittanbieterdaten (Streaming-Anbieter, Versicherungsträger), um genaue Preise und gebündelte Angebote zu präsentieren.
- Verwenden Sie Geräte- und Nutzungsdaten, um Empfehlungen zu formulieren, z. B. Vorschläge für eine Geräteversicherung für Abonnenten mit neuen Premium-Geräten oder Cloud-Speicher für diejenigen, denen der Gerätespeicher ausgeht.
- Koordinieren Sie sich mit In-App- und Web-Personalisierung, um Add-on-Empfehlungen für Self-Service-Touchpoints zu verstärken.


## Netzwerkleistung Personalization

Personalisieren Sie Informationen und Empfehlungen zur Netzwerkleistung basierend auf dem Standort, dem Gerät und den Nutzungsmustern des Kunden. Abonnentinnen und Abonnenten dabei zu unterstützen, ihre Konnektivität zu optimieren, schafft Vertrauen und reduziert die Support-Kontakte, die mit Leistungsproblemen verbunden sind.

### Auswirkung auf den Betrieb

Personalisierte Erlebnisse mit Netzwerkleistung steigern in der Regel die Interaktion mit Mobile Apps um 35-45 %, wenn Abonnentinnen und Abonnenten zurückkehren, um die Abdeckung zu überprüfen, Probleme zu beheben und Optimierungstipps zu finden, die auf ihre Situation zugeschnitten sind.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um personalisierte Dashboards zur Netzwerkleistung, Informationen zur Abdeckung und Optimierungsempfehlungen für das App- und Web-Kontoerlebnis des Abonnenten bereitzustellen.

### Technische Überlegungen

- Integrieren Sie Netzwerkqualitätsmetriken und Abdeckungsdaten, um standortspezifische Leistungsinformationen bereitzustellen, die für das Zuhause, die Arbeit und die häufig besuchten Bereiche der Abonnenten relevant sind.
- Schließen Sie Gerätediagnosedaten an, um maßgeschneiderte Empfehlungen zur Fehlerbehebung auf der Grundlage des spezifischen Gerätemodells und der Softwareversion des Abonnenten anzubieten.
- Verwenden Sie [!DNL Adobe Experience Platform] Edge-Services, um Personalisierung mit niedriger Latenz innerhalb des App-Erlebnisses bereitzustellen, ohne die Leistung zu beeinträchtigen.
- Implementieren Sie Feedback-Schleifen, damit Abonnentinnen und Abonnenten Probleme mit der Abdeckung melden können, wobei die Netzwerkdaten angereichert werden und gleichzeitig Reaktionen auf ihr Erlebnis gezeigt werden.


## Interaktion mit Treueprogrammen

Personalisieren Sie die Kommunikation, Prämien und Angebote im Rahmen des Treueprogramms auf der Grundlage der Stufe, des Punktesaldos und des Einlösungsverlaufs des Kunden. Ein gut personalisiertes Treueerlebnis stärkt die emotionale Bindung zur Marke und verursacht über die Vertragsbedingungen hinaus aussagekräftige Wechselkosten.

### Auswirkung auf den Betrieb

Personalisierte Interaktion mit Treueprogrammen erhöht in der Regel die Programmteilnahme und die Prämieneinlösung um 30-40 %, was zu höheren Kundenbindungsraten bei registrierten Abonnenten führt.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um personalisierte Treuekommunikation zu orchestrieren, die relevante Belohnungen hervorheben, Abonnentinnen und Abonnenten über den Fortschritt der Stufe informieren und Einlösungsmöglichkeiten präsentieren, die an ihren Präferenzen und Verhaltensweisen ausgerichtet sind.

### Technische Überlegungen

- Integrieren Sie die Treueplattform für den Zugriff auf Echtzeit-Punktestände, den Stufenstatus und den Einlösungsverlauf, um eine präzise Personalisierung zu ermöglichen.
- Verbinden Sie Partnerprämienkataloge, um eine breite Palette von Einlösungsoptionen zu präsentieren, die auf die demonstrierten Interessen und früheren Einlösungen jedes Abonnenten zugeschnitten sind.
- Koordinieren Sie Treuemeldungen mit anderen Campaign-Journey, um sicherzustellen, dass Bindungsangebote und Treueprämien sich ergänzen und nicht miteinander in Konflikt geraten.
- Unterstützen Sie Stufen-Progressionstreiber, indem Sie berechnen, wie nah ein Abonnent der nächsten Stufe ist, und umsetzbare Schritte vorstellen, um sie zu erreichen.
