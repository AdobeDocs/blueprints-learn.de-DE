---
title: Web-/App-Personalization für bekannte Besucher
description: Erfahren Sie, wie Sie auf der Grundlage von Echtzeit-Profil- und Segmentzugehörigkeit personalisierte Inhalte, Angebote oder Promotions für identifizierte Besucher bereitstellen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 2%

---


# Web-/App-Personalisierung für bekannte Besucher

Dieser Referenzplan bietet eine vollständige Implementierungshilfe für die Bereitstellung personalisierter Inhalte für identifizierte Besucher auf digitalen Oberflächen mithilfe von [!DNL Adobe Journey Optimizer] (AJO) und [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die alle praktikablen Implementierungsansätze, die in jeder Phase zu treffenden Entscheidungen und die Experience League-Dokumentation zur Konfigurationsunterstützung verstehen müssen.

Die Web-/App-Personalisierung bekannter Besucher ist das primäre Personalisierungsmuster für authentifizierte digitale Erlebnisse. Im Gegensatz zur anonymen Besucherpersonalisierung, die ausschließlich auf Verhaltenssignalen in der Sitzung beruht, nutzt dieses Muster das gesamte einheitliche Profil: historische Verhaltensdaten, Segmentzugehörigkeit, Treuestufe, Kaufverlauf, Lebenszyklusstadium, berechnete Attribute und Tendenzwerte. Es unterstützt die Personalisierung auf allen Web-Seiten (über den AJO-Web-Kanal), in mobilen In-App-Nachrichten und Inhaltskarten.

Dieses Handbuch stellt alle praktikablen Implementierungsoptionen - segmentbasiert, entscheidungsbasiert und mit mehreren Oberflächen - mit Kompromissen, Entscheidungshilfen und Verweisen auf [!DNL Adobe Experience League] Dokumentation vor.

## Anwendungsfall - Übersicht

Unternehmen mit authentifizierten digitalen Eigenschaften - E-Commerce-Websites, Bankportale, Abonnement-Services, Treueprogramme, mobile Apps - müssen personalisierte Erlebnisse bereitstellen, die die Beziehung jedes Kunden zur Marke widerspiegeln. Wenn sich ein Besucher anmeldet oder durch Identitätsauflösung erkannt wird, kann die Plattform auf sein gesamtes Profil zugreifen und Inhalte bereitstellen, die auf seine spezifischen Attribute, Verhaltensweisen und Vorlieben zugeschnitten sind.

Dieses Muster behandelt das Szenario, in dem ein identifizierter Besucher über eine Web-Eigenschaft ankommt oder eine Mobile App öffnet, und das System muss den optimalen Inhalt, das optimale Angebot oder die optimale Promotion ermitteln, die basierend auf Echtzeit-Profildaten und der Zielgruppenzugehörigkeit angezeigt werden soll. Die Personalisierungsentscheidung findet am Edge in Millisekunden statt und ermöglicht die Bereitstellung von Inhalten in Subsekunden ohne merkliche Latenz.

Das Muster unterstützt sowohl deterministische Personalisierung (bei der bestimmte Inhalte bestimmten Zielgruppensegmenten zugeordnet sind) als auch dynamische Entscheidungsfindung (bei der AJO Decisioning Eignungsregeln und Rangfolgestrategien bewertet, um den optimalen Inhalt pro Profil auszuwählen). Es umfasst mehrere digitale Oberflächen - Web-Seiten, mobile In-App-Nachrichten und Inhaltskarten - und ermöglicht so eine konsistente Personalisierung auf allen digitalen Journey-Seiten des Kunden.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden mit diesem Anwendungsfallmuster erreicht.

### Bereitstellen personalisierter Kundenerlebnisse

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an. Weitere Informationen finden Sie unter [Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

| KPI | Beschreibung |
| --- | --- |
| Interaktion | Häufigkeit und Tiefe der Interaktion mit personalisierten Inhalten auf digitalen Oberflächen |
| Konversionsraten | Prozentsatz der Besucherinnen und Besucher, die die gewünschten Aktionen nach Erhalt personalisierter Inhalte abgeschlossen haben |
| Kundenzufriedenheit (CSAT) | Verbesserung der allgemeinen Zufriedenheit durch relevante, personalisierte digitale Erlebnisse |

### Website-Interaktion steigern

Verbesserung der Besuchszeit auf der Site, der Seiten pro Sitzung und der Interaktion mit Web-Inhalten durch relevante Erlebnisse. Weitere Informationen finden Sie unter [Website-Interaktion &#x200B;](../../business-objectives/acquisition-growth/increase-website-engagement.md).

| KPI | Beschreibung |
| --- | --- |
| Time On (Web)-Seite | Verkürzte Verweildauer in personalisierten Inhaltsbereichen |
| Interaktion | Interaktionsraten mit personalisierten Elementen (Klicks, Scrolls, Interaktionen) |
| Konversionsraten | Verbesserte Konvertierung von personalisierten Inhalten in Standardinhalte |

### Erhöhen der Interaktion mit Mobile Apps

Fördern Sie die tägliche aktive Nutzung, die Aktivierung von Funktionen und In-App-Konversionen durch personalisierte In-App-Erlebnisse.

| KPI | Beschreibung |
| --- | --- |
| Interaktion | In-App-Interaktionsraten mit personalisierten Nachrichten und Inhaltskarten |
| Treue | Verbesserte App-Bindung durch personalisierte Erlebnisse |
| Konversionsraten | In-App-Konversionsverbesserungen durch personalisierte Angebote und Empfehlungen |

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie häufige taktische Implementierungen dieses Musters:

- Startseiten-Personalisierung nach Treuestufe oder Lebenszyklusstufe - Zeigen Sie verschiedene Hero-Banner an, je nachdem, ob der Kunde neu, aktiv, gefährdet oder VIP ist
- Produktempfehlungskarussell basierend auf dem Kaufverlauf - zeigt relevante Produktvorschläge basierend auf früheren Kaufdaten und Produktaffinitätswerten auf
- Personalisiertes Werbebanner nach Kundensegment - zeigt verschiedene Angebote für hochwertige, risikobehaftete und neue Kundensegmente an.
- In-App-Nachricht für mobile Benutzer basierend auf der Aktivierung von Funktionen - führt Benutzer zu selten genutzten Funktionen basierend auf ihren Nutzungsmustern
- Inhaltskarte mit personalisiertem Angebot im Konto-Dashboard - beständige, ausgeschlossene Angebote, die auf das Kundenprofil zugeschnitten sind
- Personalisierte Preis- oder Rabattanzeige auf Basis der Kundenebene - Anzeige stufenspezifischer Preise oder exklusiver Rabatte für Mitglieder des Treueprogramms
- Crosssell-Empfehlungs-Widget basierend auf eigenen Produkten — schlagen ergänzende Produkte oder Services basierend auf aktuellem Portfolio vor
- Personalisierte Navigation oder Inhaltsreihenfolge auf der Grundlage von Interessen - Sortieren Sie Inhaltsmodule oder Navigationselemente basierend auf demonstrierten Voreinstellungen neu

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität dieses Anwendungsfallmusters gemessen werden.

| KPI | Messansatz | Benchmark-Leitlinien |
| --- | --- | --- |
| Interaktionsrate für Personalization | Klicks und Interaktionen mit personalisierten Inhaltselementen, unterteilt durch Impressionen | Personalisierte Inhalte sollten die Standardinhalte um 20-50 % übertreffen |
| Steigerung der Konversionsrate | Konversionsrate personalisierter Erlebnisse im Vergleich zu Kontroll-/Standarderlebnissen | 10-30 % Steigerung gegenüber nicht personalisierten Erlebnissen |
| Clickthrough-Rate (CTR) | Klicks auf personalisierte CTAs, Angebote und Recommendations dividiert durch Impressionen | Monitor pro Oberfläche (Web, In-App, Inhaltskarte) und pro Segment |
| Umsatz pro Besuch | Einnahmen, die Sitzungen mit personalisierten Erlebnissen zugeordnet werden | Vergleich der Kohorten personalisierter und nicht personalisierter Besucher |
| Interaktionsrate der Inhaltskarte | Klicks auf und Abweisungen von Inhaltskarten in Bezug auf Impressions | Tracking nach Kartentyp und Zielgruppensegment |
| In-App-Nachrichteninteraktion | In-App-Nachrichteninteraktionen (CTA-Klicks, Abweisungen) in Bezug auf Impressionen | Vergleichen von Zielgruppensegmenten und Nachrichtentypen |
| Zeit auf Seite | Durchschnittliche Zeit, die auf Seiten mit personalisierten Inhalten verbracht wurde, im Vergleich zum Standard | Personalisierte Seiten sollten eine längere Verweilzeit aufweisen |
| Annahmerate | Prozentsatz der entscheidungsausgewählten Angebote, die zu einem Konversionsereignis führen | Tracking pro Angebot, pro Platzierung und pro Rangfolgestrategie |

## Anwendungsfallmuster

In diesem Abschnitt werden das Kernmuster und seine Funktionskette beschrieben.

**Web-/App-Personalisierung für bekannte Besucher**

Stellen Sie einem identifizierten Besucher auf der Grundlage von Echtzeit-Profil und Segmentzugehörigkeit personalisierte Inhalte, Angebote oder Angebote auf Web-, Mobile-In-App- und Inhaltskartenoberflächen bereit.

**Funktionskette:** Zielgruppenauswertung > Personalization Decisioning > Oberflächen-/Kanalkonfiguration > Inhaltsbereitstellung > Impression-Tracking > Berichterstellung

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Web-Kanalkonfiguration, In-App-Kanalkonfiguration, Konfiguration des Inhaltskarten-Kanals, Entscheidungsfindung (Angebotsauswahl und Rangfolge), Nachrichtenbearbeitung (Erstellung personalisierter Inhalte), Kampagnenausführung, Inhaltsexperimentierung und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Zielgruppenbewertung (Edge, Streaming und Batch), Echtzeit-Profilsuche über Edge Network, Profilanreicherung mit berechneten Attributen und Tendenzwerten
- **[!DNL Adobe Experience Platform] (AEP)** - Profilspeicher, Identity Service, Web SDK, Mobile SDK, Datenstromkonfiguration, Edge Network-Bereitstellung

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit konfigurierten Web-Kanal-, In-App-Kanal- und Entscheidungsberechtigungen. Benutzende mit den Rollen „Marketer“ und „Inhaltsautor“. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Das Profilschema muss Attribute enthalten, die für die Personalisierung und Segmentierung verwendet werden (z. B. Treuestufe, Kaufverlauf, Produktinteressen, Lebenszyklusphase). Erlebnisereignis-Schema für Web-/App-Interaktions-Tracking- und -Konversionsereignisse. Datensätze für [!DNL Real-Time Customer Profile] aktiviert. | [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Erforderlich | Web SDK wurde in Web-Eigenschaften für die Bereitstellung von Erlebnissen und das Impression-Tracking implementiert. Mobile SDK wurde in Mobile Apps für die Bereitstellung von In-App- und Inhaltskarten implementiert. Datenstrom, der mit aktiviertem AJO-Service für die Edge-Personalisierung konfiguriert wurde. Am Edge verfügbare Echtzeit-Profildaten für die Personalisierung in Subsekunden. | [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home), [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure) |
| Identitäts- und Profilkonfiguration | Erforderlich | Bekannte Identity-Namespaces (CRM-ID, E-Mail, authentifizierte Benutzer-ID) wurden konfiguriert. Identitätszusammenfügung zwischen anonymen und authentifizierten Sitzungen für einen nahtlosen Übergang von der anonymen zur Personalisierung bekannter Besucher. Edge-Zusammenführungsrichtlinie mit `isActiveOnEdge: true` konfiguriert, um das authentifizierte Profil am Edge aufzulösen. | [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Audiences, die mithilfe von Profilattributen, Verhaltensdaten und berechneten Attributen definiert wurden. Die Edge- oder Streaming-Auswertung wurde für die Echtzeit-Personalisierungsqualifizierung aktiviert. Zielgruppen, die für die segmentbasierte Personalisierung verwendet werden, müssen für die Edge-Evaluierung qualifiziert sein. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home), [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute (z. B. [!DNL Customer AI] Tendenzwerte, Lebenszeitwert, Interaktionswert, Produktaffinität, Tage seit dem letzten Kauf) verbessern die Personalisierungsqualität erheblich, indem sie umfangreichere Signale für die Zielgruppendefinition und Inhaltsauswahl bereitstellen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview), [Kunden-KI - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Empfohlen | Richtlinien zur Profil- und Ereignisdatenspeicherung stellen sicher, dass aktuelle, relevante Daten zu Personalisierungsentscheidungen führen. Durch die Durchsetzung des Einverständnisses wird sichergestellt, dass bei der Personalisierung die Benutzereinstellungen berücksichtigt werden. | [Übersicht über das erweiterte Daten-Lifecycle-Management](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home), [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für Profilattribute, die für die Personalisierung verwendet werden (insbesondere personenbezogene Daten benachbarte Attribute wie Kaufverlauf, Standort, Finanzdaten), stellen die Einhaltung von Datennutzungsrichtlinien sicher. | [Data Governance - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home), [Übersicht über Datennutzungskennzeichnungen](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview) |
| Überwachung und Beobachtbarkeit | Empfohlen | Die Leistungsüberwachung von Edge für Versand und Personalisierung hilft bei der Erkennung von Latenzproblemen, Versandfehlern oder Problemen mit der Datenfrische, die das personalisierte Erlebnis beeinträchtigen. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home), [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview) |
| Reporting und Analyse | Eingeschlossen | Personalization-Leistungsberichte sind Teil der Funktionskette in Schritt 6. [!DNL Customer Journey Analytics] Die -Analyse ermöglicht eine gründliche Untersuchung der Auswirkungen der Personalisierung auf Konversion, Interaktion und Umsatz in allen Besuchersegmenten. | [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview), [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kanalkonfiguration | Oberflächen- und Kanalkonfiguration | Konfigurieren von Kanaloberflächen für Web-, In-App- und Inhaltskarten für die Personalisierungsbereitstellung |
| Verfassen von Nachrichten | Inhaltserstellung | Erstellen Sie für jede Oberfläche personalisierte Inhaltsvarianten mit dynamischen Inhalten, Personalisierungsausdrücken und bedingten Bausteinen |
| Kampagnenausführung | Einrichten und Aktivieren von Kampagnen | Erstellen und aktivieren Sie Web-Kampagnen (geplant oder API-ausgelöst), die Audiences, Oberflächen und Inhalte verbinden |
| Entscheidungsfindung | Decisioning-Setup (Option B/C) | Konfigurieren von Entscheidungsrichtlinien mit Eignungsregeln, Rangfolgestrategien und Angebots-/Inhaltselementen für die dynamische Personalisierung |
| Inhaltsexperiment | Optimierung (optional) | Führen Sie A/B-Tests mit personalisierten Inhaltsvarianten durch, um die Leistung zu optimieren |
| Häufigkeits- und Geschäftsregeln | Einrichten und Aktivieren von Kampagnen | Setzen Sie Impression-Frequenzlimits durch, um eine Überpersonalisierungsermüdung zu verhindern |
| Reporting und Leistungsanalyse | Reporting und Optimierung | Überwachen von Personalisierungsbereitstellungs-, Interaktions- und Konversionsmetriken pro Oberfläche und Segment |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Zielgruppendefinition und -auswertung | Definieren und Auswerten von Zielgruppen mithilfe von Profilattributen, Verhaltensdaten und berechneten Attributen mit Edge- oder Streaming-Auswertung |
| Echtzeit-Profilsuche | Inhaltsbereitstellung (Laufzeit) | Zugriff auf Echtzeit-Profilattribute und Segmentzugehörigkeiten über Edge Network für Personalisierungsentscheidungen im Anschluss an eine Sekunde |
| Profilanreicherung | Vor der Implementierung (unterstützend) | Profile mit berechneten Attributen, [!DNL Customer AI] und aggregierten Verhaltenssignalen anreichern, die die Personalisierungsqualität verbessern |

## Voraussetzungen

Bevor Sie dieses Anwendungsfallmuster implementieren, stellen Sie sicher, dass Folgendes vorhanden ist:

- [ ] Web SDK in Ziel-Web-Eigenschaften implementiert, wobei `alloy("sendEvent")` für Seitenansichten und Interaktions-Tracking konfiguriert sind
- [ ] Mobile SDK auf Ziel-Mobile-Apps implementiert (wenn In-App- oder Inhaltskartenoberflächen verwendet werden)
- [ ] Datenstrom, der mit aktiviertem [!DNL Adobe Journey Optimizer]-Service konfiguriert wurde
- [ ] Profilschema enthält Attribute, die für die Personalisierung verwendet werden (Treuestufe, Kaufverlauf, Produktinteressen, Lebenszyklusphase)
- [ ] Erlebnisereignis-Schema, das für das Impression- und Konversionstracking konfiguriert ist
- [ ] Es wurden bekannte Identity-Namespaces erstellt und die Identitätszuordnung zwischen anonymen (ECID) und authentifizierten Identitäten ist funktionsfähig
- [ ] Edge-Zusammenführungsrichtlinie mit `isActiveOnEdge: true` konfiguriert
- [ ] Zielgruppen, die mit Edge-fähiger Auswertung für die Echtzeit-Personalisierung definiert wurden
- [ ] für jede Personalisierungsvariante vorbereitete Inhalts-Assets (Bilder, Kopien, CTAs)
- [ ] dokumentierte Personalization-Strategie: Welche Attribute steuern welche Inhalte, für welche Oberflächen

## Implementierungsoptionen

In diesem Abschnitt werden die verfügbaren Implementierungsansätze für dieses Anwendungsfallmuster beschrieben.

### Option A: Segmentbasierte Web-Personalisierung

**Optimiert für:** Deterministische Personalisierung, bei der bestimmte Inhaltsvarianten direkt Zielgruppensegmenten zugeordnet werden - auf Treuestufen zugeschnittene Hero-Banner, Lebenszyklus-Staging-Messaging, Werbeinhalte für Kundensegmente. Ideal, wenn die Zuordnung von Inhalten zu Segmenten klar definiert ist und keine dynamische Rangfolge oder Optimierung erfordert.

**Funktionsweise:**

Die segmentbasierte Personalisierung ordnet Inhaltsvarianten direkt Zielgruppensegmenten zu. Wenn das Profil eines bekannten Besuchers beim Laden der Seite anhand von Zielgruppen ausgewertet wird, die für Edge geeignet sind, bestimmt das System, zu welchen Segmenten der Besucher gehört, und zeigt die entsprechende Inhaltsvariante an. Die Auswahl basiert auf der Segmentzugehörigkeitspriorität. Wenn ein Besucher für mehrere Segmente qualifiziert ist, wird der Inhalt des Segments mit der höchsten Priorität angezeigt.

Dieser Ansatz nutzt AJO-Web-Kanal-Kampagnen (oder In-App-/Inhaltskarten-Kampagnen) mit bedingten Inhaltsregeln oder mehreren Abwandlungs-Targeting-Konfigurationen. Jedes Zielgruppensegment ist mit einem bestimmten Inhaltserlebnis verknüpft. Es ist keine Entscheidungs-Engine involviert. Die Logik der Inhaltsauswahl ist vollständig segmentgesteuert.

Inhalte werden mit der AJO-Benutzeroberfläche zum Erstellen von Nachrichten mit dynamischen Inhaltsblöcken erstellt, die unterschiedliche Inhalte basierend auf der Zielgruppenzugehörigkeit oder Profilattributen rendern. Web SDK oder Mobile SDK bietet das personalisierte Erlebnis in Echtzeit über die Edge Network.

**Wichtige Aspekte:**

- Inhaltsvarianten müssen für jedes Segment vorab erstellt werden
- Segmentdefinitionen müssen Edge-fähig für die Echtzeit-Qualifizierung sein
- Zum Hinzufügen neuer Segmente oder Inhaltsvarianten muss die Kampagnenkonfiguration aktualisiert werden
- Die Inhaltsauswahl ist deterministisch - dasselbe Segment sieht immer denselben Inhalt

**Vorteile:**

- Einfach zu implementieren und zu pflegen mit klarer Zuordnung von Inhalt zu Segment
- Einfach zu verstehen und Stakeholdern die Personalisierungslogik zu erklären
- Kein Entscheidungs-Overhead - schnellere Inhaltsauflösung
- Vollständige Kontrolle darüber, welche Inhalte jedes Segment erhält

**Einschränkungen:**

- Eingeschränkte Flexibilität bei steigender Anzahl von Segmenten und Inhaltsvarianten
- Inhaltsauswahl kann nicht basierend auf Signalen auf Profilebene über die Segmentzugehörigkeit hinaus dynamisch optimiert werden
- Das Hinzufügen neuer Inhaltsvarianten erfordert manuelle Kampagnenaktualisierungen
- Unterstützt keine Szenarien mit dem nächstbesten Angebot, in denen mehrere Angebote um dieselbe Platzierung konkurrieren

**Experience League:**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/create-web)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Option B: Entscheidungsbasierte Personalisierung

**Am besten geeignet für:** Dynamische Personalisierung, bei der der optimale Inhalt oder das optimale Angebot anhand von Eignungsregeln und Ranking-Strategien pro Profil ausgewählt werden muss - nächstbestes Angebot auf der Homepage, personalisierte Produktempfehlungen, dynamische Auswahl von Werbebannern. Ideal, wenn mehrere Angebote oder Inhaltselemente um dieselbe Platzierung konkurrieren und das System das beste auswählen muss.

**Funktionsweise:**

Die entscheidungsbasierte Personalisierung nutzt AJO Decisioning, um das Besucherprofil anhand eines Katalogs mit Inhaltselementen oder Angeboten zu bewerten, Eignungsregeln anzuwenden, um zu bestimmen, welche Elemente qualifiziert sind, und dann eine Rangfolgestrategie (prioritätsbasiert, formularbasiert oder KI-Rangfolge) anzuwenden, um das optimale Element für jede Platzierung auszuwählen.

Die Implementierung umfasst die Erstellung von Platzierungen (wo der Inhalt angezeigt wird), die Definition von Angeboten mit Eignungsregeln und Inhaltsdarstellungen, die Organisation von Angeboten in Sammlungen und die Erstellung von Entscheidungsrichtlinien, die Platzierungen mit Ranking-Strategien an Sammlungen binden. Wenn ein Besucher zur Laufzeit eine Seite lädt, bewertet die Edge Network die Entscheidungsrichtlinie anhand des Besucherprofils und gibt den ausgewählten Angebotsinhalt zurück.

Dieser Ansatz unterstützt ausgefeilte Personalisierungsszenarien, einschließlich des nächstbesten Angebots, personalisierter Promotions mit Begrenzungen und KI-optimierter Inhaltsauswahl. Angebote können pro Profil und global Begrenzungen, Gültigkeitsdatumsbereiche und komplexe Eignungskriterien aufweisen, die Profilattribute und Zielgruppenmitgliedschaften kombinieren.

**Wichtige Aspekte:**

- Erfordert eine schnellere Konfiguration (Platzierungen, Angebote, Eignungsregeln, Sammlungen, Entscheidungen)
- Rangfolgestrategien können prioritätsbasiert (manuell), formelbasiert (benutzerdefinierter Ausdruck) oder KI-Rangfolgen (automatische Optimierung) sein
- Für das KI-Ranking sind mindestens 1.000 Konversionsereignisse für das Modelltraining erforderlich
- Angebotsbegrenzungszähler können bei Szenarien mit hohem Durchsatz eine leichte Verzögerung aufweisen
- Ein Fallback-Angebot muss für den Fall konfiguriert werden, dass kein personalisiertes Angebot geeignet ist

**Vorteile:**

- Dynamische Inhaltsauswahl pro Profil ohne hartcodierte Zuordnung von Segment zu Inhalt
- Unterstützt komplexe Eignungskriterien und Ranking-Logik
- Die KI-Ranking-Option ermöglicht eine automatische Optimierung ohne manuelles Eingreifen
- Angebotsbegrenzungen verhindern eine übermäßige Offenlegung bestimmter Inhalte
- Zentralisiertes Angebotsmanagement - Angebote können kanalübergreifend wiederverwendet werden

**Einschränkungen:**

- Höhere Implementierungskomplexität als segmentbasierte Personalisierung
- Für das KI-Ranking ist ein ausreichendes Konversionsereignisvolumen für das Training erforderlich
- Die Entscheidungsauswertung führt zu einer marginalen Latenz im Vergleich zur direkten segmentbasierten Inhaltsbereitstellung
- Das formularbasierte Ranking erfordert ein sorgfältiges Design, um eine unbeabsichtigte Priorisierung zu vermeiden

**Experience League:**

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Option C: Personalisierung mit mehreren Oberflächen (Web + In-App + Inhaltskarte)

**Best for:** Konsistente Personalisierung über mehrere digitale Oberflächen hinweg - Bereitstellung koordinierter personalisierter Erlebnisse auf Web-Seiten, mobilen In-App-Nachrichten und Inhaltskarten. Ideal, wenn das Unternehmen sowohl über Web- als auch über Mobile-App-Eigenschaften verfügt und eine einheitliche Personalisierungslogik für alle digitalen Touchpoints benötigt.

**Funktionsweise:**

Die Personalisierung mehrerer Oberflächen erweitert entweder Option A (segmentbasiert) oder Option B (entscheidungsbasiert), um personalisierte Inhalte über mehrere AJO-Oberflächentypen hinweg bereitzustellen. Jeder Oberflächentyp - Web, In-App, Inhaltskarte - kann unterschiedliche Inhaltsformate und Bereitstellungsmechanismen haben, aber die zugrunde liegende Personalisierungslogik (Zielgruppenzugehörigkeit oder Entscheidung) wird gemeinsam genutzt.

Die Implementierung umfasst die Konfiguration von Kanaloberflächen für jeden Oberflächentyp, die Erstellung oberflächenspezifischer Inhalte (Web-HTML/CSS für Web-Oberflächen, strukturierte Nachrichten für In-App-Nachrichten, Kartenlayouts für Inhaltskarten) und die Erstellung von Kampagnen, die auf die jeweilige Oberfläche abzielen. Die Web-SDK übernimmt die Bereitstellung der Web-Oberfläche, während die Mobile SDK die Bereitstellung in der App und der Inhaltskarte übernimmt.

Inhaltskarten sind besonders für persistente, verwerfbare personalisierte Nachrichten auf Konto-Dashboards oder App-Startbildschirmen nützlich. In-App-Nachrichten eignen sich ideal für die kontextbezogene, sitzungsspezifische Kommunikation. Die Web-Personalisierung verarbeitet Hero-Banner, Empfehlungs-Widgets und Werbeinhalte.

**Wichtige Aspekte:**

- Jeder Oberflächentyp benötigt eine eigene Kanaloberfläche und Inhaltserstellung
- Sowohl Web SDK als auch Mobile SDK müssen implementiert und konfiguriert werden
- Inhalte müssen für jedes Oberflächenformat (verschiedene Abmessungen, Layouts, Interaktionsmuster) entworfen werden
- Freigegebene Audiences und Entscheidungslogik stellen die Konsistenz über Oberflächen hinweg sicher
- Die Tests müssen alle Oberflächentypen geräteübergreifend abdecken

**Vorteile:**

- Konsistentes Personalisierungserlebnis auf allen digitalen Touchpoints
- Freigegebene Zielgruppe und Entscheidungslogik reduzieren Duplizierung
- Inhaltskarten bieten eine beständige, nicht aufdringliche Personalisierungsoberfläche
- In-App-Nachrichten ermöglichen eine kontextbezogene, sitzungsspezifische Personalisierung auf Mobilgeräten

**Einschränkungen:**

- Höchste Implementierungskomplexität - Erfordert Konfiguration für jeden Oberflächentyp
- Erfordert sowohl die Implementierung von Web SDK als auch von Mobile SDK
- Inhalte müssen für jedes Oberflächenformat entworfen und verwaltet werden
- Der Testumfang erhöht sich mit jedem zusätzlichen Oberflächentyp

**Experience League:**

- [In-App-Kanal - Übersicht](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Inhaltskarten-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/get-started-web)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen verglichen.

| Kriterien | Option A: segmentbasiert | Option B: Entscheidungsbasiert | Option C: Multi-Surface |
| --- | --- | --- | --- |
| Am besten geeignet für | Bekannte Zuordnung von Segment zu Inhalt | Dynamische Inhaltsauswahl pro Profil | Konsistente Personalisierung über Web + Mobile hinweg |
| Komplexität | Niedrig | Medium-Hoch | Hoch (baut auf A oder B auf) |
| Latenz | Schnellste (direkte Segmentauflösung) | Etwas höher (Entscheidungsbewertung) | Hängt von der zugrunde liegenden Option (A oder B) ab |
| Flexibilität | Auf vordefinierte Segment-Inhalt-Paare beschränkt | Hoch — dynamisches Ranking und Eignung | Höchste - mehrere Oberflächen mit gemeinsamer Logik |
| Content-Management | Manuelle Zuordnung von Segmenten zu Inhalten | Zentralisierte Angebotsbibliothek mit Eignungsregeln | Oberflächenspezifische Inhalte mit freigegebener Personalisierungslogik |
| Optimierung | Manuelle A/B-Tests | Automatische Optimierung für KI-Rangfolgen verfügbar | Oberflächenoptimierung |
| Erfordert | Edge-fähige Zielgruppen, Web-SDK | Platzierungen, Angebote, Eignungsregeln, Entscheidungen | Web SDK + Mobile SDK, mehrere Oberflächenkonfigurationen |
| Unterstützte Oberflächen | Web (primär) | Web (primär) | Web + In-App + Inhaltskarte |

### Wählen der richtigen Option

Beginnen Sie mit diesen Fragen, um den richtigen Implementierungsansatz auszuwählen:

1. **Wie viele Oberflächen?** Wenn Sie sowohl im Web als auch in Mobile Apps personalisieren müssen, wählen Sie Option C aus (die entweder auf A oder B für die zugrunde liegende Logik aufbaut). Wenn nur Web, wählen Sie zwischen A und B.

2. **Wie dynamisch ist Ihre Inhaltsauswahl?** Wenn Sie über eine klar definierte Zuordnung von Segmenten zu Inhaltsvarianten verfügen (z. B. 3-5 Treuestufen, jede mit einem bestimmten Hero-Banner), wählen Sie Option A. Wenn Sie aus einem Angebotskatalog mit komplexer Eignung und Rangfolge auswählen müssen, wählen Sie Option B.

3. **Benötigen Sie eine KI-optimierte Auswahl?** Wenn Sie möchten, dass das System automatisch lernt und optimiert, welche Inhalte für jedes Profil am besten funktionieren, wählen Sie Option B mit KI-Rangfolgenentscheidung.

4. **Wie viele Inhaltsvarianten?** Wenn Sie weniger als 10 Inhaltsvarianten mit klaren Segmentzuordnungen haben, ist Option A einfacher. Wenn Sie Dutzende von Angeboten haben, die Eignungsfilterung und Rangfolge erfordern, skaliert Option B besser.

5. **Planen Sie die Erweiterung auf andere Kanäle?** Wenn Ihre Entscheidungslogik letztendlich Angebote über E-Mail, Web und andere Kanäle bereitstellen soll, bietet Option B die zentrale Entscheidungsgrundlage, die Cross-Channel Offer Decisioning erweitert.

## Implementierungsphasen

In diesem Abschnitt werden die einzelnen Phasen der Implementierung im Detail beschrieben.

### Phase 1: Audiences definieren und Auswertung konfigurieren

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung

**Was Sie konfigurieren werden:** Definieren Sie die Zielgruppen, die die Auswahl von Personalisierungsinhalten fördern. Diese Zielgruppen stellen die Besuchersegmente dar, die personalisierte Erlebnisse erhalten - Treuestufen, Lebenszyklusphasen, Verhaltenskohorten oder Produktaffinitätsgruppen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Methode zur Zielgruppenauswertung**
>
>Wie schnell muss die Zielgruppenzugehörigkeit für die Personalisierung aufgelöst werden? Dies wirkt sich direkt darauf aus, ob die Personalisierung beim Laden der Seite stattfinden kann oder eine Verzögerung erfordert.
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Edge-Auswertung | Echtzeit-Web-/App-Personalisierung, die eine Qualifizierung im Sekundenbereich erfordert | Auf einfache Profilattributprüfungen und Segmentzugehörigkeit beschränkt. Keine Zeitreihenabfragen oder komplexen Aggregationen. Erforderlich für die Personalisierung bekannter Besucher. |
>| Streaming-Auswertung | Quasi-Echtzeit-Qualifizierung, wenn Profile auf der Grundlage von Verhaltensereignissen in Zielgruppen eintreten/diese verlassen | Unterstützt Abfragen für einzelne Ereignisse und für begrenzte Zeitfenster. Zielgruppenänderungen werden innerhalb von Minuten angezeigt. Geeignet für In-App- und Inhaltskarten-Oberflächen, bei denen eine geringe Verzögerung akzeptabel ist. |
>| Batch-Auswertung | Tägliche Aktualisierungen der Zielgruppe für Segmente basierend auf komplexen Aggregationen oder historischen Mustern | Unterstützung der vollständigen Segmentregelfunktion. Nicht für die Echtzeit-Personalisierung geeignet, kann jedoch Edge-Zielgruppen mit komplexen vorberechneten Segmenten ergänzen. |

>[!NOTE]
>**Entscheidung: Personalization-Attribute**
>
>Welche Profilattribute sollten die Zielgruppendefinition und Inhaltsauswahl steuern?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Profilattribute (Treuestufe, Lebenszyklusphase) | Deterministische Personalisierung basierend auf bekannten Kundeneigenschaften | Stabile, klar definierte Attribute. Einfach zuzuordnen zu Inhaltsvarianten. Am Edge verfügbar, wenn das Profil ordnungsgemäß konfiguriert ist. |
>| Verhaltenssignale (Kaufverlauf, Suchmuster) | Personalization auf der Grundlage aktueller Verhaltensweisen und Interaktionsmuster | Erfordert berechnete Attribute oder Streaming-Segmente. Dynamischer, aber komplexer zu verwalten. |
>| Neigungswerte ([!DNL Customer AI]) | Prädiktive Personalisierung basierend auf der Wahrscheinlichkeit einer Konversion, Abwanderung oder eines Kaufs | Erfordert berechnete Attribute. Ermöglicht anspruchsvolle Personalisierung, erfordert jedoch ML-Modell-Trainingsdaten. |
>| Kombinierter Ansatz | Die meisten Produktionsimplementierungen | Verwendet Profilattribute für die primäre Segmentierung mit Verhaltenssignalen und Tendenzwerten zur Verfeinerung. |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

**Wichtige Konfigurationsdetails:**

- Audiences mit Segment Builder mit Segmentregelausdrücken definieren, die auf Profilattribute verweisen
- Sicherstellen, dass Segmentregelausdrücke für die Edge-Evaluierung qualifiziert sind (einfache Attributprüfungen, Segmentzugehörigkeit)
- Konfigurieren von Audiences, die für Edge geeignet sind, für Anwendungsfälle der Echtzeit-Personalisierung
- Erwägen von Unterdrückungs-Zielgruppen, um kürzlich konvertierte oder abgemeldete Besucher auszuschließen

**Dokumentation zu Experience League:**

- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Einrichten der Entscheidungsfindung (nur Option B und C)

**Anwendungsfunktion:** AJO: Decisioning

**Was Sie konfigurieren werden:** Richten Sie die Decisioning-Infrastruktur ein, die dynamisch den optimalen Inhalt oder das optimale Angebot für jeden Besucher auswählt. Dazu gehören Platzierungen (wo Angebote angezeigt werden), Angebote (welche Inhalte verfügbar sind), Eignungsregeln (wer qualifiziert ist), Rangfolgestrategien (wie man die besten auswählt) und Entscheidungsrichtlinien (wie alles verbunden ist).

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Rangfolgestrategie**
>
>Wie sollten geeignete Angebote eingestuft werden, um für jeden Besucher das beste Angebot auszuwählen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Prioritätsbasiert (manuell) | Einfache Anwendungsfälle mit klarer Angebotshierarchie | Jedes Angebot hat einen manuellen Prioritätswert. Das Angebot mit der höchsten Priorität gewinnt. Einfach zu verstehen und zu kontrollieren. |
>| Formelbasiert (benutzerdefinierter Ausdruck) | Bei der Rangfolge sollten Profilattribute berücksichtigt werden | Benutzerdefinierte Rangfolgeformeln verweisen auf Profildaten (z. B. Bewertung nach Treuestufe + Neuigkeit). Flexibel, erfordert aber Design und Tests von Formeln. |
>| KI-Rangfolge (automatische Optimierung) | Wenn das System die Angebotsauswahl automatisch optimieren soll | Das ML-Modell lernt, welche Angebote für welche Profile am besten geeignet sind. Es sind mindestens 1.000 Konversionsereignisse für das Training erforderlich. Optimiert für Platzierungen mit hohem Traffic. |

>[!NOTE]
>**Entscheidung: Angebotsbegrenzung**
>
>Sollte es Beschränkungen geben, wie oft ein Angebot einem Besucher oder allen Besuchern angezeigt wird?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Obergrenze pro Profil | Verhindern Sie, dass dasselbe Angebot wiederholt angezeigt wird | Begrenzt die Impressionen pro Besucher über einen bestimmten Zeitraum. Sorgt für Abwechslung beim personalisierten Erlebnis. |
>| Globale Begrenzung | Gesamtzahl der Impressions für ein Promotion- oder eingeschränktes Verfügbarkeitsangebot begrenzen | Begrenzt die Gesamtzahl der Impressionen für alle Besucher. Nützlich für Werbeaktionen in begrenzter Anzahl. |
>| Keine Begrenzung | Immergrüne Inhalte oder immer relevante Angebote | Keine Impressionsbeschränkungen. Geeignet für persistente Inhalte wie Banner der Treuestufe. |

**UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management

**Wichtige Konfigurationsdetails:**

- Erstellen Sie Platzierungen für jede Oberfläche, auf der Angebote angezeigt werden (Webbanner, In-App-Nachrichtenbereich, Karteninhalt).
- Definieren von Eignungsregeln mithilfe von Segmentregelausdrücken, die auf Profilattribute und Zielgruppenzugehörigkeit verweisen
- Personalisierte Angebote mit Inhaltsdarstellungen für jede Platzierung erstellen
- Erstellen Sie ein Fallback-Angebot, das alle Platzierungen abdeckt (angezeigt, wenn kein personalisiertes Angebot qualifiziert ist)
- Angebote mit Sammlungsqualifizierern (Tags) organisieren und in Sammlungen gruppieren
- Erstellen einer Entscheidungsrichtlinie, die Platzierungen an Sammlungen mit der ausgewählten Rangfolgestrategie bindet

**Dokumentation zu Experience League:**

- [Erstellen von Platzierungen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 3: Konfigurieren von Oberflächen und Kanälen

**Anwendungsfunktion:** AJO: Kanalkonfiguration

**Was Sie konfigurieren werden:** Konfigurieren Sie die Kanaloberflächen, die definieren, wo personalisierte Inhalte bereitgestellt werden. Jeder Oberflächentyp (Web, In-App, Inhaltskarte) erfordert eine eigene Konfiguration, die den Oberflächen-URI, das Inhaltsformat und die Bereitstellungsparameter angibt.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Zieloberflächen**
>
>Welche digitalen Oberflächen erhalten personalisierte Inhalte?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Webkanal | Personalization mit Fokus auf Web-Eigenschaften | Erfordert Web-SDK. Einfachste Implementierung. Behandelt Hero-Banner, Werbebereiche, Recommendations-Widgets. |
>| Nur In-App-Kanal | Personalization konzentriert sich auf Erlebnisse in mobilen Apps | Erfordert Mobile SDK. Behandelt kontextbezogene, sitzungsspezifische Nachrichten innerhalb der App. |
>| Nur Inhaltskarten-Kanal | Beständige, ausblendbare personalisierte Nachrichten | Erfordert Mobile SDK oder Web SDK. Karten bleiben bis zur Verwerfung bestehen. Ideal für Dashboards und Startbildschirme. |
>| Mehrere Oberflächen (Option C) | Konsistente Personalisierung im Web und auf Mobilgeräten | Erfordert sowohl Web SDK als auch Mobile SDK. Jede Oberfläche benötigt eine separate Konfiguration und einen separaten Inhalt. |

>[!NOTE]
>**Entscheidung: Ansatz für die Konfiguration der Web-Oberfläche**
>
>Wie sollte die Web-Oberfläche für die Inhaltsbereitstellung konfiguriert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Single Page Application (SPA) | Moderne Web-Apps mit Client-seitigem Routing | Verwenden Sie `renderDecisions: true` in Web-SDK-`sendEvent`. Inhalte, die automatisch von SDK gerendert werden. |
>| Mehrseitige Anwendung (MPA) | Herkömmliche Server-gerenderte Web-Seiten | Bei Seitenladevorgang über Edge Network-Antwort bereitgestellte Inhalte Möglicherweise ist eine URI-Konfiguration auf Seitenebene erforderlich. |

**UI-Navigation:** [!DNL Journey Optimizer] > Administration > Kanäle > Kanaloberflächen

**Wichtige Konfigurationsdetails:**

- Für Web-Oberflächen: Konfigurieren Sie den URI der Web-Oberfläche, der mit der/den Zielseite(n) übereinstimmt
- Für In-App-Oberflächen: Konfigurieren der Mobile-App-Oberfläche mit App-ID und Oberflächentyp
- Für Oberflächen von Inhaltskarten: Konfigurieren der Oberfläche von Inhaltskarten mit App-ID oder Web-Kontext
- Stellen Sie sicher, dass für den Datenstrom der AJO-Service für die Bereitstellung der Edge-Personalisierung aktiviert ist

**Dokumentation zu Experience League:**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/get-started-web)
- [Konfiguration des Web-Kanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [Voraussetzungen für In-App-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Konfiguration der Inhaltskarte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Phase 4: Inhalt erstellen

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung

**Was Sie konfigurieren werden** Erstellen Sie die personalisierten Inhaltsvarianten für jede Oberfläche und jedes Segment bzw. Angebot. Dazu gehören das Entwerfen des visuellen Layouts, das Hinzufügen von Personalisierungsausdrücken, die auf Profilattribute verweisen, das Konfigurieren von bedingten Inhaltsbausteinen und das Erstellen wiederverwendbarer Inhaltsfragmente.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Content-Ansatz**
>
>Wie sollten personalisierte Inhalte für diesen Anwendungsfall strukturiert sein?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Bedingte Inhaltsbausteine | Verschiedene Inhaltsabschnitte innerhalb desselben Layouts variieren je nach Zielgruppe | Einzelnes Inhalts-Asset mit bedingten Regeln. Effizient für kleinere Varianten (Überschrift, CTA-Text, Bildtausch). |
>| Separate Inhaltsvarianten pro Abwandlung | Grundsätzlich unterschiedliche Layouts oder Designs pro Zielgruppe | Mehrere vollständige Inhalts-Assets. Mehr Flexibilität, aber mehr Wartung. Erforderlich für Inhaltsexperimente. |
>| Entscheidungsgesteuerte Inhalte | Dynamisch aus einem Angebotskatalog ausgewählte Inhalte | Angebotsdarstellungen definieren den Inhalt. Das Content-Management wird in der Angebotsbibliothek zentralisiert. |

>[!NOTE]
>**Entscheidung: Personalization-Tiefe**
>
>Wie viel des Inhalts sollte personalisiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Personalisierung auf Oberflächenebene | Nur bestimmte Elemente werden personalisiert (Hero-Bild, CTA, Angebotsbanner) | Geringere Komplexität. Fokussierte Personalisierung auf wirkungsvolle Bereiche. Häufigster Ausgangspunkt. |
>| Vollständige Personalisierung der Seite | Das gesamte Seitenlayout oder die Inhaltsreihenfolge wird personalisiert | Höhere Komplexität. Erfordert umfangreiche Inhaltserstellung. Bietet ein maßgeschneidertes Erlebnis. |
>| Personalisierung auf Token-Ebene | Inline-Personalisierungs-Token (Name, Stufe, Punktestand) | Einfachste Form. Fügt Profilattributwerte in ansonsten statische Inhalte ein. |

**UI-Navigation:** [!DNL Journey Optimizer] > Kampagnen > Kampagne erstellen > Inhalt bearbeiten

**Wo die Optionen unterschiedlich sind:**

**Für Option A (segmentbasiert):**

- Erstellen Sie Inhaltsvarianten für jedes Zielgruppensegment mit dem Web-Designer oder Code-Editor
- Verwenden dynamischer Inhaltsbausteine mit Bedingungen, die auf der Zielgruppenzugehörigkeit basieren
- Konfigurieren von Personalisierungsausdrücken, die auf Profilattribute verweisen (z. B. `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}`)
- Richten Sie bedingte Regeln ein, um je nach Segmentzugehörigkeit unterschiedliche Inhalte anzuzeigen

**Für Option B (entscheidungsbasiert):**

- Erstellen Sie Inhaltsdarstellungen für jede in Phase 2 definierte Platzierung
- Für jedes Angebot sind eine oder mehrere Darstellungen (HTML, Bild, JSON) mit Platzierungen abgeglichen
- Integrieren der Entscheidungsausgabe in die Web-Seite oder das Programm durch Einbetten von Entscheidungsplatzierungen
- Der Inhalt wird zur Laufzeit dynamisch ausgewählt - die Bearbeitung konzentriert sich auf einzelne Angebotselemente

**Für Option C (mehrere Oberflächen):**

- Erstellen von oberflächenspezifischen Inhalten für jede Zieloberfläche (Web-HTML/CSS, strukturierte In-App-Nachricht, Inhaltskarten-Layout)
- Beibehaltung einer konsistenten Personalisierungslogik für alle Oberflächen bei gleichzeitiger Anpassung an die Formateinschränkungen jeder Oberfläche
- Testen des Renderings von Inhalten für jeden Oberflächentyp

**Dokumentation zu Experience League:**

- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/create-web)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Erstellen von In-App-Nachrichten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Erstellen von Inhaltskarten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Phase 5: Einrichten und Aktivieren von Kampagnen

**Anwendungsfunktion:** AJO: Kampagnenausführung

**Konfiguration:** Erstellen und aktivieren Sie die AJO-Kampagne, die Zielgruppe, Oberfläche und Inhalt für die Bereitstellung zusammenhält. Bei der Web-Personalisierung werden Kampagnen in der Regel für die sofortige oder laufende Aktivierung und nicht für einmalige geplante Sendungen konfiguriert.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Kampagnentyp**
>
>Wie sollte die Personalisierungskampagne ausgelöst werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Geplante Kampagne (immer aktiv) | Fortlaufende Personalisierung, die für alle qualifizierten Besucher kontinuierlich ausgeführt wird | Legen Sie das Startdatum auf Sofort und kein Enddatum fest. Kampagne bleibt aktiv, bis sie manuell gestoppt wird. Am häufigsten für die Web-Personalisierung. |
>| Geplante Kampagne (zeitlich begrenzt) | Personalization ist an einen bestimmten Promotion-Zeitraum gebunden | Legen Sie das Start- und Enddatum fest. Die Kampagne endet automatisch nach dem Enddatum. Geeignet für saisonale Aktionen oder zeitlich begrenzte Angebote. |
>| API-ausgelöste Kampagne | Durch ein bestimmtes Anwendungsereignis ausgelöste Personalization | Wird programmgesteuert ausgelöst. Dies ist nützlich, wenn die Personalisierung nur als Reaktion auf bestimmte Systemereignisse angezeigt werden soll. |

>[!NOTE]
>**Entscheidung: Frequenzlimitierung**
>
>Sollte die Häufigkeit der Impressionen für diese Personalisierung begrenzt sein?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Häufigkeitsregeln anwenden | Werbe- oder angebotsbasierte Personalisierung, die Besucher übermüden könnte | Verhindert, dass dieselbe Personalisierung zu oft angezeigt wird. Über AJO-Geschäftsregeln konfiguriert. |
>| Keine Frequenzbegrenzung | Permanente Inhaltspersonalisierung (Banner der Treuestufe, Dashboard-Inhalte) | Immer relevante Inhalte, die keine Ermüdung verursachen. Keine Impressionsbeschränkungen erforderlich. |

**UI-Navigation:** [!DNL Journey Optimizer] > Kampagnen > Kampagne erstellen

**Wichtige Konfigurationsdetails:**

- Wählen Sie den Kanal Web, In-App oder Inhaltskarte und die in Phase 3 konfigurierte Oberfläche aus
- Binden der in Phase 1 definierten Zielgruppe
- Verknüpfen der in Phase 4 erstellten Inhalte
- Konfigurieren des Kampagnenzeitplans (sofort, im Datumsbereich oder API-gesteuert)
- Kampagne überprüfen und aktivieren
- Für das Inhaltsexperiment: Aktivieren Sie den Umschalter Experiment , definieren Sie Abwandlungen, legen Sie die Traffic-Zuordnung und Erfolgsmetriken vor der Aktivierung fest

**Dokumentation zu Experience League:**

- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Phase 6: Verfolgen von Impressionen und Erfassen von Daten

**Anwendungsfunktion:** AEP: Datenquellen und Erfassung

**Was Sie konfigurieren werden** Stellen Sie sicher, dass Impressionen, Interaktionen und Konversionen von personalisierten Erlebnissen zum Reporting, zur Neubewertung der Zielgruppe und zur Entscheidungsoptimierung zurück auf die Plattform verfolgt werden.

**Wichtige Konfigurationsdetails:**

- Überprüfen, ob Web SDK beim Rendern personalisierter Inhalte `decisioning.propositionDisplay` sendet
- Überprüfen Sie, ob Web SDK `decisioning.propositionInteract` sendet, wenn Besucher mit personalisierten Inhalten interagieren (Klicks, Abweisungen)
- Für Mobile SDK: Überprüfen, ob In-App-Nachrichten- und Inhaltskarten-Interaktionsereignisse erfasst werden
- Konfigurieren der Konversionsereignis-Nachverfolgung für nachgelagerte Erfolgsmetriken (Käufe, Anmeldungen, Funktionsübernahme)
- Stellen Sie sicher, dass die Ereignisse die Vorschlagskennung für die Attribution zu bestimmten Personalisierungsentscheidungen enthalten

**Dokumentation zu Experience League:**

- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Tracking von Ereignissen mit Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Phase 7: Berichterstellung und Optimierung

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse, Reporting und Analyse

**Was Sie konfigurieren werden:** Richten Sie Leistungsüberwachung und -analyse ein, um die Effektivität der Personalisierung über Oberflächen, Segmente und Inhaltsvarianten hinweg zu messen. Verwenden Sie native AJO-Berichte für operative Metriken und [!DNL Customer Journey Analytics] für eine kanalübergreifende Analyse der geschäftlichen Auswirkungen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Berichtsumfang**
>
>Welcher Analysegrad ist für diesen Personalisierungs-Anwendungsfall erforderlich?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur native AJO-Berichte | Operative Überwachung der Versand- und Interaktionsmetriken | Integrierte Kampagnenberichte mit Impressions-, Klick- und Konversionsdaten. Schnellste Einrichtung. |
>| Kanalübergreifende Analyse von CJA | Detaillierte Analyse der Auswirkungen der Personalisierung auf Geschäftsergebnisse | Erfordert CJA-Verbindung und Datenansicht. Ermöglicht kanalübergreifende funnel-Analyse, Kohortenvergleiche und Attributionsmodellierung. |
>| AJO und CJA | Vollständige operative und analytische Sichtbarkeit | Verwenden Sie AJO für die tägliche Überwachung und CJA für strategische Analysen. Empfohlen für Produktions-Implementierungen. |

**Navigation in der Benutzeroberfläche:**

- AJO-Berichte: Kampagnen > Kampagne auswählen > Bericht anzeigen
- CJA: Projekte > Neues Projekt erstellen

**Wichtige Konfigurationsdetails:**

- Zugreifen auf Live-Berichte von Kampagnen während des aktiven Personalisierungsversands
- Überprüfen historischer Berichte für abgeschlossene Kampagnen oder periodische Analysen
- Für CJA: Konfigurieren einer Verbindung einschließlich AJO-Erlebnisereignis-Datensätzen und Erstellen einer Datenansicht mit Personalisierungsmetriken
- Erstellen von Dashboards zur Verfolgung der Interaktionsrate bei der Personalisierung, Steigerung der Konversionsrate, Annahme des Angebots und Umsatz pro Besuch
- Für die entscheidungsbasierte Personalisierung (Option B): Überwachen der Angebotsleistung nach Platzierung und Effektivität der Rangfolgestrategie

**Dokumentation zu Experience League:**

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/home)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Überlegungen bei der Implementierung

In diesem Abschnitt werden Leitplanken, häufige Fallstricke, Best Practices und Entscheidungen zu Kompromissen behandelt, die für dieses Anwendungsfallmuster relevant sind.

### Leitplanken und Beschränkungen

- Edge Network-Suchen haben eine SLA-Reaktionszeit von weniger als 200 ms für Edge-bewertete Segmente - [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Segmentierungsleitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- Edge-Segmente sind auf einfache Attributprüfungen und Segmentzugehörigkeitsabfragen beschränkt — keine Zeitreihenabfragen — [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- Pro Sandbox kann nur eine Zusammenführungsrichtlinie in Edge aktiv sein - [Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)
- Maximal 10.000 genehmigte personalisierte Angebote pro Sandbox - [Leitplanken im Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 30 Platzierungen pro Entscheidung - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)
- KI-Rangfolgemodelle erfordern mindestens 1.000 Konversionsereignisse für das Training.
- SLA hat eine Reaktionszeit von weniger als 500 ms bei P95 für Anfragen mit einem Umfang
- Maximal 500 aktive Live-Kampagnen pro Sandbox - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 25 aktive berechnete Attribute pro Sandbox - [Leitplanken für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)

### Häufige Fehler

- **Edge-Zusammenführungsrichtlinie nicht konfiguriert:** Ohne eine Edge-aktive Zusammenführungsrichtlinie kann die Edge Network das authentifizierte Profil nicht auflösen, was dazu führt, dass die Personalisierung fehlschlägt oder auf anonymes Verhalten zurückgreift. Stellen Sie sicher, dass in der Sandbox genau eine Zusammenführungsrichtlinie `isActiveOnEdge: true` ist.
- **Zielgruppe nicht Edge-fähig:** Wenn die Regelausdrücke für Zielgruppensegmente Zeitreihenabfragen, komplexe Aggregationen oder `inSegment()` auf Segmente verwenden, die nur Batch sind, sind sie nicht für die Edge-Evaluierung geeignet und können die Echtzeit-Personalisierung nicht unterstützen. Edge-Eignung während der Zielgruppendefinition überprüfen.
- **Identitäts-Stitching-Lücke während der Authentifizierung:** Wenn ein Besucher von anonym zu authentifiziert wechselt, kann es einen kurzen Moment geben, in dem das Profil noch nicht aufgelöst wurde. Stellen Sie sicher, dass die Identitätszuordnung ordnungsgemäß konfiguriert ist und dass die Web-SDK die authentifizierte Identität über `identityMap` sofort nach der Anmeldung sendet.
- **Fehlendes Fallback-Angebot in Decisioning:** kein Fallback-Angebot konfiguriert wurde und sich kein personalisiertes Angebot für einen Besucher qualifiziert, gibt die Entscheidung leere Inhalte zurück und erzeugt ein fehlerhaftes Erlebnis. Konfigurieren Sie immer ein Fallback-Angebot, das alle Platzierungen abdeckt.
- **Web SDK sendet keine Anzeigeereignisse für Vorschläge:** Wenn `renderDecisions` auf `true` gesetzt ist, aber Anzeigeereignisse nicht gesendet werden, spiegelt das Reporting die tatsächlichen Impressionen nicht wider. Überprüfen Sie die Ereignisverfolgung, indem Sie Netzwerkanfragen in den Entwickler-Tools des Browsers prüfen.
- **Inhaltsflackern beim Laden der Seite:** Wenn personalisierte Inhalte während des Entscheidungsaufrufs nicht vorab ausgeblendet werden, können Besuchende den Standardinhalt kurz sehen, bevor er ersetzt wird. Verwenden Sie das pre-hiding-Snippet oder das CSS-basierte pre-hiding, um Flackern zu vermeiden.

### Best Practices

- Beginnen Sie mit der segmentbasierten Personalisierung (Option A) für die erste Implementierung und entwickeln Sie sich dann zu entscheidungsbasiert (Option B), wenn der Angebotskatalog wächst und der Optimierungsbedarf steigt
- Verwenden Sie nach Möglichkeit kantenbewertete Zielgruppen für die Echtzeit-Personalisierung. Reservieren Sie Streaming- und Batch-Zielgruppen für komplementäre Anwendungsfälle.
- Implementieren von Inhaltsexperimenten für personalisierte Erlebnisse, um zu überprüfen, ob die Personalisierung die messbare Steigerung gegenüber Standardinhalten bewirkt
- Gestalten der Personalisierung mit einer Strategie der ordnungsgemäßen Verschlechterung. Wenn das Profil am Edge nicht aufgelöst werden kann, sollten Sie anstelle eines fehlerhaften Erlebnisses gut gestaltete Standardinhalte anzeigen
- Verwenden Sie berechnete Attribute, um hochwertige Personalisierungssignale wie Interaktionswert, Produktaffinität und Tage seit dem letzten Kauf zu erstellen, wodurch sowohl die segmentbasierte als auch die entscheidungsbasierte Personalisierungsqualität verbessert werden
- Pflegen Sie einen Content-Governance-Prozess, um sicherzustellen, dass personalisierte Inhalte auf allen Oberflächen aktuell, markenkonform und konform bleiben
- Überwachen Sie die Personalisierungsleistung nach Segment, um festzustellen, welche Zielgruppen am meisten von der Personalisierung profitieren und wo die Steigerung am stärksten ist

### Entscheidungen über Kompromisse

>[!NOTE]
>**Kompromiss: Granularität von Personalization im Vergleich zur Komplexität des Content-Managements**
>
>Eine granularere Personalisierung (mehr Segmente, mehr Inhaltsvarianten, mehr Oberflächen) liefert zunehmend maßgeschneiderte Erlebnisse, erfordert jedoch proportional mehr Aufwand bei der Inhaltserstellung, -pflege und -verwaltung.
>
>- **Höhere Granularität begünstigt:** besseres Kundenerlebnis, höhere Interaktion, stärkere Konversionssteigerung
>- **Geringere Granularität begünstigt:** Schnellere Implementierung, geringerer Aufwand für die Inhaltswartung, einfachere Governance
>- **Empfehlung:** Sie mit 3-5 wirkungsvollen Segmenten (z. B. Treuestufen oder Lebenszyklusphasen) mit einer klaren Inhaltsdifferenzierung. Erweitern Sie die Granularität auf der Grundlage der gemessenen Leistungssteigerung. Verwenden Sie Entscheidungsfindung (Option B), um die Granularität ohne proportionales Content-Management-Wachstum zu skalieren.

>[!NOTE]
>**Kompromiss: Echtzeit-Entscheidungsfindung vs. deterministische Inhaltssteuerung**
>
>Entscheidungsbasierte Personalisierung (Option B) bietet eine dynamische Optimierung, aber reduziert die direkte Kontrolle darüber, welche Inhalte jeder Besucher sieht. Die segmentbasierte Personalisierung (Option A) bietet vollständige deterministische Kontrolle, begrenzt aber die dynamische Optimierung.
>
>- **Entscheidungsvorteile:** Skalierbarkeit, automatische Optimierung, komplexe Eignungsszenarien
>- **Segmentbasierte Vorteile:** Vorhersagbarkeit, Compliance-Kontrolle, Stakeholder-Transparenz
>- **Empfehlung:** Verwenden Sie segmentbasierte Personalisierung für Compliance-sensible Inhalte (Regulatory Messaging, stufenspezifische Preise), wenn eine exakte Kontrolle erforderlich ist. Verwenden Sie Decisioning für Werbeinhalte, Angebote und Empfehlungen, bei denen die dynamische Optimierung einen Mehrwert bietet.

>[!NOTE]
>**Zielsetzung: Edge-Datenverfügbarkeit im Vergleich zur Personalisierungsvielfalt**
>
>Die von Edge ausgewertete Personalisierung ist auf Attribute beschränkt, die im Edge-Profilspeicher verfügbar sind. Umfassendere Personalisierungssignale (vollständiger Verhaltensverlauf, komplexe berechnete Attribute) erfordern möglicherweise eine Server-seitige Suche oder Vorberechnung.
>
>- **Nur-Edge-Vorteile:** Latenz unter Sekunden, einfachste Architektur
>- **Vorberechnete Anreicherungsvorteile:** Personalisierungssignale, komplexere Zielgruppendefinitionen
>- **Empfehlung** Verwenden Sie berechnete Attribute, um umfangreiche Verhaltenssignale vorab in Edge-verfügbare Profilattribute zu aggregieren. Dies liefert die Fülle von Verhaltensdaten mit der Geschwindigkeit der Edge-Auswertung.

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten weitere Details zu den Technologien und Konfigurationen, auf die in diesem Handbuch verwiesen wird.

### Web-Kanal-Personalisierung

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/web/create-web)
- [Konfiguration des Web-Kanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### In-App- und Inhaltskarten-Kanäle

- [In-App-Kanal - Übersicht](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Voraussetzungen für In-App-Kanal](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Erstellen von In-App-Nachrichten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Inhaltskarten-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Konfiguration der Inhaltskarte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Erstellen von Inhaltskarten](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Entscheidungs-Management

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization und Inhalte

- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Hilfsfunktionen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/pql/overview)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-linking-logic)
- [Profilübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/de/docs/experience-platform/profile/merge-policies/overview)

### Datenerfassung und SDK

- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/install/overview)
- [Übersicht über Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/de/docs/experience-platform/edge-network-server-api/overview)

### Kampagnen und Experimente

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Berechnete Attribute und Anreicherung

- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview)
- [Handbuch zur Benutzeroberfläche für berechnete Attribute](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/ui)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/intelligent-services/customer-ai/overview)

### Reporting und Analysen

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/home)

### Governance und Datenschutz

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/guardrails)
