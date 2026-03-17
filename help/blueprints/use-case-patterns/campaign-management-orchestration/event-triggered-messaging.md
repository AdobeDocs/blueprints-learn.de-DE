---
title: Ereignisausgelöstes Messaging
description: Erfahren Sie, wie Sie kontextbezogene Echtzeit-Nachrichten als Reaktion auf Verhaltens- oder Systemereignisse versenden können.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '9039'
ht-degree: 1%

---


# Ereignisausgelöstes Messaging

Dieses Handbuch bietet einen umfassenden Implementierungs-Blueprint für ereignisgesteuertes Messaging mit [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP). Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die als Reaktion auf Verhaltens- oder Systemereignisse kontextbezogene Echtzeit-Nachrichten bereitstellen müssen.

Verwenden Sie dieses Handbuch, um zu verstehen, was konfiguriert werden soll, wo Implementierungsoptionen vorhanden sind und welche Kompromisse die einzelnen Entscheidungen antreiben.

Das Handbuch behandelt den gesamten Lebenszyklus von der Ereignisaufnahme und Journey-Erstellung über den Nachrichtenversand bis hin zum Leistungs-Reporting und bietet detaillierte Entscheidungshandbücher zu drei verschiedenen Implementierungsoptionen.

## Anwendungsfall - Übersicht

Ereignisausgelöstes Messaging liefert eine kontextuelle Nachricht als Reaktion auf ein Echtzeit-Verhaltens- oder Systemereignis. Im Gegensatz zur Aktivierung ausgehender Batch-Nachrichten, die zu einem bestimmten Zeitpunkt an eine vorausgewertete Audience gesendet wird, überwacht dieses Muster ein qualifizierendes Ereignis, z. B. einen Warenkorbabbruch, eine Durchsuchsitzung, eine Formularübermittlung oder eine Systemstatusänderung, und gibt das auslösende Profil sofort auf eine Journey ein, die die Bedingungen auswertet und eine Nachricht sendet.

Das Muster basiert auf dem Echtzeit-Ereignis-Streaming in AEP (über Web SDK, Mobile SDK oder serverseitige API), einer Journey mit einem unitären Ereigniseintrag in AJO und einer Bedingungsauswertungslogik, die bestimmt, ob und was gesendet wird. Die Nachricht wird normalerweise innerhalb von Minuten nach dem auslösenden Ereignis gesendet, was dieses Muster ideal für zeitabhängige, kontextuell relevante Nachrichten macht.

Unternehmen verwenden dieses Muster, um auf Kundenaktionen in Echtzeit zu reagieren, wodurch die Relevanz steigt und im Vergleich zur geplanten Batch-Kommunikation höhere Interaktions- und Konversionsraten erzielt werden. Häufige Szenarien sind die Wiederherstellung bei Transaktionsabbruch, die Nachverfolgung nach dem Kauf, Willkommensnachrichten nach der Registrierung und zeitkritische Benachrichtigungen wie Zahlungsausfälle oder Warnhinweise bei Preisrückgängen.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Wiederherstellen von Transaktionsabbrüchen und Journey](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Erneutes Ansprechen von Benutzern, die während des Kaufs, der Bewerbung oder der Registrierung abgebrochen sind, durch zeitnahe, personalisierte Folgemaßnahmen.

| KPIs |
| --- |
| Konversionsraten, inkrementeller Umsatz, Interaktion |

**[Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbessern Sie den Prozentsatz der Besucher und Interessenten, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen.

| KPIs |
| --- |
| Konversionsraten, Lead-Konversion, Kosten pro Lead |

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.

| KPIs |
| --- |
| Interaktion, Konversionsraten, Kundenzufriedenheit (CSAT) |

**[Verbessern des Kunden-Onboarding](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Verkürzen Sie die Amortisierungszeit für neue Kunden mit optimierten, personalisierten Willkommens- und Aktivierungs-Journey.

| KPIs |
| --- |
| Interaktion, Kundenbindung, Konversionsraten |

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie ereignisgesteuertes Messaging auf verschiedene Geschäftskontexte angewendet werden kann.

- **E-Mail oder SMS zu Warenkorbabbruch** - Senden Sie eine Erinnerungsnachricht, wenn ein Kunde Artikel zu seinem Warenkorb hinzufügt, den Kauf jedoch nicht innerhalb eines bestimmten Zeitfensters abschließt
- **Follow-up bei Abbruch durchsuchen** - Erneutes Ansprechen von Besucherinnen und Besuchern, die Produkte oder Inhalte angesehen, aber keine Konversionsaktion durchgeführt haben
- **Dankeschön oder Crosssell nach dem Kauf** — Geben Sie sofort nach einem Kaufereignis eine Bestätigung und eine Crosssell-Empfehlung ab
- **Testablauf-Erinnerung** - Benachrichtigen Sie Benutzer, die sich dem Ende einer kostenlosen Testversion nähern, mit einer Nachricht zur Verlängerung oder Konversion
- **Willkommensnachricht nach der Registrierung** - Senden Sie eine sofortige Onboarding-Nachricht, wenn sich ein neuer Benutzer registriert oder ein Konto erstellt
- **Formularübermittlungsbestätigung** - Bestätigt Formularübermittlungen (Kontaktanfragen, Bewerbungen, Registrierungen) mit einer kontextuellen Bestätigung
- **Benachrichtigung bei Zahlungsausfällen** — Benachrichtigung der Kunden, wenn eine wiederkehrende Zahlung fehlschlägt, und Aufforderung, die Zahlungsinformationen zu aktualisieren
- **App-Deinstallation einer Win-Back-Push-Benachrichtigung** - Trigger erhält eine Win-back-Nachricht, wenn ein Benutzer eine Mobile App deinstalliert
- **Buchung oder Terminbestätigung** — Senden Sie sofort eine Bestätigung, nachdem eine Buchung, Reservierung oder ein Termin geplant ist
- **Warnhinweis bei Preisverfall für Artikel auf der Wunschliste** - Benachrichtigen Sie Kunden, wenn ein Produkt auf ihrer Wunschliste im Preis sinkt

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität von ereignisgesteuerten Messaging-Implementierungen gemessen werden.

| KPI | Beschreibung | Messung |
| --- | --- | --- |
| Konversionsrate | Prozentsatz der ausgelösten Nachrichtenempfänger, die die gewünschte Aktion abgeschlossen haben (Kauf, Anmeldung, Verlängerung) | Konversionen/Zugestellte Nachrichten * 100 |
| Inkrementeller Umsatz | Zusätzliche Einnahmen, die durch ereignisgesteuerte Nachrichten im Vergleich zu Kontrollgruppen ohne Versand erzielt werden können | Umsatz aus ausgelösten Sendungen - Baseline der Kontrollgruppe |
| Öffnungsrate | Prozentsatz der zugestellten Nachrichten, die von Empfängern geöffnet wurden | Öffnungen/Geliefert * 100 |
| Clickthrough-Rate (CTR) | Prozentsatz der zugestellten Nachrichten, die mindestens einen Klick generiert haben | Klicks/Zugestellt * 100 |
| Zeit bis zur Konversion | Durchschnittliche Zeit zwischen Nachrichtenversand und Konversionsereignis | AVG(Konversions-Zeitstempel - Versand-Zeitstempel) |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die die Journey betreten und den Nachrichtenversand-Schritt erreichen (nicht durch Bedingungen oder Ausstiege verworfen) | Profile, die den Versand erreichen / Profile, die in den Journey eintreten * 100 |
| Unterdrückungsrate der Nachricht | Prozentsatz der qualifizierten Profile, die aufgrund von Häufigkeitsbegrenzungen, Einverständnis oder Bedingungsauswertung unterdrückt wurden | Unterdrückte Profile/Gesamtzahl der qualifizierten Profile * 100 |
| Bounce-Rate | Prozentsatz der Nachrichten, die aufgrund von Hard- oder Softbounces nicht zugestellt werden konnten | Bounces/Gesendet * 100 |

## Anwendungsfallmuster

In diesem Abschnitt werden das Kernmuster und die Funktionskette beschrieben, die das ereignisgesteuerte Messaging antreiben.

**Ereignisausgelöstes Messaging**

Achten Sie auf ein Echtzeit-Verhaltens- oder Systemereignis und senden Sie dann eine kontextuelle Nachricht an das auslösende Profil.

**Funktionskette:** Ereignisaufnahme > Journey-Eintrag > Bedingungsauswertung > Nachrichtenversand > Berichterstellung

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer](AJO)** - Journey-Orchestrierung mit unitärer Ereigniseingabe, Bedingungsauswertung, Warteschritten, Nachrichtenbearbeitung, Kanalkonfiguration, Frequenzverwaltung und Versandberichten
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** - Zielgruppenbewertung für bedingungsbasierte Filterung innerhalb von Journeys, Durchsetzung von Einverständnis und Governance, Profilanreicherung
- **[!DNL Adobe Experience Platform](AEP)** - Echtzeit-Ereignisaufnahme über Web SDK, Mobile SDK oder Server-seitige API; Datenmodellierung; Identitätsauflösung; Edge Network

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit aktiver Kanalkonfiguration bereitgestellt. Dem Implementierungsteam zugewiesene Berechtigungen zum Erstellen und Veröffentlichen von Journey. Benutzerrollen, die für die Journey-Verwaltung, Inhaltserstellung und Kanalverwaltung konfiguriert sind. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Ein XDM-ExperienceEvent-Schema muss das auslösende Ereignis mit allen kontextuellen Feldern erfassen, die für die Bedingungsauswertung und Nachrichtenpersonalisierung erforderlich sind (z. B. `commerce.productListAdds` für Warenkorbereignisse, Produktdetails, Warenkorbwert). Das Schema muss für das Echtzeit-Kundenprofil aktiviert sein. Ein entsprechender Datensatz muss erstellt und für das Profil aktiviert werden. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Erforderlich | Das Echtzeit-Ereignis-Streaming muss konfiguriert werden - Web SDK für Web-Ereignisse, Mobile SDK für App-Ereignisse oder Edge Network Server-API für Systemereignisse. Ein Datenstrom muss mit aktivierten AEP- und AJO-Services konfiguriert werden, sodass Ereignisse an den richtigen Datensatz weitergeleitet werden. Dies ist eine kritische Abhängigkeit, da das Muster von der Echtzeit-Ereignisaufnahme abhängt. | [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identitäts- und Profilkonfiguration | Erforderlich | Das auslösende Ereignis muss einer bekannten Identität zugeordnet sein (E-Mail, CRM-ID oder authentifizierte Sitzung), damit die Journey das Profil auflösen und die Nachricht versenden kann. Für die vom auslösenden Ereignis verwendeten Kennungen müssen Identity-Namespaces vorhanden sein. Anonyme Ereignisse erfordern eine Identitätszuordnung über das Identitätsdiagramm, bevor eine Nachricht gesendet werden kann. Es muss eine Zusammenführungsrichtlinie konfiguriert werden. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Empfohlen | Während dies für ereignisgesteuerte Journey nicht unbedingt erforderlich ist (der Eintritt ist ereignisbasiert, nicht zielgruppenbasiert), können Zielgruppensegmente zur Bedingungsbewertung innerhalb der Journey verwendet werden (z. B. nur senden, wenn das Profil einem „hochwertigen Kunden“-Segment angehört, oder unterdrücken, wenn das Profil einem „kürzlich kontaktierten“ Segment angehört). Eine Streaming-Auswertung wird für Prüfungen der Echtzeit-Segmentzugehörigkeit in Journey empfohlen. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie die Anzahl der Warenkorbabbrüche, Tage seit dem letzten Kauf, der durchschnittliche Bestellwert und die Gesamtkaufsdauer verbessern die Bewertung der Bedingung und die Personalisierung innerhalb der ausgelösten Journey. Diese Verhaltens-Aggregate ermöglichen eine präzisere Zielgruppenbestimmung (z. B. Unterscheidung von Personen, die beim ersten Mal auf die Behandlung verzichten, von Personen, die wiederholt auf die Behandlung verzichten). | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Ablauf von Ereignisdaten sollte für vorübergehende Verhaltensereignisse (Seitenansichten, Suchen, Klicks) konfiguriert werden, um Speicherkosten und Compliance zu verwalten. Felder im Einverständnisschema müssen während des Nachrichtenversands für die kanalspezifische Opt-in-/Opt-out-Durchsetzung vorhanden sein. | [Erweiterte Übersicht über das Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für Ereignis- und Profilfelder stellen eine konforme Personalisierung sicher. Wenn ausgelöste Nachrichten personalisierte Inhalte mithilfe von personenbezogenen Daten oder Verhaltensdaten enthalten, sollten Datennutzungskennzeichnungen und Governance-Richtlinien überprüft werden, um eine nicht autorisierte Datennutzung im Nachrichteninhalt zu verhindern. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Die Überwachung der Journey-Ausführung ist Teil der Reporting-Phase. Konfigurieren Sie außerdem Warnhinweise für Fehler bei der Ereignisaufnahme oder Verzögerungen bei der Journey-Verarbeitung, um Pipeline-Probleme zu erkennen, die das Senden ausgelöster Nachrichten verhindern würden. | [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Journey-Leistungsberichte werden in der Reporting-Phase behandelt. Um die Effektivität ausgelöster Nachrichten kanalübergreifend und im Zeitverlauf zu analysieren, konfigurieren Sie CJA-Verbindungen und -Arbeitsbereiche, um die Konversionszuordnung, die Konversionszeit und die Kanalleistung zu analysieren. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Journey Orchestration | Erstellung und Konfiguration von Journey | Erstellen Sie eine Journey mit einem unitären Ereigniseintrag, konfigurieren Sie das qualifizierende Ereignis, fügen Sie Bedingungsknoten hinzu, warten Sie Schritte, Nachrichtenaktionen, Beendigungskriterien und Wiedereintrittsregeln |
| Kanalkonfiguration | Einrichten der Kanaloberfläche | Konfigurieren oder validieren Sie Kanaloberflächen (E-Mail, SMS, Push-Benachrichtigung) einschließlich Subdomain-Zuweisung, IP-Pools, Absendereinstellungen und Verwaltung der Unterdrückungsliste |
| Verfassen von Nachrichten | Erstellung des Nachrichteninhalts | Erstellen von kontextuellen Nachrichteninhalten mit ereignisgesteuerter Personalisierung, bedingten Inhaltsbausteinen und wiederverwendbaren Fragmenten |
| Häufigkeits- und Geschäftsregeln | Erstellung und Konfiguration von Journey (Option C) | Konfigurieren Sie Häufigkeitsbegrenzungen und Deduplizierungsregeln, um Übernachrichten aus Ereignisquellen mit hoher Häufigkeit zu verhindern |
| Konflikt- und Prioritätenmanagement | Erstellung und Konfiguration von Journey | Prioritätswerte zuweisen und Konflikterkennung für Journey konfigurieren, die um dieselben Profile konkurrieren |
| Reporting und Leistungsanalyse | Reporting und Überwachung | Überwachen von Journey-Versandmetriken über Live- und Verlaufsberichte; Zugreifen auf programmgesteuerte Leistungsdaten über CJA |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Grundlegende Einrichtung (F5) | Auswerten von Zielgruppensegmenten, die für die bedingungsbasierte Filterung innerhalb der Journey verwendet werden (z. B. hochwertige Kundensegmente, Unterdrückungssegmente) |
| Durchsetzung von Einverständnis und Governance | Grundlegende Einrichtung (S2/S3) | Erzwingen von Einverständnisvoreinstellungen und Datennutzungs-Governance-Richtlinien während des Nachrichtenversands, um eine konforme Kommunikation zu gewährleisten |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [ ] AJO-Sandbox mit Journey-Erstellungs- und Veröffentlichungsberechtigungen (F1)
- [ ] XDM ExperienceEvent-Schema, das das auslösende Ereignis mit kontextuellen Feldern erfasst, aktiviert für das Echtzeit-Kundenprofil (F2)
- [ ] Echtzeit-Ereignis-Streaming, das über die Web-SDK-, Mobile-SDK- oder Edge Network-Server-API mit einem Datenstrom konfiguriert wird, der Ereignisse an den richtigen AEP-Datensatz weiterleitet (F3)
- [ ] Identity-Namespaces, die für die Kennungen des auslösenden Ereignisses konfiguriert sind; Regeln zur Identitätsverknüpfung vorhanden (F4)
- [ ] Kanaloberfläche (E-Mail, SMS oder Push), die mit einem erfolgreichen Testversand konfiguriert und validiert wurde
- [ ] Nachrichteninhalte, die mit Beispielprofilen verfasst, geprüft und getestet wurden
- [ ] Einverständnisfelder werden in Profilen für den Zielkanal ausgefüllt (z. B. `consents.marketing.email.val`)
- [ ] Bei Verwendung der bedingungsbasierten Zielgruppenfilterung (Option B/C) werden für das Streaming ausgewertete Zielgruppensegmente definiert und aktiv ausgewertet

## Implementierungsoptionen

In diesem Abschnitt werden drei Implementierungsoptionen für ereignisausgelöstes Messaging beschrieben. Jede Option baut auf der vorherigen auf und fügt zusätzliche Funktionen hinzu.

### Option A: Einfache, durch ein Ereignis ausgelöste Nachricht

**Am besten geeignet für:** Sofortige Antworten mit einer Nachricht, bei denen keine Verzögerung oder bedingte Logik erforderlich ist - Bestellbestätigung, Begrüßungs-E-Mail, Formularsendebestätigung, Buchungsbestätigung.

**Funktionsweise:**

Der Journey überwacht über einen unitären Ereigniseinstiegsknoten ein qualifizierendes Ereignis. Wenn das Ereignis eingeht, gelangt das Profil auf die Journey, durchläuft eine minimale Bedingungsauswertung (Einverständnisprüfung, Profilexistenzüberprüfung) und erhält über den konfigurierten Kanalaktionsknoten sofort eine einzige Nachricht.

Dies ist die einfachste Implementierungsvariante. Die Journey-Arbeitsfläche enthält einen Ereigniseinstiegsknoten, einen optionalen Bedingungsknoten für grundlegende Eignungsprüfungen, einen einzelnen Nachrichtenaktionsknoten und einen Endknoten. Es gibt keine Warteschritte, keine komplexen Verzweigungen und keine Konversionsprüfungen. Die Nachricht wird normalerweise innerhalb von Sekunden bis Minuten nach dem auslösenden Ereignis gesendet.

Ereignisdaten aus dem auslösenden Ereignis (Produktname, Bestellsumme, Formulardetails) können über kontextuelle Attribute im Personalisierungseditor für die Personalisierung von Nachrichten verwendet werden. Dieser Ansatz maximiert die Geschwindigkeit der Bereitstellung und minimiert die Komplexität des Journey.

**Wichtige Aspekte:**

- Die Nachricht wird unabhängig davon gesendet, ob der Kunde nach dem Ereignis selbst konvertiert (keine Konversionsprüfung)
- Am besten geeignet für Ereignisse, die von Natur aus eine sofortige Reaktion rechtfertigen (Bestätigungen, Bestätigungen)
- Die Regeln für den erneuten Eintritt sollten sorgfältig konfiguriert werden. Bei Bestätigungsnachrichten müssen Sie den erneuten Eintritt erlauben, sodass jedes Ereignis eine Nachricht erzeugt. Bei Begrüßungsnachrichten müssen Sie den erneuten Eintritt verhindern

**Vorteile:**

- Schnellste Zeit bis zum Versand (Sekunden bis Minuten nach dem Ereignis)
- Einfachste Journey-Konfiguration mit minimalen beweglichen Teilen
- Geringstes Risiko für Journey-Fehler oder steckengebliebene Profile
- Einfaches Testen und Verwalten

**Einschränkungen:**

- Keine Möglichkeit, vor dem Senden zu überprüfen, ob der Kunde selbst konvertiert hat
- Zeitverzögerte Bedingungslogik kann nicht integriert werden
- Kann unnötige Nachrichten generieren, wenn das Ereignis häufig ohne Häufigkeits-Governance auftritt

**Experience League:**

- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### Option B: Durch ein bedingtes Ereignis ausgelöste Nachricht mit Wartezeit

**Am besten geeignet für:** Verzögerte, bedingte Antworten, bei denen der Kunde vor Erhalt der Nachricht Zeit zur Selbstkonvertierung haben sollte - Warenkorbabbruch (1-4 Stunden warten, dann überprüfen, ob der Warenkorb noch immer abgebrochen ist), Durchsuchen des Abbruchs (24 Stunden warten, überprüfen, ob der Kauf getätigt wurde), Testablauf (warten, bis das Ablaufdatum näher rückt).

**Funktionsweise:**

Die Journey überwacht ein Qualifizierungsereignis, tritt in das Profil ein und führt eine Wartezeit ein, bevor die Bedingungen bewertet werden. Nach der Wartezeit prüft ein Bedingungsknoten, ob der Kunde sich selbst konvertiert hat (z. B. den Kauf abgeschlossen, das Abonnement verlängert hat) oder ob der ursprüngliche Kontext noch gültig ist. Nur wenn die Bedingung erfüllt ist (z. B. wenn der Warenkorb noch immer verlassen ist), fährt die Journey mit dem Nachrichtenversand fort.

Die Journey-Arbeitsfläche enthält einen Ereigniseinstiegsknoten, einen Warteknoten (konfigurierbare Dauer oder spezifisches Datum/Uhrzeit), einen Bedingungsknoten, der auf ein Konversionsereignis oder eine Profilstatusänderung prüft, Verzweigungspfade (Senden-Nachricht vs. Beenden ohne Senden), einen Nachrichtenaktionsknoten auf dem Qualifizierungspfad und einen Endknoten auf jeder Verzweigung. Beendigungskriterien können so konfiguriert werden, dass Profile automatisch vom Journey entfernt werden, wenn das Konversionsereignis während der Wartezeit eintritt, sodass keine explizite Bedingungsprüfung erforderlich ist.

Dieser Ansatz reduziert unnötige Nachrichten, da Kunden Zeit zur Selbstkonvertierung haben, das Kundenerlebnis verbessert wird und die wahrgenommene Relevanz der gesendeten Nachrichten zunimmt.

**Wichtige Aspekte:**

- Die Wartezeit wirkt sich erheblich auf die Konversionsraten aus. Kürzere Wartezeiten (1-2 Stunden) erzeugen eine höhere Dringlichkeit, aber unnötigere Sendungen. Längere Wartezeiten (24-48 Stunden) verringern das Volumen, verpassen jedoch möglicherweise das Relevanzfenster
- Die Bedingungsauswertung erfordert, dass das Konversionsereignis in AEP erfasst und mit derselben Profilidentität verknüpft wird
- Beendigungskriterien bieten eine sauberere Alternative zu expliziten Bedingungsknoten für die Konversionsprüfung
- Regeln für den erneuten Eintritt müssen die Wartezeit berücksichtigen - ein Profil sollte die Journey nicht erneut eingeben, während es bereits wartet

**Vorteile:**

- Reduziert unnötiges Messaging durch Prüfung auf Selbstkonvertierung
- Höhere Qualität und Relevanz der Kommunikation
- Unterstützt zeitkritische Anwendungsfälle mit konfigurierbaren Verzögerungsfenstern
- Beendigungskriterien ermöglichen die automatische Journey-Entfernung bei der Konvertierung

**Einschränkungen:**

- Erhöhte Journey-Komplexität mit Warte- und Bedingungsknoten
- Profile belegen Journey-Slots während Wartezeiten (abhängig von einer 91-tägigen Journey-Zeitüberschreitung)
- Erfordert, dass das Konversionsereignis innerhalb des Wartefensters in AEP aufgenommen wird, um eine genaue Bedingungsauswertung zu ermöglichen
- Längere Zeit bis zur Lieferung im Vergleich zu Option A

**Experience League:**

- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Option C: Ereignisgesteuert mit Frequency Governance

**Am besten geeignet für:** Häufige Ereignisquellen, bei denen die Nachrichtenermüdung ein Problem darstellt - Seitenansichten, Produktansichten, Suchabfragen, Hinzufügungen zum wiederholten Warenkorb. Kann als Überlagerung auf Option A oder Option B angewendet werden.

**Funktionsweise:**

Diese Option fügt entweder Option A oder Option B eine Frequenzverwaltung hinzu, um Übermeldungen zu verhindern. Bei sehr häufigen Verhaltensereignissen (z. B. Produktansichten oder wiederholten Hinzufügungen zum Warenkorb) kann der Journey innerhalb eines kurzen Zeitraums mehrmals Trigger werden. Ohne Häufigkeits-Governance kann ein Profil doppelte oder übermäßige Nachrichten erhalten.

Die Frequenzverwaltung wird durch zwei sich ergänzende Mechanismen implementiert: AJO-Geschäftsregeln (Häufigkeitsbegrenzungen), die begrenzen, wie viele Nachrichten ein Profil pro Kanal und Zeitraum erhält, und Regeln für den erneuten Eintritt auf Journey-Ebene, die eine Abklingzeit definieren, bevor ein Profil erneut auf dieselbe Journey zugreifen kann. Geschäftsregeln werden auf Organisationsebene angewendet und setzen Obergrenzen für alle Kampagnen und Journey durch (z. B. maximal 3 E-Mails pro Woche), während die Abklingzeit für den erneuten Eintritt auf der Ebene der einzelnen Journey erfolgt (z. B. kann ein Profil diese Journey nicht innerhalb von 72 Stunden nach dem letzten Eintrag erneut aufrufen).

Darüber hinaus kann die Konflikt- und Prioritätsverwaltung so konfiguriert werden, dass der ausgelösten Journey Prioritätswerte zugewiesen werden. So wird sichergestellt, dass die Kommunikation mit der höchsten Priorität gewinnt, wenn mehrere Journey oder Kampagnen um dasselbe Profil konkurrieren.

**Wichtige Aspekte:**

- Häufigkeitsbegrenzungen müssen ein Gleichgewicht zwischen der Vermeidung von Ermüdung und der Sicherstellung, dass wichtige ausgelöste Nachrichten zugestellt werden, herstellen
- Kanalspezifische Begrenzungen werden empfohlen - E-Mail, SMS und Push-Benachrichtigungen haben unterschiedliche Ermüdungsschwellen
- Die Abklingzeit für den erneuten Eintritt von Journey und die Häufigkeitsbegrenzungen auf Organisationsebene funktionieren zusammen. Beide sollten konfiguriert werden
- Prioritätswerte bestimmen, welche Kommunikation gewinnt, wenn Obergrenzen erreicht werden - Journey mit höherer Priorität sollten höhere Werte zugewiesen werden

**Vorteile:**

- Verhindert das Ermüden von Nachrichten durch hochfrequente Ereignisquellen
- Aufrechterhaltung der Markenreputation und der Kundenzufriedenheit
- Obergrenzen auf Organisationsebene bieten ein Sicherheitsnetz für alle Kampagnen und Journey
- Mit der Prioritätsbewertung wird sichergestellt, dass die wichtigsten Nachrichten gesendet werden, wenn die Begrenzungen erreicht sind

**Einschränkungen:**

- Einige qualifizierte Profile werden unterdrückt, wobei möglicherweise relevante Nachrichten fehlen.
- Die Konfiguration der Häufigkeitsbegrenzung erhöht die administrative Komplexität
- Begrenzungen können unerwartet mit anderen aktiven Kampagnen und Journey interagieren, die denselben Kanal nutzen
- Fortlaufende Überwachung und Anpassung im Zuge von Änderungen am Messaging-Portfolio erforderlich

**Experience League:**

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: Einfaches, ereignisgesteuertes Ereignis | Option B: Bedingt mit Warten | Option C: Frequenzverwaltung |
| --- | --- | --- | --- |
| Am besten geeignet für | Sofortige Bestätigungen, Bestätigungen | Abbruch der Wiedereinziehung, verzögerte bedingte Reaktionen | Häufige Ereignisquellen, Multi-Journey-Umgebungen |
| Komplexität | Niedrig | Mittel | Medium-Hoch (fügt zu A oder B hinzu) |
| Nachrichtenlatenz | Sekunden bis Minuten | Minuten bis Stunden/Tage (konfigurierbare Wartezeit) | Gleich wie die zugrunde liegende Option (A oder B) |
| Konversionsprüfung | Nein | Ja (über Bedingungs- oder Ausstiegskriterien) | Hängt von der zugrunde liegenden Option ab |
| Frequenzschutz | Keine (außer in Kombination mit C) | Keine (außer in Kombination mit C) | Ja - Kanalbegrenzungen und Abklingzeit für erneuten Eintritt |
| Journey Canvas-Knoten | 3-4 (Ereignis, optionale Bedingung, Aktion, Ende) | 5-7 (Ereignis, Warten, Bedingung, Verzweigungen, Aktion, Ende) | Wie A oder B plus Konfiguration der Geschäftsregel |
| Erfordert | Ereignisschema, Kanaloberfläche, Nachrichteninhalt | Alle Optionen von Option A + Aufnahme von Konversionsereignissen | Gesamte Konfiguration von Option A oder B + Häufigkeitsregeln |

### Wählen der richtigen Option

Verwenden Sie die folgenden Entscheidungshilfen, um die richtige Implementierungsoption auszuwählen.

1. **Muss die Nachricht sofort und ohne Verzögerung gesendet werden?** Wenn ja, beginnen Sie mit **Option A**. Bestätigungsnachrichten, Begrüßungs-E-Mails und Bestätigungen erfordern in der Regel keine Wartezeit.

2. **Sollte der Kunde Zeit haben, sich selbst zu konvertieren, bevor er die Nachricht erhält?** Wenn ja, wählen Sie **Option B**. Bei einem Warenkorbabbruch, einem Durchsuchen-Abbruch und einem Ablauf von Testversionen profitieren Kunden von einer Wartezeit, während der sie die Aktion selbst durchführen können.

3. **Tritt das auslösende Ereignis häufiger auf (tritt mehrmals pro Sitzung oder pro Tag für dasselbe Profil auf)?** Wenn ja, fügen Sie **Option C** als Überlagerung über Option A oder B hinzu. Produktansichten, Seitenansichten und Suchereignisse können eine große Anzahl von Triggern generieren, die einen Häufigkeitsschutz erfordern.

4. **Sind mehrere ausgelöste Journey und Kampagnen in der Sandbox aktiv?** Wenn ja, fügen Sie **Option C** unabhängig von der Ereignisfrequenz hinzu, um die Cross-Journey-Kommunikationslast zu verwalten und Kanalermüdung zu vermeiden.

In der Praxis verwenden die meisten Produktionsimplementierungen die Optionen B + C für Anwendungsfälle im Stil eines Abbruchs (bedingtes Warten mit Frequency Governance) und A + C für Anwendungsfälle im Stil einer Bestätigung (sofortiger Versand mit Frequency Governance als Sicherheitsnetz).

## Implementierungsphasen

In den folgenden Phasen wird die End-to-End-Implementierung von ereignisgesteuertem Messaging erläutert.

### Phase 1: Konfigurieren des Ereignisschemas und der Datenerfassung

**Anwendungsfunktion:** AEP: Datenmodellierung (F2), AEP: Datenquellen und Erfassung (F3)

**Was Sie konfigurieren werden:** Das XDM ExperienceEvent-Schema, das das auslösende Ereignis erfasst, den Datensatz, in dem diese Ereignisse gespeichert werden, und die Echtzeit-Datenerfassungs-Pipeline (Web SDK, Mobile SDK oder Server API), die Ereignisse an AEP streamt. In dieser Phase wird die Datengrundlage geschaffen, auf die die Journey lauschen wird.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Ereignistyp wird ausgelöst**
>
>Welches Ereignis gibt der Nachricht Trigger? Der Ereignistyp bestimmt die erforderlichen Schemafelder und die Sammlungsmethode.
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Commerce-Ereignis (Hinzufügen zum Warenkorb, Kauf, Checkout) | E-Commerce-Anwendungsfälle - Warenkorbabbruch, nach dem Kauf | Erfordert Commerce-Feldergruppe mit `productListItems`, `cart`, `order` Feldern |
>| Web-Interaktionsereignis (Seitenansicht, Produktansicht) | Browser-Abbruch, Trigger zur Inhaltsinteraktion | Erfordert die Feldergruppe „Web-Details“ mit `webPageDetails`, `webInteraction` Feldern |
>| Anwendungsereignis (App-Installation, -Deinstallation, In-App-Aktion) | Trigger für mobile Interaktion | Erfordert mobile SDK-Implementierung und Anwendungsfeldgruppe |
>| Systemereignis (Zahlungsfehler, Abonnementänderung, Statusaktualisierung) | Benachrichtigungen zu Vorgängen | Server-seitige API oder Quell-Connector ist erforderlich, um Systemereignisse aufzunehmen |
>| Formularübermittlungsereignis | Lead-Generierung, Registrierungsbestätigung | Erfordert die Erfassung von Formulardatenfeldern durch benutzerdefinierte Feldergruppen |

>[!NOTE]
>
>**Entscheidung: Sammlungsmethode**
>
>Wie wird das auslösende Ereignis erfasst und in AEP gestreamt?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Web SDK | Web-basierte Verhaltensereignisse (Hinzufügen zum Warenkorb, Seitenansichten, Formularübermittlungen) | Erfordert die Installation von Web SDK auf der Website; Ereignisse werden in Echtzeit über Edge Network gestreamt |
>| Mobile SDK | Mobile-App-Ereignisse (App-Öffnungen, In-App-Aktionen, Push-Token-Registrierung) | Erfordert die Integration von Mobile SDK in die native App oder den React Native-Wrapper |
>| Edge Network Server-API | Serverseitige Systemereignisse (Zahlungsverarbeitung, Abonnementverwaltung, Backend-Trigger) | Keine Client-seitige Abhängigkeit; Ereignisse, die von den Backend-Systemen des Unternehmens gesendet werden |
>| Source-Connector | Ereignisse aus externen Systemen (CRM, Marketing-Automatisierung, Legacy-Plattformen) | Normalerweise Batch-basiert; unterstützt möglicherweise nicht die Echtzeit-Auslösung, es sei denn, es ist Streaming-fähig. |

**Benutzeroberflächennavigation:** Datenerfassung > Datenströme > Neuer Datenstrom (für die Datenstromeinrichtung); Schemata > Schema erstellen (für Ereignisschema); Datensätze > Datensatz aus Schema erstellen (für die Datensatzerstellung)

**Wichtige Konfigurationsdetails:**

- Das Ereignisschema muss alle Felder enthalten, die für das Journey der Bedingungsauswertung und Nachrichtenpersonalisierung erforderlich sind
- Für den Datenstrom müssen sowohl [!DNL Adobe Experience Platform]- als auch [!DNL Adobe Journey Optimizer]-Services aktiviert sein
- Der Datensatz muss für das Echtzeit-Kundenprofil aktiviert sein, damit Ereignisse mit einheitlichen Profilen verknüpft werden
- Ereignisdaten müssen ein Identitätsfeld (E-Mail, CRM-ID, ECID) enthalten, das in ein bekanntes Profil aufgelöst werden kann

**Dokumentation zu Experience League:**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Übersicht über die Streaming-Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Phase 2: Konfigurieren von Identität und Profil

**Anwendungsfunktion:** AEP: Identitäts- und Profilkonfiguration (F4)

**Was Sie konfigurieren werden:** Identity-Namespaces für die Kennungen des auslösenden Ereignisses, primäre Identitätsbezeichnung im Ereignisschema, Identitätsverknüpfungsregeln für die geräteübergreifende Auflösung und eine Zusammenführungsrichtlinie für die Profilvereinheitlichung. Dadurch wird sichergestellt, dass das auslösende Ereignis mit einem einheitlichen Kundenprofil verknüpft ist, sodass die Journey Kontaktinformationen auflösen und die Nachricht versenden kann.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Primäre Identität für Ereignisschema**
>
>Welches Identitätsfeld im auslösenden Ereignis sollte als primäre Identität für die Profilauflösung dienen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| E-Mail-Adresse | Ereignisse aus authentifizierten Web-Sitzungen oder Formularen, in denen E-Mails erfasst werden | Direkte Auflösung zu einer kontaktierbaren Identität; einfachster Pfad zum E-Mail-Versand |
>| CRM-ID | Ereignisse aus authentifizierten Systemen, bei denen die CRM-ID die primäre Kennung ist | Erfordert die Erstellung eines CRM-ID-Namespace. Das Profil muss über eine verknüpfte E-Mail oder Telefonnummer für den Nachrichtenversand verfügen |
>| ECID (Experience Cloud ID) | Anonyme Web- oder App-Ereignisse, bei denen keine authentifizierte Identität verfügbar ist | Erfordert Identitätszuordnung, um ECID mit einer bekannten Identität zu verknüpfen; Nachrichten können nicht allein an ECID gesendet werden |
>| Telefonnummer | Ereignisse aus Interaktionen mit Mobilgeräten oder Callcentern | Unterstützt den SMS-Versand; erfordert Namespace per Telefon |

**UI-Navigation:** Identitäten > Identity-Namespace erstellen; Schemata > Schema auswählen > Feld auswählen > Identität > Als primäre Identität festlegen; Profile > Zusammenführungsrichtlinien

**Wichtige Konfigurationsdetails:**

- Bei anonymen Ereignissen (nur ECID) kann der Nachrichtenversand erst dann im Trigger erfolgen, wenn die ECID über das Identitätsdiagramm mit einer bekannten kontaktierbaren Identität (E-Mail, Telefon) verknüpft ist
- Die von AJO verwendete Zusammenführungsrichtlinie muss mit der für die Zielgruppenbewertung verwendeten konsistent sein
- Stellen Sie bei einem Web-basierten ausgelösten Messaging sicher, dass das Identitätsdiagramm die ECID über Anmeldeereignisse mit authentifizierten Identitäten verknüpft

**Dokumentation zu Experience League:**

- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 3: Einrichten von Kanaloberflächen

**Anwendungsfunktion:** AJO: Kanalkonfiguration

**Was Sie konfigurieren werden:** Die Kanaloberfläche (Voreinstellung), die die Versandinfrastruktur für die ausgelöste Nachricht definiert - Subdomain-Delegierung, IP-Pool, Absenderidentität, Antwort-an-Adresse, Abmelde-Handhabung und kanalspezifische Anmeldeinformationen (SMS-Anbieter, Push-Zertifikate). Es muss eine gültige Kanaloberfläche vorhanden sein, bevor Nachrichteninhalte erstellt oder Journey veröffentlicht werden können.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Nachrichtenkanal**
>
>Welchen Kanal verwendet die ausgelöste Nachricht?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| E-Mail | Am häufigsten ausgelöste Messaging-Anwendungsfälle - Abbruch, Wiederherstellung, Bestätigung, Onboarding | Subdomain-Delegierung, IP-Pool, Absenderkonfiguration erforderlich; unterstützt umfangreiche HTML-Inhalte und Personalisierung |
>| SMS | Zeitkritische Benachrichtigungen, knappe Warnhinweise, Zielgruppen mit hoher SMS-Interaktion | Erfordert die Integration von SMS-Anbietern (Sinch, Twilio, Infobip); unterliegt Zeichenbeschränkungen und strengeren Zustimmungsanforderungen |
>| Push-Benachrichtigung | Mobile-App-Interaktion, Rückgewinnung von App-Nutzern | Erfordert die Konfiguration von Push-Anmeldeinformationen (APNs für iOS, FCM für Android). Die App muss für den Benutzer mit aktiviertem Push installiert sein |
>| Mehrere Kanäle | Umfassende Interaktionsstrategie mit Kanalpräferenz- oder Fallback-Logik | Erfordert mehrere Kanaloberflächen; die Kanalauswahl kann über Journey-Bedingungsknoten verwaltet werden |

>[!NOTE]
>
>**Entscheidung: Methode der Subdomain-Zuweisung (E-Mail)**
>
>Wie sollte die Subdomain für den E-Mail-Versand an Adobe delegiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Vollständige Delegierung | Das Unternehmen möchte, dass Adobe alle DNS-Einträge für die sendende Subdomain verwaltet | Einfachste Einrichtung; Adobe verwaltet SPF-, DKIM- und DMARC-Datensätze automatisch |
>| CNAME-Delegierung | Unternehmen möchte die DNS-Kontrolle beibehalten und gleichzeitig auf die Adobe-Infrastruktur verweisen | Erfordert manuelle DNS-Eintragsverwaltung; bietet mehr organisatorische Kontrolle über DNS |

**UI-Navigation:** Administration > Kanäle > Subdomains (für die Einrichtung von Subdomains); Administration > Kanäle > IP-Pools (für die Konfiguration von IP-Pools); Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen (für die Erstellung von Oberflächen)

**Wichtige Konfigurationsdetails:**

- Die Subdomain-Verifizierung und DNS-Verbreitung kann bis zu 48 Stunden dauern
- Neue IP-Pools erfordern einen Aufwärmplan (2-4 Wochen mit schrittweiser Volumenzunahme)
- Konfigurieren von 1-Klick-Abmelde-Headern für E-Mail-Compliance
- Konfigurieren Sie für SMS die Provider-Anmeldeinformationen, bevor Sie die SMS-Kanaloberfläche erstellen
- Konfigurieren Sie für Push-Benachrichtigungen APNs und FCM-Anmeldeinformationen, bevor Sie die Oberfläche des Push-Kanals erstellen

**Dokumentation zu Experience League:**

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 4: Nachrichteninhalt erstellen

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung

**Was Sie konfigurieren werden:** Der Nachrichteninhalt, der von der Journey bereitgestellt wird, einschließlich Layout-Design, Personalisierungs-Token mit Profil- und Ereignisattributen, bedingten Inhaltsbausteinen, wiederverwendbaren Fragmenten (Kopfzeilen, Fußzeilen, Haftungsausschlüsse) und Inhaltsvorschau und Tests.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Content-Ansatz**
>
>Wie sollte der Nachrichteninhalt erstellt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Mit vorhandener Vorlage beginnen | Organisationsvorlagen sind vorhanden, und Markenkonsistenz ist erforderlich | Schnellster Pfad zur Inhaltserstellung; stellt die Markenkonformität sicher; Vorlagenänderungen werden auf neue Nachrichten übertragen |
>| Erstellen von neuen Inhalten in Email Designer | Benutzerdefiniertes Layout für diese spezifische ausgelöste Nachricht erforderlich | Vollständige kreative Steuerung; visueller Drag-and-Drop-Editor; langsamer, aber flexibler |
>| HTML importieren | Inhalte werden von einem externen Team oder einer externen Agentur erstellt und als HTML bereitgestellt | Erfordert HTML-Programmierkenntnisse; unterstützt möglicherweise nicht alle E-Mail-Designer-Funktionen. |

>[!NOTE]
>
>**Entscheidung: Personalisierung von Ereignissen**
>
>Welche Ereignisdaten sollten im Nachrichteninhalt verwendet werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Kontextuelle Ereignisattribute | Die Nachricht sollte Details zum auslösenden Ereignis enthalten (Produktname, Warenkorbwert, Formularfelder) | Verwenden von kontextuellen Ereignisattributen im Personalisierungseditor; Daten stammen aus der Payload des auslösenden Ereignisses |
>| Profilattribute | Die Nachricht sollte Daten auf Profilebene (Vorname, Treuestufe, Standort) enthalten | Verwenden von Profilattributen über XDM-Pfade (z. B. `profile.person.name.firstName`); Daten stammen aus dem einheitlichen Profil |
>| Ereignis- und Profilattribute | Die Nachricht sollte Ereigniskontext mit Profilpersonalisierung kombinieren | Häufigster Ansatz für ausgelöste Nachrichten; stellt sowohl Relevanz (Ereignis) als auch Personalisierung (Profil) sicher |

**UI-Navigation:** Content-Management > Inhaltsvorlagen > Durchsuchen (für Vorlagenauswahl); Kampagnen- oder Journey-Aktion > Inhalt bearbeiten > E-Mail-Designer (für Inhaltsdesign); Auswählen von Textkomponente > Personalization-Symbol (für das Hinzufügen von Personalisierung)

**Wichtige Konfigurationsdetails:**

- Verwenden Sie kontextuelle Attribute, um mit Daten aus dem auslösenden Ereignis zu personalisieren (z. B. Produktname, Warenkorbwert)
- Profilattribute für Name, Voreinstellungen und Treuedaten verwenden
- Konfigurieren Sie bedingte Inhaltsbausteine, um Inhalte nach Profilsegment oder -attribut zu variieren (z. B. verschiedene CTA für Mitglieder des Treueprogramms).
- Erstellen Sie wiederverwendbare Fragmente für Kopf- und Fußzeilen sowie Haftungsausschlüsse, die für ausgelöste Nachrichten freigegeben werden
- Vorschau mit mehreren Testprofilen, um zu überprüfen, ob die Personalisierung korrekt dargestellt wird
- Führen Sie Testsendungen an interne Stakeholder durch, bevor Sie die Journey veröffentlichen

**Dokumentation zu Experience League:**

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 5: Erstellen und Konfigurieren der Journey

**Anwendungsfunktion:** AJO: Journey Orchestration, AJO: Häufigkeits- und Geschäftsregeln (Option C), AJO: Konflikt- und Prioritätsverwaltung

**Was Sie konfigurieren werden:** Die Journey, die auf das auslösende Ereignis wartet und den Nachrichtenversand koordiniert. Dies ist die Kernimplementierungsphase, in der die Journey-Arbeitsfläche mit dem Ereigniseinstiegsknoten, Bedingungsknoten, Warteschritten (für Option B), Nachrichtenaktionsknoten und Beendigungskriterien entworfen wird. Diese Phase umfasst auch die Frequenzverwaltung (Option C) und die Konflikt-/Prioritätskonfiguration.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Regeln für den Wiedereintritt**
>
>Kann ein Profil diese Journey erneut aufrufen, wenn das auslösende Ereignis erneut auftritt?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Erneuten Eintritt erlauben (mit Abklingzeit) | Das Ereignis kann legitimerweise wiederholt werden und jedes Ereignis rechtfertigt eine Nachricht (z. B. sollte bei jedem Warenkorbabbruch eine Wiederherstellungsmeldung Trigger werden) | Legen Sie einen Abklingzeitraum (mindestens 5 Minuten) fest, um einen schnellen erneuten Eintritt von doppelten Ereignissen zu verhindern. Die typische Abklingzeit liegt zwischen 1 Stunde und 72 Stunden |
>| Kein Wiedereintritt | Die Nachricht sollte unabhängig vom Wiederauftreten des Ereignisses (z. B. Willkommensnachricht nach der ersten Registrierung) nur einmal pro Profil gesendet werden | Das Profil wird nach dem ersten Journey-Abschluss dauerhaft ausgeschlossen. Dies ist für einmalige Lebenszyklusnachrichten geeignet. |

>[!NOTE]
>
>**Entscheidung: Wartezeit (nur Option B)**
>
>Wie lange sollte die Journey warten, bevor Bedingungen ausgewertet und die Nachricht gesendet wird?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Kurze Wartezeit (1-4 Stunden) | Anwendungsfälle mit hoher Dringlichkeit, wie z. B. Warenkorbabbruch, bei denen eine sofortige Nachbereitung wirksam ist | Höheres Nachrichtenvolumen; kann einige Selbstkonvertierer erfassen; am besten geeignet für die Wiederherstellung von hochwertigen Warenkorbdaten |
>| Medium-Wartezeit (12-24 Stunden) | Anwendungsfälle mit mittlerer Dringlichkeit wie Browser-Abbruch oder Inhaltsinteraktion | Ausgewogener Ansatz; reduziert unnötige Sendungen bei Beibehaltung der Relevanz |
>| Lange Wartezeit (2-7 Tage) | Anwendungsfälle mit geringer Dringlichkeit wie Erinnerungen an den Ablauf von Testversionen oder regelmäßige Check-ins | Geringeres Nachrichtenvolumen, höheres Risiko, die kontextuelle Relevanz zu verlieren |
>| Benutzerdefiniertes Datum/benutzerdefinierte Uhrzeit | Anwendungsfälle, die an ein bestimmtes Datum gebunden sind (z. B. 3 Tage vor Ablauf der Testversion senden) | Auf ein berechnetes Datum/eine berechnete Uhrzeit warten; verwendet den benutzerdefinierten Ausdruckseditor. |

>[!NOTE]
>
>**Entscheidung: Ausstiegskriterien**
>
>Unter welchen Bedingungen soll ein Profil vom Journey entfernt werden, bevor die Nachrichtenaktion erreicht wird?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Konversionsereignis (z. B. Kauf abgeschlossen) | Warenkorb- oder Durchsuchen-Abbruch, bei dem das Ziel die Konversion ist | Das Profil wird automatisch beendet, wenn das Konversionsereignis erkannt wird. Der sauberste Ansatz für Option B. |
>| Änderung der Zielgruppenzugehörigkeit | Das Profil sollte beendet werden, wenn es ein qualifizierendes Segment verlässt | Erfordert eine vom Streaming bewertete Zielgruppe, die nahezu in Echtzeit aktualisiert wird |
>| Journey-Zeitüberschreitung (max. 91 Tage) | Standardverhalten - Das Profil wird nach der maximalen Journey-Dauer beendet | Sicherheitsnetz; sollte nicht der primäre Ausstiegsmechanismus für kurzlebige ausgelöste Journey sein |
>| Keine expliziten Ausstiegskriterien | Einfache Bestätigungen (Option A), bei denen jedes qualifizierte Profil die Nachricht erhalten soll | Das Profil wird automatisch nach der Nachrichtenaktion und dem Endknoten beendet |

>[!NOTE]
>
>**Entscheidung: Frequenzverwaltung (Option C)**
>
>Wie viele ausgelöste Nachrichten soll ein Profil pro Zeitraum erhalten?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Kanalspezifische Begrenzungen (z. B. 3 E-Mails/Woche, 1 SMS/Tag) | Verschiedene Kanäle haben unterschiedliche Ermüdungsschwellen | Empfohlener Ansatz; berücksichtigt das Eindringlichkeitsniveau jedes Kanals |
>| Globale Begrenzung (z. B. 5 Nachrichten/Woche über alle Kanäle hinweg) | Vereinfachte Governance für alle Kommunikationstypen | Einfacheres Management, aber weniger nuanciert; kann weniger störende Kanäle übermäßig einschränken |
>| Nur Abklingzeit für erneuten Eintritt auf Journey-Ebene | Frequenzverwaltung, die für diese spezifische Journey erforderlich ist, aber nicht unternehmensweit | Einfachste Implementierung; schützt nicht vor Cross-Journey-Ermüdung |

**Benutzeroberflächennavigation:** Journey > Journey erstellen (für die Journey-Erstellung); Journey-Arbeitsfläche > Ereignisaktivität ziehen (für die Ereigniseingabe); Journey-Arbeitsfläche > Aktivität „Warten“ ziehen (für die Wartekonfiguration); Journey-Arbeitsfläche > Aktivität „Bedingung“ ziehen (für die Bedingungsverzweigung); Journey-Eigenschaften > Beendigungskriterien (für die Beendigungskonfiguration); Administration > Geschäftsregeln > Regel erstellen (für Frequenzbegrenzungen)

**Wichtige Konfigurationsdetails:**

- Konfigurieren Sie das Journey-Ereignis, indem Sie das Ereignisschema auswählen und die qualifizierenden Bedingungen definieren
- Für Option B fügen Sie den Warteknoten unmittelbar nach dem Ereigniseintrag und vor einer Bedingungsauswertung hinzu
- Konfigurieren von Bedingungsknoten mithilfe von Profilattributen, Ereignisdaten oder Prüfungen der Zielgruppenzugehörigkeit
- Verknüpfen des Nachrichtenaktionsknotens mit der Kanaloberfläche und den erstellten Inhalten aus den Phasen 3 und 4
- Legen Sie die maximale Wartezeit für den Journey auf eine geeignete Dauer fest (weniger als 91 Tage für ausgelöste Journey)
- Erstellen Sie für Option C Häufigkeitsregeln über Administration > Geschäftsregeln , bevor Sie die Journey veröffentlichen
- Weisen Sie der Journey einen Prioritätswert zu, wenn andere Kampagnen oder Journey Audiences überschneiden

**Wo die Optionen unterschiedlich sind:**

**Für Option A (einfaches Ereignis ausgelöst):**
Die Journey-Arbeitsfläche ist minimal: Ereigniseintrag > Optionale Einverständnis-/Eignungsbedingung > Nachrichtenaktion > Ende. Keine Warteschritte oder Konversionsprüfungen. Legen Sie Regeln für den erneuten Eintritt fest, je nachdem, ob das Ereignis bei jedem Auftreten eine Nachricht erzeugen soll.

**Für Option B (bedingt mit Warten):**
Fügen Sie nach dem Ereigniseintrag einen Warteknoten hinzu. Fügen Sie nach der Wartezeit einen Bedingungsknoten hinzu, um die Konvertierung zu überprüfen (z. B. um zu überprüfen, ob `commerce.purchases` Ereignis nach dem Journey-Eintritt aufgetreten ist), oder verwenden Sie Beendigungskriterien, um automatisch konvertierte Profile zu entfernen. Verzweigung zur Nachrichtenaktion auf dem Pfad „nicht konvertiert“ und zu einem Endknoten auf dem Pfad „konvertiert“.

**Für Option C (Frequency Governance):**
Konfigurieren Sie Häufigkeitsbegrenzungen auf Organisationsebene über Administration > Geschäftsregeln vor der Veröffentlichung. Legen Sie die Abklingzeit für den erneuten Eintritt auf Journey-Ebene in den Journey-Eigenschaften fest. Optional können Sie über Journey-Eigenschaften einen Prioritätswert zuweisen, um zu steuern, welche Kommunikation gewinnt, wenn Begrenzungen erreicht werden. Dies kann zusätzlich zu Option A oder Option B angewendet werden.

**Dokumentation zu Experience League:**

- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Phase 6: Testen und Bereitstellen der Journey

**Anwendungsfunktion:** AJO: Journey Orchestration

**Was Sie konfigurieren werden:** Validierung des Testmodus, um zu überprüfen, ob sich die Journey wie erwartet verhält, mit Testprofilen, gefolgt von einer Journey-Veröffentlichung, um sie live zu schalten.

**Benutzeroberflächennavigation:** Journey-Arbeitsfläche > Umschalter für Testmodus (zum Testen); Journey-Arbeitsfläche > Veröffentlichen (für die Bereitstellung)

**Wichtige Konfigurationsdetails:**

- Aktivieren Sie den Testmodus auf der Journey-Arbeitsfläche, um Ereignis-Trigger mit Testprofilen zu simulieren
- Testprofile mit gültigen Kanalkontaktdaten (E-Mail-Adresse, Telefonnummer) auswählen
- Trigger des Testereignisses und Überprüfung, ob das Testprofil den erwarteten Pfad durchläuft
- Überprüfen Sie für Option B, ob sich der Warteschritt korrekt verhält und die Bedingungsauswertung die erwartete Verzweigung erzeugt
- Überprüfen, ob Personalisierungs-Token in der Testmeldung korrekt dargestellt werden
- Veröffentlichen Sie die Journey nach erfolgreichem Test, um sie live zu schalten
- Überwachen des Journey-Status und der Metriken für den anfänglichen Profileintrag nach der Veröffentlichung

**Dokumentation zu Experience League:**

- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Phase 7: Überwachen und Erstellen von Berichten zur Leistung

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse, S4: Monitoring und Observability, S5: Reporting und Analyse

**Was Sie konfigurieren werden:** Live- und Verlaufs-Journey-Berichte für die Versand- und Interaktionsüberwachung, Plattformwarnmeldungen für Fehler bei der Ereignisaufnahme und beim Journey-Verarbeiten sowie optional CJA-Arbeitsbereiche für eine tiefere kanalübergreifende Analyse der Effektivität ausgelöster Nachrichten.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Berichtstiefe**
>
>Wie viel Reporting und Analyse ist für diesen Anwendungsfall erforderlich?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur native AJO-Berichte | Die operative Überwachung der Versandmetriken ist ausreichend | Sofort verfügbar; Covers gesendet, zugestellt, gebounct, geöffnet, angeklickt; keine zusätzliche Konfiguration erforderlich |
>| Integration von AJO Native und CJA | Kanalübergreifende Analyse, Konversionszuordnung und Trendanalyse sind erforderlich | Erfordert eine Verbindung mit CJA und eine Datenansicht, die mit AJO-Datensätzen verknüpft sind; bietet tiefere Analysefunktionen |

**Benutzeroberflächennavigation:** Journey > Journey auswählen > Live-Bericht (für die Live-Überwachung); Journey > Journey auswählen > Alle Zeitberichte (für die Verlaufsanalyse); Warnhinweise > Warnhinweisregeln > Abonnieren (für die Warnhinweiskonfiguration)

**Wichtige Konfigurationsdetails:**

- Zugreifen auf den Journey-Live-Bericht während der aktiven Ausführung zur Überwachung von Profileinträgen, -austritten und Versandmetriken
- Lesen Sie den Verlaufsbericht, nachdem die Journey ausreichend lange aktiv war, um aussagekräftige Daten zu sammeln
- Konfigurieren von Warnhinweisen für Fehler bei der Ausführung des Quellflusses (Ereignisaufnahme) und Verzögerungen bei der Journey-Verarbeitung
- Stellen Sie bei der CJA-Integration sicher, dass die CJA-Verbindung AJO-Erlebnisereignis-Datensätze enthält (Nachrichten-Feedback-Ereignisdatensatz, E-Mail-Tracking-Erlebnisereignis-Datensatz)

**Dokumentation zu Experience League:**

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Überlegungen bei der Implementierung

Dieser Abschnitt enthält Informationen zu Leitplanken, allgemeinen Fallstricken, Best Practices und Entscheidungen bei durch ein Ereignis ausgelösten Messaging-Implementierungen.

### Leitplanken und Beschränkungen

Die folgenden Leitplanken und Einschränkungen gelten für Implementierungen von ereignisausgelöstem Messaging.

- **Durchsatz von unitären Ereignissen:** Maximal 5.000 Journey pro Sekunde für unitäre Ereignisse - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Limit für Live-Journey:** Maximal 500 Live-JourneyJourney Optimizer ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)[
- **Journey-Arbeitsfläche Limit:** Maximal 50 Aktivitäten pro Journey-Arbeitsfläche
- **Journey-Zeitüberschreitung:** Die maximale Journey-Dauer beträgt 91 Tage (globales Zeitlimit)
- **Abklingzeit für erneuten Eintritt:** Mindestabklingzeit für erneuten Eintritt beträgt 5 Minuten.
- **Konfigurationen der Frequenzlimitierung:** Maximal 10 Begrenzungskonfigurationen pro Sandbox
- **Kanaloberflächen:** Maximal 10 Kanaloberflächen pro Kanaltyp pro Sandbox
- **Streaming-Aufnahme:** Maximal 20.000 Datensätze pro Sekunde pro HTTP-Verbindung — [Aufnahme-Schutzmechanismen](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **Berechnete Attribute:** Maximal 25 berechnete Attribute pro Sandbox - [Leitplanken für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **Inhaltsfragmente:** maximal 30 Inhaltsfragmente pro Nachricht
- **Aktualisierung des Live-Berichts:** Live-Berichte werden alle 60 Sekunden aktualisiert und zeigen die Daten der letzten 24 Stunden an
- **Latenz bei historischen Berichten:** Es kann bis zu 2 Stunden dauern, bis historische Berichte (alle Zeiten) vollständig ausgefüllt sind, nachdem die Ausführung beendet wurde

### Häufige Fehler

Beachten Sie bei der Implementierung von ereignisgesteuertem Messaging die folgenden häufigen Probleme.

- **Anonyme Ereignisse ohne Identitätsauflösung:** Auslösen von Ereignissen, die nur eine ECID (anonyme Cookie-ID) tragen, kann nicht in ein kontaktierbares Profil für den Nachrichtenversand aufgelöst werden. Stellen Sie sicher, dass das auslösende Ereignis eine authentifizierte Identität enthält oder dass das Identitätsdiagramm die ECID mit einem bekannten Kontakt verknüpft. Ohne Identitätsauflösung gelangen Profile auf die Journey, schlagen jedoch beim Nachrichtenversand fehl.

- **Konversionsereignis für Bedingungsprüfungen von Option B fehlt:** Wenn das Konversionsereignis (z. B. der Kauf) nicht in AEP aufgenommen wird oder nicht mit derselben Profilidentität wie das auslösende Ereignis verknüpft ist, wird die Bedingungsprüfung fälschlicherweise als „nicht konvertiert“ ausgewertet und sendet unnötige Nachrichten. Vergewissern Sie sich, dass Konversionsereignisse in Echtzeit in AEP eingehen und sich mit dem auslösenden Ereignis identifizieren.

- **Übermäßig permissive Regeln für den erneuten Eintritt** Wenn Sie bei häufigen Ereignisquellen einen erneuten Eintritt ohne Abklingzeit zulassen, kann dies dazu führen, dass dasselbe Profil innerhalb von Minuten mehrere Nachrichten erhält. Legen Sie immer eine erneute Abklingzeit fest, die dem Geschäftskontext entspricht (z. B. 4-Stunden-Abklingzeit für Warenkorbabbruch, 24-Stunden-Abklingzeit für Browser-Abbruch).

- **Zeitzonenfehler bei Warteschritten:** Warteschrittprozess wird standardmäßig in UTC ausgeführt. Wenn die Journey auf Profile in mehreren Zeitzonen abzielt und die Wartezeit an die Ortszeit der Empfängerin bzw. des Empfängers angepasst werden soll, konfigurieren Sie die Zeitzoneneinstellungen auf der Journey entsprechend.

- **Häufigkeitsbegrenzungen, die mit anderen Kampagnen im Konflikt stehen**: Häufigkeitsbegrenzungen auf Organisationsebene gelten für alle Kampagnen und Journey. Eine neu ausgelöste Journey kann unterdrückt werden, wenn Profile bereits ihre Obergrenze aus anderen aktiven Kampagnen erreicht haben. Überwachen Sie die Unterdrückungsrate und passen Sie Prioritätswerte an, um sicherzustellen, dass wichtige ausgelöste Nachrichten priorisiert werden.

- **Fehler bei der Journey-Veröffentlichung aufgrund fehlender Abhängigkeiten:** Jede Verzweigung auf der Journey-Arbeitsfläche muss mit einer Endaktivität beendet werden. Alle Aktionsknoten müssen auf gültige Kanaloberflächen mit aktivem Nachrichteninhalt verweisen. Überprüfen Sie alle Abhängigkeiten vor der Veröffentlichung.

### Best Practices

Befolgen Sie diese Empfehlungen für erfolgreiche Implementierungen von ereignisgesteuertem Messaging.

- **Einfach beginnen und dann iterieren:** Mit Option A beginnen für neue Anwendungsfälle des ausgelösten Messaging. Fügen Sie eine Warte- und Bedingungslogik (Option B) nur nach der Validierung der Ereignis-Pipeline und des Nachrichtenversands hinzu. Fügen Sie die Frequenzverwaltung (Option C) hinzu, wenn mehrere ausgelöste Journey aktiv sind.

- **Ausstiegskriterien anstelle von Bedingungsknoten für Konversionsprüfungen verwenden:** Ausstiegskriterien entfernen automatisch Profile vom Journey, wenn ein qualifizierendes Ereignis (z. B. ein Kauf) auftritt, sodass nach dem Warteschritt kein expliziter Bedingungsknoten erforderlich ist. Dies erzeugt eine sauberere Journey-Arbeitsfläche und eine reaktionsschnellere Konversionserkennung.

- **Testen mit echten Ereignisdaten in einer Entwicklungs-Sandbox:** Verwenden Sie den Testmodus mit tatsächlichen Ereignis-Payloads (nicht nur Testprofilen), um zu überprüfen, ob Ereignisschemafelder, Personalisierungs-Token und Bedingungsausdrücke mit produktionsähnlichen Daten ordnungsgemäß funktionieren.

- **Ereignisspezifische Abklingzeiten für erneuten Eintritt festlegen:** Ordnen Sie die Abklingzeit dem Geschäftskontext des auslösenden Ereignisses zu. Warenkorbabbruch-Journey verwenden in der Regel eine Abklingzeit von 4-24 Stunden. Bestätigungs-Journey können einen sofortigen erneuten Eintritt erlauben. Onboarding-Journey sollten den erneuten Eintritt vollständig verhindern.

- **Überwachen der Unterdrückungsrate als Konsistenzmetrik:** Wenn die Unterdrückungsrate (Profile, die sich qualifizieren, aber aufgrund von Häufigkeits-Begrenzungen oder -Bedingungen keine Nachrichten erhalten) 30-40 % überschreitet, überprüfen Sie, ob die Begrenzungen zu restriktiv sind oder ob das auslösende Ereignis zu breit definiert ist.

- **Version Journey statt Live-Journey bearbeiten:** Eine Live-kann nicht direkt bearbeitet werden. Erstellen Sie eine neue Version, indem Sie die Journey duplizieren, Änderungen vornehmen und dann die alte Version stoppen und die neue Version veröffentlichen. Dadurch wird verhindert, dass Profile, die sich derzeit im Journey befinden, gestört werden.

- **Fallback-/Standardpfad in Bedingungsknoten einschließen:** Konfigurieren Sie immer einen Standardpfad (andernfalls) in Bedingungsknoten, um unerwartete Profilstatus zu verarbeiten. Profile, die keiner Bedingungsverzweigung entsprechen, sollten ordnungsgemäß beendet werden, anstatt hängen zu bleiben.

### Entscheidungen über Kompromisse

Beachten Sie beim Entwerfen Ihrer Implementierung von ereignisgesteuertem Messaging die folgenden Kompromisse.

>[!NOTE]
>
>**Kompromiss: Nachrichtengeschwindigkeit vs. Nachrichtenrelevanz**
>
>Sofortiger Nachrichtenversand (Option A) maximiert die Geschwindigkeit, kann jedoch Nachrichten an Kunden senden, die sich selbst konvertiert hätten. Verzögerte bedingte Bereitstellung (Option B) verbessert die Relevanz, indem Selbstkonverter herausgefiltert werden, führt jedoch zu einer Latenz, die die Dringlichkeit verringern kann.
>
>- **Option A bevorzugt:** Geschwindigkeit, Einfachheit, Anwendungsfälle im Bestätigungsstil, bei denen jedes Ereignis eine Nachricht rechtfertigt
>- **Option B bevorzugt:** Relevanz, reduzierte Nachrichtenermüdung, Anwendungsfälle im Stile eines Abbruchs, bei denen Selbstkonvertierung üblich ist
>- **Empfehlung** Verwenden Sie Option A für Transaktions- und Bestätigungsnachrichten, bei denen Geschwindigkeit der Hauptwert ist. Verwenden Sie Option B für Nachrichten, die eine Wiederherstellung oder erneute Interaktion ermöglichen, wenn die Relevanz die Geschwindigkeit übersteigt. Experimentieren Sie mit Wartezeiten, um für jeden Anwendungsfall das optimale Gleichgewicht zu finden.

>[!NOTE]
>
>**Kompromiss: Frequenzschutz vs. Nachrichtenabdeckung**
>
>Strenge Häufigkeitsbegrenzungen (Option C) verhindern Ermüdung, können aber wichtige ausgelöste Nachrichten unterdrücken, wenn sich die Profile ihrer Begrenzung nähern. Zulässige oder keine Begrenzungen maximieren die Abdeckung, riskieren jedoch Übernachrichten und Kanalermüdung.
>
>- **Strenge Begrenzungen zugunsten von** Kundenerlebnis, Markenreputation, Zustellbarkeit (weniger Spam-Beschwerden)
>- **Permissive Begrenzungen für :** Nachrichtenabdeckung, Konversionsmöglichkeiten, Vermeidung verpasster Trigger
>- **Empfehlung:** Beginnen Sie mit branchenüblichen Obergrenzen (3-5 E-Mails/Woche, 1-2 SMS/Woche, 2-3 Push/Tag) und passen Sie sie auf der Grundlage von Interaktionsmetriken und Abmelderaten an. Weisen Sie ausgelösten Nachrichten höhere Prioritätswerte zu, damit sie Batch-Kampagnen überzeugen, wenn Obergrenzen erreicht werden.

>[!NOTE]
>
>**Kompromiss: Journey-Einfachheit vs. Journey-Raffinesse**
>
>Einfache Journey (wenige Knoten, keine Verzweigung) sind einfacher zu erstellen, zu testen und zu pflegen, bieten jedoch eine begrenzte kontextuelle Anpassung. Komplexere Journey (mehrere Bedingungen, Verzweigungen, Segmentprüfungen) ermöglichen differenziertere Reaktionen, erhöhen jedoch die Komplexität und das Fehlerrisiko.
>
>- **Einfache Journey bevorzugen:** Implementierung, einfacheres Debugging, geringerer Wartungsaufwand
>- **Erfahrene Journey bevorzugen** Präziseres Targeting, bessere Personalisierung, weniger unnötige Sendungen
>- **Empfehlung:** Beginnen Sie mit der einfachsten Journey, die den Geschäftsanforderungen entspricht. Inkrementelles Hinzufügen von Komplexität basierend auf Leistungsdaten. Eine einfache Journey, die zuverlässig funktioniert, ist wertvoller als eine komplizierte Journey mit unerkannten Fehlern.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in dieser Implementierung verwendeten Funktionen.

### Journey-Orchestrierung

- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Erstellen einer SMS-Nachricht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Gestalten einer Push-Benachrichtigung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Häufigkeits- und Geschäftsregeln

- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Übersicht über Geschäftsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Begrenzungs-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Konflikt- und Prioritätenmanagement

- [Erste Schritte mit Konflikt- und Prioritätsverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Reporting und Leistung

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Datenerfassung und -aufnahme

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über die Streaming-Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Datenmodellierung und Schemata

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentierung und Audiences

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Berechnete Attribute

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Überwachung und Beobachtbarkeit

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Tutorials und Handbücher

- [Journey-Tutorial erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
