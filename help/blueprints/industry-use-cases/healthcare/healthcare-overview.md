---
title: Anwendungsfälle für das Gesundheitswesen
description: Erfahren Sie, wie Unternehmen im Gesundheitswesen Adobe Experience Platform verwenden, um die Interaktion mit Patienten zu verbessern, die Koordinierung der Pflege zu optimieren und bessere Ergebnisse im Gesundheitswesen zu erzielen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 8da82711-a783-488d-a0ed-070b33ecbbc4
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3818'
ht-degree: 0%

---

# Anwendungsfälle für das Gesundheitswesen

Gesundheitseinrichtungen verwenden Adobe Experience Platform, um einheitliche Patientenprofile zu erstellen und personalisierte, zeitnahe Kommunikation über jeden Touchpoint bereitzustellen. Durch die Verbindung von klinischen Daten, Verhaltens- und Präferenzdaten an einem Ort können Betreuungsteams Patienten effektiver einbinden und dabei die höchsten Standards in Bezug auf Datenschutz und Compliance beibehalten.

>[!IMPORTANT]
>Anwendungsfälle im Gesundheitswesen umfassen geschützte Gesundheitsinformationen (PHI), die den HIPAA und anderen geltenden Vorschriften unterliegen. Bevor Sie eines dieser Muster implementieren, stellen Sie sicher, dass [!DNL Adobe Experience Platform] als HIPAA-fähiger Service bereitgestellt wird und dass mit Adobe ein Business Associate Agreement (BAA) geschlossen wurde. Die technischen Überlegungen in jedem Abschnitt heben wichtige Compliance-Anforderungen hervor, erschöpfen diese jedoch nicht. Arbeiten Sie mit Ihren Rechts-, Compliance- und Sicherheits-Teams zusammen, um Ihre Implementierung anhand aller geltenden gesetzlichen Anforderungen zu validieren.

## Automatisierung der Terminerinnerung

Senden Sie personalisierte Terminerinnerungen per E-Mail, SMS und Push-Benachrichtigungen basierend auf den Kommunikationsvoreinstellungen und dem Termintyp jedes Patienten. Automatische Erinnerungen reduzieren die Anzahl verpasster Termine und sorgen für einen reibungslosen Ablauf, sodass sich das Personal auf die Patientenversorgung konzentrieren kann.

### Auswirkung auf den Betrieb

Unternehmen, die automatisierte Terminerinnerungen implementieren, sehen messbare Verbesserungen bei den Terminanzeigesätzen und eine deutliche Verringerung der kostspieligen No-Shows.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Terminerstellung und Aktualisierungsereignisse aus dem Terminplanungssystem dienen als natürliche Trigger für zeitnahe, relevante Erinnerungsnachrichten. Dies ist das richtige Muster, wenn ein diskretes Terminereignis der Trigger ist und die erforderliche Reaktion eine einzige, zeitkritische Benachrichtigung ist - anstelle einer anhaltenden Interaktionssequenz, da Patienten eine sofortige Bestätigung ohne nachfolgende Schritte benötigen.

### Technische Überlegungen

- Stellen Sie sicher, dass alle Patientenkontaktdaten und Termindetails in Übereinstimmung mit den HIPAA-Anforderungen übertragen und gespeichert werden, wobei geeignete Datennutzungskennzeichnungen verwendet werden, um den unbefugten Zugriff zu beschränken.
- Integration mit dem elektronischen System zur Planung von Gesundheitsdatensätzen, um Terminerstellung, -stornierung und -umplanung in Echtzeit zu erfassen.
- Wenden Sie Einverständnisverwaltungs-Richtlinien an, sodass Erinnerungen nur über Kanäle gesendet werden, für die sich der Patient ausdrücklich entschieden hat.
- Konfigurieren Sie Unterdrückungsregeln, um doppelte oder übermäßige Erinnerungen zu verhindern, wenn Termine in schneller Folge neu geplant werden.


## Kampagnen zur Einhaltung von Medikamenten

Senden Sie personalisierte Erinnerungen und Schulungsinhalte, damit die Patienten mit ihren Medikamenten und Behandlungsplänen auf dem Laufenden bleiben. Maßgeschneiderte Botschaften auf der Basis von Medikationstyp, Dosierungsschema und Patientenanamnese fördern eine bessere Einhaltung und bessere gesundheitliche Ergebnisse.

### Auswirkung auf den Betrieb

Personalisierte Kampagnen zur Einhaltung von Medikamenten tragen dazu bei, die Einhaltungsraten zu verbessern, was zu besseren gesundheitlichen Ergebnissen und weniger Rückübernahmen in Krankenhäusern führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Die Einhaltung der Medikation erfordert einen anhaltenden Multi-Touch-Ansatz mit eskalierenden Erinnerungen, Touchpoints zur Aufklärung und Follow-up-Check-ins im Verlauf eines Behandlungsplans. Dies ist das richtige Muster, da das Medikamentenmanagement einen sequenziellen Fluss mit mehreren Nachrichten über Tage oder Wochen mit bedingter Verzweigung basierend auf Nachfüllereignissen und Interaktionssignalen erfordert - eine einzelne ausgelöste Nachricht kann die Abhängigkeitslogik zwischen Bildungsschritten und Eskalationspfaden nicht berücksichtigen.

### Technische Überlegungen

- Wenden Sie strenge Datennutzungskennzeichnungen auf alle geschützten Gesundheitsinformationen an, die sich auf Medikamente- und Diagnosedaten beziehen, um eine unbefugte nachgelagerte Aktivierung zu verhindern.
- Integration mit Apotheken- und elektronischen Patientendatensystemen, um Daten zum Ausfüllen und Nachfüllen von Rezepten zu erhalten, die Trigger-Journey-Schritte ausführen.
- Implementieren Sie ein robustes Einverständnismanagement, um sicherzustellen, dass die Patienten zugestimmt haben, medikamentöse Mitteilungen zu erhalten, und die Einwilligung jederzeit widerrufen können.
- Entwerfen Sie eine Journey-Logik, um Muster zu erkennen, die zu keiner Interaktion führen, und eskalieren Sie an die Benachrichtigungen des Betreuungsteams, wenn bei einem Patienten das Risiko einer Nichteinhaltung besteht.


## Erinnerungen zur Vorsorge

Proaktive Erinnerung der Patienten an empfohlene Vorsorgemaßnahmen wie Impfungen, Screenings und jährliche Untersuchungen auf der Grundlage ihres Alters, ihrer Krankengeschichte und ihrer Risikofaktoren. Rechtzeitige Erinnerungen an Vorsorgemaßnahmen helfen, Versorgungslücken zu schließen und die allgemeine Gesundheit der Bevölkerung zu verbessern.

### Auswirkung auf den Betrieb

Proaktive Präventionsarbeit führt zu besseren Abschlussraten in der Präventivversorgung, was zu einer besseren Gesundheit der Bevölkerung und niedrigeren Langzeitbehandlungskosten beiträgt.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für ausgehende Nachrichten ](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) Batch. Erinnerungen zur Vorsorge werden am besten über geplante Batch-Kampagnen bereitgestellt, die die Eignung des Patienten regelmäßig anhand klinischer Richtlinien bewerten. Dies ist das richtige Muster, wenn die Zielgruppe durch klinische Richtlinienkriterien vordefiniert ist, der Bereitstellungszeitpunkt eher in einem regelmäßigen Rhythmus als ereignisgesteuert geplant wird und keine Verzweigung oder Entscheidung in Echtzeit erforderlich ist.

### Technische Überlegungen

- Zielgruppensegmente mithilfe von Kriterien gemäß klinischen Richtlinien (Alter, Geschlecht, Familiengeschichte, frühere Screening-Daten) erstellen und dabei Datennutzungskennzeichnungen auf alle geschützten Gesundheitsinformationen anwenden, die in der Segmentierung verwendet werden.
- Koordinieren Sie sich mit klinischen Teams, um sicherzustellen, dass der Erinnerungsinhalt mit den aktuellen evidenzbasierten Präventionsrichtlinien und Organisationsprotokollen übereinstimmt.
- Setzen Sie eine Frequenzlimitierung ein, um zu vermeiden, dass Patienten, die sich für mehrere präventive Pflegeempfehlungen qualifizieren, überfordert werden.
- Führen Sie ein Audit-Protokoll zu allen Mitteilungen zur Vorsorge, die zur regulatorischen Berichterstattung und zur Dokumentation von Qualitätsmaßnahmen gesendet werden.


## Follow-up-Kampagnen nach einem Besuch

Senden Sie nach dem Besuch automatisch Umfragen, Pflegehinweise und Follow-up-Termine je nach Art des Besuchs und den spezifischen Bedürfnissen jedes Patienten. Rechtzeitige Nachuntersuchungen verbessern die Zufriedenheit der Patienten und stellen die Kontinuität der Versorgung nach jeder Begegnung sicher.

### Auswirkung auf den Betrieb

Automatisierte Follow-up-Kampagnen nach der Visite führen zu besseren Antwortraten in der Umfrage und höheren Scores für die Patientenzufriedenheit.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Besuchsabschlussereignisse aus dem elektronischen Patientendatensystem bieten einen natürlichen, zeitnahen Trigger für die Nachfolgekommunikation, die auf den jeweiligen Begegnungstyp zugeschnitten ist. Dies ist das richtige Muster, wenn ein diskretes Besuchsereignis der Trigger ist und die erforderliche Antwort eine sofortige Nachbereitung ist, die auf den jeweiligen Begegnungstyp zugeschnitten ist - und nicht auf eine mehrstufige Sequenz, da jeder Besuch seinen eigenen unabhängigen Nachverfolgungsbedarf erzeugt.

### Technische Überlegungen

- Integration mit dem elektronischen Patientendatensystem, um Besuchsentlassungsereignisse zu erhalten, die den Besuchstyp, den Provider und die relevanten Pflegehinweise umfassen, ohne vollständige klinische Hinweise verfügbar zu machen.
- Wenden Sie Datennutzungskennzeichnungen auf alle Inhalte von Pflegehinweisen an, um sicherzustellen, dass geschützte Gesundheitsinformationen nur über sichere, vom Patienten autorisierte Kanäle weitergegeben werden.
- Konfigurieren Sie Zeitregeln, die dem Besuchstyp Rechnung tragen - z. B. können postoperative Nachuntersuchungen einen anderen Zeitpunkt erfordern als routinemäßige Untersuchungen.
- Sichere Links zum Patientenportal für den Abschluss von Umfragen und die Terminplanung, anstatt Gesundheitsinformationen über ungesicherte Kanäle zu erfassen.


## Programme zur Behandlung chronischer Krankheiten

Personalisieren Sie die Kommunikation zum Management chronischer Krankheiten, die informativen Inhalte und die Überwachung der Erinnerungen basierend auf dem spezifischen Zustand und Behandlungsplan jedes Patienten. Ein nachhaltiges, relevantes Engagement hilft den Patienten, im Laufe der Zeit eine aktive Rolle bei der Verwaltung ihrer Gesundheit zu übernehmen.

### Auswirkung auf den Betrieb

Personalisierte Programme für die Behandlung chronischer Krankheiten führen zu höheren Interaktionsraten bei Programmen, was zu verbesserten Ergebnissen beim Krankheitsmanagement und einer reduzierten Nutzung der Notfallversorgung führt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Chronisches Krankheitsmanagement ist von Natur aus ein langjähriges, an mehrere Touchpoints geknüpftes Erlebnis, das adaptive Messaging auf der Grundlage von Patienteninteraktion und Meilensteinen im Gesundheitswesen erfordert. Dies ist das richtige Muster, da das Management chronischer Krankheiten adaptives Messaging über einen längeren Zeitraum mit bedingten Verzweigungen basierend auf klinischen Metriken und Interaktionsmustern erfordert - ereignisgesteuertes Messaging kann die laufende, dynamische Neubewertung nicht verarbeiten, die erforderlich ist, um Interventionen auf der Grundlage sich entwickelnder Gesundheitsdaten anzupassen.

### Technische Überlegungen

- Entwerfen Sie eine Journey-Verzweigungslogik, die sich anhand von zustandsspezifischen Metriken anpasst (z. B. Blutzuckertrends für das Diabetesmanagement oder Blutdruckmessungen für Hypertonieprogramme).
- Implementieren Sie eine strikte Data Governance mit [!DNL Adobe Experience Platform] Datennutzungskennzeichnungen, um zustandsspezifische Gesundheitsdaten im gesamten Journey zu klassifizieren und zu schützen.
- Integration mit Patientenfernüberwachungsgeräten und Patientenberichtssystemen, um Gesundheitsdaten in Echtzeit in Journey-Entscheidungspunkte einzuspeisen.
- Erstellen Sie im Journey Eskalationspfade für das Betreuungsteam, damit die Trigger bei Nichtinteraktion oder Gesundheitstrends den entsprechenden Klinikmitarbeitern Warnmeldungen senden.


## Neue Patienten-Onboarding-Journey

Automatisieren Sie eine mehrstufige Onboarding-Journey für neue Patienten, die Begrüßungsinformationen, Zugriffsanweisungen für das Patientenportal und Anleitungen zur Terminplanung enthält. Ein reibungsloses Onboarding gibt den Ton für eine engagierte, langfristige Patientenbeziehung vor.

### Auswirkung auf den Betrieb

Automatisiertes Onboarding neuer Journey für Patienten trägt dazu bei, die Portalaktivierungsraten zu verbessern und die frühzeitige Patienteninteraktion zu verbessern.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Das Onboarding von Patienten ist ein von Natur aus sequenzieller, mehrstufiger Prozess, bei dem jede Kommunikation auf der vorherigen aufbaut und sich daran anpasst, ob der Patient wichtige Aktionen abgeschlossen hat. Dies ist das richtige Muster, da das Onboarding einen sequenziellen, abhängigen Fluss über mehrere Tage mit Verzweigungen basierend auf Patientenaktionen (Portalaktivierung, Formularvervollständigung) erfordert - ein einzelner Nachrichten- oder Batch-Ansatz kann die Interdependenzen zwischen den Schritten nicht berücksichtigen oder sich an den progressiven Abschluss anpassen.

### Technische Überlegungen

- Integration mit dem Patientenregistrierungssystem, um die Onboarding-Journey sofort nach der Erstellung neuer Patientenakten in Trigger zu nehmen, sodass ein rechtzeitiger erster Eindruck gewährleistet ist.
- Verwenden Sie die Identitätsauflösung, um bereits vorhandene Datensätze (z. B. von einem Website-Besuch oder einer Terminanfrage) mit dem neuen Patientenprofil zusammenzuführen, um doppelte Kommunikation zu vermeiden.
- Stellen Sie sicher, dass Links und Anmeldeinformationen zur Portalaktivierung über sichere, HIPAA-konforme Kanäle bereitgestellt werden und nach einem bestimmten Zeitraum ablaufen.
- Gestalten Sie die Journey so, dass sie Portalaktivierungs- und Formularvervollständigungsereignisse erkennt, sodass nachfolgende Schritte sich anpassen und Informationen, auf die der Patient bereits reagiert hat, nicht wiederholen.


## Bereitstellung personalisierter Gesundheitsinhalte

Stellen Sie personalisierte Inhalte, Wellness-Tipps und Ressourcen bereit, die auf die Bedingungen, Interessen und Gesundheitsziele jedes Patienten zugeschnitten sind. Relevante Inhalte schaffen Vertrauen, verbessern die Gesundheitskompetenz und ermöglichen Patienten, fundierte Entscheidungen über ihre Pflege zu treffen.

### Auswirkung auf den Betrieb

Durch die Bereitstellung personalisierter Gesundheitsinhalte werden höhere Interaktionsraten erzielt, was zu einer verbesserten Patientenaufklärung und Gesundheitskompetenz führt.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Die Bereitstellung von Gesundheitsinhalten profitiert von der Echtzeit-Entscheidungsfindung , die den relevantesten Inhalt für jeden Patienten basierend auf seinen Bedingungen, Vorlieben und vergangenen Interaktionen auswählt, die über seinen bevorzugten Kanal bereitgestellt werden. Dies ist das richtige Muster, wenn bei der Inhaltsauswahl die Patientenbedingungen, Einverständnisvoreinstellungen und Kanalvoreinstellungen berücksichtigt werden müssen, während eine doppelte oder ermüdende Bereitstellung verhindert werden muss - eine mehrstufige Orchestrierung allein bietet nicht die Echtzeit-Entscheidungsebene, die erforderlich ist, um dynamische Inhaltsinventare an die individuellen Bedürfnisse des Patienten anzupassen.

### Technische Überlegungen

- Wenden Sie Inhaltsklassifizierungs- und Datennutzungskennzeichnungen auf alle Materialien zur Gesundheitserziehung an, um sicherzustellen, dass bedingte Inhalte nur an Patienten übermittelt werden, die dem Erhalt von Gesundheitsinformationen zu diesem Thema zugestimmt haben.
- Integrieren Sie die Entscheidungs-Engine mit einem Content-Repository, das regelmäßig von klinischen Teams überprüft und genehmigt wird, um die medizinische Genauigkeit sicherzustellen.
- Implementieren Sie Regeln zur Ermüdung von Inhalten, um zu vermeiden, dass zu viele Inhalte zu einem einzigen Thema bereitgestellt werden, und um das Schulungsmaterial auf die verschiedenen Gesundheitsbedürfnisse eines Patienten abzuwägen.
- Verfolgen Sie Inhaltsinteraktionssignale (Öffnungen, Klicks, Besuchszeit), um die Inhaltsrelevanz kontinuierlich zu verfeinern, ohne zusätzliche geschützte Gesundheitsinformationen zu erfassen oder zu speichern.


## Benachrichtigung zu Laborergebnissen

Benachrichtigen Sie die Patienten, wenn Laborergebnisse über ihren bevorzugten Kommunikationskanal mit personalisiertem, sicherem Messaging verfügbar sind. Eine sofortige Benachrichtigung ermutigt die Patienten, die Ergebnisse schnell zu überprüfen und bei Bedarf mit ihrem Betreuungsteam nachzufragen.

### Auswirkung auf den Betrieb

Automatisierte Benachrichtigungen zu Laborergebnissen tragen dazu bei, höhere Ergebnisanzeigeraten zu erzielen, die Kommunikation mit den Patienten zu verbessern und eine schnellere klinische Nachverfolgung zu ermöglichen, wenn Ergebnisse Maßnahmen erfordern.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Die Verfügbarkeit von Laborergebnissen ist ein diskretes Ereignis, das eine sofortige, einmalige Benachrichtigung über den bevorzugten Kanal des Patienten erfordert. Dies ist das richtige Muster, wenn ein diskretes Laborergebnisereignis der Trigger ist und die erforderliche Reaktion eine einzige, sofortige Benachrichtigung ist - anstelle einer Sequenz mit mehreren Nachrichten, da die Patienten einen sofortigen Alarm benötigen, um ihr Portal ohne zusätzliche Folgenachrichten zu überprüfen.

### Technische Überlegungen

- Die tatsächlichen Laborergebniswerte dürfen niemals in die Benachrichtigungsmeldungen aufgenommen werden - der Patient muss nur darüber informiert werden, dass die Ergebnisse verfügbar sind, und er muss sie an das sichere Patientenportal weiterleiten, um weitere Informationen zu erhalten.
- Integrieren Sie sich in das Laborinformationssystem, um ergebnisbereite Ereignisse zu empfangen, und wenden Sie gleichzeitig strenge Datennutzungskennzeichnungen an, um zu verhindern, dass klinische Daten in Marketing-Kanäle fließen.
- Implementieren Sie eine Warteschlangenlogik, damit Benachrichtigungen erst gesendet werden, nachdem der behandelnde Arzt die Ergebnisse geprüft und für den Patienten freigegeben hat.
- Stellen Sie sicher, dass alle Benachrichtigungslinks auf authentifizierte, verschlüsselte Patientenportalsitzungen verweisen, die den HIPAA-Sicherheitsanforderungen entsprechen.


## Überprüfung des Versicherungsschutzes

Proaktive Verifizierung und Kommunikation der Informationen zum Versicherungsschutz mit den Patienten vor deren Termin, um Überraschungen bei der Abrechnung zu vermeiden und das allgemeine Patientenerlebnis zu verbessern. Klare Kommunikation im Voraus schafft Vertrauen und verringert Streitigkeiten über die Abrechnung nach einem Besuch.

### Auswirkung auf den Betrieb

Die proaktive Überprüfung des Versicherungsschutzes führt zu besseren Bestätigungsraten vor einem Besuch und einer deutlichen Verringerung von Abrechnungsstreitigkeiten und Patientenbeschwerden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Termintermine dienen als Trigger, um eine Abdeckungsprüfung einzuleiten und dem Patienten vor dem Besuch Ergebnisse zu kommunizieren. Dies ist das richtige Muster, wenn ein diskretes Terminplanungsereignis der Trigger ist und die erforderliche Reaktion eine einzige, zeitkritische Benachrichtigung über die Abdeckung ist - anstelle einer mehrstufigen Interaktionssequenz, da der Patient vor seinem Termin eine eindeutige Nachricht benötigt.

### Technische Überlegungen

- Integration mit Systemen zur Überprüfung der Versicherungsfähigkeit, um den Status der Versicherungsdeckung in Echtzeit abzurufen, ohne die vollständigen Daten über Versicherungsansprüche in der Kundendatenplattform zu speichern.
- Wenden Sie Datennutzungskennzeichnungen auf alle Finanz- und Versicherungsinformationen an, um ihre Verwendung auf abrechnungsbezogene Mitteilungen zu beschränken.
- Konfigurieren Sie den Zeitpunkt der Nachricht, um den Patienten ausreichend Vorlaufzeit vor dem Termin zu gewähren, damit sie Deckungsprobleme lösen oder sich an ihren Versicherungsanbieter wenden können.
- Geben Sie klare Anweisungen und Kontaktinformationen für die Abrechnungsabteilung, damit Patienten vor ihrem Besuch Fragen stellen oder aktualisierte Versicherungsdetails angeben können.


## Telehealth-Terminerinnerungen

Senden Sie personalisierte Erinnerungen an Telehealth-Termine, die Verbindungsanweisungen, Tipps zur Vorbereitung und technische Support-Informationen enthalten. Wirksame Erinnerungen an elektronische Gesundheitsdienste reduzieren das Verpassen virtueller Besuche und helfen Patienten, sich mit digitalen Pflegewerkzeugen sicher zu fühlen.

### Auswirkung auf den Betrieb

Personalisierte Erinnerungen zu Terminen im Telehealth-Bereich helfen dabei, die Anzahl der virtuellen Besuche zu erhöhen und die Akzeptanz des Telehealth-Programms in der gesamten Patientenpopulation zu beschleunigen.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Terminplanungsereignisse für Telemedizintermine bieten einen natürlichen Trigger für rechtzeitige Erinnerungen, die Verbindungsdetails und Anleitungen zur Vorbereitung enthalten. Dies ist das richtige Muster, wenn ein diskretes Telemedizintereignis der Trigger ist und die erforderliche Reaktion eine einzige, sofortige Erinnerung mit technischer Anleitung ist - und nicht eine mehrstufige Abfolge, da Patienten klare Anweisungen vor der Verabredung benötigen, ohne dass eine nachfolgende Meldung erfolgt.

### Technische Überlegungen

- Schließen Sie plattformspezifische Verbindungsanweisungen (Desktop oder Mobilgerät) ein, die auf den bekannten Gerätevoreinstellungen des Patienten oder früheren Telehealth-Sitzungsdaten basieren.
- Stellen Sie sicher, dass alle Telehealth-Verbindungslinks und Sitzungskennungen über verschlüsselte, HIPAA-konforme Kanäle bereitgestellt werden und nach dem geplanten Terminfenster ablaufen.
- Integration mit der Telehealth-Plattform, um zu erkennen, wann ein Patient erfolgreich verbunden wurde, sodass sekundäre Erinnerungsnachrichten unterdrückt werden können.
- Fallback-Pfad zu Kontaktinformationen des technischen Supports für Patienten bereitstellen, die sich nicht innerhalb eines definierten Zeitfensters vor dem Zeitpunkt des Terminbeginns angemeldet haben.


## Interaktion mit dem Wellnessprogramm

Personalisieren Sie die Kommunikation, Herausforderungen und Prämien des Wellness-Programms basierend auf den Gesundheitszielen, dem Aktivitätsniveau und den Präferenzen jedes Patienten. Die Einbindung von Wellness-Programmen motiviert Patienten, gesündere Gewohnheiten anzunehmen und das langfristige Wohlbefinden aufrechtzuerhalten.

### Auswirkung auf den Betrieb

Personalisierte Kampagnen zur Interaktion mit Wellness-Programmen führen zu höheren Teilnahmeraten, was zu verbesserten gesundheitlichen Ergebnissen und einer stärkeren Patientenloyalität beiträgt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Wellness-Programme sind nachhaltige Interaktionserlebnisse mit mehreren Meilensteinen, Herausforderungen und Belohnungs-Touchpoints, für die eine adaptive Orchestrierung auf der Grundlage der Patientenbeteiligung und des Fortschritts erforderlich ist. Dies ist das richtige Muster, da Wellness-Programme einen sequenziellen Fluss mit mehreren Nachrichten über einen längeren Zeitraum mit bedingter Verzweigung basierend auf Teilnahme-Meilensteinen und Interaktionsmustern erfordern - ereignisgesteuertes Messaging kann die nachhaltige, adaptive Orchestrierung nicht bewältigen, die erforderlich ist, um Herausforderungen und Belohnungen auf der Grundlage der kontinuierlichen Fortschrittsverfolgung anzupassen.

### Technische Überlegungen

- Integration mit Daten-Feeds für Wearable-Geräte und Fitness-Anwendungen bei gleichzeitiger Anwendung klarer Datennutzungskennzeichnungen, um Wellness-Daten von klinischen Gesundheitsdaten zu unterscheiden, die strengeren gesetzlichen Anforderungen unterliegen.
- Implementieren Sie ein Einverständnismanagement, das es den Patienten ermöglicht, unabhängig von ihren klinischen Kommunikationsvorlieben die Erlaubnis zur Erfassung von Wellnessdaten zu erteilen und zu widerrufen.
- Entwerfen Sie eine Journey-Logik, die die Anfrageschwierigkeiten und die Kommunikationsfrequenz auf der Grundlage der Interaktionsmuster jedes Patienten anpasst, um Entmutigung oder Ermüdung zu vermeiden.
- Stellen Sie sicher, dass die Belohnungs- und Anreizverfolgung den geltenden Gesundheitsvorschriften bezüglich Patientenaufforderungen und Anti-Kickback-Anforderungen entspricht.


## Betreuerteam-Koordination

Ermöglichen Sie eine personalisierte Kommunikation und Koordination zwischen den Patienten und ihren Mitgliedern des Pflegeteams auf der Grundlage des Behandlungsplans und der individuellen Präferenzen. Eine bessere Koordinierung führt zu nahtloseren Pflegeübergängen und verbesserten Ergebnissen für Patienten mit komplexem Pflegebedarf.

### Auswirkung auf den Betrieb

Eine effektive Koordinationskommunikation zwischen Betreuungsteams führt zu einer verbesserten Interaktion mit Betreuungsteams und zu besseren Ergebnissen bei der Koordinierung der Betreuung über mehrere Anbieter hinweg.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Die Koordination des Betreuungsteams umfasst mehrere Stakeholder und fortlaufende Kommunikationsflüsse, die sich auf der Grundlage von Meilensteinen des Behandlungsplans, Änderungen des Patientenstatus und Maßnahmen des Anbieters anpassen müssen. Dies ist das richtige Muster, da die Koordinierung der Versorgung adaptive, mehrstufige Messaging-Flüsse erfordert, die sich auf der Grundlage von Meilensteinen des Behandlungsplans und Anbieteraktionen über mehrere Stakeholder hinweg verzweigen - eine einzige Nachricht oder ein einfacheres Muster kann nicht die komplexen gegenseitigen Abhängigkeiten und rollenbasierten Weiterleitungen von Nachrichten berücksichtigen, die für klinische Teams erforderlich sind.

### Technische Überlegungen

- Implementieren Sie rollenbasierte Zugriffskontrollen und Datennutzungskennzeichnungen, um sicherzustellen, dass jedes Mitglied des Pflegeteams nur Patientendaten erhält, die für seine Rolle im Pflegeplan relevant sind.
- Integration mit dem Betreuungs-Management und elektronischen Patientendatensystemen, um Pflegeplanaktualisierungen, Überweisungsabschlüsse und Versorgungsübergangsereignisse zu erhalten, die Trigger-Koordinationsnachrichten sind.
- Entwerfen Sie separate Kommunikationswege für patienten- und anbieterorientierte Nachrichten, um sicherzustellen, dass klinische Terminologie für Anbieter angemessen verwendet wird, während Patientennachrichten klar und zugänglich bleiben.
- Pflegen Sie einen vollständigen Audit-Protokoll aller Pflege-Koordinationskommunikationen zur Einhaltung von Pflege-Kontinuitätsvorschriften und Akkreditierungsanforderungen.


## Journey Funnel und Pflegelückenanalyse für Patienten

Ordnen Sie das End-to-End-Journey des Patienten von der anfänglichen Web-Recherche über Terminplanung, Pflegebereitstellung und Nachsorge zu, um zu ermitteln, wo Patienten sich zurückziehen und welche Populationen Lücken in der empfohlenen präventiven oder chronischen Pflege haben. Gesundheitssysteme, denen die Sichtbarkeit des Cross-Channel-Journey fehlt, können nicht zwischen Reibung beim Terminieren und der Entbindung der Patienten unterscheiden - was ihre Fähigkeit einschränkt, den Zugang zu verbessern und Versorgungslücken im großen Maßstab zu schließen.

### Auswirkung auf den Betrieb

Wenn man weiß, wo Patienten die Versorgungswege abbrechen und welche Mitglieder die höchste Konzentration an Versorgungslücken aufweisen, kann das Betreuungs-Management und das Marketing-Team die Ressourcen auf die Populationen und Reibungspunkte konzentrieren, die die größte Verbesserung bei der Einhaltung der Versorgungsvorschriften bewirken.

### Implementieren

Verwenden Sie das [Muster Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) . Dieser Ansatz verbindet Web- und Portal-Verhaltensdaten, Termindatensätze und Pflegeanfragedaten mit Customer Journey Analytics, wo die Fallout-Analyse den Abbruch bei jedem Zeitplan- oder Pflegeschritt misst und die Kohortenanalyse identifiziert, welche Mitgliedersegmente die niedrigsten Pflege-Compliance-Raten haben. Wenn das Ziel in der Generierung und Populationsanalyse von insight besteht, ist dies das richtige Muster - zu verstehen, wo die Journey aufbrechen und wer am meisten gefährdet ist - anstatt eine Kontaktaufnahme auszulösen oder eine Unterdrückungsliste zu aktivieren.

### Technische Überlegungen

- Termins- und Anspruchsdaten aus klinischen Systemen müssen vor der Aufnahme in AEP HIPAA-konformen XDM-Schemata zugeordnet werden. Außerdem müssen Datennutzungskennzeichnungen angewendet werden, um den Zugriff auf geschützte Gesundheitsinformationen in CJA-Datenansichten zu beschränken.
- Patienten- oder Mitgliedsidentifikatoren im Web-Portal, im Zeitplansystem und in der EHR müssen in eine konsistente Personen-ID in der CJA-Verbindung aufgelöst werden, um eine kohärente systemübergreifende Journey-Ansicht zu erstellen, ohne Einzelpersonen zu duplizieren.
- Die Pflegelückenanalyse erfordert Suchdatensätze, die klinische Richtliniendefinitionen codieren - z. B. empfohlene Vorsorgeintervalle nach Alter und Zustand -, damit aus CJA abgeleitete Felder Mitglieder kennzeichnen können, die die empfohlene Behandlung nicht innerhalb des Richtlinienfensters abgeschlossen haben.
- Planung Die funnel-Analyse sollte sowohl abgeschlossene als auch abgebrochene Planungssitzungen erfassen, einschließlich Ausgangspunkte in mehrstufigen Planungsflüssen, damit Reibungspunkte auf Schrittebene und nicht als aggregierte Abbruchraten sichtbar sind.


## Inhalt des Patientenportals - Personalization

Personalisieren Sie das authentifizierte Patientenportal-Erlebnis, indem Sie die relevantesten Inhalte, Tools und Ressourcen für das Gesundheitswesen basierend auf dem Verhalten und der Interaktionsgeschichte jedes einzelnen Patienten während der Sitzung aufdecken. Ein Portal, das sich an das anpasst, woran ein Patient aktiv forscht - anstatt jedem Besucher dasselbe statische Erlebnis zu präsentieren - erleichtert es den Patienten, das zu finden, was sie brauchen, und ermutigt zu einer stärkeren Interaktion mit den verfügbaren Gesundheitsressourcen.

### Auswirkung auf den Betrieb

Die Personalisierung des Patientenportalerlebnisses auf der Grundlage des Interaktionsverhaltens steigert die Erkennung von Inhalten und die Selbstbedienungsrate. Patienten können so sicherer durch ihre Versorgung navigieren, ohne dass ein Eingreifen des Betreuungsteams erforderlich ist.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). In-Session-Verhaltenssignalen aus dem authentifizierten Portal - einschließlich Seitenansichten der Inhalte, Nutzung von Gesundheitstools, Interaktion mit FAQ-Themen und Terminplanung - wird ein Empfehlungsmodell trainiert, das die relevantesten Ressourcen für jeden Patienten basierend auf dem, was er aktiv untersucht, aufzeigt, ohne dass klinische Daten als Eingabe erforderlich sind. Dies ist das richtige Muster, wenn die Personalisierung durch implizite Verhaltenssignale innerhalb einer authentifizierten Sitzung gesteuert wird und das Ziel das Ranking der Relevanz eines Inhalts und eines Ressourcenkatalogs ist - anstelle einer geregelten Eignungsentscheidung, die besser geeignet ist, wenn klinische Kriterien bewerten müssen, was ein Patient sieht.

### Technische Überlegungen

- Beschränken Sie Verhaltenssignale, die für Recommendations verwendet werden, auf Daten zu Portalinteraktionen - Inhaltsansichten, Tool-Nutzung und Navigationsmuster - und implementieren Sie Datennutzungskennzeichnungen, die verhindern, dass abgeleitete Gesundheitsinteressen außerhalb der authentifizierten Portalsitzung oder in Marketing-Kanäle fließen.
- Implementieren Sie eine klinisch geprüfte Inhaltsbibliothek als Empfehlungspool, sodass das Modell nur vorab genehmigte Gesundheitserziehungsmaterialien aufdecken kann, um sicherzustellen, dass jede empfohlene Ressource vor der Bereitstellung auf ihre Genauigkeit überprüft wurde.
- Stellen Sie sicher, dass das Empfehlungssystem die HIPAA-Anforderungen an die technische Sicherheit für die authentifizierte Portal-Umgebung erfüllt, einschließlich der Steuerung von Sitzungs-Timeouts und der Auditprotokollierung, welche Inhalte jedem Patienten zu welchem Zeitpunkt präsentiert wurden.
- Stellen Sie Patienten sichtbare Kontrollmöglichkeiten zur Verfügung, um den Navigationsverlauf des Portals zu löschen und die Verhaltenspersonalisierung zu deaktivieren, sodass die Transparenz und das Vertrauen in die Verwendung ihrer Interaktionsdaten innerhalb des Portalerlebnisses gewahrt bleiben.

## Patienteninteraktion und Terminerinnerungen

Senden Sie personalisierte Terminerinnerungen, Gesundheitstipps und Folgenachrichten über konforme, einverständnisbewusste Multi-Channel-Journey. Automatisierte, personalisierte Erinnerungen an Termine senken die Abwesenheitsraten und stellen gleichzeitig sicher, dass die Kommunikation den Datenschutzbestimmungen des Gesundheitswesens und den Präferenzen des Patienten entspricht.

### Auswirkung auf den Betrieb

Gesundheitsorganisationen mit automatisierten Erinnerungsprogrammen für Termine können signifikante Senkungen der No-Show- und Late-Cancellation-Raten feststellen, was durch bessere Einhaltung von Terminen die Auslastung des Anbieterzeitplans und die Ergebnisse für die Gesundheit der Patienten verbessert.

### Implementieren

Verwenden Sie das [Ereignisgesteuerte Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um auf Terminplanungsereignisse mit zeitnahen, personalisierten Erinnerungen zu reagieren, die in optimalen Intervallen vor dem Termindatum stattfinden. Dies ist das richtige Muster, wenn die Kommunikation durch ein bestimmtes Patienteninteraktionsereignis ausgelöst wird und die Reaktion eine zeitabhängige, individualisierte Nachricht ist - und keine mehrwöchige Pflegesequenz oder komplexe Angebotsauswahl.

### Technische Überlegungen

- Alle Patientenmitteilungen müssen den geltenden Datenschutzbestimmungen für das Gesundheitswesen entsprechen. Der Nachrichteninhalt muss vermeiden, geschützte Gesundheitsinformationen über das für die Kommunikation unbedingt erforderliche Maß hinaus einzuschließen.
- Die Einverständnisverwaltung muss auf Kanalebene durchgesetzt werden - Patienten, die sich nicht für SMS-Erinnerungen entschieden haben, dürfen keine Texte erhalten, selbst wenn SMS der effektivste Erinnerungskanal für ihre Demografie wäre.
- Die Integration mit dem Terminplanungssystem muss Terminereignisse nahezu in Echtzeit bereitstellen, damit der Erinnerungszeitpunkt dem tatsächlichen Terminplan entspricht, einschließlich der Neutermine und Absagen am selben Tag.
- Mehrkanalige Erinnerungssequenzen müssen eine Unterdrückungslogik enthalten, damit Patienten, die ihren Termin bestätigen, keine Erinnerungsnachrichten für diesen Termin erhalten.
