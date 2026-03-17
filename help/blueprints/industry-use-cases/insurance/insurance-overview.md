---
title: Anwendungsfälle für Versicherungen
description: Erfahren Sie, wie Versicherungsunternehmen Adobe Experience Platform verwenden, um die Richtlinienverwaltung zu personalisieren, die Schadenerfahrung zu verbessern und die Kundenbindung zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2494'
ht-degree: 0%

---


# Anwendungsfälle für Versicherungen

Versicherungsunternehmen verwenden Adobe Experience Platform, um Daten über Policenmanagement-, Schadenersatzansprüche- und Interaktionssysteme hinweg zu vereinheitlichen und in jeder Phase der Kundenbeziehung personalisierte Mitteilungen bereitzustellen. Durch die Verbindung von Verhaltenssignalen mit Policys und Schadeninformationen können Versicherer Kunden proaktiv mit relevanten Angeboten, zeitnahen Service-Updates und aussagekräftigem Support ansprechen, der die Kundenbindung und den Wert während der gesamten Lebensdauer steigert.

## Kampagnen zur Richtlinienverlängerung

Senden Sie personalisierte Erinnerungen und Angebote zur Richtlinienverlängerung basierend auf dem Richtlinienverlauf, dem Schadendatensatz und den Präferenzen jedes Kunden. Rechtzeitige, relevante Erneuerungsmaßnahmen reduzieren die Stornierungsraten der Police und stärken langfristige Kundenbeziehungen, indem sie es Versicherungsnehmern erleichtern, ihre Optionen zu verstehen und Maßnahmen zu ergreifen.

### Auswirkung auf den Betrieb

Unternehmen, die personalisierte Kampagnen zur Erneuerung von Richtlinien implementieren, erzielen in der Regel eine Verbesserung der Erneuerungsraten um 25 bis 35 Prozent, was die Kundenabwanderung direkt reduziert und den wiederkehrenden Prämienumsatz schützt.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Die Verlängerungstermine der Police sind natürliche Trigger, die in dem Moment, in dem die Versicherungsnehmer ihre Verlängerungsentscheidung treffen, eine rechtzeitige, personalisierte Öffentlichkeitsarbeit einleiten.

### Technische Überlegungen

- Integrieren Sie sich in das Policy-Management-System, um Verlängerungsdaten und aktuelle Richtliniendetails zu erhalten, um sicherzustellen, dass die Nachrichten eine genaue Abdeckung und Premium-Informationen widerspiegeln.
- Wenden Sie Data-Governance-Kennzeichnungen auf alle persönlich identifizierbaren und finanzpolitischen Daten an, um die gesetzlichen Versicherungs- und Datenschutzbestimmungen einzuhalten.
- Konfigurieren Sie Unterdrückungsregeln, um zu verhindern, dass Verlängerungsnachrichten an Versicherungsnehmer gesendet werden, die bereits erneuert haben oder aktive Ansprüche haben, die sich auf ihre Verlängerungsbedingungen auswirken können.
- Koordinieren Sie die Zeitplanung mit den Zuweisungen an Agenten oder Broker, sodass Direktnachrichten an den Kunden gerichtet sind, die mit jeder Kontaktaufnahme übereinstimmen, die der zugewiesene Agent ebenfalls durchführen kann.


## Crossselling-Produktempfehlungen

Auf der Grundlage der bestehenden Versicherungspolicen, des Lebensstadiums und des Risikoprofils jedes Kunden zusätzliche Versicherungsprodukte wie Leben, Heim oder Auto-Versicherungsschutz empfehlen. Personalisierte Produktempfehlungen helfen den Versicherungsnehmern, Deckungslücken zu erkennen und ein umfassenderes Schutzportfolio aufzubauen.

### Auswirkung auf den Betrieb

Personalisierte Crosssell-Empfehlungen bewirken in der Regel eine Verbesserung der Crosssell-Konversionsraten um 20 bis 30 Prozent, wodurch die Policys pro Haushalt und der Gesamtwert der Kundenlebensdauer erhöht werden.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Die Echtzeit-Entscheidungsfindung bewertet die vorhandene Abdeckung, das Lebensstadium und die Verhaltenssignale jedes Kunden, um die relevanteste Produktempfehlung aus dem verfügbaren Katalog auszuwählen.

### Technische Überlegungen

- Integrieren Sie Richtliniendaten aus allen Produktlinien in ein einheitliches Kundenprofil, damit die Entscheidungs-Engine bei der Auswahl von Empfehlungen einen vollständigen Überblick über die vorhandene Abdeckung hat.
- Konfigurieren Sie die Eignungsregeln innerhalb des Entscheidungsmodells, um Produkte auszuschließen, die bereits im Besitz eines Kunden sind oder die mit den Underwriting-Richtlinien für sein Risikoprofil kollidieren.
- Wenden Sie regulatorische Compliance-Regeln an, um sicherzustellen, dass Produktempfehlungen den bundesstaatlichen Versicherungs- und Marketing-Anforderungen entsprechen.
- Koordinieren Sie die Entscheidungsausgabe mit dem Agentenportal, sodass empfohlene Produkte für zugewiesene Agenten sichtbar sind, die möglicherweise direkte Gespräche mit dem Kunden führen.


## Personalization für Schadensfallbearbeitung

Personalisieren Sie die Kommunikation zum Schadenprozess, Statusaktualisierungen und Support-Ressourcen basierend auf dem Anspruchtyp, den Kundenpräferenzen und dem Schadenverlauf. Eine transparente, gut kommunizierte Schadenerfahrung reduziert die Angst in stressigen Momenten und baut nachhaltiges Vertrauen zu den Versicherungsnehmern auf.

### Auswirkung auf den Betrieb

Personalisierte Schadensmeldungen führen in der Regel zu einer Verbesserung der Schadenzufriedenheitswerte um 40 bis 50 Prozent, wodurch Beschwerden reduziert und die Wahrscheinlichkeit einer Richtlinienverlängerung nach einem Anspruch erhöht wird.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Der Schadenprozess ist ein mehrstufiges Erlebnis mit unterschiedlichen Phasen - Einreichung, Untersuchung, Anpassung und Abwicklung -, die jeweils maßgeschneiderte Kommunikation und adaptives Timing erfordern.

### Technische Überlegungen

- Integration mit dem Schadensregulierungssystem, um Statusänderungsereignisse in Echtzeit zu erhalten, die den Kunden durch den entsprechenden Journey-Schritt voranbringen.
- Entwerfen Sie eine Verzweigungslogik für Journey, die den Nachrichtenton und den Inhalt je nach Anspruchstyp anpasst, z. B. Autokollision versus Sachschaden versus Haftungsansprüche.
- Implementieren Sie Unterdrückungsregeln während aktiver Schadenuntersuchungen, um zu verhindern, dass Marketing- oder Crosssell-Nachrichten Kunden in sensiblen Momenten erreichen.
- Stellen Sie sicher, dass alle anspruchsbezogenen Daten, die in das Kundenprofil fließen, mit entsprechenden Data-Governance-Beschränkungen gekennzeichnet sind, um ihre Verwendung außerhalb der Service-Kommunikation zu verhindern.


## Risikobewertung und -prävention

Stellen Sie personalisierte Informationen zur Risikobewertung und Tipps zur Prävention bereit, die auf dem Richtlinientyp, dem geografischen Standort und den spezifischen Risikofaktoren des jeweiligen Kunden basieren. Eine proaktive Risikoaufklärung hilft den Versicherungsnehmern, ihre Verlustrisiken zu reduzieren, was sowohl dem Kunden als auch dem Versicherer zugute kommt.

### Auswirkung auf den Betrieb

Personalisierte Maßnahmen zur Risikovermeidung tragen in der Regel zu einer 30- bis 40-prozentigen Verbesserung des präventiven Engagements bei, wodurch die Schadenshäufigkeit reduziert und die Kundenzufriedenheit erhöht werden.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Risikopräventionsschulung ist am effektivsten als nachhaltige Multi-Touch-Journey, die im Laufe der Zeit relevante Anleitungen bietet und sich an die Kundeninteraktion und saisonalen Risikofaktoren anpasst.

### Technische Überlegungen

- Integrieren Sie mit Drittanbietern von Risikodaten für Informationen zu Wetter, geografischen Gefahren und Immobilienrisiken, die Kundenprofile mit standortspezifischen Risikobewertungen anreichern.
- Entwerfen Sie saisonale Journey-Logik, die relevante Präventionsinhalte vor Hochrisikozeiten liefert, z. B. die Vorbereitung auf die Hurrikan-Saison für Inhaber von Küstenverträgen oder Winterwettertipps für Kunden mit kalten Temperaturen.
- Wenden Sie Data-Governance-Kennzeichnungen an, um Risikobewertungsdaten, die für die Kundenschulung verwendet werden, von Daten zu unterscheiden, die in versicherungsmathematischen Underwriting-Entscheidungen verwendet werden.
- Koordinieren Sie die Inhalte zur Risikovermeidung mit der spezifischen Abdeckung des Versicherungsnehmers, sodass die Empfehlungen für die Risiken relevant sind, die von deren Police tatsächlich abgedeckt werden.


## Benachrichtigungen zu Richtlinienänderungen

Senden Sie personalisierte Benachrichtigungen über Richtlinienänderungen, Aktualisierungen der Abdeckung und neue Optionen basierend auf den spezifischen Richtlinien- und Kommunikationsvoreinstellungen jedes Kunden. Klare, zeitnahe Benachrichtigungen halten die Versicherungsnehmer auf dem Laufenden und verringern die Verwirrung über ihren Deckungsstatus.

### Auswirkung auf den Betrieb

Personalisierte Benachrichtigungen zu Richtlinienänderungen erzielen in der Regel eine Verbesserung der Benachrichtigungsbestätigungsraten um 50 bis 60 Prozent, reduzieren Kundendienstanfragen und verbessern das Verständnis der Versicherungsnehmer insgesamt.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Richtlinienänderungsereignisse aus dem Administrationssystem dienen als natürliche Trigger für sofortige, relevante Benachrichtigungen über den bevorzugten Kanal jedes Kunden.

### Technische Überlegungen

- Integration mit dem Richtlinienverwaltungssystem, um Änderungen von Empfehlungen, Änderungen und Erneuerungen in Echtzeit zu erfassen und so sicherzustellen, dass Benachrichtigungen den aktuellen Richtlinienstatus widerspiegeln.
- Wenden Sie regulatorische Compliance-Regeln an, um sicherzustellen, dass Benachrichtigungen die staatlich vorgeschriebenen Kommunikationsanforderungen für Richtlinienänderungen erfüllen, einschließlich der erforderlichen Sprache und der erforderlichen Bereitstellungszeiträume.
- Konfigurieren Sie die Kanalprioritätslogik basierend auf der Dringlichkeit und dem Typ der Änderung - beispielsweise können Abdeckungsreduzierungen sofortigere Kanäle erfordern als informative Aktualisierungen.
- Pflegen Sie ein Versand-Audit-Protokoll für alle Benachrichtigungen zu Richtlinienänderungen, um die Dokumentation zur Einhaltung von Vorschriften und zur Streitbeilegung zu unterstützen.


## Kursabbruch-Wiederherstellung

Rückgewinnung von Kunden, die begonnen, aber kein Versicherungsangebot abgeschlossen haben, mit personalisierten Folgenachrichten und maßgeschneiderten Angeboten. Rechtzeitige Recovery Outreach-Maßnahmen bringen potenzielle Kunden zurück zum Kostenvoranschlagsprozess und beseitigen gängige Hindernisse für den Abschluss.

### Auswirkung auf den Betrieb

Recovery-Kampagnen zur Angebotsabbruch führen in der Regel zu einer Verbesserung der Quote-Abschlussraten um 20 bis 30 Prozent, wodurch mehr potenzielle Kunden in Versicherungsnehmer umgewandelt und die Kosten für die Kundenakquise gesenkt werden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Ein Zitatabbruch ist ein Verhaltensereignis, das die Trigger rechtzeitig verfolgen, solange das Interesse und die Absicht des potenziellen Kunden noch aktuell sind.

### Technische Überlegungen

- Integration mit der Online-Angebotsplattform, um Abbruchs-Ereignisse zusammen mit den vom Kunden bereits angegebenen Angebotsdetails zu erfassen und so eine personalisierte Rückgewinnung zu ermöglichen.
- Konfigurieren Sie Zeitregeln, die Dringlichkeit und Respekt ausbalancieren - anfängliche Nachbereitung innerhalb von Stunden mit einer begrenzten Anzahl nachfolgender Erinnerungen über die folgenden Tage.
- Wenden Sie Einverständnis- und Datenschutzregeln an, um sicherzustellen, dass Folgemaßnahmen nur an Interessenten gesendet werden, die sich für Marketing-Nachrichten entschieden haben, insbesondere für Kunden, die noch keine Geschäftsbeziehung aufgebaut haben.
- Schließen Sie Deep-Links ein, die den potenziellen Kunden direkt zu seinem gespeicherten Angebot zurückführen, anstatt ihn zu verpflichten, den Prozess von Anfang an neu zu starten.


## Produktangebote auf Basis der Lebensphase

Identifizieren Sie Kunden, die in neue Lebensstadien eintreten - z. B. Heirat, Wohnungskauf, wachsende Familie oder Ruhestand - und bieten Sie relevante Versicherungsprodukte an, die ihren sich verändernden Schutzbedürfnissen entsprechen. Das Life Stage Targeting hilft Versicherungsnehmern, die richtige Abdeckung zum richtigen Zeitpunkt aufzubauen.

### Auswirkung auf den Betrieb

Produktangebote in der Lebensphase bewirken in der Regel eine 35- bis 45-prozentige Verbesserung der Akzeptanzraten von Produkten in der Lebensphase und vertiefen die Kundenbeziehungen in wichtigen Entscheidungsprozessen.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Transitionen in der Lebensphase profitieren von einer kanalübergreifenden Orchestrierung in Kombination mit Echtzeit-Entscheidungen, um das relevanteste Produkt auszuwählen und es zum optimalen Zeitpunkt über den bevorzugten Kanal des Kunden bereitzustellen.

### Technische Überlegungen

- Erstellen Sie Modelle zur Erkennung von Lebensstadien mithilfe von Verhaltenssignalen wie Adressänderungen, Empfängeraktualisierungen und Online-Forschungsmustern in Kombination mit Ereignissen zur Richtlinienänderung.
- Konfigurieren Sie die Entscheidungs-Engine mit Produkteignungs- und Eignungsregeln, die jedes Lebensstadium den entsprechenden Abdeckungsempfehlungen entsprechen.
- Koordinieren Sie die Life-Stage-Angebote mit dem zugewiesenen Agenten oder Broker, damit diese bereit sind, den Kunden bei der Unterbreitung des Angebots mit einem Beratungsgespräch zu unterstützen.
- Wenden Sie Data-Governance-Kennzeichnungen auf alle Datenquellen von Drittanbietern an, die für den Lebensstadium-Rückschluss verwendet werden, um die Einhaltung von Datenschutzbestimmungen und fairen Marketing-Praktiken sicherzustellen.


## Rabatt und Sparmöglichkeiten

Identifizieren und kommunizieren Sie personalisierte Rabattmöglichkeiten - wie z. B. Paketangebote, sichere Treiber, Treuerabatte und papierlose Abrechnungsrabatte - basierend auf dem Profil und Verhalten jedes Kunden. Proaktive Sparkommunikation zeigt Wert und stärkt das Preis-Nutzen-Verhältnis.

### Auswirkung auf den Betrieb

Personalisierte Rabatt- und Sparkommunikation führt in der Regel zu einer 25- bis 35-prozentigen Verbesserung der Rabattnutzungsraten, einer Verbesserung der Kundenzufriedenheit und einer Reduzierung der preisbedingten Abwanderung.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Die Echtzeit-Entscheidungsfindung bewertet die Berechtigung jedes Kunden für verfügbare Rabatte und wählt die wirkungsvollste Sparmöglichkeit aus, die er zum richtigen Zeitpunkt bieten kann.

### Technische Überlegungen

- Integration mit den Policy-Rating- und Abrechnungssystemen zur Berechnung der genauen Rabattberechtigung und potenziellen Einsparbeträge für jeden Kunden in Echtzeit.
- Konfigurieren Sie Entscheidungsregeln, die den Einschränkungen für die Rabattstapelung Rechnung tragen und sicherstellen, dass die kommunizierten Einsparbeträge genau sind und vom Preisfindungs-Team genehmigt wurden.
- Anwendung bundesstaatlicher Regeln für Rabattmitteilungen, da bestimmte Staaten Beschränkungen für den Vertrieb und die Anwendung von Versicherungsrabatten haben.
- Verfolgen Sie die Ergebnisse der Rabattakzeptanz, um das Entscheidungsmodell kontinuierlich zu verfeinern und die Sparbotschaften zu priorisieren, die bei den verschiedenen Kundensegmenten am meisten Anklang finden.


## Betrugsbekämpfung bei Schadensfällen

Verwenden Sie intelligente Betrugserkennung, um verdächtige Schadenmuster zu identifizieren und die Ermittlungskommunikation zu personalisieren, während das Vertrauen der Kunden gewahrt bleibt. Eine wirksame Betrugsprävention schützt ehrliche Versicherungsnehmer, indem sie die Prämien fair hält und sicherstellt, dass berechtigte Ansprüche schnell bearbeitet werden.

### Auswirkung auf den Betrieb

Intelligente Programme zur Betrugsbekämpfung erreichen in der Regel eine 15- bis 25-prozentige Verbesserung der Aufdeckungsraten von Betrug, wodurch betrügerische Auszahlungen reduziert und die Gesamtkosten für Schadenersatzansprüche gesenkt werden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Betrugsrisiko-Bewertungsereignisse Trigger geeigneter Ermittlungsmitteilungen und Prozessanpassungen in Echtzeit, um sicherzustellen, dass gekennzeichnete Schadensfälle sofort bearbeitet werden.

### Technische Überlegungen

- Integrieren Sie Betrugsrisikobewertungen aus dem Schadensanalysesystem in das Kundenprofil, während Sie strenge Data-Governance-Kennzeichnungen anwenden, um zu verhindern, dass Betrugsuntersuchungsdaten in kundenorientierten Kommunikationen angezeigt werden.
- Entwerfen Sie Kommunikationswege, die einen professionellen, respektvollen Ton für Kunden aufrechterhalten, deren Ansprüche überprüft werden, und bewahren Sie die Beziehung unabhängig vom Untersuchungsergebnis.
- Implementieren Sie rollenbasierte Zugriffskontrollen, um sicherzustellen, dass Betrugsindikatoren nur für autorisierte Ermittlungsteams sichtbar sind und nie in den standardmäßigen Agenten- oder Kundendienstansichten angezeigt werden.
- Koordinieren Sie sich mit dem [!DNL Adobe Experience Platform] Identity Resolution Service, um Muster in verwandten Profilen zu erkennen, z. B. freigegebene Adressen oder Telefonnummern, die mit mehreren verdächtigen Ansprüchen verknüpft sind.


## Wellness- und Präventionsprogramme

Personalisieren Sie die Kommunikation zum Wellness-Programm, Teilnahmerinnerungen und Prämienbenachrichtigungen für Kund*innen von Kranken- und Lebensversicherungen auf Grundlage ihrer Ziele und Interaktionsstufen. Aktive Wellness-Programme verbessern die Gesundheit der Versicherungsnehmer und schaffen einen stärkeren, engagierteren Kundenstamm.

### Auswirkung auf den Betrieb

Personalisierte Mitteilungen über Wellness- und Präventionsprogramme führen in der Regel zu einer 30- bis 40-prozentigen Verbesserung der Teilnahmeraten an Programmen, was zu besseren gesundheitlichen Ergebnissen und einer reduzierten Schadenshäufigkeit beiträgt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Wellnessprogramme sind nachhaltige Interaktionserlebnisse mit Meilensteinen, Herausforderungen und Belohnungen, die eine adaptive Orchestrierung basierend auf der Aktivität und dem Fortschritt jedes Teilnehmers erfordern.

### Technische Überlegungen

- Integration mit Daten-Feeds für Wearable-Geräte und Gesundheitsanwendungen mithilfe [!DNL Adobe Experience Platform] Streaming-Aufnahme, wobei klare Data Governance-Kennzeichnungen angewendet werden, um Wellness-Daten von Versicherungs- oder Schadensdaten zu unterscheiden.
- Implementieren Sie separate Einverständnismechanismen für die Wellness-Datenerfassung, um sicherzustellen, dass die Teilnehmer verstehen, wie ihre Gesundheitsaktivitätsdaten verwendet werden, und sich abmelden können, ohne ihre Richtlinie zu beeinflussen.
- Entwerfen Sie eine Journey-Logik, die die Programmintensität und die Kommunikationsfrequenz auf der Grundlage des Interaktionsniveaus jedes Teilnehmers anpasst, um Ermüdung zu vermeiden und anhaltende Teilnahme zu fördern.
- Stellen Sie sicher, dass die Wellness-Incentive- und Belohnungsverfolgung den geltenden Versicherungsvorschriften für Versicherungsanreize und Prämienrabattprogramme entspricht.


## Koordination von Agent und Broker

Personalisierte Kommunikation und Koordination zwischen Kunden und ihren zugewiesenen Agenten oder Brokern auf der Grundlage von Richtlinienanforderungen, Service-Verlauf und Voreinstellungen ermöglichen. Eine bessere Koordination schafft ein nahtloses Erlebnis, bei dem sich Kunden von einem kompetenten Berater unterstützt fühlen, der ihre vollständige Beziehung versteht.

### Auswirkung auf den Betrieb

Effektive Agent- und Broker-Koordinationskommunikation führt in der Regel zu einer 35- bis 45-prozentigen Verbesserung der Interaktion mit Agenten, was zu stärkeren Kundenbeziehungen und einer höheren Kundenbindung führt, die durch vertrauenswürdige Beratungsinteraktionen angetrieben wird.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für ausgehende Nachrichten &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Batch. Die Agentenkoordination wird am besten durch geplante Batch-Aktivierungen bereitgestellt, die Agenten regelmäßig mit priorisierten Kontaktlisten, Gesprächspunkten und empfohlenen Aktionen versorgen.

### Technische Überlegungen

- Integration mit dem Agenten-Management-System, um präzise Agent-Kunden-Zuweisungen zu verwalten und sicherzustellen, dass die Kommunikation die richtige Beziehung widerspiegelt, insbesondere während Agentenübergängen.
- Gestalten Sie die Datenaktivierung für das Agentenportal, damit Agenten eine konsolidierte Ansicht von Kundeneinblicken, bevorstehenden Erneuerungen und empfohlenen Aktionen erhalten, ohne rohe Verhaltensdaten verfügbar zu machen.
- Wenden Sie Data-Governance-Kennzeichnungen an, um zu beschränken, welche Kundendatenelemente mit externen Brokerpartnern oder firmeneigenen Agenten geteilt werden, wobei die vertraglichen und regulatorischen Datenfreigabegrenzen zu beachten sind.
- Implementieren Sie Feedback-Schleifen aus Agenten-Interaktionen wieder in das Kundenprofil, sodass Einblicke aus persönlichen oder Telefongesprächen die einheitliche Ansicht bereichern und die zukünftige Personalisierung verbessern.


## Reaktion auf Katastrophenfälle

Proaktive Kommunikation mit Kunden in betroffenen Gebieten während Naturkatastrophen oder Katastrophenereignissen mit personalisierten Support-Informationen, Anleitungen zur Antragstellung und Notfallressourcen. Schnelle, einfühlsame Kontaktaufnahme während einer Krise zeigt das Engagement des Versicherers, dort zu sein, wo Kunden es am meisten brauchen.

### Auswirkung auf den Betrieb

Proaktive Kommunikation über die Reaktion auf Katastrophenereignisse erzielt in der Regel eine Verbesserung der Kundenkommunikationsraten um 60 bis 70 Prozent bei Ereignissen, wodurch die Antragstellung erheblich beschleunigt und das langfristige Vertrauen und die Kundentreue gestärkt werden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Katastrophenereignis-Deklarationen dienen als hochprioritäre Trigger für eine sofortige, personalisierte Kontaktaufnahme zu allen Versicherungsnehmern im betroffenen geografischen Gebiet.

### Technische Überlegungen

- Integration mit Katastrophenüberwachungs-Services und der Bereitstellung von Daten für die Katastrophenanmeldung durch die Regierung, wenn Ereignisse für bestimmte geografische Gebiete gemeldet werden, schnell zur Kommunikation durch die Trigger.
- Erstellen Sie geografische Zielgruppensegmente mithilfe von Adressdaten des Versicherungsnehmers und Standortinformationen der Immobilien, um Kunden im betroffenen Bereich genau zu identifizieren, ohne zu stark mit nicht betroffenen Kunden zu kommunizieren.
- Konfigurieren Sie ein Routing für Nachrichten mit hoher Priorität, bei dem die standardmäßigen Frequenzlimitierungs- und Unterdrückungsregeln außer Kraft gesetzt werden, um sicherzustellen, dass wichtige Sicherheits- und Schadensinformationen Kunden sofort erreichen.
- Erstellen Sie Nachrichtenvorlagen und Journey-Konfigurationen für gängige Katastrophenereignistypen vorab, damit die Kommunikation innerhalb von Stunden nach einer Ereignisdeklaration aktiviert werden kann, anstatt die Erstellung von Inhalten während der Krise zu erfordern.
