---
title: B2B-Anwendungsfälle
description: Erfahren Sie, wie B2B-Unternehmen Adobe Experience Platform verwenden, um die Pipeline zu beschleunigen, die Lead-Qualität zu verbessern und die Kundenexpansion zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 1%

---


# B2B-Anwendungsfälle

Business-to-Business-Unternehmen verwenden Adobe Experience Platform zur Vereinheitlichung von Account- und Personendaten, sodass Marketing- und Vertriebsteams in allen Phasen des Journey-Kaufs koordinierte, relevante Erlebnisse bereitstellen können. Von der Pipeline-Beschleunigung bis zur Kundenerweiterung zeigen diese Anwendungsfälle, wie B2B-Teams komplexe Daten in messbare Geschäftsergebnisse umwandeln.

>[!NOTE]
>
>Blueprints für die B2B-spezifische Architektur, einschließlich kontobasierter Aktivierung und Einkaufsgruppenverwaltung, finden Sie unter [B2B-Aktivierung und Marketing-Blueprints](/help/blueprints/b2b/overview.md).

## Account-Based Marketing Personalization

Personalisieren Sie die Marketing-Kommunikation und den Inhalt für Zielkonten auf der Grundlage des Kontoprofils, des Interaktionsverlaufs und der Kaufsignale. Durch die Ausrichtung der Botschaften an den individuellen Kontexten jedes Kontos können Marketing-Teams das Rauschen durchbrechen und die richtigen Stakeholder mit den richtigen Inhalten interagieren.

### Auswirkung auf den Betrieb

Unternehmen, die Account-basierte Marketing-Personalisierung implementieren, verzeichnen in der Regel einen Anstieg der Account-Interaktionsrate um 30-40 %, was zu einer stärkeren Pipeline und einem schnelleren Abschluss-Fortschritt führt.

### Implementieren

Verwenden Sie das [B2B-Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)-Muster, um Zielgruppen auf Kontoebene zu erstellen und kanalübergreifend personalisierte Inhalte zu aktivieren. Dieses Muster wurde speziell für Account-basierte Strategien entwickelt und unterstützt sowohl das Targeting auf Konto- als auch auf Personenebene.

### Technische Überlegungen

- CRM-Daten integrieren (z. B. [!DNL Salesforce] oder [!DNL Microsoft Dynamics]), um aktuelle Account-Hierarchien, Opportunity-Stadien und Eigentümerzuweisungen beizubehalten.
- Konfigurieren Sie Profilschemata auf Kontoebene, um firmografische Attribute wie Branche, Mitarbeiteranzahl, Umsatzbereich und Technologie-Stack zu erfassen.
- Ordnen Sie Personen-Konto-Beziehungen zu, um sicherzustellen, dass individuelle Interaktionssignale für die Bewertung und Segmentierung auf Kontoebene verwendet werden.
- Stimmen Sie sich mit [!DNL Marketo Engage] ab, um Marketing-Automatisierungskampagnen auf plattformgesteuerte Account-Zielgruppen abzustimmen.


## Lead-Bewertung und -Pflege

Führt automatisch eine Bewertung für Leads anhand von Profildaten und -verhalten durch und leitet dann Leads mit hoher Punktzahl mit personalisierten Pflegekampagnen für andere zu Verkäufen weiter. Dieser Ansatz stellt sicher, dass sich die Vertriebsteams auf die viel versprechendsten Möglichkeiten konzentrieren, während das Marketing die Interessenten in einer früheren Phase weiter entwickelt.

### Auswirkung auf den Betrieb

Unternehmen, die verhaltensorientierte Lead-Bewertung und automatisierte Pflege implementieren, erreichen in der Regel einen Anstieg der Lead-zu-Opportunity-Konversionen um 25-35 %, wodurch die Pipeline-Geschwindigkeit beschleunigt und die Verkaufsproduktivität verbessert wird.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um verzweigende Journey zu entwickeln, die auf Änderungen der Lead-Bewertung und Verhaltens-Trigger reagieren. Dieses Muster unterstützt die bedingte Logik, die zum Routen von Leads zwischen Nurture-Tracks und Workflows zur Verkaufsübergabe erforderlich ist.

### Technische Überlegungen

- Einrichten einer bidirektionalen CRM-Synchronisation (z. B. [!DNL Salesforce] oder [!DNL Microsoft Dynamics]), damit Lead-Bewertungen und Qualifizierungsstatus zwischen Marketing- und Vertriebssystemen konsistent bleiben.
- Definieren Sie sowohl demografische (Rolle, Unternehmensgröße, Branche) als auch verhaltensbezogene Dimensionen (Inhalts-Downloads, Webinar-Anwesenheit, Produktseitenbesuche) für die Bewertung.
- Koordinieren Sie Lead-Bewertungsmodelle mit [!DNL Marketo Engage], um plattformübergreifend widersprüchliche Bewertungen zu vermeiden.
- Legen Sie Regeln für den Verfall von Bewertungen fest, um sicherzustellen, dass Leads, die nicht geräuschlos sind, im Laufe der Zeit depriorisiert werden.


## Content Personalization für Interessenten

Personalisieren Sie den Inhalt, die Ressourcen und die Angebote der Website basierend auf der Branche, der Rolle, der Unternehmensgröße und dem Interaktionsverlauf des potenziellen Kunden. Wenn Interessenten Inhalte sehen, die für ihre spezifische Situation relevant sind, interagieren sie stärker und durchlaufen die funnel schneller.

### Auswirkung auf den Betrieb

B2B-Unternehmen, die Web-Erlebnisse für bekannte Interessenten personalisieren, verzeichnen in der Regel einen Anstieg der Interaktion mit Inhalten um 20-30 %, was zu einer stärker qualifizierten Pipeline und kürzeren Verkaufszyklen führt.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um auf der Grundlage einheitlicher Profile potenzieller Kundinnen und Kunden maßgeschneiderte Inhaltserlebnisse bereitzustellen. Dieses Muster nutzt Echtzeit-Profildaten, um für jeden Besucher die relevantesten Ressourcen, Fallstudien und Aktionsaufrufe bereitzustellen.

### Technische Überlegungen

- Implementieren Sie die Identitätsauflösung, damit das anonyme Browsing-Verhalten bekannten Interessenten-Datensätzen entspricht, sobald sie sich authentifizieren oder ein Formular senden.
- Definieren Sie Personalisierungsregeln anhand von Attributen auf Kontoebene (Branche, Segment, Abschlussstufe) sowie Attributen auf individueller Ebene (Rolle, vergangener Inhaltsverbrauch).
- Integration mit Ihrem Content-Management-System, um Hero-Banner, Ressourcenempfehlungen und Aktionsaufrufe dynamisch auszutauschen.
- Stellen Sie sicher, [!DNL Marketo Engage] Webtracking-Daten in das einheitliche Profil eingespeist werden, um ein vollständiges Verhaltensbild zu erhalten.


## Registrierung und Follow-up von Veranstaltungen

Personalisierte Bestätigungen, Erinnerungen und Follow-up für Veranstaltungen basierend auf Ereignistyp und Teilnehmerprofil automatisieren Dadurch werden Interessenten vor, während und nach Ereignissen aktiv gehalten, während das Marketing-Team von der manuellen Koordination befreit wird.

### Auswirkung auf den Betrieb

Automatisierte, personalisierte Workflows für die Veranstaltungskommunikation steigern in der Regel die Teilnahme an Veranstaltungen um 40-50 %, maximieren die Rendite aus Investitionen in Veranstaltungen und stärken die Beziehungen zu Interessenten.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um den gesamten Ereignislebenszyklus von der Registrierung bis hin zur Pflege nach dem Ereignis zu orchestrieren. Dieses Muster unterstützt zeitbasierte Trigger, bedingte Verzweigungen nach Ereignistyp und mehrkanalige Folgesequenzen.

### Technische Überlegungen

- Registrierungsdaten von Webinar-Plattformen (z. B. [!DNL ON24], [!DNL Zoom Webinar]) und persönlichen Veranstaltungssystemen in das einheitliche Profil integrieren.
- Erfassen Sie Anwesenheit und Interaktionssignale (Sitzungsdauer, gestellte Fragen, Umfrageantworten), um Folgenachrichten zu personalisieren.
- Koordinieren Sie Ereignis-Journey mit [!DNL Marketo Engage] Programmstatus, um systemübergreifend ein konsistentes Reporting zu gewährleisten.
- Entwerfen Sie separate Journey-Verzweigungen für Teilnehmer und Teilnehmer bzw. Teilnehmer, die nicht teilgenommen haben, mit maßgeschneiderten Inhalten für jeden Teilnehmer.


## Konversionskampagnen zu Produktversuchen

Ansprechen Sie Testanwender mit personalisierten Produktempfehlungen, Schulungsressourcen und Angeboten, um die Konvertierung in bezahlte Pläne zu fördern. Durch die Begegnung mit Testbenutzern, wo sie sich in der Produkterkundung befinden, können Teams Reibungen beseitigen und den Weg zum Kauf beschleunigen.

### Auswirkung auf den Betrieb

Unternehmen, die personalisierte Testkonversionskampagnen bereitstellen, verzeichnen in der Regel einen Anstieg der Konversionen zwischen Testversand und Paid um 25-35 %, was sich direkt auf den Unternehmensumsatz auswirkt und die Kosten für die Kundenakquise senkt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um zeit- und verhaltensbasierte Konversions-Journey für Testanwender zu erstellen. Dieses Muster unterstützt bedingte Pfade, die auf Produktnutzungs-Meilensteinen basieren, und ermöglicht gezielte Nudges zum richtigen Zeitpunkt.

### Technische Überlegungen

- Nehmen Sie die Produktnutzungsmessung (Funktionsübernahme, Anmeldefrequenz, Produkteinführungszeit) auf, um Echtzeit-Testinteraktionsprofile zu erstellen.
- Definieren Sie nutzungsbasierte Meilensteine (z. B. erstes erstelltes Projekt, verwendetes Schlüsselfeature, eingeladene Zusammenarbeit) als Journey-Trigger für zeitnahe Kontaktaufnahme.
- Synchronisieren Sie Teststatus- und Konversionsereignisse wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit die Vertriebsmitarbeiter die Testaktivität vollständig einsehen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage] Nurture-Programmen, um Überschneidungen der Kommunikation während der Testphase zu vermeiden.


## Customer Success und Onboarding

Personalisieren Sie Onboarding-Journey für Kunden mit relevanten Schulungen, Ressourcen und Support, die auf dem erworbenen Produkt und dem Kundenprofil basieren. Effektives Onboarding reduziert die Wertschöpfungszeit und schafft die Grundlage für langfristige Kundenbindung und Wachstum.

### Auswirkung auf den Betrieb

Unternehmen mit personalisierten Onboarding-Programmen erzielen in der Regel innerhalb der ersten 90 Tage eine 50-60%ige Steigerung der Funktionsübernahme, was direkt zu höheren Bindungs- und Expansionsumsätzen beiträgt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Onboarding-Sequenzen zu orchestrieren, die auf Produkt, Planebene und Kundensegment zugeschnitten sind. Dieses Muster unterstützt einen Milestone-basierten Fortschritt und stellt sicher, dass Kunden in jeder Phase ihres Onboarding die richtige Anleitung erhalten.

### Technische Überlegungen

- Nehmen Sie die Produktnutzungsmetrik auf, um Onboarding-Meilensteine (erste Anmeldung, Erstkonfiguration, erster abgeschlossener Workflow) zu verfolgen, und führen Sie den nächsten Journey-Trigger entsprechend aus.
- Ordnen Sie Kundenprofile der richtigen Onboarding-Spur zu, basierend auf erworbenem Produkt, Planebene und der Anzahl der lizenzierten Benutzer.
- Integrieren Sie Daten der Customer Success-Plattform, um Integritätsbewertungen zu ermitteln und Risikokonten für proaktive Maßnahmen zu kennzeichnen.
- Synchronisieren Sie den Onboarding-Status und die Akzeptanzmetriken wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit Customer Success Manager die Kontaktaufnahme priorisieren können.


## Kampagnen zur Vertragsverlängerung

Proaktive Interaktion mit Kunden, die eine Vertragsverlängerung anstreben, mit personalisierten Angeboten, Nutzungseinblicken und Verlängerungsanreizen. Zeitnahe, datengesteuerte Verlängerungsaktionen reduzieren die Abwanderung und schützen die wiederkehrenden Umsätze.

### Auswirkung auf den Betrieb

Unternehmen, die proaktive, personalisierte Verlängerungskampagnen durchführen, verzeichnen in der Regel einen Anstieg der Verlängerungsrate um 30-40 %, wodurch der wiederkehrende Umsatz geschützt und die Kosten für die Wiederbeschaffung von Kunden gesenkt werden.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um das richtige Erneuerungsangebot über den richtigen Kanal zum richtigen Zeitpunkt bereitzustellen. Dieses Muster kombiniert die Journey-Orchestrierung mit Offer Decisioning und ermöglicht dynamische Verlängerungsanreize basierend auf dem Wert und der Nutzung des Kontos.

### Technische Überlegungen

- Das Enddatum des Vertrags, die Verlängerungsbedingungen und den Kontowert zum entsprechenden Vorlaufzeitpunkt (z. B. 90, 60, 30 Tage) von [!DNL Salesforce] oder [!DNL Microsoft Dynamics] auf die Journey der Trigger-Verlängerung abrufen.
- Integrieren Sie Produktnutzungsdaten und Kundengesundheitsbewertungen, um das Erneuerungsrisiko zu bestimmen und die Angebotsstrategie entsprechend anzupassen.
- Verwenden Sie Decisioning, um den optimalen Verlängerungsanreiz (Rabatt, verlängerte Bedingungen, Premium-Upgrade) basierend auf dem Wert der Kontolebensdauer und der Abwanderungswahrscheinlichkeit auszuwählen.
- Koordinieren Sie die Verlängerungsarbeit mit den Customer Success- und Vertriebsteams, um widersprüchliche Nachrichten durch die Zuweisung von [!DNL Marketo Engage]- und CRM-Aufgaben zu vermeiden.


## Upsell- und Erweiterungsmöglichkeiten

Identifizieren Sie Kunden, die für Produkt-Upgrades oder zusätzliche Lizenzen bereit sind, basierend auf Nutzungsmustern, Wachstumsindikatoren und Kundenerfolgsdaten. Proaktive Expansionsmaßnahmen machen aus der Kundendynamik ein Umsatzwachstum.

### Auswirkung auf den Betrieb

Unternehmen, die Expansionssignale systematisch identifizieren und darauf reagieren, generieren in der Regel eine Steigerung des Expansionsumsatzes um 20-30 %, wodurch die Nettoumsatzbindung und der Kundenlebenszeitwert verbessert werden.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um personalisierte Upsell- und Expansionsangebote auf der Grundlage von Echtzeit-Nutzung und Kontosignalen bereitzustellen. Dieses Muster verwendet die Entscheidungsfindung, um jedes Konto kanalübergreifend mit dem relevantesten Erweiterungsangebot abzugleichen.

### Technische Überlegungen

- Nehmen Sie die Telemetrie zur Produktnutzung auf, um Erweiterungssignale wie Lizenznutzungsschwellen, Funktionsobergrenzen und wachsende Benutzerzahlen zu erkennen.
- Erstellen Sie Tendenzmodelle auf Kontoebene mit historischen Erweiterungsdaten, Nutzungstrends und firmografischen Attributen.
- Synchronisieren Sie Erweiterungsmöglichkeiten und empfohlene Angebote wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit Vertriebsteams die vom Marketing generierte Pipeline verfolgen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um sicherzustellen, dass Expansion Messaging nicht mit laufendem Support oder Erneuerungskommunikation kollidiert.


## Konkurrenzfähige Ersatzkampagnen

Targeting von potenziellen Kunden durch Verwendung von Produkten von Mitbewerbern mit personalisiertem Messaging, Migrationsangeboten und Vergleichen mit Mitbewerbern. Durch die Behandlung der spezifischen Probleme jedes Mitbewerbers können Marketing-Teams effektiver differenzieren und Switching-Entscheidungen beschleunigen.

### Auswirkung auf den Betrieb

B2B-Organisationen, die zielgerichtete wettbewerbsorientierte Ersatzkampagnen durchführen, erreichen in der Regel eine Steigerung der wettbewerbsfähigen Gewinnquote um 15-25 %, erobern Marktanteile und verdrängen etablierte Anbieter.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Multi-Touch-Kampagnen im Wettbewerb zu orchestrieren, die auf die spezifischen Wettbewerber- und Interessentenprofile zugeschnitten sind. Dieses Muster unterstützt eine bedingte Verzweigung auf der Grundlage der vom Mitbewerber identifizierten Inhalte und ermöglicht so eine Botschaft, die die individuellen Probleme jedes Wettbewerbsszenarios adressiert.

### Technische Überlegungen

- Daten zu Wettbewerbsinformationen (z. B. technische Anbieter, CRM-Mitbewerberfelder) in das einheitliche Profil integrieren, um zu ermitteln, welchen Mitbewerber ein potenzieller Mitbewerber derzeit verwendet.
- Erstellen Sie wettbewerbsspezifische Content-Assets (Migrationshandbücher, Vergleichsblätter, ROI-Rechner) und ordnen Sie sie Journey-Inhaltsblöcken zu.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um Konkurrenzkampagnen für potenzielle Kunden, die sich bereits in aktiven Verkaufszyklen befinden, oder Bestandskunden zu unterbinden.
- Verfolgen Sie die Pipeline zur Verdrängung von Mitbewerbern in [!DNL Salesforce] oder [!DNL Microsoft Dynamics] mit dedizierter Kampagnenzuordnung, um die Effektivität des Programms zu messen.


## Webinar- und Demoplanung

Personalisieren Sie die Einladungen zu Webinaren und die Planung der Demos auf der Grundlage der Interessen, der Branche und des Interaktionsverlaufs des potenziellen Kunden. Relevante, zeitnahe Einladungen steigern die Anwesenheit und generieren aus Live-Interaktionen eine Pipeline mit höherer Qualität.

### Auswirkung auf den Betrieb

Personalisierte Einladungsprogramme für Webinare und Demos steigern in der Regel die Teilnahme an Webinaren um 35-45 %, wodurch die Möglichkeiten der Live-Interaktion noch besser qualifiziert werden.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöste Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um personalisierte Einladungen zu senden, wenn Interessenten Interessensignale zeigen, die auf kommende Webinar- oder Demothemen abgestimmt sind. Dieses Muster reagiert in Echtzeit auf verhaltensbezogene Trigger und stellt sicher, dass Einladungen ankommen, wenn das Interesse am größten ist.

### Technische Überlegungen

- Definieren Sie interessenbasierte Trigger-Ereignisse (z. B. Besuch einer Produktseite, Herunterladen einer zugehörigen Ressource, Interaktion mit einem Konkurrenzvergleich), die mit geplanten Webinar- oder Demothemen im Einklang stehen.
- Integrieren Sie Daten der Webinar-Plattform (z. B. [!DNL ON24], [!DNL Zoom Webinar]), um Registrierungs-, Teilnahme- und Interaktionsmetriken innerhalb des einheitlichen Profils zu verfolgen.
- Synchronisieren Sie Demoanfragen und planen Sie Daten mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], um sicherzustellen, dass die Vertriebsteams rechtzeitig Benachrichtigungen und Kontext erhalten.
- Koordinieren Sie die Einladungskadenz mit [!DNL Marketo Engage] Kommunikationsbeschränkungen, um zu verhindern, dass potenzielle Kunden, die sich für mehrere Ereignisse qualifizieren, übermäßig viele Nachrichten senden.


## Fallstudie und ROI Personalization

Stellen Sie personalisierte Fallstudien, ROI-Rechner und Erfolgsgeschichten bereit, die auf der Branche, der Unternehmensgröße und dem Anwendungsfall des potenziellen Kunden basieren. Wenn Interessenten von Organisationen, die ihren ähnlich sind, Korrekturpunkte erhalten, wächst das Vertrauen schneller und Kaufentscheidungen werden schneller.

### Auswirkung auf den Betrieb

Unternehmen, die Korrekturabzugsinhalte personalisieren, verzeichnen in der Regel einen Anstieg der Interaktion mit Fallstudien um 25-35 %, was zu stärkerem Abschlussvertrauen und schnelleren Abschlussraten beiträgt.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um die relevantesten Fallstudien und ROI-Erkenntnisse dynamisch basierend auf dem Profil jedes potenziellen Kunden darzustellen. Dieses Muster ordnet Besucherattribute einer Inhaltsbibliothek zu und stellt sicher, dass jeder Interessent Testpunkte aus seiner Branche und aus anderen Gruppen erhält.

### Technische Überlegungen

- Markieren Sie Fallstudien und ROI-Inhalte mit Metadaten (Branche, Unternehmensgröße, Anwendungsfall, Produkt), um einen dynamischen Abgleich mit Interessentenprofilen zu ermöglichen.
- Implementieren Sie Personalisierungsregeln, die zunächst Branchenabgleich, dann Unternehmensgröße und Anwendungsfall priorisieren, mit Fallback-Inhalten für potenzielle Kunden mit eingeschränkten Profildaten.
- Integrieren Sie Content-Interaktionssignale (Downloads, Zeit auf der Seite, Freigaben) wieder in das einheitliche Profil, um Lead-Bewertung und Verkaufsförderung zu unterstützen.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um personalisierte Korrekturpunktinhalte in die Pflege-E-Mail-Sequenzen und nicht nur in die Erlebnisse vor Ort einzubeziehen.


## Programme zur Kundenunterstützung

Identifizieren und gewinnen Sie zufriedene Kunden für Advocacy-Möglichkeiten wie Referenzen, Fallstudien und Testimonials, die auf Datennutzungs- und Zufriedenheitsdaten basieren. Zufriedene Kunden sind ein leistungsstarker Wachstumsmotor, wenn sie erkannt und eingeladen werden, ihren Erfolg zu teilen.

### Auswirkung auf den Betrieb

Strukturierte Programme zur Kundeninteraktion fördern in der Regel eine Steigerung der Interessensvertretung um 20-30 %, wodurch ein stetiger Strom von Referenzen, Fallstudien und Testimonials generiert wird, die die Akquise neuer Unternehmen unterstützen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Advocacy-Identifikations- und Interaktions-Workflows zu erstellen, die auf Zufriedenheits- und Nutzungssignale reagieren. Dieses Muster unterstützt progressive Advocacy-Aufgaben, beginnend mit einer geringen Beteiligung (z. B. einer Überprüfung) und dem Voranschreiten zu tieferen Verpflichtungen (z. B. einem Referenzaufruf oder einer Fallstudie).

### Technische Überlegungen

- Nehmen Sie Zufriedenheitsumfrageergebnisse (z. B. Net Promoter Score, Kundenzufriedenheitswerte) und Produktverwendungsdaten auf, um einen Advocacy-Readiness-Score für jedes Konto zu erstellen.
- Definieren Sie Eignungskriterien für die Advocacy-Kampagne, die Zufriedenheitsschwellen, Nutzungsmeilensteine und Kontobeschäftigungen kombinieren, um eine verfrühte Kontaktaufnahme zu vermeiden.
- Synchronisieren Sie den Advocacy-Status und den Teilnahmeverlauf wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit die Vertriebs-Teams bei der Interessentenakquise auf die Advocates der Kunden verweisen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um die Kontaktaufnahme zu Interessengruppen während aktiver Support-Eskalationen oder Verlängerungsverhandlungen zu unterbinden.
