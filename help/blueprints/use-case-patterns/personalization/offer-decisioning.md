---
title: Offer Decisioning
description: Erfahren Sie, wie Sie mit zentralisierter Entscheidungslogik das nächstbeste Angebot oder den nächstbesten Inhalt für ein Profil kanalübergreifend auswählen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: ccfd8c987a0090ca690e15a4bd89f4d96ec9c01f
workflow-type: tm+mt
source-wordcount: '7889'
ht-degree: 2%

---

# Offer Decisioning

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für Offer Decisioning mithilfe von [!DNL Adobe Journey Optimizer] (AJO) Decisioning und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die eine zentralisierte Angebotsauswahllogik implementieren müssen, die kanalübergreifend das nächstbeste Angebot für jedes Kundenprofil bestimmt.

Verwenden Sie dieses Handbuch, um zu verstehen, was konfiguriert werden muss, wo Auswahlmöglichkeiten bestehen und welche Kompromisse für jede Entscheidung gelten.

Das Muster entkoppelt die Entscheidung, was angezeigt werden soll, von der Kanallogik, wo es angezeigt werden soll, und ermöglicht eine konsistente, optimierte Angebotsauswahl über E-Mail, Web, Mobile App und jeden anderen Touchpoint. AJO Decisioning verwaltet den gesamten Angebotslebenszyklus: die Angebotserstellung und -katalogverwaltung, Eignungsregeln (wer die einzelnen Angebote sehen kann), Rangfolgestrategien (wie die Auswahl unter geeigneten Angeboten erfolgt), Platzierungen (wo Angebote angezeigt werden) und Entscheidungsrichtlinien (die alles miteinander verbinden).

## Anwendungsfall - Übersicht

Unternehmen müssen häufig jedem Kunden zum Zeitpunkt der Interaktion das relevanteste Angebot, die relevanteste Promotion oder den relevantesten Anreiz unterbreiten. Unabhängig davon, ob die Interaktion in einer E-Mail-Kampagne, auf einer Website-Homepage, in einer Mobile App oder an einem Entscheidungspunkt innerhalb einer mehrstufigen Journey stattfindet, ist die Herausforderung dieselbe: Wählen Sie aus einem Katalog verfügbarer Optionen das optimale Angebot aus, je nachdem, wer der Kunde ist, für was er sich qualifiziert und welches Angebot am ehesten das gewünschte Ergebnis erzielt.

Offer Decisioning löst dieses Problem, indem es die gesamte Angebotsauswahllogik in der Entscheidungs-Management-Engine von AJO zentralisiert. Anstatt die Angebotszuweisungen in einzelne Kampagnen oder Kanäle zu hartcodieren, wertet die Entscheidungs-Engine die Attribute jedes Profils, die Zielgruppenzugehörigkeit und kontextuelle Signale aus, um das beste Angebot in Echtzeit zu ermitteln. Durch diese Zentralisierung wird sichergestellt, dass derselbe Kunde konsistente, optimierte Angebote erhält, unabhängig davon, über welchen Kanal er interagiert.

Dieses Muster unterscheidet sich vom Umfang der Web-/App-Personalisierung bekannter Besucher - die Angebotsentscheidung ist kanalunabhängig und zentralisiert, während die Personalisierung bekannter Besucher sich auf die Personalisierung digitaler Oberflächen konzentriert. Sie unterscheidet sich von der Verhaltensempfehlung durch einen Ansatz: Offer Decisioning verwendet explizite Eignungsregeln und Rangfolgestrategien, während die Verhaltensempfehlung verhaltenssignalgesteuerte Empfehlungen mithilfe von Auswahlstrategien und ML-Modellen hervorhebt.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.
**KPIs:**, Konversionsraten, Kundenzufriedenheit (CSAT)

**[Umsatz durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.
**KPIs:** Upsell-/Crossselling- %, inkrementeller Umsatz, Kundenlebenszeitwert

**[Steigerung der Kundentreue und des Lebenszeitwerts](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Vertiefung der Kundenbeziehungen und Maximierung des langfristigen Nutzens durch Treueprogramme, Prämien und personalisierte Interaktion.
**KPIs:** Kundenlebenszeitwert, Kundenbindung, Upsell/Crosssell %

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie Offer Decisioning in der Praxis angewendet werden kann.

- Nächstbestes Angebot in E-Mail-Kampagnen — Wählen Sie die zum Sendezeitpunkt relevanteste Promotion pro Empfänger aus.
- Werbebanner in Echtzeit auf Website - Decisioning wählt das Angebot beim Laden der Seite auf der Grundlage des Besucherprofils aus
- Personalisierte In-App-Karte mit dem besten Anreiz für die Lebenszyklusphase des Benutzers
- Kanalübergreifende Angebotskonsistenz - Dieselbe Entscheidungslogik dient E-Mail, Web und Push, damit der Kunde ein einheitliches Angebotserlebnis sieht
- Dynamische Gutschein- oder Rabattauswahl auf Basis der Kundenwertstufe (z. B. erhalten hochwertige Kunden ein Premium-Angebot)
- Auswahl von Angeboten für Produktaktualisierungen oder Upsell-Angebote auf Basis der aktuellen Abonnementebene
- Personalisierung des Treueprämienangebots basierend auf der Stufe und dem Aktivitätsverlauf

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität einer Offer-Decisioning-Implementierung gemessen werden.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Annahmerate | Prozentsatz der bereitgestellten Angebote, die zu einem Klick, einer Einlösung oder einer Konversion führen | Klicks auf Angebote oder Einlösungen / Insgesamt bereitgestellte Angebote |
| Verteilung der Angebotsauswahl | Anteil jedes ausgewählten Angebots an allen Entscheidungen | Anzahl pro Angebot/Gesamtzahl der gerenderten Entscheidungen |
| Fallback-Rate | Prozentsatz der Entscheidungen, bei denen kein personalisiertes Angebot qualifiziert und das Fallback bereitgestellt wurde | Fallback-Impressions/Entscheidungen insgesamt |
| Konversionsrate | Prozentsatz der Angebotsempfänger, die die gewünschte Aktion abgeschlossen haben (Kauf, Anmeldung, Einlösung) | Konversionen/Angebots-Impressionen |
| Inkrementeller Umsatz | Umsatz, der entscheidungsausgewählten Angeboten gegenüber einer Kontrollgruppe oder einem Fallback zugeschrieben wird | Umsätze durch personalisierte Angebote - Umsätze durch Fallback/Kontrolle |
| Kanalübergreifende Konsistenzbewertung | Prozentsatz der Profile, die dasselbe Angebot über mehrere Kanäle innerhalb eines definierten Fensters erhalten | Konsistente Angebote/Gesamtzahl der Multi-Channel-Impressions |
| Klickrate des Angebots | Prozentsatz der Angebots-Impressionen, die zu einem Klick führen | Angebotsklicks/Angebots-Impressionen |

## Anwendungsfallmuster

In diesem Abschnitt werden die Funktionskette und die Musterdefinition für Offer Decisioning beschrieben.

**Offer Decisioning**

Verwenden Sie eine zentralisierte Entscheidungslogik, um kanalübergreifend das nächstbeste Angebot oder den nächstbesten Inhalt für ein Profil auszuwählen.

**Funktionskette:** Zielgruppenbewertung > Angebotseignung > Rangfolgestrategie > Entscheidungsausführung > Versand > Berichterstellung

Im Abschnitt [Implementierungsoptionen](#implementation-options) finden Sie Informationen zur Manifestation jeder Komposition.

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Entscheidungs-Management-Engine für die Angebotserstellung, Eignungsregeln, Ranking-Strategien, Platzierungen und Entscheidungsrichtlinien; Kanalkonfiguration und Nachrichtenbearbeitung für den Versand von Angeboten; Kampagnen und Journey-Ausführung
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung für Angebotseignungssegmente; Profildaten und berechnete Attribute, die in Eignung und Ranking verwendet werden
- **[!DNL Adobe Experience Platform] (AEP)** - Einheitlicher Profilspeicher, Identitätsauflösung und Data Foundation, die sowohl AJO als auch RT-CDP unterstützen

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit aktivierten Entscheidungsberechtigungen. Dem Implementierungs-Team zugewiesene Funktionen zum Angebotsmanagement (Entscheidungs-Manager, Angebotsgenehmiger) | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Profilschema muss Attribute enthalten, die für Regeln der Angebotseignung verwendet werden (z. B. Treuestufe, Kaufverlauf, Abonnementtyp). Es sollte ein Schema für die Angebotsantwort/Interaktion zum Tracking von Angebotsimpressionen, Klicks und Konversionen vorhanden sein. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Die in den Eignungsregeln verwendeten Profilattribute müssen aktuell sein. Für die Web-Bereitstellung (Option B) muss Web SDK mit aktiviertem AJO-Service im Datenstrom implementiert werden. Für den E-Mail-Versand müssen Profilattribute zum Versandzeitpunkt aufgelöst werden können. | [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identitäts- und Profilkonfiguration | Angenommen an Ort und Stelle | Profile müssen über alle Kanäle aufgelöst werden können, über die Angebote bereitgestellt werden. Für eine kanalübergreifende Angebotskonsistenz ist eine einheitliche Identität von entscheidender Bedeutung. Daher muss dasselbe Profil in E-Mail-, Web- und Mobile-Kontexten erkannt werden. Für die Bereitstellung in Echtzeit über Web/App ist eine Edge-aktive Zusammenführungsrichtlinie erforderlich. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Audiences, die als Kriterien für die Angebotseignung verwendet werden, müssen definiert und bewertet werden (z. B. „hochwertige Kunden“, „Testbenutzer“, „Treuestufe Gold„). Die Auswertungsmethode muss mit der Versandlatenz übereinstimmen - Edge-Auswertung für Echtzeit-Web/App, Batch oder Streaming für E-Mail-Kampagnen. | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Tendenzwerte für Kunden-KI, Berechnungen des Lebenszeitwerts und Interaktionsmetriken verbessern die Effektivität der Rangfolgestrategie erheblich. Berechnete Attribute wie „Tage seit dem letzten Kauf“ oder „Gesamtausgaben in 90 Tagen“ ermöglichen präzisere Eignungsregeln und eine formularbasierte Rangfolge. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Empfohlen | Daten zum Angebotsverlauf und zu Entscheidungsereignissen werden im Laufe der Zeit gesammelt. Aufbewahrungsrichtlinien (Gültigkeit) sollten für Offer Interaction-Ereignisdatensätze konfiguriert werden, um Speicher zu verwalten und die Datenaufbewahrungsanforderungen zu erfüllen. | [Erweiterte Übersicht über das Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen stellen sicher, dass Angebote mit sensiblen Zielgruppenkriterien (z. B. Finanzstatus, Gesundheitsbedingungen) den Datennutzungsrichtlinien entsprechen. Kennzeichnungen auf Feldern, die in Eignungsregeln verwendet werden, verhindern das nicht konforme Targeting von Angeboten. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Empfohlen | Die Leistung der Entscheidungs-Engine, die Fallback-Raten und der Zustand des Versands von Angeboten sollten überwacht werden. Warnhinweise für hohe Fallback-Raten können auf eine Fehlkonfiguration von Eignungsregeln oder Probleme mit der Datenfrische hinweisen. | [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Die Leistungsberichterstattung für Angebote ist Teil der Funktionskette (Phase 7). Die CJA-Analyse ermöglicht eine kanalübergreifende Messung der Angebotseffektivität, die Attribution von Umsatzauswirkungen und die Identifizierung von Optimierungsmöglichkeiten. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

In der folgenden Tabelle sind die AJO-Funktionen und die Implementierungsphasen aufgeführt, in denen sie konfiguriert werden.

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Entscheidungsfindung | Phase 3: Einrichten der Entscheidungsfindung | Erstellen Sie Angebotselemente, definieren Sie Eignungsregeln, konfigurieren Sie Rangfolgestrategien, erstellen Sie Fallback-Angebote, definieren Sie Platzierungen und erstellen Sie Entscheidungsrichtlinien |
| Kanalkonfiguration | Phase 4: Kanal- und Oberflächenkonfiguration | Konfigurieren von E-Mail-, Web-, In-App- oder Code-basierten Kanaloberflächen für die Angebotsbereitstellung |
| Verfassen von Nachrichten | Phase 5: Konfiguration von Inhalten und Bereitstellung | Entwerfen von Nachrichtenvorlagen mit Platzierungszonen für Angebote; Konfigurieren von Code-basierten Erlebnissen für den Web-/App-Versand |
| Kampagnenausführung | Phase 5: Konfiguration von Inhalten und Bereitstellung | Ausführen geplanter oder API-ausgelöster Kampagnen, die Entscheidungsrichtlinien aufrufen (Option A) |
| Inhaltsexperiment | Phase 5: Konfiguration von Inhalten und Bereitstellung | Optional können A/B-Tests verschiedene Rangfolgestrategien durchführen oder kreative Varianten anbieten |
| Reporting und Leistungsanalyse | Phase 7: Reporting und Leistungsüberwachung | Überwachen der Angebotsauswahl, der Verteilung der Akzeptanzraten, der Fallback-Raten und der Performance auf Kanalebene |

### [!DNL Real-Time CDP] (RT-CDP)

In der folgenden Tabelle sind die RT-CDP-Funktionen und die Implementierungsphasen aufgeführt, in denen sie konfiguriert sind.

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 2: Evaluierung der Zielgruppe | Audiences definieren und auswerten, die für Regeln zur Angebotseignung verwendet werden; entsprechende Auswertungsmethode auswählen (Batch, Streaming oder Edge) |
| Profilanreicherung | Phase 1 (unterstützend): Berechnete Attribute | Profile mit berechneten Attributen und Tendenzwerten anreichern, die die Effektivität der Rangfolgestrategie verbessern |

## Voraussetzungen

Führen Sie die folgenden Voraussetzungen aus, bevor Sie mit der Implementierung beginnen.

- [ ] der AJO-Sandbox mit aktivierten Entscheidungs-Management-Funktionen
- [ Benutzerrollen mit Entscheidungs-Management-Berechtigungen ] (Angebote, Platzierungen, Entscheidungen erstellen/bearbeiten)
- [ ] Profilschema enthält Attribute, die für die Angebotseignung erforderlich sind (z. B. Treuestufe, Kundensegment, Abonnementebene)
- [ ] Profildaten sind aktuell und werden aktiv in die Aktualisierung der Eignungsattribute aufgenommen
- [ ] für Option A (E-Mail): E-Mail-Kanaloberfläche, die mit verifizierter Subdomain und erwärmtem IP-Pool konfiguriert ist
- [ ] Für Option B (Web/App): Web-SDK mit aktiviertem AJO-Service im Datenstrom implementiert; Edge-aktive Zusammenführungsrichtlinie konfiguriert
- [ ] Für Option C (Journey): Journey-Leinwand-Berechtigungen und mindestens ein Journey-Eintrittsereignis oder eine Zielgruppe konfiguriert
- [ ] Kreativ-Assets (Bilder, Kopien, CTAs) für jede Kombination aus Angebot und Platzierung
- [ ] Fallback-Angebotsinhalte, die für jede Platzierung vorbereitet werden
- [ Zielgruppen für Regeln zur Angebotseignung ], die in RT-CDP definiert und ausgewertet werden

## Implementierungsoptionen

In diesem Abschnitt werden die verfügbaren Implementierungsoptionen für Offer Decisioning beschrieben. Jede Option dient einem anderen Versandkanal und Anwendungsfallkontext.

### Option A: E-Mail-Angebotsentscheidung

Diese Option eignet sich am besten zur Auswahl des besten Angebots, das in ausgehende E-Mail-Kampagnen aufgenommen werden soll - Werbe-E-Mails, Newsletter-Personalisierung, Lebenszyklus-E-Mails mit dynamischen Angebotsinhalten. Die Entscheidung wird für jeden Empfänger zur Rendering-Zeit der Nachricht getroffen.

#### Funktionsweise

Entscheidungsrichtlinien werden beim Rendern von E-Mail-Nachrichten aufgerufen, um das beste Angebot für jede Empfängerin und jeden Empfänger auszuwählen. Die E-Mail-Vorlage enthält einen Platzierungsbereich, in dem die Decisioning-Engine die Inhaltsdarstellung des ausgewählten Angebots (Bild, HTML oder Text) einfügt. Zum Zeitpunkt des Versands bewertet die Engine das Profil jedes Empfängers anhand der Eignungsregeln für Angebote, wendet die Rangfolgestrategie an und bettet den Inhalt des erfolgreichsten Angebots in die E-Mail ein.

Dieser Ansatz funktioniert sowohl mit geplanten Kampagnen (die zur Kampagnenausführungszeit ausgewertet werden) als auch mit Journey-eingebetteten E-Mails (die ausgewertet werden, wenn das Profil den Nachrichtenaktionsknoten erreicht). Der Angebotsinhalt - Bild, Überschrift, Textkörper und CTA - wird je nach Empfänger und Empfängerin auf der Grundlage des Entscheidungsergebnisses personalisiert.

#### Wichtige Aspekte

- Die Angebotseignung wird zum Sendezeitpunkt anhand des aktuellen Status des Profils bewertet
- Die Batch-Zielgruppenauswertung ist ausreichend, da während des Nachrichtenrenderings Entscheidungen getroffen werden
- Jedes Angebot benötigt eine HTML- oder Bildinhaltsdarstellung für die E-Mail-Platzierung
- Das Fallback-Angebot muss für jede verwendete E-Mail-Platzierung Inhalt haben

#### Vorteile

- Einfachster Implementierungspfad - Verwendet Standard-Kampagnen- oder Journey-E-Mail-Versand
- Keine Client-seitigen SDK-Anforderungen
- Funktioniert mit vorhandener E-Mail-Infrastruktur und Kanaloberflächen
- Unterstützt große Zielgruppenvolumen durch die Batch-Kampagnenausführung

#### Einschränkungen

- Entscheidung wird zum Zeitpunkt des Versands getroffen; kann nicht an das Verhalten nach dem Versand angepasst werden
- Der Angebotsinhalt ist statisch, sobald die E-Mail zugestellt wurde (keine Echtzeit-Updates)
- Auf im Hub-Profilspeicher verfügbare Profilattribute beschränkt (nicht Edge)

#### Experience League-Ressourcen

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Option B: Echtzeit-Angebotsentscheidung über Web/App

Diese Option eignet sich am besten für die Auswahl von Angeboten in Echtzeit auf Web-Seiten oder mobilen Apps - Homepage-Werbebanner, Angebots-Widgets des Konto-Dashboards, In-App-Angebotskarten oder beliebigen digitalen Oberflächen, auf denen das Angebot zum Zeitpunkt des Ladens der Seite oder des Bildschirmrenderns ausgewählt werden soll.

#### Funktionsweise

Entscheidungsrichtlinien werden beim Laden der Seite oder beim Rendern des App-Bildschirms über das Edge Decisioning-Netzwerk oder Code-basierte Erlebnisse aufgerufen. Wenn ein Besucher eine Seite lädt, sendet die Web-SDK eine Anfrage an die Edge Network, die das Edge-Profil des Besuchers anhand der Angebotseignungsregeln und Ranking-Strategien auswertet. Das ausgewählte Angebot wird in der Antwort zurückgegeben und an der konfigurierten Position auf der digitalen Oberfläche gerendert.

Bei Code-basierten Erlebnissen ruft das Programm die Entscheidungsantwort ab und rendert den Angebotsinhalt mithilfe benutzerdefinierter Frontend-Logik. Für Web-Kanalerlebnisse kann der AJO-Webkanal den Angebotsinhalt mithilfe von visueller oder Code-basierter Inhaltserstellung direkt in die Seite einfügen.

#### Wichtige Aspekte

- Erfordert die Implementierung von Web SDK oder Mobile SDK mit aktiviertem AJO-Service im Datenstrom
- Für die Echtzeit-Profilsuche ist eine Edge-aktive Zusammenführungsrichtlinie erforderlich
- Zielgruppen, die für die Eignung verwendet werden, müssen die Edge-Evaluierung unterstützen (einfache Attributprüfungen und Segmentzugehörigkeit)
- Angebotsinhaltsdarstellungen sollten JSON- oder Bild-URL-Formate für das Client-seitige Rendering verwenden
- Das Impression-Tracking muss implementiert werden, um Angebotsansichten und Klicks zu erfassen

#### Vorteile

- Auswahl von Angeboten in Echtzeit während der Sitzung basierend auf dem aktuellen Profilstatus des Besuchers
- Latenz der Entscheidung in der zweiten Sekunde über Edge Network
- Angebote passen sich an die neuesten am Edge verfügbaren Profildaten an
- Unterstützt A/B-Tests von Angebotsstrategien durch Inhaltsexperimente

#### Einschränkungen

- Erfordert Client-seitige SDK-Implementierung (Web SDK oder Mobile SDK)
- Das Edge-Profil hat eine Untergruppe von vollständigen Hub-Profilattributen. Komplexe Eignungsregeln werden möglicherweise nicht korrekt ausgewertet
- Edge-Segmente verfügen über Segmentkomplexitätsbeschränkungen (keine Zeitreihenabfragen)
- Erfordert Frontend-Entwicklung für das benutzerdefinierte Rendering in Code-basierten Erlebnissen

#### Experience League-Ressourcen

- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Code-basierter Erlebniskanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

### Option C: Journey-Entscheidungsknoten

Diese Option eignet sich am besten für die Angebotsauswahl in einem mehrstufigen Journey. Dabei wird das beste Angebot an einem Entscheidungspunkt auf einer Kunden-Journey ausgewählt und dann über den nächsten Aktionsknoten bereitgestellt. Verwenden Sie diese Option, wenn die Angebotsentscheidung Teil eines umfassenderen Orchestrierungsflusses mit Wartezeiten, Bedingungen und mehreren Nachrichtenaktionen ist.

#### Funktionsweise

Entscheidungsrichtlinien werden von einem Entscheidungsknoten auf einer AJO Journey-Arbeitsfläche aufgerufen. Wenn ein Profil den Entscheidungsknoten erreicht, bewertet die Engine die Angebotseignung und das Ranking, um das optimale Angebot auszuwählen. Das ausgewählte Angebot informiert über die nächste Nachrichtenaktion - welche Angebotsinhalte einbezogen werden sollen, welcher Kanal verwendet werden soll oder welche Journey-Verzweigung je nach Angebotsergebnis durchgeführt werden soll.

Dieser Ansatz ermöglicht adaptive Journey, bei denen die Angebotsentscheidung nachfolgende Journey-Schritte beeinflusst. Beispielsweise kann eine Journey das beste Angebot auswählen, es per E-Mail versenden, auf Interaktionen warten und dann mit einer Push-Benachrichtigung nachgehen, wenn das Angebot nicht geöffnet wurde.

#### Wichtige Aspekte

- Die Journey muss mit einem Entscheidungsknoten und einem oder mehreren Nachrichtenaktionsknoten entworfen werden
- Die Angebotseignung wird anhand des Profilstatus zu dem Zeitpunkt bewertet, zu dem das Profil den Entscheidungsknoten erreicht
- Das Journey von Warteschritten zwischen der Entscheidung und dem Versand kann zu einer Änderung des Profilstatus führen
- Kann mit der Journey-Verzweigung kombiniert werden, um je nach ausgewähltem Angebot unterschiedliche Pfade zu wählen

#### Vorteile

- Integriert die Angebotsauswahl in mehrstufige Orchestrierungsflüsse
- Aktiviert adaptive Journey , bei denen die Angebotsauswahl Einfluss auf nachfolgende Schritte hat
- Unterstützt einen kanalübergreifenden Versand innerhalb derselben Journey (E-Mail, Push, SMS)
- Kann mit Journey-Bedingungen für das Tracking von Interaktionen nach dem Angebot kombiniert werden

#### Einschränkungen

- Komplexer einzurichten als die eigenständige Kampagnenentscheidung
- Es gelten Journey-Durchsatzbeschränkungen (Eintragsrate von 5.000 Profilen pro Sekunde)
- Entscheidung ist an den Journey-Kontext gebunden - Änderungen erfordern Journey-Versionierung
- Journey muss erneut veröffentlicht werden, damit Angebotskatalog- oder Entscheidungsrichtlinienaktualisierungen wirksam werden

#### Experience League-Ressourcen

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: E-Mail-Entscheidung | Option B: Web/App in Echtzeit | Option C: Journey-Entscheidungsknoten |
| --- | --- | --- | --- |
| Am besten geeignet für | Batch-E-Mail-Kampagnen mit Angebotsauswahl pro Empfänger | Echtzeit-Angebotsbanner auf Web-/App-Oberflächen | Angebotsauswahl in mehrstufigen orchestrierten Journeys |
| Entscheidungslatenz | Zum Sendezeitpunkt (Sekunden pro Empfänger während des Batch-Renderings) | Subsekunde (Edge Network) | Bei Ausführung des Journey-Knotens (Sekunden) |
| Kanal | E-Mail | Web, Mobile App, Code-basierte Oberflächen | Beliebiger Kanal (E-Mail, Push, SMS) innerhalb der Journey |
| SDK erforderlich | Nein | Ja (Web SDK oder Mobile SDK) | Nein (für E-Mail/Push); Ja (wenn der Webkanal eine Journey-Aktion ist) |
| Zielgruppenauswertung | Batch oder Streaming | Edge | Batch, Streaming oder Edge (je nach Journey-Eintrag) |
| Umfang der Profildaten | Vollständiges Hub-Profil | Edge-Profil (Teilmenge) | Vollständiges Hub-Profil |
| Komplexität | Niedrig | Medium-Hoch | Mittel |
| Durchsatz | Hoch (Batch-Kampagnenvolumen) | Hoch (Edge Network-Skala) | Medium (Journey-Durchsatzbeschränkungen gelten) |

### Wählen der richtigen Option

Verwenden Sie die folgenden Anleitungen, um die beste Implementierungsoption für Ihren Anwendungsfall auszuwählen.

- **Wählen Sie Option A**, wenn der primäre Anwendungsfall die Auswahl des besten Angebots pro Empfänger in ausgehenden E-Mail-Kampagnen ist und keine Client-seitige SDK verfügbar ist. Dies ist der einfachste Implementierungspfad und eignet sich gut für Werbe-E-Mails, Newsletter und Lebenszyklus-Kampagnen.
- **Option B auswählen** wenn Angebote in Echtzeit ausgewählt werden müssen, wenn ein Besucher eine Web-Seite lädt oder eine Mobile App öffnet. Dies erfordert Web SDK oder Mobile SDK und eine Edge-aktive Zusammenführungsrichtlinie, bietet jedoch die schnellste und kontextuellste Angebotsauswahl.
- **Wählen Sie Option C**, wenn die Angebotsentscheidung Teil einer umfassenderen Kunden-Journey mit mehreren Schritten, Wartezeiten und bedingter Verzweigung ist. Dies ist die richtige Wahl, wenn das ausgewählte Angebot nachgelagerte Journey-Aktionen beeinflussen soll oder wenn eine kanalübergreifende Weiterverfolgung auf der Grundlage der Angebotsinteraktion erforderlich ist.
- **Kombinieren von Optionen** wenn Angebote kanalübergreifend konsistent bereitgestellt werden müssen. Verwenden Sie dieselbe Entscheidungsrichtlinie für alle drei Optionen, um sicherzustellen, dass ein Kunde dasselbe Angebot in E-Mail (Option A), auf der Website (Option B) und im Rahmen eines Journey-Follow-ups (Option C) sieht.

## Implementierungsphasen

In den folgenden Phasen wird die End-to-End-Implementierungssequenz für Offer Decisioning beschrieben.

### Phase 1: Validieren der grundlegenden Voraussetzungen

**Anwendungsfunktion:** AEP: Datenmodellierung und -vorbereitung, AEP: Identitäts- und Profilkonfiguration

In dieser Phase wird überprüft, ob die grundlegende Datenschicht Offer Decisioning unterstützt. Profilschemata müssen die in den Eignungsregeln für Angebote verwendeten Attribute enthalten, und die Identitätskonfiguration muss eine kanalübergreifende Profilauflösung ermöglichen.

#### Entscheidung: Profilattribute für die Eignung

Legen Sie fest, welche Profilattribute in den Eignungsregeln des Angebots verwendet werden.

>[!NOTE]
>Die Auswahl von Profilattributen wirkt sich sowohl auf das Design von Eignungsregeln als auch auf die Effektivität der Rangfolgestrategie aus. Erwägen Sie berechnete Attribute und Tendenzwerte, um die Entscheidungsqualität zu verbessern.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Standardattribute (Treuestufe, Kaufverlauf) | Im Profilschema sind bereits Attribute vorhanden | Keine Schemaänderungen erforderlich; Datenaktualität überprüfen |
| Berechnete Attribute (Lebenszeitwert, Interaktionswert) | Die Eignung für das Ranking hängt von den aggregierten Verhaltensdaten ab | Erfordert S1-Konfiguration; fügt eine Abhängigkeit von der berechneten Aktualisierungskadenz des Attributs hinzu |
| Kunden-KI-Tendenzwerte | Die Rangfolge sollte ML-basierte Prognosen nutzen | Erfordert ausreichende Schulungsdaten (über 10.000 Profile mit Zielereignis); Modell der Schulungszeit |

#### Wichtige Konfigurationsdetails

- Überprüfen, ob das Profilschema Felder enthält, auf die in Eignungsregeln verwiesen wird (z. B. `_tenantId.loyaltyTier`, `_tenantId.subscriptionType`)
- Bestätigen, dass das Tracking-Schema für Angebotsinteraktionen für Impression-, Klick- und Konversionsereignisse vorhanden ist
- Für Option B: Überprüfen, ob die Edge-aktive Zusammenführungsrichtlinie konfiguriert ist und der Web SDK-Datenstrom den AJO-Service aktiviert hat

#### Dokumentation zu Experience League

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Aktivieren eines Schemas für das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Phase 2: Konfigurieren der Zielgruppenauswertung

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung

In dieser Phase werden die Zielgruppen definiert und ausgewertet, die als Kriterien für die Angebotseignung verwendet werden. Diese Zielgruppen bestimmen, welche Kundensegmente für bestimmte Angebote qualifiziert sind (z. B. qualifizieren sich „hochwertige Kunden“ für Premium-Angebote, „Testbenutzer“ für Konversionsangebote).

#### Entscheidung: Methode zur Zielgruppenauswertung

Legen Sie fest, wie schnell die Zielgruppenzugehörigkeit für die Angebotseignung aktualisiert werden muss.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch-Auswertung | Option A (E-Mail-Kampagnen), bei der die Eignung zum Zeitpunkt des Versands bewertet wird | Einfach; alle Segmentregelausdrücke werden unterstützt; tägliche oder On-Demand-Aktualisierung |
| Streaming-Auswertung | Option A oder C, wenn nahezu in Echtzeit stattfindende Zielgruppenaktualisierungen zwischen Batches erforderlich sind | Automatisch für geeignete Segmente; begrenzte Unterstützung von Segmentregeln (einzelne Ereignisse, Attributvergleiche) |
| Edge-Auswertung | Option B (Web/App in Echtzeit), bei der die Eignung beim Laden der Seite bewertet werden muss | Subsekunde; erforderlich für Web-/App-Angebote in Echtzeit; auf einfache Attributprüfungen und Segmentzugehörigkeit beschränkt |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

#### Wichtige Konfigurationsdetails

- Definieren Sie Zielgruppen für die Angebotseignung (z. B. „Treueprogramm-Gold-Stufe“, „hochwertige Kunden“, „Testbenutzer„).
- Definieren Sie Unterdrückungszielgruppen bei Bedarf (z. B. „Kürzlich empfangenes Angebot X„)
- Für Option B: Überprüfen, ob geeignete Zielgruppen für die Edge-Evaluierung qualifiziert sind - vermeiden Sie Zeitreihenabfragen und komplexe Aggregationen in Segmentregelausdrücken.

#### Wo die Optionen auseinander gehen

**Für Option A (E-Mail-Entscheidungsfindung):**
Batch- oder Streaming-Auswertung ist ausreichend. Audiences werden vor oder während der Ausführung der Kampagne ausgewertet. Komplexe Segmentregelausdrücke einschließlich zeitbasierter Bedingungen und Ereignisaggregationen werden vollständig unterstützt.

**Für Option B (Web/App in Echtzeit):**
Edge-Auswertung ist erforderlich. Zielgruppen müssen einfache Attributprüfungen oder Segmentzugehörigkeitsbedingungen verwenden. Testen Sie die Edge-Eignung, indem Sie überprüfen, ob der Segmentregelausdruck für die Edge-Segmentierung geeignet ist.

**Für Option C (Journey-Entscheidungsknoten):**
Jede Auswertungsmethode funktioniert abhängig von den Journey-Eingabekriterien. Wenn die Journey einen zielgruppenbasierten Eintrag verwendet, entspricht die Zielgruppenauswertungsmethode den Anforderungen der Journey.

#### Dokumentation zu Experience League

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Phase 3: Einrichten der Entscheidungsfindung

**Anwendungsfunktion:** AJO: Decisioning

Dies ist die Kernphase, in der der Angebotskatalog, Eignungsregeln, Rangfolgestrategien und Entscheidungsrichtlinien erstellt werden. In dieser Phase wird die Konfiguration der Entscheidungs-Engine erstellt, die alle Bereitstellungsoptionen (A, B, C) nutzen.

#### Entscheidung: Platzierungskanal und Inhaltsformat

Legen Sie fest, wo und in welchem Format Angebote angezeigt werden.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| E-Mail (HTML) | Option A - Angebotsinhalt, der im E-Mail-Textkörper als HTML gerendert wird | Unterstützt Rich-Formatierung; muss mit E-Mail-Clients kompatibel sein |
| E-Mail (Bild-URL) | Option A - Angebot, das als gehostetes Bild in E-Mails gerendert wird | Einfacher: Bild muss gehostet und zugänglich sein; kein dynamischer Text |
| Web (HTML) | Option B — Angebot, das als HTML auf einer Web-Seite gerendert wird | Vollständige Layout-Steuerung; unterstützt interaktive Elemente |
| Web/Mobile (JSON) | Option B - Als JSON für benutzerdefiniertes Rendering zurückgegebene Angebotsdaten | Maximale Flexibilität; erfordert Frontend-Entwicklung zum Rendern |
| Code-basiert (JSON) | Option B - Angebotsdaten für Code-basierte Erlebnisoberflächen | Anwendungs-Rendering steuert; flexibelste |

#### Entscheidung: Rangfolgestrategie

Legen Sie fest, wie das beste Angebot aus geeigneten Angeboten ausgewählt werden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Prioritätsbasiert (manuell) | Kleine Angebotskataloge; explizite Geschäftsregeln für die Angebotsbestellung | Einfachste Konfiguration; manuelle Zuweisung des Prioritätswerts pro Angebot; deterministisch |
| Formelbasiert (benutzerdefinierter Ausdruck) | Die Rangfolge sollte Profilattribute berücksichtigen (z. B. Treuestufe, Neuigkeit) | Flexibel; verwendet Profildaten zur Berechnung eines Rangfolgenwerts; erfordert Design von Segmentausdrücken |
| KI-Rangfolge (automatische Optimierung) | Große Angebotskataloge: ML soll die Auswahl im Laufe der Zeit optimieren | Erfordert mindestens 1.000 Konversionsereignisse für das Modell-Training. Lernt aus Daten zur Angebotsleistung |

#### Entscheidung: Angebotsbegrenzung

Legen Sie fest, ob es Beschränkungen für die Häufigkeit der Anzeige eines Angebots geben soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Obergrenze pro Profil | Verhindern, dass dasselbe Angebot einem Kunden zu oft angezeigt wird | Vermeidet Angebotsermüdung; Zählerverzögerung von einigen Sekunden in Szenarien mit hohem Durchsatz |
| Globale Begrenzung | Gesamtimpressionen für ein Angebot auf alle Profile begrenzen (z. B. begrenzter Bestand) | Steuert die Angebotsbereitstellung. Sobald die Obergrenze erreicht ist, wird das Angebot von Entscheidungen ausgeschlossen. |
| Keine Begrenzung | Angebote sind unbegrenzt verfügbar | Einfach; geeignet für ständig laufende Werbeaktionen |

**UI-Navigation:** Komponenten > Entscheidungs-Management > Platzierungen / Regeln / Angebote / Entscheidungen

#### Wichtige Konfigurationsdetails

1. **Platzierungen erstellen** - Definieren Sie, wo Angebote angezeigt werden, indem Sie den Kanaltyp und das Inhaltsformat für jede Platzierung angeben.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Platzierungen
   - Erstellen Sie eine Platzierung pro Kanal-/Formatkombination (z. B. „E-Mail-Hero-Banner - HTML&quot;, „Web-Homepage - JSON“, „Mobile-App-Karte - JSON„).

2. **Eignungsregeln definieren** - Erstellen Sie Regeln mithilfe von Segmentregelausdrücken, die auf Profilattribute oder die Zielgruppenzugehörigkeit verweisen.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Regeln
   - Regeln können auf Zielgruppenzugehörigkeit, Profilattribute (Treuestufe, Abonnementtyp), Datumsbeschränkungen oder kontextuelle Daten verweisen

3. **Personalisierte Angebote erstellen** - Erstellen Sie jedes Angebot mit Inhaltsdarstellungen für jede Platzierung, weisen Sie Eignungsregeln zu, legen Sie die Priorität fest und konfigurieren Sie eine optionale Begrenzung.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Angebote > Angebot erstellen
   - Jedes Angebot benötigt eine Inhaltsdarstellung pro Platzierung (z. B. HTML für E-Mail, JSON für Web)
   - Weisen Sie Eignungsregeln zu, um zu steuern, welche Profile die einzelnen Angebote sehen können
   - Festlegen des Gültigkeitsdatums des Angebots (Start/Ende) und optionale Frequenzlimitierung
   - Jedes Angebot validieren, um es für eine Entscheidung infrage zu stellen

4. **Fallback-Angebote erstellen** — Für jede Platzierung, die angezeigt wird, wenn kein personalisiertes Angebot geeignet ist, wird ein Standardangebot erstellt.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Angebote > Fallback-Angebot erstellen
   - Fallback muss für jede in der Entscheidung verwendete Platzierung repräsentativ sein

5. **Erstellen von Sammlungsqualifizierern und Sammlungen** - Organisieren Sie Angebote mithilfe von Qualifizierer-Tags in Sammlungen.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Sammlungsqualifizierer
   - Gruppenbezogene Angebote (z. B. „Sommerangebote“, „Treueprämien„) zur Verwendung in Entscheidungsumfängen

6. **Entscheidungsrichtlinien erstellen** - Binden Sie Platzierungen, Sammlungen, Rangfolgestrategien und Fallback-Angebote an ausführbare Entscheidungen.
   - Benutzeroberfläche: Komponenten > Entscheidungs-Management > Entscheidungen > Entscheidung erstellen
   - Jeder Entscheidungsumfang verknüpft eine Platzierung mit einer Sammlung und gibt die Rangfolgenmethode an

#### Dokumentation zu Experience League

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Erstellen von Sammlungsqualifizierern](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Konfigurieren von Kanal und Oberfläche

**Anwendungsfunktion:** AJO: Kanalkonfiguration

In dieser Phase werden die Kanaloberflächen konfiguriert, über die Angebote bereitgestellt werden. Die Konfiguration hängt davon ab, welche Implementierungsoptionen verwendet werden.

#### Entscheidung: Kanaltyp

Bestimmen Sie, welchen Messaging-Kanal der Anwendungsfall erfordert.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| E-Mail | Option A oder Option C mit E-Mail-Versand | Subdomain-Delegierung, IP-Pool, Absendereinstellungen erforderlich |
| Web | Option B für die Bereitstellung der Web-Oberfläche | Web-SDK und Datenstromkonfiguration erforderlich |
| In-App | Option B für Mobile-App-Bereitstellung | Mobile SDK und Push-Anmeldedaten erforderlich |
| Code-basiertes Erlebnis | Option B für benutzerdefinierte Rendering-Oberflächen | Am flexibelsten: Die Anwendung übernimmt das Rendering |

#### Wo die Optionen auseinander gehen

**Für Option A (E-Mail-Entscheidungsfindung):**
- Benutzeroberfläche: Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen (E-Mail)
- Konfigurieren von Subdomain, IP-Pool, Absendername/E-Mail, Antwort-an, Abmeldeeinstellungen
- Überprüfen der SPF-, DKIM- und DMARC-Einträge für die sendende Subdomain

**Für Option B (Web/App in Echtzeit):**
- Benutzeroberfläche: Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen (Web oder In-App)
- Für Web: Konfigurieren des URL-Musters der Web-Oberfläche
- Für Code-basierte Erlebnisse: Definieren der Oberflächen-URI für das Programm
- Überprüfen, ob für den Datenstrom der AJO-Service aktiviert ist

**Für Option C (Journey-Entscheidungsknoten):**
- Kanaloberflächen für jeden Kanal konfigurieren, der in der Journey verwendet wird (E-Mail, Push, SMS oder Web)
- Jede Journey-Nachrichtenaktion erfordert eine entsprechende aktive Kanaloberfläche

#### Dokumentation zu Experience League

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5: Konfigurieren von Inhalt und Bereitstellung

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung, AJO: Kampagnenausführung

In dieser Phase werden die Nachrichtenvorlagen oder Erlebnisoberflächen entworfen, die das ausgewählte Angebot anzeigen, und dann der Versandmechanismus (Kampagne, Journey oder Code-basiertes Erlebnis) konfiguriert.

#### Entscheidung: Inhaltsansatz für die Angebotswiedergabe

Legen Sie fest, wie der Angebotsinhalt in die Nachricht oder das Erlebnis integriert werden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Komponente Angebotsentscheidung in E-Mail-Designer | Option A - Platzierung von Angeboten in E-Mail-Vorlage einbetten | Drag-and-Drop; Angebotsinhalte werden basierend auf dem Entscheidungsergebnis automatisch gerendert |
| Code-basiertes Erlebnis mit Entscheidungsrichtlinie | Option B — Das Programm ruft Angebotsdaten ab und rendert sie | Maximale Kontrolle über das Rendering; Frontend-Entwicklung erforderlich |
| Journey-Nachrichtenaktion mit eingebetteter Entscheidung | Option C - Entscheidungsknoten-Feeds bieten Inhalt an Journey-Nachricht | Angebotsauswahl und Versand werden im Journey-Ablauf orchestriert |

#### Entscheidung: Kampagnentyp (nur Option A)

Ermitteln, ob es sich um eine geplante Marketing-Kampagne oder eine API-ausgelöste Kampagne handelt.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Geplante Kampagne | Einmalige oder wiederkehrende Batch-Sendungen an eine definierte Zielgruppe | Zielgruppe zur Ausführungszeit ausgewertet; Datum/Uhrzeit oder Wiederholung festlegen |
| API-ausgelöste Kampagne | Ereignisgesteuerte oder systemausgelöste Sendungen an bestimmte Profile | In der Trigger-Payload angegebene Profile; unterstützt bis zu 20 Empfänger pro Anfrage |

#### Wo die Optionen auseinander gehen

**Für Option A (E-Mail-Entscheidungsfindung):**

1. Verfassen Sie die E-Mail-Nachricht mit der E-Mail-Designer
   - Benutzeroberfläche: Kampagnen > Kampagne erstellen > E-Mail auswählen > Inhalt bearbeiten
   - Fügen Sie eine Angebotsentscheidungs -Komponente in das E-Mail-Layout ein, um die Platzierungszone zu definieren
   - Personalisierungs-Token für Inhalte auf Profilebene hinzufügen (Name, Treuestufe)
   - Konfigurieren von Betreffzeile und Preheader mit optionaler Personalisierung
2. Erstellen und Konfigurieren der Kampagne
   - Benutzeroberfläche: Kampagnen > Kampagne erstellen > Geplant oder API-ausgelöst
   - Binden der Zielgruppe und Auswählen der Kanaloberfläche
   - Festlegen des Ausführungsplans oder der API-Trigger-Konfiguration
   - Kampagne überprüfen und aktivieren

**Für Option B (Web/App in Echtzeit):**

1. Konfigurieren des Code-basierten Erlebnisses oder Webkanals
   - Benutzeroberfläche: Kampagnen > Kampagne erstellen > Code-basiertes Erlebnis (oder Web)
   - Verknüpfen der Entscheidungsrichtlinie mit der Erlebnisoberfläche
   - Rendering-Format definieren (JSON-Antwort für Code-basierten Visual Editor für Webkanal)
2. Client-seitiges Rendering implementieren
   - Verwenden Sie die Web SDK `sendEvent`-Antwort, um das ausgewählte Angebot abzurufen
   - Rendern des Angebotsinhalts an der vorgesehenen Platzierung auf der Seite
   - Implementieren von Impression- und Klick-Tracking

**Für Option C (Journey-Entscheidungsknoten):**

1. Entwerfen der Journey mit einem Entscheidungsknoten
   - Benutzeroberfläche: Journey > Journey erstellen > Entscheidungsknoten hinzufügen
   - Konfigurieren Sie den Entscheidungsknoten, um die Entscheidungsrichtlinie aus Phase 3 aufzurufen
2. Hinzufügen von Nachrichtenaktionsknoten nach der Entscheidung
   - Konfigurieren von E-Mail-, Push- oder SMS-Aktionen, die auf das ausgewählte Angebot verweisen
   - Hinzufügen von Warteschritten, Bedingungen oder Verzweigungen basierend auf der Angebotsinteraktion
3. Journey veröffentlichen

#### Dokumentation zu Experience League

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Phase 6: Testen und Validieren

**Anwendungsfunktion:** AJO: Decisioning, AJO: Nachrichtenbearbeitung

In dieser Phase wird überprüft, ob die Decisioning-Engine die richtigen Angebote für Testprofile zurückgibt und ob der Angebotsinhalt in jedem Versandkanal ordnungsgemäß gerendert wird.

#### Entscheidungslogik testen

Verwenden Sie Testprofile mit bekannten Attributen, um zu überprüfen, ob die richtigen Angebote basierend auf Eignung und Ranking ausgewählt wurden.

- Erstellen von Testprofilen, die unterschiedlichen Eignungskriterien entsprechen (z. B. Gold-Stufe, Silber-Stufe, Testbenutzer)
- Überprüfen Sie, ob jedes Testprofil das erwartete Angebot erhält
- Überprüfen Sie, ob Profile, die keinen Eignungsregeln entsprechen, das Fallback-Angebot erhalten

#### Testen des Inhalts-Renderings

Anzeigen des Angebotsinhalts in jedem Versandkanal in der Vorschau.

- Für Option A: Verwenden Sie die E-Mail-Vorschau mit Testprofilen, um zu überprüfen, ob der Angebotsinhalt korrekt dargestellt wird
- Für Option B: Testen der Edge Decisioning-Antwort in einer Staging-Umgebung
- Für Option C: Verwenden Sie den Journey-Testmodus, um zu überprüfen, ob der Entscheidungsknoten korrekt ausgewählt wird

#### Impression-Tracking validieren

Vergewissern Sie sich, dass Angebotsimpressionen, Klicks und Konversionen verfolgt werden.

- Überprüfen Sie, ob die Interaktionsereignisse des Angebots in den Tracking-Datensätzen angezeigt werden
- Attribution zwischen Angebotsimpressionen und nachgelagerten Konversionen bestätigen

#### Dokumentation zu Experience League

- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [E-Mail-Testsendungen durchführen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### Phase 7: Konfigurieren von Reporting und Leistungsüberwachung

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse

In dieser Phase wird ein Reporting zur Nachverfolgung der Angebotsauswahl, der Verteilung der Akzeptanzraten, der Konversionsauswirkungen und der Fallback-Raten eingerichtet. In dieser Phase werden sowohl native Berichte von AJO als auch die CJA-basierte kanalübergreifende Analyse behandelt.

#### Entscheidung: Berichtsmethode

Bestimmen Sie, welche Reporting-Tools für die Analyse der Angebotsleistung benötigt werden.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native AJO-Berichte | Operative Überwachung von Einzelkampagnen oder Journey | Schnellzugriff; integrierte Versand- und Interaktionsmetriken; eingeschränkte entitätsübergreifende Analyse |
| CJA Workspace-Analyse | Kanalübergreifende Angebotseffektivität, Umsatzzuordnung, funnel-Analyse | Erfordert CJA-Verbindung und Datenansicht; tiefere Analysefunktionen |
| Sowohl AJO als auch CJA | Vollständige operationelle und analytische Abdeckung | Empfohlen für Produktionsimplementierungen; AJO für Echtzeit-Überwachung, CJA für strategische Analysen |

#### Wichtige Konfigurationsdetails

1. **Natives Reporting in AJO** - Überwachen Sie die Kampagnen- oder Journey-Performance mithilfe integrierter Berichte.
   - Benutzeroberfläche: Kampagnen > Kampagne auswählen > Alle Zeitberichte (oder Live-Bericht)
   - Überprüfen der angebotsspezifischen Metriken: Impressionen pro Angebot, Klickrate pro Angebot, Fallback-Rate
   - Versand überwachen funnel: Zielgruppe > Gesendet > Zugestellt > Öffnungen > Klicks

2. **CJA-Analyse (empfohlen)** - Erstellen von kanalübergreifenden Angebots-Performance-Dashboards.
   - Konfigurieren einer CJA-Verbindung einschließlich AJO-Angebotsinteraktions-Datensätzen
   - Erstellen Sie eine Datenansicht mit angebotsspezifischen Dimensionen (Angebotsname, Platzierung, Entscheidung) und Metriken (Impressionen, Klicks, Konversionen)
   - Arbeitsbereich erstellen für Analyse: Angebotsauswahl, Verteilung der Akzeptanzrate nach Segment, Auswirkungen auf den Umsatz, Konsistenz der kanalübergreifenden Angebote

#### Dokumentation zu Experience League

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## Überlegungen bei der Implementierung

Dieser Abschnitt enthält Informationen zu Leitplanken, allgemeinen Fallstricken, Best Practices und Entscheidungen bei der Entscheidungsfindung bei Offer Decisioning-Implementierungen.

### Leitplanken und Beschränkungen

Beachten Sie die folgenden Leitplanken und Einschränkungen bei der Planung Ihrer Implementierung.

- Maximal 10.000 genehmigte personalisierte Angebote pro Sandbox - [Leitplanken im Entscheidungs-Management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 30 Platzierungen pro Entscheidung
- Maximal 30 Sammlungsbereiche pro Entscheidungsanfrage
- KI-Rangfolgemodelle erfordern mindestens 1.000 Konversionsereignisse für das Training.
- Angebotsbegrenzungszähler können in Szenarien mit hohem Durchsatz eine Verzögerung von bis zu einigen Sekunden aufweisen
- Edge-Entscheidungen sind auf Profilattribute beschränkt, die im Edge-Profilspeicher verfügbar sind
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Platform-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Pro Sandbox kann nur eine Zusammenführungsrichtlinie in Edge aktiv sein
- Maximal 500 aktive Live-Kampagnen pro Sandbox
- Journey-Einstiegsrate-Limit: 5.000 Profile pro Sekunde
- Maximal 10 Kanaloberflächen pro Kanaltyp pro Sandbox

### Häufige Fehler

Vermeiden Sie diese häufig auftretenden Probleme während der Implementierung.

- **Entscheidung gibt immer Fallback-Angebot zurück:** Dies bedeutet in der Regel, dass personalisierte Angebote nicht genehmigt werden, außerhalb des Gültigkeitsdatums liegen oder die Eignungsregeln nicht mit den Attributen des Testprofils übereinstimmen. Überprüfen Sie jede Bedingung: Genehmigungsstatus, Datumsbereich und Genauigkeit des Segmentausdrucks. Stellen Sie außerdem sicher, dass die Begrenzungen nicht erreicht wurden.
- **Angebot wird nicht in Sammlung angezeigt** Stellen Sie sicher, dass das Angebot mit dem richtigen Sammlungsqualifizierer getaggt wurde und dass der Sammlungsfilter übereinstimmt. Angebote müssen sowohl getaggt als auch genehmigt sein, damit sie in sammlungsbasierten Entscheidungsumfängen angezeigt werden.
- **Rangfolgenformel nicht angewendet:** Überprüfen Sie, ob die Formel syntaktisch gültig ist und auf barrierefreie Profilattribute verweist. Formelfehler kehren im Hintergrund zur prioritätsbasierten Rangfolge zurück, ohne dass ein Fehler sichtbar ist.
- **Edge-Versand gibt eine leere Personalisierung zurück:** Stellen Sie sicher, dass der Datenstrom mit aktiviertem [!DNL Adobe Journey Optimizer]-Service konfiguriert ist und dass der Entscheidungsumfang korrekt formatiert ist. Überprüfen Sie, ob die Edge-aktive Zusammenführungsrichtlinie vorhanden ist.
- **Inkonsistente Angebote über verschiedene Kanäle hinweg:** Wenn separate Entscheidungsrichtlinien pro Kanal verwendet werden, kann dasselbe Profil verschiedene Angebote erhalten. Verwenden Sie eine einzige Entscheidungsrichtlinie für alle Kanäle, um Konsistenz zu gewährleisten, oder akzeptieren Sie absichtliche Abweichungen basierend auf kanalspezifischen Platzierungen.
- **Angebotsinhalte werden nicht in E-Mails gerendert** Überprüfen Sie, ob das Angebot über eine Inhaltsdarstellung verfügt, die dem E-Mail-Platzierungsformat (HTML oder Bild-URL) entspricht. Fehlende Darstellungen führen zu leeren Platzierungszonen.

### Best Practices

Befolgen Sie diese Empfehlungen für eine erfolgreiche Offer Decisioning-Implementierung.

- **Beginnen Sie mit einem kleinen Angebotskatalog und iterieren Sie** - Beginnen Sie mit 5 bis 10 Angeboten und erweitern Sie sie, wenn das Entscheidungs-Framework validiert wird. Dies vereinfacht die Fehlerbehebung und stellt sicher, dass die Eignungsregeln vor der Skalierung korrekt funktionieren.
- **Sammlungsqualifizierer strategisch verwenden** - Taggen Sie Angebote nach Kategorie (z. B. Akquise, Bindung, Upsell), um flexible sammlungsbasierte Entscheidungsumfänge zu ermöglichen, die in Kampagnen und Journey wiederverwendet werden können.
- **Erstellen Sie immer aussagekräftige Fallback**-Angebote - Fallback-Angebote sind nicht nur ein Sicherheitsnetz, sondern das Standarderlebnis für Profile, die keiner Eignungsregel entsprechen. Investieren Sie in Fallback-Inhalte, die auch ohne Personalisierung Mehrwert bieten.
- **Eignungsregeln sollten nach Möglichkeit gegenseitig ausschließen** Wenn sich die Eignungskriterien mehrerer Angebote überschneiden, wird die Rangfolgestrategie kritisch. Wenn geschäftliche Anforderungen ein bestimmtes Angebot für ein bestimmtes Segment erfordern, schließen sich die Eignungsregeln gegenseitig aus und verlassen sich nicht nur auf das Ranking.
- **Testen mit Edge-repräsentativen Profilen für Option B** - Edge-Profile enthalten eine Untergruppe von Hub-Profilattributen. Testen Sie mit Profilen, die über Edge-verfügbare Attribute verfügen, um sicherzustellen, dass die Eignung in der Produktion korrekt ausgewertet wird.
- **Fallback-Raten als Konsistenzmetrik überwachen** - Eine hohe Fallback-Rate (über 20-30 %) deutet darauf hin, dass der Angebotskatalog nicht genügend Kundensegmente abdeckt. Erweitern Sie den Angebotskatalog oder erweitern Sie die Eignungsregeln.
- **Entscheidungsrichtlinien versionieren anstatt Live-Richtlinien zu bearbeiten** - Erstellen Sie eine neue Version der Entscheidungsrichtlinie, anstatt eine aktive zu ändern. Dies verhindert Unterbrechungen von Live-Kampagnen und ermöglicht A/B-Vergleiche von Entscheidungsstrategien.

### Entscheidungen über Kompromisse

Beachten Sie bei Architektur- und Konfigurationsentscheidungen die folgenden Kompromisse.

#### Eignungsgenauigkeit vs. Angebotsabdeckung

Strenge Eignungsregeln stellen sicher, dass jedes Angebot nur die relevantesten Profile erreicht, können jedoch zu hohen Fallback-Raten führen, wenn die Profile mit keinem Angebot übereinstimmen. Umfassende Eignungsregeln maximieren die Angebotsabdeckung, verringern jedoch die Personalisierungsgenauigkeit.

- **Enge Eignungsfavoriten:** Höhere Akzeptanzraten, bessere Personalisierung, geringere Angebotsmüdigkeit
- **Umfassende Eignungsfavoriten:** Niedrigere Fallback-Raten, mehr Profile erhalten personalisierte Angebote, einfachere Regelverwaltung
- **Empfehlung:** Sie mit umfassenderen Eignungsregeln beginnen und diese auf der Grundlage von Leistungsdaten verschärfen. Überwachen Sie Fallback-Raten und Akzeptanzraten, um das richtige Gleichgewicht zu finden. Verwenden Sie Rangfolgestrategien, um zwischen allgemein geeigneten Angeboten zu unterscheiden.

#### Prioritätsbasiert vs. KI-Rangfolge

Das prioritätsbasierte Ranking gibt dem Unternehmen die volle Kontrolle darüber, welche Angebote angezeigt werden, während das KI-Ranking für die Konversion optimiert ist, aber die menschliche Kontrolle über die Angebotsauswahl reduziert.

- **Prioritätsbasierte Vorteile:** Geschäftskontrolle, Vorhersehbarkeit, keine Anforderung von Schulungsdaten, sofortige Bereitstellung
- **KI-Rangfolge-Favoriten:** Konversionsoptimierung, Erkennung unerwarteter Muster, automatische Anpassung an sich änderndes Kundenverhalten
- **Empfehlung:** Verwenden Sie die prioritätsbasierte Rangfolge für erste Launches und regulatorisch sensible Angebote, bei denen die Geschäftssteuerung von größter Bedeutung ist. Der Wechsel zur KI-Rangfolge für leistungsoptimierte Anwendungsfälle mit hohem Volumen erfolgt, sobald ausreichende Konversionsdaten (über 1.000 Ereignisse) verfügbar sind.

#### Richtlinien zu einzelnen Entscheidungen im Vergleich zu Richtlinien pro Kanal

Eine einzige Entscheidungsrichtlinie gewährleistet die Angebotskonsistenz über alle Kanäle hinweg, beschränkt jedoch die Optimierung pro Kanal. Kanalspezifische Richtlinien ermöglichen eine kanalspezifische Rangfolge und Eignung, bergen jedoch das Risiko inkonsistenter Kundenerlebnisse.

- **Eine Richtlinie begünstigt** Kanalübergreifende Konsistenz, einfacheres Management, einheitliches Reporting
- **Richtlinien pro Kanal begünstigen:** kanaloptimierte Rangfolge, kanalspezifische Eignung (z. B. Nur-Web-Angebote), unabhängige Iteration
- **Empfehlung** Beginnen Sie mit einer einzigen Entscheidungsrichtlinie für Cross-Channel-Konsistenz. Erstellen Sie Richtlinien pro Kanal nur, wenn geschäftliche Anforderungen kanalspezifische Angebotsstrategien erfordern (z. B. Vertrieb ausschließlich über das Web).

#### Hub Decisioning (Option A/C) vs. Edge Decisioning (Option B)

Hub Decisioning hat Zugriff auf das gesamte Profil, funktioniert jedoch zum Sendezeitpunkt. Edge Decisioning arbeitet in Echtzeit mit einer Latenz von Unter-Sekunden, ist jedoch auf Edge-verfügbare Profilattribute beschränkt.

- **Hub-Entscheidungsvorteile:** Zugriff auf vollständige Profildaten, komplexe Eignungsregeln, Batch-Kampagnen-Volumes
- **Edge Decisioning-Vorteile:** Echtzeit-Kontext, Personalisierung in der Sitzung, Antwort in Untersekunden
- **Empfehlung:** Verwenden von Hub Decisioning für ausgehende Kanäle (E-Mail, Push), bei denen vollständige Profildaten die Angebotsrelevanz verbessern. Verwenden Sie Edge Decisioning für eingehende Kanäle (Web, App), bei denen die Echtzeit-Antwort wichtig ist. Stellen Sie sicher, dass die Eignungsregeln nur für Edge-verfügbare Attribute verwendet werden.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den Komponenten, die in diesem Anwendungsfallmuster verwendet werden.

### Entscheidungs-Management

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Erstellen von Sammlungsqualifizierern](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Angebotsversand

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Unterbreiten von Angeboten mithilfe der Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Kampagnen und Journey

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Inhaltsexperiment

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profil und Identität

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Datenmodellierung und -erfassung

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Reporting und Analysen

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Data Governance und Lebenszyklus

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutorials

- [Entscheidungs-Management-API - Erste Schritte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
