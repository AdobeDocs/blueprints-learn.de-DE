---
title: Mehrstufige orchestrierte Journey
description: Erfahren Sie, wie Sie ein Profil durch einen verzweigten Multi-Touch-Journey mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen im Laufe der Zeit führen.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '8173'
ht-degree: 1%

---


# Mehrstufige orchestrierte Journey

Dieses Handbuch bietet einen umfassenden Implementierungs-Blueprint für das Erstellen mehrstufiger orchestrierter Journey mit [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Real-Time Customer Data Platform] (RT-CDP). Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verzweigte, Multi-Touch-Kunden-Journey koordinieren müssen, die im Laufe der Zeit mehrere Nachrichten senden.

Es enthält alle praktikablen Implementierungsoptionen, Entscheidungsüberlegungen an jedem Konfigurationspunkt und Links zu [!DNL Adobe Experience League] Dokumentation. Verwenden Sie dieses Handbuch, um Ihre mehrstufige Journey-Implementierung zu planen, zu konfigurieren und zu validieren.

## Anwendungsfall - Übersicht

Mehrstufige orchestrierte Journey befassen sich mit Geschäftsszenarien, in denen eine einzige Nachricht nicht ausreicht, um das gewünschte Kundenergebnis zu erzielen. Anstelle eines einmaligen Versands führt der Journey jedes Profil durch eine Sequenz von Touchpoints - E-Mails, SMS-Nachrichten, Push-Benachrichtigungen oder In-App-Nachrichten - im Abstand von Tagen oder Wochen, mit einer Verzweigungslogik, die den Pfad basierend auf Profilattributen, Verhaltenssignalen oder Ereignisdaten anpasst.

Diese Journey sind die komplexesten Kampagnenmuster in AJO. Sie kombinieren zielgruppen- oder ereignisbasierte Eingabe mit einer Arbeitsfläche aus Aktionsknoten (Nachrichten), Bedingungsknoten (Verzweigungslogik), Warteknoten (Zeitverzögerungen) und Beendigungskriterien (Konversionsereignisse oder Zeitüberschreitungen). Jedes Profil durchläuft die Journey unabhängig in seinem eigenen Tempo und erhält bei jedem Schritt kontextbezogene Inhalte.

Dieses Muster fasst die einfacheren Muster zusammen - Aktivierung ausgehender Batch-Nachrichten für Kampagnen mit einem Versand und ereignisausgelöstes Messaging für Antworten mit einem Ereignis. Verwenden Sie dieses Muster, wenn der Anwendungsfall die Pflege eines Profils durch mehrere Interaktionen im Laufe der Zeit erfordert.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Verbesserung der Kundenbindung

Halten Sie bestehende Kundinnen und Kunden durch wertorientierte Erlebnisse und kontinuierliche Pflege von Beziehungen in Kontakt und erneuern Sie diese.

**KPIs:**, Kundenlebenszeitwert, Interaktion

[Weitere Informationen zur Verbesserung der Kundenbindung](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Verbessern des Kunden-Onboarding

Verkürzen Sie die Amortisierungszeit für neue Kunden mit optimierten, personalisierten Willkommens- und Aktivierungs-Journey.

**KPIs:** Interaktion, Kundenbindung, Konversionsraten

[Weitere Informationen zur Verbesserung des Onboarding von Kunden](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Erneute Interaktion mit inaktiven Kunden

Gewinnen Sie inaktive oder abgelaufene Kunden mit zielgerichteten Reaktivierungskampagnen zurück, die auf Verhaltenssignalen basieren.

**KPIs:** Interaktion, Kundenbindung, Konversionsraten

### Wiederherstellen von Transaktionsabbrüchen und Journey

Erneutes Ansprechen von Benutzern, die während des Kaufs, der Bewerbung oder der Registrierung abgebrochen sind, durch zeitnahe, personalisierte Folgemaßnahmen.

**KPIs:** Konversionsraten, inkrementeller Umsatz, Interaktion

[Erfahren Sie mehr über die Wiederherstellung von Transaktionsabbrüchen und Journey](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen gängige Anwendungen des mehrstufigen orchestrierten Journey-Musters.

- **Onboarding-Serie** - Willkommens-E-Mail, gefolgt von Funktionsschulung und einer Aktivierungsaufforderung in den ersten 14 Tagen nach der Registrierung
- **Drip-Kampagne zur erneuten Interaktion** - eine Erinnerungs-E-Mail, dann ein Incentive-Angebot und schließlich eine letzte Benachrichtigung für abgelaufene Kundinnen und Kunden über einen Zeitraum von drei Wochen
- **Meilenstein-Journey zum Treueprogramm** - Benachrichtigung zur Aktualisierung der Stufe, gefolgt von einem Exklusivangebot und einer Verlängerungserinnerung zum bevorstehenden Mitgliedschaftsjubiläum
- **Win-Back-Sequenz** - E-Mail „Wir vermissen Sie“, dann ein Rabattangebot per E-Mail, dann eine abschließende SMS-Erinnerung für abgelaufene Käufer
- **Journey zur Produktakzeptanz** - Testwillkommen, Tipps zur Nutzung und eine Upgrade-Eingabeaufforderung im Verlauf des Testzeitraums
- **Sequenz der Abonnementverlängerung** - 30-Tage-Benachrichtigung, 7-Tage-Erinnerung, dann eine Nachricht zum Ablauf des Tages für bevorstehende Abonnementverlängerungen
- **Pflege nach dem Kauf** - Dankeschön-E-Mail, Benutzerhandbuch, Crosssell-Empfehlung und eine Überprüfungsanfrage über 30 Tage nach dem Kauf

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität Ihrer mehrstufigen orchestrierten Journey-Implementierung zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die das vollständige Journey ohne vorzeitiges Beenden abschließen | Journey-Bericht: Beendet (abgeschlossen)/Eingetreten |
| Schrittkonversionsrate | Prozentsatz der Profile, die von einem Schritt zum nächsten wechseln | Metriken pro Knoten im Journey-Bericht |
| Kanalinteraktionsrate | Öffnungsraten, Clickthrough-Raten und Reaktionsraten an jedem Touchpoint | Versand- und Interaktionsmetriken pro Nachricht |
| Konversionsrate der Ausstiegskriterien | Prozentualer Anteil der Profile, die vor dem Journey-Timeout den Trigger des Beendigungsereignisses (z. B. Kauf, Anmeldung) vornehmen | Ausstiegskriterien Trefferanzahl / Gesamtzahl eingegeben |
| Zeit bis zur Konversion | Durchschnittliche Dauer vom Journey-Eintritts- zum Ausstiegskriterienereignis | Journey Analytics: Zeitstempel des Eintrags zum Konversionsereignis-Zeitstempel |
| Journey-Abfallrate | Prozentsatz der Profile, die bei jedem Schritt nicht mehr interagieren (Fallout-Analyse) | CJA Fallout-Visualisierung über Journey-Schritte hinweg |
| Bindungsgrad/Rückgewinnungsrate | Prozentsatz der Zielgruppenprofile, die zum aktiven Status zurückkehren | Verhaltensanalyse nach dem Journey in CJA |

## Anwendungsfallmuster

**Mehrstufige orchestrierte Journey**

Führen Sie ein Profil durch einen verzweigenden Multi-Touch-Journey mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen im Laufe der Zeit.

**Funktionskette:** Zielgruppenauswertung > Journey-Ausführung (mehrere Knoten) > Bedingungsverzweigung > Nachrichtenversand (xN) > Beendigungskriterien > Berichte

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Adobe Journey Optimizer](AJO)** - Journey-Orchestrierungs-Engine, Nachrichtenbearbeitung, Kanalkonfiguration, Inhaltsexperiment, Häufigkeit und Konfliktmanagement sowie Reporting
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** - Zielgruppenbewertung und -definition für Journey-Einstiegs-Zielgruppen, Profildaten für die Personalisierung und Bedingungsverzweigung
- **[!DNL Adobe Experience Platform](AEP)** - Profilspeicher, Identity Service, Ereignisdatenaufnahme und grundlegende Dateninfrastruktur

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit Berechtigungen zum Erstellen und Veröffentlichen von Journey. Kanaloberflächen für alle auf der Journey verwendeten Kanäle müssen konfiguriert werden. Benutzende müssen über die entsprechenden Rollen (Marketing-Experten, Journey-Manager) mit Journey- und Kampagnenberechtigungen verfügen. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | XDM-Profilschema mit Attributen, die für die Bedingungsverzweigung und Personalisierung über mehrere Nachrichten hinweg verwendet werden (z. B. Treuestufe, Produktzweck, Interaktionswert). Erlebnisereignis-Schemata für Konversionsereignisse, die die Ausstiegskriterien und die Auswertung von Bedingungen steuern (z. B. Kaufereignisse, Formularübermittlungen). | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Ereignis-Streaming muss aktiv sein, wenn die Beendigungskriterien oder -bedingungen von Echtzeit-Ereignissen abhängen (z. B. Kaufereignis zum Beenden des Journey). Batch-Aufnahme für Profilattribute, die in der Verzweigung verwendet werden. Web SDK oder Server-seitige API für die Erfassung verhaltensbezogener Ereignisse. | [Streaming-Aufnahme - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview), [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identitäts- und Profilkonfiguration | Angenommen an Ort und Stelle | Profile müssen über alle in der Journey verwendeten Kanäle (E-Mail, SMS, Push) aufgelöst werden können. Geräteübergreifende Identitäten müssen konfiguriert werden, wenn die Journey Web- und Mobile-Touchpoints umfasst. Die Zusammenführungsrichtlinie muss für die Sandbox konfiguriert werden. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Einstiegszielgruppe muss für zielgruppenlesbare Journey definiert werden. Segmente können auch in Bedingungsknoten für Verzweigungen verwendet werden. Die Auswertungsmethode (Batch oder Streaming) muss den Journey-Eingabeanforderungen entsprechen. | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie Interaktionswerte, Tage seit der letzten Aktivität oder der Lebenszeitkaufwert verbessern die Logik der Bedingungsverzweigung und ermöglichen intelligentere Journey-Pfadentscheidungen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Die Aufbewahrung von Journey-Ereignisdaten sollte mit Datensatz-Ablaufrichtlinien konfiguriert werden, um den Speicher zu verwalten und die Vorschriften zur Datenaufbewahrung einzuhalten. Durch die Durchsetzung des Einverständnisses wird sichergestellt, dass nur angemeldete Profile Nachrichten an jedem Kanal-Touchpoint erhalten. | [Erweiterte Übersicht über das Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen stellen eine konforme Personalisierung über mehrere Nachrichten-Touchpoints hinweg sicher. Dies ist besonders wichtig, wenn Journey personenbezogene Daten oder vertrauliche Daten für die kanalübergreifende Personalisierung verwenden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Warnhinweise zur Journey-Ausführungsüberwachung bei Verarbeitungsfehlern, Engpässen bei der Profileingabe und Versandproblemen. Wesentlich für Produktions-Journey, bei denen Verzögerungen oder Ausfälle das Kundenerlebnis beeinträchtigen. | [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | CJA funnel und Fallout-Analysen auf der gesamten Journey bieten eine tiefere insight als native AJO-Berichte allein. Ermöglicht die schrittweise Konversionsanalyse, den Kohortenvergleich und die Journey-Optimierung. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kanalkonfiguration | Phase 1: Kanaleinrichtung | Kanaloberflächen (E-Mail, SMS, Push) für jeden Messaging-Touchpoint auf der Journey konfigurieren |
| Verfassen von Nachrichten | Phase 2: Erstellung des Nachrichteninhalts | Verfassen Sie Nachrichteninhalte mit Personalisierung, dynamischen Inhalten und Vorlagen für jeden Journey-Aktionsknoten |
| Journey Orchestration | Phase 3: Journey-Design und -Aktivierung | Entwerfen der mehrstufigen Journey-Arbeitsfläche mit Einstiegs-, Aktions-, Bedingungs-, Warte- und Ausstiegsknoten; Testen und Veröffentlichen |
| Häufigkeits- und Geschäftsregeln | Phase 4: Governance und Optimierung | Konfigurieren Sie Häufigkeitsbegrenzungen, um Übernachrichten über Journey-Touchpoints und andere gleichzeitige Kampagnen hinweg zu verhindern. |
| Konflikt- und Prioritätenmanagement | Phase 4: Governance und Optimierung | Prioritätswerte zuweisen und Konflikterkennung für Journey konfigurieren, die mit anderen aktiven Kommunikationen konkurrieren |
| Inhaltsexperiment | Phase 4: Governance und Optimierung | Führen Sie A/B-Tests für Nachrichteninhalte innerhalb von Journey-Aktionsknoten durch, um die Leistung zu optimieren |
| Reporting und Leistungsanalyse | Phase 5: Reporting und Überwachung | Überwachen der Journey-Ausführung, der Bereitstellungsmetriken pro Schritt und der Interaktionsleistung |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 1: Kanaleinrichtung (Voraussetzung) | Definieren und Auswerten der Einstiegszielgruppe für von der Zielgruppe gelesene Journey; Definieren von Bedingungszielgruppen für Verzweigungen |
| Durchsetzung von Einverständnis und Governance | Phase 4: Governance und Optimierung | Erzwingen von Einverständnisvoreinstellungen und Datennutzungsrichtlinien für Journey-Nachrichtenaktionen |

## Voraussetzungen

Führen Sie die folgenden Voraussetzungen aus, bevor Sie mit der Implementierung beginnen.

- [ ] AJO-Sandbox verfügt über Berechtigungen zum Erstellen und Veröffentlichen von Journey
- [ ] Mindestens eine Kanaloberfläche (E-Mail, SMS oder Push) ist konfiguriert und aktiv
- [ ] Profilschema enthält Attribute, die für die Bedingungsverzweigung und Personalisierung benötigt werden
- [ ] Erlebnisereignis-Schema ist für Konversionsereignisse konfiguriert, die in Beendigungskriterien verwendet werden
- [ ] Ereignis-Streaming ist für Echtzeit-Ereignisse aktiv, die in Abbruchkriterien oder ereignisgesteuerten Eintritten verwendet werden
- [ ] Identity-Namespaces und Zusammenführungsrichtlinien sind für die kanalübergreifende Profilauflösung konfiguriert
- [ ] Content-Assets (Bilder, Kopien, CTAs) werden für jeden Nachrichten-Touchpoint vorbereitet.
- [ ] Eintrags-Zielgruppe wird definiert und ausgewertet (für Journey mit Zielgruppenlesen)
- [ ] Das Ereignisauslösungsschema ist konfiguriert (für ereignisgesteuerte Journey)
- [ ] Testprofile sind für die Validierung des Journey-Testmodus verfügbar
- [ ] Unterdrückungsliste wird für alle verwendeten Kanäle überprüft und auf dem neuesten Stand gehalten

## Implementierungsoptionen

Überprüfen Sie die folgenden Optionen, um den besten Ansatz für Ihre mehrstufige orchestrierte Journey zu ermitteln.

### Option A: Vom Publikum gelesenes orchestriertes Journey

**Am besten geeignet für:** Zeitbasierte Pflegesequenzen, bei denen eine bekannte Zielgruppe die Journey betritt und über geplante Touchpoints fortschreitet - Onboarding-Serien, Erneuerungssequenzen, Rückgewinnungstrips, Loyalitäts-Milestone-Journey.

**Funktionsweise:**

Eine Zielgruppe wird beim Journey-Eintrag gelesen, entweder als einmaliges Lesen oder in einem wiederkehrenden Zeitplan. Alle qualifizierten Profile gelangen gleichzeitig in die Journey und durchlaufen die Arbeitsfläche in ihrem eigenen Tempo, das von Wartezeiten und Bedingungsauswertungen bestimmt wird. Der Pfad jedes Profils durch die Journey ist unabhängig. Einige nehmen möglicherweise die Verzweigung „Interagiert“, während andere die Verzweigung „Nicht Interagiert“ basierend auf ihrem Verhalten oder ihren Attributen annehmen.

Die Zielgruppe wird zum Zeitpunkt der Ausführung der Aktivität „Zielgruppe lesen“ ausgewertet. Bei wiederkehrenden Journey wird die Zielgruppe bei jeder Wiederholung neu ausgewertet, und neue qualifizierte Profile gelangen auf die Journey, während sich bereits auf der Journey befindliche Profile weiter im Pfad befinden. Dieser Ansatz bietet eine vorhersehbare Einstiegszeit und eignet sich gut für geplante Lebenszyklusprogramme.

**Wichtige Aspekte:**

- Zielgruppe muss vor dem Journey der Aktivierung definiert und ausgewertet werden
- Durch das wiederkehrende Lesen können neue Kriterien in jeden Zyklus eingegeben werden.
- Profile auf der Journey werden nicht erneut gelesen; bei nachfolgenden Lesevorgängen werden nur neue Kriterien eingegeben.
- Warteschritte haben eine Mindestdauer von 1 Stunde für Journey, die von der Zielgruppe gelesen werden

**Vorteile:**

- Vorhersehbare Einstiegszeiten, die an den Geschäftsplänen ausgerichtet sind
- Unterstützt große Zielgruppenvolumen (bis zu 20.000 Profile pro Sekunde, Standardeinschränkung)
- Einfach zu testen und zu überwachen mit bekannten Zielgruppen
- Kann für wiederkehrenden Eintrag geplant werden (täglich, wöchentlich, monatlich)

**Einschränkungen:**

- Die Eingabe erfolgt stapelbasiert, nicht in Echtzeit - Profile werden zum geplanten Lesezeitpunkt eingegeben, nicht wenn sie sich qualifizieren
- Nicht geeignet für verhaltensgesteuerte Sequenzen, die eine sofortige Reaktion erfordern
- Zielgruppenänderungen zwischen Lesevorgängen werden für Profile, die sich bereits auf der Journey befinden, nicht übernommen

**Experience League:**

- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option B: Ereignisgesteuerte orchestrierte Journey

**Am besten geeignet für:** Verhaltensgesteuerte Sequenzen, bei denen ein Echtzeitereignis die Journey startet - Warenkorbabbruch, Eskalation nach dem Kauf, Pflege, durch einen Meilenstein ausgelöste Treue-Journey, Testaktivierungssequenzen.

**Funktionsweise:**

Ein unitäres Ereignis (z. B. ein Kauf, ein Warenkorbabbruch, eine Formularübermittlung oder eine App-Installation), bei dem Trigger in Echtzeit einen Journey-Eintrag für einzelne Profile erstellen. Wenn das Ereignis eingeht, tritt das Profil in den Journey ein und durchläuft dann die Sequenz von Touchpoints mit Bedingungen, Wartezeiten und Verzweigungen. Dieser Ansatz kombiniert die Unmittelbarkeit von ereignisgesteuertem Messaging mit der mehrstufigen Orchestrierung einer vollständigen Journey.

Das auslösende Ereignis muss als Journey-Ereignis konfiguriert werden, wobei sein Schema und seine Bedingungen definiert sind. Die Journey überwacht kontinuierlich das Ereignis und tritt bei Eintreffen der Ereignisse nacheinander in Profile ein. Nachfolgende Journey-Knoten können die Antwort des Profils auswerten, um zu bestimmen, welcher Verzweigung folgen soll.

**Wichtige Aspekte:**

- Echtzeit-Ereignis-Streaming muss aktiv sein
- Ereignisschema und -bedingungen müssen präzise konfiguriert werden, um falsche Trigger zu vermeiden
- Wiedereintrittsregeln sind wichtig - Legen Sie fest, ob ein Profil erneut eintreten kann, wenn das Ereignis erneut ausgelöst wird.
- Unterstützt bis zu 5.000 Ereignisse pro Sekunde pro Sandbox

**Vorteile:**

- Echtzeit-Einstieg basierend auf Kundenverhalten - stark kontextuell
- Jedes Profil tritt unabhängig ein, wenn das Ereignis eintritt, nicht nach einem Zeitplan
- Natürliche Eignung für verhaltensbezogene Antwortsequenzen (Warenkorbabbruch, nach dem Kauf)
- Kann nach der Eingabe mit Profildaten für eine personalisierte Verzweigung kombiniert werden

**Einschränkungen:**

- Erfordert die Einrichtung einer Infrastruktur für Streaming-Ereignisse
- Höhere Komplexität bei der Konfiguration und beim Testen von Ereignisschemata
- Jedes Ereignis tritt in ein Profil ein — nicht für die Massenaktivierung von Zielgruppen geeignet
- Zum Debuggen müssen einzelne Profil-Journey verfolgt werden

**Experience League:**

- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### Option C: Mehrkanal-orchestrierte Journey

**Am besten geeignet für:** Kanalübergreifende Sequenzen, die an jedem Touchpoint unterschiedliche Kanäle verwenden - E-Mail, dann SMS, dann Push-Eskalation oder E-Mail plus ergänzendes In-App-Messaging. Kann entweder einen Eintrag vom Typ „Zielgruppe gelesen“ oder „Ereignis ausgelöst“ verwenden.

**Funktionsweise:**

Diese Option erweitert Option A oder Option B durch Einbeziehung mehrerer Nachrichtenkanäle auf derselben Journey. Jeder Aktionsknoten auf der Journey kann einen anderen Kanal ansprechen (E-Mail, SMS, Push, In-App oder Web), wofür jeweils eine separate Kanaloberfläche erforderlich ist. Der Journey-Designer wählt in jedem Schritt den entsprechenden Kanal aus und ermöglicht Eskalationsmuster (z. B. zuerst E-Mail, dann SMS, wenn keine Interaktion stattfindet) oder komplementäre Muster (z. B. E-Mail mit In-App-Verstärkung).

Cross-Channel-Journey benötigen Kanaloberflächen für jeden verwendeten Kanal und müssen kanalspezifische Personalisierung, Zeichenbeschränkungen und Opt-in-Anforderungen berücksichtigen. Bedingungsknoten können die Interaktion mit früheren Nachrichten (z. B. „Geöffnete E-Mails?„) überprüfen. als Verzweigungsbedingung), um den nächsten Kanal zu bestimmen.

**Wichtige Aspekte:**

- Erfordert aktive Kanaloberflächen für jeden auf der Journey verwendeten Kanal
- Jeder Kanal verfügt über verschiedene Personalisierungsfunktionen und Inhaltsbeschränkungen
- Das Einverständnis muss pro Kanal verifiziert werden - ein Profil kann für E-Mail, aber nicht für SMS angemeldet werden
- Kanalspezifische Frequenzlimitierungen sollten so konfiguriert werden, dass Übermeldungen kanalübergreifend verhindert werden

**Vorteile:**

- Maximiert die Reichweite, indem Profile über ihre bevorzugten Kanäle hinweg einbezogen werden
- Aktiviert Eskalationsstrategien für nicht-responsive Profile
- Unterstützt komplementäres Messaging über verschiedene Kanäle hinweg zur Verstärkung
- Anspruchsvollstes Kundenerlebnis möglich

**Einschränkungen:**

- Höchste Implementierungskomplexität - Erfordert Konfiguration für jeden Kanal
- Inhalte müssen für jeden Kanal an jedem Touchpoint erstellt werden
- Die Einverständnis- und Frequenzverwaltung wird kanalübergreifend komplexer
- Tests erfordern Validierung über alle Kanaloberflächen hinweg.

**Experience League:**

- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: Audience-Read | Option B: Ereignisausgelöst | Option C: Multi-Channel |
| --- | --- | --- | --- |
| Am besten geeignet für | Geplante Lebenszyklusprogramme, Nurture-Reihe | Verhaltensmäßige Reaktionssequenzen, Warenkorbabbruch | Kanalübergreifende Eskalation, komplementäre Messaging |
| Timing beim Eintritt | Geplant (Batch) | Echtzeit (ereignisgesteuert) | Entweder geplant oder in Echtzeit |
| Komplexität | Mittel | Medium-Hoch | Hoch |
| Eintrittsvolumen | Bis zu 20.000 Profile/s | Bis zu 5.000 Ereignisse/Sek | Gleich wie zugrunde liegende Eingabemethode |
| Kanalbereich | Einzel- oder Mehrfachkanäle | Einzel- oder Mehrfachkanäle | Mehrere Kanäle erforderlich |
| Erfordert | Definierte Zielgruppe, Auswertungszeitplan | Infrastruktur für Streaming-Ereignisse | Kanaloberflächen für jeden Kanal |
| Echtzeit-Reaktion | Nein — Chargeneingabe | Ja — unmittelbar nach Ereignis | Hängt von Eingabemethode ab |

### Wählen der richtigen Option

Verwenden Sie den folgenden Entscheidungsfluss, um den richtigen Implementierungsansatz auszuwählen:

1. **Wird das Journey durch ein Kundenverhalten oder ein Kundenereignis initiiert?** Wenn ja, wählen Sie **Option B** (ereignisausgelöst) aus. Wenn das Journey von einem geplanten Audience-Lesevorgang initiiert wird, wählen Sie **Option A** (Audience-Read) aus.

2. **Verwendet die Journey mehrere Nachrichtenkanäle (z. B. E-Mail UND SMS)?** Falls ja, wenden Sie **Option C** (Multi-Channel) zusätzlich zu Ihrer Eingabemethode an (A oder B). Wenn die Journey durchgehend einen einzigen Kanal verwendet, ist Option A oder B ausreichend.

3. **Müssen Sie je nach Interaktion an einen anderen Kanal eskalieren?** Wenn ja, wählen Sie **Option C** mit Bedingungsknoten, die die Interaktion mit vorherigen Nachrichten überprüfen und auf alternative Kanäle verzweigen.

4. **Ist die Zielgruppe im Voraus bekannt und wird sie nach einem Zeitplan verarbeitet?** Wenn ja, wählen Sie **Option A**. Wenn Profile die Journey in dem Moment eingeben sollen, in dem sie eine Aktion ausführen, wählen Sie **Option B**.

## Implementierungsphasen

In den folgenden Phasen wird die End-to-End-Implementierung einer mehrstufigen orchestrierten Journey erläutert.

### Phase 1: Einrichten von Kanälen und Vorbereiten von Zielgruppen

**Anwendungsfunktionen:** AJO: Kanalkonfiguration, RT-CDP: Zielgruppenbewertung

Vor der Erstellung der Journey müssen alle Kanaloberflächen aktiviert und die Einstiegszielgruppe (für Option A) definiert und ausgewertet werden. In dieser Phase wird sichergestellt, dass die Infrastruktur für den Nachrichtenversand bereit ist.

#### Kanaltyp für jeden Touchpoint festlegen

Welche Messaging-Kanäle verwendet die Journey an jedem Touchpoint?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur E-Mail | Journey kommuniziert ausschließlich per E-Mail (Onboarding, Pflege) | Einfache Einrichtung; erfordert E-Mail-Subdomain und IP-Pool; abhängig von der Platzierung im Posteingang |
| Nur SMS | Zeitkritische Warnhinweise, Terminerinnerungen | Erfordert SMS-Provider-Anmeldedaten (Sinch, Twilio, Infobip); höhere Kosten pro Nachricht; strengere Opt-out-Regeln |
| Nur Push | In-App-Interaktionssequenzen für mobile Benutzer | Erfordert APNs/FCM-Anmeldeinformationen; Benutzer müssen die App installiert haben |
| Mehrkanal | Eskalation oder ergänzende Messaging über verschiedene Kanäle hinweg | Erfordert Kanaloberfläche pro Kanal; komplexeste, aber höchste Reichweite |

#### Festlegen der Methode zur Zielgruppenauswertung (Option A)

Wie schnell müssen sich Profile für die Einstiegszielgruppe qualifizieren?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch-Auswertung | Zielgruppe wird nach einem Zeitplan gelesen (täglich, wöchentlich); kein Echtzeit-Eintrag erforderlich | Einfaches Setup; Zielgruppe vor dem Lesen des Journey evaluiert; unterstützt komplexe Segmentregeln |
| Streaming-Auswertung | Profile sollten sich nahezu in Echtzeit qualifizieren, wenn sich Attribute ändern | Segmentregelausdruck muss streaming-fähig sein; Qualifizierung nahezu in Echtzeit |

#### Methode zur Zuweisung von Subdomains festlegen (E-Mail-Kanal)

Wie sollte die Subdomain für den E-Mail-Versand an Adobe delegiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Vollständige Delegierung | Adobe verwaltet DNS-Einträge; einfachste Einrichtung | Schnellste Konfiguration; Adobe verarbeitet SPF, DKIM, DMARC |
| CNAME-Delegierung | Organisation behält DNS-Kontrolle | Erfordert die Beteiligung des DNS-Administrators; CNAME-Einträge müssen konfiguriert werden |

#### Navigation in der Benutzeroberfläche

- Kanaloberflächen: Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen
- Subdomains: Administration > Kanäle > Subdomains
- SMS-Konfiguration: Administration > Kanäle > SMS-Konfiguration
- Push-Konfiguration: Administration > Kanäle > Einstellungen für Push-Benachrichtigungen
- Zielgruppen: Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

#### Wichtige Konfigurationsdetails

- IP-Pool-Aufwärmstatus für E-Mails überprüfen - neue IP-Pools erfordern einen schrittweisen Aufwärmplan über 2-4 Wochen
- Konfigurieren Sie für SMS die Provider-Anmeldeinformationen und überprüfen Sie die Registrierung der Absendernummer
- Laden Sie für Push-Benachrichtigungen APNs-Zertifikate und FCM-Serverschlüssel hoch
- Definieren der Einstiegszielgruppe mit Segment Builder mit Segmentregeln, die die Zielpopulation abdecken
- Unterdrückungsregeln in die Zielgruppendefinition einschließen (kürzlich konvertierte, global abgemeldete ausschließen)

#### Wo die Optionen auseinander gehen

**Für Option A (audience-read):**
Definieren und Auswerten der Einstiegszielgruppe. Bestätigen Sie, dass die Zielgruppe eine Population ungleich null aufweist. Stellen Sie fest, ob die Journey einen einmaligen Lesevorgang für die Zielgruppe oder einen wiederkehrenden Lesezeitplan verwendet.

**Für Option B (ereignisausgelöst):**
Überprüfen Sie, ob das auslösende Ereignisschema konfiguriert ist und ob Ereignisse an die Plattform gestreamt werden. Es ist keine vordefinierte Zielgruppe erforderlich. Profile werden beim Empfang des Ereignisses einzeln eingegeben.

**Für Option C (Mehrkanal):**
Konfigurieren Sie Kanaloberflächen für jeden auf der Journey verwendeten Kanal (E-Mail, SMS, Push, In-App). Überprüfen Sie den Einverständnisstatus der Zielpopulation pro Kanal.

#### Dokumentation zu Experience League

- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### Phase 2: Nachrichteninhalt erstellen

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung

Verfassen Sie den Nachrichteninhalt für jeden Touchpoint auf der Journey. Jede Nachricht kann unterschiedliche Inhalte, Personalisierungstiefe und Kanäle aufweisen. In dieser Phase werden alle lieferbaren Inhalte erstellt, auf die Journey-Aktionsknoten verweisen.

#### Festlegen eines Inhaltsansatzes

Soll jede Nachricht von einer Vorlage ausgehen, von Grund auf neu entworfen werden oder sollte HTML importiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Vorhandene Inhaltsvorlage | Markenkonsistente Nachrichten mit etablierten Layouts | Schnellste; Sicherstellung der Markenkonformität; Vorlage muss vorhanden sein und mit Kanaltyp übereinstimmen |
| Von Grund auf gestalten | Eindeutige, benutzerdefinierte Layouts für jeden Touchpoint | Am flexibelsten, längere Erstellungszeit, Drag-and-Drop mit E-Mail Designer |
| HTML importieren | Vorkonfigurierte HTML aus externen Design-Tools | Erfordert eine saubere HTML. Möglicherweise muss die Reaktionszeit angepasst werden |

#### Festlegen der Personalisierungstiefe

Wie viel Personalisierung sollte jede Nachricht enthalten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Einfache Token-Einfügung | Vorname, Stadt, einfache Profilattribute | Geringe Komplexität; verwendet Handlebars-Syntax mit XDM-Pfaden |
| Bedingte Inhaltsbausteine | Unterschiedlicher Inhalt wird basierend auf Segment oder Attribut angezeigt | Medium - Komplexität; erfordert dynamische Inhaltsregeln |
| Journey-kontextuelle Personalisierung | Der Inhalt variiert je nach Journey-Pfad und vorherigen Interaktionen | Höhere Komplexität; nutzt Journey-Kontextvariablen und Ereignisdaten |

#### Entscheidung über Fragmentstrategie

Sollten freigegebene Inhaltsblöcke (Kopfzeilen, Fußzeilen, Rechtstext) als wiederverwendbare Fragmente erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Wiederverwendbare Fragmente | Mehrere Nachrichten haben gemeinsame Elemente; Markenkonsistenz ist erforderlich | Änderungen werden auf alle Nachrichten übertragen, die das Fragment verwenden. Es können maximal 30 Fragmente pro Nachricht verwendet werden. |
| Inline-Inhalt | Einmalige Nachrichten mit eindeutigem Layout | Schnellere Bereitstellung von Inhalten für den einmaligen Gebrauch, kein Vorteil durch eine konsistente Nachrichtenübermittlung |

#### Navigation in der Benutzeroberfläche

- Content-Management > Inhaltsvorlagen > Durchsuchen
- E-Mail an Designer senden (innerhalb von Campaign oder Journey-Aktion)
- Content-Management > Fragmente > Fragment erstellen

#### Wichtige Konfigurationsdetails

- Inhalt für JEDE Nachrichtenaktion auf der Journey erstellen - Für eine 4-stufige Journey sind möglicherweise 4 separate Nachrichtendesigns erforderlich
- Verwenden von Personalisierungsausdrücken, die auf XDM-Profilpfade verweisen (z. B. `{{profile.person.name.firstName}}`)
- Konfigurieren von dynamischen Inhaltsblöcken für segmentspezifische Varianten
- Vorschau jeder Nachricht mit Testprofilen zur Überprüfung des Personalisierungs-Renderings
- Durchführen eines Testversands an interne Stakeholder zur Inhaltsüberprüfung
- Beachten Sie für SMS die Zeichenbeschränkungen (160 Zeichen für die Standard-GSM-Kodierung).
- Konfigurieren Sie für Push Titel, Textkörper, Bild und Deep-Link-/URL-Aktion

#### Dokumentation zu Experience League

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Erstellen einer SMS-Nachricht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Gestalten einer Push-Benachrichtigung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### Phase 3: Journey entwerfen und aktivieren

**Anwendungsfunktion:** AJO: Journey Orchestration

Entwerfen Sie die mehrstufige Journey-Arbeitsfläche einschließlich des Einstiegsknotens, der Aktionsknoten (Nachrichten), der Bedingungsknoten (Verzweigung), der Warteknoten (Zeitverzögerungen) und der Beendigungskriterien. Testen Sie dann mit Testprofilen und veröffentlichen Sie.

#### Festlegen des Eintragstyps

Wie sollen Profile auf die Journey gelangen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Zielgruppe lesen | Geplante Nurture-Sequenzen; bekannte Zielgruppe im Batch verarbeitet | Zielgruppe zur Lesezeit ausgewertet; unterstützt einmalige oder wiederkehrende Lesevorgänge; bis zu 20.000 Profile/Sek. |
| Unitäres Ereignis | Trigger im Verhalten in Echtzeit (Kauf, Warenkorbabbruch) | Echtzeit-Eintritt; erfordert Ereignis-Streaming; bis zu 5.000 Ereignisse/Sek. |
| Zielgruppen-Qualifizierung | Eintritt, wenn ein Profil nahezu in Echtzeit in eine Zielgruppe eintritt oder diese verlässt | Streaming-Auswertung; ausgelöst durch Änderung der Segmentzugehörigkeit |
| Geschäftsereignis | Organisationsweite Veranstaltung - Trigger der Journey für eine Zielgruppe | Nützlich für Produktstarts, Wetterereignisse, Systemwarnungen |

#### Entscheidung über die Richtlinie für den Wiedereintritt

Kann ein Profil nach Abschluss oder Verlassen die Journey erneut aufrufen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Erneuten Eintritt erlauben (mit Abklingzeit) | Profile müssen die Journey möglicherweise wiederholen (wiederkehrende Käufe, saisonale Rückgewinnung) | Minimale Abklingzeit von 5 Minuten; verhindert doppelte Einträge im Abklingfenster |
| Kein Wiedereintritt | Einmalige Journey (Onboarding, einmaliges Lebenszyklus-Ereignis) | Das Profil schließt die Journey ab oder verlässt sie und kann nicht erneut eintreten |

#### Festlegen der Wartezeiten zwischen Touchpoints

Wie lange sollte die Journey zwischen den einzelnen Nachrichten warten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Feste Dauer (z. B. 3 Tage) | Konsistentes Tempo unabhängig vom Profilverhalten | Einfach; vorhersehbarer Zeitpunkt; mindestens 1 Stunde für Journey mit Zielgruppenlesen |
| Bestimmtes Datum/bestimmte Uhrzeit | Die Nachricht muss zu einem bestimmten Zeitpunkt eintreffen (z. B. Datum der Verlängerung) | Verwendet ein Profilattribut oder einen Ausdruck, um das genaue Datum/die genaue Uhrzeit zu bestimmen |
| Benutzerdefinierter Ausdruck | Dynamische Wartezeit basierend auf Profildaten oder Journey-Kontext | Am flexibelsten; Erfordert Ausdruckserstellung |

#### Festlegen von Verzweigungsbedingungen

Welche Bedingungen bestimmen, welchen Pfad ein Profil einschlägt?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Prüfung der Profilattribute | Branch basierend auf Treuestufe, Produktinteresse, Geografie | Verwendet zum Zeitpunkt der Auswertung verfügbare Profildaten |
| Prüfung der Segmentzugehörigkeit | Verzweigung basierend darauf, ob das Profil zu einer bestimmten Zielgruppe gehört | Zielgruppe muss definiert und ausgewertet werden |
| Prüfung der Ereignisdaten | Verzweigung in Abhängigkeit davon, ob das Profil eine Aktion ausgeführt hat (geöffnete E-Mail, angeklickter Link) | Wertet Ereignisdaten im Journey-Bereich aus. Nützlich für interaktionsbasierte Verzweigungen |
| Prozentuale Aufspaltung | Profile nach dem Zufallsprinzip über Pfade verteilen (für A/B-Tests oder kontrollierte Rollouts) | Verwendet keine Profildaten; rein zufällige Zuordnung |

#### Entscheidung über Ausstiegskriterien

Welches Ereignis oder welche Bedingung führt dazu, dass ein Profil die Journey vorzeitig beendet?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Konversionsereignis | Das Profil führt die gewünschte Aktion aus (Kauf, Anmeldung, Formularübermittlung) | Erfordert Ereignis-Streaming; gängigste Ausstiegskriterien |
| Zielgruppenzugehörigkeit - Austritt | Das Profil verlässt die Eintrittzielgruppe oder tritt einer Ausschlusszielgruppe bei | Wird für Streaming-Zielgruppen nahezu in Echtzeit ausgewertet |
| Zeitüberschreitung | Maximale Journey-Dauer erreicht (bis zu 91 Tage) | Standard-Sicherheitsnetz; konfigurierbar in Journey-Eigenschaften |
| Keine Ausstiegskriterien | Das Profil vervollständigt natürlich den gesamten Journey-Pfad | Einfachste: Alle Profile durchlaufen die gesamte Journey, sofern sie nicht manuell entfernt wurden |

#### Festlegen der Journey-Zeitüberschreitung

Wie lange kann ein Profil maximal auf der Journey bleiben?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| 91 Tage (maximal) | Journey mit langer Laufzeit (vierteljährliche Verlängerung, erweitertes Onboarding) | Maximal zulässig; Profile, die sich zum Zeitpunkt der Zeitüberschreitung noch auf der Journey befinden, werden automatisch beendet |
| Benutzerdefinierte kürzere Dauer | Das Journey sollte innerhalb eines definierten Zeitfensters (7 Tage, 14 Tage, 30 Tage) abgeschlossen sein | Basierend auf dem natürlichen Lebenszyklus des Anwendungsfalls |

#### Navigation in der Benutzeroberfläche

- Journey erstellen: Journey > Journey erstellen
- Journey-Eigenschaften: Journey-Arbeitsfläche > Eigenschaftenbereich
- Einstiegsknoten: Journey-Arbeitsfläche > Ziehen der Aktivität „Zielgruppe lesen“ oder „Ereignis“
- Aktionsknoten: Journey-Arbeitsfläche > Kanalaktion per Drag-and-Drop (E-Mail, SMS, Push)
- Bedingungsknoten: Journey-Arbeitsfläche > Ziehen der Aktivität „Bedingung“
- Warteknoten: Journey-Arbeitsfläche > Ziehen der Aktivität „Warten“
- Beendigungskriterien: Journey-Eigenschaften > Beendigungskriterien > Konfigurieren
- Testmodus: Journey-Arbeitsfläche > Umschalten des Testmodus
- Veröffentlichen: Journey-Arbeitsfläche > Veröffentlichen

#### Wichtige Konfigurationsdetails

- Benennen Sie die Journey mit einer klaren, beschreibenden Konvention (z. B. „Onboarding_Series_Email_v1„)
- Zeitzone des Journey für konsistente Warteschrittverarbeitung festlegen
- Konfigurieren Sie jeden Aktionsknoten mit der entsprechenden Kanaloberfläche und einem Link zum erstellten Nachrichteninhalt.
- Jede Verzweigung muss mit einer Ende -Aktivität enden
- Konfigurieren Sie die für den Anwendungsfall geeigneten Regeln für den erneuten Eintritt
- Testmodus mit Testprofilen verwenden, um den vollständigen Journey-Pfad vor der Veröffentlichung zu simulieren
- Überprüfen, ob Testprofile die erwarteten Pfade durchlaufen und korrekte Nachrichten empfangen

#### Wo die Optionen auseinander gehen

**Für Option A (audience-read):**

- Ziehen Sie die Aktivität „Zielgruppe lesen“ als Einstiegsknoten
- Die in Phase 1 definierte Zielgruppe auswählen
- Optional können Sie einen Zeitplan für wiederkehrende Lesevorgänge konfigurieren (täglich, wöchentlich)
- Konfigurieren der Leseratendrosselung, wenn die nachgelagerte Systemlast ein Problem darstellt

**Für Option B (ereignisausgelöst):**

- Auslösendes Ereignis als Einstiegsknoten ziehen
- Konfigurieren des Ereignisschemas und der Einstiegsbedingungen
- Legen Sie die Regeln für den erneuten Eintritt sorgfältig fest, um doppelte Einträge aufgrund wiederholter Ereignisse zu vermeiden

**Für Option C (Mehrkanal):**

- Verwenden der Eingabemethode von Option A oder B
- Wählen Sie bei jedem Aktionsknoten die entsprechende Kanaloberfläche für diesen Touchpoint aus
- Fügen Sie Bedingungsknoten zwischen Kanälen hinzu, um die Interaktion zu überprüfen (z. B. „Hat das Profil die E-Mail geöffnet?„) und zu alternativen Kanälen weiterleiten

#### Dokumentation zu Experience League

- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Endaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### Phase 4: Konfigurieren von Governance und Optimierung

**Anwendungsfunktionen:** AJO: Frequency &amp; Business Rules, AJO: Conflict &amp; Priority Management, AJO: Content Experimentation, RT-CDP: Consent &amp; Governance Enforcement

Wenden Sie Häufigkeitsbegrenzungen an, um Übernachrichten zu verhindern, weisen Sie Prioritätswerte für die Konfliktlösung mit anderen aktiven Kommunikationen zu, konfigurieren Sie optional A/B-Tests innerhalb von Journey-Nachrichten und überprüfen Sie die Durchsetzung des Einverständnisses.

#### Festlegen der Frequenzlimitierung

Sollten Journey-Nachrichten globale Frequenzlimits einhalten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Häufigkeitsregeln anwenden | Journey arbeitet mit anderen Kampagnen und Journey zusammen. Profile sollten nicht überbewertet werden | Nachrichten können unterdrückt werden, wenn das Profil bereits die Begrenzung aus anderen Nachrichten erreicht hat |
| Von der Begrenzung ausgenommen | Journey-Nachrichten sind wichtig und müssen immer zugestellt werden (Transaktions- und behördliche Auflagen) | Nur sparsam verwenden; kann bei übermäßiger Nutzung zur Nachrichtenermüdung beitragen |

#### Festlegen der Prioritätsbewertungszuweisung

Wie sollte diese Journey im Vergleich zu anderen aktiven Kampagnen und Journey bewertet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Hohe Priorität (70-100) | Journey-Nachrichten sind wichtige Lebenszykluskommunikationen (Onboarding, Verlängerung) | Höhere Priorität gewinnt, wenn Konflikte mit anderen Kommunikationen auftreten |
| Medium-Priorität (30-69) | Journey-Nachrichten sind wichtig, aber nicht dringend (Pflege, Bildung) | Kann durch Kommunikation mit höherer Priorität unterdrückt werden |
| Niedrige Priorität (0-29) | Journey-Nachrichten sind ergänzend oder werbewirksam | Wird unterdrückt, wenn mit Nachrichten höherer Priorität konkurriert wird |

#### Entscheidung über Inhaltsexperimente

Sollte eine Journey-Nachricht einen A/B- oder Multivarianz-Test enthalten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Ja — A/B-Test | Optimieren von Betreffzeilen, CTAs oder Inhalts-Layouts an einem bestimmten Touchpoint | Erfordert für statistische Signifikanz ausreichend Volumen pro Variante; 2-10 Behandlungen unterstützt |
| Keine Experimente | Der Inhalt ist fertig gestellt oder das Volumen ist zu niedrig für aussagekräftige Tests | Einfachere Einrichtung, kein Varianten-Tracking erforderlich |

#### Navigation in der Benutzeroberfläche

- Häufigkeitsregeln: Administration > Geschäftsregeln > Regel erstellen
- Prioritätswerte: Journey-Eigenschaften > Prioritätswert
- Konflikterkennung: Administration > Geschäftsregeln > Konflikt und Priorität
- Inhaltsexperiment: Journey-Arbeitsfläche > Nachrichtenaktion auswählen > Umschalter für Inhaltsexperiment
- Einverständnisrichtlinien: Datenschutz > Richtlinien > Einverständnisrichtlinien

#### Wichtige Konfigurationsdetails

- Kanalspezifische Häufigkeitsbegrenzungen festlegen (z. B. maximal 3 E-Mails/Woche, maximal 1 SMS/Tag, maximal 2 Push/Tag)
- Weisen Sie der Journey einen Prioritätswert (0-100) zu, der ihre geschäftliche Bedeutung im Verhältnis zu anderen aktiven Kommunikationen widerspiegelt
- Überprüfen Sie das Bedienfeld „Konflikterkennung“, um sich überschneidende Kampagnen oder Journey zu identifizieren
- Wenn Sie ein Inhaltsexperiment durchführen, definieren Sie Abwandlungsvarianten, legen Sie die Traffic-Zuordnung fest, wählen Sie die Erfolgsmetrik (Öffnungen, Klicks oder Konversionen) aus und legen Sie den Konfidenzschwellenwert (normalerweise 95 %) fest
- Stellen Sie sicher, dass die Einverständnisdurchsetzung für jeden auf der Journey verwendeten Kanal aktiv ist.

#### Dokumentation zu Experience League

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### Phase 5: Konfigurieren von Reporting und Überwachung

**Anwendungsfunktionen:** AJO: Reporting und Leistungsanalyse, Überwachung und Beobachtbarkeit, Reporting und Analyse

Überwachen Sie die Journey-Ausführung während und nach der Aktivierung, überprüfen Sie die Versand- und Interaktionsmetriken für einzelne Schritte, konfigurieren Sie Warnhinweise für Journey-Verarbeitungsfehler und erstellen Sie optional eine CJA Workspace-Analyse für umfassende funnel- und Fallout-Visualisierung.

#### Festlegen der Berichtsmethode

Welche Reporting-Tools sind für diese Journey erforderlich?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native AJO-Berichte | Die grundlegende Versand- und Interaktionsüberwachung ist ausreichend | Live-Bericht (während der Ausführung) und All-Time-Bericht (nach der Ausführung); aktualisiert alle 60 Sekunden für die Live-Schaltung |
| Analyse von AJO und CJA | Detaillierte funnel-Analysen, Schrittkonversionsraten, Fallout-Visualisierung oder Cross-Journey-Vergleich sind erforderlich | Erfordert eine Verbindung mit CJA und eine Datenansicht, die mit AJO-Datensätzen verknüpft sind. Umfassendste Beschreibung |
| Nur CJA | Das Unternehmen verwendet CJA als primäre Analyseplattform | Erfordert CJA-Konfiguration; native AJO-Berichte sind weiterhin als Backup verfügbar |

#### Entscheidung über Warnhinweiskonfiguration

Welche Journey-Fehler sollten Trigger-Warnhinweise anzeigen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Journey von Verarbeitungs-Warnhinweisen | Immer für Produktions-Journey empfohlen | Warnhinweise zu Fehlern bei Profileinträgen, Fehlern im Aktionsknoten und Journey-Verzögerungen |
| Warnhinweise bei fehlgeschlagenen Sendungen | Kritisch für Journey mit hochwertiger Kommunikation | Warnhinweise zu Bounce-Raten bei Überschreitung von Schwellenwerten, fehlgeschlagene Sendungen |

#### Navigation in der Benutzeroberfläche

- Journey-Live-Bericht: Journey > Journey auswählen > Live-Bericht
- Journey des Zeitberichts: Journey > Journey auswählen > Alle Zeitberichte
- Warnhinweise: Warnhinweise > Warnhinweisregeln > Abonnieren
- CJA Workspace: Projekte > Neues Projekt erstellen

#### Wichtige Konfigurationsdetails

- Greifen Sie während der Journey-Ausführung auf den Live-Bericht zu, um Profileinträge, -austritte und Bereitstellungsmetriken pro Schritt in Echtzeit zu überwachen
- Überprüfen Sie nach Abschluss des Journey-Vorgangs (oder nachdem ausreichende Daten gesammelt wurden) den Bericht Gesamte Zeit , um eine umfassende Analyse zu erhalten
- Konfigurieren von Platform-Warnungen bei Journey-Verarbeitungsfehlern und Versandproblemen
- Stellen Sie für die CJA-Analyse sicher, dass die CJA-Verbindung AJO-Erlebnisereignis-Datensätze enthält (Nachrichtenfeedback, E-Mail-Tracking, Journey-Schrittereignisse)
- Erstellen Sie eine CJA Workspace mit:
   - Funnel-Visualisierung mit der Profilanzahl bei jedem Journey-Schritt
   - Fallout-Visualisierung zur Identifizierung von Abfallpunkten
   - Berechnung der Schrittkonversionsrate
   - Analyse der Zeit bis zur Konversion
   - Aufschlüsselung der Interaktion auf Kanalebene (für Multi-Channel-Journey)

#### Dokumentation zu Experience League

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Überlegungen bei der Implementierung

Überprüfen Sie die folgenden Leitplanken, Fallstricke, Best Practices und Kompromisse vor und während Ihrer Implementierung.

### Leitplanken und Beschränkungen

- Maximal **500 Live-Journey** pro Sandbox - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Die maximale Dauer von **Journey beträgt 91 Tage** (globale Zeitüberschreitung) - Profile, die sich zur Zeitüberschreitung noch auf der Journey befinden, werden automatisch beendet
- Maximal **50 Aktivitäten** pro Journey-Arbeitsfläche
- Audience-Journey lesen verarbeitet bis zu **20.000 Profile pro Sekunde** (Standarddrosselung)
- Unitäre Ereignis-Journey unterstützen bis zu **5.000 Ereignisse pro Sekunde** pro Sandbox
- Warteschritte haben eine **Mindestdauer von 1 Stunde** für Journey mit Zielgruppenlesen
- Journey **Abklingzeit beim erneuten Eintritt beträgt mindestens 5 Minuten**
- Maximal **10 Kanaloberflächen pro Kanaltyp** pro Sandbox
- Maximale E-Mail-Größe von **100 KB** empfohlen für optimale Zustellbarkeit
- Maximal **30 Inhaltsfragmente** pro Nachricht
- Maximal **10 Inhaltsexperimentbehandlungen** (Varianten) pro Experiment
- Maximal **10 Begrenzungskonfigurationen** pro Sandbox
- Maximal **4.000 Segmentdefinitionen** pro Sandbox

### Häufige Fehler

- **Veröffentlichung ohne Tests:** Verwenden Sie immer den Testmodus mit Testprofilen, um den vollständigen Journey-Pfad vor der Veröffentlichung zu validieren. Stellen Sie sicher, dass die Profile die erwarteten Verzweigungen durchlaufen, die Warteschritte ordnungsgemäß ausgeführt werden und die Nachrichten ordnungsgemäß gerendert werden.
- **Fehlende Endaktivitäten in Verzweigungen:** Jede Journey-Verzweigung muss mit einer Endaktivität enden. Die Veröffentlichung des Journey schlägt fehl, wenn eine Verzweigung ohne Abschlussknoten belassen wird.
- **Zu weite Einstiegsbedingungen:** Eine locker definierte Einstiegszielgruppe oder -ereignisbedingung kann die Journey mit unbeabsichtigten Profilen überfluten. Eingabekriterien mit spezifischen Attributprüfungen und Unterdrückungsregeln verfeinern.
- **Wiederholungsregeln werden ignoriert:** Bei ereignisausgelösten Journey kann es vorkommen, dass Profile das auslösende Ereignis mehrmals auslösen. Ohne ordnungsgemäße Konfiguration für den erneuten Eintritt (erneute Eingabe verweigern oder Abklingzeit) können sich Profile auf der Journey ansammeln und doppelte Nachrichten verursachen.
- **Zeitzonenverwirrung bei Warteschritten:** Wartezeiten werden in UTC verarbeitet. Legen Sie die Journey-Zeitzone explizit in den Journey-Eigenschaften fest, um sicherzustellen, dass die Warteschritte zur erwarteten lokalen Zeit voranschreiten.
- **Das Bearbeiten einer Live-Journey:** Live-Journey kann nicht direkt bearbeitet werden. Um Änderungen vorzunehmen, duplizieren Sie die Journey, ändern Sie die Kopie, stoppen Sie das Original und veröffentlichen Sie die neue Version. Planen Sie die Journey-Versionierung vor der Live-Schaltung.
- **Keine Ausstiegskriterien definiert:** Ohne Ausstiegskriterien erhalten Profile, die Mid-Journey konvertieren, weiterhin nachfolgende Nachrichten - möglicherweise irrelevant oder widersprüchlich. Beendigungskriterien für Konversionsereignisse immer konfigurieren.
- **Fehlende Ausrichtung des Kanaleinverständnisses:** Ein Profil kann für E-Mail, aber nicht für SMS angemeldet werden. Multi-Channel-Journey müssen das Einverständnis pro Kanal respektieren. Überprüfen Sie, ob die Einverständnisfelder auf jeder Kanaloberfläche ausgefüllt und durchgesetzt werden.

### Best Practices

- **Einfach beginnen, iterieren:** Beginnen Sie mit einem linearen 2-3-stufigen Journey, bevor Sie komplexe Verzweigungen hinzufügen. Validieren Sie, ob der Kernfluss funktioniert, bevor Sie Bedingungen und Kanäle übereinander legen.
- **Verwenden Sie beschreibende Benennungskonventionen:** Benennen Sie Journey-Knoten, Bedingungen und Warteschritte klar (z. B. „Wait_3_Days_After_Welcome“ statt „Wait 1„). Dies erleichtert das Debugging im Testmodus und die Interpretation von Berichten erheblich.
- **Frühzeitiges Konfigurieren der Beendigungskriterien:** Sie das Konversionsereignis als Beendigungskriterium, bevor Sie die Journey-Pfade entwerfen. Dadurch wird sichergestellt, dass Profile, die konvertieren, unabhängig von ihrem aktuellen Schritt von der Journey entfernt werden.
- **Aussagekräftige Wartezeiten festlegen** Auf Kundenverhaltensdaten basierende Wartezeiten - Zeit zwischen typischen Interaktionen, erwarteten Antwortfenstern und einer kanalangemessenen Kadenz (z. B. 2-3 Tage zwischen E-Mails, 1 Woche zwischen SMS).
- **Verwenden von Bedingungsknoten zur Überprüfung der Interaktion:** Fügen Sie nach einer Nachrichtenaktion eine Bedingung hinzu, um zu überprüfen, ob das Profil interagiert hat (geöffnet, geklickt). Weiterleiten von eingeschalteten Profilen an einen Pfad und von nicht eingeschalteten Profilen an einen Eskalations- oder alternativen Kanalpfad.
- **Nutzen berechneter Attribute für Verzweigungen:** Verwenden Sie berechnete Attribute wie Interaktionswerte, Kaufhäufigkeit oder Tage seit der letzten Aktivität, um Verzweigungsentscheidungen datengesteuert anstatt willkürlich zu treffen.
- **Iterativ überwachen und optimieren** Überprüfen Sie Journey-Berichte wöchentlich während der ersten Ausführung. Identifizieren Sie Abfallpunkte, passen Sie Wartezeiten an, verfeinern Sie Bedingungen und optimieren Sie den Nachrichteninhalt basierend auf den Leistungsdaten pro Schritt.
- **Version Ihrer Journey** Wenn Sie Änderungen vornehmen, duplizieren Sie die Journey, um eine neue Version zu erstellen. Verwaltet ein Protokoll der Versionsänderungen für das Audit- und Optimierungs-Tracking.

### Entscheidungen über Kompromisse

Die folgenden Kompromisse sollten im Kontext Ihrer spezifischen Geschäftsanforderungen bewertet werden.

#### Eintrag „Zielgruppe lesen“ im Vergleich zu „ereignisausgelöster Eintrag“

Der Eintrag für das Lesen von Zielgruppen ermöglicht eine vorhersehbare, Batch-basierte Verarbeitung, die einfacher zu verwalten und zu testen ist. Der ereignisgesteuerte Eintritt bietet Reaktionsfähigkeit in Echtzeit, die kontextabhängiger ist, aber Streaming-Infrastrukturen und eine sorgfältigere Verwaltung des erneuten Eintritts erfordert.

- **Audience-Read-Vorteile:** Vorhersagbarkeit, Verarbeitung großer Datenmengen, geplante Lebenszyklusprogramme, einfachere Tests
- **Ereignisausgelöste Gefälligkeiten:** Echtzeit-Relevanz, Verhaltenskontext, individuelles Profil-Pacing, sofortige Reaktion auf Kundenaktionen
- **Empfehlung:** Verwenden Sie „Audience-Read“ für geplante Lebenszyklusprogramme (Onboarding, Verlängerung), bei denen das Timing geschäftsorientiert ist. Verwenden Sie ereignisgesteuerte Abfragen für Verhaltensreaktionssequenzen (Warenkorbabbruch, nach dem Kauf), bei denen der Zeitpunkt kundengesteuert ist.

#### Einkanal- und Mehrkanal-Journey

Einkanal-Journey sind einfacher zu implementieren, zu testen und zu verwalten. Multi-Channel-Journey bieten umfassendere Reichweite und Eskalationsfunktionen, erhöhen jedoch die Komplexität bei der Inhaltserstellung, der Einverständnisverwaltung und der Häufigkeits-Governance.

- **Einzel-Kanal-Vorteile:** Schnellere Implementierung, einfachere Einverständnisverwaltung, geringerer Aufwand bei der Inhaltserstellung, einfacheres Debugging
- **Multi-Channel-Vorteile:** Höheres Interaktionspotenzial, Kanaleskalation für nicht-responsive Profile, umfassendere Kundenerfahrung
- **Empfehlung:** Beginnen Sie mit einer Einkanal-Journey und validieren Sie die Fluss- und Geschäftsauswirkungen, bevor Sie sie auf mehrere Kanäle ausdehnen. Fügen Sie inkrementell Kanäle hinzu, bei denen die Interaktionsdaten zeigen, dass der primäre Kanal die Zielgruppe nicht effektiv erreicht.

#### Journey-Komplexität im Vergleich zu Verwaltbarkeit

Eine stark verzweigte Journey mit vielen Bedingungen und Pfaden kann mehr Szenarien bewältigen, wird jedoch schwieriger zu testen, zu debuggen und zu optimieren. Eine einfachere Journey mit weniger Verzweigungen ist einfacher zu verwalten, kann aber ein weniger personalisiertes Erlebnis bieten.

- **Komplexe Journey bevorzugen** Granulare Personalisierung, segmentspezifische Pfade, umfassende Szenarioabdeckung
- **Einfachere Journey bevorzugen:** schnellere Bereitstellung, einfachere Tests, klarere Berichterstellung, geringere Wartungskosten
- **Empfehlung:** Begrenzung der Journey auf 3-5 Hauptzweige und 15-25 Aktivitäten. Wenn die Logik komplexer ist, sollten Sie die Aufteilung in mehrere Journey mit Cross-Journey-Koordination anstelle einer einzigen monolithischen Journey erwägen.

#### Strenge der Häufigkeitsbegrenzung vs. Journey-Abschluss

Strenge Häufigkeitsbegrenzungen schützen vor übermäßigem Messaging, unterdrücken jedoch möglicherweise Journey-Nachrichten, sodass Profile Schritte überspringen und die Journey-Abschlussraten sinken. Lockere Begrenzungen gewährleisten, dass Journey-Nachrichten gesendet werden, riskieren aber eine Ermüdung des Kanals.

- **Strenge Obergrenzen zugunsten von** Kundenerlebnisschutz, reduzierte Abmelderaten, Markenvertrauen
- **Lenient caps favor:** Journey-Abschlussraten, Versand mit vollständiger Nachrichtensequenz, Effektivität des Marketing-Programms
- **Empfehlung:** Weisen Sie kritischen Journey-Nachrichten (Onboarding, Verlängerung) höhere Prioritätswerte zu, sodass sie Vorrang vor Werbekampagnen haben, wenn Obergrenzen erreicht werden. „Frei von der Begrenzung“ nur für wirklich wichtige Mitteilungen vorbehalten.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in dieser Implementierung verwendeten Funktionen.

### Journeys

- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Journey-Aktivitäten

- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Endaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Konfigurieren einer benutzerdefinierten Aktion](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Einreise- und Ausreiseverwaltung

- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Verwenden von Inhaltskomponenten von Email Designer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Inhaltsexperiment

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische Berechnungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Häufigkeit, Konflikt und Priorität

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Erste Schritte mit Konflikt- und Prioritätsverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Reporting und Analysen

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Einverständnis und Governance

- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Datengrundlage

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profilübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
