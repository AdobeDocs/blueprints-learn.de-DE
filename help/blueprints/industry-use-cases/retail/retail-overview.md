---
title: Anwendungsfälle für den Einzelhandel
description: Erfahren Sie, wie Einzelhandelsunternehmen Adobe Experience Platform verwenden, um Einkaufserlebnisse zu personalisieren, Transaktionsabbrüche zu beheben und die Kundentreue zu steigern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: 89a5b6b5-bb71-4154-bb3b-f6dbbbef13eb
source-git-commit: 3542d76106fada9019b70a8cc9fd4c74872d4995
workflow-type: tm+mt
source-wordcount: '7216'
ht-degree: 0%

---

# Anwendungsfälle für den Einzelhandel

Einzelhandelsunternehmen verwenden Adobe Experience Platform, um Kundendaten aus Online-Shops, physischen Standorten und Treueprogrammen in einer einzigen Ansicht jedes Kunden zu vereinheitlichen. Diese Grundlage ermöglicht personalisierte Einkaufserlebnisse, zeitnahe Kontaktaufnahme, die entgangene Umsätze wieder hereinbringt, und Treuestrategien, die dafür sorgen, dass die Kunden immer wieder zurückkommen.

## Personalisierte Produktempfehlung

Zeigen Sie personalisierte Produktempfehlungen auf der Homepage, auf Kategorieseiten und Produktdetailseiten basierend auf dem Browser-Verlauf, dem Kaufverlauf und ähnlichem Kundenverhalten an. Wenn Käufer Produkte sehen, die auf ihre Interessen zugeschnitten sind, verbringen sie mehr Zeit mit der Erkundung und kaufen viel eher.

### Auswirkung auf den Betrieb

Einzelhändler sehen verbesserte Clickthrough- und Konversionsraten, wenn sie personalisierte Empfehlungen anstelle von statischen Produktlisten bereitstellen.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Dieser Ansatz nutzt KI-gesteuerte Empfehlungsmodelle, die kontinuierlich aus Kundeninteraktionen lernen, um für jede Person die relevantesten Produkte zu ermitteln. Dies ist das richtige Muster, wenn der Elementsatz groß ist und sich ständig ändert und die Auswahl von der Verhaltensauffinität gesteuert wird - und nicht von einem begrenzten Satz von Angeboten, die von Eignungsregeln geregelt werden.

### Technische Überlegungen

- Produktkatalogdaten müssen erfasst und auf dem neuesten Stand gehalten werden, einschließlich Produktattribute, Bilder, Preise und Verfügbarkeit, um sicherzustellen, dass die Empfehlungen widerspiegeln, was Kunden tatsächlich kaufen können.
- Verhaltenssignale wie Produktansichten, Ereignisse vom Typ „In den Warenkorb legen“ und Käufe müssen nahezu in Echtzeit fließen, damit die Empfehlungen innerhalb einer einzigen Browsersitzung aktuell bleiben.
- Empfehlungsmodelle erfordern eine Kaltstart-Strategie für neue Besucher, die keinen Browser-Verlauf haben und typischerweise auf Trend- oder Bestsellerprodukte zurückgreifen.
- Die Seitenladeleistung muss sorgfältig überwacht werden, da Personalisierungsaufrufe keine merkliche Latenz zum Einkaufserlebnis hinzufügen sollten.


## E-Mail-Wiederherstellung bei Transaktionsabbruch

Senden Sie automatisch personalisierte E-Mail-Erinnerungen an Kunden, die ihren Warenkorb verlassen haben, einschließlich der genauen hinterlassenen Artikel und relevanter Angebote, um die Fertigstellung zu fördern. Warenkorbabbrüche sind eine der größten Quellen für Umsatzeinbußen im Einzelhandel, und rechtzeitige Folgemaßnahmen können einen erheblichen Teil dieser Verkäufe zurückgewinnen.

### Auswirkung auf den Betrieb

Effektive Programme zur Wiederherstellung des Warenkorbs verbessern die Wiederherstellungsraten des Warenkorbs und können je nach Speichervolumen einen bedeutenden zusätzlichen Umsatz generieren.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf ein Echtzeit-Warenkorbabbruchs-Ereignis und sendet eine rechtzeitige Erinnerung, während die Kaufabsicht immer noch hoch ist. Dies ist das richtige Muster, wenn eine diskrete Kundenaktion der Trigger ist und die erforderliche Antwort eine einzige, zeitkritische Nachricht ist - und keine mehrstufige Sequenz oder dynamische Angebotsauswahl.

### Technische Überlegungen

- Zur Erkennung eines Warenkorbabbruchs muss ein Schwellenwert für Inaktivität (in der Regel 30-60 Minuten) definiert werden, bevor die erste Erinnerung ausgelöst wird. So werden Nachrichten an Kunden vermieden, die noch aktiv einkaufen.
- E-Mail-Inhalte müssen aktuelle Produktbilder, Preise und Verfügbarkeit zum Versandzeitpunkt dynamisch aus dem Katalog abrufen, da sich Artikel zwischen Abbruch und Versand ausverkaufen oder den Preis ändern können.
- Die Regeln zur Frequenzlimitierung sollten verhindern, dass Kundinnen und Kunden innerhalb eines kurzen Zeitraums mehrere E-Mails zum Warenkorb mit Abbruch erhalten, insbesondere wenn sie den Warenkorb häufig verlassen.
- Einverständnis- und Unterdrückungslisten müssen vor dem Senden überprüft werden, und Kunden, die ihren Kauf über einen anderen Kanal abgeschlossen haben, sollten in Echtzeit ausgeschlossen werden.


## Inventarbasierte Dringlichkeitskampagnen

Trigger-Echtzeitwarnungen und -kampagnen, wenn der Produktbestand niedrig ist, wodurch eine Dringlichkeit entsteht und zum sofortigen Kauf ermutigt wird. Kunden, die sehen, dass nur noch wenige Artikel übrig sind, sind motiviert, schnell zu handeln, anstatt ihre Entscheidung zu verzögern.

### Auswirkung auf den Betrieb

Dringlichkeitskampagnen mit geringem Bestand fördern eine verbesserte Konversion für vorgestellte Produkte und tragen gleichzeitig dazu bei, Überbestände zu reduzieren, indem der Verkauf von sich langsam bewegenden Artikeln beschleunigt wird.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf Inventarschwellenwertereignisse und aktiviert automatisch die Dringlichkeitsnachrichten, wenn die Lagerbestände unter definierte Grenzwerte fallen. Dies ist das richtige Muster, wenn der Trigger eher ein Systemereignis als ein Kundenverhalten ist und die erforderliche Kommunikation sofort und reaktiv erfolgt und keine nachhaltige Nurture-Sequenz ist.

### Technische Überlegungen

- Inventar-Feeds müssen nahezu in Echtzeit in die Kundendatenplattform integriert werden, damit Dringlichkeitsnachrichten die tatsächlichen Lagerbestände und nicht veraltete Daten widerspiegeln.
- Schwellenwerte sollten für jede Produktkategorie konfiguriert werden, da sich ein Schwellenwert für „niedrige Lagerbestände“ bei einem großen Warenvolumen erheblich von einem für einen Luxusartikel unterscheidet.
- Die Werbebotschaft muss wahrheitsgetreu sein und den Verbraucherschutzbestimmungen entsprechen. Eine falsche Verknappung kann das Vertrauen der Marke schädigen und in bestimmten Märkten gegen die Werbestandards verstoßen.
- Die Messaging- und E-Mail-Kanäle vor Ort sollten so koordiniert werden, dass ein Kunde, der bereits gekauft hat, nicht weiterhin Benachrichtigungen zur Dringlichkeit für dasselbe Produkt erhält.


## Crosssell- und Upsell-Empfehlungen

Zeigen Sie relevante Crosssell- und Upsell-Produkte an der Kasse, in E-Mails und auf Produktseiten basierend auf Kaufmustern und Produktbeziehungen an. Der Vorschlag ergänzender oder Premium-Alternativen zum richtigen Zeitpunkt erhöht die Warenkorbgröße, ohne dass die Kunden selbst nach verwandten Artikeln suchen müssen.

### Auswirkung auf den Betrieb

Gut ausgeführte Crosssell- und Upsell-Strategien erhöhen den durchschnittlichen Bestellwert und steigern den Umsatz pro Transaktion, was zu einer besseren Gesamtwirtschaft beiträgt.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Dieser Ansatz verwendet eine zentralisierte Entscheidungslogik, um alle verfügbaren Angebote zu bewerten und die beste Crosssell- oder Upsell-Option für jeden Kunden und Kontext auszuwählen. Dies ist das richtige Muster, wenn bei der Angebotsauswahl Gewinnspannen, Lagerverfügbarkeit und Produktbeziehungsregeln berücksichtigt werden müssen - geschäftliche Einschränkungen, die eine geregelte Entscheidungslogik erfordern, anstatt nur eine Rangliste der verhaltensbezogenen Affinität zu erstellen.

### Technische Überlegungen

- Produktbeziehungsdaten, einschließlich häufig erworbener Verknüpfungen und Aktualisierungspfade, müssen gepflegt und regelmäßig aktualisiert werden, um aktuelle Kaufmuster widerzuspiegeln.
- Die Ranking-Logik von Angeboten sollte die Spanne, Relevanz und Lagerbestände berücksichtigen, sodass die rentabelsten und verfügbaren Optionen zuerst angezeigt werden.
- Crosssell-Empfehlungen an der Kasse müssen schnell geladen werden und dürfen den Kauffluss nicht stören. Langsame oder aufdringliche Vorschläge können die Konversionsrate tatsächlich verringern.
- [!DNL Journey Optimizer] Entscheidungsregeln sollten Fallback-Angebote enthalten, damit jeder geeignete Kunde eine Empfehlung erhält, selbst wenn die am häufigsten platzierte Option nicht verfügbar ist.


## Neue Kunden-Begrüßungsreihe

Automatisieren Sie eine Willkommensreihe mit mehreren E-Mails für neue Kunden mit personalisierten Produktempfehlungen, Marken-storytelling und Sonderangeboten. Die ersten Interaktionen nach dem Beitritt eines Kunden prägen seine langfristige Beziehung zur Marke und machen diese Serie zu einem der wirkungsvollsten Programme, die ein retailer ausführen kann.

### Auswirkung auf den Betrieb

Eine gut gestaltete Willkommensserie fördert die starke Interaktion unter neuen Kunden und verbessert den Lebenszeitwert bedeutend, indem die Markenaffinität frühzeitig aufgebaut wird.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Dieser Multi-Touch-Nurture-Journey führt neue Kunden durch eine Reihe von Markeneinführungen, Produktentdeckungen und Incentive-Botschaften, die sich an ihr Engagement anpassen. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen Fluss mit mehreren Nachrichten über Tage mit bedingter Verzweigung basierend auf Interaktionsereignissen erfordert - eine einzelne ausgelöste Nachricht kann die Abhängigkeitslogik zwischen den Schritten nicht berücksichtigen.

### Technische Überlegungen

- Der Journey-Einstiegs-Trigger muss Neukundenerstellungsereignisse aus allen Registrierungsquellen zuverlässig erfassen, einschließlich Web, Mobile App, Verkaufsstellen in Geschäften und Drittanbieter-Marketplaces.
- Warteschritte zwischen E-Mails sollten auf der Grundlage von Interaktionsdaten konfiguriert werden. Kunden, die sich öffnen und klicken, erhalten die nächste Nachricht möglicherweise früher, während weniger interaktive Kunden von mehr Abstand profitieren.
- Produktempfehlungen in Begrüßungs-E-Mails sollten widerspiegeln, was der Kunde bei seinem ersten Besuch angesehen oder gekauft hat, und nicht allgemeine Bestseller.
- Kunden, die während der Begrüßungsserie einen Kauf tätigen, sollten sich in einen Post-Purchase-Fluss verzweigen, anstatt weiterhin akquisitionsorientierte Nachrichten zu erhalten.


## Warnhinweise bei Preisverfall

Benachrichtigen Sie Kunden per E-Mail oder Push-Benachrichtigung, wenn Produkte auf ihrer Wunschliste oder zuvor angesehene Artikel im Preis fallen. Interessenten, die nicht eingekauft haben, reagieren sehr schnell auf Preisnachlässe, was dies zu einer der effizientesten Möglichkeiten macht, Überlegungen in Umsätze umzuwandeln.

### Auswirkung auf den Betrieb

Warnhinweise zu Preisrückgängen führen zu höheren Konversionsraten bei den Empfängern und verbessern die Kundenzufriedenheit messbar, da sie Kundinnen und Kunden das Gefühl geben, den besten Wert zu erhalten.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf Produktpreisänderungsereignisse und ordnet sie mit Kundeninteressensignalen ab, um zeitnahe Benachrichtigungen zu liefern. Dies ist das richtige Muster, wenn es sich bei dem Trigger um ein Katalogsystemereignis handelt und das Versandfenster zeitkritisch ist. Ein nachhaltiges Journey würde zu langsam sein und über die ursprüngliche Benachrichtigung hinaus ist kein mehrstufiges Follow-up erforderlich.

### Technische Überlegungen

- Zur Erkennung von Preisänderungen müssen Sie die aktuellen Preise mit früheren Werten im Produktkatalog-Feed vergleichen und nur Warnhinweise auslösen, die aussagekräftige Reduzierungen und keine geringfügigen Schwankungen bewirken.
- Kundeninteressensignale (Hinzufügungen zur Wunschliste, Produktseitenansichten, auf Produktseiten verbrachte Zeit) müssen effizient gespeichert und mit potenziell Tausenden von täglichen Preisänderungen abgeglichen werden.
- Die Benachrichtigungen sollten den ursprünglichen Preis, den neuen Preis und den Einsparbetrag enthalten, um den Wert klar zu kommunizieren. Vage „preisreduzierte“ Meldungen führen zu weniger spezifischen Einsparhinweisen.
- [!DNL Real-Time Customer Data Platform] Segmente für preisbewusste Käufer können verwendet werden, um den Versand von Warnhinweisen zu priorisieren und den Nachrichtenton anzupassen.


## Erinnerungs-Wiederauffüllung

Senden automatisierter Erinnerungen an Kunden für Produkte, die sie regelmäßig kaufen, z. B. Abonnements und Verbrauchsmaterialien, um sie zu wiederholten Käufen zu ermutigen, bevor sie ausgehen. Proaktive Erinnerungen verringern die Wahrscheinlichkeit, dass Kunden zu einem Mitbewerber wechseln, nur weil sie die Neuanordnung vergessen haben.

### Auswirkung auf den Betrieb

Reminder-Programme für Nachschublieferungen fördern verbesserte Wiederholungsraten und verbessern die Kundenbindung, indem sie es den Käufern erleichtern, die Produkte, auf die sie angewiesen sind, wieder aufzufüllen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Diese wiederkehrende geplante Journey verwendet Prognosen zur Kaufhäufigkeit, um Erinnerungen zum optimalen Zeitpunkt zu senden, bevor ein Kunde wahrscheinlich eine Nachfüllung benötigt. Dies ist das richtige Muster, wenn es kein diskretes Auslöseereignis gibt und die Zeitplanung anhand von Kauffrequenzmodellen berechnet werden muss, die dynamisch neu kalibriert werden. Durch ereignisgesteuerte Nachrichten können keine prädiktiven Zeitplanungs- oder Zeitplananpassungen verarbeitet werden, wenn Kunden vorzeitig oder zu spät neu anordnen.

### Technische Überlegungen

- Bei der Berechnung der Kaufhäufigkeit müssen die unterschiedlichen Verbrauchsraten in den verschiedenen Produktkategorien berücksichtigt werden. Eine Erinnerung für Kaffee sollte mit einer anderen Kadenz eingehen als für Reinigungsmittel.
- Die Journey sollte den Zeitpunkt dynamisch anpassen, wenn ein Kunde früher oder später als prognostiziert neu bestellt, und die nächste Erinnerung auf der Grundlage aktualisierter Kaufdaten neu kalibrieren.
- Erinnerungen sollten einen direkten Link zur Neuanordnung oder eine Ein-Klick-Rückkaufoption enthalten, um die Reibung zu minimieren und die Konversion aus der Benachrichtigung zu maximieren.
- Kunden, die bereits über einen anderen Kanal (In-Store, Abonnement-Service) neu bestellt haben, müssen unterdrückt werden, um das Senden irrelevanter Erinnerungen zu vermeiden.


## Personalisierte Kategorieseiten

Kategorieseiten dynamisch personalisieren, um zunächst die relevantesten Produkte basierend auf den Vorlieben, früheren Käufen und dem Browserverhalten jedes Kunden anzuzeigen. Wenn Käufer oben auf der Seite Produkte sehen, die ihrem Geschmack entsprechen, entdecken sie, was sie schneller möchten, und konvertieren zu höheren Raten.

### Auswirkung auf den Betrieb

Personalisierte Kategorieseiten fördern die Interaktion mit Kategorieseiten und verbessern die Produkterkennung deutlich, insbesondere für Einzelhändler mit großen Katalogen.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Bei diesem Ansatz werden Auswahlstrategien und Rangfolgemodelle verwendet, um Produkte auf Kategorieseiten basierend auf dem Profil jedes Besuchers und dem Echtzeitverhalten neu anzuordnen. Dies ist das richtige Muster, wenn die Aufgabe eine große, offene Produktgruppe mithilfe von verhaltensbezogenen Affinitätssignalen nach Rang ordnet. Die Angebotsentscheidung ist hier nicht geeignet, da es keine Eignungsregeln oder Geschäftsbeschränkungen gibt, die einschränken, welche Produkte angezeigt werden.

### Technische Überlegungen

- Das Produkt-Ranking muss schnell genug ausgeführt werden, um wahrgenommene Seitenladeverzögerungen zu vermeiden. Häufig ist eine Server-seitige Personalisierung oder Edge-basierte Entscheidungsfindung für Kategorieseiten mit Hunderten von Produkten erforderlich.
- Die Personalisierungslogik sollte individuelle Präferenzen mit Merchandising-Regeln kombinieren, um sicherzustellen, dass beworbene Produkte, Neuankömmlinge und saisonale Artikel weiterhin angemessene Sichtbarkeit erhalten.
- Es sollte eine Infrastruktur für A/B-Tests vorhanden sein, um die Umsatzauswirkungen von personalisierter Sortierung gegenüber standardmäßigen Merchandising-Regeln laufend zu messen.
- [!DNL Experience Platform] Web SDK-Implementierung muss Kategorieseiteninteraktionen (Bildlauftiefe, Produktklicks, Filternutzung) erfassen, um die Rangfolgemodelle kontinuierlich zu verfeinern.


## Follow-up-Kampagnen nach dem Kauf

Senden Sie E-Mails nach dem Kauf mit Tipps zur Produktpflege, zugehörigen Produktvorschlägen, Prüfungsanfragen und Informationen zum Treueprogramm. Der Zeitraum unmittelbar nach dem Kauf ist der Zeitraum, in dem Kunden die Marke am meisten interagieren, was sie zu einem idealen Fenster macht, um die Beziehung zu vertiefen und zukünftige Aktivitäten zu fördern.

### Auswirkung auf den Betrieb

Effektive Kampagnen nach dem Kauf steigern die Übermittlungsraten für Überprüfungen und fördern die Rate wiederholter Käufe, wodurch einmalige Käufer zu treuen Kunden werden.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Dieser mehrstufige Post-Purchase-Fluss verwendet eine Verzweigungslogik, um Folgenachrichten auf der Grundlage von Produkttyp, Kundensegment und Interaktion mit früheren E-Mails der Serie anzupassen. Dies ist das richtige Muster, da die Nachverfolgung mehrere Tage dauert, vom Erfüllungsstatus abhängt und Verzweigungen basierend auf Produktkategorie und Rückgabeereignissen aufweist. Eine einzelne ausgelöste Nachricht kann die erforderliche bedingte Logik in der gesamten Zeitleiste nach dem Kauf nicht unterstützen.

### Technische Überlegungen

- Der Journey muss den Status der Bestellabwicklung berücksichtigen. Pflegetipps und Überprüfungsanfragen sollten erst nach der Lieferung des Produkts gesendet werden, nicht sofort nach dem Kauf.
- Produktspezifische Inhalte (Pflegehinweise, Benutzerhandbücher, Zubehörvorschläge) erfordern ein Content-Mapping-System, das jede Produktkategorie mit relevanten Folgematerialien verknüpft.
- Der Zeitpunkt der Überprüfungsanfrage sollte basierend auf der Produktkategorie optimiert werden. Elektronik benötigt möglicherweise eine längere Nutzungsdauer, bevor eine aussagekräftige Überprüfung durchgeführt wird, während Bekleidung kurz nach der Lieferung überprüft werden kann.
- Kunden, die eine Rückgabe oder einen Austausch einleiten, sollten automatisch aus dem standardmäßigen Post-Purchase-Fluss entfernt und zu einem Service-Wiederherstellungspfad weitergeleitet werden.


## Exklusive VIP-Kundenangebote

Identifizieren Sie hochwertige Kunden und bieten Sie exklusive Angebote, frühzeitigen Zugriff auf den Verkauf und personalisierte Einkaufserlebnisse, die ihre Loyalität belohnen. Eine Kundenbindung auf höchster Ebene ist wesentlich kostengünstiger, als neue Kunden zu gewinnen, und eine exklusive Behandlung stärkt die emotionale Verbindung, die sie am Leben erhält.

### Auswirkung auf den Betrieb

VIP-Programme generieren ein starkes Engagement von erstklassigen Kunden und verbessern den Kundenlebenszeitwert messbar, indem sie die Abwanderung unter den gewinnträchtigsten Segmenten reduzieren.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Bei diesem Ansatz wird die Journey-Orchestrierung mit der Echtzeit-Entscheidungsfindung für die Angebotsauswahl kombiniert, sodass jeder VIP-Kunde über jeden Kanal hinweg das relevanteste Exklusivangebot erhält. Dies ist das richtige Muster, wenn die Journey die Bereitstellung kanalübergreifend koordinieren muss, um doppelte Angebote zu verhindern, und wenn die Angebotsauswahl Eignungsregeln und geschäftliche Einschränkungen erfordert - eine mehrstufige Orchestrierung allein bietet nicht die Entscheidungsebene in Echtzeit, die erforderlich ist, um zu steuern, welches exklusive Angebot jede VIP erhält.

### Technische Überlegungen

- VIP-Segmentierungskriterien müssen mithilfe von Metriken für Neuigkeit, Häufigkeit und Geldwert klar definiert werden. Segmente sollten häufig genug aktualisiert werden, um Kunden zu erfassen, die sich kürzlich qualifiziert oder disqualifiziert haben.
- Exklusive Angebote müssen an der Einlösungsstelle (Web, App, Store) durchgesetzt werden, um zu verhindern, dass Nicht-VIP-Kunden auf sie zugreifen. Dies erfordert die Integration in Werbe- und Preissysteme.
- Die Kanalpräferenzen variieren erheblich zwischen hochwertigen Kundinnen und Kunden. Einige bevorzugen E-Mails, andere reagieren auf App-Benachrichtigungen oder Briefpost, sodass die Journey Versandkanäle auf der Grundlage früherer Interaktionen anpassen sollte.
- [!DNL Journey Optimizer] Entscheidungsfindung muss kanalübergreifend koordiniert werden, um zu verhindern, dass ein VIP-Kunde dasselbe Angebot gleichzeitig per E-Mail, Push-Benachrichtigung und SMS erhält.


## Nicht vorrätige Benachrichtigungen

Kunden erlauben, sich für Benachrichtigungen zu registrieren, wenn nicht vorrätige Produkte verfügbar werden, und sie dann automatisch per E-Mail oder Textnachricht benachrichtigen. Die Erfassung der Nachfrage nach nicht verfügbaren Produkten verhindert Umsatzeinbußen und gibt den Kunden einen Grund, zum Geschäft zurückzukehren, anstatt bei einem Wettbewerber zu kaufen.

### Auswirkung auf den Betrieb

Backin-Stock-Benachrichtigungen erzielen hohe Konversionsraten unter den Abonnenten und verringern bedeutend Umsatzverluste für nachfrageseitige Produkte, die vorübergehende Lagerbestände erleben.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz ermöglicht den Trigger von Benachrichtigungen zu Back-in-Stock-Ereignissen, indem Inventaraktualisierungen mit der Anmeldung bei Kundenbenachrichtigungen abgeglichen werden, um zeitnahe Warnhinweise zu liefern. Dies ist das richtige Muster, da es sich bei dem Trigger um ein diskretes Inventarsystemereignis handelt, die Bereitstellung zeitkritisch ist (das Inventar kann schnell wieder ausverkauft sein) und die Kommunikation eine einzige Benachrichtigung und keine fortlaufende Journey ist.

### Technische Überlegungen

- Bei der Bestandsüberwachung müssen Wiederauffüllungsereignisse schnell erkannt werden. Verzögerungen von nur wenigen Stunden können dazu führen, dass das Produkt erneut ausverkauft wird, bevor benachrichtigte Kunden eine Chance auf den Kauf haben.
- Wenn ein beliebtes Produkt in begrenzter Menge wieder vorrätig ist, sollten Benachrichtigungen nach dem Anmeldedatum gestaffelt oder priorisiert sein, um zu vermeiden, dass Warnhinweise an mehr Kunden gesendet werden, als der verfügbare Bestand bereitstellen kann.
- Der Anmeldungsmechanismus für Benachrichtigungen muss die Kanalpräferenz (E-Mail oder Textnachricht) erfassen und die Opt-in-Anforderungen für jeden Kanal erfüllen, insbesondere für SMS.
- [!DNL Real-Time Customer Data Platform] Profilattribute sollten verfolgen, welche Produkte jeder Kunde beobachtet, damit doppelte Benachrichtigungen verhindert werden, wenn dasselbe Produkt mehrmals wiederhergestellt wird.


## Social Proof Personalization

Zeigen Sie personalisierte Social-Proof-Nachrichten an, einschließlich Bewertungen, Bewertungen und Empfehlungen von „Kunden, die dies gekauft haben, haben auch gekauft“, die auf dem Profil und den Präferenzen jedes Kunden basieren. Durch die Anpassung des sozialen Beweises an die Erfahrungen ähnlicher Kunden wird Vertrauen effektiver aufgebaut als durch Bewertungen allein.

### Auswirkung auf den Betrieb

Personalisierter sozialer Korrekturabzug erhöht Konversionsraten und verbessert das Kundenvertrauen, insbesondere bei Erstkäufern und teureren Produkten, bei denen die Kaufzurückhaltung am größten ist.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz personalisiert Web-Inhalte für identifizierte Besucher und wählt die relevantesten Reviews und Social-Proof-Elemente basierend auf dem Kundenprofil, den Voreinstellungen und dem Browserkontext aus. Dies ist das richtige Muster, wenn die Personalisierung von Profilattributen und Segmentzugehörigkeit und nicht von einem verhaltensbezogenen Affinitätsmodell gesteuert wird. Verhaltensempfehlungen sind hier nicht geeignet, da die Auswahl des Social-Proof-Tests davon abhängt, wer der Kunde ist, und nicht davon, welche Elemente er durchsucht hat.

### Technische Überlegungen

- Überprüfungs- und Bewertungsdaten müssen nach Kundenattributen strukturiert und getaggt sein (z. B. Kaufkontext, Kundensegment und Produktanwendungsfall), um eine aussagekräftige Filterung und Personalisierung zu ermöglichen.
- Elemente des sozialen Testversands sollten asynchron geladen werden, um zu vermeiden, dass das Rendern der Haupt-Produktseite blockiert wird, da Überprüfungsdaten von einer Prüfplattform eines Drittanbieters mit variablen Antwortzeiten stammen können.
- Datenschutzbestimmungen verlangen, dass Kundendaten, die zum Abgleichen von Bewertungen mit Besuchern verwendet werden, gemäß den Einverständnisvoreinstellungen verarbeitet werden. Die Anzeige von Inhalten des Typs „Kunden wie Sie“ impliziert Profiling, das möglicherweise offen gelegt werden muss.
- [!DNL Experience Platform] Zielgruppenzugehörigkeit kann verwendet werden, um auszuwählen, welche Rezensionen hervorgehoben werden sollen, wobei Outdoor-Enthusiasten-Rezensionen von anderen Outdoor-Käufern anstelle von generischen, top bewerteten Rezensionen angezeigt werden.


## KI-Produktberater

Onlinehändler führen Tausende von SKUs über komplexe Kategoriehierarchien hinweg, wodurch es für Käufer schwierig wird, das richtige Produkt ohne umfangreiches Browsen oder abgebrochene Suchen zu finden. Ein KI-gestützter Produktberater bindet Kunden in einen natürlichen Multi-Turn-Dialog ein - indem er qualifizierte Fragen zu Bedürfnissen, Präferenzen und Budget stellt - und verengt dann das Sortiment auf einen kuratierten Satz personalisierter Empfehlungen. Das Erlebnis spiegelt die Anleitung wider, die ein sachkundiger Mitarbeiter im Geschäft bieten würde, bereitgestellt in digitalem Maßstab.

### Auswirkung auf den Betrieb

Einzelhändler, die geführte dialogorientierte Entdeckungen einsetzen, sehen im Vergleich zum nicht unterstützten Browsen höhere Konversionsraten und einen höheren durchschnittlichen Bestellwert und reduzieren gleichzeitig durch fundiertere Kaufentscheidungen die Produktrendite.

### Implementieren

Verwenden Sie das [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)-Muster. Dieser Ansatz stellt die Product Advisor Agent anhand eines strukturierten Produktkatalogs bereit und verwendet AEP Agent Orchestrator- und Echtzeit-Kundenprofildaten, um markensichere, personalisierte Produktempfehlungen über einen natürlichen Dialog zu generieren. Dies ist das richtige Muster, wenn das Ziel in einer interaktiven, interaktiven, interaktiven, dialogorientierten Entdeckung besteht, die von kundenspezifischen Anforderungen gesteuert wird. Dies unterscheidet sich von ereignisgesteuertem Messaging, das einseitig ist und auf eine bestimmte Aktion reagiert, und von personalisierten Web-Erlebnissen, die Empfehlungen passiv anzeigen, anstatt Kundinnen und Kunden in Gespräche einzubinden. Dies erfordert die Konfiguration von AEP Agent Orchestrator und Brand Governance.

### Technische Überlegungen

- Der Produktkatalog muss mit umfangreichen Attributdaten strukturiert sein - einschließlich Größe, Material, Kompatibilität, Verfügbarkeit und Preise -, da die Product Advisor Agent Empfehlungen im Kataloginhalt begründet und keine zuverlässigen Ratschläge zu Produkten mit unvollständigen Attributen geben kann.
- Die Echtzeit-Kundenprofilsuche über RT-CDP muss mit Edge-Aktivierung konfiguriert werden, damit während der Live-Konversation ohne Latenz, die das Erlebnis stören würde, auf den Kaufverlauf, das Suchverhalten und die Daten der Treuestufe zugegriffen werden kann.
- Es müssen Leitplanken für die Markenverwaltung definiert werden, um festzulegen, wie der Agent mit nicht vorrätigen Artikeln, wettbewerbsfähigen Produktvergleichen, Werbepreisbehauptungen und verbotenen Themen umgeht, um sicherzustellen, dass jede Antwort mit den Markenstandards des Einzelhandels übereinstimmt.
- Konversationsereignisse - einschließlich Absichtssignale, Produktinteraktionen und Empfehlungsakzeptanz - müssen als XDM ExperienceEvents erfasst und an AEP zurückgestreamt werden. Dabei werden Kundenprofile mit Produktaffinitätsdaten angereichert, was die zukünftige Personalisierung auf allen Kanälen verbessert.


## Kanalübergreifende Attributionsanalyse

Messen Sie, wie jeder Marketing-Touchpoint - Paid Search-, E-Mail-, Social- und In-Store-Angebote - zu Online- und Offline-Kaufkonversionen beiträgt. Einzelhändler, die auf die Attribution „Letztkontakt“ angewiesen sind, unterschätzen systematisch die funnel-Kanäle der oberen Ebene und treffen Entscheidungen über die Budgetzuweisung auf der Grundlage eines unvollständigen Bildes des Kaufpfads.

### Auswirkung auf den Betrieb

Marketing-Teams für den Einzelhandel, die von der Letztkontakt- zur Multi-Touch-Attribution wechseln, erhalten einen klareren Überblick darüber, welche Kanäle die Kaufabsicht steuern, was zu besser informierten Budgetentscheidungen und einer verbesserten Rendite auf Marketing-Ausgaben führt.

### Implementieren

Verwenden Sie das [Muster Customer Analytics &amp; Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) . Dieser Ansatz verbindet Online- und Offline-Ereignisdaten - Web-Klicks, E-Mail-Interaktionen, Treuetransaktionen und Point-of-Sale-Datensätze - mit Customer Journey Analytics, wo Attributionsmodelle über den gesamten Kaufpfad konfiguriert und verglichen werden können. Dies ist das richtige Muster, wenn es darum geht, Zielgruppen zu messen und insight über eine komplexe Multi-Channel-Journey zu generieren, anstatt Zielgruppen zu aktivieren oder Nachrichten auszulösen, und wenn die Analyse Customer Journey Analytics statt eines CDP- oder Kampagnenorchestrierungs-Tools erfordert.

### Technische Überlegungen

- Die Transaktionsdaten von Verkaufsstellen und E-Commerce müssen eine konsistente Kundenkennung gemeinsam haben, damit In-Store- und Online-Konversionen in CJA in einer einzigen kanalübergreifenden Ansicht zusammengefasst werden können.
- In der CJA-Datenansicht sollten mehrere Attributionsmodelle - Erstkontakt, Letztkontakt, Linear und Zeitverfall - konfiguriert werden, damit Analysten sie nebeneinander vergleichen können, ohne die Analyse neu erstellen zu müssen.
- Paid-Media-Impressions- und -Klickdaten von externen Anzeigenplattformen müssen über Quell-Connectoren oder Batch-Uploads aufgenommen werden, um bezahlte Kanäle neben eigenen Kanälen in den Attributionspfad aufzunehmen.
- Konversionsfenster und Credit-Lookback-Zeiträume müssen pro Kanaltyp definiert werden, da sich das relevante Attributionsfenster für einen Paid-Search-Klick erheblich von dem einer saisonalen E-Mail-Kampagne unterscheidet.

## Zielgruppensegmentierung und Aktivierung für bezahlte Medien

Erstellen Sie hochwertige Zielgruppensegmente aus einheitlichen Kundenprofilen und aktivieren Sie diese über Paid-Media-Ziele wie Google Ads, Meta und The Trade Desk für Akquise- und Retargeting-Kampagnen. Die Vereinheitlichung von Verhaltens-, Transaktions- und Treuedaten ermöglicht eine präzisere Zielgruppenbestimmung, wodurch Verschwendung und Ausgaben reduziert und die Kampagnenrendite verbessert werden.

### Auswirkung auf den Betrieb

Einzelhändler, die hochwertige First-Party-Zielgruppen aktivieren, sehen verbesserte Übereinstimmungsraten auf Paid-Media-Plattformen, geringere Kosten pro Akquise und eine höhere Rendite für Werbeausgaben im Vergleich zu Drittanbietersegmenten.

### Implementieren

Verwenden Sie das Muster [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md), um die Zielgruppenzugehörigkeit anhand von einheitlichen Profilen zu bewerten und Segmente für verbundene Paid-Media-Ziele auf geplanter oder Streaming-Basis zu veröffentlichen. Dies ist das richtige Muster, wenn die Hauptanforderung die Segmentveröffentlichung in externen Systemen ist und nicht orchestriertes Messaging oder Echtzeit-Entscheidungsfindung.

### Technische Überlegungen

- Zur Erstellung vollständiger Kundenprofile vor der Aktivierung ist eine Identitätsauflösung für Web-, Mobile- und Treuedaten erforderlich. Fragmentierte Profile reduzieren die Zielgruppen-Qualität und die Übereinstimmungsraten.
- Ziel-Connectoren müssen für jede bezahlte Medienplattform konfiguriert werden, wobei die entsprechenden Einverständniskennzeichnungen auf Profilebene beachtet werden müssen, um zu verhindern, dass nicht einverstandene Daten aktiviert werden.
- Die Häufigkeit der Segmentaktualisierung sollte mit den Kampagnenzielen übereinstimmen. Möglicherweise müssen die Akquise-Zielgruppen täglich aktualisiert werden, während das Retargeting von Zielgruppen von nahezu in Echtzeit durchgeführten Aktualisierungen profitiert, um aktuelle Käufer auszuschließen.
- Die Überschneidungsanalyse zwischen Akquise- und Bindungs-Audiences hilft dabei, eine Kreuzkontamination zu vermeiden, wenn Bestandskunden Nachrichten zur Neukundenakquise erhalten.


## Kundenunterdrückung für Akquise-Kampagnen

Unterdrücken Sie bestehende Kundinnen und Kunden sowie aktuelle Konvertierer von Akquise und Ausgaben, indem Sie Ausschlusszielgruppen für Paid-Media-Ziele aktivieren und so verschwendete Ausgaben reduzieren. Durch das kontinuierliche Synchronisieren von Unterdrückungslisten wird sichergestellt, dass bezahlte Budgets auf neue Interessenten abzielen und nicht auf Personen, die bereits konvertiert sind oder aktiv interagieren.

### Auswirkung auf den Betrieb

Die Unterdrückung bestehender Kunden aus Akquise-Kampagnen reduziert die verschwendeten Ausgaben für bezahlte Medien, verbessert die Kosten pro Akquise und verhindert, dass bestehende Kunden Nachrichten erhalten, die für ihre Beziehungsphase irrelevant sind.

### Implementieren

Verwenden Sie das Muster [Audience Activation to Destinations](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md), um Ausschlusszielgruppen - aktuelle Käufer, aktive Abonnenten, hochwertige Kunden - regelmäßig für jedes Paid-Media-Ziel zu veröffentlichen. Dies ist das richtige Muster, wenn das Ziel die Segmentveröffentlichung zur Unterdrückung ist, anstatt eine kundenorientierte Journey zu orchestrieren.

### Technische Überlegungen

- Für Unterdrückungszielgruppen ist eine klare Definition erforderlich, wer ausgeschlossen werden soll - in der Regel Kunden, die innerhalb der letzten 30-90 Tage einen Kauf getätigt haben, aktive Mitglieder des Treueprogramms und aktuelle E-Mail-Konvertierungen.
- Ausschlusslisten müssen häufig genug aktualisiert werden, um Käufer auszuschließen, bevor Anzeigen geschaltet werden. Veraltete Unterdrückungslisten verursachen die meisten Markenkomfortationen in Zeiten mit hohem Verkaufsvolumen.
- Die Qualität des Identitätsabgleichs wirkt sich direkt auf die Unterdrückungsgenauigkeit aus - ein schlechter Abgleich von E-Mail- oder Geräte-IDs führt dazu, dass Bestandskunden noch Akquise-Anzeigen sehen.
- Stellen Sie sicher, dass Unterdrückungszielgruppen von Aufbewahrungszielgruppen getrennt sind, damit Win-Back-Kampagnen auch nach dem Ablauf veraltete Kundinnen und Kunden erreichen können, die nicht unterdrückt werden sollten.


## Personalisierte Web-Erlebnisse für bekannte Besucher

Stellen Sie authentifizierten Website-Besuchern personalisierte Hero-Banner, Produktempfehlungen und Werbeinhalte basierend auf ihrem Echtzeit-Profil, ihrer Segmentzugehörigkeit und ihrem Verhaltensverlauf bereit. Wenn wiederkehrende Kundinnen und Kunden Erlebnisse sehen, die auf ihren Treuestatus, ihren Kaufverlauf und ihre Voreinstellungen zugeschnitten sind, verbessern sich die Interaktionsraten und die Konversionsraten im Vergleich zu generischen Homepage-Erlebnissen erheblich.

### Auswirkung auf den Betrieb

Einzelhändler, die für bekannte Besucher personalisieren, sehen eine deutliche Verbesserung bei den Interaktionsmetriken, einschließlich der Zeit vor Ort, Seiten pro Sitzung und der Konversionsrate, mit der größten Auswirkung auf die Mitglieder des Treueprogramms, die häufig besuchen.

### Implementieren

Verwenden Sie das [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md), um profilgesteuerte personalisierte Erlebnisse beim Laden der Seite mithilfe von Echtzeit-Segmentzugehörigkeit und Profilattributen bereitzustellen. Dies ist das richtige Muster, wenn das Erlebnis durch identitätsverknüpfte Profildaten und nicht durch reine Sitzungssignale gesteuert werden muss - und wenn Inhaltsentscheidungen keine komplexen Angebots-Ranking oder geschäftlichen Einschränkungen erfordern.

### Technische Überlegungen

- Die Authentifizierung muss vor der Aktivierung der profilgesteuerten Personalisierung erfolgen. Die Website benötigt einen Mechanismus, um den Besucher zu identifizieren und seine ECID in ein bekanntes Profil aufzulösen.
- Die Echtzeit-Profilsuche muss innerhalb des Budgets der Seitenladelatenz abgeschlossen werden. Dies erfordert in der Regel eine vom Edge bereitgestellte Profilbewertung anstelle Server-seitiger API-Aufrufe auf dem kritischen Renderpfad.
- Inhaltsvarianten müssen für alle Zielgruppensegmente entworfen werden, die angesprochen werden sollen, einschließlich eines Standarderlebnisses für Besuchende, die keiner Personalisierungsregel entsprechen.
- Personalization-Entscheidungen sollten zur Analyse protokolliert werden, um A/B-Tests von Inhaltsvarianten und die Attribution von Interaktionsverbesserungen auf bestimmte Segmente zu ermöglichen.


## Web-Personalization für anonyme Besucher

Personalisieren Sie Inhalte für nicht identifizierte Website-Besuchende mithilfe von In-Session-Verhaltenssignalen wie aufgerufene Seiten, durchsuchte Produktkategorien und Empfehlungsquelle. Da der Großteil des Web-Traffics im Einzelhandel anonym ist, wird durch die Personalisierung für nicht erkannte Besucher die Reichweite der Personalisierung auf der Site über das authentifizierte Segment hinaus erheblich erweitert.

### Auswirkung auf den Betrieb

Einzelhändler, die anonymen Besuchern personalisierte Erlebnisse bereitstellen, sehen verbesserte Interaktionen und Konversionsraten beim ersten Besuch, was besonders starke Auswirkungen auf Besucherinnen und Besucher hat, die aus bestimmten Kampagnenquellen ankommen oder anspruchsvolle Kategorieseiten durchsuchen.

### Implementieren

Verwenden Sie das [Anonymer Besucher Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)-Muster, um sitzungsinterne Verhaltenssignale am Edge auszuwerten und relevante Inhaltsvarianten bereitzustellen, ohne dass eine Authentifizierung erforderlich ist. Dies ist das richtige Muster, wenn die Personalisierung sofort nach der ersten Interaktion funktionieren muss, ohne auf ein persistentes Profil angewiesen zu sein - insbesondere für Akquise-Traffic und Besuchende, die sich noch nicht angemeldet haben.

### Technische Überlegungen

- Die Personalisierung während der Sitzung beruht auf Streaming-Ereignisdaten, die über Edge Network erfasst werden. Die Edge-Auswertungsregeln müssen bereitgestellt und getestet werden, bevor Traffic an sie gesendet wird.
- Inhaltsvarianten sollten auf das Verhalten während der Sitzung mit hohem Signal ausgerichtet sein - Verweisquelle, erste Seitenansicht, erkundete Produktkategorie - und nicht auf Attribute mit niedrigem Signal, die eine Absicht nicht zuverlässig vorhersagen können.
- Die Datenschutzanforderungen müssen sorgfältig bewertet werden; einige Gerichtsbarkeiten behandeln die Verhaltenspersonalisierung auch für anonyme Besucher als Einverständnispflicht.
- Personalization-Regeln für anonyme Besucher sollten einfacher und schneller auszuwerten sein als Regeln für bekannte Besucher, da Edge-Latenzbeschränkungen strenger sind.


## Begrüßungs-Journey

Gestalten Sie eine mehrstufige Willkommens-Journey für neu registrierte Kunden und stellen Sie Onboarding-Inhalte, Produktschulungen und einen Erstankaufsanreiz über E-Mail- und Push-Kanäle bereit. Eine gut durchdachte Begrüßungsserie gibt den Ton für die Kundenbeziehung vor und erhöht die Wahrscheinlichkeit, dass ein neuer Registrant zu seinem ersten Kauf konvertiert, erheblich.

### Auswirkung auf den Betrieb

Welcome Series-Programme fördern bedeutsame Verbesserungen der Aktivierungsraten von Neukunden und der First-Purchase-Konversion. Die größte Wirkung erzielen Sie, wenn die Serie Bildungsinhalte mit einem zeitnahen, personalisierten Anreiz kombiniert.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um eine mehrtägige Onboarding-Sequenz mit Warteschritten, Kanalverzweigung basierend auf Interaktion und Unterdrückung zu entwerfen, wenn das erste Kaufziel erreicht ist. Dies ist das richtige Muster, wenn der Anwendungsfall einen sequenziellen, zeitlich beabstandeten Kommunikationsfluss mit bedingter Logik erfordert - eine einzelne ausgelöste Nachricht ist nicht ausreichend, um einen neuen Kunden durch das Onboarding-Erlebnis zu führen.

### Technische Überlegungen

- Der Journey-Eintrag sollte durch Kontoregistrierungsereignisse in Echtzeit ausgelöst werden, sodass die erste Begrüßungsnachricht sofort ankommt, wenn der Registrierungsaufwand hoch ist.
- Die Journey muss Ausstiegsbedingungen enthalten, die verbleibende Nachrichten unterdrücken, wenn ein neuer Kunde seinen ersten Kauf abschließt - die Fortsetzung der Begrüßungsreihe nach dem Kauf untergräbt die Relevanz der Nachricht.
- Die Kanalpräferenz muss überall eingehalten werden. Push-Benachrichtigungsschritte erfordern eine App-Installation und Push-Opt-in mit E-Mail-Fallback für Kunden ohne Opt-in.
- Personalization in der Welcome Series verbessert die Konversionsrate, erfordert jedoch genügend Profildaten, um aussagekräftig zu sein. Neue Profile benötigen daher häufig ein Fallback auf Bestseller oder Trend-Produkte.


## Warenkorbabbruch-Wiederherstellung

Trigger-E-Mail- und Push-Benachrichtigungen in Echtzeit, wenn ein Kunde seinen Warenkorb verlässt, mit personalisierten Produkterinnerungen und zeitlich begrenzten Kaufanreizen. Der Warenkorbabbruch gehört zu den Anwendungsfällen mit dem höchsten ROI im Einzelhandel und erzielt Umsätze von Kunden, die bereits eine starke Kaufabsicht gezeigt haben.

### Auswirkung auf den Betrieb

Gut ausgeführte Programme zum Verlassen des Warenkorbs erzielen einen bedeutenden Anteil des verworfenen Umsatzes, wobei die Wiederherstellungsraten am höchsten sind, wenn die erste Nachricht innerhalb einer Stunde nach dem Verlassen des Warenkorbs eintrifft und die exakten Artikel enthält, die im Warenkorb verbleiben.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöste Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um auf das Warenkorbabbruchs-Ereignis mit einer sofort ausgelösten Kommunikation zu reagieren, während die Kaufabsicht noch aktiv ist. Dies ist das richtige Muster, wenn eine diskrete Kundenaktion der Trigger ist und die Hauptanforderung eine zeitnahe, personalisierte Antwort ist - und nicht eine mehrwöchige Nurture-Sequenz oder eine komplexe Angebotsentscheidung mit geschäftlichen Einschränkungen.

### Technische Überlegungen

- Die Warenkorbabbruch-Erkennung erfordert einen definierten Inaktivitätsschwellenwert (in der Regel 30-60 Minuten), um zu vermeiden, dass Kunden, die noch aktiv im Internet surfen oder den Checkout-Ablauf abschließen, eine Nachricht senden.
- E-Mail-Inhalte müssen aktuelle Produktbilder, Preise und den Lagerstatus zum Versandzeitpunkt dynamisch rendern, da sich Artikel zwischen Abbruch und Nachrichtenversand verkaufen oder den Preis ändern können.
- Die Unterdrückungslogik muss Kundinnen und Kunden ausschließen, die ihren Kauf über einen anderen Kanal zwischen der Abbruchserkennung und dem Nachrichtenversand abgeschlossen haben.
- Die Regeln zur Frequenzlimitierung sollten Meldungen über einen wiederholten Warenkorbabbruch in kurzen Zeitfenstern verhindern, insbesondere für Kunden, die gewohnheitsmäßig den Warenkorb als Browser-Verhalten verlassen.


## Interaktions-Journey nach dem Kauf

Stellen Sie Post-Purchase-Nachrichten bereit, einschließlich Bestellbestätigungen, Versandaktualisierungen, Crosssell-Empfehlungen und Überprüfungsanfragen über eine orchestrierte mehrstufige Journey. Das Zeitfenster nach dem Kauf ist einer der Momente mit der höchsten Interaktion im Kundenlebenszyklus. Daher ist es ein idealer Zeitpunkt, um Kundentreue aufzubauen und relevante ergänzende Produkte einzuführen.

### Auswirkung auf den Betrieb

Einzelhändler mit strukturierten Journey nach dem Kauf sehen verbesserte Raten für Wiederholungskäufe und Kundenbewertungen, was sowohl zu langfristiger Treue als auch zu einem sozialen Nachweis beiträgt, der zukünftige Akquise unterstützt.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um eine Abfolge von Post-Purchase-Kommunikationen zu orchestrieren, die an wichtige Meilensteine geknüpft sind: Bestellbestätigung, Versand, Lieferung und Nachverfolgung nach dem Versand. Dies ist das richtige Muster, wenn der Anwendungsfall mehrere Tage mit mehreren Zielen umfasst - eine einzige ausgelöste Nachricht kann den Bogen von der Transaktionsbestätigung zur Treueakquise nicht verarbeiten, um die Kontaktaufnahme zu überprüfen.

### Technische Überlegungen

- Die Integration des Order Management-Systems ist erforderlich, um Kauf- und Versandereignisse in Echtzeit zu empfangen. Verzögerungen bei der Ereignisaufnahme führen zu einer ungünstigen Zeitplanung in der Post-Kauf-Kommunikation.
- Crosssell-Empfehlungen in der Nachkaufsequenz erfordern Echtzeit-Produktkatalogdaten und Rückschlüsse auf das Empfehlungsmodell zur Rendering-Zeit der Nachricht, um den aktuellen Bestand und die aktuellen Preise widerzuspiegeln.
- Nachrichten zu Überprüfungsanfragen müssen den Servicebedingungen der Plattform entsprechen, damit Anreize für Überprüfungen gegeben werden können, und sollten rechtzeitig versandt werden, nachdem der Kunde ausreichend Zeit hatte, das Produkt zu verwenden.
- Die Kanalkoordination ist wichtig - Kundinnen und Kunden sollten nicht beide E-Mails und Push-Benachrichtigungen für denselben Meilenstein erhalten, es sei denn, sie haben mit dem ersten Kanal interagiert.


## Upgrade-Kampagne für Treuestufe

Ermitteln Sie Kundinnen und Kunden, die sich den Schwellenwerten für die Treuestufe nähern, und stellen Sie zielgerichtete Kampagnen bereit, mit personalisierten Angeboten, die auf dem Kaufverlauf und den Präferenzen basieren, die nächste Stufe zu erreichen. Wenn Kunden ein Stufenupgrade in Reichweite haben, sorgt zielgerichtetes Messaging mit personalisierten Anreizen für Dringlichkeit und steigert das Kaufverhalten.

### Auswirkung auf den Betrieb

Upgrade-Kampagnen für die Treuestufe steigern das inkrementelle Kaufvolumen und verbessern die Interaktion mit dem Programm. Dies wirkt sich am stärksten auf Mid-Tier-Mitglieder aus, die kurz vor dem nächsten Schwellenwert stehen und die kürzlich eine Kaufaktivität gezeigt haben.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster, um eine Stufenannäherungskampagne zu erstellen, die Kunden erreicht, wenn sie einen definierten Ausgabenschwellenwert unterhalb ihrer nächsten Stufe erreichen, und sie durch eine Abfolge von Vorteilsbotschaften und Incentive-Angeboten führt. Dies ist das richtige Muster, wenn der Anwendungsfall die Überwachung eines berechneten Profilattributs im Laufe der Zeit und die Orchestrierung einer mehrstufigen Kampagne erfordert, die an den Fortschritt des Kunden bei der Erreichung eines Ziels gebunden ist.

### Technische Überlegungen

- Treueplattformdaten - Punktestand, Stufenstatus, Stufenschwellen - müssen erfasst und im Kundenprofil auf dem neuesten Stand gehalten werden, damit die Stufenannäherungsberechnungen korrekt sind.
- Kampagnen mit Stufenupgrades sollten für Kundinnen und Kunden unterdrückt werden, die die Zielstufe bereits erreicht haben oder deren Treuestatus sich seit dem Kampagneneintritt geändert hat.
- Personalisierte Anreize im Rahmen der Upgrade-Kampagne sollten sich auf Angebote beschränken, für die der Kunde tatsächlich infrage kommt und die den wahrgenommenen Wert der Stufenstruktur nicht untergraben.
- Die Kampagne muss eindeutige Ausstiegsbedingungen für Kunden enthalten, die ihr Stufenupgrade Mitte Journey abgeschlossen haben, sodass sie lieber eine Glückwunschnachricht senden, als die Überredungssequenz fortzusetzen.


## Kanalübergreifende Orchestrierung einer Kampagne

Orchestrieren Sie koordinierte Marketing-Kampagnen über E-Mail-, SMS-, Push- und Web-Kanäle hinweg mit Journey-Verzweigungen, Warteschritten und Frequenzlimitierungen, um die Interaktion ohne Ermüdung zu maximieren. Eine koordinierte kanalübergreifende Orchestrierung stellt sicher, dass Kunden unabhängig davon, auf welchen Kanal sie zuerst reagieren, ein kohärentes Kampagnenerlebnis erhalten, sodass doppelte Nachrichten und widersprüchliche Angebote vermieden werden.

### Auswirkung auf den Betrieb

Einzelhändler mit kanalübergreifenden Orchestrierungsfunktionen sehen höhere Kampagneninteraktions- und Konversionsraten als Einzelkanal-Kampagnen, während sie gleichzeitig die Abmelderaten reduzieren, die durch Kanalmüdigkeit aufgrund von unkoordiniertem Messaging verursacht werden.

### Implementieren

Verwenden Sie das [Cross-Channel Journey with Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster, um Kampagnen zu erstellen, die Kundinnen und Kunden durch personalisierte Kanalsequenzen auf Grundlage ihres Interaktionsverlaufs, ihrer Kanalvoreinstellungen und ihrer Echtzeit-Antwortsignale führen. Dies ist das richtige Muster, wenn die Kampagne eine geregelte Angebotsauswahl, ein Routing mit Kanalvoreinstellungen und eine dynamische Verzweigung basierend auf In-Journey-Interaktionen erfordert - anstelle einer festen Reihenfolge, die an alle Kampagnenempfängerinnen und -empfänger gesendet wird.

### Technische Überlegungen

- Globale Frequenzlimitierungen müssen für alle Kanäle konfiguriert werden, um zu verhindern, dass Kunden zu viele Nachrichten erhalten, wenn mehrere Journey gleichzeitig ausgeführt werden.
- Kanalpräferenzdaten müssen aktuell und verwertbar sein. Präferenzprofile, die monatelang veraltet sind, leiten Kunden zu Kanälen, mit denen sie nicht mehr interagieren.
- Die Journey-Orchestrierungslogik sollte den erneuten Eintritt problemlos handhaben und Kunden daran hindern, zweimal in dieselbe Kampagne einzutreten, und gleichzeitig sicherstellen, dass sie nicht von wirklich neuen Kampagnen ausgeschlossen werden.
- Echtzeit-Interaktionssignale (E-Mail-Öffnungen, Link-Klicks, Websitzungen) sollten zurück auf die Journey geleitet werden, um einen Kanalwechsel und einen frühzeitigen Ausstieg für Kunden zu ermöglichen, die bereits konvertiert haben.


## Brand Concierge - Gesprächserlebnis

Stellen Sie einen KI-gestützten, markensicheren Konversationsagenten für digitale Eigenschaften bereit, um personalisierte Produktanleitung, Hilfe bei der Site-Navigation und nahtlose Übergabe an Live-Agenten bereitzustellen. Ein KI-Concierge vor Ort erweitert den personalisierten Service in großem Umfang und hilft Käufern, Produkte zu finden, Optionen zu vergleichen und Käufe abzuschließen, ohne dass ein menschlicher Agent für gängige Fragen erforderlich ist.

### Auswirkung auf den Betrieb

Einzelhändler mit KI-Concierge-Funktionen melden verbesserte Self-Service-Auflösungsraten, ein reduziertes eingehendes Support-Volumen für Produkt- und Navigationsfragen und eine höhere Konversionsrate bei Kunden, die vor dem Kauf mit Konversationsanleitungen interagieren.

### Implementieren

Verwenden Sie das [Brand Concierge Conversational Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)-Muster, um einen geregelten KI-Agenten bereitzustellen, der auf Produktkatalogdaten, Markenrichtlinien und dem Echtzeit-Kundenprofilkontext basiert. Dies ist das richtige Muster, wenn der Anwendungsfall die Interaktion in natürlicher Sprache über einen großen, dynamischen Produktsatz erfordert - anstelle eines skriptgesteuerten Chatbots mit festen Intents oder eines Musters, das einem bestimmten Kanal wie E-Mail entspricht.

### Technische Überlegungen

- Der KI-Agent muss auf aktuellen Produktkatalogdaten basieren, einschließlich Beschreibungen, Spezifikationen, Verfügbarkeit und Preisen, um eine genaue Anleitung zu bieten. Veraltete Produktdaten führen zu falschen Empfehlungen.
- Die Markensicherheit muss so konfiguriert sein, dass der Agent keine Wettbewerbsprodukte diskutieren, Preisverpflichtungen eingehen kann, die mit Werbeaktionen kollidieren, oder auf Off-Topic-Anfragen reagiert.
- Die Übergabelogik an Live-Agenten erfordert die Integration mit der Service-Plattform und sollte ausgelöst werden, wenn der KI-Agent die Kundenabfrage nach einer definierten Anzahl von Runden nicht lösen kann.
- Die Profildatenintegration ermöglicht es dem Agenten, Antworten basierend auf dem Kaufverlauf und dem Treuestatus zu personalisieren. Dies erfordert jedoch eine Identitätsauflösung vor Beginn der Gesprächssitzung.

## Check-in-Erinnerung mit App Download CTA

Erinnern Sie die Gäste daran, einzuchecken, und ermutigen Sie sie, die App herunterzuladen, um leicht auf Informationen zuzugreifen. Rechtzeitige Check-in-Erinnerungen zusammen mit Eingabeaufforderungen zum Herunterladen von Apps fördern die Interaktion mit Mobilgeräten und ermöglichen umfangreichere Erlebnisse am Veranstaltungsort.

### Auswirkung auf den Betrieb

Einzelhändler, die Check-in-Erinnerungen mit Appdownload-Aktionsaufrufen kombinieren, sehen höhere App-Akzeptanzraten und höhere Interaktionen im Geschäft, da Kunden, die die Mobile App verwenden, häufiger mit Werbe- und Veranstaltungsort-Inhalten interagieren.

### Implementieren

Verwenden Sie das [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um eine Check-in-Erinnerung mit der Mobile App zum Herunterladen von CTA auf der Grundlage von Ereignisteilnahme- oder Reservierungsdaten Trigger. Dies ist das richtige Muster, wenn als Reaktion auf ein bekanntes Ereignis oder einen Trigger beim Planen eine einzige zeitnahe Nachricht gesendet werden muss.

### Technische Überlegungen

- Check-in-Erinnerungen müssen zeitlich am Ereignis- oder Besuchsdatum ausgerichtet sein, um die Interaktion zu maximieren, ohne dass sie als zu früh oder zu spät wahrgenommen werden.
- Deep-Links zum App-Download sollten basierend auf der Geräteplattform des Kunden (iOS oder Android) zum richtigen App Store weitergeleitet werden.
- Kunden, die die App bereits installiert haben, sollten eine andere Nachrichtenvariante erhalten, bei der der CTA-Download übersprungen wird und der Schwerpunkt auf der Eincheckfunktion liegt.

## Geburtstagskampagnen für Fans

Sprechen Sie Fans an ihrem Geburtstag mit einer personalisierten Geburtstagsnachricht und einem exklusiven Angebot an. Geburtstagskampagnen schaffen emotionale Verbindungen zu Fans und fördern inkrementelle Käufe durch zeitnahe, personalisierte Öffentlichkeitsarbeit.

### Auswirkung auf den Betrieb

Geburtstagskampagnen liefern durchgängig überdurchschnittliche Öffnungs- und Konversionsraten, da sie zu einem Zeitpunkt von persönlicher Bedeutung kommen, Wohlwollen schaffen und Fans ermutigen, sich mit einem speziellen Kauf zu behandeln.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöste Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um eine personalisierte Geburtstagsnachricht zu senden, wenn das Geburtstagsdatum des Kunden eintrifft. Dies ist das richtige Muster, wenn eine einzelne ereignisgesteuerte Nachricht auf der Grundlage eines Datums-Triggers des Profilattributs gesendet wird.

### Technische Überlegungen

- Das Geburtstagsdatum muss im Kundenprofil erfasst und validiert werden, um zu verhindern, dass Nachrichten an falsche Daten gesendet werden.
- Angebote sollten über ein definiertes Gültigkeitsfenster verfügen (z. B. die Geburtstagswoche), um eine Dringlichkeit zu erstellen und den Kunden gleichzeitig eine angemessene Zeit zum Einlösen zu geben.
- Fans, die keinen Geburtstag haben, sollten von der Kampagne ausgeschlossen werden, anstatt eine allgemeine Nachricht zu senden.

## Geburtstagskampagnen für Käufer

Targeting von Kunden zu ihrem Geburtstag mit einer personalisierten Geburtstagsnachricht und einem exklusiven Angebot. Geburtstagskampagnen fördern die Markentreue, indem sie Kunden persönlich ansprechen und zum Kauf anregen.

### Auswirkung auf den Betrieb

Personalisierte Geburtstagsangebote führen zu höheren Einlösungsraten als allgemeine Werbeaktionen, da sie mit einem Moment übereinstimmen, in dem Käufer bereits geneigt sind, diskretionäre Käufe für sich selbst zu tätigen.

### Implementieren

Verwenden Sie das [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um einen Trigger für eine Geburtstagsnachricht und ein Angebot basierend auf dem Geburtsdatums-Profilattribut des Käufers auszuführen. Dies ist das richtige Muster, wenn eine einzelne personalisierte Nachricht an einem bestimmten Kalenderdatum gesendet werden muss, das mit dem Kundenprofil verknüpft ist.

### Technische Überlegungen

- Das Geburtstagsdatum muss als Profilattribut gespeichert werden und sollte bei der Registrierung oder bei der Treueprogramm-Anmeldung erfasst werden.
- Bei der Personalisierung von Angeboten sollten der Kaufverlauf und die Voreinstellungen des Käufers berücksichtigt werden, um relevante Produktvorschläge zusammen mit dem Geburtstagsrabatt zu präsentieren.
- Für Kunden, die in mehreren Systemen auftauchen, ist eine doppelte Unterdrückungslogik erforderlich, um das Senden mehrerer Geburtstagsnachrichten zu vermeiden.

## Werbekampagnen zum Spieltag

Targeting-Fans, um Tickets für ein bevorstehendes Spiel mit personalisierten Aktionen und Angeboten zu kaufen. Werbeaktionen am Spieltag fördern den Ticketverkauf, indem sie mit zeitnahem, ereignisspezifischem Messaging die richtige Zielgruppe erreichen.

### Auswirkung auf den Betrieb

Gezielte Game Day-Werbeaktionen verbessern die Ticket-Durchverkaufsraten, indem sie Fans mit relevanten Angeboten ansprechen, die auf ihren Team-Vorlieben, der bisherigen Anwesenheit und der Nähe zum Veranstaltungsort basieren.

### Implementieren

Verwenden Sie das [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)-Muster, um im Vorfeld bevorstehender Spiele Werbenachrichten an segmentierte Fan-Zielgruppen zu senden. Dies ist das richtige Muster, wenn ein Batch personalisierter Nachrichten planmäßig an ein vordefiniertes Zielgruppensegment gesendet werden muss.

### Technische Überlegungen

- Spielplandaten müssen vor jedem Trigger zur richtigen Vorlaufzeit in die Werbeaktionen integriert werden.
- Bei der Zielgruppensegmentierung sollten die Team-Affinität, die geografische Nähe und vergangene Anwesenheitsmuster berücksichtigt werden, um die Relevanz zu maximieren.
- Kunden, die bereits Tickets für das beworbene Spiel gekauft haben, sollten von Akquise-Nachrichten ausgeschlossen werden und erhalten stattdessen möglicherweise Upsell-Angebote für Upgrades oder Add-ons.

## Kampagnen zur Produktwerbung

Targeting von Kundinnen und Kunden zum Kauf von Produkten während einer laufenden Produktförderungskampagne. Werbekampagnen steigern den Umsatz, indem sie die richtigen Kunden mit zeitnahen Angeboten verbinden, die auf aktive Werbeaktionen abgestimmt sind.

### Auswirkung auf den Betrieb

Gezielte Produktförderkampagnen übertreffen breit angelegte Werbeaktionen, indem sie sich auf die Käufer konzentrieren, die am ehesten konvertieren, und so die Werbeverschwendung reduzieren und den Return on Marketing-Ausgaben verbessern.

### Implementieren

Verwenden Sie das [Aktivierungsmuster für Batch-](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) ausgehende Nachrichten), um während aktiver Kampagnenfenster Werbenachrichten an qualifizierte Zielgruppensegmente zu senden. Dies ist das richtige Muster, wenn ein geplanter Batch personalisierter Werbenachrichten während einer zeitgebundenen Kampagne eine definierte Zielgruppe erreichen muss.

### Technische Überlegungen

- Start- und Enddatum der Promotion müssen verwaltet werden, um sicherzustellen, dass Nachrichten nur während des aktiven Promotion-Fensters gesendet werden.
- Bei der Zielgruppensegmentierung sollten der Kaufverlauf, das Browser-Verhalten und die Produktaffinität genutzt werden, um Kunden anzusprechen, die mit größter Wahrscheinlichkeit mit den beworbenen Produkten interagieren.
- Die Frequenzlimitierung sollte angewendet werden, um Werbe-Ermüdung zu vermeiden, insbesondere wenn mehrere Kampagnen gleichzeitig ausgeführt werden.

## Warenkorbabbruch

Binden Sie Kunden, die ihren Warenkorb verlassen, erneut mit personalisierten Erinnerungen und Anreizen ein, um den Kauf abzuschließen. Die Wiederherstellung bei Warenkorbabbrüchen ist einer der Anwendungsfälle mit dem höchsten ROI im Einzelhandelsmarketing.

### Auswirkung auf den Betrieb

Warenkorbabbruch-Recovery-Kampagnen erzielen einen aussagekräftigen Prozentsatz des sonst verlorenen Umsatzes, indem sie Kunden zum Zeitpunkt der höchsten Kaufabsicht mit personalisierten Erinnerungen und Anreizen erneut kontaktieren.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöste Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster, um eine Wiederherstellungsmeldung Trigger, wenn ein Warenkorbabbruchs-Ereignis erkannt wird. Dies ist das richtige Muster, wenn als Reaktion auf ein Verhaltensereignis eine einzelne Echtzeitnachricht gesendet werden muss, z. B. wenn Artikel im Warenkorb gelassen werden, ohne den Checkout abzuschließen.

### Technische Überlegungen

- Die Erkennung eines Warenkorbabbruchs erfordert einen definierten Inaktivitätsschwellenwert (in der Regel 30-60 Minuten), um einen echten Abbruch von Kunden zu unterscheiden, die noch im Internet surfen.
- Der Inhalt des Warenkorbs muss in der Ereignis-Payload übergeben werden, um personalisierte Produkterinnerungen in der Wiederherstellungsmeldung zu ermöglichen.
- Kunden, die ihren Kauf zwischen dem Abbruchs-Ereignis und dem Versand der Nachricht abschließen, müssen unterdrückt werden, um irrelevante Nachrichten zu vermeiden.
