---
title: Anwendungsfälle für Finanzdienstleistungen
description: Erfahren Sie, wie Finanzdienstleister Adobe Experience Platform verwenden, um Produktangebote zu personalisieren, Abwanderungen zu verhindern und die Kundenbeziehungen zu vertiefen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 1f22d684-11bd-473d-8b10-5f88cb0cd088
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '4039'
ht-degree: 0%

---

# Anwendungsfälle für Finanzdienstleistungen

Finanzdienstleister verlassen sich auf Adobe Experience Platform, um Kundendaten über Bank-, Kredit- und Investitionskanäle hinweg zu vereinheitlichen und so personalisierte Erlebnisse zu ermöglichen, die Beziehungen stärken und das Wachstum fördern. Durch die Kombination von Kontoaktivität, Transaktionsverlauf und Verhaltenssignalen können diese Unternehmen das richtige Angebot zum richtigen Zeitpunkt bereitstellen und gleichzeitig das Vertrauen und die Compliance aufrechterhalten, die ihre Kunden erwarten.

## Hochwertige Bleipflege

Identifizieren Sie hochwertige Interessenten anhand von Profildaten und -verhalten und unterstützen Sie sie mit personalisierten Inhalten und Angeboten durch automatisierte Journey. Durch die Kombination von demografischen Details, Browsing-Aktivitäten und Interaktionssignalen können Finanzinstitute die Leads priorisieren, die am wahrscheinlichsten konvertiert werden, und sie durch einen maßgeschneiderten Weg zu Kunden führen.

### Auswirkung auf den Betrieb

Unternehmen, die hochwertige Lead-Pflege implementieren, erzielen höhere Lead-zu-Kunden-Konversionsraten und bauen gleichzeitig eine gesündere, berechenbarere Vertriebspipeline auf.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um automatisierte Nurture-Sequenzen zu erstellen, die sich auf der Grundlage von Interaktions- und Bereitschaftssignalen potenzieller Kundinnen und Kunden anpassen. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenzierten Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf Interaktionsmetriken erfordert - eine einzelne ausgelöste Nachricht kann die adaptive Nurturing-Logik oder Abhängigkeitslogik zwischen den Qualifizierungsschritten nicht berücksichtigen.

### Technische Überlegungen

- CRM-Lead-Scoring-Daten und Website-Verhaltensereignisse in einheitliche Interessentenprofile integrieren, um die Journey-Einstiegs- und Verzweigungslogik zu unterstützen.
- Stellen Sie sicher, dass Einverständnis- und Opt-in-Voreinstellungen bei jedem Touchpoint durchgesetzt werden, insbesondere bei Telefon- und E-Mail-Kontakten, die durch Finanzmarketing-Vorschriften geregelt sind.
- Konfigurieren Sie Journey-Einschränkungen, um zu vermeiden, dass potenzielle Kunden während kurzer Auswertungsfenster mit mehreren Nachrichten überfordert werden.
- Berücksichtigen Sie die Datenlatenz zwischen Interaktionen mit Zweigstellen oder Beratern und die digitale Interaktion, um sicherzustellen, dass Puture Messaging relevant ist.


## Produktempfehlung für Bestandskunden

Empfehlen Sie Bestandskunden relevante Finanzprodukte wie Kreditkarten, Kredite und Anlageprodukte auf Grundlage ihres Profils, ihrer Transaktionshistorie und ihres Lebenszyklus. In diesem Anwendungsbeispiel werden alltägliche Kontodaten in umsetzbare Einblicke umgewandelt, die für jeden Kunden das nächstbeste Produkt ergeben.

### Auswirkung auf den Betrieb

Personalisierte Produktempfehlungen steigern die Akzeptanzrate von Produkten und erhöhen den Kundenlebenszeitwert messbar, indem sie den Anteil an der digitalen Brieftasche erhöhen.

### Implementieren

Verwenden Sie das [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)-Muster, um jeden Kunden anhand geeigneter Produktangebote in Echtzeit zu bewerten und die Empfehlungen nach Relevanz und Geschäftspriorität zu ordnen. Dies ist das richtige Muster, wenn bei der Angebotsauswahl finanzielle Eignungsregeln und regulatorische Eignungsbegrenzungen berücksichtigt werden müssen - Begrenzungen, die eine geregelte Entscheidungslogik erfordern, anstatt nur eine Rangliste der verhaltensbezogenen Affinität zu erstellen.

### Technische Überlegungen

- Vereinheitlichen Sie Transaktionsdaten, Kontostände und Produktbestände in einem einzigen Kundenprofil, sodass Entscheidungsmodelle einen vollständigen Überblick über bestehende Beziehungen haben.
- Wenden Sie finanzielle Eignungsregeln und regulatorische Eignungsbegrenzungen als feste Leitplanken innerhalb der Entscheidungs-Engine an, bevor Sie Angebote bewerten.
- Koordinieren Sie den Versand von Angeboten über Online-Banking-, Mobile-App-, E-Mail- und Advisor-Kanäle, um widersprüchliche oder doppelte Empfehlungen zu vermeiden.
- Führen Sie eine Frequenzlimitierung pro Produktkategorie ein, um Empfehlungsmüdigkeit zu vermeiden, insbesondere für hochwertige Produkte wie Hypotheken und Investitionskonten.


## Kampagnen zur Verhinderung von Abwanderungen

Identifizieren Sie Kundinnen und Kunden, bei denen das Risiko einer Abwanderung besteht, mithilfe einer KI-gestützten Abwanderungsprognose und interagieren Sie mit Aufbewahrungsangeboten und personalisierter Kommunikation. Durch die frühzeitige Erkennung von Ausstiegssignalen können Finanzinstitute eingreifen, bevor ein Kunde Konten schließt oder Vermögenswerte an einen anderen Ort verschiebt.

### Auswirkung auf den Betrieb

Proaktive Maßnahmen zur Vermeidung von Abwanderungen tragen dazu bei, die Kundenabwanderung zu reduzieren, wiederkehrende Umsatzströme zu schützen und die Kosten für den Kundenaustausch zu senken.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster für Journey zur Kundenbindung von Triggern, wenn die Abwanderungsrisikowerte definierte Schwellenwerte überschreiten, mit eingebetteter Entscheidungsfindung, um das überzeugendste Kundenbindungsangebot auszuwählen. Dies ist das richtige Muster, wenn der Journey die Bereitstellung kanalübergreifend koordinieren muss, um doppelte Aufbewahrungsangebote zu verhindern, und wenn die Angebotsauswahl Risikobewertungsschwellen und geschäftliche Einschränkungen erfordert - eine mehrstufige Orchestrierung allein bietet nicht die Echtzeit-Entscheidungsebene, die erforderlich ist, um das optimale Aufbewahrungsangebot pro Kunde auszuwählen.

### Technische Überlegungen

- Übertragen Sie Account-Aktivitätstrends, den Verlauf von Service-Interaktionen und die Interaktionshäufigkeit in [!DNL Customer AI] Abwanderungsneigungsmodelle, um Risikobewertungen zu generieren.
- Definieren Sie für Produktlinien spezifische Abwanderungsrisikoschwellen, da sich die Auskoppelungssignale für Girokonten von denen für Anlageportfolios unterscheiden.
- Überprüfen Sie die Targeting- und Unterdrückungskriterien mit Ihren Rechts- und Datenschutz-Teams, um sicherzustellen, dass die geltenden Vorschriften für faire Kreditvergabe und Gleichbehandlung eingehalten werden, bevor Sie Aufbewahrungsangebote aktivieren.
- Erstellen Sie eine Unterdrückungslogik, um Kundinnen und Kunden auszuschließen, die aufgrund von Betrug oder Compliance-Aktionen abwandern, wenn eine Bindung unangemessen wäre.


## Personalisiertes Konto-Dashboard

Personalisieren Sie das Online-Banking-Dashboard und das Mobile-App-Erlebnis basierend auf den Kontoaktivitäten, Voreinstellungen und finanziellen Zielen jedes Kunden. Ein maßgeschneidertes Dashboard hilft Kunden, das Wichtigste zu finden und relevante Einblicke zu erhalten, ohne dass sie eine Suche durchführen müssen.

### Auswirkung auf den Betrieb

Personalisierte Dashboards steigern die Interaktionsraten und verbessern die Kundenzufriedenheit deutlich, indem sie das digitale Banking intuitiv und relevant gestalten.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um in Echtzeit personalisierte Inhaltsbausteine, Produkt-Spotlights und finanzielle Einblicke in authentifizierten digitalen Erlebnissen bereitzustellen. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und Kontoaktivitäten gesteuert wird und nicht von einem verhaltensbezogenen Affinitätsmodell, und wenn die Latenz von Untersekunden für das Benutzererlebnis entscheidend ist.

### Technische Überlegungen

- Nutzen Sie [!DNL Edge Network] für Personalisierungsentscheidungen im Sekundenbereich innerhalb authentifizierter Banksitzungen, bei denen sich die Latenz direkt auf das Benutzererlebnis auswirkt.
- Aggregieren Sie Transaktionsdaten in vorab berechneten Profilattributen wie Ausgabenkategorien und Spartrends, um Berechnungen großer Datensätze in Echtzeit zu vermeiden.
- Einhaltung von Barrierefreiheitsstandards und Sicherstellung, dass personalisierte Inhalte dieselben Offenlegungsanforderungen erfüllen wie statische Inhalte.
- Koordinieren Sie die Personalisierungslogik zwischen Web- und mobilen Kanälen, damit Kunden unabhängig vom Gerät ein konsistentes Erlebnis sehen.


## Produktangebote auf Basis der Lebensphase

Identifizieren Sie Kunden, die in neue Lebensphasen eintreten, wie z. B. Heirat, Wohnungskauf oder Pensionierung, und bieten Sie proaktiv relevante Finanzprodukte und -dienstleistungen an. Das Antizipieren dieser Meilensteine ermöglicht es den Instituten, sich in entscheidenden Finanzsituationen als vertrauenswürdige Partner zu positionieren.

### Auswirkung auf den Betrieb

Durch Angebote, die über das gesamte Produktstadium hinweg ausgelöste Neuerungen erzielen, werden höhere Produktakzeptanzraten erzielt, die die allgemeinen Kampagnen übertreffen, während die langfristigen Kundenbeziehungen gestärkt werden.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Lebensphasenindikatoren zu erkennen und Multi-Touch-Journey mit integrierter Angebotsauswahl zu orchestrieren, die auf jeden Meilenstein zugeschnitten ist. Dies ist das richtige Muster, wenn der Journey in wichtigen finanziellen Momenten die Bereitstellung kanalübergreifend koordinieren muss und wenn die Angebotsauswahl Eignungsprüfungen und Geschäftsregeln erfordert - eine mehrstufige Orchestrierung allein bietet nicht die Entscheidungsebene, die erforderlich ist, um Compliance und Relevanz sicherzustellen.

### Technische Überlegungen

- Erstanbietersignale wie Adressänderungen, gemeinsame Kontoeröffnungen und große Einlagen mit zulässigen Drittanbieterdaten kombinieren, um auf Stadienübergänge im Lebenszyklus zu schließen.
- Seien Sie beim Umgang mit sensiblen Lebensereignissen vorsichtig, da falsch abgeleitete Meilensteine das Vertrauen untergraben können.
- Die regulatorische Eignung wird in Offer Decisioning überprüft, sodass die empfohlenen Produkte mit der geprüften Finanzlage des Kunden übereinstimmen.
- Erstellen Sie Abkühlungszeiträume zwischen den Kampagnen in der Lebensphase, um zu verhindern, dass sich die Reichweite überschneidet, wenn mehrere Indikatoren in einem kurzen Fenster ausgelöst werden.


## Transaktionsbasierte Warnhinweise und Empfehlungen

Senden Sie Echtzeitwarnungen für Transaktionen und geben Sie personalisierte Empfehlungen, die auf Ausgabenmustern und Kontoaktivitäten basieren. Zeitnahe, relevante Benachrichtigungen halten Kunden auf dem Laufenden und schaffen natürliche Momente, um hilfreiche finanzielle Beratung zu bieten.

### Auswirkung auf den Betrieb

Transaktionsbasierte Warnhinweise fördern ein starkes Engagement, verbessern das Sicherheitsbewusstsein und schaffen hochwertige Touchpoints für personalisierte Empfehlungen.

### Implementieren

Verwenden Sie das [ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um in Echtzeit auf Transaktionsereignisse mit Warnhinweisen und kontextuell relevanten Empfehlungen zu reagieren. Dies ist das richtige Muster, wenn der Trigger eher ein Systemereignis als ein Kundenverhalten ist und wenn die erforderliche Kommunikation sofort und reaktiv statt einer nachhaltigen Pflegeresequenz erfolgt - die Warnungslatenz wirkt sich direkt auf die Sicherheitseffektivität aus.

### Technische Überlegungen

- Transaktionsereignisse über eine Streaming-Pipeline mit Bereitstellungsanforderungen mit geringer Latenz erfassen, da Sicherheitswarnungen ihren Wert verlieren, wenn sie um mehr als einige Minuten verzögert werden.
- Wenden Sie kundendefinierte Warnhinweiseinstellungen und -schwellen an, damit Benachrichtigungen individuelle Einstellungen widerspiegeln und nicht universelle Regeln.
- Trennen Sie in der Messaging-Architektur obligatorische Sicherheitswarnungen von optionalen Empfehlungsnachrichten, um sicherzustellen, dass Compliance-Benachrichtigungen nie unterdrückt werden.
- Berücksichtigung hoher Transaktionsvolumina in Spitzenzeiten wie Zahlungstagen und Feiertagen durch die Entwicklung von Durchsatzkapazitäten, die mit der Nachfrage skalieren.


## Rückforderung bei Abbruch einer Kreditkartenanwendung

Identifizieren Sie Kunden, die mit Kreditkartenanträgen begonnen, diese jedoch nicht abgeschlossen haben, und setzen Sie sie mit personalisierten Nachrichten und Angeboten erneut in Kontakt. Bei einem Programmabbruch handelt es sich um eine Zielgruppe mit hohen Absichten, die häufig nur einen kleinen Anstoß benötigt, um den Prozess abzuschließen.

### Auswirkung auf den Betrieb

Abbruch-Recovery-Kampagnen verbessern die Abschlussraten von Anwendungen und erhöhen direkt die Neukontoakquise aus einer Audience, die bereits Interesse bekundet hat.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um Anwendungsabbruchsereignisse und zeitnahe Folgenachrichten von Triggern zu erkennen, die häufige Abbruchgründe behandeln. Dies ist das richtige Muster, wenn eine diskrete Kundenaktion (Abbruch) der Trigger ist und die erforderliche Antwort eine zeitkritische Nachricht ist, die gesendet wird, bevor die Anwendungsdaten veraltet sind. Eine mehrstufige Sequenz kann die Dringlichkeit und das enge Wiederherstellungsfenster nicht berücksichtigen.

### Technische Überlegungen

- Erfassen Sie den spezifischen Schritt, bei dem die Anwendung aufgegeben wurde, um die Messaging-Funktion anzupassen, da jemand, der bei der Identitätsüberprüfung abgebrochen hat, andere Zusicherungen benötigt als jemand, der bei der Überprüfung der Bedingungen gegangen ist.
- Arbeiten Sie vor der Bereitstellung mit Ihren Rechts- und Compliance-Teams zusammen, um zu bestätigen, dass alle Recovery-Kommunikationen die geltenden Offenlegungsanforderungen für das Kreditmarketing und die kanalspezifischen Einverständnisregeln erfüllen.
- Implementieren Sie eine Zeitverfallslogik, damit die Recovery-Reichweite nach einem definierten Zeitfenster beendet wird, da veraltete Anwendungsdaten für die Vorqualifizierung möglicherweise nicht mehr gültig sind.
- Abstimmung mit dem Anwendungssystem, um Wiederherstellungsnachrichten für Antragsteller zu unterdrücken, die über einen anderen Kanal abgeschlossen haben, z. B. einen Zweigbesuch oder einen Telefonanruf.


## Empfehlungen für Investment Portfolio

Geben Sie personalisierte Anlageempfehlungen auf der Grundlage des Risikoprofils jedes Kunden, seiner Investitionshistorie und seiner finanziellen Ziele. Datengestützte Portfolioberatung hilft Kunden, fundierte Entscheidungen zu treffen und gleichzeitig ihre Interaktion mit Vermögensverwaltungsdiensten zu vertiefen.

### Auswirkung auf den Betrieb

Personalisierte Anlageempfehlungen fördern die verstärkte Akzeptanz von Anlageprodukten und verbessern die Portfoliodiversifizierung innerhalb des Kundenstamms.

### Implementieren

Verwenden Sie das [Verhaltens-Recommendations](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)-Muster, um das Investitionsverhalten und die Präferenzen zu analysieren, und legen Sie dann relevante Portfolioempfehlungen über digitale Kanäle und Beratungs-Tools offen. Dies ist das richtige Muster, wenn der Elementsatz (das Anlageuniversum) groß ist und die Auswahl durch Verhaltensauffinität und Risikoausrichtung gesteuert wird - und nicht durch einen begrenzten Satz von Angeboten, die durch strenge Eignungsregeln oder Entscheidungen über die Eignungsprüfung allein geregelt sind.

### Technische Überlegungen

- Integrieren Sie Brokerage- und Depotdaten-Feeds, um einen genauen, aktuellen Überblick über die aktuellen Bestände und Zuweisungen jedes Kunden zu erhalten.
- Durchsetzung der durch die Wertpapiervorschriften vorgeschriebenen Eignungsanforderungen, sodass die Empfehlungen den dokumentierten Risikotoleranz- und Anlagezielen des Kunden entsprechen.
- Sie sollten personalisierte Anlageinhalte bei Bedarf eindeutig als pädagogische oder informative Inhalte kennzeichnen, was sie von formeller Anlageberatung unterscheidet, die treuhänderische Pflichten mit sich bringt.
- Aktualisieren Sie die Empfehlungsmodelle regelmäßig, um Marktveränderungen, Portfoliodrifts und Änderungen der Kundenziele Rechnung zu tragen.


## Betrugswarnung Personalization

Personalisieren Sie Warnungen zu Betrug und Sicherheitsmeldungen basierend auf den Kommunikationsvoreinstellungen jedes Kunden und dem Verlauf früherer Interaktionen. Maßgeschneiderte Warnhinweise erhöhen die Wahrscheinlichkeit, dass Kunden kritische Sicherheitsbenachrichtigungen bemerken, verstehen und darauf reagieren.

### Auswirkung auf den Betrieb

Personalisierte Warnhinweise zu Betrug verbessern die Reaktionsraten von Warnhinweisen, verbessern die Sicherheitskonformität und verringern die Anfälligkeit für verdächtige Aktivitäten.

### Implementieren

Verwenden Sie das [ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um über den bevorzugten Kanal jedes Kunden Betrugswarnungen mit kontextuellen Details zu senden, die die Bestätigung oder Anfechtung von Aktivitäten erleichtern. Dies ist das richtige Muster, wenn der Trigger eher ein Systemereignis als ein Kundenverhalten ist und wenn die erforderliche Kommunikation sofort und ohne Zeit für mehrstufige Sequenzen erfolgt - Warnungslatenz korreliert direkt mit dem finanziellen Verlustrisiko.

### Technische Überlegungen

- Priorisieren Sie die Versandgeschwindigkeit und -zuverlässigkeit vor allen anderen Design-Überlegungen, da die Warnungslatenz für Betrug direkt mit der finanziellen Verlustgefahr korreliert.
- Leiten Sie Warnhinweise über den verifizierten bevorzugten Kanal des Kunden weiter, während Sie Fallback-Kanäle beibehalten, um den Versand auch dann sicherzustellen, wenn der primäre Kanal ausfällt.
- Den Interaktionsverlauf von Warnhinweisen speichern, um die zukünftige Relevanz von Warnhinweisen zu verbessern und die falsch-positive Ermüdung von Kunden zu reduzieren, die häufig reisen oder atypische Käufe tätigen.
- Stellen Sie sicher, dass alle Betrug-Warnhinweise und Workflows den Sicherheitsvorschriften für Banken entsprechen und keine sensiblen Kontodetails in der Nachrichtenvorschau oder in Betreffzeilen verfügbar machen.


## Interaktion mit Treueprogrammen

Personalisieren Sie die Kommunikation, Belohnungen und Angebote im Treueprogramm, indem Sie die Angebotsarbitrierung in Echtzeit für Online-Banking, Mobile Apps, E-Mail und Zweigkanäle koordinieren, um zu verhindern, dass doppelte oder widersprüchliche Treueangebote dasselbe Mitglied gleichzeitig erreichen. Stufenbasierte Eignungsregeln - die bestimmen, auf welche Belohnungen, Promotions und Einlösungsoptionen jedes Mitglied zugreifen kann - werden auf der Entscheidungsebene durchgesetzt und nicht nur durch Segmentierung allein aufgelöst, um sicherzustellen, dass bei der Angebotsauswahl die Programmeinschränkungen auf allen Kanälen berücksichtigt werden. Treueangebote werden mit umfassenderen Marketing-Journey koordiniert, sodass Produkt- und Treueangebote nicht miteinander in Konflikt stehen. So erhalten die Mitglieder ein kohärentes Erlebnis, anstatt sich mit anderen Botschaften zu messen.

### Auswirkung auf den Betrieb

Personalisierte Interaktion mit Treueprogrammen erhöht die Programmteilnahme und führt zu einer messbar höheren Punktzahl, was die Wertwahrnehmung des Programms stärkt.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um die Treuekommunikation kanalübergreifend zu orchestrieren, mit eingebetteter Entscheidungsfindung, um die relevanteste Belohnung oder das relevanteste Angebot für jedes Mitglied auszuwählen. Dies ist das richtige Muster, wenn der Journey den Versand kanalübergreifend koordinieren muss, um Nachrichtenübermüdung und widersprüchliche Angebote zu verhindern, und wenn die Angebotsauswahl stufenbasierte Regeln und Mitgliederbeschränkungen erfordert - eine mehrstufige Orchestrierung allein bietet nicht die Entscheidungsebene in Echtzeit, die erforderlich ist, um Treueregeln und differenzierte Mitgliederbehandlung zu respektieren.

### Technische Überlegungen

- Synchronisieren Sie Daten der Treueplattform, einschließlich Stufenstatus, Punktesalden und Einlösungshistorie, nahezu in Echtzeit mit Kundenprofilen, um zu vermeiden, dass abgelaufene oder ungenaue Salden höher gestuft werden.
- Segmentieren Sie die Journey-Logik nach Ebene, um differenzierte Erlebnisse bereitzustellen, da Mitglieder der höheren Ebene eine exklusive Behandlung und frühzeitigen Zugriff auf Werbeaktionen erwarten.
- Koordinieren Sie Treuemeldungen mit umfassenderen Marketing-Kampagnen, um programmübergreifend Nachrichtenermüdung und widersprüchliche Angebote zu verhindern.
- Verfolgen Sie die Attribution von Rücknahmen auf allen Kanälen, um zu messen, welche personalisierte Kommunikation den höchsten ROI des Programms erzielt.


## Kampagnen zur Vorabgenehmigung von Hypotheken

Targeting von Kunden, die sich wahrscheinlich auf dem Markt für eine Hypothek befinden, basierend auf Profildaten, Verhaltenssignalen und Lebensphase-Indikatoren. Durch eine proaktive Kontaktaufnahme im Vorfeld der Genehmigung wird das Institut in einer der größten finanziellen Entscheidungen, die ein Kunde treffen wird, als eine praktische erste Wahl positioniert.

### Auswirkung auf den Betrieb

Gezielte Hypotheken-Vorabgenehmigungskampagnen erhöhen die Bewerbungsraten und verbessern das Kreditausgabevolumen, indem sie qualifizierte Interessenten zum richtigen Zeitpunkt erreichen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Hypothekenpotenziale durch eine Multi-Touch-Nurture-Sequenz zu führen, von der Bewusstseinsbildung bis zur Vorabgenehmigung und der Anpassung auf der Grundlage von Interaktions- und Qualifizierungssignalen. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen, mehrfachen Nachrichtenfluss über eine erweiterte Zeitleiste mit bedingter Verzweigung basierend auf Interaktions- und Qualifizierungssignalen erfordert - eine einzelne ausgelöste Nachricht kann die adaptive Nurturing-Logik oder die Übergabe an formale Anwendungsprozesse nicht berücksichtigen.

### Technische Überlegungen

- Kombinieren Sie Suchverhalten von Immobilien, Wachstumstrends beim Sparen und Leasingablaufsignale, um ein Tendenzmodell zu erstellen, das wahrscheinliche Hypothekensuchende identifiziert.
- Sicherstellen, dass alle Vorabbestätigungs-E-Mails den Vorschriften für die Hypothekenwerbung entsprechen, einschließlich der erforderlichen Angaben, der Genauigkeit des Zinssatzes und der gleichen Wohnsprache.
- Abstimmung des Kampagnenzeitplans mit Änderungen der Zinsertragsumgebung, sodass die Reichweite an den günstigen Kreditbedingungen ausgerichtet wird und veraltete Zinsreferenzen vermieden werden.
- Erstellen Sie Übergabe-Workflows an Kreditsachbearbeiter, damit digital gepflegte Leads reibungslos in den formellen Bewerbungs- und Zeichnungsprozess übergehen.


## Personalisierte Inhalte zur Finanzbildung

Stellen Sie personalisierte Inhalte, Tipps und Ressourcen zu Finanzfragen bereit, die auf dem Finanzprofil, den Zielen und den Interessen jedes Kunden basieren. Relevante Bildungsinhalte schaffen Vertrauen, verbessern die Finanzkompetenz und schaffen organische Möglichkeiten, relevante Produkte einzuführen.

### Auswirkung auf den Betrieb

Personalisierte Schulungsinhalte erhöhen die Interaktionsraten bei Inhalten und verbessern die Finanzkompetenz der Kunden, was wiederum zu einer sichereren Produktakzeptanz führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um eine kuratierte Sequenz von Schulungsinhalten kanalübergreifend bereitzustellen, wobei mithilfe von Decisioning Themen an die finanzielle Situation und Interessen jedes Kunden angepasst werden. Dies ist das richtige Muster, wenn der Journey die Bereitstellung kanalübergreifend mit progressiven Lernpfaden koordinieren muss und wenn die Themenauswahl Eignungsregeln erfordert, die auf dem Finanzprofil basieren - mehrstufige Orchestrierung allein bietet nicht die Entscheidungsebene, die erforderlich ist, um Inhalte an die finanzielle Situation des Kunden anzupassen oder Verstöße gegen Voraussetzungen zu verhindern.

### Technische Überlegungen

- Ordnen Sie Lehrinhalte Finanzprofilattributen wie Schuldenquote, Sparquote und Investitionserfahrung zu, um die Relevanz des Themas sicherzustellen.
- Tagging von Inhalten mit Schwierigkeitsgraden und vorausgesetzten Themen, um progressive Lernpfade zu erstellen, anstatt getrennte Einzelartikel bereitzustellen.
- Verfolgen Sie die Interaktion mit Inhalten auf Themenebene, um Personalisierungsmodelle zu verfeinern und neue Interessensbereiche im gesamten Kundenstamm zu identifizieren.
- Sicherstellen, dass sich pädagogische Inhalte klar vom Produktmarketing unterscheiden, um die Einhaltung behördlicher Auflagen zu gewährleisten und das Vertrauen der Kunden in die Objektivität des Programms zu wahren.


## KI-Finanzprodukthandbuch

Finanzdienstleister bieten Produktportfolios - Scheck- und Sparkonten, Kreditkarten, Kreditprodukte, Versicherungsoptionen und Anlageinstrumente - an, die für Kunden ohne personalisierte Anleitung schwer zu navigieren sind. Aufgrund gesetzlicher Einschränkungen können digitale Erlebnisse keine maßgeschneiderten Investitionsempfehlungen geben. Es ist jedoch von erheblichem Nutzen, Kunden dabei zu helfen, die Funktionsweise von Produkten zu verstehen, die ihren angegebenen Anforderungen entsprechen und den nächsten Schritt in Richtung Anwendung zu machen. Ein KI-Finanzproduktleitfaden bindet Kunden in natürliche Gespräche ein, stellt qualifizierte Fragen zu Finanzzielen und zum Lebensstadium und leitet sie zu den richtigen Produkten - ohne in ein reguliertes Beratungsgebiet zu gelangen.

### Auswirkung auf den Betrieb

Geführte Konversationsanalysen verbessern die Startraten für Produktanwendungen und verringern die Abbrüche zwischen Bekanntheit und Anwendung. Gleichzeitig werden Absichtssignale erfasst, die die Workflows für nachgelagerte Pflege und Beratung verbessern.

### Implementieren

Verwenden Sie das [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)-Muster. Dieser Ansatz stellt die Product Advisor Agent anhand der genehmigten Produktinhaltsbibliothek und Wissensdatenbank bereit und nutzt AEP Agent Orchestrator- und Echtzeit-Kundenprofildaten, um Kunden mithilfe eines Dialogfelds, das auf markengesteuerten, durch die Einhaltung überprüften Inhalten basiert, zu geeigneten Produkten zu führen. Dies ist das richtige Muster, wenn das Ziel eine interaktive, interaktive, interaktive, dialogorientierte Ermittlung ist, die Kunden dabei hilft, Finanzprodukte zu verstehen und selbst auszuwählen. Dies unterscheidet sich von ereignisgesteuertem Messaging, das einseitig ist und auf diskrete Kontoereignisse reagiert, und von personalisierten Web-Erlebnissen, die Produktinhalte passiv darstellen, ohne Kunden in einen qualifizierten Dialog einzubinden. Dies erfordert die Konfiguration von AEP Agent Orchestrator und Brand Governance.

### Technische Überlegungen

- Die Leitplanken der Brand Governance müssen mit Compliance und rechtlicher Überprüfung konfiguriert werden, um strenge Inhaltsgrenzen zu definieren: Der Agent muss Kunden zu geeigneten Produkten auf der Grundlage angegebener Bedürfnisse führen, ohne eine Anlageberatung darzustellen, und verbotene Themen (spezifische Renditeprognosen, Garantien, vergleichende Leistungsansprüche) müssen explizit definiert und durchgesetzt werden.
- Die Ebene der Inhaltsintegration muss auf von der Compliance genehmigten Produktbeschreibungen, Offenlegungen und FAQs basieren und nicht auf dynamisch generierten Ansprüchen, um sicherzustellen, dass jede Antwort des Agenten von Rechts- und Regulierungsteams vor der Bereitstellung geprüft wurde.
- Die Echtzeit-Kundenprofilsuche sollte Beziehungsdaten - vorhandene Produkte, Kontoinhaberschaft und Kundensegment - aufdecken, damit der Agent vermeiden kann, Produkte zu empfehlen, die der Kunde bereits besitzt, und die Anleitung auf die bestehende Beziehung des Kunden mit dem Institut zuschneiden kann.
- Die Übergabe von Live-Agenten muss für Szenarien konfiguriert werden, in denen die Kundenbedürfnisse den Umfang des Konversationshandbuchs überschreiten - wie z. B. komplexe Kreditsituationen oder Anfragen zur personalisierten Finanzplanung -, wobei der vollständige Konversationskontext an den empfangenden Berater übertragen wird, um zu vermeiden, dass sich der Kunde wiederholt.


## Produktakzeptanz Funnel und Analyse der Abwanderungstreiber

Analysieren Sie, wo Kundinnen und Kunden während der Eröffnung digitaler Konten, des Kreditantrags oder des Investitions-Onboarding-Flusses abbrechen, und identifizieren Sie die Verhaltenssignale, die der Produktzugehörigkeit vorausgehen. Finanzinstitute, die diese Absetzpunkte oder Abwanderungsausgangsstoffe nicht erkennen können, sind nicht in der Lage, zwischen Fehlern bei Produkterfahrungen und Disqualifizierung zu unterscheiden, was die Sanierungsbemühungen unpräzise macht.

### Auswirkung auf den Betrieb

Wenn Sie genau verstehen, wo Bewerber digitale Flüsse aufgeben und welche Verhaltensweisen Kontoschließungen vorausgehen, können Produkt- und Marketing-Teams Erlebnisverbesserungen priorisieren, die zu weniger Abbrüchen führen und die Kundenbindung verlängern.

### Implementieren

Verwenden Sie das [Muster Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) . Dieser Ansatz verbindet digitale Verhaltensdaten, CRM-Datensätze und Produktereignis-Streams mit Customer Journey Analytics, wo Fallout-Visualisierungen Abbruchschritte identifizieren und Unterschiede bei der Kohortenanalyse-Oberflächen-Bindung über Produktlinien und Akquise-Segmente hinweg aufzeigen. Dies ist das richtige Muster, wenn es darum geht, zu verstehen und zu diagnostizieren - zu analysieren, wo die Journey versagen und was die Abreibung antreibt - anstatt eine Audience für Unterdrückung zu aktivieren oder eine Retentionsmeldung auszulösen.

### Technische Überlegungen

- Digitale Anwendungsereignisdaten müssen jeden Schritt im Onboarding- oder Anwendungsfluss als diskrete Ereignisse mit konsistenten Schrittkennungen erfassen, damit die CJA-Fallout-Analyse genau isolieren kann, wo das Volumen verloren geht.
- CRM-Produktzugehörigkeits- und -Kontostatusdaten sollten in der CJA-Verbindung mit Verhaltensdaten verbunden werden, damit die Abwanderungsanalyse das Verhalten vor der Attrition mit den tatsächlichen Kontoschließungsergebnissen korrelieren kann.
- Data Governance-Kennzeichnungen müssen auf alle sensiblen Finanz- oder Identitätsfelder angewendet werden, die in der CJA-Verbindung enthalten sind, um die Offenlegung personenbezogener Daten in freigegebenen Dashboards zu verhindern, auf die Analysten ohne Data Steward-Berechtigung zugreifen.
- Die Kohortenanalyse zur Datenspeicherung erfordert eine ausreichende historische Datentiefe - in der Regel 12 bis 24 Monate -, sodass die Richtlinien zur Datensatzspeicherung in AEP so konfiguriert werden müssen, dass der für aussagekräftige Kohortenvergleiche erforderliche Ereignisverlauf beibehalten wird.

## Nächstbeste Offer Decisioning

Verwenden Sie eine zentralisierte Entscheidungslogik, um kanalübergreifend das relevanteste Angebot für jeden Kunden auszuwählen und Eignungsregeln, geschäftliche Einschränkungen und KI-gestützte Ranking-Strategien zu kombinieren. Durch die Zentralisierung der Angebotsauswahl wird sichergestellt, dass jede Kundin und jeder Kunde das kontextuell am besten geeignete Finanzproduktangebot erhält und dabei die regulatorischen Eignungsanforderungen und die geschäftlichen Zwänge berücksichtigt werden.

### Auswirkung auf den Betrieb

Finanzdienstleister, die zentralisierte Next-Best-Offer-Decisioning verwenden, sehen verbesserte Produktakzeptanzraten und höhere Umsätze pro Kundeninteraktion mit der stärksten Performance, wenn die Angebotsauswahl sowohl für Tendenzwerte als auch für Eignungs-Leitplanken berücksichtigt.

### Implementieren

Verwenden Sie das Muster [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md), um eine zentralisierte Entscheidungs-Engine zu erstellen, die die Kundeneignung bewertet, geschäftliche Einschränkungen anwendet und ein KI-Ranking verwendet, um das optimale Angebot für jede Kundeninteraktion über Web-, App- und ausgehende Kanäle auszuwählen. Dies ist das richtige Muster, wenn die Angebotsauswahl allein für eine regelbasierte Personalisierung zu komplex ist und eine Kombination aus Eignungslogik, Prioritätsregeln und adaptivem Ranking erfordert, um die optimale Auswahl aus einem Angebotskatalog zu treffen.

### Technische Überlegungen

- Die Regeln für die Angebotseignung müssen in der Entscheidungs-Engine aufbewahrt und mit den Produkteignungskriterien des Kernbankensystems oder der Produktsysteme synchronisiert werden, um zu verhindern, dass nicht infrage kommende Angebote angezeigt werden.
- KI-Ranking-Modelle erfordern ausreichende Schulungsdaten aus früheren Angebotsinteraktionen, um zuverlässige Tendenzwerte zu generieren. Neu eingeführte Produkte benötigen Fallback-Ranking-Strategien, bis genügend Daten gesammelt wurden.
- Durch regulatorische Anforderungen an Finanzdienstleistungen kann das eingeschränkt werden, was wem und über welchen Kanal angeboten werden kann; die Entscheidungslogik muss diese Einschränkungen als harte Regeln und nicht als weiche Präferenzen kodieren.
- Das Tracking der Angebotsmüdigkeit ist wichtig. Kunden, die wiederholt Angebote für dasselbe Produkt erhalten, das sie nicht akzeptiert haben, sollten dieses Angebot nach einer bestimmten Anzahl von Risiken nach ihrer Priorität ordnen oder unterdrücken lassen.


## Customer Journey Analytics-Dashboard

Erstellen Sie kanalübergreifende Analyse-Workspaces, die Web-, App-, E-Mail- und Callcenter-Daten kombinieren, um Kunden-Journey zu visualisieren, Abbrechpunkte zu identifizieren und die Kampagnenzuordnung zu messen. Ein einheitlicher Analytics-Arbeitsbereich bietet Produkt- und Marketing-Teams einen vollständigen Überblick darüber, wie Kunden kanalübergreifend und über Touchpoints hinweg arbeiten. So können sie datengestützte Entscheidungen darüber treffen, wo sie in die Verbesserung des Journey-Systems investieren sollten.

### Auswirkung auf den Betrieb

Finanzdienstleister mit Cross-Channel Journey Analytics verkürzen die Time-to-insight für Kampagnen- und Produkt-Teams und ermöglichen so eine schnellere Identifizierung wirkungsvoller Optimierungsmöglichkeiten über Onboarding-Flüsse, Anwendungstrichter und Kundendienst-Journey hinweg.

### Implementieren

Verwenden Sie das Muster [Kundenanalyse und Insight-Generierung](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) um Ereignis-Streams aus allen digitalen und Offline-Kanälen zu einem einheitlichen Analysedatensatz zusammenzufügen und dann Arbeitsbereich-Visualisierungen zu erstellen, die Journey-Flüsse, funnel-Abbrüche und Attributionsmodelle verfügbar machen. Dies ist das richtige Muster, wenn die Hauptanforderung nicht die Echtzeit-Aktivierung, sondern analytische insight und Visualisierung ist. Die Daten werden für Entscheidungen verwendet, anstatt für kundenorientierte Trigger-Aktionen.

### Technische Überlegungen

- Cross-Channel-Daten-Stitching erfordert eine konsistente Kundenkennung über alle Quellsysteme hinweg. Unternehmen mit fragmentierten Identitätsstrategien sehen unvollständige Journey, die die Analyse untergraben.
- Callcenter- und Offline-Interaktionsdaten müssen genau aufgenommen und mit einem Zeitstempel versehen werden, um sie in Bezug auf digitale Touchpoints korrekt in der Journey-Sequenz zu platzieren.
- Die Datenlatenz zwischen Quellsystemen und dem Analytics Workspace beeinflusst, wie schnell Einblicke verfügbar sind. Häufige Analyseanwendungsfälle können eine nahezu in Echtzeit erfolgende Aufnahme anstelle täglicher Batch-Feeds erfordern.
- Die Datenschutz- und Data Governance-Kontrollen müssen auf Analytics-Datensätze angewendet werden, um zu verhindern, dass persönlich identifizierbare Informationen in Dashboards angezeigt werden, auf die Analysten zugreifen können, die keinen Zugriff auf einzelne Kundendatensätze haben sollten.
