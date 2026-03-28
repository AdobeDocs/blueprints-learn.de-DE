---
title: Anwendungsfälle für Versicherungen
description: Erfahren Sie, wie Versicherungsunternehmen Adobe Experience Platform verwenden, um die Richtlinienverwaltung zu personalisieren, die Schadenerfahrung zu verbessern und die Kundenbindung zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a082598f-555b-49a4-b201-a55bee793959
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '3016'
ht-degree: 0%

---

# Anwendungsfälle für Versicherungen

Versicherungsunternehmen verwenden Adobe Experience Platform, um Daten über Policenmanagement-, Schadenersatzansprüche- und Interaktionssysteme hinweg zu vereinheitlichen und in jeder Phase der Kundenbeziehung personalisierte Mitteilungen bereitzustellen. Durch die Verbindung von Verhaltenssignalen mit Policys und Schadeninformationen können Versicherer Kunden proaktiv mit relevanten Angeboten, zeitnahen Service-Updates und aussagekräftigem Support ansprechen, der die Kundenbindung und den Wert während der gesamten Lebensdauer steigert.

## Kampagnen zur Richtlinienverlängerung

Senden Sie personalisierte Erinnerungen und Angebote zur Richtlinienverlängerung basierend auf dem Richtlinienverlauf, dem Schadendatensatz und den Präferenzen jedes Kunden. Rechtzeitige, relevante Erneuerungsmaßnahmen reduzieren die Stornierungsraten der Police und stärken langfristige Kundenbeziehungen, indem sie es Versicherungsnehmern erleichtern, ihre Optionen zu verstehen und Maßnahmen zu ergreifen.

### Auswirkung auf den Betrieb

Unternehmen, die personalisierte Kampagnen zur Erneuerung von Policys implementieren, profitieren von verbesserten Verlängerungsraten, die die Kundenabwanderung direkt reduzieren und den wiederkehrenden Prämienumsatz schützen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Bei diesem Ansatz wird eine zeitgesteuerte Erneuerungssequenz erstellt, die von der ersten Benachrichtigung über eskalierende Erinnerungen und bei Bedarf über eine letzte Dringlichkeitsmeldung fortschreitet, wobei die Kadenz und das Angebot auf der Grundlage der Frage angepasst werden, ob der Versicherungsnehmer frühere Maßnahmen ergriffen hat. Dies ist das richtige Muster, wenn das Timing von einem Vertragsdatum und nicht von einem diskreten Kundenereignis gesteuert wird und die Geschäftsabsicht einen sequenziellen Fluss mit mehreren Nachrichten über 30 oder mehr Tage mit bedingter Verzweigung basierend auf Interaktion erfordert. Ereignisausgelöstes Messaging verarbeitet reaktive Antworten auf diskrete Ereignisse, kann jedoch nicht die kalenderbasierte Planungslogik oder Eskalationsabhängigkeiten berücksichtigen, die für eine Verlängerungskampagne erforderlich sind.

### Technische Überlegungen

- Integrieren Sie sich in das Policy-Management-System, um Verlängerungsdaten und aktuelle Richtliniendetails zu erhalten, um sicherzustellen, dass die Nachrichten eine genaue Abdeckung und Premium-Informationen widerspiegeln.
- Wenden Sie Data-Governance-Kennzeichnungen auf alle persönlich identifizierbaren und finanzpolitischen Daten an, um die gesetzlichen Versicherungs- und Datenschutzbestimmungen einzuhalten.
- Konfigurieren Sie Unterdrückungsregeln, um zu verhindern, dass Verlängerungsnachrichten an Versicherungsnehmer gesendet werden, die bereits erneuert haben oder aktive Ansprüche haben, die sich auf ihre Verlängerungsbedingungen auswirken können.
- Koordinieren Sie die Zeitplanung mit den Zuweisungen an Agenten oder Broker, sodass Direktnachrichten an den Kunden gerichtet sind, die mit jeder Kontaktaufnahme übereinstimmen, die der zugewiesene Agent ebenfalls durchführen kann.


## Crossselling-Produktempfehlungen

Auf der Grundlage der bestehenden Versicherungspolicen, des Lebensstadiums und des Risikoprofils jedes Kunden zusätzliche Versicherungsprodukte wie Leben, Heim oder Auto-Versicherungsschutz empfehlen. Personalisierte Produktempfehlungen helfen den Versicherungsnehmern, Deckungslücken zu erkennen und ein umfassenderes Schutzportfolio aufzubauen.

### Auswirkung auf den Betrieb

Personalisierte Crosssell-Empfehlungen steigern die Crosssell-Konversionsraten, erhöhen die Policys pro Haushalt und den Gesamtwert der Kundenlebensdauer.

### Implementieren

Verwenden Sie das Muster {0](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. [Die Echtzeit-Entscheidungsfindung bewertet die vorhandene Abdeckung, das Lebensstadium und die Verhaltenssignale jedes Kunden, um die relevanteste Produktempfehlung aus dem verfügbaren Katalog auszuwählen. Dies ist das richtige Muster, wenn die Produktauswahl Eignungsregeln, Underwriting-Richtlinien und regulatorische Eignungsanforderungen berücksichtigen muss - Einschränkungen, die eine geregelte Entscheidungslogik erfordern, anstatt nur eine Rangliste der Verhaltensauffinität zu erstellen.

### Technische Überlegungen

- Integrieren Sie Richtliniendaten aus allen Produktlinien in ein einheitliches Kundenprofil, damit die Entscheidungs-Engine bei der Auswahl von Empfehlungen einen vollständigen Überblick über die vorhandene Abdeckung hat.
- Konfigurieren Sie die Eignungsregeln innerhalb des Entscheidungsmodells, um Produkte auszuschließen, die bereits im Besitz eines Kunden sind oder die mit den Underwriting-Richtlinien für sein Risikoprofil kollidieren.
- Wenden Sie sich vor der Live-Schaltung an Ihre Rechts- und Compliance-Teams, um zu überprüfen, ob die Eignungsregeln für Produktempfehlungen mit den geltenden staatlichen Marketing- und Eignungsanforderungen für Versicherungen übereinstimmen.
- Koordinieren Sie die Entscheidungsausgabe mit dem Agentenportal, sodass empfohlene Produkte für zugewiesene Agenten sichtbar sind, die möglicherweise direkte Gespräche mit dem Kunden führen.


## Personalization für Schadensfallbearbeitung

Personalisieren Sie die Kommunikation zum Schadenprozess, Statusaktualisierungen und Support-Ressourcen basierend auf dem Anspruchtyp, den Kundenpräferenzen und dem Schadenverlauf. Eine transparente, gut kommunizierte Schadenerfahrung reduziert die Angst in stressigen Momenten und baut nachhaltiges Vertrauen zu den Versicherungsnehmern auf.

### Auswirkung auf den Betrieb

Personalisierte Mitteilungen über Schadensfälle führen zu besseren Scores für die Schadenzufriedenheit, reduzieren Beschwerden und erhöhen die Wahrscheinlichkeit einer Erneuerung der Police nach einem Schaden.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Der Schadenprozess ist ein mehrstufiges Erlebnis mit unterschiedlichen Phasen - Einreichung, Untersuchung, Anpassung und Abwicklung -, die jeweils maßgeschneiderte Kommunikation und adaptives Timing erfordern. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf Anspruchsstatusereignissen erfordert - eine einzelne ausgelöste Nachricht kann die Abhängigkeitslogik zwischen sequenziellen Anspruchsphasen nicht berücksichtigen.

### Technische Überlegungen

- Integration mit dem Schadensregulierungssystem, um Statusänderungsereignisse in Echtzeit zu erhalten, die den Kunden durch den entsprechenden Journey-Schritt voranbringen.
- Entwerfen Sie eine Verzweigungslogik für Journey, die den Nachrichtenton und den Inhalt je nach Anspruchstyp anpasst, z. B. Autokollision versus Sachschaden versus Haftungsansprüche.
- Implementieren Sie Unterdrückungsregeln während aktiver Schadenuntersuchungen, um zu verhindern, dass Marketing- oder Crosssell-Nachrichten Kunden in sensiblen Momenten erreichen.
- Stellen Sie sicher, dass alle anspruchsbezogenen Daten, die in das Kundenprofil fließen, mit entsprechenden Data-Governance-Beschränkungen gekennzeichnet sind, um ihre Verwendung außerhalb der Service-Kommunikation zu verhindern.


## Risikobewertung und -prävention

Stellen Sie personalisierte Informationen zur Risikobewertung und Tipps zur Prävention bereit, die auf dem Richtlinientyp, dem geografischen Standort und den spezifischen Risikofaktoren des jeweiligen Kunden basieren. Eine proaktive Risikoaufklärung hilft den Versicherungsnehmern, ihre Verlustrisiken zu reduzieren, was sowohl dem Kunden als auch dem Versicherer zugute kommt.

### Auswirkung auf den Betrieb

Personalisierte Kontaktaufnahme zur Risikovermeidung trägt zu einer verbesserten präventiven Interaktion bei, wodurch weniger Ansprüche geltend gemacht werden müssen und die Kundenzufriedenheit steigt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Risikopräventionsschulung ist am effektivsten als nachhaltige Multi-Touch-Journey, die im Laufe der Zeit relevante Anleitungen bietet und sich an die Kundeninteraktion und saisonalen Risikofaktoren anpasst. Dies ist das richtige Muster, wenn der Journey Inhalte über längere Zeiträume mit saisonalen Zeitplananpassungen und interaktionsbasierten Verzweigungen bereitstellen muss - ereignisgesteuertes Messaging kann keinen prädiktiven Zeitplan oder den mehrstufigen Kadenz bewältigen, der für eine nachhaltige Ausbildung erforderlich ist.

### Technische Überlegungen

- Integrieren Sie mit Drittanbietern von Risikodaten für Informationen zu Wetter, geografischen Gefahren und Immobilienrisiken, die Kundenprofile mit standortspezifischen Risikobewertungen anreichern.
- Entwerfen Sie saisonale Journey-Logik, die relevante Präventionsinhalte vor Hochrisikozeiten liefert, z. B. die Vorbereitung auf die Hurrikan-Saison für Inhaber von Küstenverträgen oder Winterwettertipps für Kunden mit kalten Temperaturen.
- Wenden Sie Data-Governance-Kennzeichnungen an, um Risikobewertungsdaten, die für die Kundenschulung verwendet werden, von Daten zu unterscheiden, die in versicherungsmathematischen Underwriting-Entscheidungen verwendet werden.
- Koordinieren Sie die Inhalte zur Risikovermeidung mit der spezifischen Abdeckung des Versicherungsnehmers, sodass die Empfehlungen für die Risiken relevant sind, die von deren Police tatsächlich abgedeckt werden.


## Benachrichtigungen zu Richtlinienänderungen

Senden Sie personalisierte Benachrichtigungen über Richtlinienänderungen, Aktualisierungen der Abdeckung und neue Optionen basierend auf den spezifischen Richtlinien- und Kommunikationsvoreinstellungen jedes Kunden. Klare, zeitnahe Benachrichtigungen halten die Versicherungsnehmer auf dem Laufenden und verringern die Verwirrung über ihren Deckungsstatus.

### Auswirkung auf den Betrieb

Personalisierte Benachrichtigungen zu Richtlinienänderungen führen zu verbesserten Bestätigungsraten für Benachrichtigungen, reduzierten Anfragen beim Kundendienst und einem besseren Verständnis der Versicherungsnehmer insgesamt.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Richtlinienänderungsereignisse aus dem Administrationssystem dienen als natürliche Trigger für sofortige, relevante Benachrichtigungen über den bevorzugten Kanal jedes Kunden. Dies ist das richtige Muster, wenn der Trigger ein Systemereignis (Richtlinienänderung) und kein Kundenverhalten ist und die erforderliche Kommunikation sofort und reaktiv erfolgt und keine nachhaltige Nurture-Sequenz ist.

### Technische Überlegungen

- Integration mit dem Richtlinienverwaltungssystem, um Änderungen von Empfehlungen, Änderungen und Erneuerungen in Echtzeit zu erfassen und so sicherzustellen, dass Benachrichtigungen den aktuellen Richtlinienstatus widerspiegeln.
- Arbeiten Sie vor der Aktivierung automatisierter Kommunikation mit Ihrer Rechtsabteilung zusammen, um zu bestätigen, dass Benachrichtigungen zu Richtlinienänderungen die geltenden gesetzlichen Anforderungen an den Zeitpunkt, die Sprache und den Versandkanal erfüllen.
- Konfigurieren Sie die Kanalprioritätslogik basierend auf der Dringlichkeit und dem Typ der Änderung - beispielsweise können Abdeckungsreduzierungen sofortigere Kanäle erfordern als informative Aktualisierungen.
- Pflegen Sie ein Versand-Audit-Protokoll für alle Benachrichtigungen zu Richtlinienänderungen, um die Dokumentation zur Einhaltung von Vorschriften und zur Streitbeilegung zu unterstützen.


## Kursabbruch-Wiederherstellung

Rückgewinnung von Kunden, die begonnen, aber kein Versicherungsangebot abgeschlossen haben, mit personalisierten Folgenachrichten und maßgeschneiderten Angeboten. Rechtzeitige Recovery Outreach-Maßnahmen bringen potenzielle Kunden zurück zum Kostenvoranschlagsprozess und beseitigen gängige Hindernisse für den Abschluss.

### Auswirkung auf den Betrieb

Recovery-Kampagnen zur Angebotsabbruch fördern verbesserte Quote-Abschlussraten, verwandeln mehr potenzielle Kunden in Versicherungsnehmer und senken die Kosten für die Kundenakquise.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Ein Zitatabbruch ist ein Verhaltensereignis, das die Trigger rechtzeitig verfolgen, solange das Interesse und die Absicht des potenziellen Kunden noch aktuell sind. Dies ist das richtige Muster, wenn ein diskretes Kundenverhalten (Abbruch) der Trigger ist und die erforderliche Reaktion die zeitabhängige Rückgewinnung ist - anstelle einer mehrstufigen Nurture-Sequenz oder einer komplexen Angebotsentscheidung.

### Technische Überlegungen

- Integration mit der Online-Angebotsplattform, um Abbruchs-Ereignisse zusammen mit den vom Kunden bereits angegebenen Angebotsdetails zu erfassen und so eine personalisierte Rückgewinnung zu ermöglichen.
- Konfigurieren Sie Zeitregeln, die Dringlichkeit und Respekt ausbalancieren - anfängliche Nachbereitung innerhalb von Stunden mit einer begrenzten Anzahl nachfolgender Erinnerungen über die folgenden Tage.
- Wenden Sie Einverständnis- und Datenschutzregeln an, um sicherzustellen, dass Folgemaßnahmen nur an Interessenten gesendet werden, die sich für Marketing-Nachrichten entschieden haben, insbesondere für Kunden, die noch keine Geschäftsbeziehung aufgebaut haben.
- Schließen Sie Deep-Links ein, die den potenziellen Kunden direkt zu seinem gespeicherten Angebot zurückführen, anstatt ihn zu verpflichten, den Prozess von Anfang an neu zu starten.


## Rabatt und Sparmöglichkeiten

Identifizieren und kommunizieren Sie personalisierte Rabattmöglichkeiten - wie z. B. Paketangebote, sichere Treiber, Treuerabatte und papierlose Abrechnungsrabatte - basierend auf dem Profil und Verhalten jedes Kunden. Proaktive Sparkommunikation zeigt Wert und stärkt das Preis-Nutzen-Verhältnis.

### Auswirkung auf den Betrieb

Personalisierte Rabatt- und Sparkommunikation sorgt für eine bessere Rabattnutzung, eine höhere Kundenzufriedenheit und eine geringere Abwanderung zu Preisen.

### Implementieren

Verwenden Sie das Muster {0](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. [Die Echtzeit-Entscheidungsfindung bewertet die Berechtigung jedes Kunden für verfügbare Rabatte und wählt die wirkungsvollste Sparmöglichkeit aus, die er zum richtigen Zeitpunkt bieten kann. Dies ist das richtige Muster, wenn die Rabattauswahl Stackingbeschränkungen, regulatorische Einschränkungen und genaue versicherungsmathematische Berechnungen berücksichtigen muss - Einschränkungen, die eine geregelte Entscheidungslogik erfordern, anstatt nur einfache Eignungsprüfungen durchzuführen.

### Technische Überlegungen

- Integration mit den Policy-Rating- und Abrechnungssystemen zur Berechnung der genauen Rabattberechtigung und potenziellen Einsparbeträge für jeden Kunden in Echtzeit.
- Konfigurieren Sie Entscheidungsregeln, die den Einschränkungen für die Rabattstapelung Rechnung tragen und sicherstellen, dass die kommunizierten Einsparbeträge genau sind und vom Preisfindungs-Team genehmigt wurden.
- Anwendung bundesstaatlicher Regeln für Rabattmitteilungen, da bestimmte Staaten Beschränkungen für den Vertrieb und die Anwendung von Versicherungsrabatten haben.
- Verfolgen Sie die Ergebnisse der Rabattakzeptanz, um das Entscheidungsmodell kontinuierlich zu verfeinern und die Sparbotschaften zu priorisieren, die bei den verschiedenen Kundensegmenten am meisten Anklang finden.


## Betrugsbekämpfung bei Schadensfällen

Verwenden Sie intelligente Betrugserkennung, um verdächtige Schadenmuster zu identifizieren und die Ermittlungskommunikation zu personalisieren, während das Vertrauen der Kunden gewahrt bleibt. Eine wirksame Betrugsprävention schützt ehrliche Versicherungsnehmer, indem sie die Prämien fair hält und sicherstellt, dass berechtigte Ansprüche schnell bearbeitet werden.

### Auswirkung auf den Betrieb

Mit intelligenten Programmen zur Betrugsbekämpfung werden die Aufdeckungsraten bei Betrug verbessert, betrügerische Auszahlungen reduziert und die Gesamtkosten für Schadenersatzansprüche gesenkt.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Betrugsrisiko-Bewertungsereignisse Trigger geeigneter Ermittlungsmitteilungen und Prozessanpassungen in Echtzeit, um sicherzustellen, dass gekennzeichnete Schadensfälle sofort bearbeitet werden. Dies ist das richtige Muster, wenn ein vom System abgeleitetes Ereignis (Betrugsrisikobewertung) der Trigger ist und die erforderliche Maßnahme eine sofortige interne Prozessanpassung mit sorgfältiger Kundenkommunikation ist - und nicht ein mehrstufiges Journey- oder Entscheidungsszenario.

### Technische Überlegungen

- Integrieren Sie Betrugsrisikobewertungen aus dem Schadensanalysesystem in das Kundenprofil, während Sie strenge Data-Governance-Kennzeichnungen anwenden, um zu verhindern, dass Betrugsuntersuchungsdaten in kundenorientierten Kommunikationen angezeigt werden.
- Entwerfen Sie Kommunikationswege, die einen professionellen, respektvollen Ton für Kunden aufrechterhalten, deren Ansprüche überprüft werden, und bewahren Sie die Beziehung unabhängig vom Untersuchungsergebnis.
- Implementieren Sie rollenbasierte Zugriffskontrollen, um sicherzustellen, dass Betrugsindikatoren nur für autorisierte Ermittlungsteams sichtbar sind und nie in den standardmäßigen Agenten- oder Kundendienstansichten angezeigt werden.
- Koordinieren Sie sich mit dem [!DNL Adobe Experience Platform] Identity Resolution Service, um Muster in verwandten Profilen zu erkennen, z. B. freigegebene Adressen oder Telefonnummern, die mit mehreren verdächtigen Ansprüchen verknüpft sind.


## Wellness- und Präventionsprogramme

Personalisieren Sie die Kommunikation zum Wellness-Programm, Teilnahmerinnerungen und Prämienbenachrichtigungen für Kund*innen von Kranken- und Lebensversicherungen auf Grundlage ihrer Ziele und Interaktionsstufen. Aktive Wellness-Programme verbessern die Gesundheit der Versicherungsnehmer und schaffen einen stärkeren, engagierteren Kundenstamm.

### Auswirkung auf den Betrieb

Personalisierte Mitteilungen über Wellness- und Präventionsprogramme fördern die Teilnahme an Programmen, tragen zu besseren gesundheitlichen Ergebnissen bei und reduzieren die Schadenshäufigkeit.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Wellnessprogramme sind nachhaltige Interaktionserlebnisse mit Meilensteinen, Herausforderungen und Belohnungen, die eine adaptive Orchestrierung basierend auf der Aktivität und dem Fortschritt jedes Teilnehmers erfordern. Dies ist das richtige Muster, wenn der Anwendungsfall einen langfristigen, mehrfachen Nachrichtenfluss mit interaktionsbasierter Verzweigung und adaptiven Timing-Anpassungen erfordert - ereignisgesteuertes Messaging kann die komplexe Meilenstein-Logik nicht verarbeiten oder die Notwendigkeit, die Kommunikationskadenz auf der Grundlage von nachhaltigem Aktivitäts-Tracking anzupassen.

### Technische Überlegungen

- Integration mit Daten-Feeds für Wearable-Geräte und Gesundheitsanwendungen mithilfe [!DNL Adobe Experience Platform] Streaming-Aufnahme, wobei klare Data Governance-Kennzeichnungen angewendet werden, um Wellness-Daten von Versicherungs- oder Schadensdaten zu unterscheiden.
- Implementieren Sie separate Einverständnismechanismen für die Wellness-Datenerfassung, um sicherzustellen, dass die Teilnehmer verstehen, wie ihre Gesundheitsaktivitätsdaten verwendet werden, und sich abmelden können, ohne ihre Richtlinie zu beeinflussen.
- Entwerfen Sie eine Journey-Logik, die die Programmintensität und die Kommunikationsfrequenz auf der Grundlage des Interaktionsniveaus jedes Teilnehmers anpasst, um Ermüdung zu vermeiden und anhaltende Teilnahme zu fördern.
- Wenden Sie sich vor dem Start an Ihre Rechts- und Compliance-Teams, um die Strukturen der Wellness-Incentive-Programme und die Prämienrabatte auf die Einhaltung der geltenden staatlichen Versicherungsvorschriften zu überprüfen.


## Koordination von Agent und Broker

Personalisierte Kommunikation und Koordination zwischen Kunden und ihren zugewiesenen Agenten oder Brokern auf der Grundlage von Richtlinienanforderungen, Service-Verlauf und Voreinstellungen ermöglichen. Eine bessere Koordination schafft ein nahtloses Erlebnis, bei dem sich Kunden von einem kompetenten Berater unterstützt fühlen, der ihre vollständige Beziehung versteht.

### Auswirkung auf den Betrieb

Effektive Agent- und Broker-Koordinationskommunikation führt zu einer verbesserten Agent-Interaktion, was zu stärkeren Kundenbeziehungen und einer höheren Kundenbindung führt, die durch vertrauenswürdige Beratungsinteraktionen angetrieben wird.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für ausgehende Nachrichten ](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Batch. Die Agentenkoordination wird am besten durch geplante Batch-Aktivierungen bereitgestellt, die Agenten regelmäßig mit priorisierten Kontaktlisten, Gesprächspunkten und empfohlenen Aktionen versorgen. Dies ist das richtige Muster, wenn die Zielgruppe groß und vordefiniert ist, der Versandzeitpunkt auf wiederkehrender Basis geplant wird und nicht ereignisgesteuert ist und keine Verzweigung oder Entscheidung in Echtzeit erforderlich ist.

### Technische Überlegungen

- Integration mit dem Agenten-Management-System, um präzise Agent-Kunden-Zuweisungen zu verwalten und sicherzustellen, dass die Kommunikation die richtige Beziehung widerspiegelt, insbesondere während Agentenübergängen.
- Gestalten Sie die Datenaktivierung für das Agentenportal, damit Agenten eine konsolidierte Ansicht von Kundeneinblicken, bevorstehenden Erneuerungen und empfohlenen Aktionen erhalten, ohne rohe Verhaltensdaten verfügbar zu machen.
- Wenden Sie Data-Governance-Kennzeichnungen an, um zu beschränken, welche Kundendatenelemente mit externen Brokerpartnern oder firmeneigenen Agenten geteilt werden, wobei die vertraglichen und regulatorischen Datenfreigabegrenzen zu beachten sind.
- Implementieren Sie Feedback-Schleifen aus Agenten-Interaktionen wieder in das Kundenprofil, sodass Einblicke aus persönlichen oder Telefongesprächen die einheitliche Ansicht bereichern und die zukünftige Personalisierung verbessern.


## Reaktion auf Katastrophenfälle

Proaktive Kommunikation mit Kunden in betroffenen Gebieten während Naturkatastrophen oder Katastrophenereignissen mit personalisierten Support-Informationen, Anleitungen zur Antragstellung und Notfallressourcen. Schnelle, einfühlsame Kontaktaufnahme während einer Krise zeigt das Engagement des Versicherers, dort zu sein, wo Kunden es am meisten brauchen.

### Auswirkung auf den Betrieb

Proaktive Kommunikation zur Reaktion auf Katastrophenereignisse verbessert die Kundenkommunikationsraten bei Ereignissen, beschleunigt die Einreichung von Anträgen und stärkt das langfristige Vertrauen und die Loyalität der Kunden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Katastrophenereignis-Deklarationen dienen als hochprioritäre Trigger für eine sofortige, personalisierte Kontaktaufnahme zu allen Versicherungsnehmern im betroffenen geografischen Gebiet. Dies ist das richtige Muster, wenn der Trigger ein externes Ereignis mit hoher Priorität ist und die erforderliche Reaktion eine sofortige, umfassende geografische Reichweite mit zeitkritischen Informationen ist - und nicht etwa individuelle Kundenverhaltensmuster oder eine komplexe Sequenzierung.

### Technische Überlegungen

- Integration mit Katastrophenüberwachungs-Services und der Bereitstellung von Daten für die Katastrophenanmeldung durch die Regierung, wenn Ereignisse für bestimmte geografische Gebiete gemeldet werden, schnell zur Kommunikation durch die Trigger.
- Erstellen Sie geografische Zielgruppensegmente mithilfe von Adressdaten des Versicherungsnehmers und Standortinformationen der Immobilien, um Kunden im betroffenen Bereich genau zu identifizieren, ohne zu stark mit nicht betroffenen Kunden zu kommunizieren.
- Konfigurieren Sie ein Routing für Nachrichten mit hoher Priorität, bei dem die standardmäßigen Frequenzlimitierungs- und Unterdrückungsregeln außer Kraft gesetzt werden, um sicherzustellen, dass wichtige Sicherheits- und Schadensinformationen Kunden sofort erreichen.
- Erstellen Sie Nachrichtenvorlagen und Journey-Konfigurationen für gängige Katastrophenereignistypen vorab, damit die Kommunikation innerhalb von Stunden nach einer Ereignisdeklaration aktiviert werden kann, anstatt die Erstellung von Inhalten während der Krise zu erfordern.


## Personalization für Policeninhaber-Portal

Personalisieren Sie das authentifizierte Self-Service-Portal und die Mobile App für Versicherungsnehmer, indem Sie die relevantesten Informationen, Tools und Ressourcen basierend auf ihrem Browsing-Verhalten, ihrem Policy-Portfolio und den letzten Service-Interaktionen aufdecken. Ein Portal, das sich an den aktuellen Kontext jedes Versicherungsnehmers anpasst, reduziert Reibungen und erleichtert es den Kunden, das zu finden, was sie brauchen, wenn sie es brauchen.

### Auswirkung auf den Betrieb

Durch die Personalisierung des Portals für Versicherungsnehmer werden messbare Verbesserungen bei der Erfüllung von Selbstbedienungsaufgaben und der digitalen Interaktion erzielt, das Volumen der eingehenden Kontaktzentren verringert und die Kundenzufriedenheit mit dem digitalen Kanal erhöht.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Verhaltenssignale aus authentifizierten Portal-Sitzungen - Nutzung des Abdeckungsrechners, Ansichten von Richtliniendokumenten, Statusprüfungen von Ansprüchen und Interaktion mit häufig gestellten Themen - trainieren ein Empfehlungsmodell, das dynamisch die relevantesten Inhalte und Tools für den aktuellen Kontext jedes Versicherungsnehmers aufzeigt. Dies ist das richtige Muster, wenn die Personalisierung durch implizite Verhaltenssignale innerhalb einer authentifizierten Sitzung gesteuert wird und das Ziel die Rangfolge der Relevanz eines Inhalts oder Ressourcenkatalogs ist - anstelle von Offer Decisioning, das eine geregelte Eignung und versicherungsmathematische Genehmigung erfordert, bevor ein Produktangebot unterbreitet wird, oder Cross-Channel with Decisioning, das bei der Koordinierung eines Produktangebots über mehrere Kanäle hinweg besser geeignet ist.

### Technische Überlegungen

- Wenden Sie Data Governance-Kennzeichnungen auf Verhaltenssignale an, die im Portal für Versicherungsnehmer erfasst werden, um die Interaktionsanalyse von den regulierten Versicherungsdaten zu unterscheiden, und beschränken Sie alle Signale aus dem Schadenverlauf, die ohne explizite versicherungsmathematische und Compliance-Prüfung in Personalisierungsmodelle fließen.
- Integrieren Sie das Verhaltensmodell in das Policy-Management-System, um sicherzustellen, dass die Inhalts- und Tool-Empfehlungen das aktive Policy-Portfolio jedes Versicherungsnehmers widerspiegeln, d. h. Tools zur automatischen Abdeckung für Kfz-Versicherungsnehmer und Immobilienressourcen für Hauseigentümer, ohne dem Empfehlungsmodell über die Klassifizierung der Produktlinie hinaus rohe Policy-Daten zur Verfügung zu stellen.
- Implementieren Sie landesspezifische Compliance-Kontrollen, um sicherzustellen, dass die Verhaltenspersonalisierung keine Versicherungs- oder Marketing-Empfehlung gemäß den geltenden staatlichen Vorschriften darstellt, insbesondere wenn Verhaltenssignale eine Erkennung von Abdeckungslücken implizieren könnten.
- Koordinieren Sie die Portalpersonalisierungssignale mit dem Agentenportal, damit Agenten für Versicherungsnehmer, die ein ausgeprägtes Selbstbedienungs-Forschungsverhalten gezeigt haben, neben der Servicegeschichte auch einen konsolidierten Überblick über das digitale Engagement des Kunden erhalten.
