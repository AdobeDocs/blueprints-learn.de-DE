---
title: B2B-Anwendungsfälle
description: Erfahren Sie, wie B2B-Unternehmen Adobe Experience Platform verwenden, um die Pipeline zu beschleunigen, die Lead-Qualität zu verbessern und die Kundenexpansion zu fördern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 6073bdc4-e148-455e-aa4e-3d5226d4b5a2
source-git-commit: 0236bd326730ee9a0be621ee0e60ddc3d352410d
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---

# B2B-Anwendungsfälle

Business-to-Business-Unternehmen verwenden Adobe Experience Platform zur Vereinheitlichung von Account- und Personendaten, sodass Marketing- und Vertriebsteams in allen Phasen des Journey-Kaufs koordinierte, relevante Erlebnisse bereitstellen können. Von der Pipeline-Beschleunigung bis zur Kundenerweiterung zeigen diese Anwendungsfälle, wie B2B-Teams komplexe Daten in messbare Geschäftsergebnisse umwandeln.

>[!NOTE]
>
>Blueprints für die B2B-spezifische Architektur, einschließlich kontobasierter Aktivierung und Einkaufsgruppenverwaltung, finden Sie unter [B2B-Aktivierung und Marketing-Blueprints](/help/blueprints/b2b/overview.md).

## Account-Based Marketing Personalization

Personalisieren Sie die Marketing-Kommunikation und den Inhalt für Zielkonten auf der Grundlage des Kontoprofils, des Interaktionsverlaufs und der Kaufsignale. Durch die Ausrichtung der Botschaften an den individuellen Kontexten jedes Kontos können Marketing-Teams das Rauschen durchbrechen und die richtigen Stakeholder mit den richtigen Inhalten interagieren.

### Auswirkung auf den Betrieb

Unternehmen, die Account-basierte Marketing-Personalisierung implementieren, profitieren von einer verbesserten Account-Interaktion, einer stärkeren Pipeline und einem schnelleren Abschluss.

### Implementieren

Verwenden Sie das [B2B-Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)-Muster, um Zielgruppen auf Kontoebene zu erstellen und kanalübergreifend personalisierte Inhalte zu aktivieren. Dieses Muster wurde speziell für Account-basierte Strategien entwickelt und unterstützt sowohl das Targeting auf Konto- als auch auf Personenebene. Dies ist das richtige Muster, wenn das Targeting auf Kontoebene und nicht auf individueller Ebene erfolgen muss - die standardmäßige RT-CDP-Zielgruppenaktivierung unterstützt nicht das Account-basierte Datenmodell, das für ABM-Strategien erforderlich ist.

### Technische Überlegungen

- CRM-Daten integrieren (z. B. [!DNL Salesforce] oder [!DNL Microsoft Dynamics]), um aktuelle Account-Hierarchien, Opportunity-Stadien und Eigentümerzuweisungen beizubehalten.
- Konfigurieren Sie Profilschemata auf Kontoebene, um firmografische Attribute wie Branche, Mitarbeiteranzahl, Umsatzbereich und Technologie-Stack zu erfassen.
- Ordnen Sie Personen-Konto-Beziehungen zu, um sicherzustellen, dass individuelle Interaktionssignale für die Bewertung und Segmentierung auf Kontoebene verwendet werden.
- Stimmen Sie sich mit [!DNL Marketo Engage] ab, um Marketing-Automatisierungskampagnen auf plattformgesteuerte Account-Zielgruppen abzustimmen.


## Lead-Bewertung und -Pflege

Führt automatisch eine Bewertung für Leads anhand von Profildaten und -verhalten durch und leitet dann Leads mit hoher Punktzahl mit personalisierten Pflegekampagnen für andere zu Verkäufen weiter. Dieser Ansatz stellt sicher, dass sich die Vertriebsteams auf die viel versprechendsten Möglichkeiten konzentrieren, während das Marketing die Interessenten in einer früheren Phase weiter entwickelt.

### Auswirkung auf den Betrieb

Unternehmen, die verhaltensorientierte Lead-Bewertung und automatisierte Pflege implementieren, sehen eine verbesserte Lead-zu-Opportunity-Konversion, eine beschleunigte Pipeline-Geschwindigkeit und eine verbesserte Verkaufsproduktivität.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um verzweigende Journey zu entwickeln, die auf Änderungen der Lead-Bewertung und Verhaltens-Trigger reagieren. Dieses Muster unterstützt die bedingte Logik, die zum Routen von Leads zwischen Nurture-Tracks und Workflows zur Verkaufsübergabe erforderlich ist. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf Lead-Score-Änderungen und Verhaltensereignissen erfordert - eine einzelne ausgelöste Nachricht kann die Abhängigkeitslogik zwischen Scoring-Stadien und Routing-Entscheidungen nicht berücksichtigen.

### Technische Überlegungen

- Einrichten einer bidirektionalen CRM-Synchronisation (z. B. [!DNL Salesforce] oder [!DNL Microsoft Dynamics]), damit Lead-Bewertungen und Qualifizierungsstatus zwischen Marketing- und Vertriebssystemen konsistent bleiben.
- Definieren Sie sowohl demografische (Rolle, Unternehmensgröße, Branche) als auch verhaltensbezogene Dimensionen (Inhalts-Downloads, Webinar-Anwesenheit, Produktseitenbesuche) für die Bewertung.
- Koordinieren Sie Lead-Bewertungsmodelle mit [!DNL Marketo Engage], um plattformübergreifend widersprüchliche Bewertungen zu vermeiden.
- Legen Sie Regeln für den Verfall von Bewertungen fest, um sicherzustellen, dass Leads, die nicht geräuschlos sind, im Laufe der Zeit depriorisiert werden.


## Content Personalization für Interessenten

Personalisieren Sie den Inhalt, die Ressourcen und die Angebote der Website basierend auf der Branche, der Rolle, der Unternehmensgröße und dem Interaktionsverlauf des potenziellen Kunden. Wenn Interessenten Inhalte sehen, die für ihre spezifische Situation relevant sind, interagieren sie stärker und durchlaufen die funnel schneller.

### Auswirkung auf den Betrieb

B2B-Organisationen, die Web-Erlebnisse für bekannte Interessenten personalisieren, erzielen eine verbesserte Content-Interaktion, was zu einer stärker qualifizierten Pipeline und kürzeren Verkaufszyklen führt.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um auf der Grundlage einheitlicher Profile potenzieller Kundinnen und Kunden maßgeschneiderte Inhaltserlebnisse bereitzustellen. Dieses Muster nutzt Echtzeit-Profildaten, um für jeden Besucher die relevantesten Ressourcen, Fallstudien und Aktionsaufrufe bereitzustellen. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und Segmentzugehörigkeit und nicht von einem verhaltensbezogenen Affinitätsmodell gesteuert wird - sodass Attribute auf Konto- und individueller Ebene das Erlebnis steuern können.

### Technische Überlegungen

- Implementieren Sie die Identitätsauflösung, damit das anonyme Browsing-Verhalten bekannten Interessenten-Datensätzen entspricht, sobald sie sich authentifizieren oder ein Formular senden.
- Definieren Sie Personalisierungsregeln anhand von Attributen auf Kontoebene (Branche, Segment, Abschlussstufe) sowie Attributen auf individueller Ebene (Rolle, vergangener Inhaltsverbrauch).
- Integration mit Ihrem Content-Management-System, um Hero-Banner, Ressourcenempfehlungen und Aktionsaufrufe dynamisch auszutauschen.
- Stellen Sie sicher, [!DNL Marketo Engage] Webtracking-Daten in das einheitliche Profil eingespeist werden, um ein vollständiges Verhaltensbild zu erhalten.


## Registrierung und Follow-up von Veranstaltungen

Personalisierte Bestätigungen, Erinnerungen und Follow-up für Veranstaltungen basierend auf Ereignistyp und Teilnehmerprofil automatisieren Dadurch werden Interessenten vor, während und nach Ereignissen aktiv gehalten, während das Marketing-Team von der manuellen Koordination befreit wird.

### Auswirkung auf den Betrieb

Automatisierte, personalisierte Workflows für die Veranstaltungskommunikation steigern die Anwesenheitsrate von Veranstaltungen, maximieren den ROI von Veranstaltungsinvestitionen und stärken die Beziehungen mit potenziellen Kunden.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um den gesamten Ereignislebenszyklus von der Registrierung bis hin zur Pflege nach dem Ereignis zu orchestrieren. Dieses Muster unterstützt zeitbasierte Trigger, bedingte Verzweigungen nach Ereignistyp und mehrkanalige Folgesequenzen. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf der Ereignisregistrierung und der Anwesenheit erfordert - zeitbasiertes Messaging allein kann die komplexe Verzweigungslogik zwischen registrierten, teilnehmenden und nicht angezeigten Pfaden nicht verarbeiten.

### Technische Überlegungen

- Registrierungsdaten von Webinar-Plattformen (z. B. [!DNL ON24], [!DNL Zoom Webinar]) und persönlichen Veranstaltungssystemen in das einheitliche Profil integrieren.
- Erfassen Sie Anwesenheit und Interaktionssignale (Sitzungsdauer, gestellte Fragen, Umfrageantworten), um Folgenachrichten zu personalisieren.
- Koordinieren Sie Ereignis-Journey mit [!DNL Marketo Engage] Programmstatus, um systemübergreifend ein konsistentes Reporting zu gewährleisten.
- Entwerfen Sie separate Journey-Verzweigungen für Teilnehmer und Teilnehmer bzw. Teilnehmer, die nicht teilgenommen haben, mit maßgeschneiderten Inhalten für jeden Teilnehmer.


## Konversionskampagnen zu Produktversuchen

Ansprechen Sie Testanwender mit personalisierten Produktempfehlungen, Schulungsressourcen und Angeboten, um die Konvertierung in bezahlte Pläne zu fördern. Durch die Begegnung mit Testbenutzern, wo sie sich in der Produkterkundung befinden, können Teams Reibungen beseitigen und den Weg zum Kauf beschleunigen.

### Auswirkung auf den Betrieb

Unternehmen, die personalisierte Testkonversionskampagnen bereitstellen, profitieren von einer verbesserten Konversion zu Testpreisen, die sich direkt auf den Unternehmensumsatz auswirkt und die Kosten für die Kundenakquise senkt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um zeit- und verhaltensbasierte Konversions-Journey für Testanwender zu erstellen. Dieses Muster unterstützt bedingte Pfade, die auf Produktnutzungs-Meilensteinen basieren, und ermöglicht gezielte Nudges zum richtigen Zeitpunkt. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen, mehrfachen Nachrichtenfluss erfordert, der durch Nutzungsmeilensteine mit bedingter Verzweigung ausgelöst wird - ereignisgesteuertes Messaging kann die prädiktive Timing- und Abhängigkeitslogik, die für die Meilenstein-basierte Pflege erforderlich ist, nicht verarbeiten.

### Technische Überlegungen

- Nehmen Sie die Produktnutzungsmessung (Funktionsübernahme, Anmeldefrequenz, Produkteinführungszeit) auf, um Echtzeit-Testinteraktionsprofile zu erstellen.
- Definieren Sie nutzungsbasierte Meilensteine (z. B. erstes erstelltes Projekt, verwendetes Schlüsselfeature, eingeladene Zusammenarbeit) als Journey-Trigger für zeitnahe Kontaktaufnahme.
- Synchronisieren Sie Teststatus- und Konversionsereignisse wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit die Vertriebsmitarbeiter die Testaktivität vollständig einsehen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage] Nurture-Programmen, um Überschneidungen der Kommunikation während der Testphase zu vermeiden.


## Customer Success und Onboarding

Personalisieren Sie Onboarding-Journey für Kunden mit relevanten Schulungen, Ressourcen und Support, die auf dem erworbenen Produkt und dem Kundenprofil basieren. Effektives Onboarding reduziert die Wertschöpfungszeit und schafft die Grundlage für langfristige Kundenbindung und Wachstum.

### Auswirkung auf den Betrieb

Unternehmen mit personalisierten Onboarding-Programmen profitieren von einer verbesserten Implementierung von Funktionen in den ersten 90 Tagen, was direkt zu höheren Umsätzen bei Kundenbindung und Erweiterung beiträgt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Onboarding-Sequenzen zu orchestrieren, die auf Produkt, Planebene und Kundensegment zugeschnitten sind. Dieses Muster unterstützt einen Milestone-basierten Fortschritt und stellt sicher, dass Kunden in jeder Phase ihres Onboarding die richtige Anleitung erhalten. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenzierten Fluss mit mehreren Nachrichten mit bedingter Weiterentwicklung basierend auf Produktnutzungs-Meilensteinen erfordert - ereignisgesteuertes Messaging kann die komplexe Staging-Logik, die für einen geführten Onboarding-Fortschritt erforderlich ist, nicht berücksichtigen.

### Technische Überlegungen

- Nehmen Sie die Produktnutzungsmetrik auf, um Onboarding-Meilensteine (erste Anmeldung, Erstkonfiguration, erster abgeschlossener Workflow) zu verfolgen, und führen Sie den nächsten Journey-Trigger entsprechend aus.
- Ordnen Sie Kundenprofile der richtigen Onboarding-Spur zu, basierend auf erworbenem Produkt, Planebene und der Anzahl der lizenzierten Benutzer.
- Integrieren Sie Daten der Customer Success-Plattform, um Integritätsbewertungen zu ermitteln und Risikokonten für proaktive Maßnahmen zu kennzeichnen.
- Synchronisieren Sie den Onboarding-Status und die Akzeptanzmetriken wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit Customer Success Manager die Kontaktaufnahme priorisieren können.


## Kampagnen zur Vertragsverlängerung

Proaktive Interaktion mit Kunden, die eine Vertragsverlängerung anstreben, mit personalisierten Angeboten, Nutzungseinblicken und Verlängerungsanreizen. Zeitnahe, datengesteuerte Verlängerungsaktionen reduzieren die Abwanderung und schützen die wiederkehrenden Umsätze.

### Auswirkung auf den Betrieb

Unternehmen, die proaktive, personalisierte Verlängerungskampagnen durchführen, profitieren von höheren Verlängerungsraten, dem Schutz wiederkehrender Umsätze und der Senkung der Kosten für die Rückgewinnung von Kunden.

### Implementieren

Verwenden Sie das [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um das richtige Erneuerungsangebot über den richtigen Kanal zum richtigen Zeitpunkt bereitzustellen. Dieses Muster kombiniert die Journey-Orchestrierung mit Offer Decisioning und ermöglicht dynamische Verlängerungsanreize basierend auf dem Wert und der Nutzung des Kontos. Dies ist das richtige Muster, wenn die Journey die Bereitstellung kanalübergreifend koordinieren muss und die Angebotsauswahl Kontowert- und Nutzungsbeschränkungen erfordert. Die Journey-Orchestrierung allein bietet nicht die Echtzeit-Entscheidungsebene, die erforderlich ist, um Verlängerungsanreize dynamisch abzustimmen.

### Technische Überlegungen

- Das Enddatum des Vertrags, die Verlängerungsbedingungen und den Kontowert zum entsprechenden Vorlaufzeitpunkt (z. B. 90, 60, 30 Tage) von [!DNL Salesforce] oder [!DNL Microsoft Dynamics] auf die Journey der Trigger-Verlängerung abrufen.
- Integrieren Sie Produktnutzungsdaten und Kundengesundheitsbewertungen, um das Erneuerungsrisiko zu bestimmen und die Angebotsstrategie entsprechend anzupassen.
- Verwenden Sie Decisioning, um den optimalen Verlängerungsanreiz (Rabatt, verlängerte Bedingungen, Premium-Upgrade) basierend auf dem Wert der Kontolebensdauer und der Abwanderungswahrscheinlichkeit auszuwählen.
- Koordinieren Sie die Verlängerungsarbeit mit den Customer Success- und Vertriebsteams, um widersprüchliche Nachrichten durch die Zuweisung von [!DNL Marketo Engage]- und CRM-Aufgaben zu vermeiden.


## Upsell- und Erweiterungsmöglichkeiten

Identifizieren Sie Kunden, die für Produkt-Upgrades oder zusätzliche Lizenzen bereit sind, basierend auf Nutzungsmustern, Wachstumsindikatoren und Kundenerfolgsdaten. Proaktive Expansionsmaßnahmen machen aus der Kundendynamik ein Umsatzwachstum.

### Auswirkung auf den Betrieb

Organisationen, die Erweiterungssignale systematisch identifizieren und darauf reagieren, generieren höhere Expansionsumsätze, verbessern die Nettoumsatzbindung und den Kundenlebenszeitwert.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um personalisierte Upsell- und Expansionsangebote auf der Grundlage von Echtzeit-Nutzung und Kontosignalen bereitzustellen. Dieses Muster verwendet die Entscheidungsfindung, um jedes Konto kanalübergreifend mit dem relevantesten Erweiterungsangebot abzugleichen. Dies ist das richtige Muster, wenn die Journey die Bereitstellung kanalübergreifend koordinieren muss und die Angebotsauswahl Eignungsregeln erfordert, die regeln, welche Erweiterungsangebote mit bestimmten Konten übereinstimmen. Die Journey-Orchestrierung allein bietet nicht die Entscheidungsebene, die für den einschränkungsgesteuerten Angebotsabgleich erforderlich ist.

### Technische Überlegungen

- Nehmen Sie die Telemetrie zur Produktnutzung auf, um Erweiterungssignale wie Lizenznutzungsschwellen, Funktionsobergrenzen und wachsende Benutzerzahlen zu erkennen.
- Erstellen Sie Tendenzmodelle auf Kontoebene mit historischen Erweiterungsdaten, Nutzungstrends und firmografischen Attributen.
- Synchronisieren Sie Erweiterungsmöglichkeiten und empfohlene Angebote wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit Vertriebsteams die vom Marketing generierte Pipeline verfolgen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um sicherzustellen, dass Expansion Messaging nicht mit laufendem Support oder Erneuerungskommunikation kollidiert.


## Konkurrenzfähige Ersatzkampagnen

Targeting von potenziellen Kunden durch Verwendung von Produkten von Mitbewerbern mit personalisiertem Messaging, Migrationsangeboten und Vergleichen mit Mitbewerbern. Durch die Behandlung der spezifischen Probleme jedes Mitbewerbers können Marketing-Teams effektiver differenzieren und Switching-Entscheidungen beschleunigen.

### Auswirkung auf den Betrieb

B2B-Organisationen, die zielgerichtete wettbewerbsorientierte Ersatzkampagnen durchführen, erzielen verbesserte wettbewerbsfähige Gewinnraten, gewinnen Marktanteile und verdrängen etablierte Anbieter.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Multi-Touch-Kampagnen im Wettbewerb zu orchestrieren, die auf die spezifischen Wettbewerber- und Interessentenprofile zugeschnitten sind. Dieses Muster unterstützt eine bedingte Verzweigung auf der Grundlage der vom Mitbewerber identifizierten Inhalte und ermöglicht so eine Botschaft, die die individuellen Probleme jedes Wettbewerbsszenarios adressiert. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten mit bedingter Verzweigung basierend auf dem spezifischen Mitbewerber- und Interessentenprofil erfordert - ereignisgesteuertes Messaging kann die Komplexität der mitbewerberspezifischen Verzweigungslogik über mehrere Touchpoints hinweg nicht verarbeiten.

### Technische Überlegungen

- Daten zu Wettbewerbsinformationen (z. B. technische Anbieter, CRM-Mitbewerberfelder) in das einheitliche Profil integrieren, um zu ermitteln, welchen Mitbewerber ein potenzieller Mitbewerber derzeit verwendet.
- Erstellen Sie wettbewerbsspezifische Content-Assets (Migrationshandbücher, Vergleichsblätter, ROI-Rechner) und ordnen Sie sie Journey-Inhaltsblöcken zu.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um Konkurrenzkampagnen für potenzielle Kunden, die sich bereits in aktiven Verkaufszyklen befinden, oder Bestandskunden zu unterbinden.
- Verfolgen Sie die Pipeline zur Verdrängung von Mitbewerbern in [!DNL Salesforce] oder [!DNL Microsoft Dynamics] mit dedizierter Kampagnenzuordnung, um die Effektivität des Programms zu messen.


## Webinar- und Demoplanung

Personalisieren Sie die Einladungen zu Webinaren und die Planung der Demos auf der Grundlage der Interessen, der Branche und des Interaktionsverlaufs des potenziellen Kunden. Relevante, zeitnahe Einladungen steigern die Anwesenheit und generieren aus Live-Interaktionen eine Pipeline mit höherer Qualität.

### Auswirkung auf den Betrieb

Personalisierte Webinar- und Demo-Einladungsprogramme steigern die Anwesenheitsraten von Webinaren und fördern so die qualifizierte Nutzung von Live-Interaktionsmöglichkeiten.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöste Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um personalisierte Einladungen zu senden, wenn Interessenten Interessensignale zeigen, die auf kommende Webinar- oder Demothemen abgestimmt sind. Dieses Muster reagiert in Echtzeit auf verhaltensbezogene Trigger und stellt sicher, dass Einladungen ankommen, wenn das Interesse am größten ist. Dies ist das richtige Muster, wenn der Trigger eine diskrete Kundenaktion ist, die mit der Webinar-Relevanz abgestimmt ist, und die erforderliche Antwort eine einzige, zeitkritische Einladung ist - und keine mehrstufige Sequenz oder ein fortlaufendes Nurture-Programm.

### Technische Überlegungen

- Definieren Sie interessenbasierte Trigger-Ereignisse (z. B. Besuch einer Produktseite, Herunterladen einer zugehörigen Ressource, Interaktion mit einem Konkurrenzvergleich), die mit geplanten Webinar- oder Demothemen im Einklang stehen.
- Integrieren Sie Daten der Webinar-Plattform (z. B. [!DNL ON24], [!DNL Zoom Webinar]), um Registrierungs-, Teilnahme- und Interaktionsmetriken innerhalb des einheitlichen Profils zu verfolgen.
- Synchronisieren Sie Demoanfragen und planen Sie Daten mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], um sicherzustellen, dass die Vertriebsteams rechtzeitig Benachrichtigungen und Kontext erhalten.
- Koordinieren Sie die Einladungskadenz mit [!DNL Marketo Engage] Kommunikationsbeschränkungen, um zu verhindern, dass potenzielle Kunden, die sich für mehrere Ereignisse qualifizieren, übermäßig viele Nachrichten senden.


## Fallstudie und ROI Personalization

Stellen Sie personalisierte Fallstudien, ROI-Rechner und Erfolgsgeschichten bereit, die auf der Branche, der Unternehmensgröße und dem Anwendungsfall des potenziellen Kunden basieren. Wenn Interessenten von Organisationen, die ihren ähnlich sind, Korrekturpunkte erhalten, wächst das Vertrauen schneller und Kaufentscheidungen werden schneller.

### Auswirkung auf den Betrieb

Organisationen, die Korrekturabzugsinhalte personalisieren, profitieren von einer verbesserten Interaktion mit Fallstudien, die zu einem stärkeren Vertrauen in Abschlüsse und schnelleren Abschlussraten führt.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um die relevantesten Fallstudien und ROI-Erkenntnisse dynamisch basierend auf dem Profil jedes potenziellen Kunden darzustellen. Dieses Muster ordnet Besucherattribute einer Inhaltsbibliothek zu und stellt sicher, dass jeder Interessent Testpunkte aus seiner Branche und aus anderen Gruppen erhält. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und Segmentzugehörigkeit und nicht von einem verhaltensbezogenen Affinitätsmodell gesteuert wird, sodass Attribute der Branche und der Unternehmensgröße potenzielle Kunden mit relevanten Korrekturpunkten abgleichen können.

### Technische Überlegungen

- Markieren Sie Fallstudien und ROI-Inhalte mit Metadaten (Branche, Unternehmensgröße, Anwendungsfall, Produkt), um einen dynamischen Abgleich mit Interessentenprofilen zu ermöglichen.
- Implementieren Sie Personalisierungsregeln, die zunächst Branchenabgleich, dann Unternehmensgröße und Anwendungsfall priorisieren, mit Fallback-Inhalten für potenzielle Kunden mit eingeschränkten Profildaten.
- Integrieren Sie Content-Interaktionssignale (Downloads, Zeit auf der Seite, Freigaben) wieder in das einheitliche Profil, um Lead-Bewertung und Verkaufsförderung zu unterstützen.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um personalisierte Korrekturpunktinhalte in die Pflege-E-Mail-Sequenzen und nicht nur in die Erlebnisse vor Ort einzubeziehen.


## Programme zur Kundenunterstützung

Identifizieren und gewinnen Sie zufriedene Kunden für Advocacy-Möglichkeiten wie Referenzen, Fallstudien und Testimonials, die auf Datennutzungs- und Zufriedenheitsdaten basieren. Zufriedene Kunden sind ein leistungsstarker Wachstumsmotor, wenn sie erkannt und eingeladen werden, ihren Erfolg zu teilen.

### Auswirkung auf den Betrieb

Strukturierte Programme zur Kundenunterstützung fördern eine verbesserte Interessensvertretung und erzeugen einen stetigen Strom von Referenzen, Fallstudien und Testimonials, die die Akquise neuer Unternehmen unterstützen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um Advocacy-Identifikations- und Interaktions-Workflows zu erstellen, die auf Zufriedenheits- und Nutzungssignale reagieren. Dieses Muster unterstützt progressive Advocacy-Aufgaben, beginnend mit einer geringen Beteiligung (z. B. einer Überprüfung) und dem Voranschreiten zu tieferen Verpflichtungen (z. B. einem Referenzaufruf oder einer Fallstudie). Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenzierten Fluss mit mehreren Nachrichten mit bedingter Weiterentwicklung basierend auf Zufriedenheits- und Nutzungssignalen erfordert - eine einzelne ausgelöste Nachricht kann die progressive Interaktionslogik nicht verarbeiten, die zum Eskalieren von Advocacy-Anfragen im Laufe der Zeit erforderlich ist.

### Technische Überlegungen

- Nehmen Sie Zufriedenheitsumfrageergebnisse (z. B. Net Promoter Score, Kundenzufriedenheitswerte) und Produktverwendungsdaten auf, um einen Advocacy-Readiness-Score für jedes Konto zu erstellen.
- Definieren Sie Eignungskriterien für die Advocacy-Kampagne, die Zufriedenheitsschwellen, Nutzungsmeilensteine und Kontobeschäftigungen kombinieren, um eine verfrühte Kontaktaufnahme zu vermeiden.
- Synchronisieren Sie den Advocacy-Status und den Teilnahmeverlauf wieder mit [!DNL Salesforce] oder [!DNL Microsoft Dynamics], damit die Vertriebs-Teams bei der Interessentenakquise auf die Advocates der Kunden verweisen können.
- Koordinieren Sie sich mit [!DNL Marketo Engage], um die Kontaktaufnahme zu Interessengruppen während aktiver Support-Eskalationen oder Verlängerungsverhandlungen zu unterbinden.

## B2B-Account-Based Audience Activation

Erstellen Sie Zielgruppen auf Kontoebene, die firmografische Daten, Kaufgruppensignale und Interaktionen auf Personenebene kombinieren, und aktivieren Sie sie dann für LinkedIn, nachfrageseitige Plattformen und CRM-Ziele. Account-basierte Zielgruppenaktivierung ermöglicht es B2B-Unternehmen, ganze Einkaufsorganisationen mit koordinierter digitaler Werbung anstatt einzelner Kontakte anzusprechen und bezahlte Medienausgaben mit den Prioritäten der Account-Pipeline abzustimmen.

### Auswirkung auf den Betrieb

B2B-Organisationen mit Account-basierter Zielgruppenaktivierung sehen einen stärkeren Pipeline-Einfluss von Paid-Media-Programmen. Dies hat besonders große Auswirkungen, wenn Zielgruppensegmente an den Prioritäten des Vertriebsgebiets ausgerichtet und häufig aktualisiert werden, wenn sich die Scores für die Account-Interaktion ändern.

### Implementieren

Verwenden Sie das [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)-Muster, um Segmente auf Kontoebene mithilfe von Konto-Personen-Beziehungen zu erstellen und für B2B-fähige Paid-Media-Ziele zu aktivieren. Dies ist das richtige Muster, wenn die Erstellung von Zielgruppen auf Kontoebene erfolgen muss - wobei Signale von mehreren Kontakten innerhalb einer kaufenden Organisation kombiniert werden - und nicht auf der Ebene einzelner Personen.

### Technische Überlegungen

- Die Konfiguration des B2B-Identitätsdiagramms muss bekannte Personen genau mit ihren Kontoaufzeichnungen verknüpfen. Lücken in den Konto-Personen-Verknüpfungen führen zu einer unvollständigen Aggregation der Kaufgruppensignale.
- Die Segmente der Konto-Zielgruppe sollten entsprechend einem Zeitplan aktualisiert werden, der den Kampagnenflugdaten und der Pipeline-Überprüfungskadenz entspricht. Segmente, die vom aktuellen Pipeline-Status abweichen, reduzieren die Effizienz der Medienausgaben.
- LinkedIn Matched Audiences und ähnliche B2B-Plattformen stimmen auf professionellen E-Mail-Adressen überein, die sich von den im CRM gespeicherten persönlichen E-Mail-Adressen unterscheiden können. Beide E-Mail-Typen sollten in Audience-Payloads enthalten sein.
- Aktivierungs-Zielgruppen sollten Konten in aktiven Deal-Phasen ausschließen, in denen bezahlte Werbung eine unangenehme Überschneidung mit der Reichweite des Direktverkaufs verursachen könnte.


## Einkaufsgruppe Journey Orchestration

Orchestrieren Sie Journey auf Kontoebene, die Mitglieder der Einkaufsgruppe basierend auf ihren Rollen, Interaktionswerten und dem Kontoqualifizierungsstatus pflegen, mit automatisierter Übergabe an den Vertrieb. Durch die Koordinierung der Journey-Logik auf der Ebene der Einkaufsgruppe und nicht auf individueller Ebene wird sichergestellt, dass jeder Stakeholder die seiner Rolle und Entscheidungsstufe entsprechende Botschaft erhält, während die Konsistenz innerhalb des Accounts gewahrt bleibt.

### Auswirkung auf den Betrieb

B2B-Unternehmen, die die Journey-Orchestrierung für eine Einkaufsgruppe verwenden, sehen verbesserte Opportunity-Erstellungsraten von der Marketing-basierten Pipeline und einen schnelleren Fortschritt bis hin zu frühen Abschlussphasen, insbesondere wenn die Verkaufsübergabe automatisch auf der Grundlage messbarer Interaktionsschwellen ausgelöst wird.

### Implementieren

Verwenden Sie das Muster [Kaufen gruppenbasiertes Marketing](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md), um kontoqualifizierte Journey zu erstellen, die Käufergruppenmitglieder nach Rolle segmentieren, Interaktionssignale auf Gruppenebene auswerten und koordinierte Multi-Person-Multi-Touch-Kampagnen mit bedingter Verzweigung basierend auf dem Kontostatus orchestrieren. Dies ist das richtige Muster, wenn die Journey-Logik auf der Ebene der Kontengruppe und nicht auf der Ebene der Einzelperson agieren muss - eine standardmäßige Journey-Orchestrierung auf Personenebene kann die Anforderungen der Gruppenqualifizierung und der personenübergreifenden Koordinierung der B2B-Einkaufsgruppenverwaltung nicht erfüllen.

### Technische Überlegungen

- Definitionen der Einkaufsgruppenmitgliedschaft müssen im B2B-Datenmodell beibehalten werden, indem bekannte Kontakte mit ihren Konten verknüpft und ihnen Rollen wie „Champion“, „Economic Buyer“ oder „Technical Evaluator“ zugewiesen werden.
- Die Bewertung der Kontointeraktion muss Signale mehrerer Personen innerhalb der Einkaufsgruppe aggregieren. Die Interaktion eines einzelnen Kontakts reicht nicht aus, um die Bereitschaft auf Kontoebene zu bestimmen.
- Die Journey-Unterdrückung muss mit den CRM-Opportunity-Stadien synchronisiert werden, um zu verhindern, dass Nachrichten zur Marketing-Automatisierung mit aktiven Verkaufsgesprächen in Konflikt geraten.
- Warnhinweise und Übergabebenachrichtigungen müssen in die CRM- und Vertriebsaktivitätsplattform integriert werden, damit die Mitarbeiter rechtzeitig einen umsetzbaren Kontext erhalten, wenn Konten den Schwellenwert für die Übergabe erreichen.


## Account-Based Marketing (ABM) Personalization

Personalisieren Sie die Marketing-Kommunikation und den Inhalt für Zielkonten auf der Grundlage des Kontoprofils, des Interaktionsverlaufs und der Kaufsignale. Die ABM-Personalisierung geht über das Targeting von Konten hinaus, indem der Nachrichteninhalt und das Web-Erlebnis an die spezifische Branche, Größe und bekannten geschäftlichen Herausforderungen jedes Kontos angepasst werden. So wird eine Relevanz geschaffen, die generische Kampagnenbotschaften nicht erreichen können.

### Auswirkung auf den Betrieb

B2B-Organisationen mit Personalisierung auf Kontoebene melden verbesserte Interaktionsraten bei ausgehenden Kampagnen und höhere Konversionsraten von der Web- zur Pipeline für zielgerichtete Konten. Dies hat besonders starke Ergebnisse, wenn sich die Personalisierung auf Landingpages und Website-Erlebnisse erstreckt, die über bezahlte Medien besucht wurden.

### Implementieren

Verwenden Sie das [B2B-Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)-Muster, um Profile auf Kontoebene für die Personalisierung über Web- und ausgehende Kanäle hinweg zu aktivieren. Dies ist das richtige Muster, wenn die Hauptanforderung das Targeting auf Kontoebene für die Personalisierung und nicht die Journey-Orchestrierung auf Kontaktebene ist - Account-Profildaten bestimmen die Personalisierungsentscheidungen und nicht die individuellen Verhaltenssignale.

### Technische Überlegungen

- Account-Firmographiedaten - Branche, Unternehmensgröße, Geografie, Technologie-Stack - müssen aktuell und konsistent modelliert sein, um eine aussagekräftige Personalisierung von Inhalten über das allgemeine Targeting auf Branchenebene hinaus zu ermöglichen.
- Die Web-Personalisierung für bekannte B2B-Besucher erfordert eine IP-zu-Account-Auflösung oder direkte Authentifizierung. Die IP-basierte Auflösung hat eine geringere Genauigkeit und sollte nicht für hochwertige Account-Entscheidungen verwendet werden.
- Inhalte müssen für jedes Konto-Segment entwickelt werden, das an die Personalisierung gebunden ist. Wenn Sie die Personalisierung aktivieren, ohne dass ausreichende Inhaltsvarianten vorhanden sind, erhalten einige Konten unveränderte Erlebnisse.
- Personalization-Entscheidungen auf Kontoebene sollten mit der aktuellen CRM-Phase und der Vertriebsaktivität übereinstimmen, um zu vermeiden, dass funnel-Awareness-Top-Inhalte an Accounts übermittelt werden, die bereits aktiv sind.
