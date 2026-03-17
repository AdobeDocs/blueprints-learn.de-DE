---
title: Anwendungsfälle für das Gesundheitswesen
description: Erfahren Sie, wie Unternehmen im Gesundheitswesen Adobe Experience Platform verwenden, um die Interaktion mit Patienten zu verbessern, die Koordinierung der Pflege zu optimieren und bessere Ergebnisse im Gesundheitswesen zu erzielen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 1%

---


# Anwendungsfälle für das Gesundheitswesen

Gesundheitseinrichtungen verwenden Adobe Experience Platform, um einheitliche Patientenprofile zu erstellen und personalisierte, zeitnahe Kommunikation über jeden Touchpoint bereitzustellen. Durch die Verbindung von klinischen Daten, Verhaltens- und Präferenzdaten an einem Ort können Betreuungsteams Patienten effektiver einbinden und dabei die höchsten Standards in Bezug auf Datenschutz und Compliance beibehalten.

## Automatisierung der Terminerinnerung

Senden Sie personalisierte Terminerinnerungen per E-Mail, SMS und Push-Benachrichtigungen basierend auf den Kommunikationsvoreinstellungen und dem Termintyp jedes Patienten. Automatische Erinnerungen reduzieren die Anzahl verpasster Termine und sorgen für einen reibungslosen Ablauf, sodass sich das Personal auf die Patientenversorgung konzentrieren kann.

### Auswirkung auf den Betrieb

Unternehmen, die automatisierte Terminerinnerungen implementieren, erzielen in der Regel eine 30- bis 40-prozentige Verbesserung der Terminanzeigeraten und eine deutliche Verringerung der kostenintensiven „No-Shows“.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Terminerstellung und Aktualisierungsereignisse aus dem Terminplanungssystem dienen als natürliche Trigger für zeitnahe, relevante Erinnerungsnachrichten.

### Technische Überlegungen

- Stellen Sie sicher, dass alle Patientenkontaktdaten und Termindetails in Übereinstimmung mit den HIPAA-Anforderungen übertragen und gespeichert werden, wobei geeignete Datennutzungskennzeichnungen verwendet werden, um den unbefugten Zugriff zu beschränken.
- Integration mit dem elektronischen System zur Planung von Gesundheitsdatensätzen, um Terminerstellung, -stornierung und -umplanung in Echtzeit zu erfassen.
- Wenden Sie Einverständnisverwaltungs-Richtlinien an, sodass Erinnerungen nur über Kanäle gesendet werden, für die sich der Patient ausdrücklich entschieden hat.
- Konfigurieren Sie Unterdrückungsregeln, um doppelte oder übermäßige Erinnerungen zu verhindern, wenn Termine in schneller Folge neu geplant werden.


## Kampagnen zur Einhaltung von Medikamenten

Senden Sie personalisierte Erinnerungen und Schulungsinhalte, damit die Patienten mit ihren Medikamenten und Behandlungsplänen auf dem Laufenden bleiben. Maßgeschneiderte Botschaften auf der Basis von Medikationstyp, Dosierungsschema und Patientenanamnese fördern eine bessere Einhaltung und bessere gesundheitliche Ergebnisse.

### Auswirkung auf den Betrieb

Personalisierte Kampagnen zur Einhaltung von Medikamenten führen in der Regel zu einer 20- bis 30-prozentigen Verbesserung der Einhaltungsraten, was zu messbar besseren Gesundheitsergebnissen und weniger Krankenhauseinweisungen führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Die Einhaltung der Medikation erfordert einen anhaltenden Multi-Touch-Ansatz mit eskalierenden Erinnerungen, Touchpoints zur Aufklärung und Follow-up-Check-ins im Verlauf eines Behandlungsplans.

### Technische Überlegungen

- Wenden Sie strenge Datennutzungskennzeichnungen auf alle geschützten Gesundheitsinformationen an, die sich auf Medikamente- und Diagnosedaten beziehen, um eine unbefugte nachgelagerte Aktivierung zu verhindern.
- Integration mit Apotheken- und elektronischen Patientendatensystemen, um Daten zum Ausfüllen und Nachfüllen von Rezepten zu erhalten, die Trigger-Journey-Schritte ausführen.
- Implementieren Sie ein robustes Einverständnismanagement, um sicherzustellen, dass die Patienten zugestimmt haben, medikamentöse Mitteilungen zu erhalten, und die Einwilligung jederzeit widerrufen können.
- Entwerfen Sie eine Journey-Logik, um Muster zu erkennen, die zu keiner Interaktion führen, und eskalieren Sie an die Benachrichtigungen des Betreuungsteams, wenn bei einem Patienten das Risiko einer Nichteinhaltung besteht.


## Erinnerungen zur Vorsorge

Proaktive Erinnerung der Patienten an empfohlene Vorsorgemaßnahmen wie Impfungen, Screenings und jährliche Untersuchungen auf der Grundlage ihres Alters, ihrer Krankengeschichte und ihrer Risikofaktoren. Rechtzeitige Erinnerungen an Vorsorgemaßnahmen helfen, Versorgungslücken zu schließen und die allgemeine Gesundheit der Bevölkerung zu verbessern.

### Auswirkung auf den Betrieb

Proaktive präventive Gesundheitsarbeit führt in der Regel zu einer 25-35-prozentigen Steigerung der Abschlussraten der präventiven Pflege, was zu einer verbesserten Gesundheit der Bevölkerung und niedrigeren Langzeitbehandlungskosten beiträgt.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für ausgehende Nachrichten &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Batch. Erinnerungen zur Vorsorge werden am besten über geplante Batch-Kampagnen bereitgestellt, die die Eignung des Patienten regelmäßig anhand klinischer Richtlinien bewerten.

### Technische Überlegungen

- Zielgruppensegmente mithilfe von Kriterien gemäß klinischen Richtlinien (Alter, Geschlecht, Familiengeschichte, frühere Screening-Daten) erstellen und dabei Datennutzungskennzeichnungen auf alle geschützten Gesundheitsinformationen anwenden, die in der Segmentierung verwendet werden.
- Koordinieren Sie sich mit klinischen Teams, um sicherzustellen, dass der Erinnerungsinhalt mit den aktuellen evidenzbasierten Präventionsrichtlinien und Organisationsprotokollen übereinstimmt.
- Setzen Sie eine Frequenzlimitierung ein, um zu vermeiden, dass Patienten, die sich für mehrere präventive Pflegeempfehlungen qualifizieren, überfordert werden.
- Führen Sie ein Audit-Protokoll zu allen Mitteilungen zur Vorsorge, die zur regulatorischen Berichterstattung und zur Dokumentation von Qualitätsmaßnahmen gesendet werden.


## Follow-up-Kampagnen nach einem Besuch

Senden Sie nach dem Besuch automatisch Umfragen, Pflegehinweise und Follow-up-Termine je nach Art des Besuchs und den spezifischen Bedürfnissen jedes Patienten. Rechtzeitige Nachuntersuchungen verbessern die Zufriedenheit der Patienten und stellen die Kontinuität der Versorgung nach jeder Begegnung sicher.

### Auswirkung auf den Betrieb

Automatisierte Follow-up-Kampagnen nach der Visite erreichen in der Regel eine Verbesserung der Antwortraten in der Befragung um 40 bis 50 Prozent und messbar höhere Patientenzufriedenheitswerte.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Besuchsabschlussereignisse aus dem elektronischen Patientendatensystem bieten einen natürlichen, zeitnahen Trigger für die Nachfolgekommunikation, die auf den jeweiligen Begegnungstyp zugeschnitten ist.

### Technische Überlegungen

- Integration mit dem elektronischen Patientendatensystem, um Besuchsentlassungsereignisse zu erhalten, die den Besuchstyp, den Provider und die relevanten Pflegehinweise umfassen, ohne vollständige klinische Hinweise verfügbar zu machen.
- Wenden Sie Datennutzungskennzeichnungen auf alle Inhalte von Pflegehinweisen an, um sicherzustellen, dass geschützte Gesundheitsinformationen nur über sichere, vom Patienten autorisierte Kanäle weitergegeben werden.
- Konfigurieren Sie Zeitregeln, die dem Besuchstyp Rechnung tragen - z. B. können postoperative Nachuntersuchungen einen anderen Zeitpunkt erfordern als routinemäßige Untersuchungen.
- Sichere Links zum Patientenportal für den Abschluss von Umfragen und die Terminplanung, anstatt Gesundheitsinformationen über ungesicherte Kanäle zu erfassen.


## Programme zur Behandlung chronischer Krankheiten

Personalisieren Sie die Kommunikation zum Management chronischer Krankheiten, die informativen Inhalte und die Überwachung der Erinnerungen basierend auf dem spezifischen Zustand und Behandlungsplan jedes Patienten. Ein nachhaltiges, relevantes Engagement hilft den Patienten, im Laufe der Zeit eine aktive Rolle bei der Verwaltung ihrer Gesundheit zu übernehmen.

### Auswirkung auf den Betrieb

Personalisierte Programme für das Management chronischer Krankheiten verzeichnen in der Regel einen Anstieg der Interaktionsraten um 30 bis 40 Prozent, was zu verbesserten Krankheitsmanagementergebnissen und einer reduzierten Nutzung der Notfallversorgung führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Chronisches Krankheitsmanagement ist von Natur aus ein langjähriges, an mehrere Touchpoints geknüpftes Erlebnis, das adaptive Messaging auf der Grundlage von Patienteninteraktion und Meilensteinen im Gesundheitswesen erfordert.

### Technische Überlegungen

- Entwerfen Sie eine Journey-Verzweigungslogik, die sich anhand von zustandsspezifischen Metriken anpasst (z. B. Blutzuckertrends für das Diabetesmanagement oder Blutdruckmessungen für Hypertonieprogramme).
- Implementieren Sie eine strikte Data Governance mit [!DNL Adobe Experience Platform] Datennutzungskennzeichnungen, um zustandsspezifische Gesundheitsdaten im gesamten Journey zu klassifizieren und zu schützen.
- Integration mit Patientenfernüberwachungsgeräten und Patientenberichtssystemen, um Gesundheitsdaten in Echtzeit in Journey-Entscheidungspunkte einzuspeisen.
- Erstellen Sie im Journey Eskalationspfade für das Betreuungsteam, damit die Trigger bei Nichtinteraktion oder Gesundheitstrends den entsprechenden Klinikmitarbeitern Warnmeldungen senden.


## Neue Patienten-Onboarding-Journey

Automatisieren Sie eine mehrstufige Onboarding-Journey für neue Patienten, die Begrüßungsinformationen, Zugriffsanweisungen für das Patientenportal und Anleitungen zur Terminplanung enthält. Ein reibungsloses Onboarding gibt den Ton für eine engagierte, langfristige Patientenbeziehung vor.

### Auswirkung auf den Betrieb

Automatisiertes Onboarding neuer Journey für Patienten führt in der Regel zu einer 50- bis 60-prozentigen Verbesserung der Portalaktivierungsraten und zu einer signifikant höheren frühzeitigen Patienteninteraktion.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Das Onboarding von Patienten ist ein von Natur aus sequenzieller, mehrstufiger Prozess, bei dem jede Kommunikation auf der vorherigen aufbaut und sich daran anpasst, ob der Patient wichtige Aktionen abgeschlossen hat.

### Technische Überlegungen

- Integration mit dem Patientenregistrierungssystem, um die Onboarding-Journey sofort nach der Erstellung neuer Patientenakten in Trigger zu nehmen, sodass ein rechtzeitiger erster Eindruck gewährleistet ist.
- Verwenden Sie die Identitätsauflösung, um bereits vorhandene Datensätze (z. B. von einem Website-Besuch oder einer Terminanfrage) mit dem neuen Patientenprofil zusammenzuführen, um doppelte Kommunikation zu vermeiden.
- Stellen Sie sicher, dass Links und Anmeldeinformationen zur Portalaktivierung über sichere, HIPAA-konforme Kanäle bereitgestellt werden und nach einem bestimmten Zeitraum ablaufen.
- Gestalten Sie die Journey so, dass sie Portalaktivierungs- und Formularvervollständigungsereignisse erkennt, sodass nachfolgende Schritte sich anpassen und Informationen, auf die der Patient bereits reagiert hat, nicht wiederholen.


## Bereitstellung personalisierter Gesundheitsinhalte

Stellen Sie personalisierte Inhalte, Wellness-Tipps und Ressourcen bereit, die auf die Bedingungen, Interessen und Gesundheitsziele jedes Patienten zugeschnitten sind. Relevante Inhalte schaffen Vertrauen, verbessern die Gesundheitskompetenz und ermöglichen Patienten, fundierte Entscheidungen über ihre Pflege zu treffen.

### Auswirkung auf den Betrieb

Die Bereitstellung personalisierter Gesundheitsinhalte erzielt in der Regel eine Steigerung der Interaktionsraten von Inhalten um 35 bis 45 Prozent, was zu einer messbar verbesserten Patientenaufklärung und Gesundheitskompetenz führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Die Bereitstellung von Gesundheitsinhalten profitiert von der Echtzeit-Entscheidungsfindung , die den relevantesten Inhalt für jeden Patienten basierend auf seinen Bedingungen, Vorlieben und vergangenen Interaktionen auswählt, die über seinen bevorzugten Kanal bereitgestellt werden.

### Technische Überlegungen

- Wenden Sie Inhaltsklassifizierungs- und Datennutzungskennzeichnungen auf alle Materialien zur Gesundheitserziehung an, um sicherzustellen, dass bedingte Inhalte nur an Patienten übermittelt werden, die dem Erhalt von Gesundheitsinformationen zu diesem Thema zugestimmt haben.
- Integrieren Sie die Entscheidungs-Engine mit einem Content-Repository, das regelmäßig von klinischen Teams überprüft und genehmigt wird, um die medizinische Genauigkeit sicherzustellen.
- Implementieren Sie Regeln zur Ermüdung von Inhalten, um zu vermeiden, dass zu viele Inhalte zu einem einzigen Thema bereitgestellt werden, und um das Schulungsmaterial auf die verschiedenen Gesundheitsbedürfnisse eines Patienten abzuwägen.
- Verfolgen Sie Inhaltsinteraktionssignale (Öffnungen, Klicks, Besuchszeit), um die Inhaltsrelevanz kontinuierlich zu verfeinern, ohne zusätzliche geschützte Gesundheitsinformationen zu erfassen oder zu speichern.


## Benachrichtigung zu Laborergebnissen

Benachrichtigen Sie die Patienten, wenn Laborergebnisse über ihren bevorzugten Kommunikationskanal mit personalisiertem, sicherem Messaging verfügbar sind. Eine sofortige Benachrichtigung ermutigt die Patienten, die Ergebnisse schnell zu überprüfen und bei Bedarf mit ihrem Betreuungsteam nachzufragen.

### Auswirkung auf den Betrieb

Automatisierte Benachrichtigungen zu Laborergebnissen führen normalerweise zu einer Steigerung der Ergebnisanzeigeraten um 60 bis 70 Prozent, verbessern die Kommunikation mit den Patienten und ermöglichen eine schnellere klinische Nachverfolgung, wenn Ergebnisse Maßnahmen erfordern.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Die Verfügbarkeit von Laborergebnissen ist ein diskretes Ereignis, das eine sofortige, einmalige Benachrichtigung über den bevorzugten Kanal des Patienten erfordert.

### Technische Überlegungen

- Die tatsächlichen Laborergebniswerte dürfen niemals in die Benachrichtigungsmeldungen aufgenommen werden - der Patient muss nur darüber informiert werden, dass die Ergebnisse verfügbar sind, und er muss sie an das sichere Patientenportal weiterleiten, um weitere Informationen zu erhalten.
- Integrieren Sie sich in das Laborinformationssystem, um ergebnisbereite Ereignisse zu empfangen, und wenden Sie gleichzeitig strenge Datennutzungskennzeichnungen an, um zu verhindern, dass klinische Daten in Marketing-Kanäle fließen.
- Implementieren Sie eine Warteschlangenlogik, damit Benachrichtigungen erst gesendet werden, nachdem der behandelnde Arzt die Ergebnisse geprüft und für den Patienten freigegeben hat.
- Stellen Sie sicher, dass alle Benachrichtigungslinks auf authentifizierte, verschlüsselte Patientenportalsitzungen verweisen, die den HIPAA-Sicherheitsanforderungen entsprechen.


## Überprüfung des Versicherungsschutzes

Proaktive Verifizierung und Kommunikation der Informationen zum Versicherungsschutz mit den Patienten vor deren Termin, um Überraschungen bei der Abrechnung zu vermeiden und das allgemeine Patientenerlebnis zu verbessern. Klare Kommunikation im Voraus schafft Vertrauen und verringert Streitigkeiten über die Abrechnung nach einem Besuch.

### Auswirkung auf den Betrieb

Die proaktive Überprüfung des Versicherungsschutzes führt in der Regel zu einer Verbesserung der Bestätigungsraten für den Versicherungsschutz vor einem Besuch um 25 bis 35 Prozent und zu einer deutlichen Verringerung von Abrechnungsstreitigkeiten und Patientenbeschwerden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Termintermine dienen als Trigger, um eine Abdeckungsprüfung einzuleiten und dem Patienten vor dem Besuch Ergebnisse zu kommunizieren.

### Technische Überlegungen

- Integration mit Systemen zur Überprüfung der Versicherungsfähigkeit, um den Status der Versicherungsdeckung in Echtzeit abzurufen, ohne die vollständigen Daten über Versicherungsansprüche in der Kundendatenplattform zu speichern.
- Wenden Sie Datennutzungskennzeichnungen auf alle Finanz- und Versicherungsinformationen an, um ihre Verwendung auf abrechnungsbezogene Mitteilungen zu beschränken.
- Konfigurieren Sie den Zeitpunkt der Nachricht, um den Patienten ausreichend Vorlaufzeit vor dem Termin zu gewähren, damit sie Deckungsprobleme lösen oder sich an ihren Versicherungsanbieter wenden können.
- Geben Sie klare Anweisungen und Kontaktinformationen für die Abrechnungsabteilung, damit Patienten vor ihrem Besuch Fragen stellen oder aktualisierte Versicherungsdetails angeben können.


## Telehealth-Terminerinnerungen

Senden Sie personalisierte Erinnerungen an Telehealth-Termine, die Verbindungsanweisungen, Tipps zur Vorbereitung und technische Support-Informationen enthalten. Wirksame Erinnerungen an elektronische Gesundheitsdienste reduzieren das Verpassen virtueller Besuche und helfen Patienten, sich mit digitalen Pflegewerkzeugen sicher zu fühlen.

### Auswirkung auf den Betrieb

Personalisierte Telehealth-Terminerinnerungen bewirken in der Regel eine 40- bis 50-prozentige Verbesserung der virtuellen Besuchsraten und beschleunigen die allgemeine Einführung von Telehealth in der gesamten Patientenpopulation.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Terminplanungsereignisse für Telemedizintermine bieten einen natürlichen Trigger für rechtzeitige Erinnerungen, die Verbindungsdetails und Anleitungen zur Vorbereitung enthalten.

### Technische Überlegungen

- Schließen Sie plattformspezifische Verbindungsanweisungen (Desktop oder Mobilgerät) ein, die auf den bekannten Gerätevoreinstellungen des Patienten oder früheren Telehealth-Sitzungsdaten basieren.
- Stellen Sie sicher, dass alle Telehealth-Verbindungslinks und Sitzungskennungen über verschlüsselte, HIPAA-konforme Kanäle bereitgestellt werden und nach dem geplanten Terminfenster ablaufen.
- Integration mit der Telehealth-Plattform, um zu erkennen, wann ein Patient erfolgreich verbunden wurde, sodass sekundäre Erinnerungsnachrichten unterdrückt werden können.
- Fallback-Pfad zu Kontaktinformationen des technischen Supports für Patienten bereitstellen, die sich nicht innerhalb eines definierten Zeitfensters vor dem Zeitpunkt des Terminbeginns angemeldet haben.


## Interaktion mit dem Wellnessprogramm

Personalisieren Sie die Kommunikation, Herausforderungen und Prämien des Wellness-Programms basierend auf den Gesundheitszielen, dem Aktivitätsniveau und den Präferenzen jedes Patienten. Die Einbindung von Wellness-Programmen motiviert Patienten, gesündere Gewohnheiten anzunehmen und das langfristige Wohlbefinden aufrechtzuerhalten.

### Auswirkung auf den Betrieb

Personalisierte Kampagnen zur Interaktion mit Wellness-Programmen erreichen in der Regel eine Steigerung der Programmteilnahmequoten um 30 bis 40 Prozent, was zu verbesserten gesundheitlichen Ergebnissen und einer stärkeren Patientenloyalität beiträgt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Wellness-Programme sind nachhaltige Interaktionserlebnisse mit mehreren Meilensteinen, Herausforderungen und Belohnungs-Touchpoints, für die eine adaptive Orchestrierung auf der Grundlage der Patientenbeteiligung und des Fortschritts erforderlich ist.

### Technische Überlegungen

- Integration mit Daten-Feeds für Wearable-Geräte und Fitness-Anwendungen bei gleichzeitiger Anwendung klarer Datennutzungskennzeichnungen, um Wellness-Daten von klinischen Gesundheitsdaten zu unterscheiden, die strengeren gesetzlichen Anforderungen unterliegen.
- Implementieren Sie ein Einverständnismanagement, das es den Patienten ermöglicht, unabhängig von ihren klinischen Kommunikationsvorlieben die Erlaubnis zur Erfassung von Wellnessdaten zu erteilen und zu widerrufen.
- Entwerfen Sie eine Journey-Logik, die die Anfrageschwierigkeiten und die Kommunikationsfrequenz auf der Grundlage der Interaktionsmuster jedes Patienten anpasst, um Entmutigung oder Ermüdung zu vermeiden.
- Stellen Sie sicher, dass die Belohnungs- und Anreizverfolgung den geltenden Gesundheitsvorschriften bezüglich Patientenaufforderungen und Anti-Kickback-Anforderungen entspricht.


## Betreuerteam-Koordination

Ermöglichen Sie eine personalisierte Kommunikation und Koordination zwischen den Patienten und ihren Mitgliedern des Pflegeteams auf der Grundlage des Behandlungsplans und der individuellen Präferenzen. Eine bessere Koordinierung führt zu nahtloseren Pflegeübergängen und verbesserten Ergebnissen für Patienten mit komplexem Pflegebedarf.

### Auswirkung auf den Betrieb

Eine effektive Koordinationskommunikation zwischen Betreuungsteams führt in der Regel zu einer 35- bis 45-prozentigen Verbesserung der Interaktion mit Betreuungsteams und messbar besseren Ergebnissen bei der Pflegekoordination in den Betreuungsplänen mehrerer Anbieter.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Die Koordination des Betreuungsteams umfasst mehrere Stakeholder und fortlaufende Kommunikationsflüsse, die sich auf der Grundlage von Meilensteinen des Behandlungsplans, Änderungen des Patientenstatus und Maßnahmen des Anbieters anpassen müssen.

### Technische Überlegungen

- Implementieren Sie rollenbasierte Zugriffskontrollen und Datennutzungskennzeichnungen, um sicherzustellen, dass jedes Mitglied des Pflegeteams nur Patientendaten erhält, die für seine Rolle im Pflegeplan relevant sind.
- Integration mit dem Betreuungs-Management und elektronischen Patientendatensystemen, um Pflegeplanaktualisierungen, Überweisungsabschlüsse und Versorgungsübergangsereignisse zu erhalten, die Trigger-Koordinationsnachrichten sind.
- Entwerfen Sie separate Kommunikationswege für patienten- und anbieterorientierte Nachrichten, um sicherzustellen, dass klinische Terminologie für Anbieter angemessen verwendet wird, während Patientennachrichten klar und zugänglich bleiben.
- Pflegen Sie einen vollständigen Audit-Protokoll aller Pflege-Koordinationskommunikationen zur Einhaltung von Pflege-Kontinuitätsvorschriften und Akkreditierungsanforderungen.
