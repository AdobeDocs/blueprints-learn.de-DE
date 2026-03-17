---
title: Cross-Channel-Journey mit Decisioning
description: Erfahren Sie, wie Sie eine mehrstufige Journey mit Echtzeit-Entscheidungsfindung orchestrieren können, um optimale Kanäle, Inhalte oder Angebote auszuwählen.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8992'
ht-degree: 2%

---


# Cross-Channel-Journey mit Decisioning

Dieses Handbuch bietet eine vollständige Implementierungsreferenz für Cross-Channel-Journey mit Decisioning. Es wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die mehrstufige Journey-Systeme koordinieren müssen, die Echtzeit-Entscheidungsfindung auf einem oder mehreren Journey-Knoten beinhalten.

Verwenden Sie dieses Handbuch, um die vollständige Landschaft der Implementierungsoptionen zu verstehen, Kompromisse zu bewerten und zur entsprechenden Experience League-Dokumentation zu navigieren, um detaillierte Konfigurationsanweisungen zu erhalten.

Cross-Channel-Journey mit Decisioning ist das komplexeste Kampagnenorchestrierungsmuster im [!DNL Adobe Experience Platform]. Es erweitert mehrstufig orchestrierte Journey durch Einbeziehung der Echtzeit-Entscheidungsfindung - mithilfe von [!DNL AJO] Decisioning, um den aktuellen Kontext eines Profils zu bewerten und an einem oder mehreren Entscheidungspunkten auf der Journey-Arbeitsfläche dynamisch den optimalen Kanal, Inhalt oder das Angebot auszuwählen.

## Anwendungsfall - Übersicht

Unternehmen müssen zunehmend adaptive, personalisierte Kunden-Journey bereitstellen, die dynamisch auf den Echtzeit-Kontext jedes Einzelnen reagieren, anstatt eine feste, vorab festgelegte Abfolge einzuhalten. Der bevorzugte Kanal eines Kunden, sein Interaktionsverlauf, seine Treuestufe, sein prognostizierter Lebensdauerwert und seine aktuellen Produktinteressen fließen in die Frage ein, welche Aktion an jedem Touchpoint die nächstbeste sein sollte.

Das Cross-Channel-Journey mit Entscheidungsfindung erfüllt diese Anforderungen, indem zwei leistungsstarke [!DNL AJO] kombiniert werden: Journey-Orchestrierung (die den mehrstufigen Fluss, die Zeitplanung, die Bedingungen und die Kanalbereitstellung verwaltet) und Entscheidungsfindung (die Eignungsregeln bewertet, Rangfolgestrategien anwendet und an jedem Entscheidungspunkt die optimale Angebots- oder Inhaltsvariante auswählt).

Dieses Muster ist geeignet, wenn:

- Die Journey muss sich dynamisch an den Echtzeitstatus jedes Profils anpassen, anstatt einem festen Kanal oder einer festen Inhaltssequenz zu folgen
- Mehrere Angebote, Inhaltsvarianten oder Kanäle sind auf einem oder mehreren Journey-Knoten möglich. Die beste Option sollte auf der Grundlage des Profilkontexts ausgewählt werden
- Um die Angebotsauswahl auf der gesamten Journey zu optimieren, ist ein KI-unterstütztes oder formularbasiertes Ranking erforderlich
- Das Unternehmen möchte die Kanalauswahllogik und das Angebotsmanagement in einem zentralisierten Entscheidungs-Framework konsolidieren, anstatt eine komplexe Verzweigungslogik beizubehalten

Die Zielgruppe umfasst Marketing-Fachleute für die Verwaltung von Lebenszyklusprogrammen, Treue-Journey, Win-Back-Sequenzen und Onboarding-Flüssen, bei denen eine skalierbare Personalisierung an jedem Touchpoint eine automatisierte Entscheidungsfindung erfordert.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden mit diesem Anwendungsfallmuster erreicht.

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Passen Sie Inhalte, Angebote und Nachrichten an individuelle Voreinstellungen, Verhaltensweisen und Lebenszyklusphasen an.
**KPIs:**, Konversionsraten, Kundenzufriedenheit (CSAT)

**[Steigerung der Kundentreue und des Lebenszeitwerts](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Vertiefung der Kundenbeziehungen und Maximierung des langfristigen Nutzens durch Treueprogramme, Prämien und personalisierte Interaktion.
**KPIs:** Kundenlebenszeitwert, Kundenbindung, Upsell/Crosssell %

**[Verbesserung der Kundenbindung](../../business-objectives/customer-experience/improve-customer-retention.md)**
Halten Sie bestehende Kundinnen und Kunden durch wertorientierte Erlebnisse und kontinuierliche Pflege von Beziehungen in Kontakt und erneuern Sie diese.
**KPIs:**, Kundenlebenszeitwert, Interaktion

**[Umsatz durch Crosssell und Upsell steigern](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Werben Sie für ergänzende und Premium-Produkte oder -Services für bestehende Kunden auf der Grundlage des Verhaltens und der Kaufhistorie.
**KPIs:** Upsell-/Crossselling- %, inkrementeller Umsatz, Kundenlebenszeitwert

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie Cross-Channel-Journey mit Decisioning in der Praxis angewendet werden kann.

- **Adaptives Win-Back-Journey** - Ein mehrstufiges Journey, bei dem Decisioning den Kanal (E-Mail, Push oder SMS) auf der Grundlage des Interaktionsverlaufs jedes Profils auswählt und dynamisch das beste Incentive-Angebot auf der Grundlage des prognostizierten Lebenszeitwerts auswählt
- **Next-best-action-Lifecycle-Journey** - Die Entscheidungsfindung bestimmt, was in jeder Phase des Kundenlebenszyklus kommuniziert werden soll. Dabei wird zwischen Onboarding-Inhalten, Crosssell-Angeboten, Treueprämien oder Kundenbindungsanreizen ausgewählt
- **Personalisiertes Onboarding mit dynamischer Inhaltsauswahl** - Onboarding-Journey für neue Kunden, bei der jeder Touchpoint mithilfe von Entscheidungsfindung die relevantesten Produktschulungsinhalte, Tipps oder Aktivierungsangebote auswählt
- **Cross-Channel-Treueprogramm-Journey mit personalisierten Prämien** - Mitglieder des Treueprogramms entwickeln eine Journey, auf der Decisioning personalisierte Prämienangebote basierend auf der Stufe, dem Kaufverlauf und der Kategorieaffinität auswählt
- **Dynamische Rückgewinnung mit Kanal- und Anreizoptimierung** — Ruhende Rückgewinnung von Kunden, wobei sowohl der Outreach-Kanal als auch der Anreiz dynamisch ausgewählt werden, um die Reaktionswahrscheinlichkeit zu maximieren
- **Customer Lifecycle Nurture mit KI-bewerteten Inhaltsempfehlungen** - Fortlaufendes Nurture-Journey, bei dem KI-bewertete Entscheidungen die relevantesten Inhalte oder Produktempfehlungen an jedem Touchpoint auswählen

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Journey-Abschlussrate | Prozentualer Anteil der Profile, die den vollständigen Journey abschließen | Journey-Bericht: abgeschlossen/eingegeben |
| Annahmerate | Prozentsatz der entscheidungsausgewählten Angebote, mit denen interagiert wird (angeklickt, eingelöst) | Entscheidungsbericht: Angebotsklicks/Angebots-Impressionen |
| Kanalinteraktionsrate | Öffnungs- und Klickraten für jeden auf der Journey verwendeten Kanal | Versandmetriken pro Kanal im Journey-Bericht |
| Konversionsrate | Prozentualer Anteil der Journey-Teilnehmer, die die Zielkonversionsaktion abgeschlossen haben | Journey-Exitevent-Tracking oder CJA funnel Analysis |
| Fallback-Angebotsrate | Prozentsatz der Entscheidungsanfragen, die das Fallback-Angebot anstelle eines personalisierten Angebots zurückgeben | Entscheidungsbericht: Fallback-Auswahl/Gesamtauswahl |
| Auswirkungen auf den Kundenlebenszeitwert | Veränderung der CLV für Journey-Teilnehmer vs. Kontrollgruppe | CJA-Kohortenanalyse mit Holdout-Vergleich |
| Crosssell-/Upsell-Umsatz | Inkrementeller Umsatz, der den durch die Entscheidungsfindung ausgewählten Angeboten zugeordnet wird | CJA-Attributionsanalyse zu angebotsgesteuerten Konversionen |
| Effektivität der Entscheidungsrangliste | Leistungsunterschied zwischen KI-bewerteten Angeboten und zufälliger/prioritätsbasierter Auswahl | A/B-Experiment zum Vergleich von Rangfolgestrategien |

## Anwendungsfallmuster

**Cross-Channel-Journey mit Decisioning**

Orchestrieren Sie eine mehrstufige Multi-Channel-Journey, die Echtzeit-Entscheidungsfindung an einem oder mehreren Knoten beinhaltet, um den optimalen Kanal, Inhalt oder Angebot auszuwählen.

**Funktionskette:** Zielgruppenauswertung > Journey-Ausführung > Entscheidungsknoten > Kanalauswahl > Nachrichtenversand > Berichterstellung

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Adobe Journey Optimizer]([!DNL AJO])** - Journey-Orchestrierung (mehrstufiges Canvas-Design, Einstiegsbedingungen, Wartezeiten, Bedingungen, Ausstiegskriterien), Nachrichten-Authoring kanalübergreifend, Kanaloberflächenkonfiguration, Konflikt- und Prioritätsverwaltung
- **[!DNL Adobe Journey Optimizer]Decisioning** - Verwaltung von Angeboten und Inhaltselementen, Eignungsregeln, Rangfolgestrategien (Priorität, Formel, KI), Entscheidungsrichtlinien, Platzierungen, Fallback-Angebote
- **[!DNL Adobe Real-Time Customer Data Platform]([!DNL RT-CDP])** - Zielgruppenbewertung für Journey-Eintritts- und Angebotseignungssegmente, Profilanreicherung mit berechneten Attributen und Tendenzwerten, Einverständnis- und Governance-Durchsetzung
- **[!DNL Adobe Experience Platform]([!DNL AEP])** — Echtzeit-Kundenprofilspeicher, Identity Service für Cross-Channel-Auflösung, Datenmodellierung und Aufnahmeinfrastruktur

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | [!DNL AJO] Sandbox mit konfigurierten Journey-, Kampagnen- und Entscheidungsberechtigungen. Kanaloberflächen für alle möglichen Versandkanäle. Benutzerrollen für Journey-Designer, Entscheidungs-Manager und Inhaltsautoren. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Das Profilschema muss Attribute enthalten, die für die Entscheidungsfindung verwendet werden (z. B. Treuestufe, Kaufverlauf, Kanalvoreinstellungen, Interaktionswerte). Angebotskatalog- und Entscheidungselementschemata müssen konfiguriert werden. ExperienceEvent-Schemas müssen Verhaltenssignale erfassen, die von Eignungsregeln und Rangfolgenformeln verwendet werden. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Profilattribute und Verhaltenssignale, die von der Entscheidungsfindung verwendet werden, müssen aktuell sein. Das Ereignis-Streaming in Echtzeit ist erforderlich, wenn der Journey ereignisausgelöste Ein- oder Ausstiegskriterien verwendet. Web SDK, Mobile SDK oder Server-seitige Erfassung müssen für Kanäle aktiv sein, die den Entscheidungskontext unterstützen. | [Web SDK - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | Die kanalübergreifende Identitätsauflösung ist wichtig - die Journey muss Profile über E-Mail, Push, SMS und Internet auflösen. Zusammenführungsrichtlinien müssen ein einheitliches Profil für die Entscheidungsfindung erzeugen. Identity-Namespaces für alle Kundenkennungen (CRM-ID, E-Mail, ECID, Telefon) müssen konfiguriert werden. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Einstiegs-Zielgruppendefinition für den Journey. Zusätzliche Segmente, die für Angebotseignungsregeln und Bedingungsverzweigungen innerhalb der Journey verwendet werden. Die Auswertungsmethode muss den Latenzanforderungen entsprechen (Streaming für Echtzeiteingabe, Batch für geplant). | [Segmentation Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie Tendenzwerte für Kunden-KI, Interaktionswerte, Kanalpräferenzwerte und Berechnungen des Lebenszeitwerts verbessern die Entscheidungsqualität erheblich. Diese erweiterten Profilattribute ermöglichen komplexere Eignungsregeln und Rangfolgenformeln. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Data Lifecycle Management | Empfohlen | Daten zum Angebotsverlauf und zu Entscheidungsereignissen werden im Laufe der Zeit gesammelt und sollten Aufbewahrungsrichtlinien enthalten. Die Durchsetzung des Einverständnisses über mehrere Kanäle hinweg ist wichtig - Profile ohne gültiges Einverständnis für einen Kanal müssen aus dem Versandpfad dieses Kanals ausgeschlossen werden. | [Übersicht über das erweiterte Daten-Lifecycle-Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Die Durchsetzung von Governance auf mehreren Kanälen und Angebotstypen ist wichtig, wenn Entscheidungen Profile an verschiedene Kanäle mit unterschiedlichen Datennutzungsbeschränkungen weiterleiten können. Gewährleistet die konforme Bereitstellung von Angeboten auf allen Kanälen. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Journey- und Entscheidungsüberwachung sind für den Produktionsbetrieb unverzichtbar. Warnhinweise für Journey-Einstiegsfehler, Entscheidungs-Fallback-Spitzen und Versandfehler ermöglichen eine schnelle Problembehebung. | [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Journey- und Entscheidungsberichte werden in der Reporting-Phase behandelt. Die CJA-Analyse der Entscheidungseffektivität, der Kanalmixoptimierung, der Angebotsleistung und des Journey-ROI bietet die erforderlichen Einblicke, um Ranking-Strategien zu verfeinern und das Journey im Laufe der Zeit zu optimieren. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] ([!DNL AJO])

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kanalkonfiguration | Phase 2: Kanalkonfiguration | Konfigurieren Sie Kanaloberflächen für alle Kanäle, die die Entscheidungsfindung auswählen kann oder die die Journey verwendet (E-Mail, SMS, Push, In-App). |
| Verfassen von Nachrichten | Phase 4: Nachrichtenbearbeitung | Verfassen Sie Nachrichteninhalte für jeden Kanal und integrieren Sie die Entscheidungsausgabe - Angebotsplatzierungen, dynamische Inhaltsbausteine, Personalisierungs-Token aus ausgewählten Angeboten |
| Entscheidungsfindung | Phase 3: Einrichten der Entscheidungsfindung | Konfigurieren Sie Angebotselemente, Eignungsregeln, Rangfolgestrategien, Entscheidungsrichtlinien und Fallback-Angebote für jeden Entscheidungspunkt im Journey |
| Journey Orchestration | Phase 5: Journey-Design und -Aktivierung | Entwerfen Sie die mehrstufige Journey-Arbeitsfläche mit Einstiegsbedingungen, Entscheidungsknoten, Kanalrouting, Warteschritten, Nachrichtenaktionen und Beendigungskriterien |
| Konflikt- und Prioritätenmanagement | Phase 5: Journey-Design und -Aktivierung | Prioritätswerte und Konflikterkennung konfigurieren, wenn mehrere Journeys gleichzeitig auf dieselben Profile abzielen |
| Häufigkeits- und Geschäftsregeln | Phase 5: Journey-Design und -Aktivierung | Setzen Sie Obergrenzen für die Nachrichtenfrequenz kanalübergreifend durch, um Übermeldungen im Multi-Channel-Journey zu verhindern |
| Reporting und Leistungsanalyse | Phase 6: Reporting und Überwachung | Überwachen von Journey- und Bereitstellungsmetriken pro Knoten, Entscheidungsleistung und Kanalinteraktion |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 1: Evaluierung der Zielgruppe | Definieren und bewerten Sie die Eintrittzielgruppe oder das qualifizierte Eintrittsereignis; erstellen Sie Eignungssegmente, die von Decisioning verwendet werden. |
| Profilanreicherung | Voraussetzungen/Unterstützung | Profile mit berechneten Attributen und Tendenzwerten anreichern, die die Entscheidungsqualität verbessern |
| Durchsetzung von Einverständnis und Governance | Phase 2: Kanalkonfiguration | Einverständnisvoreinstellungen auf allen Kanälen durchsetzen; konforme Angebotsbereitstellung sicherstellen |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [ ] [!DNL AJO] Sandbox wurde mit aktivierten Journey-Orchestrierungs- und Entscheidungsfunktionen bereitgestellt
- [ ] Alle Zielkanäle (E-Mail, SMS, Push) haben aktive, verifizierte Kanaloberflächen
- [ ] Profilschema enthält Attribute, die für die Entscheidungsfindung erforderlich sind (Treuestufe, Kaufverlauf, Kanalvoreinstellungen, Interaktionswerte)
- [ ] die kanalübergreifende Identitätsauflösung konfiguriert ist - Profile können über E-Mail-, Push-Token-, Telefonnummer- und Web-IDs aufgelöst werden
- [ ] Einstiegs-Zielgruppe wird mit einer Population ungleich null definiert und ausgewertet
- [ ] Inhalt des Angebotskatalogs (Kreativ-Assets, Kopie, Haftungsausschlüsse) ist genehmigt und kann konfiguriert werden
- [ ] Einverständnisdaten werden aufgenommen und die Einverständnisdurchsetzung ist für alle Zielkanäle aktiv
- [ ] Inhaltsvorlagen und Fragmente für jeden Kanal werden entworfen und genehmigt
- [ ] Regeln zur Frequenzlimitierung werden definiert und bereitgestellt, wenn die Organisation kampagnenübergreifende Häufigkeitsrichtlinien hat
- [ ] Bei Verwendung der KI-Rangfolge-Entscheidungsfindung sind mindestens 1.000 Konversionsereignisse für das Modelltraining vorhanden

## Implementierungsoptionen

Überprüfen Sie die folgenden Optionen und wählen Sie den Ansatz aus, der Ihren Anforderungen am besten entspricht.

### Option A: Journey mit Offer Decisioning (fester Kanal, dynamischer Inhalt)

**Am besten geeignet für:** Journey, bei denen die Kanalsequenz vorgegeben ist, aber der Inhalt oder das Angebot an jedem Touchpoint dynamisch ausgewählt werden sollte - Treueprogramm-Journey mit personalisierten Belohnungen, Rückgewinnung von dynamischen Anreizen, Lebenszykluspflege mit KI-bewerteten Inhaltsempfehlungen.

#### Funktionsweise

Die Journey-Arbeitsfläche definiert die feste Sequenz von Kanälen und Timing (z. B. Tag 0: E-Mail, Tag 3: Push, Tag 7: SMS). Bei jedem Nachrichtenaktionsknoten wählt eine Entscheidungsrichtlinie das beste Angebot oder den besten Inhalt aus einem konfigurierten Katalog mit geeigneten Elementen aus, das bzw. der in die Nachricht aufgenommen werden soll. Angebote werden im [!DNL AJO] Decisioning-Katalog mit Eignungsregeln verwaltet, die filtern, für welches Profil sich ein Profil qualifiziert, und Rangfolgestrategien, die bestimmen, welches geeignete Angebot am besten geeignet ist.

Dieser Ansatz trennt das „Wann und Wo“ (Journey-Orchestrierung) vom „Was“ (Entscheidungsfindung). Der Journey-Designer steuert den Kanalfluss, während der Entscheidungs-Manager den Angebotskatalog, die Eignungsregeln und die Rangfolgelogik unabhängig steuert. Diese Trennung der Zuständigkeiten macht die Implementierung pflegeleichter und ermöglicht es dem Angebotskatalog, sich weiterzuentwickeln, ohne die Journey-Arbeitsfläche zu ändern.

Angebotsplatzierungen werden mithilfe der E-Mail-Designer oder anderer Kanaleditoren direkt in den Nachrichteninhalt eingebettet. Wenn die Nachricht zum Zeitpunkt des Versands gerendert wird, bewertet die Decisioning-Engine die Eignung und das Ranking des Profils, um das optimale Angebot für jede Platzierung in der Nachricht auszuwählen.

#### Wichtige Aspekte

- Die Kanalsequenz ist statisch - alle Profile folgen unabhängig von ihren Voreinstellungen demselben Kanalpfad
- Die Entscheidungskomplexität ist geringer, da nur Inhalte/Angebote und nicht Kanäle ausgewählt werden
- Angebotskatalog kann unabhängig von der Journey verwaltet werden
- Für jede Platzierung müssen Fallback-Angebote konfiguriert werden, um Profile ohne geeignete personalisierte Angebote zu verarbeiten

#### Vorteile

- Einfachere Journey-Arbeitsfläche - keine Verzweigungslogik für die Kanalauswahl
- Klare Trennung von Belangen zwischen Journey-Design und Angebotsverwaltung
- Einfacher zu testen und zu validieren - jeder Kanalpfad ist deterministisch
- Geringere Implementierungskomplexität und kürzere Time-to-Market
- Änderungen am Angebotskatalog werden sofort ohne Journey wirksam

#### Einschränkungen

- Der Kanal kann nicht auf der Grundlage des Verhaltens oder der Voreinstellungen einzelner Profile angepasst werden
- Profile, die einen Kanal gegenüber einem anderen bevorzugen, erhalten weiterhin Nachrichten über die vordefinierten Kanäle
- Optimiert nicht die Interaktionsraten auf Kanalebene

#### Experience League-Verweise

- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### Option B: Journey mit dynamischer Kanalauswahl (fester Inhalt, dynamischer Kanal)

**Am besten geeignet für:** Journey, bei denen der Inhalt an jedem Touchpoint ähnlich ist, der Kanal jedoch basierend auf dem Profilkontext dynamisch ausgewählt werden sollte - adaptives Win-back (E-Mail vs. Push vs. SMS basierend auf Interaktion), Programme mit der nächsten besten Aktion, bei denen die Kanaloptimierung das Hauptziel ist.

#### Funktionsweise

Der Journey verwendet Bedingungsknoten, die über Profilattribute (z. B. Kanalpräferenzwerte, letzter Interaktionskanal oder Einverständnisstatus) oder Entscheidungsausgabe informiert sind, um Profile zu verschiedenen Kanalpfaden zu leiten. Jeder Pfad stellt kanalspezifische Inhalte über einen eigenen Nachrichtenaktionsknoten bereit. Die Entscheidungslogik bestimmt anhand des Verhaltensverlaufs des Profils, welcher Kanal am wahrscheinlichsten Interaktionen hervorruft.

Die Kanalauswahl kann mithilfe von Journey-Bedingungsknoten mit Profilattributbewertungen implementiert werden (z. B. wenn `channelPreference = "push"` zum Push-Pfad weitergeleitet wird) oder durch Verwendung von Decisioning mit kanalspezifischen Elementen, bei denen jedes „Angebot“ einen Kanal darstellt und die Rangfolgestrategie den besten Kanal bestimmt.

Durch diesen Ansatz wird der Versandkanal optimiert, während die Inhalte kanalübergreifend relativ konsistent bleiben. Nachrichteninhalte müssen für jeden möglichen Kanal erstellt werden, und Kanaloberflächen müssen für alle möglichen Kanäle konfiguriert werden.

#### Wichtige Aspekte

- Erfordert Inhaltsvarianten für jeden Kandidaten-Kanal
- Kanaloberflächen müssen für alle möglichen Kanäle aktiv sein
- Die Bedingungslogik oder Entscheidungskonfiguration muss das Einverständnis berücksichtigen — Profile ohne SMS-Einverständnis können nicht an den SMS-Pfad weitergeleitet werden
- Das Journey der Arbeitsfläche ist mit Verzweigungspfaden für jeden Kanal komplexer

#### Vorteile

- Optimiert die Kanalauswahl für jedes einzelne Profil
- Erhöht die allgemeine Interaktion, indem Profile über ihren bevorzugten Kanal erreicht werden
- Respektiert das kanalspezifische Einverständnis automatisch durch einverständnisbewusstes Routing
- Können den Interaktionsverlauf und die Kanalpräferenzwerte in Routing-Entscheidungen integrieren

#### Einschränkungen

- Komplexere Journey-Arbeitsfläche mit mehreren Kanalverzweigungen
- Inhalte müssen für jeden Kanal separat erstellt werden (obwohl der Nachrichtenzweck derselbe ist)
- Schwieriger zu testen - alle möglichen Kanalpfade müssen validiert werden
- Die Inhaltspersonalisierung in jedem Kanal ist statisch (keine Angebotsentscheidung)

#### Experience League-Verweise

- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Option C: Vollständiges adaptives Journey (dynamischer Kanal + dynamischer Inhalt)

**Best for:** Maximale Personalisierung - Sowohl der Kanal als auch der Inhalt/das Angebot werden bei jedem Knoten dynamisch ausgewählt. Passend für hochwertige Kundensegmente, anspruchsvolle Treueprogramme und Organisationen mit ausgereiften Entscheidungspraktiken und umfangreichen Profildaten.

#### Funktionsweise

Diese Option kombiniert die Optionen A und B. Der Journey verwendet die Entscheidungsfindung auf zwei Ebenen: erstens, um zu bestimmen, welcher Kanal für jeden Touchpoint verwendet werden soll, und zweitens, um zu bestimmen, welche Inhalte oder Angebote im ausgewählten Kanal bereitgestellt werden sollen. Jeder Entscheidungspunkt auf der Journey bewertet den aktuellen Kontext des Profils, um sowohl die Kanal- als auch die Inhaltsauswahl vorzunehmen.

Die Implementierung erfordert eine umfassende Entscheidungseinrichtung mit Entscheidungsrichtlinien für die Kanalauswahl und die Inhalts-/Angebotsauswahl. Bei der Kanalauswahl kann eine Entscheidungsrichtlinie verwendet werden, bei der jedes Element einen Kanal mit Eignungsregeln darstellt, die auf dem Einverständnis und der Interaktion basieren, während bei der Inhaltsauswahl eine separate Entscheidungsrichtlinie mit Angebotselementen verwendet wird, die nach Relevanz sortiert sind.

Dies ist die komplexeste Variante und erfordert die tiefste Integration zwischen Journey-Orchestrierung und Entscheidungsfindung. Er bietet ein Höchstmaß an Personalisierung, erfordert aber auch die höchste Anzahl an Konfigurationen, Tests und kontinuierliches Management.

#### Wichtige Aspekte

- Erfordert zwei Entscheidungsebenen: Kanalauswahl und Inhaltsauswahl
- Die Komplexität der Journey-Arbeitsfläche ist am höchsten bei verschachtelten Verzweigungen und Entscheidungen an jedem Knoten
- Umfassende Tests für alle möglichen Kanal-Inhalt-Kombinationen erforderlich
- Erfordert umfangreiche Profildaten (Interaktionsverlauf, Kanalvoreinstellungen, Produktaffinität, Tendenzwerte) für eine effektive Entscheidungsfindung
- KI-bewertete Entscheidungen profitieren erheblich von berechneten Attributen

#### Vorteile

- Maximale Personalisierung: Jeder Touchpoint ist für Kanal und Inhalt optimiert
- Optimales Interaktions- und Konversionspotenzial für gut konfigurierte Implementierungen
- Zentralisiert die gesamte Personalisierungslogik in der Entscheidungsfindung anstelle von statischen Journey-Verzweigungen
- Kann durch das Lernen von KI-Rangfolgemodellen kontinuierlich verbessert werden

#### Einschränkungen

- Höchste Implementierungskomplexität und längste Time-to-Market
- Erfordert die umfassendste Vorbereitung des Angebotskatalogs und der Kanalinhalte
- Schwieriger zu beheben, wenn Versandprobleme auftreten
- Erfordert eine ausgereifte Dateninfrastruktur mit umfangreichen Profilattributen
- Die KI-Rangfolge erfordert für das Modelltraining ein ausreichendes Konversionsereignisvolumen

#### Experience League-Verweise

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Vergleich von Optionen

In der folgenden Tabelle können Sie die drei Implementierungsoptionen auf einen Blick vergleichen.

| Kriterien | Option A: Offer Decisioning | Option B: Dynamischer Kanal | Option C: Vollständig adaptiv |
| --- | --- | --- | --- |
| Am besten geeignet für | Feste Kanalsequenz, dynamischer Inhalt | Kanaloptimierung, konsistente Inhalte | Maximale Personalisierung über beide Dimensionen hinweg |
| Komplexität | Mittel | Medium-Hoch | Hoch |
| Journey-Arbeitsfläche | Einfach (linear mit Entscheidungsfindung an Aktionsknoten) | Mittelmäßig (Verzweigung für Kanalpfade) | Komplexe (verschachtelte Verzweigung mit mehrstufiger Entscheidungsfindung) |
| Entscheidungsumfang | Nur Inhalts-/Angebotsauswahl | Nur Kanalauswahl | Kanal- und Inhaltsauswahl |
| Inhaltsanforderungen | Ein Content-Set pro Kanal (mit Platzierungen) | Inhalt für jeden Kandidaten-Kanal | Inhalte mit Platzierungen für jeden Kandidatenkanal |
| Profildatenanforderungen | Moderat (Attribute für Angebotseignung) | Mittelmäßig (Kanalpräferenz, Interaktion) | Hoch (sowohl Kanal- als auch Angebotsattribute) |
| Markteinführungszeit | Schneller | mittelmäßig | längste |
| Laufende Verwaltung | Verwaltung des Angebotskatalogs | Kanalrouting-Logik-Verwaltung | Angebotskatalog und Kanalrouting |
| Personalization-Tiefe | Inhalt variiert, Kanal fest | Kanal variiert, Inhalt ähnlich | Kanal und Inhalt variieren |

### Wählen der richtigen Option

Verwenden Sie die folgenden Anleitungen, um die beste Option für Ihre Situation zu ermitteln.

- **Beginnen Sie mit Option A** wenn Ihre Kanalstrategie bereits definiert ist (z. B. „Wir senden immer zuerst E-Mails, dann Push, dann SMS„) und die primäre Personalisierungsanforderung darin besteht, das richtige Angebot oder den richtigen Inhalt für jeden Touchpoint auszuwählen. Dies ist der häufigste Ausgangspunkt für Organisationen, die noch nicht mit Entscheidungen vertraut sind.

- **Wählen Sie Option B**, wenn die Kanaloptimierung Ihr Hauptziel ist - Sie möchten jeden Kunden auf dem Kanal erreichen, mit dem er am ehesten interagieren würde, aber der Nachrichteninhalt ist über alle Kanäle hinweg relativ konsistent. Dies erfordert Kanalvoreinstellungsdaten für Profile.

- **Wählen Sie Option C** nur, wenn Sie über eine ausgereifte Entscheidungsinfrastruktur, umfangreiche Profildaten (einschließlich berechneter Attribute und Tendenzwerte), einen gut gefüllten Angebotskatalog und die organisatorische Kapazität zur Verwaltung der Komplexität verfügen. Viele Unternehmen beginnen mit Option A oder B und entwickeln sich mit zunehmender Entscheidungsreife zu Option C.

- **Wenn Sie unsicher sind** beginnen Sie mit Option A. Es bietet eine aussagekräftige Personalisierung mit der geringsten Komplexität, und der Angebotskatalog, den Sie für Option A erstellen, ist direkt wiederverwendbar, wenn Sie sich später zu Option C entwickeln.

## Implementierungsphasen

Die folgenden Phasen führen durch die End-to-End-Implementierung dieses Anwendungsfallmusters.

### Phase 1: Evaluierung der Zielgruppe

**Anwendungsfunktion:** [!DNL RT-CDP]: Zielgruppenauswertung

In dieser Phase wird die Einstiegs-Audience konfiguriert, die bestimmt, welche Profile in die Journey eintreten, sowie alle zusätzlichen Segmente, die für Angebotseignungsregeln oder Bedingungsverzweigungen innerhalb der Journey verwendet werden. Die Zielgruppendefinition ist die Grundlage für alle nachgelagerten Journey- und Entscheidungslogiken.

#### Entscheidung: Eintragstyp

Wie sollen Profile über eine geplante Zielgruppe oder einen Echtzeit-Ereignis-Trigger auf die Journey gelangen?

>[!NOTE]
>Wählen Sie je nach Zeitplanung und Auslöseanforderungen des Journey einen Eintragstyp aus.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Zielgruppe lesen (Batch-Eingabe) | Lebenszyklusprogramme, Treue-Journey, geplante Rückgewinnungskampagnen | Profile werden zu geplanten Zeiten in Batches eingegeben; Zielgruppe wird zur Lesezeit ausgewertet; unterstützt große Zielgruppengrößen |
| Zielgruppen-Qualifizierung (Streaming) | Verhaltensgesteuerte Journey, bei denen der Eintritt erfolgen soll, wenn ein Profil in ein Segment eintritt oder aus einem Segment austritt | Fast Echtzeit-Eintritt; erfordert Streaming-fähige Segmentdefinition; geeignet für Milestone-basierte Journey |
| Unitäres Ereignis (Ereignis-Trigger) | Bei einem bestimmten Ereignis sollte die Journey (z. B. Kauf, Warenkorbabbruch, Registrierung) als Trigger dienen. | Echtzeit-Eintritt bei Ereignis; erfordert Konfiguration des Ereignisschemas; begrenzt auf 5.000 Ereignisse/Sekunde |

#### Entscheidung: Methode zur Zielgruppenauswertung

Wie schnell muss die Zielgruppe Profile qualifizieren?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Batch | Tägliche oder regelmäßige Zielgruppenaktualisierungen sind ausreichend. Geplante Journey im Kampagnenstil | Verarbeitet bis zu 24 Millionen Profile pro Auftrag; zeitplanbasiert; die meisten Segmentregelausdrücke werden unterstützt |
| Streaming | Für einen ereignisgesteuerten oder qualifikationsbasierten Eintrag ist eine Zielgruppenzugehörigkeit in Echtzeit erforderlich | Nahezu in Echtzeit; begrenzte Segmentregelfunktion festgelegt; keine zeitbasierten Aggregationen |
| Edge | Qualifizierung derselben Sitzung erforderlich | Millisekunden-Latenz; nur einfache Attributprüfungen; auf Edge-Profilattribute beschränkt |

#### Wichtige Konfigurationsdetails

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

- Definieren der Einstiegszielgruppe mit Segment Builder mit Segmentregelausdrücken, die auf die relevanten Profilattribute und Verhaltensereignisse abzielen
- Erstellen Sie zusätzliche Eignungssegmente, wenn die Regeln der Angebotseignung auf die Segmentzugehörigkeit verweisen (z. B. „High Value Customers“, „Loyalty Gold Tier„).
- Überprüfen Sie, ob die Zielgruppenpopulation ungleich null ist, bevor Sie mit der Journey-Konfiguration fortfahren.
- Wählen Sie die Zusammenführungsrichtlinie aus, die die für die Entscheidung erforderliche einheitliche Profilansicht erzeugt

#### Dokumentation zu Experience League

- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Kanalkonfiguration

**Anwendungsfunktion:** [!DNL AJO]: Kanalkonfiguration

In dieser Phase werden Kanaloberflächen für jeden Kanal konfiguriert, den die Journey für den Nachrichtenversand verwenden kann. Alle Kandidatenkanäle müssen über aktive, verifizierte Oberflächen verfügen, bevor Nachrichten verfasst oder die Journey veröffentlicht werden können. Für dieses Muster konfigurieren Sie in der Regel mindestens Oberflächen für E-Mail, SMS und Push-Benachrichtigungen - und möglicherweise In-App- oder Web-Entscheidungen, wenn diese Kanäle ausgewählt werden.

#### Entscheidung: Welche Kanäle konfiguriert werden sollen

Welche Kanäle kommen für die Journey in Frage - entweder als feste Journey-Schritte (Optionen A/B) oder als entscheidungsselektierbare Kanäle (Optionen B/C)?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur E-Mail | Einkanal-Journey mit Offer Decisioning (Option A, nur E-Mail) | Einfache Konfiguration; Subdomain-Delegierung und IP-Aufwärmung erforderlich |
| E-Mail + Push | Zwei-Kanal-Journey; häufig für interaktionsorientierte Journey | Push-Benachrichtigungen erfordern APNs/FCM-Anmeldeinformationen; Mobile App muss SDK integriert haben |
| E-Mail + SMS + Push | Vollständiges Cross-Channel-Journey; am häufigsten für die Optionen B und C | SMS erfordert Provider-Anmeldedaten (Sinch, Twilio, Infobip); jeder Kanal benötigt eine eigene Oberfläche |
| E-Mail + SMS + Push + In-App | Maximale Kanalabdeckung einschließlich Sitzungsoberflächen | Für In-App-Nachrichten ist die Konfiguration der mobilen SDK- und App-Oberfläche erforderlich |

#### Entscheidung: Methode der Subdomain-Zuweisung (E-Mail)

Wie sollte die sendende Subdomain an Adobe delegiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Vollständige Delegierung | Das Unternehmen möchte, dass Adobe alle DNS-Einträge für die sendende Subdomain verwaltet | Einfachste Einrichtung; Adobe übernimmt SPF, DKIM, DMARC; weniger Kontrolle über DNS |
| CNAME-Delegierung | Organisation muss die Kontrolle über DNS-Einträge behalten | Komplexere Einrichtung, kundenseitige DNS-Verwaltung, größere Flexibilität |

#### Wichtige Konfigurationsdetails

**UI-Navigation:** Administration > Kanäle > Kanaloberflächen > Oberfläche erstellen

- Für E-Mails: Subdomain, IP-Pool, Absendername, Antwortadresse und Abmeldeverarbeitung konfigurieren
- Für SMS: Konfigurieren der Anmeldeinformationen des SMS-Anbieters und der Absendernummer
- Für Push: Konfigurieren von APNs und FCM-Anmeldeinformationen für iOS und Android
- Stellen Sie sicher, dass jede Oberfläche den Status Aktiv aufweist, bevor Sie fortfahren
- Bestätigen, dass das IP-Aufwärmen für E-Mail-Versand-IPs abgeschlossen ist

#### Dokumentation zu Experience League

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Phase 3: Einrichtung der Entscheidungsfindung

**Anwendungsfunktion:** [!DNL AJO]: Decisioning

In dieser Phase wird das gesamte Entscheidungs-Framework konfiguriert, einschließlich Platzierungen, Eignungsregeln, personalisierten Angeboten, Fallback-Angeboten, Sammlungsqualifizierern, Sammlungen, Rangfolgestrategien und Entscheidungsrichtlinien. In dieser Phase wird die Entscheidungslogik erstellt, die an Journey-Entscheidungspunkten aufgerufen wird.

#### Entscheidung: Entscheidungsumfang

Was sollte die Entscheidungsfindung auswählen - Angebote/Inhalte (Option A), Kanäle (Option B) oder beides (Option C)?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Angebots-/Inhaltsauswahl | Die Kanalsequenz ist unveränderlich; Personalisierung ist im Inhalt enthalten | Entscheidungsrichtlinien zielen auf Angebotselemente mit Inhaltsdarstellungen pro Platzierung ab |
| Nur Kanalauswahl | Der Inhalt ist konsistent. Die Optimierung erfolgt auf dem Versandkanal | Entscheidungselemente stellen Kanäle dar; die Eignung umfasst Einverständnisprüfungen; die Rangfolge verwendet Interaktionsdaten |
| Kanal und Inhalt | Vollständige adaptive Personalisierung für alle Kanäle und Inhalte | Erfordert zwei Ebenen von Entscheidungsrichtlinien; die komplexeste, aber auch die höchste Personalisierungsebene |

#### Entscheidung: Rangfolgestrategie

Wie sollten geeignete Angebote eingestuft werden, um das beste Angebot auszuwählen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Prioritätsbasiert (manuell) | Einfaches Ranking, bei dem die Geschäftsregeln die Wichtigkeit des Angebots bestimmen | Jedes Angebot erhält einen Prioritätswert; die höchste Priorität gewinnt; deterministisch und leicht zu verstehen |
| Formelbasiert (benutzerdefinierter Ausdruck) | Die Rangfolge sollte in Profilattributen berücksichtigt werden (z. B. CLV, Stufe, Affinitätswert) | Benutzerdefinierte Rangfolgeformel wertet Profilkontext aus; dynamischer als Priorität; keine ML erforderlich |
| KI-Rangfolge (automatische Optimierung) | Das Ranking sollte automatisch basierend auf historischen Konversionsdaten optimiert werden | KI-Modell lernt aus Konversionsereignissen; erfordert mindestens 1.000 Ereignisse für das Training; verbessert sich kontinuierlich |

#### Entscheidung: Angebotsbegrenzung

Sollte es Grenzen dafür geben, wie oft ein Angebot angezeigt wird?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Obergrenze pro Profil | Verhindern, dass dasselbe Angebot wiederholt demselben Profil angezeigt wird | Schützt vor Angebotsermüdung; Zählerverzögerung bei hohem Durchsatz möglich |
| Globale Begrenzung | Begrenzung der Gesamtzahl der Impressions für alle Profile (z. B. eingeschränkte Inventar-Promotions) | Kontrolliert die Gesamtexposition; nützlich für Angebote mit begrenztem Angebot |
| Keine Begrenzung | Jede geeignete Impression sollte das Angebot anzeigen | Einfach; geeignet für zeitlose Inhalte oder unbegrenzte Angebote |

#### Wichtige Konfigurationsdetails

**UI-Navigation:** Komponenten > Entscheidungs-Management > Platzierungen/Angebote/Entscheidungen

- Erstellen Sie Platzierungen für jede Kombination aus Kanal und Inhaltstyp (z. B. E-Mail, HTML-Banner, Push-JSON, SMS-Text)
- Definieren von Eignungsregeln mithilfe von Segmentregelausdrücken, die auf Profilattribute oder die Zielgruppenzugehörigkeit verweisen
- Personalisierte Angebote mit Darstellungen für jede Platzierung erstellen, Eignungsregeln zuweisen und Priorität festlegen
- Erstellen Sie ein Fallback-Angebot, das alle Platzierungen abdeckt. Dies wird zurückgegeben, wenn kein personalisiertes Angebot qualifiziert ist.
- Organisieren von Angeboten in Sammlungen mithilfe von Sammlungsqualifizierern (Tags)
- Konfigurieren der Rangfolgestrategie - prioritätsbasiert, formularbasiert oder KI-Rangfolge
- Entscheidungsrichtlinien erstellen, die Platzierungen, Sammlungen, Rangfolgestrategien und Fallback-Angebote verbinden
- Alle Angebote validieren, bevor sie per Entscheidung ausgewählt werden können

#### Wo die Optionen auseinander gehen

**Für Option A (Offer Decisioning):**
Erstellen Sie in jedem Kanal Platzierungen und Angebote mit Fokus auf die Personalisierung von Inhalten (z. B. E-Mail-Hero-Bannerangebot, E-Mail-Fußzeilen-Angebot, Push-Benachrichtigungs-Textkörper-Angebot). Entscheidungsrichtlinien wählen für jede Platzierung in der Nachricht den besten Inhalt aus.

**Für Option B (dynamische Kanalauswahl):**
Erstellen Sie Entscheidungselemente, die für jeden Kanal stehen. Eignungsregeln umfassen Einverständnisprüfungen (z. B. muss ein Profil über ein SMS-Einverständnis verfügen, um für das SMS-Element infrage zu kommen). Die Rangfolge verwendet Kanalinteraktionswerte oder formularbasierte Ausdrücke.

**Für Option C (Voll adaptiv):**
Konfigurieren Sie zwei Entscheidungsebenen: einen Satz von Entscheidungsrichtlinien für die Kanalauswahl und einen separaten Satz für die Inhalts-/Angebotsauswahl im ausgewählten Kanal. Beide Ebenen erfordern Platzierungen, Angebote, Eignungsregeln und Rangfolgestrategien.

#### Dokumentation zu Experience League

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Nachrichtenbearbeitung

**Anwendungsfunktion:** [!DNL AJO]: Nachrichtenbearbeitung

In dieser Phase wird der Nachrichteninhalt für jeden Kanal und Touchpoint im Journey konfiguriert, wobei die Entscheidungsausgabe (ausgewählter Angebotsinhalt) in die Nachrichtenvorlagen integriert wird. Jeder Nachrichtenaktionsknoten auf der Journey erfordert erstellte Inhalte mit der entsprechenden Kanaloberfläche, Personalisierungs-Token und Angebotsplatzierungs-Integrationen.

#### Entscheidung: Content-Ansatz

Wie sollte der Nachrichteninhalt für jeden Kanal erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Vorlagenbasiert | Das Unternehmen hat Markenvorlagen etabliert. Konsistenz ist wichtig | Schnelleres Authoring; Sicherstellung der Markenkonsistenz; kann die Flexibilität beim Design einschränken |
| Von Grund auf gestalten | Eindeutige Kreativvorlage für diese Journey; keine existierenden Vorlagen | Vollständige Design-Kontrolle; längere Bearbeitungszeit; Verwenden von E-Mail-Designer Drag-and-Drop |
| HTML importieren | Creative-Team produziert HTML extern; importieren in [!DNL AJO] | Behält externen Design-Workflow bei; erfordert HTML-Kompatibilität mit E-Mail-Designer |

#### Entscheidung: Umfang von Personalization

Welchen Grad an Personalisierung sollten Nachrichten über die Entscheidungsausgabe hinaus beinhalten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Grundlegende Personalisierung (Name, Begrüßung) | Minimale Personalisierungsanforderungen jenseits der Angebotsauswahl | Einfache Handlebars-Ausdrücke; geringe Komplexität |
| Bedingte Inhaltsbausteine | Verschiedene Inhaltsabschnitte für verschiedene Segmente oder Attribute | Verwendet dynamische Inhaltsregeln; Inhalt variiert je nach Profilattribut oder Segmentzugehörigkeit |
| Vollständige Personalisierung mit Entscheidungsintegration | In eine Nachricht eingebettete Angebotsplatzierungen in Kombination mit profilbasierter Personalisierung | Kombiniert Offer Decisioning-Ausgabe mit Handlebars-Personalisierungs-Token; umfangreichste Erfahrung |

#### Wichtige Konfigurationsdetails

**UI-Navigation:** Wählen Sie Kampagnen- oder Journey-Aktion > Inhalt bearbeiten > E-Mail an Designer / Kanaleditor

- Verfassen Sie Nachrichteninhalte für jeden Kanal, der auf der Journey verwendet wird (E-Mail, SMS, Push, In-App)
- Platzierungen von Angebotsentscheidungen in Nachrichteninhalte einbetten, in denen entscheidungsausgewählte Angebote angezeigt werden sollen
- Hinzufügen von Personalisierungsausdrücken mithilfe der Handlebars-Syntax für Profilattribute (z. B. `{{profile.person.name.firstName}}`)
- Konfigurieren von bedingten Inhaltsbausteinen für segmentspezifisches Messaging
- Erstellen wiederverwendbarer Inhaltsfragmente für freigegebene Elemente (Kopfzeilen, Fußzeilen, Haftungsausschlüsse)
- Vorschau und Test mit Beispielprofilen, um zu überprüfen, ob die Personalisierung korrekt dargestellt wird
- Testversandnachrichten zur Überprüfung durch Stakeholder senden

#### Wo die Optionen auseinander gehen

**Für Option A (Offer Decisioning):**
Jede Nachricht enthält Angebotsplatzierungen, in denen entscheidungsausgewählte Inhalte angezeigt werden. Das Nachrichten-Layout ist konsistent, aber der Angebotsbereich zeigt dynamisch das beste Angebot für jedes Profil an.

**Für Option B (dynamische Kanalauswahl):**
Jeder Kanal verfügt über einen eigenen Nachrichteninhalt, der separat erstellt wird. Der Inhalt ist kanalübergreifend ähnlich, aber an die Kanalbeschränkungen angepasst (E-Mail-HTML vs. SMS-Text vs. Push-Benachrichtigungsformat).

**Für Option C (Voll adaptiv):**
Jeder Kanal verfügt über seinen eigenen Nachrichteninhalt mit eingebetteten Angebotsplatzierungen. Sowohl der Kanal als auch der Angebotsinhalt in diesem Kanal werden dynamisch ausgewählt.

#### Dokumentation zu Experience League

- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Erstellen einer SMS-Nachricht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Gestalten einer Push-Benachrichtigung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Phase 5: Design und Aktivierung von Journey

**Anwendungsfunktion:** [!DNL AJO]: Journey Orchestration, [!DNL AJO]: Konflikt- und Prioritätsverwaltung, [!DNL AJO]: Häufigkeit und Geschäftsregeln

In dieser Phase wird die gesamte Journey-Arbeitsfläche konfiguriert, einschließlich Einstiegskonfiguration, Entscheidungsknoten, die mit konfigurierten Entscheidungsrichtlinien verknüpft sind, Bedingungsaufteilungen für das Kanalrouting (Optionen B/C), Nachrichtenaktionsknoten für jeden Kanalpfad, Warteknoten zwischen Touchpoints, Beendigungskriterien, Konflikt-/Prioritätseinstellungen und Frequenzbegrenzungsregeln. In dieser Phase werden alle zuvor konfigurierten Komponenten in den orchestrierten Journey-Fluss zusammengeführt und aktiviert.

#### Entscheidung: Richtlinie für den Wiedereintritt

Können Profile nach Abschluss oder Verlassen die Journey erneut aufrufen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Erneuten Eintritt erlauben (mit Abklingzeit) | Wiederkehrende Journey, bei denen sich Profile erneut qualifizieren können (z. B. vierteljährliche Verlängerung der Treue) | Legen Sie einen Abklingzeitraum (mindestens 5 Minuten) fest, um einen sofortigen erneuten Eintritt zu verhindern. Das Profil wird von Anfang an neu gestartet |
| Kein Wiedereintritt | Einmalige Journey, bei denen jedes Profil nur einmal durchlaufen werden soll (z. B. Onboarding) | Profil kann nach Abschluss oder Beenden nicht erneut eintreten. Einfacheres Verhalten |

#### Entscheidung: Ausstiegskriterien

Unter welchen Bedingungen sollte ein Profil vor Abschluss von der Journey entfernt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Änderung der Zielgruppenzugehörigkeit | Das Profil sollte beendet werden, wenn es die Einstiegszielgruppe verlässt oder in eine Unterdrückungszielgruppe eintritt | Echtzeit-Austritt bei Segmentänderung; nützlich für „konvertierte“ oder „Opt-out“-Austritte |
| Ereignis-Intervall | Ein bestimmtes Ereignis (z. B. Kauf, Abo beenden) sollte den Trigger beenden | Echtzeit-Beenden bei Ereignis; erfordert Konfiguration des Ereignisschemas |
| Zeitüberschreitung | Maximale Dauer in der Journey verstrichen | Der Standardwert ist 91 Tage. Verhindert, dass Profile unbegrenzt bleiben |

#### Entscheidung: Zeitüberschreitung beim Journey

Wie lange kann ein Profil maximal auf der Journey bleiben?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| 91 Tage (maximal) | Langlebige Journey mit erweiterten Nurture-Sequenzen | Maximal zulässige Dauer; Profile beenden dies nach 91 Tagen, unabhängig davon |
| Benutzerdefinierte kürzere Dauer | Zeitgebundene Kampagnen oder saisonale Journey | Auf Journey-Geschäftslogik basierend festgelegt; eine kürzere Zeitüberschreitung reduziert veraltete Profile. |

#### Entscheidung: Konflikt- und Prioritätseinstellungen

Sollte diese Journey für die Konfliktlösung mit anderen Journey/Kampagnen vorrangig bewertet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Hohe Priorität (70-100) | Kritische Journey (Kundenbindung, Treue), die Vorrang haben sollten | Höhere Priorität gewinnt, wenn mehrere Kommunikationen miteinander konkurrieren. Verwenden Sie sparsam |
| Medium-Priorität (30-69) | Standard-Lebenszyklus-Journey | Ausgeglichene Priorität; kann durch Kommunikation mit höherer Priorität unterdrückt werden |
| Niedrige Priorität (0-29) | Ergänzende oder informative Journey | Wird unterdrückt, wenn mit wichtigeren Kommunikationen konkurriert wird |

#### Wichtige Konfigurationsdetails

**UI-Navigation:** Journey > Journey erstellen

- Erstellen der Journey und Konfigurieren der Eigenschaften (Name, Beschreibung, Zeitzone, Zeitüberschreitung)
- Eintrag konfigurieren: Zielgruppe lesen (für Batch) oder Ereignis-Trigger (für Echtzeit)
- Hinzufügen von Entscheidungsknoten, die mit konfigurierten Entscheidungsrichtlinien aus Phase 3 verknüpft sind
- Hinzufügen von Bedingungsaufteilungen für das Kanal-Routing basierend auf Entscheidungsausgabe oder Profilattributen (Optionen B/C)
- Fügen Sie Nachrichtenaktionsknoten für jeden Kanalpfad hinzu und verknüpfen Sie ihn mit den in Phase 4 erstellten Inhalten
- Hinzufügen von Warteknoten zwischen Touchpoints (mindestens 1 Stunde für Journey, die von einer Zielgruppe gelesen werden)
- Beendigungskriterien definieren (Zielgruppenänderung, Ereignis, Zeitüberschreitung)
- Zuweisen einer Prioritätsbewertung für die Konfliktlösung
- Konfigurieren der Frequenzlimitierung, wenn Cross-Journey-Frequenzlimitierungen gelten
- Testen der Journey im Testmodus mit Testprofilen vor der Veröffentlichung
- Journey veröffentlichen, um sie live zu schalten

#### Wo die Optionen auseinander gehen

**Für Option A (Offer Decisioning):**
Die Journey-Arbeitsfläche ist linear mit Entscheidungsrichtlinien, die in jedem Nachrichtenaktionsknoten eingebettet sind. Keine Verzweigung für die Kanalauswahl. Die Angebotsentscheidung wird zum Zeitpunkt der Nachrichtenwiedergabe im Aktionsknoten getroffen.

**Für Option B (dynamische Kanalauswahl):**
Fügen Sie nach jedem Warteschritt einen Bedingungsknoten hinzu, der Kanalauswahlkriterien (Profilattribute, Entscheidungsausgabe oder Einverständnisstatus) auswertet. Jede Bedingungsverzweigung führt zu einem kanalspezifischen Nachrichtenaktionsknoten. Fügen Sie einen Standard-/Sonst-Pfad für Profile ein, die keiner Bedingung entsprechen.

**Für Option C (Voll adaptiv):**
Kombinieren Sie Kanalauswahl-Bedingungsknoten mit in Entscheidungsrichtlinien eingebetteten Nachrichtenaktionsknoten. An jedem Touchpoint: Zunächst bestimmt eine Bedingung oder Entscheidung den Kanal; dann wählt eine Entscheidungsrichtlinie innerhalb der Nachrichtenaktion des ausgewählten Kanals das optimale Angebot/den optimalen Inhalt aus.

#### Dokumentation zu Experience League

- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Übersicht über Konflikt- und Prioritätsmanagement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Phase 6: Berichterstattung und Überwachung

**Anwendungsfunktion:** [!DNL AJO]: Reporting und Leistungsanalyse

In dieser Phase wird die Journey- und Entscheidungsleistungsüberwachung über Live-Berichte (während der Ausführung) und Verlaufsberichte (nach Abschluss) konfiguriert. Entscheidungsspezifische Metriken einschließlich Angebotsauswahl, Verteilung, Fallback-Raten und Ranking-Effektivität. Optional CJA Workspace-Analyse für tiefes kanalübergreifendes Journey und ROI-Entscheidungsanalyse.

#### Entscheidung: Berichtstiefe

Welcher Grad an Reporting- und Analysearbeit ist erforderlich?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native Berichte [!DNL AJO] | Operative Überwachung der Versand- und Interaktionsmetriken | Integrierte Live- und Verlaufsberichte, keine zusätzliche Konfiguration, beschränkt auf [!DNL AJO] Metriken |
| [!DNL AJO] + CJA-Analyse | Tiefe kanalübergreifende Analyse, Entscheidungseffektivität, Journey-ROI, Kohortenanalyse | Erfordert CJA-Verbindung und Datenansicht; bietet Funktionen zur Attribution, funnel und Kohortenanalyse |

#### Wichtige Konfigurationsdetails

**UI-Navigation:** Journey > Journey auswählen > Live-Bericht / All-Time-Bericht

- Überwachen des Journey-Live-Berichts bei der ersten Ausführung für Metriken zu Eintritt, Austritt und pro Knoten
- Überprüfen der Entscheidungsleistung: Angebotsauswahl, Verteilung, Fallback-Angebotsrate, Ranking-Effektivität
- Überprüfen Sie nach Abschluss des Journey die Verlaufsberichte, um eine vollständige funnel-Analyse zu erhalten
- Für die CJA-Analyse: Stellen Sie sicher, dass die CJA-Verbindung [!DNL AJO] Datensätze enthält (Nachrichten-Feedback-Ereignis, E-Mail-Tracking-Ereignis)
- Erstellen Sie CJA Workspace mit Bedienfeldern für die Kanalmischanalyse, den Angebotsleistungsvergleich und Journey-Konversionstrichter
- Erstellen von Anmerkungen für das Journey von Startdaten und wichtigen Konfigurationsänderungen

#### Dokumentation zu Experience League

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Überlegungen bei der Implementierung

Überprüfen Sie die folgenden Leitplanken, häufigen Fallstricke, Best Practices und Entscheidungen zum Kompromiss vor und während der Implementierung.

### Leitplanken und Beschränkungen

- Maximal 500 Live-Journey pro Sandbox - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Die maximale Journey-Dauer beträgt 91 Tage (globale Zeitüberschreitung)
- Maximal 50 Aktivitäten pro Journey-Arbeitsfläche
- Zielgruppen-Journey lesen kann bis zu 20.000 Profile pro Sekunde verarbeiten
- Unitäre Ereignis-Journey unterstützen bis zu 5.000 Ereignisse pro Sekunde pro Sandbox
- Maximal 10.000 genehmigte personalisierte Angebote pro Sandbox
- Maximal 30 Platzierungen pro Entscheidung
- SLA: weniger als 500 ms bei P95 für Anfragen mit einem Umfang
- KI-Rangfolgemodelle erfordern mindestens 1.000 Konversionsereignisse für das Training.
- Maximal 10 Kanaloberflächen pro Kanaltyp pro Sandbox
- Warteschritte haben eine Mindestdauer von 1 Stunde für Journey, die von der Zielgruppe gelesen werden
- Die Abklingzeit für den erneuten Eintritt von Journey beträgt mindestens 5 Minuten
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Platform-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Häufige Fehler

**Entscheidung gibt immer Fallback-Angebot zurück** Überprüfen Sie, ob personalisierte Angebote innerhalb ihres Gültigkeitsdatumsbereichs genehmigt wurden (nicht im Entwurfsstatus) und ob die Eignungsregeln mit den Attributen der Zielprofile übereinstimmen. Vergewissern Sie sich, dass die Angebotsbegrenzungen nicht erreicht wurden. Testen Sie mit einem Profil, das sich eindeutig für ein personalisiertes Angebot qualifizieren sollte.

**Journey veröffentlicht, es werden aber keine Profile eingegeben:** Bestätigen Sie für Journey, die die Zielgruppe lesen, dass die ausgewertete Population größer als null ist. Überprüfen Sie für ereignisausgelöste Journey das Ereignisschema, die Auslösebedingungen und das Senden von Ereignissen. Vergewissern Sie sich, dass die Einstiegszielgruppen-Zusammenführungsrichtlinie mit der erwarteten Zusammenführungsrichtlinie der Journey übereinstimmt.

**Rangfolgenformel wird nicht korrekt angewendet** Überprüfen Sie, ob die Formelsyntax gültig ist und auf barrierefreie Profilattribute verweist. Formelfehler werden ohne Warnung im Hintergrund auf das prioritätsbasierte Ranking zurückgesetzt. Testen Sie das Ranking mit Profilen mit unterschiedlichen Attributwerten, um zu bestätigen, dass die Formel die erwartete Reihenfolge erzeugt.

**Das Kanal-Routing ignoriert das Einverständnis:** Bedingungsknoten für die Kanalauswahl müssen Einverständnisprüfungen enthalten. Ein Profil ohne SMS-Zustimmung darf nicht an den SMS-Pfad weitergeleitet werden. Bauen Sie das Einverständnis in Eignungsregeln auf, wenn Sie die Entscheidungsfindung für die Kanalauswahl verwenden (Option B/C).

**Verzögerung der Angebotsbegrenzungszähler bei hohem Durchsatz:** Angebotsbegrenzungszähler können in Szenarien mit hohem Durchsatz eine Verzögerung von einigen Sekunden haben. Wenn eine exakte Begrenzung wichtig ist, verwenden Sie globale Begrenzungen mit einem Puffer oder kombinieren Sie sie mit Häufigkeitsregeln.

**Die Journey-Arbeitsfläche überschreitet das Limit von 50 Aktivitäten:** Komplexe Option-C-Journey mit vielen Kanalverzweigungen und Entscheidungsknoten können sich dem Limit von 50 Aktivitäten nähern. Vereinfachen Sie durch die Konsolidierung der Bedingungslogik, die Reduzierung der Anzahl der Touchpoints oder die Aufteilung in mehrere sequenzielle Journey.

**Edge-Entscheidungen geben eine leere Personalisierung zurück:** Wenn Sie Edge Decisioning für Echtzeit-Entscheidungen verwenden, stellen Sie sicher, dass für den Datenstrom der [!DNL Adobe Journey Optimizer] Service aktiviert ist und dass der Entscheidungsumfang korrekt formatiert ist. Edge-Entscheidungen sind auf Profilattribute beschränkt, die im Edge-Profilspeicher verfügbar sind.

### Best Practices

**Einfach beginnen und weiterentwickeln:** Beginnen Sie mit Option A (fester Kanal, dynamische Angebote), um das Entscheidungs-Framework zu validieren, und entwickeln Sie sich dann zu Option B oder C, wenn Ihre Datenreife und Ihre organisatorischen Kapazitäten zunehmen.

**In Profilanreicherung investieren:** Berechnete Attribute wie Interaktionswerte, Kanalpräferenzindizes und Tendenzwerte von Kunden-KI verbessern die Entscheidungsqualität erheblich. Erstellen Sie diese Anreicherungsattribute, bevor Sie komplexe Rangfolgestrategien konfigurieren.

**Fallback-Angebote immer konfigurieren:** Jede Entscheidungsrichtlinie muss ein Fallback-Angebot haben. Fallback-Angebote als wirklich wertvolle Inhalte (nicht als leere Platzhalter) gestalten, da sie Profile bereitstellen, die sich für kein personalisiertes Angebot qualifizieren.

**Testen mit verschiedenen Profilen:** Verwenden Sie den Testmodus mit Profilen, die verschiedene Eignungspfade, Kanalvoreinstellungen und Attributkombinationen darstellen. Überprüfen Sie vor der Veröffentlichung, ob alle möglichen Journey-Pfade und Entscheidungsergebnisse korrekt funktionieren.

**Fallback-Raten als Konsistenzmetrik überwachen:** Eine hohe Fallback-Angebotsrate zeigt an, dass die Eignungsregeln zu restriktiv sind oder der Angebotskatalog nicht genügend Profilsegmente abdeckt. Für eine gut konfigurierte Entscheidungsfindung sollte eine Fallback-Rate von unter 20 % angestrebt werden.

**Verwenden von Inhaltsfragmenten für Cross-Channel-Konsistenz:** Erstellen Sie freigegebene Inhaltsfragmente (Kopfzeilen, Fußzeilen, Haftungsausschlüsse, Abmeldeblöcke), um die Markenkonsistenz über E-Mail-, SMS- und Push-Nachrichten innerhalb des Journey aufrechtzuerhalten.

**Ausstiegskriterien proaktiv konfigurieren:** Definieren Sie Ausstiegskriterien für Konversionsereignisse (z. B. Kauf, Registrierung), sodass Profile, die die gewünschte Aktion ausführen, sofort vom Journey entfernt werden, anstatt weiterhin Nachrichten zu erhalten.

**Aussagekräftige Prioritätswerte zuweisen:** Wenn Sie mehrere Journey und Kampagnen ausführen, können Sie Prioritätswerte auf der Grundlage der Geschäftsauswirkungen zuweisen. Journey mit hohem Wertanteil sollten eine höhere Priorität haben als Informationskommunikation.

### Entscheidungen über Kompromisse

Überprüfen Sie die folgenden Kompromisse, um Ihre Implementierungsoptionen zu beeinflussen.

#### Komplexität der Entscheidungsfindung vs. Markteinführungszeit

Komplexere Entscheidungsfindung (Option C mit KI-Rangfolge) bietet eine höhere Personalisierung, erfordert jedoch deutlich mehr Konfiguration, Datenvorbereitung und Testzeit.

- **Option A/B-Vorteile:** Schnellere Bereitstellung, einfachere Tests, geringerer laufender Management-Overhead
- **Option C bevorzugt:** Maximale Personalisierung, kontinuierliche KI-gesteuerte Optimierung, höchstes Interaktionspotenzial
- **Empfehlung:** Sie beim ersten Start mit Option A oder B an. Erfassen Sie Leistungsdaten und erstellen Sie parallel Profilattribute für die Anreicherung. Wechseln Sie zu Option C, wenn Sie über mindestens 1.000 Konversionsereignisse für KI-Ranking-Schulungen und einen gut gefüllten Angebotskatalog verfügen.

#### Statische Verzweigung vs. Entscheidungsfindung für die Kanalauswahl

Die Kanalauswahl kann über einfache Journey-Bedingungsknoten (die Profilattribute direkt auswerten) oder über das Entscheidungs-Framework (bei dem Kanäle als Entscheidungselemente mit Eignung und Rangfolge modelliert werden) implementiert werden.

- **Statische Bedingungsknoten bevorzugen:** Einfachheit, Transparenz, einfache Fehlerbehebung. Am besten, wenn die Logik der Kanalauswahl einfach ist (z. B. „Wenn ein Push-Token vorhanden ist und der letzte Push innerhalb von 30 Tagen geöffnet wurde, verwenden Sie Push; andernfalls E-Mail„).
- **Entscheidungsbasierte Kanalauswahl begünstigt:** Zentralisierte Verwaltung, KI-Optimierungspotenzial, Möglichkeit, die Rangfolgelogik ohne Änderung der Journey-Arbeitsfläche weiterzuentwickeln. Am besten, wenn die Kanalauswahl komplex ist und sich im Laufe der Zeit verbessern sollte.
- **Empfehlung:** Verwenden Sie statische Bedingungsknoten für Option B, wenn die Kanalauswahlkriterien einfach und klar definiert sind. Verwenden Sie die entscheidungsbasierte Kanalauswahl, wenn Sie möchten, dass KI die Kanalauswahl im Laufe der Zeit optimiert oder wenn die Kanalauswahllogik komplex genug ist, um von einer zentralisierten Eignungs- und Ranking-Verwaltung zu profitieren.

#### Angebotsgranularität und Katalog-Verwaltbarkeit im Vergleich

Ein großer, granularer Angebotskatalog mit vielen zielgerichteten Angeboten erzeugt eine präzisere Personalisierung, erfordert jedoch einen höheren Verwaltungsaufwand. Ein kleinerer Katalog mit einer breiteren Eignung ist einfacher zu verwalten, aber weniger personalisiert.

- **Großer Katalog (viele spezifische Angebote) bevorzugt:** Höhere Personalisierungsgenauigkeit, relevantere Auswahl für unterschiedliche Zielgruppen, niedrigere Ausweichraten
- **Kleiner Katalog (weniger umfangreiche Angebote) bevorzugt:** Verwaltung, schnellere Einrichtung, einfachere Tests, geringeres Risiko verwaister Angebote
- **Empfehlung:** Beginnen Sie mit 5 bis 15 personalisierten Angeboten plus einem Fallback pro Entscheidung. Fügen Sie weitere Angebote hinzu, um zu sehen, welche Segmente am häufigsten Fallback-Angebote erhalten. Verwenden Sie Sammlungsqualifizierer, um Angebote nach Kategorie, Ebene oder Produktlinie zu organisieren und so ein überschaubares Wachstum zu erzielen.

#### Prioritätsbasierte vs. KI-Rangfolgenentscheidung

Die prioritätsbasierte Rangfolge ist deterministisch und transparent. Die KI-bewertete Entscheidungsfindung wird automatisch optimiert, erfordert jedoch Schulungsdaten und ist weniger transparent.

- **Prioritätsbasierte Rangfolge begünstigt:** Vorhersehbarkeit, Transparenz, sofortige Bereitstellung, keine Schulungsdaten erforderlich
- **KI-bewertete Entscheidungsfavoriten:** Kontinuierliche Optimierung, datengesteuerte Auswahl, Möglichkeit, nicht offensichtliche Angebotsprofil-Affinitäten zu erkennen
- **Empfehlung** Verwenden Sie für die erstmalige Bereitstellung die prioritätsbasierte oder die formularbasierte Rangfolge. Wechseln Sie zu einer Entscheidungsfindung mit KI-Rang, sobald Sie mindestens 1.000 Konversionsereignisse gesammelt haben und von der regelbasierten zur modellbasierten Optimierung wechseln möchten.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

### Journey-Orchestrierung

- [Erste Schritte mit Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Erstellen einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journey-Eigenschaften](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Aktivität „Zielgruppe lesen“](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Allgemeine Ereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Zielgruppen-Qualifizierungsereignisse](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Bedingungsaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Warteaktivität](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Hinzufügen einer Nachricht zu einer Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Ausstiegskriterien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Journey-Eingabeverwaltung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Journeys testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [Journey veröffentlichen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Delegieren von Subdomains](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Erstellen von IP-Pools](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-Aufwärmpläne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [E-Mail-Oberflächeneinstellungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Konfigurieren des Push-Benachrichtigungskanals](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Verfassen und Personalisieren von Nachrichten

- [Erstellen einer E-Mail](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Entwerfen von E-Mail-Inhalten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Anzeigen einer Vorschau und Testen der Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Konflikt-, Prioritäts- und Frequenzverwaltung

- [Übersicht über Konflikt- und Prioritätsmanagement](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioritätswerte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Identifizieren potenzieller Konflikte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Journey-Begrenzung und Schlichtung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Häufigkeitsregeln](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Zielgruppen und Segmentierung

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Audience-Komposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Reporting und Analysen

- [Journey-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Globaler Journey-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profil und Identität

- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Kunden-KI - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Einverständnis in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Verwalten der Unterdrückungsliste](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Leitlinien

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
