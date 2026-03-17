---
title: Anwendungsfälle für Finanzdienstleistungen
description: Erfahren Sie, wie Finanzdienstleister Adobe Experience Platform verwenden, um Produktangebote zu personalisieren, Abwanderungen zu verhindern und die Kundenbeziehungen zu vertiefen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 1%

---


# Anwendungsfälle für Finanzdienstleistungen

Finanzdienstleister verlassen sich auf Adobe Experience Platform, um Kundendaten über Bank-, Kredit- und Investitionskanäle hinweg zu vereinheitlichen und so personalisierte Erlebnisse zu ermöglichen, die Beziehungen stärken und das Wachstum fördern. Durch die Kombination von Kontoaktivität, Transaktionsverlauf und Verhaltenssignalen können diese Unternehmen das richtige Angebot zum richtigen Zeitpunkt bereitstellen und gleichzeitig das Vertrauen und die Compliance aufrechterhalten, die ihre Kunden erwarten.

## Hochwertige Bleipflege

Identifizieren Sie hochwertige Interessenten anhand von Profildaten und -verhalten und unterstützen Sie sie mit personalisierten Inhalten und Angeboten durch automatisierte Journey. Durch die Kombination von demografischen Details, Browsing-Aktivitäten und Interaktionssignalen können Finanzinstitute die Leads priorisieren, die am wahrscheinlichsten konvertiert werden, und sie durch einen maßgeschneiderten Weg zu Kunden führen.

### Auswirkung auf den Betrieb

Unternehmen, die hochwertige Lead-Pflege implementieren, verzeichnen in der Regel einen Anstieg der Lead-zu-Kunden-Konversionsraten um 25-35 % bei gleichzeitigem Aufbau einer gesünderen, berechenbareren Vertriebspipeline.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um automatisierte Nurture-Sequenzen zu erstellen, die sich auf der Grundlage von Interaktions- und Bereitschaftssignalen potenzieller Kundinnen und Kunden anpassen.

### Technische Überlegungen

- CRM-Lead-Scoring-Daten und Website-Verhaltensereignisse in einheitliche Interessentenprofile integrieren, um die Journey-Einstiegs- und Verzweigungslogik zu unterstützen.
- Stellen Sie sicher, dass Einverständnis- und Opt-in-Voreinstellungen bei jedem Touchpoint durchgesetzt werden, insbesondere bei Telefon- und E-Mail-Kontakten, die durch Finanzmarketing-Vorschriften geregelt sind.
- Konfigurieren Sie Journey-Einschränkungen, um zu vermeiden, dass potenzielle Kunden während kurzer Auswertungsfenster mit mehreren Nachrichten überfordert werden.
- Berücksichtigen Sie die Datenlatenz zwischen Interaktionen mit Zweigstellen oder Beratern und die digitale Interaktion, um sicherzustellen, dass Puture Messaging relevant ist.


## Produktempfehlung für Bestandskunden

Empfehlen Sie Bestandskunden relevante Finanzprodukte wie Kreditkarten, Kredite und Anlageprodukte auf Grundlage ihres Profils, ihrer Transaktionshistorie und ihres Lebenszyklus. In diesem Anwendungsbeispiel werden alltägliche Kontodaten in umsetzbare Einblicke umgewandelt, die für jeden Kunden das nächstbeste Produkt ergeben.

### Auswirkung auf den Betrieb

Personalisierte Produktempfehlungen steigern die Akzeptanzrate von Produkten um 20-30 % und erhöhen den Kundenlebenszeitwert messbar, indem sie den Anteil an der digitalen Brieftasche erhöhen.

### Implementieren

Verwenden Sie das [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)-Muster, um jeden Kunden anhand geeigneter Produktangebote in Echtzeit zu bewerten und die Empfehlungen nach Relevanz und Geschäftspriorität zu ordnen.

### Technische Überlegungen

- Vereinheitlichen Sie Transaktionsdaten, Kontostände und Produktbestände in einem einzigen Kundenprofil, sodass Entscheidungsmodelle einen vollständigen Überblick über bestehende Beziehungen haben.
- Wenden Sie finanzielle Eignungsregeln und regulatorische Eignungsbegrenzungen als feste Leitplanken innerhalb der Entscheidungs-Engine an, bevor Sie Angebote bewerten.
- Koordinieren Sie den Versand von Angeboten über Online-Banking-, Mobile-App-, E-Mail- und Advisor-Kanäle, um widersprüchliche oder doppelte Empfehlungen zu vermeiden.
- Führen Sie eine Frequenzlimitierung pro Produktkategorie ein, um Empfehlungsmüdigkeit zu vermeiden, insbesondere für hochwertige Produkte wie Hypotheken und Investitionskonten.


## Kampagnen zur Verhinderung von Abwanderungen

Identifizieren Sie Kundinnen und Kunden, bei denen das Risiko einer Abwanderung besteht, mithilfe einer KI-gestützten Abwanderungsprognose und interagieren Sie mit Aufbewahrungsangeboten und personalisierter Kommunikation. Durch die frühzeitige Erkennung von Ausstiegssignalen können Finanzinstitute eingreifen, bevor ein Kunde Konten schließt oder Vermögenswerte an einen anderen Ort verschiebt.

### Auswirkung auf den Betrieb

Proaktive Maßnahmen zur Verhinderung von Abwanderungen reduzieren in der Regel die Kundenabwanderung um 15-25 %, schützen wiederkehrende Umsatzströme und senken die Kosten für den Kundenaustausch.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster für Journey zur Kundenbindung von Triggern, wenn die Abwanderungsrisikowerte definierte Schwellenwerte überschreiten, mit eingebetteter Entscheidungsfindung, um das überzeugendste Kundenbindungsangebot auszuwählen.

### Technische Überlegungen

- Übertragen Sie Account-Aktivitätstrends, den Verlauf von Service-Interaktionen und die Interaktionshäufigkeit in [!DNL Customer AI] Abwanderungsneigungsmodelle, um Risikobewertungen zu generieren.
- Definieren Sie für Produktlinien spezifische Abwanderungsrisikoschwellen, da sich die Auskoppelungssignale für Girokonten von denen für Anlageportfolios unterscheiden.
- Sicherstellen, dass Aufbewahrungsangebote den Vorschriften für faire Kreditvergabe und Gleichbehandlung entsprechen, damit risikoreiche Segmente gerecht behandelt werden.
- Erstellen Sie eine Unterdrückungslogik, um Kundinnen und Kunden auszuschließen, die aufgrund von Betrug oder Compliance-Aktionen abwandern, wenn eine Bindung unangemessen wäre.


## Personalisiertes Konto-Dashboard

Personalisieren Sie das Online-Banking-Dashboard und das Mobile-App-Erlebnis basierend auf den Kontoaktivitäten, Voreinstellungen und finanziellen Zielen jedes Kunden. Ein maßgeschneidertes Dashboard hilft Kunden, das Wichtigste zu finden und relevante Einblicke zu erhalten, ohne dass sie eine Suche durchführen müssen.

### Auswirkung auf den Betrieb

Personalisierte Dashboards steigern die Interaktionsraten um 30-40 % und verbessern die Kundenzufriedenheit deutlich, indem sie das digitale Banking intuitiv und relevant gestalten.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um in Echtzeit personalisierte Inhaltsbausteine, Produkt-Spotlights und finanzielle Einblicke in authentifizierten digitalen Erlebnissen bereitzustellen.

### Technische Überlegungen

- Nutzen Sie [!DNL Edge Network] für Personalisierungsentscheidungen im Sekundenbereich innerhalb authentifizierter Banksitzungen, bei denen sich die Latenz direkt auf das Benutzererlebnis auswirkt.
- Aggregieren Sie Transaktionsdaten in vorab berechneten Profilattributen wie Ausgabenkategorien und Spartrends, um Berechnungen großer Datensätze in Echtzeit zu vermeiden.
- Einhaltung von Barrierefreiheitsstandards und Sicherstellung, dass personalisierte Inhalte dieselben Offenlegungsanforderungen erfüllen wie statische Inhalte.
- Koordinieren Sie die Personalisierungslogik zwischen Web- und mobilen Kanälen, damit Kunden unabhängig vom Gerät ein konsistentes Erlebnis sehen.


## Produktangebote auf Basis der Lebensphase

Identifizieren Sie Kunden, die in neue Lebensphasen eintreten, wie z. B. Heirat, Wohnungskauf oder Pensionierung, und bieten Sie proaktiv relevante Finanzprodukte und -dienstleistungen an. Das Antizipieren dieser Meilensteine ermöglicht es den Instituten, sich in entscheidenden Finanzsituationen als vertrauenswürdige Partner zu positionieren.

### Auswirkung auf den Betrieb

Durch das Leben ausgelöste Angebote erreichen eine Produktakzeptanzrate von 35-45 %, übertreffen die Leistungen generischer Kampagnen deutlich und stärken gleichzeitig langfristige Kundenbeziehungen.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Lebensphasenindikatoren zu erkennen und Multi-Touch-Journey mit integrierter Angebotsauswahl zu orchestrieren, die auf jeden Meilenstein zugeschnitten ist.

### Technische Überlegungen

- Erstanbietersignale wie Adressänderungen, gemeinsame Kontoeröffnungen und große Einlagen mit zulässigen Drittanbieterdaten kombinieren, um auf Stadienübergänge im Lebenszyklus zu schließen.
- Seien Sie beim Umgang mit sensiblen Lebensereignissen vorsichtig, da falsch abgeleitete Meilensteine das Vertrauen untergraben können.
- Die regulatorische Eignung wird in Offer Decisioning überprüft, sodass die empfohlenen Produkte mit der geprüften Finanzlage des Kunden übereinstimmen.
- Erstellen Sie Abkühlungszeiträume zwischen den Kampagnen in der Lebensphase, um zu verhindern, dass sich die Reichweite überschneidet, wenn mehrere Indikatoren in einem kurzen Fenster ausgelöst werden.


## Transaktionsbasierte Warnhinweise und Empfehlungen

Senden Sie Echtzeitwarnungen für Transaktionen und geben Sie personalisierte Empfehlungen, die auf Ausgabenmustern und Kontoaktivitäten basieren. Zeitnahe, relevante Benachrichtigungen halten Kunden auf dem Laufenden und schaffen natürliche Momente, um hilfreiche finanzielle Beratung zu bieten.

### Auswirkung auf den Betrieb

Transaktionsbasierte Warnhinweise erzielen eine Interaktionsrate von 50-60 %, verbessern das Sicherheitsbewusstsein erheblich und schaffen hochwertige Touchpoints für personalisierte Empfehlungen.

### Implementieren

Verwenden Sie das [ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um in Echtzeit auf Transaktionsereignisse mit Warnhinweisen und kontextuell relevanten Empfehlungen zu reagieren.

### Technische Überlegungen

- Transaktionsereignisse über eine Streaming-Pipeline mit Bereitstellungsanforderungen mit geringer Latenz erfassen, da Sicherheitswarnungen ihren Wert verlieren, wenn sie um mehr als einige Minuten verzögert werden.
- Wenden Sie kundendefinierte Warnhinweiseinstellungen und -schwellen an, damit Benachrichtigungen individuelle Einstellungen widerspiegeln und nicht universelle Regeln.
- Trennen Sie in der Messaging-Architektur obligatorische Sicherheitswarnungen von optionalen Empfehlungsnachrichten, um sicherzustellen, dass Compliance-Benachrichtigungen nie unterdrückt werden.
- Berücksichtigung hoher Transaktionsvolumina in Spitzenzeiten wie Zahlungstagen und Feiertagen durch die Entwicklung von Durchsatzkapazitäten, die mit der Nachfrage skalieren.


## Rückforderung bei Abbruch einer Kreditkartenanwendung

Identifizieren Sie Kunden, die mit Kreditkartenanträgen begonnen, diese jedoch nicht abgeschlossen haben, und setzen Sie sie mit personalisierten Nachrichten und Angeboten erneut in Kontakt. Bei einem Programmabbruch handelt es sich um eine Zielgruppe mit hohen Absichten, die häufig nur einen kleinen Anstoß benötigt, um den Prozess abzuschließen.

### Auswirkung auf den Betrieb

Abbruch-Recovery-Kampagnen verbessern die Abschlussraten von Anwendungen um 20-30 % und erhöhen direkt die Neuakquise von einer Audience, die bereits Interesse bekundet hat.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um Anwendungsabbruchsereignisse und zeitnahe Folgenachrichten von Triggern zu erkennen, die häufige Abbruchgründe behandeln.

### Technische Überlegungen

- Erfassen Sie den spezifischen Schritt, bei dem die Anwendung aufgegeben wurde, um die Messaging-Funktion anzupassen, da jemand, der bei der Identitätsüberprüfung abgebrochen hat, andere Zusicherungen benötigt als jemand, der bei der Überprüfung der Bedingungen gegangen ist.
- Einhaltung von Richtlinien zur Kreditvermarktung, einschließlich der erforderlichen Offenlegungen und Regeln für faire Kredite in allen Recovery-Mitteilungen.
- Implementieren Sie eine Zeitverfallslogik, damit die Recovery-Reichweite nach einem definierten Zeitfenster beendet wird, da veraltete Anwendungsdaten für die Vorqualifizierung möglicherweise nicht mehr gültig sind.
- Abstimmung mit dem Anwendungssystem, um Wiederherstellungsnachrichten für Antragsteller zu unterdrücken, die über einen anderen Kanal abgeschlossen haben, z. B. einen Zweigbesuch oder einen Telefonanruf.


## Empfehlungen für Investment Portfolio

Geben Sie personalisierte Anlageempfehlungen auf der Grundlage des Risikoprofils jedes Kunden, seiner Investitionshistorie und seiner finanziellen Ziele. Datengestützte Portfolioberatung hilft Kunden, fundierte Entscheidungen zu treffen und gleichzeitig ihre Interaktion mit Vermögensverwaltungsdiensten zu vertiefen.

### Auswirkung auf den Betrieb

Personalisierte Anlageempfehlungen steigern die Akzeptanz von Anlageprodukten um 25-35 % und verbessern die Portfoliodiversifizierung innerhalb des Kundenstamms.

### Implementieren

Verwenden Sie das [Verhaltens-Recommendations](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)-Muster, um das Investitionsverhalten und die Präferenzen zu analysieren, und legen Sie dann relevante Portfolioempfehlungen über digitale Kanäle und Beratungs-Tools offen.

### Technische Überlegungen

- Integrieren Sie Brokerage- und Depotdaten-Feeds, um einen genauen, aktuellen Überblick über die aktuellen Bestände und Zuweisungen jedes Kunden zu erhalten.
- Durchsetzung der durch die Wertpapiervorschriften vorgeschriebenen Eignungsanforderungen, sodass die Empfehlungen den dokumentierten Risikotoleranz- und Anlagezielen des Kunden entsprechen.
- Sie sollten personalisierte Anlageinhalte bei Bedarf eindeutig als pädagogische oder informative Inhalte kennzeichnen, was sie von formeller Anlageberatung unterscheidet, die treuhänderische Pflichten mit sich bringt.
- Aktualisieren Sie die Empfehlungsmodelle regelmäßig, um Marktveränderungen, Portfoliodrifts und Änderungen der Kundenziele Rechnung zu tragen.


## Betrugswarnung Personalization

Personalisieren Sie Warnungen zu Betrug und Sicherheitsmeldungen basierend auf den Kommunikationsvoreinstellungen jedes Kunden und dem Verlauf früherer Interaktionen. Maßgeschneiderte Warnhinweise erhöhen die Wahrscheinlichkeit, dass Kunden kritische Sicherheitsbenachrichtigungen bemerken, verstehen und darauf reagieren.

### Auswirkung auf den Betrieb

Personalisierte Warnhinweise für Betrug verbessern die Reaktionsrate von Warnhinweisen um 40-50 %, verbessern die Sicherheitskonformität erheblich und reduzieren die Anfälligkeit für verdächtige Aktivitäten.

### Implementieren

Verwenden Sie das [ereignisgesteuertes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um über den bevorzugten Kanal jedes Kunden Betrugswarnungen mit kontextuellen Details zu senden, die die Bestätigung oder Anfechtung von Aktivitäten erleichtern.

### Technische Überlegungen

- Priorisieren Sie die Versandgeschwindigkeit und -zuverlässigkeit vor allen anderen Design-Überlegungen, da die Warnungslatenz für Betrug direkt mit der finanziellen Verlustgefahr korreliert.
- Leiten Sie Warnhinweise über den verifizierten bevorzugten Kanal des Kunden weiter, während Sie Fallback-Kanäle beibehalten, um den Versand auch dann sicherzustellen, wenn der primäre Kanal ausfällt.
- Den Interaktionsverlauf von Warnhinweisen speichern, um die zukünftige Relevanz von Warnhinweisen zu verbessern und die falsch-positive Ermüdung von Kunden zu reduzieren, die häufig reisen oder atypische Käufe tätigen.
- Stellen Sie sicher, dass alle Betrug-Warnhinweise und Workflows den Sicherheitsvorschriften für Banken entsprechen und keine sensiblen Kontodetails in der Nachrichtenvorschau oder in Betreffzeilen verfügbar machen.


## Interaktion mit Treueprogrammen

Personalisieren Sie die Kommunikation, Prämien und Angebote im Rahmen des Treueprogramms auf der Grundlage der Stufe, des Punktesaldos und des Einlösungsverlaufs jedes Kunden. Relevante, zeitnahe Treuekommunikation sorgt dafür, dass die Mitglieder an der Kampagne beteiligt sind und die Teilnahme am Programm gefördert wird.

### Auswirkung auf den Betrieb

Personalisierte Treueprogramm-Interaktion erhöht die Programmteilnahme um 30-40 % und führt zu einer messbar höheren Punkteinlösung, wodurch die Wertwahrnehmung des Programms gestärkt wird.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um die Treuekommunikation kanalübergreifend zu orchestrieren, mit eingebetteter Entscheidungsfindung, um die relevanteste Belohnung oder das relevanteste Angebot für jedes Mitglied auszuwählen.

### Technische Überlegungen

- Synchronisieren Sie Daten der Treueplattform, einschließlich Stufenstatus, Punktesalden und Einlösungshistorie, nahezu in Echtzeit mit Kundenprofilen, um zu vermeiden, dass abgelaufene oder ungenaue Salden höher gestuft werden.
- Segmentieren Sie die Journey-Logik nach Ebene, um differenzierte Erlebnisse bereitzustellen, da Mitglieder der höheren Ebene eine exklusive Behandlung und frühzeitigen Zugriff auf Werbeaktionen erwarten.
- Koordinieren Sie Treuemeldungen mit umfassenderen Marketing-Kampagnen, um programmübergreifend Nachrichtenermüdung und widersprüchliche Angebote zu verhindern.
- Verfolgen Sie die Attribution von Rücknahmen auf allen Kanälen, um zu messen, welche personalisierte Kommunikation den höchsten ROI des Programms erzielt.


## Kampagnen zur Vorabgenehmigung von Hypotheken

Targeting von Kunden, die sich wahrscheinlich auf dem Markt für eine Hypothek befinden, basierend auf Profildaten, Verhaltenssignalen und Lebensphase-Indikatoren. Durch eine proaktive Kontaktaufnahme im Vorfeld der Genehmigung wird das Institut in einer der größten finanziellen Entscheidungen, die ein Kunde treffen wird, als eine praktische erste Wahl positioniert.

### Auswirkung auf den Betrieb

Gezielte Hypotheken-Vorabgenehmigungskampagnen erhöhen die Bewerbungsraten um 20-30 % und verbessern das Kreditausgabevolumen, indem sie qualifizierte Interessenten zum richtigen Zeitpunkt erreichen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Hypothekenpotenziale durch eine Multi-Touch-Nurture-Sequenz zu führen, von der Bewusstseinsbildung bis zur Vorabgenehmigung und der Anpassung auf der Grundlage von Interaktions- und Qualifizierungssignalen.

### Technische Überlegungen

- Kombinieren Sie Suchverhalten von Immobilien, Wachstumstrends beim Sparen und Leasingablaufsignale, um ein Tendenzmodell zu erstellen, das wahrscheinliche Hypothekensuchende identifiziert.
- Sicherstellen, dass alle Vorabbestätigungs-E-Mails den Vorschriften für die Hypothekenwerbung entsprechen, einschließlich der erforderlichen Angaben, der Genauigkeit des Zinssatzes und der gleichen Wohnsprache.
- Abstimmung des Kampagnenzeitplans mit Änderungen der Zinsertragsumgebung, sodass die Reichweite an den günstigen Kreditbedingungen ausgerichtet wird und veraltete Zinsreferenzen vermieden werden.
- Erstellen Sie Übergabe-Workflows an Kreditsachbearbeiter, damit digital gepflegte Leads reibungslos in den formellen Bewerbungs- und Zeichnungsprozess übergehen.


## Personalisierte Inhalte zur Finanzbildung

Stellen Sie personalisierte Inhalte, Tipps und Ressourcen zu Finanzfragen bereit, die auf dem Finanzprofil, den Zielen und den Interessen jedes Kunden basieren. Relevante Bildungsinhalte schaffen Vertrauen, verbessern die Finanzkompetenz und schaffen organische Möglichkeiten, relevante Produkte einzuführen.

### Auswirkung auf den Betrieb

Personalisierte Schulungsinhalte erhöhen die Interaktionsraten von Inhalten um 25-35 % und verbessern die Finanzkompetenz der Kunden, was wiederum zu einer zuversichtlicheren Produktakzeptanz führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um eine kuratierte Sequenz von Schulungsinhalten kanalübergreifend bereitzustellen, wobei mithilfe von Decisioning Themen an die finanzielle Situation und Interessen jedes Kunden angepasst werden.

### Technische Überlegungen

- Ordnen Sie Lehrinhalte Finanzprofilattributen wie Schuldenquote, Sparquote und Investitionserfahrung zu, um die Relevanz des Themas sicherzustellen.
- Tagging von Inhalten mit Schwierigkeitsgraden und vorausgesetzten Themen, um progressive Lernpfade zu erstellen, anstatt getrennte Einzelartikel bereitzustellen.
- Verfolgen Sie die Interaktion mit Inhalten auf Themenebene, um Personalisierungsmodelle zu verfeinern und neue Interessensbereiche im gesamten Kundenstamm zu identifizieren.
- Sicherstellen, dass sich pädagogische Inhalte klar vom Produktmarketing unterscheiden, um die Einhaltung behördlicher Auflagen zu gewährleisten und das Vertrauen der Kunden in die Objektivität des Programms zu wahren.
