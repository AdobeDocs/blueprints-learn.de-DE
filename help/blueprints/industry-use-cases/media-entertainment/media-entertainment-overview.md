---
title: Anwendungsfälle für Medien und Unterhaltung
description: Erfahren Sie, wie Medien- und Unterhaltungsunternehmen Adobe Experience Platform verwenden, um die Inhaltssuche zu personalisieren, die Abwanderung von Abonnenten zu reduzieren und die Interaktion mit Zielgruppen zu steigern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: cfcf689f-9579-447f-9ef9-72e0c80c1f27
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '3363'
ht-degree: 0%

---

# Anwendungsfälle für Medien und Unterhaltung

Medien- und Unterhaltungsunternehmen verwenden Adobe Experience Platform, um Zielgruppendaten von Streaming-Plattformen, Inhaltsbibliotheken und Abonnentenkonten in einer einzigen Ansicht jedes Viewers oder Listeners zu vereinheitlichen. Diese Grundlage ermöglicht personalisierte Inhaltsfindung, proaktive Abonnementbindung und Interaktionsstrategien, mit denen die Zielgruppen immer wiederkommen und mehr erhalten.

## Content Recommendation Engine

Bereitstellen von personalisierten Inhaltsempfehlungen, einschließlich Filmen, Fernsehsendungen, Musik und Artikeln, basierend auf dem Anzeige- und Hörverlauf, Voreinstellungen und ähnlichem Benutzerverhalten. Wenn Zielgruppen Inhalte sehen, die auf ihre Interessen zugeschnitten sind, verbringen sie mehr Zeit damit, den Katalog zu erkunden und Titel zu entdecken, die sie andernfalls verpasst hätten.

### Auswirkung auf den Betrieb

Organisationen, die personalisierte Inhaltsempfehlungs-Engines bereitstellen, sehen eine verbesserte Inhaltsinteraktion und eine bedeutsame Steigerung der gesamten Zeit beim Beobachten oder Hören pro Benutzer.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Bei diesem Ansatz werden KI-gesteuerte Empfehlungsmodelle verwendet, die kontinuierlich aus den Interaktionen mit den Zielgruppen lernen, um für jede Person die relevantesten Inhalte zu ermitteln. Dies ist das richtige Muster, wenn die Elementgruppe groß ist und sich ständig ändert (Inhaltskataloge) und die Auswahl von der aus dem Verlauf erlernten Verhaltensaffinität gesteuert wird - und nicht von einer begrenzten Anzahl von Angeboten, die durch Eignungsregeln geregelt sind.

### Technische Überlegungen

- Inhaltskatalog-Metadaten, einschließlich Genre, Besetzung, Regisseur, Stimmungs-Tags und Inhaltsbewertungen, müssen aufgenommen und auf dem neuesten Stand gehalten werden, um sicherzustellen, dass die Empfehlungen die gesamte Breite der verfügbaren Titel widerspiegeln.
- Die Anzeige- und Hörsignale müssen nahezu in Echtzeit fließen, sodass die Empfehlungen innerhalb einer einzigen Browsersitzung aktualisiert werden, wenn ein Benutzer Inhalte ansieht oder überspringt.
- Empfehlungsmodelle erfordern eine Kaltstart-Strategie für neue Abonnentinnen und Abonnenten, die keinen Ansichtsverlauf sehen, sondern in der Regel auf Trends, redaktionell kuratierte oder regional beliebte Inhalte zurückgreifen.
- Inhaltslizenzierungs- und Verfügbarkeitsfenster müssen in die Empfehlungslogik einbezogen werden, damit Benutzende nie empfohlene Titel sind, die in ihrer Region nicht verfügbar sind oder aus dem Katalog entfernt wurden.


## Verhinderung von Abwanderungen bei Abonnements

Identifizieren Sie Abonnentinnen und Abonnenten, bei denen das Risiko einer Stornierung besteht, und interagieren Sie mit personalisierten Inhaltsempfehlungen, Angeboten und Aufbewahrungskampagnen. Die Bindung bestehender Abonnent*innen ist wesentlich kosteneffektiver als die Akquise neuer Abonnent*innen, und eine proaktive Kontaktaufnahme zum richtigen Zeitpunkt kann eine erhebliche Stornierung verhindern.

### Auswirkung auf den Betrieb

Effektive Abwanderungspräventionsprogramme führen zu einer deutlichen Verringerung der Abwanderung von Abonnenten, schützen den wiederkehrenden Umsatz und verbessern den langfristigen Wert der Zielgruppenlebensdauer.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Bei diesem Ansatz wird die Journey-Orchestrierung mit der Echtzeit-Entscheidungsfindung kombiniert, um für jeden gefährdeten Abonnenten über jeden Kanal hinweg das beste Aufbewahrungsangebot oder die beste Inhaltsempfehlung auszuwählen. Dies ist das richtige Muster, wenn die Journey die Bereitstellung kanalübergreifend koordinieren muss, um doppelte Aufbewahrungsangebote zu verhindern, und wenn die Angebotsauswahl Eignungsregeln auf der Grundlage des Abonnentenwerts und des Risikograds erfordert - eine mehrstufige Orchestrierung allein bietet nicht die erforderliche Entscheidungsebene in Echtzeit.

### Technische Überlegungen

- Die Bewertung des Abwanderungsrisikos muss Interaktionssignale wie abnehmende Überwachungszeit, reduzierte Anmeldefrequenz und Inhaltsbeendigung enthalten, um gefährdete Abonnentinnen und Abonnenten zu identifizieren, bevor sie die Abbruchseite erreichen.
- Bindungsangebote sollten auf der Grundlage des Abonnentenwerts und des Risikograds gestaffelt werden, von personalisierten Content-Highlights bis hin zu vergünstigten Planerweiterungen, um den Schutz der Umsätze mit den Auswirkungen auf die Marge auszugleichen.
- Die Journey muss Aufbewahrungsnachrichten für Abonnentinnen und Abonnenten unterdrücken, die bereits erneuert oder aktualisiert haben und eine Echtzeit-Integration mit dem Abonnement-Abrechnungssystem erfordern.
- [!DNL Journey Optimizer] Entscheidungsregeln sollten den Plantyp, die Beschäftigungsdauer und den Verlauf früherer Einlösungsangebote des Abonnenten berücksichtigen, um generische oder sich wiederholende Angebote zu vermeiden.


## Benachrichtigungen zu neuen Inhaltsversionen

Benachrichtigen Sie Abonnentinnen und Abonnenten über neue Inhaltsveröffentlichungen, die ihren Voreinstellungen und ihrem Ansichtsverlauf entsprechen. Rechtzeitige Benachrichtigungen über neue Inhalte fördern die sofortige Interaktion und erinnern Abonnentinnen und Abonnenten an den kontinuierlichen Wert ihres Abonnements.

### Auswirkung auf den Betrieb

Personalisierte Versionsbenachrichtigungen fördern die Interaktion mit neuen Inhalten innerhalb der ersten Woche nach der Veröffentlichung, beschleunigen die Zuschauerzahlen und verbessern die Metriken zur Inhaltsleistung.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf Ereignisse zur Inhaltsveröffentlichung und gleicht neue Titel mit Abonnentenpräferenzprofilen ab, um zeitnahe und relevante Benachrichtigungen bereitzustellen. Dies ist das richtige Muster, wenn der Trigger ein Systemereignis (Inhaltsveröffentlichung) und kein Kundenverhalten ist und die erforderliche Kommunikation sofort und reaktiv erfolgt und keine nachhaltige Näherungssequenz ist.

### Technische Überlegungen

- Die Kalender für die Inhaltsveröffentlichung müssen integriert sein, damit Benachrichtigungen geplant oder ausgelöst werden können, sobald neue Titel verfügbar werden, sodass verfrühte Warnhinweise für Inhalte, auf die noch nicht zugegriffen werden kann, vermieden werden.
- Bei der Zuordnung von Abonnentenpräferenzen sollten mehrere Dimensionen berücksichtigt werden, einschließlich Genreaffinität, Lieblingsdarsteller oder Regisseure, zuvor angesehene Serien und Franchise-Interessen, um sicherzustellen, dass Benachrichtigungen sich persönlich relevant fühlen.
- Das Benachrichtigungsvolumen muss sorgfältig durch Frequenzlimitierung verwaltet werden, um zu verhindern, dass Abonnentinnen und Abonnenten sich in Zeiten hoher Inhaltsveröffentlichungen überfordert fühlen.
- Die Zeitzone und die Anzeige von Gewohnheitsdaten sollten den Versandzeitpunkt beeinflussen, sodass Benachrichtigungen zu dem Zeitpunkt eintreffen, an dem jeder Abonnent mit größter Wahrscheinlichkeit interagiert, und nicht zu einem einzigen globalen Versandzeitpunkt.


## Personalisierte Startseiten-Erfahrung

Personalisieren Sie die Homepage und die Inhaltserkennungsseiten dynamisch, um zuerst die relevantesten Inhalte basierend auf dem Profil und Verhalten jedes Benutzers anzuzeigen. Wenn Zuschauer Inhalte sehen, die unmittelbar nach dem Öffnen der App auf ihren Geschmack abgestimmt sind, interagieren sie schneller und surfen länger.

### Auswirkung auf den Betrieb

Personalisierte Homepage-Erlebnisse fördern die bessere Interaktion mit der Homepage und verbessern die Inhaltssuche erheblich, insbesondere für Plattformen mit großen und wachsenden Inhaltsbibliotheken.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Bei diesem Ansatz werden Auswahlstrategien und Rangfolgemodelle verwendet, um Inhaltszeilen und vorgestellte Titel auf der Homepage basierend auf dem Profil jedes Besuchers und dem Echtzeitverhalten neu anzuordnen. Dies ist das richtige Muster, wenn die Elementgruppe groß ist und sich ständig ändert und die Auswahl durch eine Verhaltensauffinität gesteuert wird, um Inhaltszeilen dynamisch zu reihen - anstelle eines statisch kuratierten Satzes oder einer einfachen attributbasierten Personalisierung.

### Technische Überlegungen

- Die Personalisierung der Startseite muss schnell genug ausgeführt werden, um wahrgenommene Lastverzögerungen zu vermeiden. Edge-basierte Entscheidungen oder Server-seitiges Rendering sind oft erforderlich, um die Erwartungen an die Antwortzeit von Untersekunden zu erfüllen.
- Die Personalisierungslogik sollte individuelle Präferenzen mit redaktionellen und Werbeprioritäten kombinieren, um sicherzustellen, dass Tentpole-Versionen, saisonale Inhalte und von Partnern geförderte Titel weiterhin angemessene Sichtbarkeit erhalten.
- Inhaltszeilen-Strategien wie „Weiter beobachten“, „Weil Sie zugesehen haben“ und „Jetzt im Trend“ erfordern jeweils unterschiedliche Dateneingaben und Rangfolgelogik, die in ein kohärentes Seiten-Layout orchestriert werden müssen.
- [!DNL Experience Platform] Web SDK-Implementierung muss Homepage-Interaktionen erfassen, einschließlich Zeilenscrollvorgänge, Kachelklicks und das Verhalten beim Bewegen des Mauszeigers, um die Rangfolgemodelle kontinuierlich zu verfeinern.


## Erinnerungen zu Watchlist und Favoriten

Senden Sie Benutzern Erinnerungen zu Inhalten in ihrer Watchlist, die sie noch nicht gesehen haben, zusammen mit personalisierten Empfehlungen für ähnliche Titel. Watchlists sind starke Absichtssignale, und sanfte Erinnerungen können diese Absichten in tatsächliche Ansichten umwandeln.

### Auswirkung auf den Betrieb

Erinnerungsprogramme für Watchlisten fördern die Abschlussraten von Watchlisten, wodurch aus gespeicherter Absicht aktive Interaktion wird und die allgemeine Plattformnutzung zunimmt.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz sendet Trigger-Erinnerungen basierend auf Aktivitäten auf der Watchlist und Inaktivitätssignalen, wobei zeitnahe Nudges gesendet werden, wenn Inhalte gespeichert, aber noch nicht gestartet wurden. Dies ist das richtige Muster, wenn ein diskretes Verhaltenssignal (Watchlist-Inaktivität) der Trigger ist und die erforderliche Antwort eine einzige, zeitabhängige Nachricht ist - und keine mehrstufige Sequenz oder ein kontinuierlicher Empfehlungs-Stream.

### Technische Überlegungen

- Der Zeitpunkt der Erinnerung sollte danach kalibriert werden, wie lange der Inhalt schon auf der Watchlist ist und ob der Benutzer kürzlich auf der Plattform aktiv war. So werden Erinnerungen in Zeiten starker Interaktion vermieden, wenn sie nicht erforderlich sind.
- Watchlist-Daten müssen sich über Geräte hinweg in Echtzeit synchronisieren, damit ein auf Mobilgeräten hinzugefügter Titel sofort in die Berechtigungsberechnungen für Erinnerungen übernommen und nicht plattformübergreifend dupliziert wird.
- Erinnerungen sollten kontextuelle Details hervorheben, wie etwa ablaufende Verfügbarkeitsfenster oder neue Staffeln gespeicherter Serien, um eine natürliche Dringlichkeit zu schaffen, ohne sich aufdringlich zu fühlen.
- Inhalte, die aus dem Katalog entfernt wurden oder in der Region des Abonnenten nicht mehr verfügbar sind, müssen automatisch von Erinnerungsnachrichten ausgeschlossen und durch alternative Empfehlungen ersetzt werden.


## Kostenlose Probekonversion-Kampagnen

Gewinnen Sie kostenlose Testbenutzer mit personalisierten Inhaltsempfehlungen und Angeboten, um die Abonnementkonversion vor Ablauf der Testphase zu fördern. Das Testfenster ist eine wichtige Gelegenheit, um den Nutzwert zu demonstrieren, den Anwender zahlen möchten. Eine strukturierte Konversions-Journey übertrifft deutlich eine einzige Erinnerung zum Testende.

### Auswirkung auf den Betrieb

Gut durchdachte Probekonvertierungs-Kampagnen bieten deutliche Verbesserungen der Konversionsraten von Testversand an Paid und steigern so direkt die Effizienz der Abonnentenerfassung und senken die Kosten pro Akquise.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Dieses Multi-Touch-Nurture-Journey führt Testanwender durch eine Abfolge von Content-Entdeckungen, Wertemeldungen und Konversionsnachrichten und passt sich während der gesamten Testphase an ihre Interaktion an. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf Interaktionsereignissen und der verbleibenden Testzeit erfordert - eine einzelne ausgelöste Nachricht kann die Abhängigkeitslogik zwischen Schritten oder die Notwendigkeit von Kadenzanpassungen nicht berücksichtigen.

### Technische Überlegungen

- Der Journey muss das Start- und Enddatum der Testversion genau verfolgen, wobei eine Verzweigungslogik die Messaging-Kadenz basierend auf den verbleibenden Testtagen und den beobachteten Interaktionswerten anpasst.
- Die Inhaltsempfehlungen auf der Journey sollten die ansprechendsten und exklusivsten Titel der Plattform priorisieren, um den wahrgenommenen Wert eines Paid Subscription während des begrenzten Testzeitraums zu maximieren.
- Benutzende, die vor Ablauf der Testversion konvertieren, sollten automatisch von der Konvertierungs-Journey in einen neuen Abonnenten-Willkommensfluss verschoben werden, um eine weitere Testversand-Nachricht zu verhindern.
- [!DNL Journey Optimizer] Journey-Bedingungen sollten den Testplantyp, die Empfehlungsquelle und die Geräteverwendung berücksichtigen, um den Konversionsansatz auf verschiedene Zielgruppensegmente anzupassen.


## Live Event Viewing Reminders

Benachrichtigen Sie Benutzer über bevorstehende Live-Ereignisse, Sportspiele oder Premieren, die ihren Interessen und ihrem Ansichtsverlauf entsprechen. Live-Inhalte fördern die Anzeige von Terminen, die die Gewohnheiten der Abonnenten stärken, und rechtzeitige Erinnerungen stellen sicher, dass Zielgruppen Ereignisse, die ihnen wichtig sind, nicht verpassen.

### Auswirkung auf den Betrieb

Personalisierte Live-Ereigniserinnerungen fördern die Verbesserung der Zuschauerzahlen bei Live-Ereignissen und maximieren die Zielgruppe für hochwertige Echtzeit-Programmierung.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz ermöglicht den Trigger von Benachrichtigungen auf der Grundlage von Ereigniszeitplandaten, wobei bevorstehende Ereignisse mit Abonnenteninteressenprofilen abgeglichen werden, um rechtzeitige Erinnerungen bereitzustellen. Dies ist das richtige Muster, wenn der Trigger ein Systemereignis (Ereigniszeitplan) und kein Kundenverhalten ist und die erforderliche Kommunikation sofort und zeitgebunden erfolgt und keine nachhaltige Nurture-Sequenz ist.

### Technische Überlegungen

- Ereigniszeitplandaten, einschließlich Startzeiten, teilnehmende Teams oder Talente und Broadcast-Details, müssen aus Programmiersystemen aufgenommen und auf dem neuesten Stand gehalten werden, um Zeitplanänderungen oder -absagen in letzter Minute zu handhaben.
- Der Versandzeitpunkt der Erinnerung sollte die Zeitzonen und typischen Vorlaufzeiten vor einem Ereignis berücksichtigen. Eine zu früh gesendete Erinnerung wird vergessen, während eine zu spät gesendete den Start verpasst.
- Bei der Interessenabstimmung sollten sowohl explizite Voreinstellungen wie bevorzugte Teams oder Genres als auch implizite Signale wie die Anzeigemuster vergangener Live-Ereignisse einbezogen werden, um relevante Ereignisse für jeden Abonnenten zu identifizieren.
- Die Koordination von Benachrichtigungen mit mehreren Geräten ist wichtig, damit ein Abonnent nicht gleichzeitig redundante Erinnerungen auf seinem Smartphone, Tablet und Smart-TV erhält.


## Generieren einer personalisierten Wiedergabeliste

Automatische Generierung und Aktualisierung personalisierter Wiedergabelisten basierend auf dem Hörverlauf, den Voreinstellungen und Stimmungsindikatoren jedes Benutzers. Kuratierte Wiedergabelisten reduzieren den Aufwand der Inhaltsauswahl und halten Hörer für längere Sitzungen interagiert.

### Auswirkung auf den Betrieb

Die Generierung personalisierter Wiedergabelisten trägt zu einer verbesserten Interaktion mit Wiedergabelisten bei und verlängert die durchschnittliche Dauer von Hörsitzungen bedeutend, wodurch die täglichen Gewohnheiten bei der Nutzung der Plattform gestärkt werden.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Dieser Ansatz verwendet KI-gesteuerte Modelle, die Hörmuster, Überspringungsverhalten und kontextuelle Signale analysieren, um Wiedergabelisten zu generieren und zu aktualisieren, die auf jeden Benutzer zugeschnitten sind. Dies ist das richtige Muster, wenn die Elementgruppe groß ist und sich ständig ändert und die Auswahl durch eine Verhaltensauffinität aus dem Hörverlauf und Stimmungssignalen gesteuert wird - und nicht durch eine begrenzte Menge von Wiedergabelisten, die durch redaktionelle Regeln geregelt werden.

### Technische Überlegungen

- Metadaten von Musikkatalogen, einschließlich Tempo, Genre, Stimmungs-Tags, Künstlerbeziehungen und Audiofunktionen, müssen umfangreich mit Tags versehen werden, um eine nuancierte Kuratierung der Wiedergabelisten zu ermöglichen, die über die einfache Zuordnung von Genres hinausgeht.
- Die Häufigkeit der Playlist-Aktualisierung sollte die Frische mit der Vertrautheit in Einklang bringen; Zuhörer erwarten neue Entdeckungen, möchten aber auch die Favoriten erneut besuchen, sodass Modelle die Exploration mit Komfort vermischen müssen.
- Kontextuelle Signale wie Tageszeit, Wochentag und Hörgerät können die Stimmung und das Energieniveau der Wiedergabeliste beeinflussen und so Wiedergabelisten erstellen, die sich für den jeweiligen Augenblick ansprechend anfühlen.
- [!DNL Experience Platform] Verhaltensdaten müssen granulare Listening-Ereignisse wie Überspringungen, Wiederholungen, Speicherungen und Sitzungsdauer erfassen, um die Empfehlungsmodelle kontinuierlich zu verfeinern.


## Plattformübergreifende Inhaltssynchronisierung

Stellen Sie ein nahtloses Inhaltserlebnis auf allen Geräten bereit, indem Sie den Verlauf, die Voreinstellungen und die Empfehlungen der Armbanduhren in Echtzeit synchronisieren. Zuschauer erwarten, dass sie auf einem Gerät anhalten und auf einem anderen fortgesetzt werden, ohne ihren Platz zu verlieren, und ein konsistentes Erlebnis über Plattformen hinweg stärkt die täglichen Nutzungsgewohnheiten.

### Auswirkung auf den Betrieb

Die plattformübergreifende Inhaltssynchronisierung verbessert die geräteübergreifende Interaktion und verringert Reibungsverluste, die zum Abbruch von Sitzungen führen können, wenn Benutzer zwischen Geräten wechseln.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz personalisiert das Erlebnis für identifizierte Benutzer über Web- und App-Plattformen hinweg und stellt so einen konsistenten Inhaltsstatus und Empfehlungen unabhängig vom Gerät sicher. Dies ist das richtige Muster, wenn die Personalisierung durch Profilattribute (geräteübergreifende Identität, Status des überwachten Fortschritts) und Segmentzugehörigkeit gesteuert wird und nicht durch ein Affinitätsmodell des Verhaltens oder eine Journey-Orchestrierungssequenz.

### Technische Überlegungen

- Die geräteübergreifende Identitätsauflösung muss Benutzersitzungen über Smart-TVs, mobile Apps, Tablets und Webbrowser hinweg zuverlässig verknüpfen, um für jeden Abonnenten ein einheitliches Profil zu pflegen.
- Fortschrittsdaten des Videoüberwachungssystems, einschließlich der genauen Wiedergabeposition, des Episodenabschlussstatus und der Voreinstellungen für Untertitel oder Audiospuren, müssen mit minimaler Latenz synchronisiert werden, um eine wirklich nahtlose Wiederaufnahme zu ermöglichen.
- Empfehlungsmodelle sollten den Gerätekontext berücksichtigen, da die Inhaltsvoreinstellungen zwischen einer mobilen Pendelsitzung und einer abendlichen Wohnzimmersitzung auf einem großen Bildschirm unterschiedlich sein können.
- [!DNL Real-Time Customer Data Platform] Profilzusammenführungsrichtlinien müssen so konfiguriert werden, dass gleichzeitige Sitzungen auf mehreren Geräten verarbeitet werden, ohne dass widersprüchliche Statusaktualisierungen erstellt werden.


## Social Sharing Personalization

Personalisieren Sie Eingabeaufforderungen und Empfehlungen für die Social Sharing basierend auf den sozialen Verbindungen und Inhaltsvoreinstellungen jedes Benutzers. Indem sie es den Zuschauern leicht und ansprechend machen, zu teilen, was sie lieben, verwandeln sie zufriedene Abonnenten in organische Fürsprecher, die das Bewusstsein und die Akquise fördern.

### Auswirkung auf den Betrieb

Personalisierte Social Sharing-Eingabeaufforderungen erzielen verbesserte Social Sharing-Raten, steigern die organische Reichweite und senken die bezahlten Anschaffungskosten.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz personalisiert In-App-Freigabeerlebnisse für identifizierte Benutzende und zeigt kontextuell relevante Freigabeaufforderungen basierend auf den Voreinstellungen und Interaktionsmustern der Benutzenden. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und dem bekannten Interaktionskontext und nicht von einem verhaltensbezogenen Affinitätsmodell gesteuert wird. Ziel ist es, das Erlebnis im Augenblick zu verbessern, ohne eine Journey-Sequenz zu orchestrieren.

### Technische Überlegungen

- Die Teilungsaufforderungen sollten in natürlichen Momenten der Freude ausgelöst werden, wie z. B. beim Abschließen einer überflüssigen Serie oder beim Entdecken eines neuen Lieblingskünstlers, anstatt in beliebigen Intervallen, die aufdringlich erscheinen.
- Vorausgefüllte Freigabenachrichten und -bilder müssen dynamisch auf der Grundlage des freigegebenen Inhalts generiert werden, einschließlich entsprechender Miniaturansichten, Beschreibungen und Deep-Links, die Empfänger zurück zur Plattform leiten.
- Mit Datenschutzkontrollen muss sichergestellt werden, dass die Anzeige von Aktivitäten nur dann freigegeben wird, wenn der Benutzer die Freigabe explizit einleitet. Die passive oder automatische Freigabe des Überwachungsverlaufs ohne Zustimmung kann das Vertrauen beschädigen.
- Die Integration von Social-Media-Plattformen muss den Freigaberichtlinien der einzelnen Netzwerke entsprechen und Authentifizierungs-, Ratenbeschränkungen- und Inhaltsformatanforderungen für Plattformen wie Instagram, TikTok und X handhaben.


## Premium-Funktion Upsell

Identifizieren Sie Benutzer, die von Premium-Funktionen profitieren würden, und präsentieren Sie personalisierte Upsell-Angebote basierend auf ihren Nutzungsmustern. Gezielte Upsell-Nachrichten für Benutzer, die bereits ein Verhalten zeigen, das mit dem Premium-Wert übereinstimmt, sind weitaus effektiver als pauschale Upgrade-Kampagnen.

### Auswirkung auf den Betrieb

Personalisierte Premium-Upsell-Kampagnen steigern die Akzeptanz von Premium-Funktionen, steigern den durchschnittlichen Umsatz pro Benutzer und bieten gleichzeitig Funktionen, die den Anforderungen der Abonnenten entsprechen.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Dieser Ansatz nutzt eine zentralisierte Entscheidungslogik, um die Nutzungsmuster jedes Abonnenten zu bewerten und das relevanteste Premium-Angebot zum richtigen Zeitpunkt auszuwählen. Dies ist das richtige Muster, wenn bei der Angebotsauswahl Einschränkungen für Nutzungsmuster und Eignungsregeln der Premium-Ebene berücksichtigt werden müssen - Einschränkungen, für die eine geregelte Entscheidungslogik erforderlich ist, anstatt nur das Ranking der Affinität mit dem Verhalten zu berücksichtigen.

### Technische Überlegungen

- Die Nutzungsmusteranalyse muss bestimmte Verhaltensweisen identifizieren, die auf Premium-Bereitschaft hinweisen, z. B. die häufige Verwendung von Funktionen, die in begrenzter Form im Basisplan verfügbar sind, die Nutzung mehrerer Geräte oder ein hohes Volumen des Inhaltsverbrauchs.
- Die Angebotsunterbreitung sollte die spezifischen Premium-Vorteile hervorheben, die für das Verhalten jedes Benutzers am relevantesten sind, anstatt alle Premium-Funktionen allgemein aufzulisten. Ein Benutzer, der häufig Inhalte herunterlädt, sollte die Offline-Anzeige hervorgehoben sehen.
- Upsell-Zeiten sollten frustrierende Momente vermeiden, z. B. unmittelbar nach einer Paywall-Sperre, und stattdessen positive Interaktionsmomente nutzen, wenn der Abonnent am empfänglichsten ist.
- [!DNL Journey Optimizer] Entscheidungsregeln müssen Upsell-Angebote für In-App-Nachrichten, E-Mails und Push-Benachrichtigungen koordinieren, um ein konsistentes Angebot zu unterbreiten, ohne den Abonnenten kanalübergreifend zu überfordern.


## Kampagnen zum Abschluss von Inhalten

Erinnern Sie Benutzer daran, Inhalte anzusehen oder anzuhören, die sie begonnen, aber nicht abgeschlossen haben, zusammen mit personalisierten Empfehlungen, was sie als Nächstes genießen sollten. Ein unvollständiger Inhalt stellt eine nicht realisierte Interaktion dar, und eine abgebrochene Sitzung wird durch einen sanften Stupser oft in ein abgeschlossenes Erlebnis umgewandelt.

### Auswirkung auf den Betrieb

Inhaltsabschlusskampagnen fördern verbesserte Inhaltsabschlussraten, erhöhen die Gesamtinteraktionszeit und stärken die Wahrnehmung der Abonnentinnen und Abonnenten hinsichtlich des Plattformwerts.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz erinnert Trigger auf der Grundlage von Ereignissen, die bei einem Inhaltsabbruch ausgelöst wurden, an rechtzeitige Nachrichten, wenn ein Benutzer teilweise durch einen Titel pausiert hat und nicht innerhalb eines definierten Fensters zurückgegeben wurde. Dies ist das richtige Muster, wenn ein diskretes Verhaltenssignal (Inhaltsabbruch) der Trigger ist und die erforderliche Antwort eine einzige, zeitabhängige Nachricht mit Kontext ist - und keine mehrstufige Journey oder dynamische Angebotsauswahl.

### Technische Überlegungen

- Die Abbruchschwellen sollten nach Inhaltstyp kalibriert werden. Ein Film, der mit der 80-%-Marke angehalten wurde, ist ein starker Abschlusskandidat, während ein Podcast, der nach zwei Minuten angehalten wird, eher auf Desinteresse als auf unterbrochenes Hören hinweisen kann.
- Erinnerungsnachrichten sollten den spezifischen Inhaltstitel, eine visuelle Miniaturansicht und einen direkten Deep-Link enthalten, der die Wiedergabe an der Stelle fortsetzt, an der der Benutzer aufgehört hat.
- Die Frequenzlimitierung muss übermäßige Erinnerungen für Benutzende verhindern, die routinemäßig Inhalte testen, ohne sie zu Ende zu führen. Wiederholte Stupser für Inhalte, die eine Benutzende aufgeben möchte, können sich aufdringlich anfühlen.
- Die Verfügbarkeit von Inhalten muss zum Zeitpunkt des Versands überprüft werden, da Titel die Plattform verlassen oder die Verfügbarkeitsregionen zwischen dem Abbruchs-Ereignis und dem Versand der Erinnerung ändern können.


## Analyse der Abonnentenabwanderung und der Inhaltsinteraktion

Ermitteln Sie, welche Muster bei der Nutzung von Inhalten, Änderungen der Interaktionsfrequenz und Verhaltensweisen bei Kataloginteraktionen einer Abmeldung von Abonnenten vorangehen, und messen Sie, wie die Inhaltsaffinität zwischen Abonnentensegmenten und Akquisekohorten variiert. Streaming- und Publishing-Unternehmen, die das Verhalten von Inhalten nicht mit Abwanderungsergebnissen verbinden können, treffen Inhaltsinvestitionsentscheidungen auf der Grundlage der aggregierten Ansichtsanzahl und nicht der Auswirkungen auf die Kundenbindung.

### Auswirkung auf den Betrieb

Die Korrelation von Interaktionsmustern bei Inhalten mit Abonnenten-Kundenbindungsergebnissen bietet Produkt-, Content-Strategie- und Marketing-Teams eine sachliche Grundlage für die Priorisierung von Kataloginvestitionen und die Gestaltung von Rückgewinnungskampagnen rund um die Verhaltensweisen, die tatsächlich Abonnements unterstützen.

### Implementieren

Verwenden Sie das [Muster Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) . Dieser Ansatz verbindet Streaming-Ereignisdaten, Inhaltsmetadaten, Abonnement-Lebenszyklusdatensätze und den Kampagneninteraktionsverlauf mit Customer Journey Analytics, wobei die Analyse der Kohortenbeibehaltung misst, wie die Inhaltsaffinität mit der Abonnentenzeit korreliert, und die Fallout-Analyse die Interaktionsabbruchmuster identifiziert, die einer Absage vorausgehen. Wenn es das Ziel ist, die verhaltensbezogenen Treiber der Abwanderung und die Content-Performance zu verstehen, ist dies das richtige Muster. Es geht nicht darum, eine Win-back-Nachricht auszulösen oder eine Zielgruppe mit Abwanderungsrisiko für die Unterdrückung zu aktivieren.

### Technische Überlegungen

- Ereignisse zur Inhaltsnutzung müssen sowohl Inhaltskennungen als auch Metadaten auf Sitzungsebene - Start-, Pause-, Fertigstellungs- und Überspringereignisse - enthalten, damit die Interaktionstiefe über die Anzahl der Rohwiedergaben in CJA hinaus gemessen werden kann.
- Abonnement-Lebenszyklusereignisse, einschließlich Teststart, Konversion, Zahlungsfehler, Downgrade und Stornierung, müssen als diskrete Ereignisse mit genauen Zeitstempeln aufgenommen werden, damit Verhaltensfenster für die Stornierung vor der Stornierung in CJA-Filtern genau definiert werden können.
- Inhaltskatalogattribute wie Genre, Format, Serienzuordnung und Versionsaktualität müssen als Lookup-Datensatz in der CJA-Verbindung verfügbar sein, damit die Inhaltsinteraktionsanalyse nach Katalogdimension aufgeschlüsselt werden kann, anstatt eine Analyse auf individueller Titelebene zu erfordern.
- Eine Kohortenanalyse, die die Kundenbindungskurven nach Akquise-Kanal und den angezeigten Originalinhalt vergleicht, erfordert, dass sowohl die Akquise-Quelle als auch der zuerst angezeigte Inhalt als Profil- oder Erstereignisdimensionen erfasst werden, die in CJA für die Kohortendefinition verfügbar sind.
