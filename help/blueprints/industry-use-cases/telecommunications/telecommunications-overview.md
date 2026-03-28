---
title: Telekommunikations-Anwendungsfälle
description: Erfahren Sie, wie Telekommunikationsunternehmen Adobe Experience Platform nutzen, um Abwanderung zu reduzieren, Geräte-Upgrades zu fördern und die Kundeninteraktion zu verbessern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 653632f0-81be-435c-a703-56c5bc132794
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '3533'
ht-degree: 0%

---

# Telekommunikations-Anwendungsfälle

Telekommunikationsunternehmen nutzen Adobe Experience Platform, um eine einheitliche Sicht auf jeden Abonnenten zu schaffen und personalisierte Erlebnisse bereitzustellen, die die Abwanderung reduzieren, Planungs- und Geräte-Upgrades erhöhen und langfristige Kundenbeziehungen stärken. Durch die Verbindung von Netznutzungsdaten, Abrechnungsinformationen und Kundeninteraktionen können Telekommunikationsanbieter die Bedürfnisse der Teilnehmer antizipieren und sie zum richtigen Zeitpunkt über ihre bevorzugten Kanäle ansprechen.

## Empfehlungen für Geräte-Upgrades

Ermitteln Sie Kunden, die für Geräte-Upgrades infrage kommen, und präsentieren Sie personalisierte Geräteempfehlungen und Upgrade-Angebote basierend auf Nutzungsmustern und -präferenzen. Durch die Analyse von Vertragslaufzeiten, Gerätealter und individuellem Surfverhalten können Telekommunikationsanbieter jedem Teilnehmer die relevantesten Geräte und Finanzierungsoptionen präsentieren.

### Auswirkung auf den Betrieb

Unternehmen, die Empfehlungen für Geräte-Upgrades implementieren, erzielen höhere Upgrade-Konversionsraten, indem sie über den bevorzugten Kanal des Kunden zur richtigen Zeit das richtige Angebot bereitstellen.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Upgrade-Journey zu orchestrieren, die die Eignung, Gerätevoreinstellungen und Kanalaffinität jedes Abonnenten bewerten, um personalisierte Upgrade-Angebote für E-Mail, App-Benachrichtigungen und In-Store-Erlebnisse bereitzustellen. Dies ist das richtige Muster, wenn bei der Angebotsauswahl die Geräteeignungsfenster, Kanalvoreinstellungen und Bestandsbeschränkungen berücksichtigt werden müssen - Einschränkungen, die eine geregelte Entscheidungslogik erfordern, anstatt nur einfache Verhaltensempfehlungen zu geben.

### Technische Überlegungen

- Integrieren Sie Geräte-Inventar- und Preissysteme, um sicherzustellen, dass die Empfehlungen die aktuelle Verfügbarkeit und die Werbepreise widerspiegeln.
- Verbinden Sie Vertragsverwaltungsdaten, um die Upgrade-Eignungsfenster und frühzeitige Upgrade-Angebote genau zu identifizieren.
- Integrieren Sie Telemetrie zur Gerätenutzung (Speicherkapazität, Akkuzustand, Leistungsmetriken), um die Relevanz der Empfehlungen zu erhöhen.
- Koordinieren Sie sich mit Einzelhandels- und E-Commerce-Plattformen, um ein konsistentes Upgrade-Erlebnis über digitale und In-Store-Kanäle hinweg aufrechtzuerhalten.


## Optimierungskampagnen planen

Analysieren Sie die Nutzungsmuster Ihrer Kunden und empfehlen Sie optimale Planänderungen, um Geld zu sparen oder je nach tatsächlichen Anforderungen bessere Funktionen zu erhalten. Durch die proaktive Kontaktaufnahme mit Planempfehlungen wird Vertrauen aufgebaut und das Risiko verringert, dass Abonnentinnen und Abonnenten gegenüber Mitbewerbern mit einfacheren Preisen ausscheiden.

### Auswirkung auf den Betrieb

Kampagnen zur Planoptimierung steigern die Planänderungsraten und verbessern die Kundenzufriedenheit. Gleichzeitig wird der durchschnittliche Umsatz pro Benutzer gesteigert, wenn Abonnenten Pläne wählen, die ihrem Verbrauch besser entsprechen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um eine Multi-Touch-Kampagne zu erstellen, die Diskrepanzen zwischen Nutzung und Plan erkennt, Abonnentinnen und Abonnenten über bessere Optionen informiert und sie durch den Planänderungsprozess mit zeitnahen Folgemaßnahmen führt. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf der Interaktion mit Abonnenten und der Annahme von Plänen erfordert - eine einzige ausgelöste Nachricht kann die Lehr-Journey und Abhängigkeitslogik zwischen Bildungs- und Konversionsschritten nicht berücksichtigen.

### Technische Überlegungen

- Nehmen Sie Echtzeit- und historische Nutzungsdaten (Sprachminuten, Datennutzung, internationale Anrufe) auf, um Planabweichungen genau zu identifizieren.
- Verbinden Sie Daten aus dem Abrechnungssystem, um potenzielle Einsparungen oder Funktionsgewinne für jede empfohlene Planänderung zu berechnen.
- Berücksichtigen Sie bei der Erstellung von Planempfehlungen die Preisregeln und vertraglichen Verpflichtungen für Werbeaktionen.
- Integration mit Self-Service-Portalen, damit Abonnentinnen und Abonnenten Planänderungen direkt über Campaign-Touchpoints abschließen können.


## Abwanderungsprävention für hochwertige Kunden

Identifizieren Sie hochwertige Kunden, bei denen das Risiko einer Abwanderung besteht, und interagieren Sie mit personalisierten Aufbewahrungsangeboten und proaktivem Kundenservice. Durch die Kombination von Verhaltenssignalen wie abnehmender Nutzung, wiederholten Service-Aufrufen und wettbewerbsorientiertem Browsen mit Lebenszeitwertdaten können Anbieter eingreifen, bevor ein Abonnent entscheidet zu gehen.

### Auswirkung auf den Betrieb

Abwanderungspräventionsprogramme, die sich an Abonnentinnen und Abonnenten mit hohem Unternehmenswert richten, führen zu einer deutlichen Abwanderungsreduzierung, schützen signifikante wiederkehrende Umsätze und senken die Kosten für die Akquise von Ersatzkunden.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Abwanderungsrisikosignale in Echtzeit zu überwachen, das beste Aufbewahrungsangebot für jeden Abonnenten zu ermitteln und personalisierte Kontaktaufnahme über digitale Kanäle und das Callcenter zu orchestrieren. Dies ist das richtige Muster, wenn der Journey die Bereitstellung über digitale und agentengestützte Kanäle koordinieren muss, um doppelte Aufbewahrungsangebote zu verhindern, und wenn die Angebotsauswahl Risikobewertungen und geschäftliche Einschränkungen erfordert - eine mehrstufige Orchestrierung allein bietet nicht die erforderliche Entscheidungsebene oder Agentenkoordination in Echtzeit.

### Technische Überlegungen

- Tendenzwerte zur Abwanderung erstellen, indem Nutzungstrends, der Verlauf von Service-Interaktionen und Sentiment-Daten aus Callcenter-Transkripten kombiniert werden.
- Integrieren Sie Callcenter- und Einzelhandelssysteme, damit Kundendienstmitarbeiter Einblick in bereits über digitale Kanäle unterbreitete Aufbewahrungsangebote erhalten.
- Verbinden Sie Daten zu Wettbewerbsinformationen (Port-Out-Anfragen, Vergleiche von Wettbewerbsplänen), um die Risikobewertung und Angebotsstrategien zu verfeinern.
- Legen Sie Governance-Regeln fest, um zu verhindern, dass gefährdete Abonnentinnen und Abonnenten übermäßig kontaktiert werden, was die Abwanderung beschleunigen kann, anstatt sie zu verhindern.


## Onboarding-Journey für neue Kunden

Automatisieren Sie eine personalisierte Onboarding-Journey für neue Kunden mit Begrüßungsinformationen, Anleitungen zur Kontoeinrichtung und Funktions-Tutorials. Ein strukturiertes Onboarding hilft Abonnentinnen und Abonnenten, den vollen Nutzen aus ihrem Plan und ihren Services zu ziehen, und schafft die Grundlage für eine langfristige Bindung.

### Auswirkung auf den Betrieb

Gut konzipierte Onboarding-Journey fördern verbesserte Funktionsaktivierungsraten, was zu höheren Zufriedenheitswerten und einer geringeren Abwanderung in den ersten Lebensjahren bei neuen Abonnenten führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um ein sequenzielles Onboarding-Erlebnis zu erstellen, das sich basierend auf dem Plantyp, dem Gerät und der Interaktion jedes Abonnenten mit vorherigen Onboarding-Schritten anpasst. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf der Erkennung und Interaktion von Funktionen erfordert - eine einzelne ausgelöste Nachricht kann die adaptive Abhängigkeitslogik zwischen Onboarding-Schritten basierend auf dem Abonnentenplan und dem Gerätetyp nicht berücksichtigen.

### Technische Überlegungen

- Integrieren Sie Kontobereitstellungssysteme, um die Onboarding-Journey sofort nach der Aktivierung in Trigger zu nehmen, und passen Sie Inhalte an den spezifischen Plan und das Gerät des Abonnenten an.
- Verbinden Sie App-Interaktionsdaten, um zu verfolgen, welche Funktionen der Abonnent untersucht hat, und passen Sie die nachfolgenden Onboarding-Nachrichten entsprechend an.
- Stimmen Sie sich mit der Support-Plattform des Kunden ab, um sicherzustellen, dass Kundendienstmitarbeiter über die Onboarding-Phase eines Abonnenten informiert sind, wenn sie sich bei Fragen melden.
- Unterstützung mehrerer Onboarding-Pfade für verschiedene Kundensegmente, z. B. einzelne Abonnenten, Familienplanadministratoren und Geschäftskonten.


## Warnhinweise und Empfehlungen zur Datennutzung

Senden Sie personalisierte Warnhinweise, wenn Kunden Datenbeschränkungen erreichen und basierend auf Nutzungsmustern Upgrades oder Daten-Add-ons planen. Rechtzeitige, hilfreiche Benachrichtigungen verwandeln ein potenziell frustrierendes Erlebnis in einen Moment vertrauensbildender Interaktion.

### Auswirkung auf den Betrieb

Proaktive Warnhinweise zur Datennutzung fördern Käufe von Zusatzdaten und verringern gleichzeitig Reklamationen aufgrund von Rechnungsschocks und verbessern die Kundenzufriedenheit insgesamt.

### Implementieren

Verwenden Sie das [Ereignisgesteuerte Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um bei Überschreiten von Nutzungsschwellen Echtzeitwarnungen zu senden, mit personalisierten Empfehlungen, die auf den historischen Verbrauchsmustern und Plandetails des Abonnenten basieren. Dies ist das richtige Muster, wenn der Trigger ein Systemereignis (Überschreitung der Nutzungsschwelle) und kein Kundenverhalten ist und die erforderliche Kommunikation sofort und reaktiv erfolgt und keine nachhaltige Nurture-Sequenz ist.

### Technische Überlegungen

- Stellen Sie eine Verbindung zu Netzwerk-Nutzungsdaten-Feeds her, die nahezu in Echtzeit Verbrauchsaktualisierungen zu Trigger-Warnhinweisen bei aussagekräftigen Schwellenwerten bereitstellen (75 %, 90 %, 100 % der Planzahlen).
- Integrieren Sie Abrechnungs- und Planverwaltungssysteme, um genaue Zusatzpreise anzuzeigen und Einkäufe mit nur einem Fingertipp direkt aus der Warnmeldung zu ermöglichen.
- Berücksichtigen Sie freigegebene Datenpools in Familienplänen, indem Sie sowohl den einzelnen Benutzer als auch den Planadministrator benachrichtigen.
- Implementieren Sie eine Frequenzlimitierung, um eine Warnhinweisermüdung für Abonnentinnen und Abonnenten zu vermeiden, die in jedem Abrechnungszyklus durchgängig hohe Datenmengen verwenden.


## Service-Ausfallbenachrichtigungen

Proaktive Benachrichtigung von Kunden über Service-Ausfälle, Wartungs- oder Netzwerkprobleme in ihrem Bereich mit personalisierten Updates und Kompensationsangeboten. Die Kontaktaufnahme mit Kundinnen und Kunden, bevor diese frustriert sind, zeigt die Verantwortlichkeit und reduziert das Volumen des eingehenden Supports erheblich.

### Auswirkung auf den Betrieb

Proaktive Ausfallbenachrichtigungen erzielen hohe Bestätigungsraten für Benachrichtigungen und reduzieren das Callcenter-Volumen bei Service-Unterbrechungen erheblich. Dies senkt die Support-Kosten und verbessert die Kundenwahrnehmung.

### Implementieren

Verwenden Sie das [Ereignisgesteuerte Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um Netzwerkereignisse zu erkennen und betroffene Abonnentinnen und Abonnenten sofort über ihre bevorzugten Kanäle mit relevanten Details, geschätzten Auflösungszeiten und angemessener Kompensation zu benachrichtigen, falls dies gerechtfertigt ist. Dies ist das richtige Muster, wenn es sich bei dem Trigger um ein Systemereignis (Netzwerkausfall) und nicht um ein Kundenverhalten handelt und die erforderliche Kommunikation sofort und reaktiv erfolgt und keine nachhaltige Nurture-Sequenz ist.

### Technische Überlegungen

- Integration mit netzwerkbetrieblichen Überwachungssystemen, um Echtzeit-Ausfall- und Wartungsereignisdaten mit Informationen über den geografischen Umfang zu erhalten.
- Nutzt die Adressen- und Standortdaten der Abonnenten, um betroffene Kunden genau zu identifizieren und zu vermeiden, dass Kunden außerhalb des betroffenen Gebiets benachrichtigt werden.
- Stellen Sie eine Verbindung zum Abrechnungs- und Gutschriftsystem her, um die Leistungspunktangebote für längere Ausfälle auf der Grundlage des Plans des Abonnenten und der Dauer der Störung zu automatisieren.
- Koordinieren Sie das Messaging über verschiedene Kanäle hinweg, um konsistente Statusaktualisierungen zu bieten und den Versand widersprüchlicher Informationen im Zuge der Entwicklung der Situation zu vermeiden.


## Familienplanverwaltung

Personalisieren Sie die Kommunikation und Angebote für Familienplanadministratoren auf der Grundlage von Familiennutzungsmustern und individuellen Bedürfnissen der Mitglieder. Familienpläne stellen wertvolle mehrzeilige Konten dar, bei denen die Interaktion mit dem Planadministrator die Kundenbindung über alle Linien hinweg vorantreibt.

### Auswirkung auf den Betrieb

Personalisierte Mitteilungen zur Verwaltung von Familienplänen fördern die Interaktion mit Familienplänen, was zu einer höheren Online-Bindung und einem höheren Lebensdauerwert pro Konto führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um die Nutzung durch alle Familienmitglieder zu analysieren, Möglichkeiten wie das Hinzufügen von Zeilen oder die Anpassung individueller Limits zu identifizieren und dem Planadministrator maßgeschneiderte Empfehlungen zu geben. Dies ist das richtige Muster, wenn bei der Angebotsauswahl Berechtigungen für die Familienhierarchie, die Aggregation mehrerer Mitglieder und Datenschutzbeschränkungen berücksichtigt werden müssen - Einschränkungen, für die eine geregelte Entscheidungslogik erforderlich ist, anstatt Empfehlungen nur von einzelnen Abonnenten.

### Technische Überlegungen

- Modellieren Sie Familienkontenhierarchien, um zwischen Planadministrator und einzelnen Mitgliedern zu unterscheiden, wobei die Berechtigungsebenen für Kommunikationen und Kontoänderungen zu beachten sind.
- Aggregieren Sie Nutzungsdaten über alle Kontozeilen hinweg, um Muster und Möglichkeiten auf Familienebene zu identifizieren, z. B. nicht ausgelastete freigegebene Daten oder unregelmäßige Geräte-Upgrade-Zyklen.
- Integration von Kindersicherung und Inhaltsfiltersystemen zur Unterstützung familienspezifischer Funktionen bei der Personalisierung.
- Stellen Sie sicher, dass Datenschutzkontrollen vorhanden sind, sodass individuelle Nutzungsdetails auf der Grundlage von Kontoberechtigungen ordnungsgemäß mit dem Planadministrator geteilt werden.


## 5G-Upgrade-Kampagnen

Kunden, die für 5G-Netzaktualisierungen infrage kommen, erhalten auf der Grundlage ihres Standorts und ihrer Nutzungsmuster personalisierte Angebote und Vorteile. Mit zunehmender 5G-Abdeckung beschleunigt die Anbindung von Abonnentinnen und Abonnenten in neu abgedeckten Gebieten mit relevanter Nachrichtenübermittlung die Akzeptanz und erhöht die Netzauslastung.

### Auswirkung auf den Betrieb

Gezielte 5G-Upgrade-Kampagnen fördern eine höhere 5G-Akzeptanzrate bei den geeigneten Abonnentinnen und Abonnenten, unterstützen die Rendite von Netzwerkinvestitionen und die Differenzierung im Wettbewerb.

### Implementieren

Verwenden Sie das [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)-Muster, um Abonnentinnen und Abonnenten auf der Grundlage der Verfügbarkeit der 5G-Abdeckung, der Gerätekompatibilität und der Planeignung zu segmentieren, und führen Sie dann personalisierte Upgrade-Kampagnen durch, die die Vorteile hervorheben, die für das Nutzungsprofil der einzelnen Abonnentinnen und Abonnenten am relevantesten sind. Dies ist das richtige Muster, wenn die Zielgruppe vordefiniert und groß ist, der Versand zeitlich geplant und nicht ereignisgesteuert ist und keine Verzweigung oder Entscheidung in Echtzeit erforderlich ist. Die Kampagne kann basierend auf den Rollout-Zeitplänen der Abdeckung vollständig im Voraus geplant werden.

### Technische Überlegungen

- Netzabdeckungskarten integrieren, um Abonnenten in Gebieten mit aktiven 5G-Diensten genau zu identifizieren und Upgrades zu vermeiden, in denen die Abdeckung noch nicht verfügbar ist.
- Verbinden Sie Gerätekompatibilitätsdaten, um zu bestimmen, welche Abonnenten ein neues Gerät benötigen, im Vergleich zu denen, die bereits über 5G-fähige Hardware verfügen.
- Abstimmung mit Einzelhandelsinventarsystemen, um sicherzustellen, dass beworbene Geräte und Pläne im bevorzugten Geschäft des Abonnenten oder online verfügbar sind.
- Segmentieren Sie das Messaging nach Nutzungsprofil, sodass Benutzer mit umfangreichen Datenmengen leistungsorientierte Vorteile erhalten, während gelegentliche Benutzer Nachrichten zur Abdeckung und Zuverlässigkeit erhalten.


## Erinnerungen für Rechnungszahlungen

Senden Sie personalisierte Erinnerungen zu Rechnungszahlungen über bevorzugte Kanäle mit Zahlungsoptionen und Kontostandsinformationen. Pünktliche, praktische Erinnerungen reduzieren Zahlungsverzug und damit verbundene Inkassokosten und halten die Kundenbeziehung positiv.

### Auswirkung auf den Betrieb

Personalisierte Erinnerungen zu Rechnungszahlungen verbessern die pünktlichen Zahlungsraten, reduzieren die Inkassokosten und minimieren Service-Aussetzungen, die die Kundenzufriedenheit steigern.

### Implementieren

Verwenden Sie [ Muster „Ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md), um Erinnerungen zu optimalen Zeiten vor dem Fälligkeitsdatum zu senden, die mit dem Kontostand des Abonnenten, der bevorzugten Zahlungsmethode und einem direkten Link personalisiert sind, um die Zahlung abzuschließen. Dies ist das richtige Muster, wenn der Trigger ein zeitbasiertes Systemereignis (Fälligkeitsdatum der Abrechnung) und kein Kundenverhalten ist und die erforderliche Kommunikation sofort und transaktional erfolgt und keine mehrstufige Interaktionssequenz ist.

### Technische Überlegungen

- Integration mit der Abrechnungsplattform für Zugriff auf Echtzeit-Kontostände, Fälligkeitsdaten und den Zahlungsverlauf für genaue Erinnerungsinhalte.
- Verbinden Sie sich mit Zahlungsverarbeitungssystemen, um eine Zahlung mit einem Tippen oder einem Klick direkt aus der Erinnerungsnachricht zu ermöglichen.
- Implementieren Sie eine Eskalationslogik, die die Dringlichkeit und Häufigkeit von Erinnerungen an den Fälligkeitszeitpunkt anpasst und dabei die Kommunikationsvoreinstellungen berücksichtigt.
- Unterstützen Sie mehrere Zahlungsmethoden (automatische Registrierung, digitale Brieftasche, Banküberweisung) und personalisieren Sie die präsentierten Optionen basierend auf der Historie des Abonnenten.


## Add-on-Service-Empfehlungen

Empfehlen Sie relevante Add-on-Services wie Geräteversicherung, Cloud-Speicher und Streaming-Pakete basierend auf dem Plan, der Verwendung und den Voreinstellungen des Kunden. Kontextuelle Empfehlungen steigern den Wert, den Abonnentinnen und Abonnenten aus ihrer Beziehung zum Anbieter erhalten, während der durchschnittliche Umsatz pro Benutzerin bzw. Benutzer steigt.

### Auswirkung auf den Betrieb

Personalisierte Add-on-Service-Empfehlungen steigern die Akzeptanzraten von Add-ons und steigern den Umsatz mit bestehenden Abonnentinnen und Abonnenten, ohne dass Kosten für die Akquise neuer Kunden entstehen.

### Implementieren

Verwenden Sie das [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)-Muster, um das Profil, die aktuellen Services und die Verhaltenssignale jedes Abonnenten zu bewerten, um das relevanteste Add-on-Angebot zu ermitteln und es über den optimalen Kanal und Zeitpunkt darzustellen. Dies ist das richtige Muster, wenn bei der Angebotsauswahl aktuelle Service-Eigentümerschaftsregeln und Geschäftsregeln berücksichtigt werden müssen, die die ergänzende Service-Eignung regeln - Regeln, die eine geregelte Entscheidungslogik erfordern, und nicht nur eine Rangliste der Verhaltens-Affinität.

### Technische Überlegungen

- Stellen Sie eine Verbindung zum aktuellen Servicekatalog des Abonnenten her, um zu vermeiden, ihm bereits vorhandene Services zu empfehlen, und um natürliche Ergänzungen zu seinem bestehenden Plan zu identifizieren.
- Integrieren Sie Partner- und Drittanbieterdaten (Streaming-Anbieter, Versicherungsträger), um genaue Preise und gebündelte Angebote zu präsentieren.
- Verwenden Sie Geräte- und Nutzungsdaten, um Empfehlungen zu formulieren, z. B. Vorschläge für eine Geräteversicherung für Abonnenten mit neuen Premium-Geräten oder Cloud-Speicher für diejenigen, denen der Gerätespeicher ausgeht.
- Koordinieren Sie sich mit In-App- und Web-Personalisierung, um Add-on-Empfehlungen für Self-Service-Touchpoints zu verstärken.


## Netzwerkleistung Personalization

Personalisieren Sie Informationen und Empfehlungen zur Netzwerkleistung basierend auf dem Standort, dem Gerät und den Nutzungsmustern des Kunden. Abonnentinnen und Abonnenten dabei zu unterstützen, ihre Konnektivität zu optimieren, schafft Vertrauen und reduziert die Support-Kontakte, die mit Leistungsproblemen verbunden sind.

### Auswirkung auf den Betrieb

Personalisierte Netzwerkleistungserlebnisse fördern die Interaktion mit Mobile Apps, da Abonnentinnen und Abonnenten zurückkehren, um die Abdeckung zu überprüfen, Probleme zu beheben und Optimierungstipps zu finden, die auf ihre Situation zugeschnitten sind.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um personalisierte Dashboards zur Netzwerkleistung, Informationen zur Abdeckung und Optimierungsempfehlungen für das App- und Web-Kontoerlebnis des Abonnenten bereitzustellen. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und Standortdaten und nicht von einem verhaltensbezogenen Affinitätsmodell gesteuert wird.

### Technische Überlegungen

- Integrieren Sie Netzwerkqualitätsmetriken und Abdeckungsdaten, um standortspezifische Leistungsinformationen bereitzustellen, die für das Zuhause, die Arbeit und die häufig besuchten Bereiche der Abonnenten relevant sind.
- Schließen Sie Gerätediagnosedaten an, um maßgeschneiderte Empfehlungen zur Fehlerbehebung auf der Grundlage des spezifischen Gerätemodells und der Softwareversion des Abonnenten anzubieten.
- Verwenden Sie [!DNL Adobe Experience Platform] Edge-Services, um Personalisierung mit niedriger Latenz innerhalb des App-Erlebnisses bereitzustellen, ohne die Leistung zu beeinträchtigen.
- Implementieren Sie Feedback-Schleifen, damit Abonnentinnen und Abonnenten Probleme mit der Abdeckung melden können, wobei die Netzwerkdaten angereichert werden und gleichzeitig Reaktionen auf ihr Erlebnis gezeigt werden.


## KI-Planberater

Die Telekommunikationskunden stehen vor einer anhaltenden Herausforderung: Sie müssen verstehen, wie sich ihr aktueller Plan im Vergleich zu den verfügbaren Optionen darstellt und ob ein anderer Plan besser zu ihrer tatsächlichen Nutzung passen würde. Auf statischen Planvergleichsseiten müssen Abonnentinnen und Abonnenten Daten selbst interpretieren, die sie möglicherweise nicht vollständig verstehen, was zu suboptimaler Planauswahl, Rechnungsschock und vermeidbarer Abwanderung führt. Ein KI-Planberater interagiert mit Abonnentinnen und Abonnenten in natürliche Gespräche, prüft ihre Nutzungsmuster anhand ihres Echtzeit-Profils, stellt qualifizierte Fragen zu Geräteanforderungen und Haushaltsanforderungen und führt sie zu dem Plan - oder der Kombination aus Plänen und Add-ons -, der am besten zu ihrer Situation passt.

### Auswirkung auf den Betrieb

Die Unterstützung von Gesprächsplänen reduziert die plangesteuerte Abwanderung, erhöht den Upgrade-Anhang für Abonnentinnen und Abonnenten, die von ihrem aktuellen Plan nicht ausreichend betreut werden, und reduziert das Volumen des Kontaktzentrums für Abrechnungs- und Planänderungsanfragen.

### Implementieren

Verwenden Sie das [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)-Muster. Dieser Ansatz stellt die Product Advisor Agent anhand des Plan- und Add-on-Katalogs bereit und verwendet AEP Agent Orchestrator- und Echtzeit-Kundenprofildaten - einschließlich des Nutzungsverlaufs und aktueller Plandetails -, um Abonnentinnen und Abonnenten durch die personalisierte Plandarstellung über einen natürlichen Dialog zu führen. Dies ist das richtige Muster, wenn das Ziel eine interaktive, interaktive, konversative Erkennung ist, die Abonnenten dabei hilft, den richtigen Plan aktiv zu bewerten und auszuwählen - im Gegensatz zu ereignisgesteuertem Messaging, das Abonnenten reaktiv über Nutzungsschwellen oder Planänderungen benachrichtigt, und von personalisierten Web-Erlebnissen, die Planvergleiche passiv anzeigen, ohne Abonnenten in einen qualifizierten Dialog einzubeziehen. Dies erfordert die Konfiguration von AEP Agent Orchestrator und Brand Governance.

### Technische Überlegungen

- Die Echtzeit-Kundenprofilsuche muss aktuelle Plandetails, Daten- und Sprachnutzungsmuster, Gerätekompatibilität und Vertragsstatus enthalten, damit der Berater genaue, kontospezifische Anleitungen anstelle allgemeiner Plandeschreibungen bereitstellen kann, die erfordern, dass der Abonnent sich selbst auf seine Situation anwendet.
- Der Plan und der Add-on-Katalog müssen durch die Integration mit dem Produkt-Management-System auf dem neuesten Stand gehalten werden, da die Empfehlung eines Plans oder eines Werbepreises, der nicht mehr verfügbar ist, oder das Auslassen einer neu eingeführten Option das Vertrauen der Abonnenten direkt untergräbt und Probleme mit den Service-Erwartungen schaffen kann.
- Die Leitplanken für die Markenführung müssen definieren, wie der Agent mit Betreibervergleichen, Werbeaussagen und Gesprächen über vertragliche Verpflichtungen umgeht, um sicherzustellen, dass die Antworten des Agenten mit regulatorischen und Markenstandards übereinstimmen, ohne irreführende Verpflichtungen zu schaffen, die der Abonnent später anfechten könnte.
- Gesprächssignale - einschließlich angegebener Haushaltsgröße, Geräteanzahl, internationalem Nutzungsinteresse und während des Dialoges angegebener Planänderungsabsicht - müssen als XDM ExperienceEvents erfasst und an AEP zurückgesendet werden, wobei die Abonnentenprofile angereichert werden, um nachgelagerte Abwanderungs-Präventions-, Upgrade- und Crosssell-Kampagnen zu unterstützen.


## Abwanderungsneigung und Network Experience Analytics

Korrelieren Sie Netzwerkerlebnismetriken - Anrufverluste, Datendurchsatzverminderung, Ausfallrisiko - mit Kundendienst-Kontaktraten und Abwanderungsergebnissen, um zu ermitteln, wo sich Probleme mit der Netzwerkqualität in messbaren Abnutzungsrisiken niederschlagen. Telekommunikationsanbieter, die die Netzwerkleistung und das Kundenverhalten in separaten Systemen analysieren, können nicht bestimmen, welche Service-Qualitätsfehler tatsächlich die Abwanderung fördern oder ohne Folgen absorbiert werden.

### Auswirkung auf den Betrieb

Durch die Verbindung von Netzwerkerlebnisdaten mit dem Kundenverhalten und Abwanderungsergebnissen können Netzwerk-, Produkt- und Kundenbindungs-Teams Korrekturinvestitionen basierend auf nachgewiesenen Abnutzungsauswirkungen und nicht nur auf dem technischen Schweregrad priorisieren.

### Implementieren

Verwenden Sie das [Muster Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) . Dieser Ansatz verbindet Netzwerkereignisdaten, Kundendienst-Interaktionsdatensätze, digitale Verhaltenssignale und Abonnenten-Lebenszyklus-Ereignisse mit Customer Journey Analytics, wobei die korrelierte Analyse die Netzwerkerlebnisschwellen und Kontaktmuster identifiziert, die statistisch mit Abwanderung und Vertragsnicht-Verlängerung verbunden sind. Dies ist das richtige Muster, wenn das Ziel in der Generierung von insight und der Ursachenanalyse besteht - zu verstehen, welche Service-Qualitätsereignisse die Attribution fördern -, anstatt ein Aufbewahrungsangebot auszulösen oder eine Zielgruppe mit Abwanderungsrisiko in einer CDP zu aktivieren.

### Technische Überlegungen

- Netzwerkerlebnisereignisse müssen mit Teilnehmerdatensätzen unter Verwendung von Geräte- oder Kontokennungen verbunden werden, die mit der in der CJA-Verbindung konfigurierten Personen-ID übereinstimmen, da Netzwerktelemetriesysteme in der Regel Geräte- statt Kundenkennungen verwenden.
- Kundendienst-Kontaktdaten - einschließlich Kontaktgrund-Codes, verwendeter Kanal und Lösungsstatus - müssen als Ereignisse mit Zeitstempeln aufgenommen werden, die es Analysten ermöglichen, sequenzielle Pfade von Netzwerkvorfällen über Service-Kontakt bis hin zur Abwanderung in CJA-Fluss- oder Fallout-Visualisierungen zu erstellen.
- Vertrags- und Plandaten von Abonnenten, einschließlich Vertragsenddaten, Planebene und Beschäftigungsdauer, sollten als Lookup-Dimensionen in der CJA-Datenansicht verfügbar sein, damit die Abwanderungsanalyse nach Vertragsnähe und -werteebene segmentiert werden kann, anstatt die Abonnentenbasis als homogen zu behandeln.
- Datenvolumen der Netzwerktelemetrie können extrem groß sein. Datensatz-Sampling-Strategien oder Voraggregation in AEP sollten in Betracht gezogen werden, um die Leistung der CJA-Verbindungsabfrage innerhalb akzeptabler Bereiche für die Selbstbedienung von Analysten zu halten.

## Abwanderungsprävention und -rückgewinnung

Verwenden Sie prädiktive Modelle und Verhaltenssignale, um gefährdete Kundinnen und Kunden zu identifizieren, und erstellen Sie personalisierte Kundenbindungskampagnen mit maßgeschneiderten Angeboten durch Trigger, bevor diese abwandern. Telekommunikationsanbieter sind einem anhaltenden Abwanderungsdruck ausgesetzt, und es ist wesentlich kosteneffektiver, gefährdete Abonnentinnen und Abonnenten mit dem richtigen Angebot zu erreichen, bevor sie die Abbruchwarteschlange kontaktieren, als Win-Back-Kampagnen im Nachhinein.

### Auswirkung auf den Betrieb

Telekommunikationsanbieter mit proaktiven Abwanderungsprogrammen sehen eine deutliche Verringerung der freiwilligen Abwanderung für zielgerichtete Segmente. Dies wirkt sich am stärksten auf mittelständische Kunden aus, bei denen zielgerichtete Kundenbindungsangebote kostengünstiger sind als pauschale Rabatte.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um eine Bindungs-Journey zu erstellen, die risikobehaftete Abonnentinnen und Abonnenten basierend auf Abwanderungsneigungswerten identifiziert, das geeignete Bindungsangebot mithilfe der Entscheidungslogik auswählt und es über die bevorzugten Kanäle des Abonnenten mit Folgeschritten bereitstellt, wenn die erste Kontaktaufnahme ignoriert wird. Dies ist das richtige Muster, wenn sowohl die Angebotsauswahl als auch die Journey-Orchestrierung erforderlich sind - eine einzige ausgelöste Nachricht kann die für eine effektive Bindung erforderliche Angebotsrangfolgelogik und Multi-Touch-Nachverfolgung nicht verarbeiten.

### Technische Überlegungen

- Abwanderungsneigungsmodelle müssen auf historischen Abwanderungsdaten trainiert werden, zu denen Netzwerkerfahrung, Abrechnungsereignisse, Service-Aufrufe und Gerätealter gehören - Modelle, die nur auf Interaktionsdaten trainiert werden, sind im Vergleich zu Telekom-spezifischen Abwanderungstreibern oft nicht leistungsfähig.
- Aufbewahrungsangebote müssen durch Kosten-zu-halten-Schwellenwerte pro Kundenwertsegment eingeschränkt werden. Die Decisioning-Engine sollte verhindern, dass kostenintensive Aufbewahrungsangebote auf Abonnenten mit niedrigem Wert angewendet werden.
- Die Verarbeitung von Abwanderungssignalen in Echtzeit muss Vertragsanfrageereignisse und Seitenbesuche zur Stornierung von Services an Trigger-Antworten auf dringende Kundenbindung erkennen, bevor der Abonnent eskaliert.
- Die Integration des Kundendienstes ist von entscheidender Bedeutung. Abonnentinnen und Abonnenten, die die Aufbewahrungswarteschlange anrufen, sollten als Journey-Abonnentinnen und -Abonnenten erkannt werden, sodass die Agenten den Kontext des Aufbewahrungsangebots bereit haben, bevor der Anruf beginnt.
