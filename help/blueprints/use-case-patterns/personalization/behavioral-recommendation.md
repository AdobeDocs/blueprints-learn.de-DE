---
title: Verhaltensempfehlung
description: Erfahren Sie, wie Sie Element- und Inhaltsempfehlungen mithilfe von Auswahlstrategien und Rangfolgemodellen generieren.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7626'
ht-degree: 2%

---


# Verhaltensempfehlung

In diesem Handbuch wird beschrieben, wie Sie verhaltensbezogene Produkt- und Inhaltsempfehlungen mithilfe von [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP) implementieren. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die personalisierte Empfehlungserlebnisse über Web-, Mobile-App- und E-Mail-Kanäle bereitstellen müssen.

Es enthält alle praktikablen Implementierungsoptionen, Entscheidungsüberlegungen für jede Phase und Links zu [!DNL Adobe Experience League] Dokumentation. Verhaltensempfehlungen generieren Empfehlungen auf Element- oder Inhaltsebene mithilfe von Verhaltenssignalen - Produktansichten, Käufe, Inhaltsinteraktionen, Suchabfragen - in Kombination mit AJO-Entscheidungsauswahlstrategien und Ranking-Modellen. Im Gegensatz zu Offer Decisioning, das anhand expliziter Eignungsregeln aus einem kuratierten Satz von Marketing-Angeboten auswählt, funktioniert dieses Muster für große Elementkataloge (Produkte, Artikel, Videos) und verwendet verhaltensbezogene Affinitätssignale und ein ML-basiertes Ranking, um die relevantesten Elemente für jeden Besucher zu ermitteln.

## Anwendungsfall - Übersicht

Organisationen mit Produktkatalogen, Inhaltsbibliotheken oder Medienbibliotheken müssen für jeden Besucher die relevantesten Elemente basierend auf seinem Verhaltensverlauf und seiner Aktivität während der Sitzung aufdecken. Unabhängig davon, ob es sich um ein „empfohlenes“ Karussell auf einer Homepage, ein Crosssell-Widget auf einer Produktdetailseite oder Produktempfehlungen handelt, die in eine E-Mail-Kampagne eingebettet sind, ist die zugrunde liegende Herausforderung dieselbe: Ordnen Sie das Verhaltensprofil jedes Besuchers den relevantesten Elementen aus einem Katalog zu und stellen Sie diese Empfehlungen dann im richtigen Moment im richtigen Kanal bereit.

Dieses Muster löst diese Herausforderung, indem es Verhaltenssignale in Echtzeit über [!DNL Web SDK] oder [!DNL Mobile SDK] aufnimmt, sie über AJO Decisioning-Auswahlstrategien verarbeitet, die Elementattribute mit Verhaltenskontext kombinieren, und die empfohlenen Elemente über Web-, In-App- oder E-Mail-Kanäle bereitstellt. Rangfolgemodelle können formularbasiert (z. B. nach Kategorieaffinitätswert sortiert) oder KI-geordnet (z. B. personalisiertes Empfehlungsmodell) sein. Das Muster behandelt auch Kaltstart-Szenarien für neue Besucher ohne Verhaltensverlauf, indem es Fallback-Empfehlungen konfiguriert.

Die Zielgruppe für dieses Muster umfasst E-Commerce-Merchandising-Teams, Personalisierungs-Teams für Inhalte und Teams für digitale Erlebnisse, die durch personalisierte Empfehlungen, die auf echtem Benutzerverhalten basieren, die Interaktion, Konversion und den durchschnittlichen Bestellwert verbessern möchten.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### [Umsatz durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.

| KPI | Beschreibung |
| --- | --- |
| Upsell/Crosssell % | Prozentsatz der Kundinnen und Kunden, die empfohlene ergänzende oder Premium-Artikel kaufen |
| Inkrementeller Umsatz | Zusätzliche Umsätze aufgrund empfohlener Käufe |
| Customer Lifetime Value | Langfristige Wertsteigerung durch tiefere Produktinteraktion |

### [Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Verbessern Sie den Prozentsatz der Besucher und Interessenten, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen.

| KPI | Beschreibung |
| --- | --- |
| Konversionsraten | Prozentsatz der Besucherinnen und Besucher, die nach der Interaktion mit Empfehlungen konvertieren |
| Lead-Konversion | Rate, mit der Besucherinnen und Besucher, die mit Empfehlungen interagieren, Kunden werden |
| Kosten pro Lead | Reduzierung der Anschaffungskosten durch die Einbindung organischer Empfehlungen |

### [Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.

| KPI | Beschreibung |
| --- | --- |
| Interaktion | Interaktionshäufigkeit mit Empfehlungsflächen (Klicks, Ansichten, Zum Warenkorb hinzufügen) |
| Konversionsraten | Steigerung der Konversionsraten bei Besuchern, die an Recommendations gebunden sind, im Vergleich zur Kontrolle |
| Kundenzufriedenheit (CSAT) | Verbesserung der Kundenzufriedenheit durch relevante, personalisierte Erlebnisse |

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie häufige taktische Implementierungen dieses Musters:

- Produkt-Crosssell-Widget auf der Produktdetailseite („Kunden haben auch gekauft„)
- Karussell „Empfohlen für Sie“ auf der Startseite basierend auf dem Durchsuchen-Verlauf
- Inhaltsempfehlungen auf der Media-Site basierend auf dem Leseverhalten
- Widget „Kürzlich angesehen“ mit ähnlichen Elementen kombiniert
- Ergänzende Produktempfehlungen nach dem Kauf
- E-Mail-Produktempfehlungen basierend auf der Affinität zum Verhalten
- Kategoriespezifische Empfehlungen, die auf dem Verhalten beim Durchsuchen während der Sitzung basieren
- Neureihung von Suchergebnissen basierend auf Verhaltenssignalen

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen dabei, die Effektivität der Implementierungen von Verhaltensempfehlungen zu messen.

| KPI | Messansatz |
| --- | --- |
| Klickrate für Empfehlungen (CTR) | Klicks auf empfohlene Elemente dividiert durch Empfehlungsimpressionen |
| Konversionsrate der Empfehlung | Käufe oder gewünschte Aktionen aus Empfehlungsklicks dividiert durch die Gesamtzahl der Empfehlungsklicks |
| Durch Recommendations beeinflusster Umsatz | Gesamtumsatz aus Bestellungen, die mindestens ein empfehlungsgesteuertes Produkt enthalten |
| Steigerung des durchschnittlichen Bestellwerts (AOV) | Erhöhung der AOV für Sitzungen, die mit Recommendations interagiert haben, im Vergleich zu Sitzungen ohne |
| Artikel pro Bestellung | Anzahl der Artikel pro Bestellung für Sitzungen, die mit Empfehlungen interagieren |
| Umfang der Empfehlung | Prozentsatz der zulässigen Seitenansichten oder Sitzungen, die personalisierte (Nicht-Fallback-)Empfehlungen erhalten haben |
| Kaltstart-Ausweichrate | Prozentsatz der Empfehlungsanfragen, die von der Fallback-Logik aufgrund eines unzureichenden Verhaltensverlaufs bereitgestellt wurden |

## Anwendungsfallmuster

**Verhaltensempfehlung**

Generieren Sie Empfehlungen auf Element- oder Inhaltsebene basierend auf Verhaltenssignalen, indem Sie AJO-Entscheidungsauswahlstrategien und Rangfolgemodelle verwenden, um kontextuelle Inhalte bereitzustellen.

**Funktionskette:** Aufnahme von Verhaltenssignalen > Bewertung der Entscheidungsstrategie > Empfehlungsversand > Reporting

Anleitungen zum Kombinieren von Mustern finden Sie im Abschnitt zur Musterkomposition unter Implementierungsüberlegungen .

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO) Decisioning** - Auswahlstrategien, Rangfolgemodelle, Elementkataloge und Entscheidungsrichtlinien, die Verhaltenssignale auswerten und für jeden Besucher die relevantesten Elemente zurückgeben
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Akkumulation von Verhaltensprofildaten, Zielgruppenbewertung für das Recommendations-Scoping und berechnete Attribute für die Bewertung der Affinität im Verhalten
- **[!DNL Adobe Experience Platform] (AEP)** - Aufnahme von Verhaltensereignissen über [!DNL Web SDK] und [!DNL Mobile SDK], [!DNL Edge Network] Verarbeitung, XDM-Schemaverwaltung für Ereignis- und Katalogdaten

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit aktivierten Entscheidungsberechtigungen. Benutzerrollen, die Zugriff auf die Verwaltung des Elementkatalogs, die Konfiguration der Auswahlstrategie und die Verwaltung der Kanaloberfläche erhalten. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Erlebnisereignis-Schema, das Verhaltenssignale (Produktansichten, Hinzufügungen zum Warenkorb, Käufe, Inhaltsinteraktionen) mit Element-/Produktkennungen erfasst. Artikelkatalogschema (Produktattribute, Kategorien, Bilder, Preise) für das Empfehlungselement festgelegt. Profilschema mit Identitätsfeldern Alle Schemata für [!DNL Real-Time Customer Profile] aktiviert. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition), [Erstellen eines Datensatzes](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| Datenquellen und Sammlung | Erforderlich | Das Echtzeit-Streaming von verhaltensbezogenen Ereignissen über [!DNL Web SDK] oder [!DNL Mobile SDK] ist von entscheidender Bedeutung. Die Qualität der Empfehlungen hängt von neuen Verhaltenssignalen ab. Artikelkatalogdaten müssen aufgenommen werden (Batch oder Streaming). Datenströme, die mit für Edge Decisioning aktiviertem AJO-Service konfiguriert wurden. | [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identitäts- und Profilkonfiguration | Erforderlich | Verhaltenssignale müssen einer Identität (bekannt oder anonym über ECID) zugeordnet werden, um Verhaltensprofile zu erstellen. Für Empfehlungen für bekannte Besucher muss eine authentifizierte Identität (CRM-ID, E-Mail) konfiguriert werden. Auf Edge aktive Zusammenführungsrichtlinie für die Bereitstellung von Echtzeit-Empfehlungen. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Empfohlen | Zielgruppen können verwendet werden, um Empfehlungen zu definieren (z. B. nur Premium-Produkte an Premium-Mitglieder weiterempfehlen) oder um zu filtern. Nicht unbedingt erforderlich, wenn Empfehlungen rein verhaltensbezogen sind. Erforderlich für E-Mail-basierte Empfehlungen (Option C), um die Zielgruppe zu definieren. | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie Kategorieaffinitätswerte, Interaktionshäufigkeit des Produkts, Kaufhäufigkeit und Gesamtausgaben verbessern die Qualität des Empfehlungs-Rankings. [!DNL Customer AI] Tendenz-Scores können die Relevanz weiter steigern, indem sie die Kaufwahrscheinlichkeit vorhersagen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Empfohlen | Verhaltensereignisdaten sollten über geeignete Ablaufrichtlinien verfügen - die Relevanz der Empfehlung verschlechtert sich mit veralteten Daten. Das Festlegen von Richtlinien zur Datensatzgültigkeit für Verhaltensereignis-Datensätze stellt die Aktualität sicher und verwaltet die Speicherung. Die Durchsetzung des Einverständnisses stellt die konforme Verwendung von Verhaltensdaten sicher. | [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [Übersicht über das erweiterte Daten-Lifecycle-Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für Verhaltensdaten stellen sicher, dass der Interaktionsverlauf für Empfehlungen konform verwendet wird. Dies ist besonders wichtig, wenn Verhaltensdaten Suchmuster, Kaufverlauf oder Signale über Gesundheit/Finanzprodukt-Interessen umfassen. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Empfohlen | Die Latenz des Empfehlungsversands, Fallback-Raten und der Aufnahmestatus des Elementkatalogs sollten überwacht werden. Warnhinweise zu Fehlern bei der Aufnahme von Verhaltensereignissen und Entscheidungsfehlern helfen bei der Aufrechterhaltung der Empfehlungsqualität. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Reporting und Analyse | Eingeschlossen | Die Leistungsberichterstattung für Recommendations ist Teil der Funktionskette in Schritt 4. [!DNL Customer Journey Analytics] Die Analyse der Effektivität von Empfehlungen, der Auswirkungen auf den Umsatz und der Leistung auf Elementebene auf allen Oberflächen und Segmenten bietet Optimierungseinblicke. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Entscheidungsfindung | Einrichten von Artikelkatalog und Auswahlstrategie | Konfigurieren von Elementkatalogen (Entscheidungselementen), Auswahlstrategien mit Verhaltens-Ranking-Modellen, Filterregeln und Fallback-Empfehlungen |
| Kanalkonfiguration | Kanal- und Oberflächenkonfiguration | Konfigurieren von Versandoberflächen für Web- (Code-basierte Erlebnisse), In-App-, Inhaltskarten- oder E-Mail-Kanäle, in denen Empfehlungen gerendert werden |
| Verfassen von Nachrichten | Konfiguration von Inhalten und Bereitstellung | Design Recommendations-Rendering-Vorlagen, Layouts für Elementanzeigen und Personalisierungsausdrücke für empfohlene Elemente |
| Reporting und Leistungsanalyse | Reporting und Optimierung | Überwachen von Recommendations-Clickthrough-, Konversions- und Umsatzmetriken über native AJO-Berichte und [!DNL Customer Journey Analytics] |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Zielgruppen-Scoping (Option C) | Auswerten von Zielgruppensegmenten, die zum Definieren von Recommendations oder der Zielpopulation für E-Mail-Recommendations-Kampagnen verwendet werden |
| Profilanreicherung | Anreicherung von Verhaltenssignalen | Profile mit berechneten Attributen anreichern (Kategorieaffinitätswerte, Interaktionshäufigkeit), die das Recommendations-Ranking verbessern |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen:

- AJO Decisioning wird in der Ziel-Sandbox bereitgestellt und aktiviert
- [!DNL Web SDK] oder [!DNL Mobile SDK] wird bereitgestellt und erfasst Verhaltensereignisse mit Produkt-/Inhaltskennungen
- Produkt- oder Inhaltskatalogdaten stehen zur Aufnahme zur Verfügung (Produktname, Kategorie, Preis, Bild-URL, Verfügbarkeit)
- Verhaltensereignisschemata enthalten Element-/Produktkennungen, die mit Katalogelementen verknüpft sind
- Datenstrom wird mit aktiviertem [!DNL Adobe Journey Optimizer]-Service konfiguriert (erforderlich für Edge Decisioning)
- Zusammenführungsrichtlinie mit `isActiveOnEdge: true` ist konfiguriert (erforderlich für Web-/App-Empfehlungen in Echtzeit)
- Für E-Mail-Empfehlungen (Option C): Die E-Mail-Kanaloberfläche ist konfiguriert und validiert
- Für E-Mail-Empfehlungen (Option C): Die Zielgruppe wird definiert und ausgewertet

## Implementierungsoptionen

Die folgenden Optionen beschreiben verschiedene Ansätze zur Implementierung von Verhaltensempfehlungen. Wählen Sie die Option aus, die Ihren Kanalanforderungen und technischen Einschränkungen am besten entspricht.

### Option A: Web-Echtzeitempfehlungen

**Am besten geeignet für:** Produkt- oder Inhaltsempfehlungen auf Web-Seiten - Crosssell-Widgets für Produktdetailseiten, Karussells für Homepage-Empfehlungen, personalisierte Listen für Kategorieseiten und Personalisierung von Suchergebnissen.

**Funktionsweise:**

Verhaltenssignale werden in Echtzeit über [!DNL Web SDK] erfasst, während Besucher die Website durchsuchen. Jede Seitenansicht, Produktinteraktion oder Suchanfrage wird an AEP gestreamt und mit dem Besucherprofil verknüpft (über ECID für anonyme Besucher oder authentifizierte Identität für bekannte Besucher). Wenn eine Seite mit einer Recommendations-Oberfläche geladen wird, fordert der [!DNL Web SDK] von AJO über die [!DNL Edge Network] eine Entscheidungsbewertung an. Die Decisioning-Engine wertet das Verhaltensprofil des Besuchers anhand der Auswahlstrategie aus, wendet die Rangfolgelogik an, filtert nicht infrage kommende Artikel (bereits gekauft, nicht vorrätig) heraus und gibt die empfohlenen Artikel zurück.

Empfehlungen werden auf der Seite über Code-basierte Erlebnisse oder Web-Kanaloberflächen gerendert. Das Rendering kann ein Karussell, ein Raster, ein Einzelelement-Widget oder ein beliebiges benutzerdefiniertes Layout sein, das in der Empfehlungsvorlage definiert ist. Impression- und Klickereignisse werden automatisch an AEP zurückverfolgt, um Leistungsberichte zu erhalten.

**Wichtige Aspekte:**

- Edge Decisioning erfordert, dass die Zusammenführungsrichtlinie auf Edge aktiv ist
- Die Empfehlungslatenz hängt von der [!DNL Edge Network] Reaktionszeit ab (unter 500 ms SLA für Anfragen mit einem Umfang)
- Anonyme Besucher erhalten Empfehlungen, die auf dem Verhalten während der Sitzung basieren. Bekannte Besucher profitieren von einem sitzungsübergreifenden Verhaltensverlauf
- Kaltstart-Besuchende ohne Verhaltensverlauf erhalten Fallback-Empfehlungen

**Vorteile:**

- Echtzeit-Personalisierung basierend auf dem Verhalten während der Sitzung
- Versand von Empfehlungen in der zweiten Sekunde über [!DNL Edge Network]
- Funktioniert sowohl für anonyme als auch für bekannte Besucher
- Automatisches Impression- und Klick-Tracking
- Für neue Empfehlungen ist kein Neuladen der Seite erforderlich

**Einschränkungen:**

- Der Edge-Profilspeicher enthält eine Teilmenge vollständiger Profilattribute
- Komplexe Ranking-Modelle mit vielen Profilattributen erfordern möglicherweise eine Hub-seitige Auswertung
- Erfordert [!DNL Web SDK] Bereitstellung mit verhaltensbasierter Ereignisverfolgung

**Experience League:**

- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### Option B: Empfehlungen für Mobile Apps

**Am besten geeignet für** In-App-Produktempfehlungen, personalisierte Inhalts-Feeds, benachrichtigungsgesteuerte Empfehlungen und mobile Commerce-Erlebnisse.

**Funktionsweise:**

Verhaltenssignale werden über die [!DNL Mobile SDK] erfasst, während Benutzende mit der App interagieren. Produktansichten, Inhaltsinteraktionen, Suchen und Käufe werden an AEP gestreamt. Wenn ein Bildschirm mit einer Recommendations-Oberfläche geladen wird, fordert der [!DNL Mobile SDK] eine Entscheidungsbewertung an. Empfehlungen werden über In-App-Nachrichten, Inhaltskarten oder Code-basierte Erlebnisse in der Mobile App bereitgestellt.

Inhaltskarten eignen sich besonders gut für Anwendungsfälle für Empfehlungen in mobilen Apps, da sie ein Feed-ähnliches Erlebnis bieten, das Benutzende nach Belieben durchsuchen können. In-App-Nachrichten können für kontextuelle Empfehlungen verwendet werden, die durch bestimmte Verhaltensweisen ausgelöst werden (z. B. die Anzeige komplementärer Produkte nach dem Hinzufügen eines Artikels zum Warenkorb).

**Wichtige Aspekte:**

- [!DNL Mobile SDK] muss für relevante Interaktionen mit verhaltensbezogener Ereignisverfolgung konfiguriert werden
- Inhaltskarten bieten eine persistente Empfehlungsoberfläche. In-App-Nachrichten sind flüchtig
- Das Offline-Verhalten-Tracking erfordert für die zeitversetzte Ereignisübermittlung die Verwaltung der SDK-Warteschlange
- App-Store-Aktualisierungszyklen beeinflussen, wie schnell Recommendations-Rendering-Änderungen bereitgestellt werden können

**Vorteile:**

- Natives mobiles Erlebnis mit reibungslosem, in Mobile Apps integriertem Empfehlungsrendering
- Inhaltskarten bieten einen beständigen, durchsuchbaren Empfehlungs-Feed
- In-App-Nachrichten ermöglichen kontextbezogene, verhaltensgesteuerte Empfehlungen
- Nutzt Signale auf Geräteebene (Standort, App-Nutzungsmuster) für erhöhte Relevanz

**Einschränkungen:**

- [!DNL Mobile SDK] Integration und App-Entwicklungsressourcen erforderlich
- Für Rendering-Änderungen sind App-Aktualisierungen erforderlich (sofern keine Code-basierten Erlebnisse mit servergesteuerten Layouts verwendet werden)
- Offline-Perioden verursachen Lücken in der Erfassung von Verhaltenssignalen

**Experience League:**

- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Option C: E-Mail-Verhaltensempfehlungen

**Am besten geeignet für:** Produktempfehlungen in E-Mail-Kampagnen - E-Mails zum Durchsuchen von E-Mails mit angezeigten Produktempfehlungen, Crosssell-E-Mails nach dem Kauf, periodischen „Auswahlen für Sie“-Auszügen und E-Mails zur erneuten Interaktion mit personalisierten Produktvorschlägen.

**Funktionsweise:**

Verhaltensprofildaten, die aus früheren Sitzungen gesammelt wurden, fließen in die Auswahl der Empfehlungen zum Zeitpunkt des E-Mail-Versands oder des Renderings ein. Eine Audience wird definiert, um die entsprechenden Empfängerinnen und Empfänger anzusprechen (z. B. Besucherinnen und Besucher, die einen Browser geöffnet haben, aber keinen Kauf getätigt haben, oder Kundinnen und Kunden, die kürzlich einen Kauf getätigt haben). Eine Kampagne oder Journey ist so konfiguriert, dass sie eine E-Mail sendet, die Platzierungen für Empfehlungen enthält. Zum Zeitpunkt des Versands bewertet AJO Decisioning das Verhaltensprofil jedes Empfängers anhand der Auswahlstrategie und fügt die empfohlenen Elemente in den E-Mail-Inhalt ein.

Diese Option beruht auf dem kumulierten Verhaltensverlauf und nicht auf In-Session-Signalen. Berechnete Attribute (Kategorieaffinitätswerte, kürzliche Produktansichten, Kaufhäufigkeit) verbessern die Empfehlungsqualität für E-Mails erheblich, da sie den Verhaltensverlauf in Signale auf Profilebene unterteilen, die von der Auswahlstrategie effizient ausgewertet werden können.

**Wichtige Aspekte:**

- E-Mail-Empfehlungen werden zum Zeitpunkt des Versands ausgewertet, nicht zum Zeitpunkt der Öffnung - der Verhaltensprofilstatus zum Zeitpunkt des Versands bestimmt die Empfehlungen
- Berechnete Attribute werden dringend empfohlen, um die Rangfolgequalität zu verbessern
- Einschränkungen beim E-Mail-Rendering (kein JavaScript, eingeschränktes CSS) schränken die Anzeigeformate der Empfehlungen ein
- Erfordert eine konfigurierte und validierte E-Mail-Kanaloberfläche

**Vorteile:**

- Nutzt den vollständigen Verhaltensverlauf in allen Sitzungen für eine tiefere Personalisierung
- Integration mit bestehenden Kampagnen- und Journey-Workflows
- Effektiv für Rückgewinnungs- und Win-back-Szenarien, in denen Web-/App-Touchpoints nicht verfügbar sind
- Kann mehrere Recommendations-Platzierungen in einer E-Mail enthalten

**Einschränkungen:**

- Empfehlungen sind zum Zeitpunkt des Versands statisch und werden beim Öffnen der E-Mail nicht aktualisiert
- Einschränkungen beim E-Mail-Rendering begrenzen die Anzeigeformate von Recommendations
- Zielgruppenevaluierung und Infrastruktur für Kampagnen-/Journey-Orchestrierung erforderlich
- Höhere Implementierungskomplexität aufgrund zusätzlicher Abhängigkeiten (Kanalkonfiguration, Zielgruppendefinition, Kampagnenausführung)

**Experience League:**

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Vergleich von Optionen

In der folgenden Tabelle sind die wichtigsten Unterschiede zwischen den Implementierungsoptionen zusammengefasst.

| Kriterien | Option A: Web in Echtzeit | Option B: Mobile App | Option C: E-Mail-Verhalten |
| --- | --- | --- | --- |
| Am besten geeignet für | Empfehlungen für Web-Seiten (PDP, Homepage, Kategorie) | In-App-Empfehlungen und Inhalts-Feeds | Email-Kampagnen mit Produktempfehlungen |
| Verhaltenssignalquelle | In-session + Cross-session ([!DNL Web SDK]) | In-App-Interaktionen [!DNL Mobile SDK] | Angesammelter Verhaltensverlauf (Profil) |
| Empfehlungslatenz | Subsekunde ([!DNL Edge Network]) | Subsekunde ([!DNL Edge Network]) | Zur Sendezeit (Hub-seitige Auswertung) |
| Besuchertyp | Anonym und bekannt | Bekannte (App-Benutzer) | Bekannte (E-Mail-Empfänger) |
| Komplexität | Mittel | Medium-Hoch | Hoch |
| Kanalabhängigkeit | [!DNL Web SDK], Code-basierte Erlebnisoberfläche | [!DNL Mobile SDK], In-App-/Inhaltskarten-Oberfläche | E-Mail-Kanaloberfläche, Zielgruppe, Kampagne/Journey |
| Erfordert | [!DNL Web SDK]-Bereitstellung, Edge-Zusammenführungsrichtlinie | [!DNL Mobile SDK]-Bereitstellung, Edge-Zusammenführungsrichtlinie | E-Mail-Oberfläche, Zielgruppendefinition, Kampagneneinrichtung |

### Wählen der richtigen Option

Verwenden Sie die folgenden Anleitungen, um die beste Option für Ihre Situation auszuwählen:

- **Beginnen Sie mit Option A** wenn Ihr primäres Ziel Echtzeit-Produktempfehlungen auf Ihrer Website sind. Dies ist der häufigste Ausgangspunkt und bietet einen sofortigen Wert bei der geringsten Implementierungskomplexität.
- **Wählen Sie Option B**, wenn Ihre Mobile App ein primärer Interaktionskanal ist und In-App-Empfehlungen eine aussagekräftige Steigerung der Konversionsrate bewirken würden. Option B kann parallel zu Option A ausgeführt werden, wobei dieselben Auswahlstrategien und Artikelkataloge verwendet werden.
- **Fügen Sie Option C** hinzu, wenn Sie Verhaltensempfehlungen auf E-Mail-Kampagnen erweitern möchten. Dies wird in der Regel über Option A oder B geschichtet, wobei dieselben Elementkataloge und Auswahlstrategien verwendet werden, jedoch mit E-Mail-spezifischen Rendering-Vorlagen und zielgruppenbasiertem Targeting.
- **Kombinieren Sie die Optionen A + C** für ein gängiges Muster: Web-Empfehlungen in Echtzeit für aktive Besucher sowie E-Mail-Empfehlungen für Besuchende, die das System verlassen, ohne zu konvertieren, wenn sie das System verlassen haben oder nach dem Kauf E-Mails abbrechen.

## Implementierungsphasen

Die folgenden Phasen führen Sie durch die End-to-End-Implementierung von Verhaltensempfehlungen.

### Phase 1: Konfigurieren des Verhaltensereignisschemas und der Datenerfassung

**Anwendungsfunktion:** AEP: Datenmodellierung und -vorbereitung (F2), AEP: Datenquellen und -erfassung (F3)

In dieser Phase werden die XDM-Schemata, Datensätze und Datenerfassungsmechanismen erstellt, die Verhaltenssignale und Elementkatalogdaten erfassen. Von dieser Datengrundlage hängt die gesamte Empfehlungslogik ab.

#### Entscheidung: Design von Verhaltensereignisschemata

Welche Verhaltenssignale sollten Empfehlungen auslösen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Produktansichten | Einfache Crosssell-/Upsell-Empfehlungen | Niedrigster Implementierungsaufwand, begrenzte Signaltiefe |
| Produktansichten + Käufe | Recommendations mit Kaufausschluss und Crosssell-Logik | Geringer Aufwand; ermöglicht Filterung „bereits gekaufte ausschließen“ |
| Vollständige Verhaltens-Suite (Ansichten, Käufe, In den Warenkorb legen, Suchen, Inhaltsinteraktionen) | Anspruchsvolle Empfehlungen mit Multi-Signal-Ranking | Höchste Signalqualität; erfordert umfassende [!DNL Web SDK]/[!DNL Mobile SDK] Instrumentierung |

#### Entscheidung: Methode zur Erfassung des Artikelkatalogs

Wie wird das Produkt oder der Inhaltskatalog in AEP aufgenommen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch-Aufnahme über Quell-Connector | Katalogaktualisierungen erfolgen regelmäßig (täglich/wöchentlich) | Einfachere Einrichtung; Katalogänderungen werden nicht in Echtzeit angezeigt |
| Streaming-Aufnahme | Katalog benötigt nahezu in Echtzeit Aktualisierungen (Preisänderungen, Verfügbarkeit) | Komplexer; stellt sicher, dass die Empfehlungen den aktuellen Bestand widerspiegeln |
| Manueller/API-Upload | Kleiner Katalog mit unregelmäßigen Änderungen | Einfache Einrichtung; nicht skalierbar für große oder dynamische Kataloge |

**UI-Navigation:** Daten-Management > Schemata > Schema erstellen; Datenerfassung > Datenströme > Neuer Datenstrom

**Wichtige Konfigurationsdetails:**

- Das Erlebnisereignis-Schema muss Produkt-/Elementkennungen (SKU, Produkt-ID, Inhalts-ID) in der Ereignis-Payload enthalten
- Das Artikelkatalogschema sollte Attribute enthalten, die für Filterung und Rangfolge verwendet werden: Kategorie, Preis, Bild-URL, Verfügbarkeitsstatus, Tags
- Für den Datenstrom muss [!DNL Adobe Journey Optimizer] -Service für Edge Decisioning aktiviert sein
- [!DNL Web SDK] `sendEvent` müssen Produktinteraktionsdaten enthalten, die XDM Commerce-Feldern zugeordnet sind

**Dokumentation zu Experience League:**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Definieren einer Beziehung zwischen zwei Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Phase 2: Konfigurieren von Identität und Profil

**Anwendungsfunktion:** AEP: Identitäts- und Profilkonfiguration (F4)

In dieser Phase werden Identity-Namespaces, primäre Identitätsbezeichnungen und Zusammenführungsrichtlinien eingerichtet, die sicherstellen, dass Verhaltenssignale korrekt mit Besucherprofilen verknüpft und für die Bereitstellung von Empfehlungen in Echtzeit verfügbar sind.

#### Entscheidung: Zusammenführungsrichtlinie für Edge Decisioning

Erfordert der Anwendungsfall „Empfehlung“ eine Evaluierung in Echtzeit durch Edge?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| In Edge-Zusammenführungsrichtlinie aktiv | Optionen A und B (Web- und Mobile-Echtzeitempfehlungen) | Erforderlich für den Versand von Empfehlungen im Sekundentakt; nur eine Edge-Zusammenführungsrichtlinie pro Sandbox |
| Standardmäßige Zusammenführungsrichtlinie (nicht auf Edge) | Nur Option C (E-Mail-Empfehlungen werden zum Versandzeitpunkt ausgewertet) | Ausreichend für die Hub-seitige Auswertung; nutzt nicht den Steckplatz für die Edge-Zusammenführungsrichtlinie |

#### Entscheidung: Anonymer vs. bekannter Besucher-ID

Wie sollten Verhaltenssignale anonymer Besucher gehandhabt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur ECID (anonym) | Empfehlungen, die hauptsächlich für anonyme Besucher basierend auf dem Verhalten während der Sitzung gedacht sind | Einfachere Einrichtung; keine sitzungsübergreifende Kontinuität, es sei denn, der Besucher authentifiziert sich |
| ECID + authentifizierte Identität (CRM-ID, E-Mail) | Empfehlungen für sitzungsübergreifende Kontakte für bekannte Besucher mit Identitätszuordnung | Umfassendere Verhaltensprofile; erfordert Authentifizierungsfluss |
| Beide mit Identitätsdiagramm-Verknüpfung | Vollständiges Journey von anonym zu bekannt mit Identitätszuordnung | Am umfassendsten; erfordert die Konfiguration von Identitätsverknüpfungsregeln |

**UI-Navigation:** Identitäten > Identity-Namespaces; Profile > Zusammenführungsrichtlinien

**Wichtige Konfigurationsdetails:**

- Der ECID-Namespace ist vorkonfiguriert und wird automatisch von [!DNL Web SDK] und [!DNL Mobile SDK] verwendet
- Benutzerdefinierte Identity-Namespaces (CRM-ID, Treueprogramm-ID) müssen für eine authentifizierte Identität erstellt werden
- Die Primäre Identität im Erlebnisereignisschema sollte ECID für Web-/Mobile-Verhaltensereignisse sein.
- Zusammenführungsrichtlinie muss privates Gerätediagramm für die Identitätszuordnung zwischen Geräten verwenden

**Dokumentation zu Experience League:**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### Phase 3: Einrichten des Artikelkatalogs und der Auswahlstrategie

**Anwendungsfunktion:** AJO: Decisioning

In dieser Phase werden der Elementkatalog (Entscheidungselemente), Auswahlstrategien, die Verhaltenssignale mit Elementattributen für die Rangfolge kombinieren, Filterregeln zum Ausschließen nicht auswählbarer Elemente und Fallback-Empfehlungen für Kaltstart-Profile konfiguriert.

#### Entscheidung: Umfang des Artikelkatalogs

Welche Artikel können empfohlen werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Produktkatalog (E-Commerce) | Physische oder digitale Produkte zum Kauf empfehlen | Artikelattribute umfassen Preis, Kategorie, Verfügbarkeit, Bilder |
| Inhaltskatalog (Medien/Veröffentlichung) | Empfohlene Artikel, Videos oder informative Inhalte | Elementattribute umfassen Thema, Autor, Veröffentlichungsdatum, Inhaltstyp |
| Hybridkatalog | Sowohl Produkte als auch Inhalte empfehlen | Erfordert ein einheitliches Schema für Elemente, das beide Typen unterstützt |

#### Entscheidung: Ranking-Ansatz

Wie sollten die geeigneten Elemente eingestuft werden, um die besten Empfehlungen zu ermitteln?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Formelbasierte Rangfolge | Klare Geschäftslogik für das Ranking (z. B. Sortieren nach der Affinitätsbewertung der Kategorie multipliziert mit der Popularität des Elements) | Transparentes, überprüfbares Ranking; erfordert definierte Rangfolgenformel |
| KI-Rangfolge (automatische Optimierung) | Maschinelles Lernen sollte das optimale Ranking auf der Grundlage von Konversionsdaten bestimmen | Erfordert mindestens 1.000 Konversionsereignisse für das Modell-Training; weniger transparent |
| Prioritätsbasiert (manuell) | Einfache, manuell kuratierte Empfehlungsreihenfolge | Einfachste Konfiguration; passt sich nicht dem individuellen Verhalten an |

#### Entscheidung: Filterregeln

Welche Elemente sollten aus den Empfehlungen ausgeschlossen werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Bereits gekaufte Artikel ausschließen | Crosssell- und Discovery-Empfehlungen | Erfordert Kaufverlauf im Verhaltensprofil |
| Nicht vorrätige Artikel ausschließen | E-Commerce mit dynamischem Inventar | Erfordert Katalogaktualisierungen in Echtzeit oder nahezu in Echtzeit |
| Ausschließen von zuvor verworfenen Elementen | Inhaltsempfehlungen, bei denen Benutzer Vorschläge verwerfen können | Verwerfungs-Tracking bei Verhaltensereignissen erforderlich |
| Filterung nach Kategorien | Auf bestimmte Kategorien beschränkte Empfehlungen | Verwendet Elementattribute zum Filtern |

#### Entscheidung: Kaltstart-Strategie

Was sollte neuen Besuchern ohne Verhaltensverlauf angezeigt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Beliebte Artikel (globale Bestseller) | Allgemeiner Fallback | Einfach zu pflegen, nicht personalisiert |
| Kategoriespezifische beliebte Elemente | Besucher ist auf einer Kategorieseite angekommen | Kontextuell relevantes Fallback; erfordert Seitenkontext |
| Kuratierte redaktionelle Auswahlen | Brand wünscht sich redaktionelle Kontrolle über das Kaltstart-Erlebnis | Erfordert manuelle Kuratierung und Aktualisierungen |
| Trend-Elemente (zeitgewichtete Popularität) | Dynamischer Fallback, der aktuelle Trends widerspiegelt | Trendsignalberechnung erforderlich |

**UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Entscheidungen; [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Angebote; [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Platzierungen

**Wichtige Konfigurationsdetails:**

- Erstellen Sie Entscheidungselemente, die jedes Produkt oder jedes Inhaltselement im Katalog darstellen, mit Attributen (Kategorie, Preis, Bild-URL, Tags)
- Definieren Sie Auswahlstrategien, die die Elementkatalogfilterung mit einer Verhaltensranking-Logik kombinieren
- Konfigurieren von Rangfolgemodellen - Formelbasierte Ausdrücke können auf Profilattribute verweisen (z. B. Kategorieaffinitätswerte aus berechneten Attributen)
- Erstellen von Fallback-Angeboten/Elementen, die als Standardempfehlungen für Kaltstart-Profile dienen
- Organisieren von Elementen in Sammlungen mithilfe von Sammlungsqualifizierern (Tags) für die logische Gruppierung
- Richten Sie Filterregeln innerhalb von Auswahlstrategien ein, um Geschäftsregeln durchzusetzen (nur gekaufte, nicht vorrätige)

**Dokumentation zu Experience League:**

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Konfigurieren von Kanal und Oberfläche

**Anwendungsfunktion:** AJO: Kanalkonfiguration

In dieser Phase werden die Versandoberflächen konfiguriert, auf denen Empfehlungen gerendert werden. Die Konfiguration variiert je nach Implementierungsoption erheblich.

#### Entscheidung: Typ der Versandoberfläche

Wo werden die Empfehlungen angezeigt?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Codebasiertes Erlebnis (Web) | Empfehlungs-Widget auf Web-Seiten mit benutzerdefiniertem Rendering | Maximale Flexibilität beim Rendern; erfordert Frontend-Entwicklung |
| Web-Kanaloberfläche | Standardmäßige Web-Personalisierungsoberfläche | Verwendet AJO Web Designer; weniger flexibel als Code-basiert |
| In-App-Nachricht | Kontextuelle Empfehlungen, die durch das Verhalten der App ausgelöst werden | Vergänglich; verschwindet nach Wechselwirkung oder Abbruch |
| Inhaltskarte (Mobiltelefon) | Dauerhafter Recommendations-Feed in der Mobile App | bleibt so lange bestehen, bis der Benutzer handelt; browserfähiges Feed-Erlebnis |
| E-Mail | In E-Mail-Kampagnen eingebettete Produktempfehlungen | Statisch zur Sendezeit; abhängig von Einschränkungen beim E-Mail-Rendering |

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Web-Echtzeitempfehlungen):**
Konfigurieren einer Code-basierten Erlebnis- oder Web-Kanaloberfläche. Code-basierte Erlebnisse bieten die größte Flexibilität für das Rendern benutzerdefinierter Empfehlungen (Karussells, Raster, Elementkarten). Der Oberflächen-URI gibt an, wo auf der Seite Empfehlungen angezeigt werden.

**Für Option B (Empfehlungen für Mobile Apps):**
Konfigurieren der Oberflächen für In-App-Nachrichten oder Inhaltskarten. Inhaltskarten werden für persistente Recommendations-Feeds empfohlen. In-App-Nachrichten eignen sich gut für kontextbezogene, verhaltensgesteuerte Empfehlungen.

**Für Option C (E-Mail-Verhaltensempfehlungen):**
Konfigurieren Sie eine E-Mail-Kanaloberfläche mit Subdomain-Zuweisung, IP-Pool-Zuweisung und Absendereinstellungen. Stellen Sie sicher, dass die Zustellbarkeit der Oberfläche validiert wurde.

**UI-Navigation:** Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen

**Dokumentation zu Experience League:**

- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 5: Konfigurieren von Inhalt und Bereitstellung

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung

In dieser Phase werden die Recommendations-Rendering-Vorlagen definiert, die steuern, wie dem Besucher empfohlene Elemente angezeigt werden. Dazu gehören der Design-Entwurf des Element-Layouts, Personalisierungsausdrücke, die Elementattribute (Name, Bild, Preis, Link) abrufen, und das allgemeine Design des Empfehlungserlebnisses.

#### Entscheidung: Anzeigeformat der Empfehlung

Wie sollten empfohlene Elemente gerendert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Karussell (horizontaler Bildlauf) | Startseite oder Kategorieseite mit begrenztem vertikalem Abstand | Vertrautes UX-Muster; zeigt mehrere Elemente in kompaktem Raum an |
| Raster (mehrere Zeilen) | Dedizierter Empfehlungsabschnitt mit reichlich Platz | Zeigt mehr Elemente auf einmal an; funktioniert gut für Abschnitte mit „Empfohlen für Sie“ |
| Widget „Einzelnes Element“ | Kontextuelle Empfehlung an einer bestimmten Seitenposition (z. B. Seitenleiste) | Minimaler Platzbedarf, wirkungsvolle Platzierung |
| Inline-E-Mail-Block | In E-Mail-Textkörper eingebettete Empfehlungen | Abhängig von E-Mail-HTML-/CSS-Einschränkungen; normalerweise 2-4 Elemente |

#### Entscheidung: Anzahl der anzuzeigenden Empfehlungen

Wie viele Elemente sollte die Entscheidung pro Platzierung zurückgeben?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| 3-4 Elemente | Standard-Empfehlungs-Widget | Balanciert Relevanz mit visueller Dichte |
| 6-8 Elemente | Karussell mit Scroll- oder Rasterlayout | Mehr Optionen für den Besucher; erfordert ausreichende Katalogtiefe |
| 1 Element | Kontextuelle Empfehlung für ein Produkt | Höchste Relevanz, einfachste Darstellung |
| Über 10 Elemente | Feed-artige Empfehlungserfahrung | Häufig verwendete Anwendungsfälle für Inhalte (Medien, Veröffentlichung) |

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Web-Echtzeitempfehlungen):**
Entwerfen Sie das Recommendations-Rendering mithilfe von Code-basierten Erlebnisvorlagen. Verwenden Sie HTML/CSS/JavaScript, um das Karussell-, Raster- oder Widget-Layout zu erstellen. Personalization-Ausdrücke verweisen auf die Attribute der Entscheidungsantwort (Elementname, Bild-URL, Preis, Produkt-URL). Impression- und Klick-Tracking werden automatisch vom [!DNL Web SDK] verarbeitet.

**Für Option B (Empfehlungen für Mobile Apps):**
Konfigurieren Sie Inhaltskarten- oder In-App-Nachrichtenvorlagen mit der Logik der Elementanzeige. Verwenden Sie JSON-basierte Inhaltsstrukturen, die von der Mobile App nativ gerendert werden. Schließen Sie Deep-Links für jedes empfohlene Element ein.

**Für Option C (E-Mail-Verhaltensempfehlungen):**
Entwerfen von E-Mail-Inhalten mit der E-Mail-Designer. Einfügen von Recommendations-Platzierungen mithilfe von entscheidungsgestützten Inhaltsbausteinen. Konfigurieren von Personalisierungsausdrücken für Elementattribute in der E-Mail-Vorlage. Die Personalisierung der Betreffzeile kann auf die am häufigsten empfohlenen Elemente verweisen.

**Benutzeroberflächennavigation:** Content-Management > Inhaltsvorlagen; Kampagne/Journey > Inhalt bearbeiten > E-Mail-Designer

**Wichtige Konfigurationsdetails:**

- Jede Platzierung einer Empfehlung muss sich auf die in Phase 3 erstellte Entscheidung beziehen
- Personalization-Ausdrücke verwenden Handlebars-Syntax zum Rendern von Elementattributen
- Für das Web: Konfigurieren des Code-basierten Erlebnisses, um die Entscheidung aufzurufen und die Antwort zu rendern
- Für E-Mail: Entscheidung in die E-Mail-Aktion innerhalb der Kampagne oder Journey einbetten
- Vorschau von Recommendations mit Testprofilen mit bekanntem Verhaltensverlauf

**Dokumentation zu Experience League:**

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Phase 6: Einrichten der Zielgruppen-Scoping und Kampagne/Journey (nur Option C)

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung, AJO: Kampagnenausführung oder Journey Orchestration

Bei E-Mail-basierten Empfehlungen (Option C) wird in dieser Phase die Zielgruppe definiert und die Kampagne oder Journey konfiguriert, die die E-Mail mit den Empfehlungen versendet. Die Optionen A und B überspringen diese Phase, da die Empfehlungen beim Laden der Seite/des Bildschirms in Echtzeit bereitgestellt werden.

#### Entscheidung: Methode zur Zielgruppenauswertung

Wie sollte die Zielgruppe für Recommendations-E-Mails bewertet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch-Auswertung | Geplante Recommendations-E-Mail-Kampagnen (tägliche, wöchentliche Zusammenfassung) | Vorhersehbarer Versandzeitpunkt; Zielgruppe vor dem Versand ausgewertet |
| Streaming-Auswertung | Ereignisgesteuerte Empfehlungs-E-Mails (abgebrochenes Durchsuchen, nach dem Kauf) | Zielgruppen-Qualifizierung nahezu in Echtzeit; paarweise mit Journey-Orchestrierung |

#### Entscheidung: Umsetzungsmechanismus

Soll die E-Mail über eine Kampagne oder eine Journey versendet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Geplante Kampagne | Einmalige oder wiederkehrende E-Mail-Nachrichten zu Empfehlungen an eine definierte Zielgruppe | Einfachere Einrichtung; Batch-Zielgruppenbewertung und Versand |
| Journey mit Zielgruppeneintrag | Laufende Recommendations-E-Mails, die durch die Zielgruppen-Qualifizierung ausgelöst werden | Aktiviert mehrstufige Flüsse (z. B. E-Mail mit Empfehlung und anschließender Erinnerung) |
| ereignisgesteuertes Journey | Durch ein bestimmtes Ereignis ausgelöste Empfehlungs-E-Mail (Abbruch durchsuchen, Kauf) | Echtzeit-Triggerung; erfordert ereignisbasierten Journey-Eintrag |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen; Kampagnen > Kampagne erstellen; Journey > Journey erstellen

**Wichtige Konfigurationsdetails:**

- Definieren Sie die Zielgruppe mithilfe von Segmentregelausdrücken, die auf den Verhaltensverlauf verweisen (z. B. „Produkte, die in den letzten 7 Tagen angezeigt, aber nicht gekauft wurden„)
- Konfigurieren Sie die Kampagne oder die Journey mit der E-Mail-Aktion, die auf die Kanaloberfläche in Phase 4 verweist.
- Einbetten der Entscheidung aus Phase 3 in den E-Mail-Inhalt
- Legen Sie Zeitplan- und Häufigkeitsregeln fest, um Übernachrichten zu vermeiden

**Dokumentation zu Experience League:**

- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Phase 7: Konfigurieren von Reporting und Optimierung

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse, S5: Reporting und Analyse

In dieser Phase wird eine Leistungsüberwachung für die Metriken Clickthrough, Konversion und Umsatz von Empfehlungen eingerichtet. Sie schafft die Reporting-Infrastruktur, um die Effektivität von Empfehlungen zu messen und Optimierungsmöglichkeiten zu identifizieren.

#### Entscheidung: Berichtstiefe

Welcher Grad an Reporting- und Analysearbeit ist erforderlich?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native AJO-Berichte | Grundlegende Leistungsüberwachung von Empfehlungen | Schnelle Einrichtung; auf von AJO verfolgte Metriken beschränkt |
| Integration von AJO und [!DNL Customer Journey Analytics] | Kanalübergreifende Analyse der Auswirkungen von Recommendations und Umsatzzuordnung | Erfordert [!DNL Customer Journey Analytics] Verbindung und Datenansicht; bietet tiefere Einblicke |
| Vollständiger [!DNL Customer Journey Analytics] mit benutzerdefinierten Dashboards | Laufendes Optimierungsprogramm mit Analyse auf Element-, Segment- und Oberflächenebene | Umfassendste Lösung; erfordert [!DNL Customer Journey Analytics] Know-how und Einrichtung |

**UI-Navigation:** Kampagnen > Kampagne auswählen > Alle Zeitberichte; Journey > Journey auswählen > Alle Zeitberichte; [!DNL Customer Journey Analytics] > Projekte > Neues Projekt erstellen

**Wichtige Konfigurationsdetails:**

- Überprüfen der AJO-Kampagnen- und Journey-Berichte auf Versand- und Interaktionsmetriken
- Erstellen Sie für [!DNL Customer Journey Analytics] Integration eine Verbindung einschließlich AJO-Erlebnisereignis-Datensätzen (Nachrichten-Feedback, E-Mail-Tracking, Decisioning)
- Erstellen Sie eine [!DNL Customer Journey Analytics] Datenansicht mit empfehlungsspezifischen Dimensionen (Elementname, Elementkategorie, Empfehlungsoberfläche) und Metriken (Impressionen, Klicks, Konversionen, Umsatz)
- Erstellen von berechneten Metriken für Recommendations-CTR, Konversionsrate und Umsatz pro Impression
- Erstellen Sie [!DNL Customer Journey Analytics] Arbeitsbereich-Bedienfelder, in denen die Empfehlungsleistung über Oberflächen, Segmente und Zeiträume hinweg verglichen wird

**Dokumentation zu Experience League:**

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Überlegungen bei der Implementierung

Überprüfen Sie die folgenden Leitplanken, Fallstricke, Best Practices und Kompromisse vor und während der Implementierung.

### Leitplanken und Beschränkungen

- Maximal 10.000 genehmigte personalisierte Angebote (Entscheidungselemente) pro Sandbox - [Entscheidungs-Management-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 30 Platzierungen pro Entscheidung
- Maximal 30 Sammlungsbereiche pro Entscheidungsanfrage
- SLA mit Reaktionszeit des Angebotsversands: weniger als 500 ms bei P95 für Edge-Anfragen mit einem Umfang
- KI-Rangfolgemodelle erfordern mindestens 1.000 Konversionsereignisse für das Training.
- Angebotsbegrenzungszähler können in Szenarien mit hohem Durchsatz eine Verzögerung von bis zu einigen Sekunden aufweisen
- Edge-Entscheidungen sind auf Profilattribute beschränkt, die im Edge-Profilspeicher verfügbar sind
- Pro Sandbox kann nur eine Zusammenführungsrichtlinie in Edge aktiv sein ([)](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximal 25 aktive berechnete Attribute pro Sandbox - [Leitplanken für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Streaming-Aufnahme: maximal 20.000 Datensätze pro Sekunde pro HTTP-Verbindung — [Aufnahme-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Häufige Fehler

- **Entscheidung gibt nur Fallback-Elemente zurück** Überprüfen Sie, ob personalisierte Entscheidungselemente innerhalb ihres Gültigkeitsdatumsbereichs genehmigt wurden und ob die Eignungsregeln mit den Profilattributen des Besuchers übereinstimmen. Vergewissern Sie sich, dass die Begrenzungen nicht erreicht wurden.
- **Edge-Versand gibt eine leere Personalisierung zurück:** Stellen Sie sicher, dass der Datenstrom mit aktiviertem [!DNL Adobe Journey Optimizer]-Service konfiguriert ist und dass der Entscheidungsumfang in der [!DNL Web SDK]-Anfrage korrekt formatiert ist.
- **Rangfolgenformel nicht angewendet:** Überprüfen Sie, ob die Formel syntaktisch gültig ist und auf barrierefreie Profilattribute verweist. Formelfehler werden im Hintergrund auf das prioritätsbasierte Ranking zurückgesetzt.
- **Veraltete Empfehlungen:** Wenn keine Verhaltensereignisdaten in Echtzeit fließen, basieren die Empfehlungen auf veralteten Verhaltensprofilen. Überprüfen Sie, [!DNL Web SDK] oder [!DNL Mobile SDK] aktiv Ereignisse streamt.
- **Die Fallback-Rate des Kaltstarts ist zu hoch:** Wenn ein großer Prozentsatz der Besucher Fallback-Empfehlungen erhält, sollten Sie die Kaltstart-Strategie mit kontextuellen Signalen (aktuelle Seitenkategorie, Empfehlungsquelle) anreichern, anstatt sich ausschließlich auf den Verhaltensverlauf zu verlassen.
- **Recommendations werden auf der Seite nicht gerendert** Überprüfen Sie, ob der Code-basierte Erlebnisoberflächen-URI dem Seiten-URL-Muster entspricht und ob der [!DNL Web SDK] die Entscheidungsantwort korrekt anfordert und rendert.
- **Katalogelemente fehlen in den Empfehlungen:** Stellen Sie sicher, dass alle Katalogelemente als Entscheidungselemente aufgenommen, mit den richtigen Sammlungsqualifizierern getaggt und in den entsprechenden Sammlungen enthalten sind, auf die die Auswahlstrategie verweist.

### Best Practices

- Beginnen Sie mit einem formularbasierten Rangfolgemodell unter Verwendung berechneter Attribute (Kategorieaffinität, Interaktionsaktualität), bevor Sie in KI-Rangfolgemodelle investieren. Formelbasierte Modelle sind transparent, überprüfbar und bieten eine solide Grundlage für den Vergleich.
- Implementieren Sie das Impression- und Klick-Tracking vom ersten Tag an. Ohne Interaktionsdaten können KI-Rangfolgemodelle nicht trainiert und die Effektivität von Empfehlungen nicht gemessen werden.
- Erstellen Sie separate Auswahlstrategien für verschiedene Empfehlungsoberflächen (Homepage, PDP, E-Mail), anstatt eine einzelne Strategie überall wiederzuverwenden. Verschiedene Oberflächen dienen unterschiedlichen Benutzerinteressen.
- Verwenden Sie berechnete Attribute, um den Verhaltensverlauf in Ranking-Signale zu unterteilen. Die Rohdaten der Ereignisse sind für ein effektives, formularbasiertes Ranking zu granular; aggregierte Signale wie „Kategorieaffinitätswert“ und „Tage seit dem letzten Kauf“ sind effektiver.
- Testen Sie Fallback-Empfehlungen getrennt von personalisierten Empfehlungen. Stellen Sie sicher, dass Fallback-Elemente hochwertige, markengerechte Standardwerte sind, die neuen Besuchern ein gutes Erlebnis bieten.
- Überwachen Sie die Fallback-Rate für den Kaltstart als wichtige Konsistenzmetrik. Eine abnehmende Fallback-Rate im Laufe der Zeit deutet auf eine wachsende Verhaltensabdeckung hin.
- Für E-Mail-Empfehlungen sendet der Zeitplan zu Zeiten, zu denen das Verhaltensprofil am vollständigsten ist (z. B. nach Spitzenzeiten beim Browsen, nicht während dieser Zeiten).

### Entscheidungen über Kompromisse

Die folgenden Kompromisse sollten auf der Grundlage Ihrer spezifischen Anforderungen bewertet werden.

#### Echtzeitsignale im Vergleich zum kumulierten Verlauf

Verhaltenssignale während der Sitzung geben sofortige Relevanz, sind aber begrenzt tief. Angesammelte Verhaltensdaten liefern Tiefe, können aber veraltet sein. Das Gleichgewicht zwischen diesen Quellen beeinflusst die Empfehlungsqualität.

- **Option A bevorzugt:** Echtzeit-Signale für unmittelbare Relevanz, ergänzt durch die gesammelte Historie für bekannte Besucher
- **Option C bevorzugt:** Ausschließlich kumulierter Verlauf, da E-Mails asynchron gesendet werden
- **Empfehlung:** Für Web- und Mobilgeräte (Optionen A, B) kombinieren Sie Sitzungssignale mit berechneten Attributen, die aus historischem Verhalten abgeleitet wurden. Investieren Sie für E-Mail (Option C) massiv in berechnete Attribute, die den Verhaltensverlauf in verwertbare Signale auf Profilebene zusammenfassen.

#### Formelbasierte im Vergleich zu KI-bewerteten Modellen

Das formularbasierte Ranking ist transparent und sofort. KI-bewertete Modelle passen sich automatisch an, benötigen jedoch Schulungsdaten und bieten weniger Einblick in Rangfolgeentscheidungen.

- **Formelbasierte Vorteile:** Transparenz, Prüfbarkeit, sofortige Bereitstellung und differenzierte Geschäftskontrolle über die Rangfolgelogik
- **KI-Rangfolge-Favoriten** Automatisierte Optimierung, Erkennung nicht offensichtlicher Muster und reduzierter manueller Optimierungsaufwand
- **Empfehlung:** Sie mit der formelbasierten Rangfolge, um eine Leistungsgrundlinie zu erstellen und Konversionsdaten zu akkumulieren. Wechseln Sie zu Modellen mit KI-Rangfolge, sobald Sie über ausreichende Schulungsdaten (über 1.000 Konversionsereignisse) verfügen und über das hinausgehen möchten, was eine manuelle Formeloptimierung erreichen kann.

#### Umfang der Empfehlung vs. Relevanz

Die Erweiterung des Elementkatalogs und die Lockerung der Filterregeln erhöhen den Prozentsatz der Anfragen, die personalisierte Empfehlungen erhalten, können jedoch die Relevanz pro Empfehlung verringern.

- **Hohe Abdeckung favorisiert:** Maximieren der Anzahl der Besucher, die personalisierte Empfehlungen sehen; nützlich, wenn das primäre Ziel die Interaktion ist
- **Hochrelevante Gefälligkeiten:** Nur Elemente mit hoher Relevanz werden angezeigt, auch wenn dadurch mehr Besucher Fallback-Empfehlungen erhalten. Nützlich, wenn das primäre Ziel die Konversion ist.
- **Empfehlung:** Beginnen Sie mit der moderaten Filterung (schließen Sie gekaufte und nicht vorrätige Artikel aus) und überwachen Sie sowohl Fallback-Rate als auch Konversionsrate. Verschärfen Sie die Filterregeln nur, wenn Konversionsdaten sie unterstützen.

#### Tiefe und Komplexität der Implementierung von Personalization im Vergleich

Reichhaltigere Verhaltenssignale und komplexere Rangfolgemodelle verbessern die Empfehlungsqualität, erhöhen jedoch die Komplexität der Implementierung und den Wartungsaufwand.

- **Einfachere Implementierung begünstigt:** Schnellere Wertschöpfung, geringere Wartung, einfachere Fehlersuche und Iteration
- **Vertiefende Personalisierungsvorteile:** höhere Konversionsrate, besseres Kundenerlebnis, Wettbewerbsvorteile
- **Empfehlung:** Implementierung in Phasen. Beginnen Sie mit Produktansichtssignalen und dem formularbasierten Ranking (Phase 1). Fügen Sie berechnete Attribute für die Verhaltensanreicherung hinzu (Phase 2). Bewerten Sie KI-Rangfolgemodelle, sobald die Grundlage ausgereift ist und ausreichende Trainingsdaten verfügbar sind (Phase 3).

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Muster verwendeten Technologien und Funktionen.

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
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Unterbreiten von Angeboten mithilfe der Edge Decisioning-API](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Datenerfassung und Web/Mobile SDK

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM und Datenmodellierung

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Erstellen eines Datensatzes](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Definieren einer Beziehung zwischen zwei Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Berechnete Attribute und Profilanreicherung

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Einrichten von Kanaloberflächen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Verfassen und Personalisieren von Nachrichten

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Reporting und Analysen

- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Data Governance und Lebenszyklus

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Datensatzgültigkeiten](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Überwachung und Beobachtbarkeit

- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Tutorials und Handbücher

- [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
