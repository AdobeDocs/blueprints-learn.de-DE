---
title: Anwendungsfälle für Automobile
description: Erfahren Sie, wie Automobilunternehmen Adobe Experience Platform verwenden, um die Fahrzeugkauf-Journey zu personalisieren, die Kundenbindung zu verbessern und die Loyalität der Eigentümer zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# Anwendungsfälle für Automobile

Automobilunternehmen verwenden Adobe Experience Platform, um Kundendaten aus Händlerinteraktionen, Online-Fahrzeugforschung, Service-Aufzeichnungen und vernetzten Fahrzeugsystemen in einer einzigen Ansicht jedes Eigentümers zu vereinheitlichen. Diese Grundlage ermöglicht personalisierte Erlebnisse während des gesamten Lebenszyklus des Eigentums, von der ersten Fahrzeugforschung bis hin zu Kauf, Service und Treue.

## Zusammenfassung eines Anwendungsfalls

| Nutzungsszenario | Beschreibung | Auswirkung auf den Betrieb | Implementierungsmuster |
| --- | --- | --- | --- |
| [Fahrzeugkauf Journey Personalization](#vehicle-purchase-journey-personalization) | Personalisieren Sie die Fahrzeugkauf-Journey von der Recherche bis zum Kauf mit relevanten Fahrzeugempfehlungen, Finanzierungsoptionen und Händlerinformationen. Wenn potenzielle Käufer in jeder Phase eine maßgeschneiderte Beratung erhalten, durchlaufen sie die Sales funnel schneller und mit größerer Zuversicht. | 20-30 % Steigerung der Lead-to-Purchase-Konversionsraten, verbesserte Vertriebspipeline | [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Service-Terminerinnerungen](#service-appointment-reminders) | Senden Sie personalisierte Service-Erinnerungen basierend auf Fahrzeugkilometerleistung, Service-Verlauf und Kundenpräferenzen. Durch proaktive Öffentlichkeitsarbeit werden Fahrzeuge gewartet und die Kunden kehren zum Händler zurück, anstatt nach Drittanbietern zu suchen. | 40-50 % mehr Service-Termine, höhere Service-Einnahmen | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Trade-In-Value-Kampagnen](#trade-in-value-campaigns) | Bieten Sie Kunden, die für ein Upgrade infrage kommen, proaktiv eine Bewertung des Gegenwerts an. Wenn Sie Besitzer zum richtigen Zeitpunkt in ihrem Eigentümerzyklus erreichen, beschleunigen Sie den Weg zu einem neuen Fahrzeugkauf. | 25-35 % mehr Inzahlungnahme, mehr Neuwagenverkäufe | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Empfehlungen für Teile und Zubehör](#parts-and-accessories-recommendations) | Empfehlen Sie relevante Teile, Zubehör und Upgrades basierend auf dem Fahrzeugmodell, der Eigentümerdauer und den Kundenpräferenzen. Personalisierte Aftermarket-Empfehlungen steigern den Umsatz und helfen den Eigentümern, ihr Fahrzeug besser zu nutzen. | 30-40 % mehr Ersatzteile-/Zubehörkäufe, mehr Aftermarket-Umsatz | [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [Rückrufaktionen für Fahrzeuge](#vehicle-recall-notifications) | Senden Sie personalisierte Rückrufbenachrichtigungen mit Serviceplanungsoptionen und Sicherheitsinformationen. Zeitnahe, klare Rückrufaktionen schützen die Sicherheit der Kunden und zeigen das Engagement der Marke für eine verantwortungsvolle Unterstützung im Hinblick auf das Eigentum. | 60-70 % höhere Rückrufantwortraten, bessere Einhaltung der Sicherheitsvorschriften | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Neue Modellstart-Kampagnen](#new-model-launch-campaigns) | Targeting von Kunden, die sich für neue Modellstarts interessieren könnten, basierend auf ihrem aktuellen Fahrzeug, ihren Präferenzen und ihrer Kaufhistorie. Gezieltes Zielgruppen-Targeting maximiert die Wirkung von Launches und sorgt für eine frühe Auftragsdynamik. | 35-45 % mehr Interaktion mit Launch-Kampagnen, mehr Interesse für neue Modelle | [Batch-Aktivierung ausgehender Nachrichten](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [Finanzierungs- und Versicherungsangebote](#financing-and-insurance-offers) | Präsentieren Sie personalisierte Finanzierungs- und Versicherungsangebote basierend auf Kreditprofil, Fahrzeugauswahl und Kaufzeitplan. Maßgeschneiderte Finanzprodukte beseitigen Hindernisse beim Kauf und helfen Kunden, sich mit ihren Bedingungen vertraut zu machen. | 25-35% Steigerung der Akzeptanzraten für Finanzierungen, Umsatzsteigerung pro Verkauf | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [Planung der Testfahrt](#test-drive-scheduling) | Personalisierte Planung von Testfahrten mit Händlerempfehlungen und Fahrzeugverfügbarkeit. Wenn sich interessierte Käufer mühelos hinter das Steuer setzen, beschleunigt sich der Weg zum Kauf. | 50-60 % höhere Abschlussraten für Testfahrten, bessere Umsätze | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [Treueprogramme für Inhaber](#owner-loyalty-programs) | Personalisieren Sie die Kommunikation, Prämien und exklusiven Angebote im Rahmen des Treueprogramms basierend auf der Eigentümerhistorie und der Treuestufe. Langfristige Besitzer zu erkennen, stärkt die emotionale Bindung zur Marke. | 40-50 % mehr Interaktion mit Treueprogrammen, mehr Wiederholungskäufe | [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [Garantiepläne und erweiterte Servicepläne](#warranty-and-extended-service-plans) | Empfehlen Sie Garantiepläne und erweiterte Servicepläne zu optimalen Zeiten basierend auf Fahrzeugalter, Kilometerstand und Kaufmuster. Zeitgerechte Outreach-Maßnahmen erfassen den Umsatz noch vor Ablauf der Werksgewährleistung. | 20-30 % mehr zusätzliche Garantie, mehr Service-Umsatz | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Connected Car Feature Activation](#connected-car-feature-activation) | Personalisieren Sie die Recommendations für vernetzte Fahrzeugfunktionen basierend auf den Fahrzeugfunktionen und den Technologievoreinstellungen. Inhabern dabei zu helfen, ungenutzte Funktionen zu entdecken, erhöht die Zufriedenheit und stärkt die digitale Beziehung. | Steigerung der Funktionsaktivierungsraten um 35-45 %, verbessertes Kundenerlebnis | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [Händlernetzwerk-Koordination](#dealer-network-coordination) | Personalisierte Händlerempfehlungen basierend auf Kundenstandort, Präferenzen und Händlerbestand aktivieren. Kunden mit dem richtigen Händler zu verbinden, verbessert das Einkaufs- und Serviceerlebnis. | 30-40 % mehr Händlerinteraktionsraten, verbesserte Vertriebskoordination | [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Technische Überlegungen nach Anwendungsfall

### Personalisierung für Fahrzeugkauf-Journey

- Die Fahrzeuginventardaten der Händlermanagementsysteme müssen regelmäßig integriert und aktualisiert werden, damit die Empfehlungen die tatsächliche Verfügbarkeit bei den nahe gelegenen Händlern widerspiegeln.
- Das Verhalten der Kundenforschung auf der gesamten Website, einschließlich Fahrzeugkonfigurationsaktivitäten, Nutzung von Vergleichstools und Downloads von Broschüren, muss erfasst werden, um Kaufabsichtssignale genau zu identifizieren.
- Lead-Scoring-Modelle sollten sowohl für Online-Interaktionen als auch für Offline-Signale wie Händlerbesuche und Telefonanfragen berücksichtigt werden, um die bestmöglichen Interessenten zu priorisieren.
- [!DNL Real-Time Customer Data Platform] Profile müssen anonyme Web-Recherche-Sitzungen mit bekannten Kundenidentitäten zusammenführen, sobald sich ein potenzieller Kunde registriert oder einen Händler besucht.

### Service-Terminerinnerungen

- Fahrzeugkilometerdaten und Telematikdaten aus vernetzten Fahrzeugsystemen oder Kundendienstdatensätzen müssen in den richtigen Serviceintervallen in Kundenprofile zu Trigger-Erinnerungen fließen.
- Erinnerungsnachrichten sollten Links zur Planung mit einem Klick enthalten, mit denen die Fahrzeuginformationen des Kunden vorab ausgefüllt und empfohlene Serviceartikel bereitgestellt werden, um die Buchungsreibung zu minimieren.
- Service-Verlaufsdatensätze müssen integriert werden, um zu vermeiden, dass Services empfohlen werden, die kürzlich abgeschlossen wurden, und um die Erinnerung mit den fälligen spezifischen Wartungspunkten zu personalisieren.
- [!DNL Journey Optimizer] Zeitpunkt der Nachrichtenvermittlung sollte die Servicekapazität des Händlers und die Betriebszeiten berücksichtigen, damit Kunden Termine buchen können, wenn sie die Erinnerung erhalten.

### Wertermittlungskampagnen

- Fahrzeugbewertungsdaten von Drittanbietern müssen regelmäßig integriert und aktualisiert werden, um sicherzustellen, dass die mit den Kunden geteilten Eintauschschätzungen korrekt und wettbewerbsfähig sind.
- Die Modelle für den Eigentümerlebenszyklus sollten Faktoren wie Leasingablaufdaten, Auszahlungsfristen für Kredite und durchschnittliche Eigentümerdauer nach Fahrzeugsegment berücksichtigen, um das optimale Outreach-Fenster zu ermitteln.
- Campaign-Messaging sollte dynamisch auf das aktuelle Fahrzeug des Kunden verweisen und spezifische Upgrade-Optionen vorschlagen, die mit seinen Präferenzen und seinem Budget übereinstimmen.
- [!DNL Experience Platform] Segmente sollten Kundinnen und Kunden ausschließen, die kürzlich ein Fahrzeug gekauft haben oder sich derzeit in einem aktiven Service-Streit befinden, um eine zeitlich schlecht abgestimmte Kontaktaufnahme zu vermeiden.

### Empfehlungen für Teile und Zubehör

- Produktkatalogdaten müssen Informationen zur Fahrzeugkompatibilität enthalten, damit die Empfehlungen nur Teile und Zubehör enthalten, die zum spezifischen Fahrzeugjahr, zur Marke und zum Modell des Kunden passen.
- Saisonale und regionale Faktoren sollten die Empfehlungen beeinflussen; Winterzubehör sollte in kälteren Klimazonen gefördert werden, während Leistungsverbesserungen in Regionen mit aktiven Enthusiasten mehr Resonanz finden könnten.
- Das Surfverhalten auf den Seiten für Teile und Zubehör muss erfasst und mit den Kundenprofilen verknüpft werden, um Empfehlungen auf der Grundlage des geäußerten Interesses zu verfeinern.
- [!DNL Experience Platform] Web SDK-Implementierung sollte Fahrzeugidentifikationsnummern-Daten aus authentifizierten Sitzungen erfassen, um sicherzustellen, dass die Kompatibilitätsfilterung korrekt ist.

### Rückrufaktionen für Fahrzeuge

- Fahrzeugkennnummern müssen in Kundenprofilen genau aufbewahrt werden, damit Rückrufbenachrichtigungen jeden betroffenen Eigentümer erreichen und nicht an nicht betroffene Kunden weitergeleitet werden.
- Die Rückrufaktion muss die gesetzlichen Anforderungen an Inhalt, Zeitplan und Lieferbestätigung für Sicherheitsbenachrichtigungen in jedem relevanten Markt erfüllen.
- Multi-Channel-Versand (E-Mail, Textnachricht, Push-Benachrichtigung und physische E-Mail) sollte verwendet werden, um die Reichweite zu maximieren, da sicherheitskritische Nachrichten eine höhere Versandsicherheit erfordern als Marketing-Nachrichten.
- [!DNL Journey Optimizer] sollten den Status der Rückrufantwort auf individueller Ebene verfolgen und Folgemitteilungen für Eigentümer eskalieren, die den Service nicht innerhalb eines bestimmten Zeitraums geplant haben.

### Neue Modellstart-Kampagnen

- Zielgruppensegmente für Launch-Kampagnen sollten das aktuelle Fahrzeugmodell, die Eigentümerdauer, frühere Modellinteressensignale und die demografische Eignung berücksichtigen, um die Perspektiven mit der höchsten Neigung zu ermitteln.
- Launch-Inhalte sollten personalisiert sein, um auf das aktuelle Fahrzeug des Kunden zu verweisen und bestimmte Verbesserungen oder Funktionen hervorzuheben, die auf seine wahrscheinlichen Prioritäten zugeschnitten sind.
- Der Zeitpunkt der Kampagnen muss mit Embargodaten und regionalen Startzeitplänen abgestimmt sein, um sicherzustellen, dass Kunden Informationen zum richtigen Zeitpunkt für ihren Markt erhalten.
- [!DNL Real-Time Customer Data Platform] Zielgruppenaktivierung sollte Launch-Segmente mit Werbeplattformen synchronisieren, um eine koordinierte Paid-Media-Unterstützung zusammen mit der eigenen Kanalinteraktion zu ermöglichen.

### Finanzierungs- und Versicherungsangebote

- Die Regeln für die Eignung finanzieller Angebote müssen sorgfältig so konfiguriert werden, dass sie den Kreditvergaberegeln entsprechen und sicherstellen, dass die den Kunden unterbreiteten Angebote tatsächlich die Angebote sind, für die sie qualifiziert sind.
- Die Integration von Kreditprofildaten erfordert eine sichere Handhabung und strenge Zugriffskontrollen, da Finanzinformationen strengeren Datenschutz- und Regulierungsanforderungen unterliegen.
- Die Angebotsunterbreitung muss die Bedingungen, Preise und Konditionen in Übereinstimmung mit den Finanzvorschriften für Verbraucher in jedem anwendbaren Markt klar offenlegen.
- [!DNL Journey Optimizer] Entscheidungsregeln sollten Fahrzeugpreise, Anzahlungen und Präferenzen für die Kreditlaufzeit berücksichtigen, um Angebote nach Relevanz und nicht nur nach Zinssatz zu ordnen.

### Planung der Testfahrt

- Händlerinventarsysteme müssen integriert werden, um zu bestätigen, dass das jeweilige Fahrzeugmodell und die Verkleidung, an der der Kunde interessiert ist, für die Testfahrt beim empfohlenen Händler zur Verfügung steht.
- Standortbasierte Händlerempfehlungen sollten die Kundenadresse, Händlerbewertungen und die aktuelle Terminverfügbarkeit berücksichtigen, um die bequemste Option vorzuschlagen.
- Bestätigungs- und Erinnerungsnachrichten für Testfahrten sollten eine Wegbeschreibung, Kontaktinformationen des Händlers und Angaben dazu enthalten, was zu erwarten ist, um die No-Show-Raten zu senken.
- [!DNL Experience Platform] Verhaltensdaten sollten den optimalen Zeitpunkt für eine Testfahrt ermitteln und so eine vorzeitige Kontaktaufnahme zu Forschern im Frühstadium, die noch nicht bereit sind, vermeiden.

### Treueprogramme für Inhaber

- Die Berechnungen der Treuestufe müssen mehrere Dimensionen der Interaktion umfassen, einschließlich Service-Besuche, Ersatzteilkäufe, Empfehlungen und Teilnahme an Veranstaltungen, nicht nur den Fahrzeugkauf.
- Belohnungs-Fulfillment-Systeme in Händlern und Service-Centern müssen integriert sein, damit Treueprogramm-Leistungen nahtlos am Point of Service eingelöst werden können.
- Die Kommunikation sollte sich je nach Lebenszyklus-Phase der Eigentümerschaft anpassen und neuen Eigentümern im ersten Jahr andere Wertversprechen bieten als langfristigen Eigentümern, die sich einem potenziellen Upgrade nähern.
- [!DNL Journey Optimizer] Journey-Logik sollte Stufenänderungen in Echtzeit erkennen und Trigger mit Gratulationen oder Rückgewinnungsmeldungen auslösen, wenn Kundinnen und Kunden zwischen Treuestufen wechseln.

### Garantiepläne und erweiterte Servicepläne

- Die Ablaufdaten und Details der Garantie müssen in den Kundenprofilen genau verfolgt werden, um die Trigger zur richtigen Zeit anzusprechen, in der Regel 60 bis 90 Tage vor Ablauf.
- Die Kilometerzahl und die Nutzungsmuster von Fahrzeugdaten oder -dienstdatensätzen sollten in die Planungsempfehlungen einfließen, da Fahrer mit hohem Kilometerstand andere Reichweiten haben als Eigentümer mit niedrigem Kilometerstand.
- Planvergleichsinhalte sollten klar und frei von Fachjargon sein und Kunden dabei helfen, genau zu verstehen, was abgedeckt wird und welchen Wert sie im Verhältnis zu den potenziellen Reparaturkosten haben.
- [!DNL Real-Time Customer Data Platform] Segmente sollten zwischen Kunden mit ablaufenden Werksgarantien, Kunden mit bestehenden erweiterten Plänen, die kurz vor der Verlängerung stehen, und Kunden ohne aktuelle Abdeckung unterscheiden.

### Aktivierung der Funktion „Connected Car“

- Die Daten der verbundenen Fahrzeugplattform müssen integriert werden, um zu ermitteln, welche Merkmale an jedem Fahrzeug verfügbar sind und welche der Eigentümer bereits aktiviert oder verwendet hat.
- Das Tracking der Funktionsübernahme sollte Aktivierungsereignisse, die Nutzungshäufigkeit und die Interaktionstiefe erfassen, um die Reihenfolge und das Tempo der Funktionsempfehlungen zu personalisieren.
- Die Benachrichtigungskanäle im Fahrzeug sollten mit E-Mail- und Mobile-App-Benachrichtigungen koordiniert werden, um Funktionsaufforderungen zum kontextuell relevantesten Zeitpunkt bereitzustellen, z. B. indem Navigationsfunktionen vorgeschlagen werden, wenn eine Straßenfahrt erkannt wird.
- [!DNL Experience Platform] sollten Fahrzeugtechnologiekonfigurationsdaten, einschließlich installierter Pakete und Softwareversionen, speichern, um sicherzustellen, dass Funktionsempfehlungen mit dem spezifischen Fahrzeug des Eigentümers kompatibel sind.

### Händlernetzwerk-Koordination

- Die Inventarinformationen der Händler müssen regelmäßig integriert und aktualisiert werden, damit die Verfügbarkeit der Fahrzeuge den Kunden genau angezeigt wird, was sich auf dem Los jedes Händlers befindet.
- Die Zuweisungslogik zwischen Kunden und Händlern sollte die räumliche Nähe, die Spezialisierung der Händler, die Sprachpräferenzen und jede bestehende Händlerbeziehung berücksichtigen, um eine optimale Übereinstimmung zu gewährleisten.
- Die Lead-Routing-Regeln müssen sicherstellen, dass eine Anfrage, die einen Kunden online zum Kauf auffordert, den entsprechenden Händler schnell und in vollem Kontext über die Forschungsaktivität des Kunden erreicht.
- [!DNL Experience Platform] Identitätsauflösung muss Szenarien handhaben, in denen ein Kunde mit mehreren Händlern interagiert, ein einheitliches Profil pflegt und dabei die Sicht jedes Händlers auf seine eigenen Kundenbeziehungen respektiert.
