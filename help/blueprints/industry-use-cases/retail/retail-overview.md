---
title: Anwendungsfälle für den Einzelhandel
description: Erfahren Sie, wie Einzelhandelsunternehmen Adobe Experience Platform verwenden, um Einkaufserlebnisse zu personalisieren, Transaktionsabbrüche zu beheben und die Kundentreue zu steigern.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2590'
ht-degree: 0%

---


# Anwendungsfälle für den Einzelhandel

Einzelhandelsunternehmen verwenden Adobe Experience Platform, um Kundendaten aus Online-Shops, physischen Standorten und Treueprogrammen in einer einzigen Ansicht jedes Kunden zu vereinheitlichen. Diese Grundlage ermöglicht personalisierte Einkaufserlebnisse, zeitnahe Kontaktaufnahme, die entgangene Umsätze wieder hereinbringt, und Treuestrategien, die dafür sorgen, dass die Kunden immer wieder zurückkommen.

## Personalisierte Produktempfehlung

Zeigen Sie personalisierte Produktempfehlungen auf der Homepage, auf Kategorieseiten und Produktdetailseiten basierend auf dem Browser-Verlauf, dem Kaufverlauf und ähnlichem Kundenverhalten an. Wenn Käufer Produkte sehen, die auf ihre Interessen zugeschnitten sind, verbringen sie mehr Zeit mit der Erkundung und kaufen viel eher.

### Auswirkung auf den Betrieb

Einzelhändler verzeichnen in der Regel einen Anstieg der Clickthrough-Raten um 20-30 % und eine Verbesserung der Konversionsraten um 15-25 %, wenn sie personalisierte Empfehlungen anstelle statischer Produktlisten bereitstellen.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Dieser Ansatz nutzt KI-gesteuerte Empfehlungsmodelle, die kontinuierlich aus Kundeninteraktionen lernen, um für jede Person die relevantesten Produkte zu ermitteln.

### Technische Überlegungen

- Produktkatalogdaten müssen erfasst und auf dem neuesten Stand gehalten werden, einschließlich Produktattribute, Bilder, Preise und Verfügbarkeit, um sicherzustellen, dass die Empfehlungen widerspiegeln, was Kunden tatsächlich kaufen können.
- Verhaltenssignale wie Produktansichten, Ereignisse vom Typ „In den Warenkorb legen“ und Käufe müssen nahezu in Echtzeit fließen, damit die Empfehlungen innerhalb einer einzigen Browsersitzung aktuell bleiben.
- Empfehlungsmodelle erfordern eine Kaltstart-Strategie für neue Besucher, die keinen Browser-Verlauf haben und typischerweise auf Trend- oder Bestsellerprodukte zurückgreifen.
- Die Seitenladeleistung muss sorgfältig überwacht werden, da Personalisierungsaufrufe keine merkliche Latenz zum Einkaufserlebnis hinzufügen sollten.


## E-Mail-Wiederherstellung bei Transaktionsabbruch

Senden Sie automatisch personalisierte E-Mail-Erinnerungen an Kunden, die ihren Warenkorb verlassen haben, einschließlich der genauen hinterlassenen Artikel und relevanter Angebote, um die Fertigstellung zu fördern. Warenkorbabbrüche sind eine der größten Quellen für Umsatzeinbußen im Einzelhandel, und rechtzeitige Folgemaßnahmen können einen erheblichen Teil dieser Verkäufe zurückgewinnen.

### Auswirkung auf den Betrieb

Effektive Warenkorb-Wiederherstellungsprogramme bieten eine Warenkorb-Wiederherstellungsrate von 25-35 % und können einen zusätzlichen monatlichen Umsatz von 100.000 bis 500.000 US-Dollar generieren, je nach Speichervolumen.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf ein Echtzeit-Warenkorbabbruchs-Ereignis und sendet eine rechtzeitige Erinnerung, während die Kaufabsicht immer noch hoch ist.

### Technische Überlegungen

- Zur Erkennung eines Warenkorbabbruchs muss ein Schwellenwert für Inaktivität (in der Regel 30-60 Minuten) definiert werden, bevor die erste Erinnerung ausgelöst wird. So werden Nachrichten an Kunden vermieden, die noch aktiv einkaufen.
- E-Mail-Inhalte müssen aktuelle Produktbilder, Preise und Verfügbarkeit zum Versandzeitpunkt dynamisch aus dem Katalog abrufen, da sich Artikel zwischen Abbruch und Versand ausverkaufen oder den Preis ändern können.
- Die Regeln zur Frequenzlimitierung sollten verhindern, dass Kundinnen und Kunden innerhalb eines kurzen Zeitraums mehrere E-Mails zum Warenkorb mit Abbruch erhalten, insbesondere wenn sie den Warenkorb häufig verlassen.
- Einverständnis- und Unterdrückungslisten müssen vor dem Senden überprüft werden, und Kunden, die ihren Kauf über einen anderen Kanal abgeschlossen haben, sollten in Echtzeit ausgeschlossen werden.


## Inventarbasierte Dringlichkeitskampagnen

Trigger-Echtzeitwarnungen und -kampagnen, wenn der Produktbestand niedrig ist, wodurch eine Dringlichkeit entsteht und zum sofortigen Kauf ermutigt wird. Kunden, die sehen, dass nur noch wenige Artikel übrig sind, sind motiviert, schnell zu handeln, anstatt ihre Entscheidung zu verzögern.

### Auswirkung auf den Betrieb

Dringlichkeitskampagnen mit geringem Bestand führen in der Regel zu einem 30-40%igen Anstieg der Konversionen für vorgestellte Produkte und tragen gleichzeitig dazu bei, Überbestände zu reduzieren, indem der Verkauf von sich langsam bewegenden Artikeln beschleunigt wird.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf Inventarschwellenwertereignisse und aktiviert automatisch die Dringlichkeitsnachrichten, wenn die Lagerbestände unter definierte Grenzwerte fallen.

### Technische Überlegungen

- Inventar-Feeds müssen nahezu in Echtzeit in die Kundendatenplattform integriert werden, damit Dringlichkeitsnachrichten die tatsächlichen Lagerbestände und nicht veraltete Daten widerspiegeln.
- Schwellenwerte sollten für jede Produktkategorie konfiguriert werden, da sich ein Schwellenwert für „niedrige Lagerbestände“ bei einem großen Warenvolumen erheblich von einem für einen Luxusartikel unterscheidet.
- Die Werbebotschaft muss wahrheitsgetreu sein und den Verbraucherschutzbestimmungen entsprechen. Eine falsche Verknappung kann das Vertrauen der Marke schädigen und in bestimmten Märkten gegen die Werbestandards verstoßen.
- Die Messaging- und E-Mail-Kanäle vor Ort sollten so koordiniert werden, dass ein Kunde, der bereits gekauft hat, nicht weiterhin Benachrichtigungen zur Dringlichkeit für dasselbe Produkt erhält.


## Crosssell- und Upsell-Empfehlungen

Zeigen Sie relevante Crosssell- und Upsell-Produkte an der Kasse, in E-Mails und auf Produktseiten basierend auf Kaufmustern und Produktbeziehungen an. Der Vorschlag ergänzender oder Premium-Alternativen zum richtigen Zeitpunkt erhöht die Warenkorbgröße, ohne dass die Kunden selbst nach verwandten Artikeln suchen müssen.

### Auswirkung auf den Betrieb

Gut ausgeführte Crosssell- und Upsell-Strategien erhöhen den durchschnittlichen Bestellwert um 25- bis 75 USD und steigern den Umsatz pro Transaktion um 10-15 %.

### Implementieren

Verwenden Sie das Muster {0[&#128279;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)Offer Decisioning}. Dieser Ansatz verwendet eine zentralisierte Entscheidungslogik, um alle verfügbaren Angebote zu bewerten und die beste Crosssell- oder Upsell-Option für jeden Kunden und Kontext auszuwählen.

### Technische Überlegungen

- Produktbeziehungsdaten, einschließlich häufig erworbener Verknüpfungen und Aktualisierungspfade, müssen gepflegt und regelmäßig aktualisiert werden, um aktuelle Kaufmuster widerzuspiegeln.
- Die Ranking-Logik von Angeboten sollte die Spanne, Relevanz und Lagerbestände berücksichtigen, sodass die rentabelsten und verfügbaren Optionen zuerst angezeigt werden.
- Crosssell-Empfehlungen an der Kasse müssen schnell geladen werden und dürfen den Kauffluss nicht stören. Langsame oder aufdringliche Vorschläge können die Konversionsrate tatsächlich verringern.
- [!DNL Journey Optimizer] Entscheidungsregeln sollten Fallback-Angebote enthalten, damit jeder geeignete Kunde eine Empfehlung erhält, selbst wenn die am häufigsten platzierte Option nicht verfügbar ist.


## Neue Kunden-Begrüßungsreihe

Automatisieren Sie eine Willkommensreihe mit mehreren E-Mails für neue Kunden mit personalisierten Produktempfehlungen, Marken-storytelling und Sonderangeboten. Die ersten Interaktionen nach dem Beitritt eines Kunden prägen seine langfristige Beziehung zur Marke und machen diese Serie zu einem der wirkungsvollsten Programme, die ein retailer ausführen kann.

### Auswirkung auf den Betrieb

Eine gut durchdachte Willkommensserie steigert die Interaktionsrate bei neuen Kunden um 40-50 % und verbessert den Lebenszeitwert bedeutend, indem die Markenaffinität frühzeitig aufgebaut wird.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Dieser Multi-Touch-Nurture-Journey führt neue Kunden durch eine Reihe von Markeneinführungen, Produktentdeckungen und Incentive-Botschaften, die sich an ihr Engagement anpassen.

### Technische Überlegungen

- Der Journey-Einstiegs-Trigger muss Neukundenerstellungsereignisse aus allen Registrierungsquellen zuverlässig erfassen, einschließlich Web, Mobile App, Verkaufsstellen in Geschäften und Drittanbieter-Marketplaces.
- Warteschritte zwischen E-Mails sollten auf der Grundlage von Interaktionsdaten konfiguriert werden. Kunden, die sich öffnen und klicken, erhalten die nächste Nachricht möglicherweise früher, während weniger interaktive Kunden von mehr Abstand profitieren.
- Produktempfehlungen in Begrüßungs-E-Mails sollten widerspiegeln, was der Kunde bei seinem ersten Besuch angesehen oder gekauft hat, und nicht allgemeine Bestseller.
- Kunden, die während der Begrüßungsserie einen Kauf tätigen, sollten sich in einen Post-Purchase-Fluss verzweigen, anstatt weiterhin akquisitionsorientierte Nachrichten zu erhalten.


## Warnhinweise bei Preisverfall

Benachrichtigen Sie Kunden per E-Mail oder Push-Benachrichtigung, wenn Produkte auf ihrer Wunschliste oder zuvor angesehene Artikel im Preis fallen. Interessenten, die nicht eingekauft haben, reagieren sehr schnell auf Preisnachlässe, was dies zu einer der effizientesten Möglichkeiten macht, Überlegungen in Umsätze umzuwandeln.

### Auswirkung auf den Betrieb

Warnhinweise zu Preissenkungen generieren eine Konversionsrate von 20-30 % bei den Empfängern und erhöhen die Kundenzufriedenheit messbar, indem sie Kundinnen und Kunden das Gefühl geben, den besten Wert zu erhalten.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz reagiert auf Produktpreisänderungsereignisse und ordnet sie mit Kundeninteressensignalen ab, um zeitnahe Benachrichtigungen zu liefern.

### Technische Überlegungen

- Zur Erkennung von Preisänderungen müssen Sie die aktuellen Preise mit früheren Werten im Produktkatalog-Feed vergleichen und nur Warnhinweise auslösen, die aussagekräftige Reduzierungen und keine geringfügigen Schwankungen bewirken.
- Kundeninteressensignale (Hinzufügungen zur Wunschliste, Produktseitenansichten, auf Produktseiten verbrachte Zeit) müssen effizient gespeichert und mit potenziell Tausenden von täglichen Preisänderungen abgeglichen werden.
- Die Benachrichtigungen sollten den ursprünglichen Preis, den neuen Preis und den Einsparbetrag enthalten, um den Wert klar zu kommunizieren. Vage „preisreduzierte“ Meldungen führen zu weniger spezifischen Einsparhinweisen.
- [!DNL Real-Time Customer Data Platform] Segmente für preisbewusste Käufer können verwendet werden, um den Versand von Warnhinweisen zu priorisieren und den Nachrichtenton anzupassen.


## Erinnerungs-Wiederauffüllung

Senden automatisierter Erinnerungen an Kunden für Produkte, die sie regelmäßig kaufen, z. B. Abonnements und Verbrauchsmaterialien, um sie zu wiederholten Käufen zu ermutigen, bevor sie ausgehen. Proaktive Erinnerungen verringern die Wahrscheinlichkeit, dass Kunden zu einem Mitbewerber wechseln, nur weil sie die Neuanordnung vergessen haben.

### Auswirkung auf den Betrieb

Reminder-Programme für Nachschublieferungen bieten eine Wiederholungsrate von 30-40 % und verbessern die Kundenbindung erheblich, indem sie es Käufern erleichtern, die Produkte, auf die sie angewiesen sind, wieder aufzufüllen.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Diese wiederkehrende geplante Journey verwendet Prognosen zur Kaufhäufigkeit, um Erinnerungen zum optimalen Zeitpunkt zu senden, bevor ein Kunde wahrscheinlich eine Nachfüllung benötigt.

### Technische Überlegungen

- Bei der Berechnung der Kaufhäufigkeit müssen die unterschiedlichen Verbrauchsraten in den verschiedenen Produktkategorien berücksichtigt werden. Eine Erinnerung für Kaffee sollte mit einer anderen Kadenz eingehen als für Reinigungsmittel.
- Die Journey sollte den Zeitpunkt dynamisch anpassen, wenn ein Kunde früher oder später als prognostiziert neu bestellt, und die nächste Erinnerung auf der Grundlage aktualisierter Kaufdaten neu kalibrieren.
- Erinnerungen sollten einen direkten Link zur Neuanordnung oder eine Ein-Klick-Rückkaufoption enthalten, um die Reibung zu minimieren und die Konversion aus der Benachrichtigung zu maximieren.
- Kunden, die bereits über einen anderen Kanal (In-Store, Abonnement-Service) neu bestellt haben, müssen unterdrückt werden, um das Senden irrelevanter Erinnerungen zu vermeiden.


## Personalisierte Kategorieseiten

Kategorieseiten dynamisch personalisieren, um zunächst die relevantesten Produkte basierend auf den Vorlieben, früheren Käufen und dem Browserverhalten jedes Kunden anzuzeigen. Wenn Käufer oben auf der Seite Produkte sehen, die ihrem Geschmack entsprechen, entdecken sie, was sie schneller möchten, und konvertieren zu höheren Raten.

### Auswirkung auf den Betrieb

Personalisierte Kategorieseiten steigern die Interaktion mit Kategorieseiten um 25-35 % und verbessern die Produkterkennung deutlich, insbesondere bei Einzelhändlern mit großen Katalogen.

### Implementieren

Verwenden Sie das [Verhaltens-](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)). Bei diesem Ansatz werden Auswahlstrategien und Rangfolgemodelle verwendet, um Produkte auf Kategorieseiten basierend auf dem Profil jedes Besuchers und dem Echtzeitverhalten neu anzuordnen.

### Technische Überlegungen

- Das Produkt-Ranking muss schnell genug ausgeführt werden, um wahrgenommene Seitenladeverzögerungen zu vermeiden. Häufig ist eine Server-seitige Personalisierung oder Edge-basierte Entscheidungsfindung für Kategorieseiten mit Hunderten von Produkten erforderlich.
- Die Personalisierungslogik sollte individuelle Präferenzen mit Merchandising-Regeln kombinieren, um sicherzustellen, dass beworbene Produkte, Neuankömmlinge und saisonale Artikel weiterhin angemessene Sichtbarkeit erhalten.
- Es sollte eine Infrastruktur für A/B-Tests vorhanden sein, um die Umsatzauswirkungen von personalisierter Sortierung gegenüber standardmäßigen Merchandising-Regeln laufend zu messen.
- [!DNL Experience Platform] Web SDK-Implementierung muss Kategorieseiteninteraktionen (Bildlauftiefe, Produktklicks, Filternutzung) erfassen, um die Rangfolgemodelle kontinuierlich zu verfeinern.


## Follow-up-Kampagnen nach dem Kauf

Senden Sie E-Mails nach dem Kauf mit Tipps zur Produktpflege, zugehörigen Produktvorschlägen, Prüfungsanfragen und Informationen zum Treueprogramm. Der Zeitraum unmittelbar nach dem Kauf ist der Zeitraum, in dem Kunden die Marke am meisten interagieren, was sie zu einem idealen Fenster macht, um die Beziehung zu vertiefen und zukünftige Aktivitäten zu fördern.

### Auswirkung auf den Betrieb

Effektive Kampagnen nach dem Kauf erhöhen die Übermittlungsraten bei Überprüfungen um 15-20 % und führen zu einer Wiederholungsrate von 10-15 %. Dadurch werden einmalige Käufer zu loyalen Kunden.

### Implementieren

Verwenden Sie das [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)-Muster. Dieser mehrstufige Post-Purchase-Fluss verwendet eine Verzweigungslogik, um Folgenachrichten auf der Grundlage von Produkttyp, Kundensegment und Interaktion mit früheren E-Mails der Serie anzupassen.

### Technische Überlegungen

- Der Journey muss den Status der Bestellabwicklung berücksichtigen. Pflegetipps und Überprüfungsanfragen sollten erst nach der Lieferung des Produkts gesendet werden, nicht sofort nach dem Kauf.
- Produktspezifische Inhalte (Pflegehinweise, Benutzerhandbücher, Zubehörvorschläge) erfordern ein Content-Mapping-System, das jede Produktkategorie mit relevanten Folgematerialien verknüpft.
- Der Zeitpunkt der Überprüfungsanfrage sollte basierend auf der Produktkategorie optimiert werden. Elektronik benötigt möglicherweise eine längere Nutzungsdauer, bevor eine aussagekräftige Überprüfung durchgeführt wird, während Bekleidung kurz nach der Lieferung überprüft werden kann.
- Kunden, die eine Rückgabe oder einen Austausch einleiten, sollten automatisch aus dem standardmäßigen Post-Purchase-Fluss entfernt und zu einem Service-Wiederherstellungspfad weitergeleitet werden.


## Exklusive VIP-Kundenangebote

Identifizieren Sie hochwertige Kunden und bieten Sie exklusive Angebote, frühzeitigen Zugriff auf den Verkauf und personalisierte Einkaufserlebnisse, die ihre Loyalität belohnen. Eine Kundenbindung auf höchster Ebene ist wesentlich kostengünstiger, als neue Kunden zu gewinnen, und eine exklusive Behandlung stärkt die emotionale Verbindung, die sie am Leben erhält.

### Auswirkung auf den Betrieb

VIP-Programme generieren in der Regel eine Interaktionsrate von 50-70 % bei erstklassigen Kunden und verbessern den Kundenlebenszeitwert messbar, indem die Abwanderung unter den gewinnträchtigsten Segmenten reduziert wird.

### Implementieren

Verwenden Sie das [Cross-Channel Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)-Muster. Bei diesem Ansatz wird die Journey-Orchestrierung mit der Echtzeit-Entscheidungsfindung für die Angebotsauswahl kombiniert, sodass jeder VIP-Kunde über jeden Kanal hinweg das relevanteste Exklusivangebot erhält.

### Technische Überlegungen

- VIP-Segmentierungskriterien müssen mithilfe von Metriken für Neuigkeit, Häufigkeit und Geldwert klar definiert werden. Segmente sollten häufig genug aktualisiert werden, um Kunden zu erfassen, die sich kürzlich qualifiziert oder disqualifiziert haben.
- Exklusive Angebote müssen an der Einlösungsstelle (Web, App, Store) durchgesetzt werden, um zu verhindern, dass Nicht-VIP-Kunden auf sie zugreifen. Dies erfordert die Integration in Werbe- und Preissysteme.
- Die Kanalpräferenzen variieren erheblich zwischen hochwertigen Kundinnen und Kunden. Einige bevorzugen E-Mails, andere reagieren auf App-Benachrichtigungen oder Briefpost, sodass die Journey Versandkanäle auf der Grundlage früherer Interaktionen anpassen sollte.
- [!DNL Journey Optimizer] Entscheidungsfindung muss kanalübergreifend koordiniert werden, um zu verhindern, dass ein VIP-Kunde dasselbe Angebot gleichzeitig per E-Mail, Push-Benachrichtigung und SMS erhält.


## Nicht vorrätige Benachrichtigungen

Kunden erlauben, sich für Benachrichtigungen zu registrieren, wenn nicht vorrätige Produkte verfügbar werden, und sie dann automatisch per E-Mail oder Textnachricht benachrichtigen. Die Erfassung der Nachfrage nach nicht verfügbaren Produkten verhindert Umsatzeinbußen und gibt den Kunden einen Grund, zum Geschäft zurückzukehren, anstatt bei einem Wettbewerber zu kaufen.

### Auswirkung auf den Betrieb

Backin-Stock-Benachrichtigungen erreichen eine Konversionsrate von 40-50 % unter den Abonnenten und verringern bedeutend Umsatzverluste für nachfrageseitige Produkte, die vorübergehende Lagerbestände aufweisen.

### Implementieren

Verwenden Sie das [Ereignis-ausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)-Muster. Dieser Ansatz ermöglicht den Trigger von Benachrichtigungen zu Back-in-Stock-Ereignissen, indem Inventaraktualisierungen mit der Anmeldung bei Kundenbenachrichtigungen abgeglichen werden, um zeitnahe Warnhinweise zu liefern.

### Technische Überlegungen

- Bei der Bestandsüberwachung müssen Wiederauffüllungsereignisse schnell erkannt werden. Verzögerungen von nur wenigen Stunden können dazu führen, dass das Produkt erneut ausverkauft wird, bevor benachrichtigte Kunden eine Chance auf den Kauf haben.
- Wenn ein beliebtes Produkt in begrenzter Menge wieder vorrätig ist, sollten Benachrichtigungen nach dem Anmeldedatum gestaffelt oder priorisiert sein, um zu vermeiden, dass Warnhinweise an mehr Kunden gesendet werden, als der verfügbare Bestand bereitstellen kann.
- Der Anmeldungsmechanismus für Benachrichtigungen muss die Kanalpräferenz (E-Mail oder Textnachricht) erfassen und die Opt-in-Anforderungen für jeden Kanal erfüllen, insbesondere für SMS.
- [!DNL Real-Time Customer Data Platform] Profilattribute sollten verfolgen, welche Produkte jeder Kunde beobachtet, damit doppelte Benachrichtigungen verhindert werden, wenn dasselbe Produkt mehrmals wiederhergestellt wird.


## Social Proof Personalization

Zeigen Sie personalisierte Social-Proof-Nachrichten an, einschließlich Bewertungen, Bewertungen und Empfehlungen von „Kunden, die dies gekauft haben, haben auch gekauft“, die auf dem Profil und den Präferenzen jedes Kunden basieren. Durch die Anpassung des sozialen Beweises an die Erfahrungen ähnlicher Kunden wird Vertrauen effektiver aufgebaut als durch Bewertungen allein.

### Auswirkung auf den Betrieb

Personalisierter sozialer Testversand erhöht die Konversionsraten um 10-15 % und verbessert das Kundenvertrauen, insbesondere bei Erstkäufern und teureren Produkten, bei denen die Kaufzurückhaltung am größten ist.

### Implementieren

Verwenden Sie das [Web-/App-Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)Muster für bekannte Besucher. Dieser Ansatz personalisiert Web-Inhalte für identifizierte Besucher und wählt die relevantesten Reviews und Social-Proof-Elemente basierend auf dem Kundenprofil, den Voreinstellungen und dem Browserkontext aus.

### Technische Überlegungen

- Überprüfungs- und Bewertungsdaten müssen nach Kundenattributen strukturiert und getaggt sein (z. B. Kaufkontext, Kundensegment und Produktanwendungsfall), um eine aussagekräftige Filterung und Personalisierung zu ermöglichen.
- Elemente des sozialen Testversands sollten asynchron geladen werden, um zu vermeiden, dass das Rendern der Haupt-Produktseite blockiert wird, da Überprüfungsdaten von einer Prüfplattform eines Drittanbieters mit variablen Antwortzeiten stammen können.
- Datenschutzbestimmungen verlangen, dass Kundendaten, die zum Abgleichen von Bewertungen mit Besuchern verwendet werden, gemäß den Einverständnisvoreinstellungen verarbeitet werden. Die Anzeige von Inhalten des Typs „Kunden wie Sie“ impliziert Profiling, das möglicherweise offen gelegt werden muss.
- [!DNL Experience Platform] Zielgruppenzugehörigkeit kann verwendet werden, um auszuwählen, welche Rezensionen hervorgehoben werden sollen, wobei Outdoor-Enthusiasten-Rezensionen von anderen Outdoor-Käufern anstelle von generischen, top bewerteten Rezensionen angezeigt werden.
