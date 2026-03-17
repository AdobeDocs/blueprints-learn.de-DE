---
title: Anwendungsfälle für Reisen und Gastgewerbe
description: Erfahren Sie, wie Reise- und Gastgewerbeunternehmen Adobe Experience Platform verwenden, um Buchungen zu personalisieren, abgebrochene Reservierungen wiederherzustellen und die Kundentreue der Gäste zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2835'
ht-degree: 0%

---


# Anwendungsfälle für Reisen und Gastgewerbe

Reise- und Gastgewerbeunternehmen verwenden Adobe Experience Platform, um Gastdaten aus Buchungs-Engines, Treueprogrammen, Immobilienverwaltungssystemen und digitalen Touchpoints in einer zentralen Ansicht für jeden Reisenden zusammenzuführen. Diese einheitliche Grundlage ermöglicht personalisierte Erlebnisse, die zu Buchungen inspirieren, verlassene Reservierungen wiederherstellen und die Art von Gastloyalität aufbauen, die zu wiederholten Besuchen führt.

## Personalisierte Homepage für neue Besucher

Zeigen Sie auf der Startseite personalisierte Empfehlungen für Kreuzfahrten, Hotels und Ziele an, die auf dem geografischen Standort des Besuchers und seinem Surfverhalten basieren. Erstbesucher, die relevante Reisemöglichkeiten sofort sehen, erkunden sich viel eher weiter und beginnen mit dem Buchungsprozess.

### Auswirkung auf den Betrieb

Die Personalisierung der Homepage für neue Besucher steigert in der Regel die Konversionsrate um 15-20 %, indem Reiseoptionen präsentiert werden, die dem Standort und den Interessen des Besuchers entsprechen, anstatt allgemeine Inhalte zu präsentieren.

### Implementieren

Verwenden Sie das [Anonymer Besucher Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)-Muster. Dieser Ansatz liefert maßgeschneiderte Inhalte für Besuchende, die sich noch nicht identifiziert haben, und nutzt verfügbare Signale wie Geolokalisierung, Gerätetyp und Empfehlungsquelle, um das Erlebnis von der ersten Seite an zu personalisieren.

### Technische Überlegungen

- Die Geolokalisierungsdaten müssen am Edge präzise aufgelöst werden, um regionsspezifische Ziele, Währungen und Abflughäfen bereitzustellen, ohne die Homepage-Last mit Latenz zu belasten.
- Die Personalization-Regeln sollten saisonale Reisetrends nach Region berücksichtigen, zum Beispiel Warmwetterdestinationen für Besucher in kalten Klimazonen während der Wintermonate.
- Fallback-Inhaltsstrategien sind für Besuchende von entscheidender Bedeutung, deren Standort nicht ermittelt werden kann oder die über Anonymisierungsdienste ankommen.
- Die Integration mit dem Verfügbarkeits-Feed des Reservierungssystems stellt sicher, dass die vorgestellten Objekte und Reiserouten tatsächlich buchbar sind, sodass Frustration nicht durch ausverkaufte Optionen verursacht wird.


## Warenkorbabbruch Recovery-Journey

Erkennen Sie automatisch, wenn ein Kunde seinen Warenkorb verlässt, und erstellen Sie einen mehrstufigen E-Mail-Trigger Journey mit personalisierten Angeboten, um zum Abschluss zu ermutigen. Aufgegebene Reservierungen stellen einen der größten Einnahmeverluste in den Bereichen Reisen und Gastgewerbe dar, und eine rechtzeitige Nachverfolgung während der Reiseabsicht noch frisch ist, deckt einen bedeutenden Anteil dieser Buchungen ab.

### Auswirkung auf den Betrieb

Effektive Buchungs-Recovery-Programme erreichen eine Warenkorb-Recovery-Rate von 25-35 % und können zusätzliche 50.000 bis 200.000 USD an monatlichem Umsatz generieren, je nach Buchungsvolumen und durchschnittlichem Reisewert.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf ein Echtzeit-Warenkorbabbruchs-Ereignis und sendet eine rechtzeitige Erinnerung, während die Reiseabsicht des Kunden immer noch hoch ist.

### Technische Überlegungen

- Die Schwellenwerte für die Warenkorbabbruch-Erkennung sollten die längeren Betrachtungszyklen berücksichtigen, die bei Reisekäufen typisch sind; eine Verzögerung von 2-4 Stunden vor der ersten Erinnerung ist oft besser geeignet als die 30-60 Minuten, die im Einzelhandel verwendet werden.
- Der E-Mail-Inhalt muss zum Versandzeitpunkt die aktuellen Preise, die Verfügbarkeit von Zimmern oder Kabinen sowie Bilder aus dem Reservierungssystem dynamisch abrufen, da sich Reisebestände und Tarife häufig ändern.
- Personalisierte Anreize wie kostenlose Upgrades oder Resort-Credits sollten durch Geschäftsregeln verwaltet werden, die Marge, Saisonabhängigkeit und die Treuestufe des Kunden berücksichtigen.
- Um irrelevante Folgenachrichten zu vermeiden, muss die Unterdrückungslogik Kunden ausschließen, die ihre Buchung über einen anderen Kanal durchgeführt haben, z. B. ein Callcenter oder ein Reisebüro.


## Zielgruppenbestimmung bei Besuchern mit hoher Absicht

Identifizieren Sie Besucher mit hoher Kaufabsicht mithilfe einer KI-gestützten Tendenzauswertung und sprechen Sie sie mit personalisierten Angeboten und Inhalten an. Wenn Sie erkennen, welche Besucher am ehesten buchen, können Sie Ihre attraktivsten Angebote und Verkaufsangebote auf die Reisenden konzentrieren, die am nächsten an einer Entscheidung stehen.

### Auswirkung auf den Betrieb

Wenn Sie Besucher mit hohen Absichten mit personalisierten Angeboten ansprechen, steigern Sie die Konversionsrate für diese Segmente um 30-40 %, sodass sich die Marketing-Investitionen auf die Bereiche konzentrieren, in denen sie die größte Rendite erbringen.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz verwendet Echtzeit-Profildaten und Verhaltenssignale, um das Web-Erlebnis für identifizierte Besucher zu personalisieren und maßgeschneiderte Inhalte und Angebote bereitzustellen, die ihrem Grad der Kaufbereitschaft entsprechen.

### Technische Überlegungen

- Tendenzmodelle müssen auf reisespezifischen Intent-Signalen wie Datumssuchen, Preisfindungsseitenansichten, Zimmervergleichsaktivitäten und wiederholten Besuchen am selben Ziel innerhalb eines kurzen Fensters trainiert werden.
- Absichtsvolle Eingriffe, wie z. B. Live-Chat-Eingabeaufforderungen oder zeitlich begrenzte Angebote, sollten an natürlichen Entscheidungspunkten im Buchungsfluss erscheinen, anstatt das Browsen zu stören.
- Das Scoring-Modell sollte zwischen Forschungsabsicht und Buchungsabsicht unterscheiden, da Reisende oft Monate recherchieren, bevor sie zum Kauf bereit sind.
- [!DNL Real-Time Customer Data Platform] berechneten Attribute können Verhaltenssignale sitzungsübergreifend aggregieren, um für jeden Besucher einen aktuellen Intent-Score bereitzustellen.


## Upsell-Kampagnen nach der Buchung

Nachdem ein Kunde eine Buchung abgeschlossen hat, führen Sie automatisch Trigger-Upsell-Kampagnen für Kabinen-Upgrades, Landausflüge, Restaurantpakete und andere Nebenleistungen durch. Der Zeitraum zwischen Buchung und Reise ist der, in dem die Gäste am meisten auf ihre bevorstehende Reise gespannt sind und am empfänglichsten für die Verbesserung ihrer Erfahrung sind.

### Auswirkung auf den Betrieb

Upsell-Kampagnen nach der Buchung erhöhen typischerweise den durchschnittlichen Bestellwert um 200 bis 500 US-Dollar und steigern den Nebenumsatz um 15 bis 25 %, wodurch eine einzelne Buchung zu einer deutlich wertvolleren Transaktion wird.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Diese mehrstufige Journey führt die gebuchten Kunden durch eine zeitgesteuerte Abfolge von Upsell-Möglichkeiten, wobei die Angebote auf der Grundlage dessen angepasst werden, was der Gast bereits gekauft hat, und die Interaktion mit früheren Nachrichten.

### Technische Überlegungen

- Die Journey muss mit dem Reservierungssystem integriert werden, um genau zu wissen, was der Gast gebucht hat, welche Upgrades für seine spezifische Reiseroute verfügbar sind und welche aktuellen Preise für jede zusätzliche Option gelten.
- Der Upsell-Zeitpunkt sollte strategisch gestaffelt werden; Kabinen-Upgrades können kurz nach der Buchung angeboten werden, während Ausflüge und Restaurantpakete besser funktionieren, wenn das Reisedatum näher rückt.
- Bestand und Verfügbarkeit von Nebenprodukten müssen zum Zeitpunkt der Angebotsunterbreitung überprüft werden, da sich Ausflugskapazität und Verfügbarkeit laufend ändern.
- [!DNL Journey Optimizer] Personalisierung sollte die Anzahl der Reisenden in der Buchung berücksichtigen und familiengerechte Ausflüge für Familienbuchungen und Erlebnisse für Paare für Zweipersonenbuchungen empfehlen.


## Win-Back-Kampagnen für veraltete Kunden

Ermitteln Sie Kunden, die in zwölf oder mehr Monaten nicht gebucht haben, und kontaktieren Sie sie mit personalisierten Win-back-Angeboten und Inhalten, die auf ihren bisherigen Reisevorlieben basieren. Die Rückgewinnung verfallener Gäste ist deutlich kostengünstiger als die Akquise völlig neuer Kunden, und vergangene Reisende sind bereits mit der Marke vertraut, die die Hürde für eine Umbuchung verringert.

### Auswirkung auf den Betrieb

Bei zielgerichteten Win-back-Kampagnen beträgt die Reaktivierungsrate bei abgelaufenen Kundinnen und Kunden 10-15 %. So werden Umsätze von Gästen erzielt, die andernfalls möglicherweise nie zurückkehren.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Diese mehrstufige Journey interagiert abgelaufene Kundinnen und Kunden erneut mit einer progressiven Reihe von Nachrichten, die sich je nach Kundenreaktion von der Inspiration zum Incentive entwickeln.

### Technische Überlegungen

- Eine abgelaufene Kundensegmentierung sollte der typischen Buchungshäufigkeit in der Reisekategorie Rechnung tragen. Ein Kunde, der jährlich bucht, sollte nach nur sechs Monaten Inaktivität nicht als abgelaufen gekennzeichnet werden.
- Win-back-Inhalte sollten sich auf frühere Reisepräferenzen des Kunden beziehen, z. B. bevorzugte Reiseziele, Kabinentypen oder Reisezeiten, um zu demonstrieren, dass sich die Marke an sie erinnert und sie schätzt.
- Angebote sollten sich über den gesamten Journey verbreiten, beginnend mit inspirierenden Inhalten und fortschreitend zu finanziellen Anreizen, nur wenn frühere Nachrichten keine Interaktion erzeugen.
- Kundendaten müssen bei Buchungen über Offline-Kanäle wie Reisebüros oder Callcenter mit dem Reservierungssystem abgeglichen werden, um zu vermeiden, dass Win-back-Nachrichten an tatsächlich aktive Kunden gesendet werden.


## Empfehlungen für dynamische Routen

Zeigen Sie personalisierte Reisepläne und Ziele für Kreuzfahrten basierend auf den vorherigen Buchungen des Kunden, dem Navigationsverlauf und den angegebenen Voreinstellungen an. Wenn Reisende Routen sehen, die auf ihre Interessen und ihren Reisestil zugeschnitten sind, interagieren sie tiefer mit der Planungserfahrung und gehen schneller zur Buchung über.

### Auswirkung auf den Betrieb

Personalisierte Empfehlungen zur Reiseroute steigern die Interaktion mit Reiseroutenseiten um 20-30 %, helfen Kunden, die richtige Reise schneller zu finden, und reduzieren die Abbrüche, die auftreten, wenn sich Reisende von zu vielen Optionen überfordert fühlen.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz personalisiert Website-Inhalte für identifizierte Besucher und nutzt deren Profildaten und Verhaltensverlauf, um die relevantesten Routen und Ziele aufzudecken.

### Technische Überlegungen

- Die Empfehlungslogik für die Reiseroute muss neben den Zielinteressen auch Segel- oder Aufenthaltsdaten, Abflughäfen und Dauerpräferenzen beinhalten, um Optionen zu präsentieren, die für den Kunden sowohl attraktiv als auch praktisch sind.
- Die Integration mit dem zentralen Reservierungssystem stellt sicher, dass die empfohlenen Reiserouten über verfügbare Inventare verfügen und aktuelle Preise widerspiegeln, sodass Frustration durch die Förderung ausverkaufter Segelreisen oder voll gebuchter Immobilien vermieden wird.
- Saisonale Faktoren sollten die Empfehlungen stark beeinflussen; Kunden, die zuvor Sommerkreuzfahrten im Mittelmeer gebucht haben, sollten ähnliche saisonale Optionen anstelle von saisonalen Alternativen sehen.
- [!DNL Experience Platform] Zusammenführungsrichtlinien für Profile müssen das Browserverhalten von mehreren Geräten korrekt vereinheitlichen, damit die auf Mobilgeräten durchgeführten Untersuchungen in den Desktop-Empfehlungen berücksichtigt werden.


## Kürzlich durchsuchte Produkte auf Homepage

Zeigen Sie kürzlich angesehene Kreuzfahrten, Hotels oder Ziele auf der Homepage an, um Besucher an ihr Interesse zu erinnern und sie zu wiederkehrenden Besuchen zu ermutigen. Reisende recherchieren vor der Buchung oft über mehrere Sitzungen hinweg und das Aufdecken ihrer früheren Interessen beseitigt den Reibungsverlust, dass sie bei jeder Rückkehr ihre Suche beginnen müssen.

### Auswirkung auf den Betrieb

Die Anzeige kürzlich durchsuchter Reiseprodukte auf der Homepage steigert die Interaktion mit Rückbesuchen um 15-20 %, sodass Kunden leichter von ihrem Ausgangspunkt profitieren und den Weg zur Buchung verkürzen können.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz verwendet die gespeicherten Profildaten des Besuchers, um zuvor angezeigte Elemente auf der Homepage zu rendern und so Kontinuität über Browser-Sitzungen hinweg zu schaffen.

### Technische Überlegungen

- Kürzlich angezeigte Daten müssen über Geräte und Sitzungen hinweg mithilfe der Identitätsauflösung bestehen bleiben, sodass ein Kunde, der auf seinem Smartphone surft, die gleichen Elemente sieht, wenn er auf einem Desktop zurückkehrt.
- Angezeigte Artikel sollten den aktuellen Preis- und Verfügbarkeitsstatus anzeigen, mit klaren Indikatoren, wenn eine zuvor angezeigte Option nicht mehr verfügbar ist oder wenn der Preis seit dem letzten Besuch geändert wurde.
- Das Zeitfenster für angezeigte Artikel sollte auf Reisebuchungszyklen abgestimmt sein. Die Anzeige einer Kreuzfahrt, die vor drei Monaten angesehen wurde, kann immer noch relevant sein, im Gegensatz zu einem Einzelhandelsprodukt, das vor so langer Zeit angesehen wurde.
- Aus Datenschutzgründen müssen kürzlich angezeigte Inhalte mit dem Einverständnisstatus des Kunden verknüpft sein. Eine Option zum Löschen des Browser-Verlaufs sollte leicht zugänglich sein.


## Modale Exitintent mit zielgerichteten Angeboten

Wenn ein Besucher die Absicht zum Beenden zeigt, zeigt er ein personalisiertes modales Fenster mit relevanten Angeboten an, die auf seinem Browser-Verhalten während der Sitzung basieren. Einen abreisenden Besucher mit einem überzeugenden, kontextuell relevanten Angebot anzusprechen, bietet eine letzte Möglichkeit, Interesse in eine Buchung umzuwandeln, bevor er abreist.

### Auswirkung auf den Betrieb

Exitintent-Modale mit personalisierten Reiseangeboten erzielen eine Konversionsrate von 5-10 % bei Besucherinnen und Besuchern, die ansonsten ohne Buchung abreisen würden, wodurch Umsätze erfasst werden, die vollständig verloren gehen würden.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Dieser Ansatz nutzt eine zentralisierte Entscheidungslogik, um alle verfügbaren Angebote zu bewerten und basierend auf ihrem Sitzungsverhalten und ihren Profildaten das für den abreisenden Besucher relevanteste Angebot auszuwählen.

### Technische Überlegungen

- Die Absichtserkennung bei der Reisebuchung auf Websites muss dem Multi-Tab-Browsing-Verhalten Rechnung tragen, da Reisende häufig mehrere Reiserouten oder Eigenschaften auf separaten Registerkarten öffnen, ohne tatsächlich zu gehen.
- Die Angebotsauswahl sollte widerspiegeln, was der Besucher während seiner Sitzung durchsucht hat, und einen Rabatt auf das spezifische Ziel oder die spezifische Eigenschaft, die er erkundet hat, anstelle einer allgemeinen Promotion darstellen.
- Die Häufigkeit der modalen Kommunikation sollte strikt begrenzt sein, um zu verhindern, dass Besucher bei jedem Besuch dasselbe Angebot sehen, was die Dringlichkeit und die wahrgenommene Exklusivität der Promotion untergräbt.
- [!DNL Journey Optimizer] Regeln für die Angebotseignung sollten die Treuestufe und den Buchungshistorie des Besuchers berücksichtigen, um angemessen bewertete Anreize zu bieten und Premium-Gästen sinnvolle Vergünstigungen anstelle kleiner Rabatte anzubieten.


## Treueprogramm Personalization

Personalisieren Sie das Website-Erlebnis, die Angebote und die Kommunikation basierend auf der Treuestufe, dem Punktesaldo und dem Interaktionsverlauf des Kunden. Mitglieder des Treueprogramms, deren Status sich auf allen Touchpoints widerspiegelt, fühlen sich anerkannt und geschätzt. Dies stärkt ihr Engagement für die Marke und fördert ihre Weiterentwicklung.

### Auswirkung auf den Betrieb

Die mehrstufige Personalisierung steigert die Interaktion der Mitglieder des Treueprogramms um 25-35 %, vertieft die Beziehung und beschleunigt das Verdienst- und Tilgungsverhalten, das den langfristigen Umsatz sichert.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Dieser Ansatz kombiniert Journey-Orchestrierung mit Echtzeit-Entscheidungsfindung, um für jedes Mitglied des Treueprogramms das richtige Angebot über den richtigen Kanal bereitzustellen und es an seine Stufe, seine Vorlieben und die jüngsten Aktivitäten anzupassen.

### Technische Überlegungen

- Treueprogramm-Daten, einschließlich Stufenstatus, Punktesalden und Einkommensverlauf, müssen erfasst und auf dem neuesten Stand gehalten werden, um sicherzustellen, dass die Website-Personalisierung und die Angebote den tatsächlichen Status des Kunden widerspiegeln.
- Statusspezifische Vorteile wie frühzeitiger Zugriff auf Buchungen, kostenlose Upgrades und exklusive Preise müssen am Einlösungspunkt durchgesetzt werden, was eine enge Integration in die Reservierungs- und Preissysteme erfordert.
- Änderungen des Punktesaldos aus Buchungen, Aufenthalten und Partnertransaktionen sollten die Neuberechnung der Personalisierungsregeln nahezu in Echtzeit durchführen, damit Kunden, die gerade genug Trigger für eine Belohnung verdient haben, diese Option sofort sehen.
- [!DNL Real-Time Customer Data Platform] Audiences sollten nach Treuestufen und wichtigen Interaktionsmeilensteinen strukturiert sein, wie z. B. die Annäherung an die nächste Stufe oder das Risiko einer Abstufung der Stufe.


## Multi-Channel-Buchungserinnerungen

Senden Sie personalisierte Buchungserinnerungen per E-Mail, SMS und Push-Benachrichtigungen an Kunden, die begonnen, aber ihre Reservierungen nicht abgeschlossen haben. Reisende beginnen häufig den Buchungsprozess und werden unterbrochen, und wenn sie sie über ihre bevorzugten Kanäle mit einer Erinnerung und ihren gespeicherten Reisedetails erreichen, werden sie zum Abschluss der Reservierung zurückgebracht.

### Auswirkung auf den Betrieb

Multi-Channel-Buchungserinnerungen verbessern die Buchungsabschlussraten um 20-30 % und erzielen so signifikante Umsätze von Kunden, die eine Buchung beabsichtigten, aber vor dem Abschluss übersprungen wurden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz erinnert Trigger automatisch daran, wenn ein unvollständiges Buchungsereignis erkannt wird, wodurch zeitnahe Nachrichten über die bevorzugten Kanäle des Kunden gesendet werden.

### Technische Überlegungen

- Die Kanalauswahllogik sollte die Kommunikationsvoreinstellungen der Kundinnen und Kunden berücksichtigen und den Versand auf der Grundlage früherer Interaktionsmuster optimieren, indem sie Push-Benachrichtigungen an Kundinnen und Kunden sendet, die gut auf Mobilgeräte reagieren, und E-Mails an diejenigen sendet, die es bevorzugen.
- Der Inhalt der Erinnerung muss einen Deep-Link enthalten, über den der Kunde direkt zu seiner gespeicherten Buchung zurückkehrt, wobei alle Auswahlen intakt bleiben müssen. So entfällt der Reibungsverlust bei der erneuten Eingabe von Reisedaten, Zimmervoreinstellungen und Gastdetails.
- Timing- und Häufigkeitsregeln sollten kanalübergreifend koordiniert werden, um den Kunden nicht zu überfordern. Eine E-Mail und eine Push-Benachrichtigung über dieselbe Buchung sollten angemessen verteilt sein, anstatt gleichzeitig gesendet zu werden.
- Bei der Integration mit dem Immobilienverwaltungs- oder zentralen Reservierungssystem muss vor dem Versand der Erinnerung überprüft werden, ob der ursprünglich ausgewählte Zimmertyp, der Tarif und die Daten noch verfügbar sind. Die Nachricht wird aktualisiert, wenn sich die Verfügbarkeit geändert hat.


## Saisonkampagne Personalization

Personalisieren Sie Kampagnen und Angebote basierend auf saisonalen Präferenzen, vergangenen saisonalen Buchungen und aktuellen saisonalen Trends. Reisende sind stark von den Jahreszeiten beeinflusst, und Kampagnen, die mit ihren nachgewiesenen saisonalen Interessen und aktuellen Reisetrends übereinstimmen, sind viel überzeugender als allgemeine Werbeaktionen.

### Auswirkung auf den Betrieb

Saisonale personalisierte Kampagnen steigern die saisonale Buchungsumrechnung um 15-25 %, sodass sich die Marketing-Investitionen auf die Reiseziele und -produkte konzentrieren, die am ehesten bei jedem Kunden Anklang finden.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für ausgehende Nachrichten &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Batch. Dieser Ansatz liefert personalisierte saisonale Kampagnennachrichten an ein großes Publikum auf geplanter Basis, wobei die Kunden nach ihren saisonalen Reisemustern und -präferenzen segmentiert werden.

### Technische Überlegungen

- Saisonale Präferenzprofile von Kunden sollten aus historischen Buchungsdaten erstellt werden, um Muster wie konsistente Sommerferien am Strand oder Winterskitouren zu identifizieren, um das Targeting von Kampagnen zu informieren.
- Die Kampagnenplanung muss die Vorlaufzeiten der Reisebranche berücksichtigen. Die Kampagnen für den Sommerurlaub sollten im Frühjahr beginnen, wenn die Familien planen, und nicht im Juni, wenn die meisten Buchungen bereits vorgenommen werden.
- Die Preise und Verfügbarkeitsdaten für das saisonale Inventar müssen integriert werden, damit die beworbenen Angebote die Echtzeitpreise und die tatsächliche Verfügbarkeit von Zimmern oder Kabinen während der genannten Reisezeiten widerspiegeln.
- [!DNL Experience Platform] Zielgruppen sollten saisonale Präferenzdaten mit aktuellen Indikatoren kombinieren, um Kunden zu priorisieren, die sich in ihrem typischen Planungsfenster für die kommende Saison befinden.


## Empfehlungen für Gruppenbuchungen

Identifizieren Sie Kunden, die häufig Gruppenreisen buchen, und empfehlen Sie proaktiv Gruppenpakete, familienfreundliche Optionen oder Mehrzimmerbuchungen. Gruppenbuchungen stellen einen deutlich höheren Umsatz pro Transaktion dar, und Kunden mit einem nachgewiesenen Muster von Gruppenreisen reagieren gut auf kuratierte Optionen, die den Planungsprozess vereinfachen.

### Auswirkung auf den Betrieb

Proaktive Empfehlungen für die Gruppenbuchung erhöhen den durchschnittlichen Bestellwert um 1.000 bis 3.000 US-Dollar pro Buchung, wobei der gesamte Wert von Gruppenreisetransaktionen erfasst wird, die andernfalls auf mehrere einzelne Buchungen aufgeteilt werden könnten.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Bei diesem Ansatz werden KI-gesteuerte Modelle verwendet, die aus den Buchungsmustern und dem Verhalten der Kunden lernen, um jedem Kunden die relevantesten Gruppenreiseoptionen zu empfehlen.

### Technische Überlegungen

- Zur Identifizierung von Gruppenreisen muss der Buchungsverlauf analysiert werden, um Muster zu ermitteln, z. B. Mehrzimmerreservierungen, Buchungen mit mehreren Passagieren und koordinierte Buchungen, die für dieselben Daten und dasselbe Ziel nahe beieinander erfolgen.
- Gruppenpaketpreise müssen dynamisch aus dem Reservierungssystem gezogen werden, da Gruppenpreise oft von individuellen Preisen abweichen und minimale Parteigrößen oder Vorbuchungsfenster erfordern können.
- Der Empfehlungsinhalt sollte auf die individuellen Bedürfnisse von Gruppenorganisatoren zugeschnitten sein, einschließlich Informationen zu den gastronomischen Optionen für Gruppen, Besprechungsräumen, Rabatten bei der Blockbuchung und der Verfügbarkeit von Gruppenausflügen.
- [!DNL Real-Time Customer Data Platform] der Profilanreicherung sollten Kundinnen und Kunden auf der Grundlage ihrer Buchungsmuster als Gruppenreiseveranstalter gekennzeichnet werden, um gezielte Kampagnen während der Spitzenzeiten der Gruppenplanung zu ermöglichen, z. B. während der Familienzusammenführungssaison oder in Rückzugsfenstern für Unternehmen.
