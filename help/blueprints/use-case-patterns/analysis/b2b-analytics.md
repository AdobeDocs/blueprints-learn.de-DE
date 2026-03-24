---
title: B2B-Analyse
description: Erfahren Sie, wie Sie Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden einbeziehen.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 1%

---

# B2B-Analyse

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für B2B-Analysen auf Kontoebene mit [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition und [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden integrieren müssen.

Es behandelt alle praktikablen Ansätze für eine Account-orientierte Analyse, von flachen Account-Strukturen bis hin zu komplexen globalen Account-Hierarchien, mit Hinweisen dazu, wann jede Option zu wählen ist. Der Plan behandelt B2B-Datenverbindungen, die Konfiguration der Kontodatenansicht, die Workspace-Analyse und die Veröffentlichung von Dashboards.

B2B Analytics erweitert die standardmäßigen [!DNL CJA] mit Account-basierten Verbindungen, B2B-spezifischen Containern (Account, Global Account, Opportunity, Buying Group) und Reporting auf Kontoebene. Diese Funktion ermöglicht es Unternehmen, Marketing- und Vertriebsaktivitäten auf Kontoebene zu analysieren, den Verlauf von Opportunitys zu verfolgen, die Vollständigkeit von Käufen zu messen und den Umsatz Marketing-Touchpoints über erweiterte B2B-Verkaufszyklen hinweg zuzuordnen.

## Anwendungsfall - Übersicht

B2B-Organisationen stehen vor einer grundlegenden Herausforderung im Bereich der Analyse: Ihre Kunden sind keine Einzelpersonen, sondern Konten, die aus mehreren Stakeholdern, Einkaufsgruppen und Opportunities bestehen. Personenbasierte Standardanalysen können keine Fragen beantworten wie: „Welche Accounts sind am meisten involviert?“, „Wie vollständig sind unsere Einkaufsgruppen?“ oder „Welche Marketing-Touchpoints fördern den Fortschritt von Opportunities?“

B2B-Analytics adressiert dies, indem [!DNL CJA] B2B edition genutzt wird, um Account-orientierte analytische Ansichten zu erstellen, die Verhaltensdaten auf Personenebene mit Account-, Opportunity- und Einkaufsgruppendimensionen kombinieren. [!DNL RT-CDP] B2B edition bietet die zugrunde liegende Kontoprofilvereinheitlichung und B2B-Identitätsauflösung, die die Analytics-Ebene befüllt. Gemeinsam ermöglichen diese Lösungen es Unternehmen, eine kanalübergreifende Journey-Analyse auf Kontoebene zu erstellen, die Marketing-Interaktion mit dem Pipeline-Fortschritt in Beziehung zu setzen und umsetzbare Einblicke sowohl für Marketing- als auch für Vertriebsteams bereitzustellen.

Die Zielgruppe umfasst B2B-Marketing-Operations-Teams, Leiter der Nachfragegenerierung, Analysten für Umsatzvorgänge und Vertriebsleiter, die Einblicke in die Interaktion auf Account-Ebene und den Pipeline-Status benötigen.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Analyse und Reporting verbessern

Verbessern Sie die Reporting-Funktionen für schnellere, umsetzbarere Marketing-Einblicke durch einheitliche Dashboards und Self-Service-Tools. B2B-Analytics ermöglicht es Unternehmen, Interaktionsdaten auf Kontoebene aus verschiedenen Quellen in einer einzigen Analyseumgebung zu konsolidieren, wodurch eine kanalübergreifende Sichtbarkeit der Auswirkungen von Marketing-Programmen auf Pipeline und Umsatz bereitgestellt wird.

**KPIs:**, Produktivität

[Erfahren Sie mehr über die Verbesserung von Analysen und Berichten](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Datengestützte Entscheidungsfindung ermöglichen

Ermöglichen Sie Teams durch Self-Service-Analysen, Echtzeit-Kundeneinblicke und KI-gestützte Prognosen eine Strategie. Analyse auf Kontoebene stattet Marketing- und Vertriebsteams mit den Daten aus, die für die Priorisierung von Accounts, die Optimierung von Interaktionsstrategien und die Abstimmung von Pipeline-Opportunitys erforderlich sind.

**KPIs:**, Produktivität

[Erfahren Sie mehr über die Aktivierung datengesteuerter Entscheidungsfindung](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Verbessern der Lead-Qualifizierung und -Konversion

Erhöhen Sie die Lead-Qualität und beschleunigen Sie den Pipeline-Fortschritt durch Bewertung, Pflege und personalisierte Nachverfolgung. CJA B2B edition bietet erweiterte 13-monatige Account-Lookback-Fenster, die speziell für B2B-Verkaufszyklen entwickelt wurden und eine genaue Multi-Touch-Attribution auf der gesamten Account-Journey ermöglichen.

**KPIs:**, inkrementeller Umsatz

[Erfahren Sie mehr über die Verbesserung der Lead-Qualifizierung und -Konversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Beispiele für taktische Anwendungsfälle

Die folgenden Szenarien veranschaulichen, wie dieses Muster in der Praxis angewendet werden kann.

- **Analyse der Kontointeraktionsbewertung** - Messen und reihen Sie Konten nach ihrer aggregierten Interaktion über Web-, E-Mail-, Ereignis- und Inhaltsinteraktionen, um Konten zu identifizieren, die eine hohe Absicht für die Vertriebsnachverfolgung verfolgen
- **Tracking der Vollständigkeit der Einkaufsgruppe** — Analysieren Sie die Zusammensetzung der Einkaufsgruppe in allen Konten, um Lücken in der Rollenabdeckung zu identifizieren und die Lead-Akquise für unvollständige Einkaufsgruppen zu priorisieren.
- **Opportunity-Pipeline-Korrelation** - Korrelieren Sie Daten zu Marketing-Interaktionen mit dem Fortschritt der Opportunity-Phase, um zu verstehen, welche Kampagnen und Touchpoints für den Fortschritt der Pipeline verantwortlich sind.
- **Multi-Touch B2B-Attribution** - Wenden Sie Attributionsmodelle mit 13-monatigen Lookback-Fenstern an, um Marketing-Touchpoints auf der gesamten B2B-Kauf-Journey vom Erstkontakt bis zum abgeschlossenen Kauf zu gutschreiben.
- **Account-Journey-Zuordnung** - Visualisieren Sie die Cross-Channel-Account-Journey von der anfänglichen Wahrnehmung bis zur Erstellung und Schließung von Opportunities und identifizieren Sie gemeinsame Pfade und Reibungspunkte
- **Kampagneneinfluss auf Pipeline** - Messen Sie, wie bestimmte Kampagnen die Erstellung der Konto-Pipeline, die Weiterentwicklung der Chancen und die Umsatzgenerierung beeinflussen
- **Progression der Kaufgruppeninteraktion** - Verfolgen Sie, wie sich die Werte für die Kaufgruppeninteraktion im Laufe der Zeit entwickeln, und korrelieren Sie Interaktionsschwellen mit Opportunity-Ergebnissen
- **Account-basierte Content-Performance** - Analysieren Sie, welche Content-Assets und Themen mit bestimmten Account-Segmenten, Branchen oder Käufergruppen-Rollen in Einklang stehen.
- **Alignment-Dashboards für Vertrieb und Marketing** - Erstellen Sie gemeinsam genutzte Dashboards, die Marketing- und Vertriebsteams eine einheitliche Sicht auf Kundeninteraktion, Pipeline-Status und Umsatzzuordnung bieten
- **Kontosegmentierung für die Aktivierung** - Erstellen Sie B2B-Segmente auf der Grundlage von Analysen auf Kontoebene (z. B. „hochgradig interaktive Konten ohne offene Möglichkeiten„) und veröffentlichen Sie sie zur nachgelagerten Aktivierung

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Kontointeraktionswert | Interaktionsmetrik für alle Kontakte innerhalb eines Kontos aggregieren | Berechnete Metrik mit Kombination von Web-Besuchen, E-Mail-Interaktionen, Ereignisteilnahme und Inhalts-Downloads auf Kontoebene |
| Vollständigkeit der Einkaufsgruppe | Prozentsatz der erforderlichen Aufgabengebiete innerhalb einer Einkaufsgruppe | Verhältnis der ausgefüllten Rollen zu den insgesamt erforderlichen Rollen pro Einkaufsgruppe, im Zeitverlauf verfolgt |
| Von Marketing beeinflusste Pipeline | Umsatz in Pipeline, der von Marketing-Aktivitäten berührt wurde | Opportunity-Wert, bei dem die zugehörigen Account-Kontakte innerhalb des Attributionsfensters Marketing-Touchpoints haben |
| Konversionsrate Konto-zu-Opportunity | Prozentsatz der engagierten Konten, die qualifizierte Opportunitys generieren | Konten mit Opportunities dividiert durch die Gesamtzahl der engagierten Konten über einen definierten Zeitraum |
| Durchschnittliche Dauer des Abschlusszyklus | Zeit vom ersten Marketing-Touch bis zum abgeschlossenen Abschluss | Durchschnittliche Dauer vom ersten zugewiesenen Touchpoint bis zum Opportunity-Abschlussdatum |
| Marketing Attribution-Umsatz | Den Marketing-Touchpoints zugeschriebener Umsatz | Umsatz aus abgeschlossenen Vertriebschancen mit Marketing-Kontakten, verteilt nach Attributionsmodell |
| Kontoreichweite und -durchdringung | Anzahl der Kontakte, die pro Zielkonto interagiert haben | Eindeutige Kontakte mit Marketing-Interaktionen pro Konto im Vergleich zu den insgesamt bekannten Kontakten |
| Inhaltsinteraktion nach Kaufrolle | Interaktionsmetriken, nach Kaufgruppenrolle segmentiert | Seitenansichten, Downloads und Besuchszeit nach Persona/Rolle in Einkaufsgruppen |

## Anwendungsfallmuster

**B2B-Analyse**

Binden Sie Informationen auf B2B-Kontoebene in die kanalübergreifende Analyse von Kunden-Journey ein.

**Funktionskette:** B2B-Datenverbindung > Konfiguration der Kontodatenansicht > Workspace Analysis > Dashboard-Veröffentlichung

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Customer Journey Analytics]B2B edition** - Bietet Account-basierte Verbindungen, B2B-spezifische Datenansichts-Container, Workspace-Analysen auf Kontoebene, Einkaufsgruppenanalysen, Opportunity-Analysen, B2B-Segmentierung und B2B-Attribution mit erweiterten Lookback-Fenstern
- **[!DNL Real-Time CDP]B2B edition** - Bietet die B2B-Datengrundlage einschließlich der Vereinheitlichung von Account-Profilen, B2B-Identitätsauflösung, B2B-Schemaklassen (Account, Opportunity, Buying Group) und [!DNL Marketo Engage] Integration für die Aufnahme von B2B-Interaktionsdaten

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Sandbox mit [!DNL CJA] Berechtigungen für B2B edition und [!DNL RT-CDP] B2B edition konfiguriert. Rollen, die für Dateningenieure, Analysten und Marketing-Operations-Benutzende mit Zugriff auf [!DNL CJA] und das B2B-Datenmodell bereitgestellt wurden. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | B2B-XDM-Schemata, die mithilfe von B2B-Klassen konfiguriert wurden: XDM Business Account, XDM Business Opportunity, XDM Business Account Person Relation, XDM Business Opportunity Person Relation und XDM Business Marketing List Members. Es müssen Feldergruppen für Kontoattribute, Opportunity-Stadien und Einkaufsgruppenrollen definiert werden. Für Profil erstellte und aktivierte Datensätze. | [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [B2B edition-Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Datenquellen und Sammlung | Erforderlich | B2B-Datenquellen verbunden, normalerweise über den [!DNL Marketo Engage]-Quell-Connector oder [!DNL Salesforce] CRM-Quell-Connector. Account-Datensätze, Opportunity-Datensätze, Personen-Account-Beziehungen und verhaltensbezogene Interaktionsereignisse müssen in AEP-Datensätze fließen. [!DNL Web SDK] Oder [!DNL Marketo] Integration muss Verhaltensereignisse mit Kontoverknüpfung erfassen. | [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [Marketo Engage-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identitäts- und Profilkonfiguration | Erforderlich | B2B-Identitätsauflösung, die zum Auflösen von Personen-Konto-Beziehungen konfiguriert ist. Konto-ID, Personen-ID ([!DNL Marketo] Lead-ID oder CRM-Kontakt-ID) und geräteübergreifende Identitäten (ECID, E-Mail) müssen verknüpft sein. Das Identitätsdiagramm muss die Viele-zu-viele-Personen-zu-Konto-Zuordnung unterstützen, die bei B2B-Datenmodellen inhärent ist. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [B2B-Identitätsauflösung](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Zielgruppendefinition und Segmentierung | Angenommen an Ort und Stelle | Zielgruppendefinitionen auf Kontoebene sollten verfügbar sein, wenn B2B-Segmente von [!DNL CJA] zur Aktivierung wieder in AEP veröffentlicht werden. Für Anwendungsfälle, die nur Analytics betreffen, ist dies keine strikte Voraussetzung, wird aber für die segmentbasierte Analyse empfohlen. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute aus Account-Profilen (z. B. Gesamt-Interaktionswert, Tage seit der letzten Aktivität, Anzahl der Opportunities) ergänzen die in [!DNL CJA] verfügbaren analytischen Dimensionen für die Analyse auf Account-Ebene. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | B2B-Datensätze, insbesondere Verhaltensereignisdaten aus [!DNL Marketo Engage], können schnell wachsen. Richtlinien zur Gültigkeit von Datensätzen helfen beim Management von Speicher und stellen die Einhaltung von Datenspeicherungsanforderungen sicher. | [Erweitertes Daten-Lifecycle-Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | B2B-Daten enthalten häufig sensible Geschäftsinformationen (Vertragswerte, Wettbewerbsdaten). Datennutzungskennzeichnungen und Governance-Richtlinien stellen sicher, dass diese Daten in allen Analyse- und Aktivierungs-Workflows angemessen verwendet werden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | B2B-Quell-Connectoren ([!DNL Marketo], [!DNL Salesforce]) erfordern eine Überwachung hinsichtlich des Aufnahmestatus. Die Überwachung des Verbindungszustands in [!DNL CJA] stellt die Datenfrische für Analysen sicher. Warnhinweisregeln für Aufnahmefehler verhindern veraltete Dashboards. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Dieses Muster ist selbst ein Analysemuster. Diese Funktion ist von Natur aus enthalten, da die Kette der Kernfunktionen Reporting- und Analysefunktionen bietet. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Customer Journey Analytics] B2B edition

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kontobasierte Verbindung | Phase 1: B2B-Datenverbindung | Konfigurieren Sie Verbindungen mithilfe des Kontos oder des globalen Kontos als primäre Kennung für die Analyse auf Unternehmensebene |
| Konfiguration der B2B-Datenansicht | Phase 2: Konfiguration der Kontodatenansicht | Datenansichten mit B2B-spezifischen Containern (Konto, globales Konto, Opportunity, Einkaufsgruppe) neben standardmäßigen Containern für Personen, Sitzungen und Ereignisse definieren |
| Workspace-Analyse auf Kontoebene | Phase 3: Workspace-Analyse | Erstellen Sie eine Freiformanalyse mithilfe von Dimensionen, Metriken und B2B-Containern auf Kontoebene für Journey-Insights auf Unternehmensebene |
| Einkaufsgruppenanalyse | Phase 3: Workspace-Analyse | Analyse der Zusammensetzung, Interaktion und Progression der Einkaufsgruppe durch den Kaufentscheidungsprozess |
| Opportunity-Analyse | Phase 3: Workspace-Analyse | Opportunity-Fortschritt über Vertriebs-funnel-Stadien verfolgen und mit Daten zur Marketing-Interaktion korrelieren |
| B2B-Segmentierung | Phase 3: Workspace-Analyse | Erstellen von Segmenten mit B2B-Containern für die gefilterte Analyse auf Kontoebene |
| B2B-Attribution | Phase 3: Workspace-Analyse | Anwenden von Attributionsmodellen mit erweiterten 13-monatigen Account-Lookback-Fenstern für die B2B-Verkaufszyklusanalyse |
| Erstellung berechneter Metriken | Phase 3: Workspace-Analyse | Definieren Sie berechnete Metriken für B2B-KPIs wie die Kontointeraktionsrate, die Vollständigkeit der Einkaufsgruppe und den Pipeline-Einfluss |
| Dashboard- und Scorecard-Veröffentlichung | Phase 4: Dashboard-Veröffentlichung | Erstellen und Freigeben von Dashboards und mobilen Scorecards für Marketing- und Vertriebsleiter |
| Zielgruppenveröffentlichung | Phase 4: Dashboard-Veröffentlichung | [!DNL CJA] kontobasierte Zielgruppen zur nachgelagerten Aktivierung wieder in AEP veröffentlichen |

### [!DNL Customer Journey Analytics] — Standardfunktionen

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Datenverbindung | Phase 1: B2B-Datenverbindung | Binden von AEP B2B-Datensätzen an [!DNL CJA] für Cross-Channel-Analysen |
| Konfiguration der Datenansicht | Phase 2: Konfiguration der Kontodatenansicht | Konfigurieren von Standarddimensionen, Metriken, Attributionen und Persistenzeinstellungen in der B2B-Datenansicht |
| Workspace-Analyse | Phase 3: Workspace-Analyse | Erstellen einer Freiformanalyse mit Tabellen, Fallout, Fluss-, Kohorten- und Attributionsvisualisierungen |
| Angeleitete Analyse | Phase 3: Workspace-Analyse | Verwenden geführter Workflows für funnel-, Trend- und Bindungsanalysen auf Kontoebene |

### [!DNL Real-Time CDP] B2B edition

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kontoprofil-Vereinheitlichung | Voraussetzung (F2/F4) | Konsolidierung quellenübergreifender B2B-Daten in einheitlichen Account-Profilen mithilfe spezialisierter XDM-B2B-Schemaklassen |
| B2B-Identitätsauflösung | Voraussetzung (F4) | Auflösen von Personen-zu-Konto-Beziehungen, die mehrstufige Account-Hierarchien und Viele-zu-Viele-Zuordnungen unterstützen |
| [!DNL Marketo Engage] Integration | Voraussetzung (F3) | Aufnehmen von Verhaltensdaten und Konto-/Lead-Datensätzen aus [!DNL Marketo Engage] über native B2B-Quell-Connectoren |

## Voraussetzungen

Die folgenden Elemente müssen vor Beginn der Implementierung vorhanden sein.

- [ ] [!DNL CJA] B2B edition-Lizenz ist aktiv und für das Unternehmen bereitgestellt
- [ ] [!DNL RT-CDP] B2B edition-Lizenz ist aktiv, wenn B2B-Schemata und Kontoprofile konfiguriert sind
- [ ] B2B-XDM-Schemata werden definiert (Konto, Opportunity, Konto-Personen-Beziehung, Opportunity-Personen-Beziehung, Marketing-Listenmitglieder)
- [ ] Quell-Connectoren für [!DNL Marketo Engage] und/oder CRM sind konfiguriert und nehmen aktiv Daten auf
- [ ] verhaltensbezogene Ereignisdaten auf Kontoebene (Web-Besuche, E-Mail-Interaktionen, Formularübermittlungen) fließen mit Kontoverknüpfung in AEP
- [ ] Personen-Konto-Beziehungen werden im Identitätsdiagramm erstellt
- [ ] Mindestens 30 Tage an historischen B2B-Interaktionsdaten stehen für aussagekräftige Analysen zur Verfügung
- [ ] Stakeholder haben sich auf die Rollendefinitionen für die Einkaufsgruppe und die Zuweisung von Lösungsinteressen geeinigt
- [ ] [!DNL CJA] Benutzerkonten werden mit entsprechenden Produktprofilen für B2B edition-Funktionen bereitgestellt
- [ ] Target-KPIs und Reporting-Anforderungen wurden von der Marketing- und Vertriebsleitung definiert

## Implementierungsoptionen

In den folgenden Abschnitten werden verschiedene Ansätze zur Implementierung dieses Anwendungsfallmusters beschrieben.

### Option A: Kontoorientierte Analyse

**Am besten geeignet für** Organisationen, die alle Interaktions- und Pipeline-Daten über die Linse des Kontos analysieren möchten. Bei diesem Ansatz wird der Konto-Container als primäre Analyseeinheit verwendet, die eine Ansicht von oben nach unten bietet, wie Konten durch den Kauf von Journey fortschreiten.

**Funktionsweise:**

Konfigurieren Sie eine [!DNL CJA] B2B-Verbindung mit Konto als primärer Kennung. Alle Verhaltensereignisse, Opportunities und Einkaufsgruppendaten werden auf Kontoebene aggregiert. Die Datenansicht verwendet das Konto als Container der höchsten Ebene, in dem Person, Sitzung und Ereignis verschachtelt sind. Dies ermöglicht Analysen wie „Wie viele Konten haben die Preisfindungsseite besucht und dann innerhalb von 30 Tagen eine Opportunity erstellt?“

Account-zentrierte Analysen bieten die natürlichste Ansicht für B2B-Organisationen, bei denen das Konto die Kaufeinheit ist. Dimensionen wie Branche, Unternehmensgröße, Kontoebene und Kontoinhaber können verwendet werden, um Interaktionsmuster und Pipeline-Metriken aufzuschlüsseln. Die Attribution wird auf Kontoebene mit 13-monatigen Lookback-Fenstern angewendet, die lange B2B-Verkaufszyklen berücksichtigen.

**Wichtige Aspekte:**

- Sauberes Konto-zu-Person-Mapping im Identitätsdiagramm erforderlich
- Alle Ereignisse auf Personenebene müssen einem Konto zugeordnet werden können
- Anonymer Web-Traffic, der keinem Konto zugeordnet werden kann, wird nicht in der Analyse auf Kontoebene angezeigt

**Vorteile:**

- Bietet eine echte Ansicht des gesamten kaufenden Journey auf Kontoebene
- Ermöglicht eine kontobasierte Attribution, die der Art und Weise entspricht, wie B2B-Umsätze generiert werden
- Unterstützt die Einkaufsgruppen- und Opportunity-Analyse als verschachtelte Container innerhalb des Kontos
- Abstimmung der Analyse mit der ABM-Strategie (Account-Based Marketing)

**Einschränkungen:**

- Robuste Identitätsauflösung von Person zu Konto erforderlich
- Anonyme oder nicht übereinstimmende Interaktionsdaten sind von der Analyse ausgeschlossen
- Komplexer zu konfigurieren als personenorientierte Analyse

**Experience League:**

- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [B2B edition-Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)

### Option B: Globale kontoorientierte Analyse

**Am besten geeignet für:** Unternehmen mit komplexen Account-Hierarchien, bei denen eine übergeordnete Firma mehrere Tochterkonten hat. Bei diesem Ansatz wird das globale Konto als primäre Kennung verwendet, wodurch alle Aktivitäten des untergeordneten Kontos auf die Ebene der übergeordneten Organisation aggregiert werden.

**Funktionsweise:**

Konfigurieren Sie die [!DNL CJA] B2B-Verbindung mit dem globalen Konto als primäre Kennung anstelle des Kontos. Dadurch werden Interaktionsdaten aus allen untergeordneten Konten ihrer übergeordneten Organisation aggregiert. Wenn beispielsweise „Acme Corp“ regionale Tochtergesellschaften „Acme EMEA“ und „Acme APAC“ hat, fasst eine globale Kontoverbindung alle Interaktionen aller drei Entitäten in einer einzigen Analyseansicht zusammen.

Die Datenansicht enthält ein globales Konto als Container der obersten Ebene, mit Konto, Person, Sitzung und Ereignis als verschachtelte Container. Dies ermöglicht die Analyse sowohl auf globaler als auch auf untergeordneter Kontoebene innerhalb desselben Workspace-Projekts. Attributions-Lookback-Fenster werden auf globaler Kontoebene angewendet und erfassen alle Touchpoints in der gesamten Unternehmenshierarchie.

**Wichtige Aspekte:**

- Erfordert Account-Hierarchie-Daten mit im B2B-Datenmodell definierten hierarchischen Beziehungen
- Globale Konto-ID muss für alle Kontodatensätze ausgefüllt und korrekt sein
- Untergeordnete Konten müssen ihrem übergeordneten Konto korrekt zugeordnet werden

**Vorteile:**

- Bietet konsolidierte Sichtbarkeit über komplexe Unternehmenskontostrukturen hinweg
- Verhindert fragmentierte Analysen, wenn ein einzelner Unternehmenskunde über mehrere Kontodatensätze verfügt
- Ermöglicht den Vergleich zwischen regionalen Niederlassungen innerhalb eines einzigen globalen Kontos
- Unterstützt Pipeline- und Umsatzberichte auf Unternehmensebene

**Einschränkungen:**

- Erfordert genaue Account-Hierarchie-Daten, die viele Unternehmen nur schwer pflegen können
- Kann Muster auf untergeordneter Ebene verdecken, wenn sie nur auf globaler Ebene angezeigt werden
- Zusätzlicher Aufwand für die Datenmodellierung zum Erstellen und Verwalten von Hierarchiebeziehungen

**Experience League:**

- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Option C: Hybride Person + Kontoanalyse

**Am besten geeignet für:** Organisationen, die von der personenbasierten Analyse zur kontobasierten Analyse wechseln oder die sowohl Ansichten auf Personen- als auch Kontoebene benötigen. Dieser Ansatz erstellt zwei Datenansichten aus derselben Verbindung - eine personenorientierte und eine kontoorientierte.

**Funktionsweise:**

Konfigurieren Sie eine einzelne [!DNL CJA] B2B-Verbindung, die alle B2B-Datensätze enthält (Ereignis, Konto, Opportunity, Einkaufsgruppe, Personen-Konto-Beziehungen). Erstellen Sie dann zwei Datenansichten: eine mit Person als primären Container (ähnlich dem Standard-[!DNL CJA]) und eine mit Account als primären Container. Analysten können je nach der gestellten Frage zwischen Datenansichten wechseln.

Die personenorientierte Datenansicht bietet eine herkömmliche Journey-Analyse auf individueller Ebene (z. B. „Was ist der Konversionspfad für Leads, die zu Opportunities werden?„), während die kontoorientierte Datenansicht eine Analyse auf Unternehmensebene bietet (z. B. „Welche Konten haben die höchste Interaktions-Pipeline-Konversionsrate?„). Beide Ansichten verwenden dieselben zugrunde liegenden Daten, was die Konsistenz gewährleistet.

**Wichtige Aspekte:**

- Erfordert zwei Datenansichten mit potenziell unterschiedlichen Dimensions- und Metrikkonfigurationen
- Analysten müssen in der Verwendung der einzelnen Ansichten geschult werden
- Berechnete Metriken müssen möglicherweise für jede Datenansicht separat erstellt werden

**Vorteile:**

- Flexibilität bei der Analyse von Daten sowohl auf Personen- als auch auf Kontoebene
- Einfacherer Anpassungspfad für Teams, die sich mit Analysen auf Benutzerebene vertraut machen
- Ermöglicht den Vergleich zwischen Metriken auf Personen- und Kontoebene
- Unterstützt sowohl Lead- als auch Account-basierte Marketing-Strategien

**Einschränkungen:**

- Zwei Datenansichten, die beibehalten und synchronisiert werden sollen
- Potenzielle Verwirrung für Analysten bezüglich der zu verwendenden Ansicht
- Berechnete Metriken und Filter müssen möglicherweise über Ansichten hinweg dupliziert werden

**Experience League:**

- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

### Vergleich von Optionen

| Kriterien | Option A: Kontenorientiert | Option B: Globales Account-orientiertes | Option C: Hybride Person + Konto |
| --- | --- | --- | --- |
| Am besten geeignet für | Standard-B2B mit flacher Kontostruktur | Unternehmen mit hierarchischen Eltern-Kind-Beziehungen | Übergang von Organisationen oder doppelte Anforderungen |
| Komplexität | Mittel | Hoch | Medium-Hoch |
| Datenanforderungen | Konto-Personen-Zuordnung | Kontenhierarchie + Zuordnung | Konto-Personen-Zuordnung |
| Attributionsbereich | Kontoebene (13-monatiger Lookback) | Globale Kontoebene (13-monatiger Lookback) | Personen- und Kontoebene |
| Anonyme Daten | Aus Kontoansicht ausgeschlossen | Aus globaler Ansicht ausgeschlossen | In der Personenansicht enthalten, von der Kontoansicht ausgeschlossen |
| Erfordert | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition, Hierarchiedaten | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition |
| Wartungsaufwand | Einzelne Datenansicht | Einzelne Datenansicht | Zwei Datenansichten |

### Wählen der richtigen Option

- **Wählen Sie Option A** Wenn Ihr Unternehmen über eine flache Kontostruktur verfügt (keine hierarchischen hierarchischen Elemente über- und untergeordneten Elementen), funktioniert Ihre ABM-Strategie auf individueller Kontoebene, und Sie möchten den einfachsten Pfad zur Analyse auf Kontoebene.
- **Wählen Sie Option B**, wenn es sich bei Ihren Zielkonten um große Unternehmen mit regionenübergreifenden Tochterkonten handelt und Sie konsolidierte Berichte auf der Ebene des übergeordneten Unternehmens benötigen. Diese Option erfordert qualitativ hochwertige Kontohierarchiedaten.
- **Wählen Sie Option C** Wenn Ihr Unternehmen von Lead-basiertem zu Account-basiertem Marketing wechselt, benötigen Ihre Analysten sowohl eine Analyse des funnel auf Personenebene als auch eine Analyse des Account-Level-Engagements, oder Sie haben einen Mix aus B2B- und B2C-Geschäftsbereichen.

## Implementierungsphasen

In den folgenden Phasen wird der empfohlene Implementierungsablauf beschrieben.

### Phase 1: B2B-Datenverbindung

**Anwendungsfunktion:** [!DNL CJA] B2B: Kontobasierte Verbindung, [!DNL CJA]: Datenverbindung

Konfigurieren Sie die [!DNL CJA], die Ihre AEP B2B-Datensätze zur Analyse an [!DNL CJA] bindet. Diese Verbindung definiert, welche Datensätze in [!DNL CJA] fließen, den primären Kennungstyp (Konto oder globales Konto) und wie Verlaufs- und Streaming-Daten aufgenommen werden. Die Verbindung bildet die Grundlage für alle nachfolgenden Analysen.

#### Entscheidung: Primärer Kennungstyp

Legen Sie fest, ob die Verbindung die Konto-ID oder die globale Konto-ID als primäre Kennung verwenden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Konto-ID | Flache Kontostruktur, keine hierarchischen Elemente | Einfachere Einrichtung; jedes Konto wird unabhängig analysiert. Die häufigste Wahl für SMB-fokussierte B2B-Lösungen. |
| Globale Konto-ID | Unternehmenskonten mit untergeordneten Hierarchien | Erfordert Hierarchiedaten; aggregiert alle Tochterunternehmen unter dem übergeordneten Objekt. Optimiert für ABM-Programme von Unternehmen. |

#### Entscheidung: Datensatzauswahl und Typenbezeichnung

Legen Sie fest, welche B2B-Datensätze einbezogen werden sollen und wie sie eingegeben werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Ereignis-Datensätze (Verhalten) | Immer einschließen | Web-Interaktionen, E-Mail-Ereignisse, Formularübermittlungen, Download von Inhalten. Muss ein Zeitstempelfeld haben. Das sind die Einrücksignale. |
| Datensatz für Kontodatensätze (Profil) | Immer einschließen | Kontoattribute wie Branche, Größe, Ebene, Inhaber. Stellt den Dimensionskontext für die Kontoanalyse bereit. |
| Opportunity-Datensätze (Suche/Profil) | Für Pipeline-Analyse einschließen | Opportunity-Stadium, Wert, Abschlussdatum. Erforderlich für die Analyse der Pipeline- und Umsatzzuordnung. |
| Kaufen von Gruppendatensätzen (Lookup/Profile) | Für die Einkaufsgruppenanalyse einschließen | Gruppenrollen kaufen, Interaktionswerte, Vollständigkeit. Erforderlich für die Analyse der Einkaufsgruppenzusammensetzung. |
| Personenkonto-Beziehungs-Datensätze (Lookup) | Immer einschließen | Ordnet Personen Konten zu. Kritisch für die Verknüpfung von Ereignissen auf Personenebene mit Analysen auf Kontoebene. |
| Kampagnen-/Programmdatensätze (Lookup) | Für Attribution einschließen | Kampagnen-Metadaten, Programmtypen, Kanäle. Aktiviert die Analyse des Kampagneneinflusses. |

#### Entscheidung: Aufstockungsbereich

Legen Sie fest, wie viele historische Daten in die Verbindung importiert werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Alle vorhandenen Daten | B2B-Verkaufszyklen sind lang (6-18 Monate) und Sie benötigen eine vollständige Historie | Empfohlen für B2B. Die Aufstockung kann bei großen Datensätzen Tage dauern, liefert jedoch vollständige Attributionsdaten. |
| Benutzerdefinierter Datumsbereich (letzte 2-3 Jahre) | Die Datenqualität geht über einen bestimmten Punkt hinaus | Gleicht Vollständigkeit mit Datenqualität ab. Häufig, wenn CRM-Daten historische Inkonsistenzen aufweisen. |
| Keine Aufstockung | Nur Tests oder Entwicklung | Nur neue Daten fließen in . Nicht geeignet für B2B-Analysen in der Produktion. |

#### Konfigurieren der B2B-Datenverbindung

**UI-Navigation:** [!DNL Customer Journey Analytics] > Verbindungen > Neue Verbindung erstellen

Wichtige Konfigurationsdetails:

- AEP-Sandbox mit B2B-Datensätzen auswählen
- Durchschnittliche Anzahl der täglichen Ereignisse für die Kapazitätsplanung festlegen
- Fügen Sie jeden Datensatz hinzu und bestimmen Sie seinen Typ (Ereignis, Suche oder Profil)
- Konfigurieren Sie das Feld Personen-ID so, dass die Konto-ID oder die globale Konto-ID für B2B-Verbindungen verwendet wird
- Aktivieren des Streaming für Datensätze, für die nahezu in Echtzeit Aktualisierungen erforderlich sind
- „Alle vorhandenen Daten importieren“ für historische Aufstockung aktivieren

**Wo die Optionen unterschiedlich sind:**

**Für Option A (kontozentriert):**
Legen Sie die primäre Kennung auf Konto-ID fest. Fügen Sie Datensätze für Kontodatensätze, Opportunities, Einkaufsgruppen und Personenkonten hinzu. Konfigurieren Sie Ereignis-Datensätze auf Personenebene mit dem Feld Konto-ID für die Verbindung über Datensätze hinweg.

**Für Option B (Global Account-Centric):**
Legen Sie die primäre Kennung auf Globale Konto-ID fest. Stellen Sie sicher, dass die Kontohierarchiedaten das Feld Globale Konto-ID enthalten. Alle Datensätze müssen die globale Konto-ID enthalten oder mit ihr verknüpft sein, damit sie ordnungsgemäß aggregiert werden können.

**Für Option C (Hybrid):**
Erstellen Sie eine einzige Verbindung mit allen B2B-Datensätzen. Konto-ID als primäre Kennung verwenden. Die personenorientierte Ansicht wird in Phase 2 erstellt, indem eine andere Datenansichtskonfiguration für dieselbe Verbindung verwendet wird.

**Dokumentation zu Experience League:**

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verwalten von Verbindungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Phase 2: Konfiguration der Kontodatenansicht

**Anwendungsfunktion:** [!DNL CJA] B2B: Konfiguration der B2B-Datenansicht, [!DNL CJA]: Konfiguration der Datenansicht

Konfigurieren Sie die Datenansicht, die definiert, wie Verbindungsdaten in der Analyse angezeigt werden. Bei B2B-Analysen umfasst dies die Konfiguration von B2B-spezifischen Containern (Konto, Opportunity, Einkaufsgruppe), die Zuordnung von B2B-Schemafeldern zu Dimensionen und Metriken, das Festlegen von Attributionsmodellen mit B2B-geeigneten Lookback-Fenstern und die Erstellung abgeleiteter Felder für B2B-Geschäftslogik.

#### Entscheidung: Container-Konfiguration

Legen Sie fest, welche B2B-Container aktiviert und wie sie benannt werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Konto + Person + Sitzung + Ereignis | Standard-B2B ohne Einkaufsgruppen- oder Opportunity-Analyse | Einfachste B2B-Container-Hierarchie. Konto ist der Container der obersten Ebene. |
| Konto + Opportunity + Person + Sitzung + Ereignis | Pipeline- und Umsatzanalyse erforderlich | Fügt Opportunity als Container-Ebene hinzu, was die Analyse auf Opportunity-Ebene ermöglicht. |
| Konto + Einkaufsgruppe + Opportunity + Person + Sitzung + Ereignis | Vollständige B2B-Analyse einschließlich der Zusammensetzung der Einkaufsgruppe | Am umfassendsten. ermöglicht die Analyse auf jeder Ebene des B2B-Datenmodells. |
| Globales Konto + Konto + Person + Sitzung + Ereignis | Analyse der globalen Kontenhierarchie | Fügt ein globales Konto als Container der obersten Ebene über dem Konto hinzu. |

#### Entscheidung: Attributionsmodell für B2B-Metriken

Bestimmen Sie, welches Attributionsmodell der Standard für Konversionsmetriken sein soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Lineare Attribution (13-monatige Rückschau) | Gleiche Gutschrift für alle Touchpoints auf dem B2B-Journey | Am besten zum Verständnis des gesamten Mix von Marketing-Aktivitäten. Empfohlener Ausgangspunkt für B2B. |
| U-förmige Attribution (13-monatiger Lookback) | Betonung auf Erstkontakt und Letztkontakt mit Verrechnung auf Mittelkontakt | Zeigt Lead-Erstellungs- und Opportunity-Konversionsmomente. Häufig in der Bedarfsanalyse. |
| Zeitverfall (13-monatiger Lookback) | Für Touchpoints der neueren Version wird eine höhere Gewichtung empfohlen | Am besten, wenn die Neuigkeit der Interaktion ein wichtiges Signal für die Verkaufsbereitschaft ist. |
| Letztkontakt | Einfache Berichterstellung zum endgültigen Touchpoint vor der Konversion | Einfach zu verstehen, aber unterschätzt Marketing in der Frühphase. Nur für schnelle operative Berichte verwenden. |

#### Entscheidung: Sitzungsdefinition für B2B

Legen Sie fest, wie Sitzungen für die B2B-Interaktion definiert werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Zeitüberschreitung nach 30 Minuten (Standard) | Standardmäßiges Web Analytics-Sitzungsverhalten | Standard für Web-Interaktionsanalyse. Kann Sitzungen zur Nutzung langer Inhalte fragmentieren. |
| Verlängerte Zeitüberschreitung (60-120 Minuten) | B2B-Nutzer nehmen an längeren Forschungssitzungen teil | B2B-Käufer verbringen oft längere Zeit mit der Überprüfung von technischen Inhalten, Preisen und Dokumentation. |
| Ereignisbasierte neue Sitzung | Bestimmte Ereignisse sollten immer eine neue Sitzung starten | Verwenden Sie diese Option, wenn Kampagnen-Clickthroughs oder Demoanfragen immer eine neue Analysesitzung beginnen sollen. |

#### Konfigurieren der Kontodatenansicht

**Benutzeroberflächennavigation:** [!DNL Customer Journey Analytics] > Datenansichten > Neue Datenansicht erstellen

Wichtige Konfigurationsdetails:

- Auswahl der in Phase 1 erstellten Verbindung
- Konfigurieren Sie die Zeitzone und den Kalendertyp entsprechend der Organisation
- Umbenennen von Containern in B2B-relevante Terminologie (z. B. Konto/Interaktion/Touchpoint)
- B2B-Schemafelder Dimensionen zuordnen: Kontoname, Konto-ID, Branche, Unternehmensgröße, Kontoebene, Kontoinhaber, Opportunity-Phase, Opportunity-Wert, Einkaufsgruppenrolle, Lösungsinteresse
- Interaktionsmetriken zuordnen: Ereignisse (Vorfälle), Personen, Sitzungen, Seitenansichten, Formularübermittlungen, E-Mail-Öffnungen, E-Mail-Klicks
- Konfigurieren der Persistenz für Schlüsseldimensionen (z. B. wenn die Kontoindustrie auf Kontoebene verbleibt)
- Setzen Sie die Attribution auf Linear mit 13-monatigem Lookback als Standard für Konversionsmetriken
- Erstellen abgeleiteter Felder für die Marketing-Kanal-Klassifizierung, Interaktionsbewertungsstufen und Opportunity-Stadiengruppierung

**Wo die Optionen unterschiedlich sind:**

**Für Option A (kontozentriert):**
Konfigurieren Sie eine einzelne Datenansicht mit Konto als Container der obersten Ebene. Opportunity- und Einkaufsgruppen-Container einschließen, wenn Pipeline- und Einkaufsgruppenanalyse benötigt werden.

**Für Option B (Global Account-Centric):**
Konfigurieren Sie das globale Konto als Container der obersten Ebene. Konto als Unter-Container einbeziehen, um sowohl globale als auch untergeordnete Analysen zu ermöglichen.

**Für Option C (Hybrid):**
Erstellen Sie zwei Datenansichten aus derselben Verbindung. Datenansicht 1 verwendet Person als primären Container ([!DNL CJA]). Datenansicht 2 verwendet Konto als primären Container mit B2B-Containern. Ordnen Sie ggf. identische Metriken beiden Ansichten zu.

**Dokumentation zu Experience League:**

- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Komponenteneinstellungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistenzeinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributionseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Abgeleitete Felder](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Sitzungseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

### Phase 3: Workspace-Analyse

**Anwendungsfunktion:** [!DNL CJA] B2B: Workspace-Analyse auf Kontoebene, Einkaufsgruppenanalyse, Opportunity-Analyse, B2B-Segmentierung, B2B-Attribution, [!DNL CJA]: Workspace-Analyse, Erstellung berechneter Metriken, Geführte Analyse

Erstellen Sie Workspace-Projekte, die die in den KPIs definierten analytischen Einblicke liefern. Diese Phase umfasst die Erstellung von Freiformtabellen mit B2B-Dimensionen und -Metriken, die Erstellung berechneter Metriken für B2B-KPIs, die Konfiguration B2B-spezifischer Visualisierungen (Fluss auf Kontoebene, Opportunity-funnel, Kaufgruppeninteraktion), die Erstellung von Filtern/Segmenten mithilfe von B2B-Containern und die Anwendung von B2B-Attributionsmodellen.

#### Entscheidung: Analysis Workspace-Struktur

Legen Sie fest, wie das Workspace-Projekt organisiert werden soll.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Einzelnes umfassendes Projekt mit mehreren Bedienfeldern | Kleines Team, alle Stakeholder sehen dieselben Berichte | Einfachere Wartung. Verwenden Sie Bedienfelder, um Themen (Interaktion, Pipeline, Attribution) zu trennen. Bis zu 40 Bedienfelder pro Projekt. |
| Mehrere zielgerichtete Projekte nach Zielgruppe | Verschiedene Stakeholder benötigen unterschiedliche Ansichten | Marketing erhält Interaktion/Attribution. Vertrieb erhält Pipeline-/Kontostatus. Vorgänge erhalten Datenqualität. Mehr Wartung, aber gezielter. |
| Vorlagenbasierte Projekte mit geführter Analyse | Self-Service-Analyse für nicht-erfahrene Benutzer | Verwenden Sie geführte Analysen für funnel und Trendansichten. Als Vorlagen für wiederholbare Analysen speichern. Am besten für eine breite Akzeptanz. |

#### Entscheidung: Berechnete B2B-Metriken

Bestimmen Sie, welche berechneten Metriken für B2B-KPIs benötigt werden.

| Metrik | Formel | Zeitpunkt der Erstellung |
| --- | --- | --- |
| Kundeninteraktionsrate | (Kontoereignisse insgesamt/Konten insgesamt) | Immer - B2B-Kernmetrik |
| Vollständigkeit der Einkaufsgruppe % | (Ausgefüllte Rollen/Erforderliche Rollen) * 100 | Beim Kauf von Gruppenanalyse ist der Umfang |
| Konto-zu-Opportunity-Konversion | Konten mit Opportunities/Engagierten Konten | Wenn eine Pipeline-Analyse erforderlich ist |
| Pipeline-Einfluss % | Beeinflusster Pipeline-Wert/Gesamtpipeline-Wert | Wenn eine Marketing-Attribution erforderlich ist |
| Durchschnittliche Interaktion pro Kontakt | Ereignisse/Unique People pro Konto | Wenn eine Analyse der Kundendurchdringung erforderlich ist |
| Inhaltsinteraktion nach Rolle | Nach Kaufgruppenrolle gefilterte Ereignisse | Wenn eine Inhaltsoptimierung für B2B erforderlich ist |

#### Entscheidung: B2B-Filter/Segmentbereich

Legen Sie fest, auf welcher Container-Ebene Filter erstellt werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Filter auf Kontoebene | Analyse der Konten, die den Kriterien entsprechen (z. B. Unternehmenskonten, bestimmte Branchen) | Umfasst alle Ereignisse aus qualifizierten Konten. Am häufigsten für B2B. |
| Filter auf Opportunity-Ebene | Analyse auf bestimmte Opportunity-Typen oder -Stadien ausgerichtet | Umfasst alle Ereignisse, die mit Opportunities in Verbindung stehen. |
| Kaufen von Filtern auf Gruppenebene | Analyse auf bestimmte Status der Einkaufsgruppe | Umfasst Ereignisse von Personen in qualifizierten Einkaufsgruppen. |
| Filter auf Benutzerebene | Analyse der Personen, die den Kriterien entsprechen (z. B. bestimmte Rollen, Titel) | Standardfilterverhalten. Verwenden Sie diese Option, wenn Sie individuelle Interaktionen im B2B-Kontext analysieren. |

#### Workspace-Analyse erstellen

**UI-Navigation:** [!DNL Customer Journey Analytics] > Workspace > Projekte > Projekt erstellen

Wichtige Konfigurationsdetails:

- Auswahl der in Phase 2 erstellten B2B-Datenansicht
- Erstellen von Freiformtabellen mit Dimensionen auf Kontoebene (Kontoname, Branche, Ebene), aufgeschlüsselt nach Interaktionsmetriken
- Opportunity funnel-Visualisierungen erstellen, die den Opportunity-Fortschritt über Stadien zeigen
- Aufbauen von Tabellen zur Gruppenzusammensetzung für den Einkauf, in denen die Füllraten und die Interaktionen pro Rolle angezeigt werden
- Konfigurieren von B2B-Attributionsfeldern, die Attributionsmodelle (linear, U-förmig, Zeitverfall) mit einem 13-monatigen Lookback vergleichen
- Erstellen Sie Visualisierungen des Kontoflusses, die gängige Pfade durch den Kauf-Journey zeigen.
- Kohortentabellen erstellen, die die Kundenbindung und Interaktion im Laufe der Zeit analysieren
- Anwenden von B2B-Filtern auf die Segmentanalyse nach Kontoebene, Branche oder Interaktionsstufe
- Erstellen Sie Anmerkungen für wichtige Ereignisse (Kampagnenstarts, Produktversionen, Preisänderungen)

**Dokumentation zu Experience League:**

- [Übersicht über Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen eines Projekts](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freiformtabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Flussvisualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Übersicht über Filter](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berechnete Metriken erstellen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Anmerkungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Aufschlüsselungsdimensionen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### Phase 4: Dashboard-Veröffentlichung

**Anwendungsfunktion:** [!DNL CJA]: Dashboard- und Scorecard-Veröffentlichung, [!DNL CJA]: Zielgruppenveröffentlichung

Erstellen Sie freigebbare Dashboards und mobile Scorecards, die Stakeholdern Einblicke in B2B-Analysen liefern. In dieser Phase werden auch [!DNL CJA] B2B-Zielgruppen zur Aktivierung in nachgelagerten Anwendungsfällen wie der B2B-Zielgruppenaktivierung wieder in AEP veröffentlicht.

#### Entscheidung: Dashboard-Versandmethode

Legen Sie fest, wie B2B-Analytics-Einblicke für Stakeholder bereitgestellt werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Workspace-Projekt (Desktop) | Analysten und Marketing-Experten, die interaktive Analysen benötigen | Vollständige Interaktivität, Drilldown, Umschalten des Filters. Erfordert [!DNL CJA] Zugriff. |
| Mobile Scorecard | Führungskräfte und Vertriebsleiter, die übersichtliche KPIs benötigen | Zusammenfassungszahlen mit Trendlinien. Zugänglich über [!DNL Adobe Analytics] Dashboards-App. Eingeschränkte Interaktivität |
| Geplanter PDF-/CSV-Export | Stakeholder ohne [!DNL CJA], die regelmäßige Updates benötigen | Automatisierter Versand nach einem Zeitplan. Keine Interaktivität. Am besten geeignet für wöchentliche/monatliche Executive-Zusammenfassungen. |
| Alle oben genannten Funktionen | Große Organisationen mit unterschiedlichen Stakeholder-Anforderungen | Maximale Reichweite. Höherer Wartungsaufwand. Empfohlen für ausgereifte B2B-Analyseprogramme. |

#### Entscheidung: Zielgruppenveröffentlichung aus [!DNL CJA]

Legen Sie fest, ob B2B-Segmente zur Aktivierung wieder in AEP veröffentlicht werden sollen.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Kontobasierte Zielgruppen veröffentlichen | Analytics-Einblicke sollten Informationen zu Targeting und Unterdrückung enthalten | Aktiviert [!DNL CJA] Segmente (z. B. „hochgradig interaktive Konten ohne offene Opportunities„) über [!DNL RT-CDP]. Aktualisierungskadenz: 4 Stunden bis wöchentlich. |
| Nicht veröffentlichen | Analytics ist nur für das Reporting, nicht für die Aktivierung vorgesehen | Einfachere Konfiguration. Die Aktivierung wird in [!DNL RT-CDP] separat durchgeführt. |

#### Veröffentlichen von Dashboards und Audiences

**Benutzeroberflächennavigation:** [!DNL Customer Journey Analytics] > Projekte > Freigeben (für Workspace), Projekte > Erstellen > Mobile Scorecard (für Scorecards), Komponenten > Zielgruppen > Veröffentlichen (für Zielgruppenveröffentlichung)

Wichtige Konfigurationsdetails:

- Erstellen von Executive-Dashboards mit Zusammenfassungsnummern für wichtige B2B-KPIs (Gesamtzahl der engagierten Konten, Pipeline-Wert, Vollständigkeit der Einkaufsgruppe)
- Konfigurieren von Vergleichszeiträumen (Monat gegenüber Monat, Quartal gegenüber Quartal) für Trendindikatoren
- Erstellen Sie mobile Scorecards mit Kacheln für Kontointeraktion, Pipeline-Status und Attributionsmetriken
- Filter für Führungskräfte hinzufügen, um Ansichten nach Region, Branche oder Kontoebene umzuschalten
- Konfigurieren der geplanten Projektbereitstellung für wöchentliche ausführende Berichte
- Für die Veröffentlichung von Zielgruppen: Wählen Sie den B2B-Filter aus, konfigurieren Sie den Identity-Namespace (Konto-ID) und legen Sie die Aktualisierungskadenz fest

**Dokumentation zu Experience League:**

- [Erstellen einer mobilen Scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Freigeben von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planen von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Scorecards konfigurieren und kuratieren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-Dashboards - Leitfaden für Führungskräfte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

## Überlegungen bei der Implementierung

In den folgenden Abschnitten werden Leitplanken, häufige Fallstricke, Best Practices und Kompromissentscheidungen behandelt, die bei der Implementierung zu beachten sind.

### Leitplanken und Beschränkungen

- [!DNL CJA] Verbindungen können Datensätze aus nur einer AEP-Sandbox enthalten - [CJA-Leitplanken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- Maximal 5.000 Dimensionen und 5.000 Metriken pro Datenansicht
- Maximal 100 abgeleitete Felder pro Datenansicht
- Die B2B-Attribution unterstützt Lookback-Fenster von bis zu 13 Monaten für Analysen auf Kontoebene
- Maximal 75 veröffentlichte Zielgruppen pro [!DNL CJA]-Kunde in allen Sandboxes
- Die minimale Aktualisierungskadenz für die Zielgruppenveröffentlichung beträgt alle 4 Stunden
- Die Streaming-Latenz von AEP zu [!DNL CJA] beträgt in der Regel weniger als 90 Minuten
- Freiformtabellen unterstützen Aufschlüsselungen von bis zu 10 Dimensionen
- Mobile Scorecards unterstützen bis zu 16 Kacheln pro Scorecard
- Workspace-Projekte unterstützen bis zu 40 Bedienfelder pro Projekt
- Die Aufstockung großer B2B-Datensätze (Milliarden von Datensätzen) kann Tage dauern

### Häufige Fehler

- **Unvollständige Zuordnung von Person zu Konto:** Wenn Ereignisse auf Personenebene nicht mit einem Konto verknüpft werden können, werden sie nicht in der Analyse auf Kontoebene angezeigt. Stellen Sie sicher, dass alle Ereignisdatensätze ein Feld enthalten, das entweder direkt oder über einen Such-Datensatz für eine Person-Konto mit der Konto-ID verbunden werden kann. Überprüfen Sie den Prozentsatz der Ereignisse mit fehlender Kontozuordnung, bevor Sie eine Analyse erstellen.
- **Falsche Bezeichnung des Datensatztyps:** B2B-Lookup-Datensätze (Opportunity, Einkaufsgruppe, Personen-Konto-Beziehungen) müssen in der [!DNL CJA]-Verbindung korrekt als Lookup- oder Profiltyp gekennzeichnet sein. Die falsche Eingabe eines Lookup-Datensatzes als Ereignis-Datensatz führt zu falschen Ergebnissen, da [!DNL CJA] versucht, jeden Datensatz als Ereignis mit Zeitstempel zu behandeln.
- **Attributionsfenster zu kurz für B2B:** Bei der Verwendung von standardmäßigen 30-tägigen Attributionsfenstern werden in B2B-Journey in der Regel frühzeitige Touchpoints verpasst, die sich über 6 bis 18 Monate erstrecken. Konfigurieren Sie immer 13-monatige Lookback-Fenster für B2B-Attributionsmetriken.
- **Metriken auf Konto- und Personenebene falsch mischen** Das Zählen von „Personen“ in einer Analyse auf Kontoebene kann irreführend sein. Stellen Sie sicher, dass berechnete Metriken auf der entsprechenden Container-Ebene definiert werden. Eine „Account-Interaktionsrate“ sollte Ereignisse auf Kontoebene verwenden, die nach Konten dividiert werden, nicht nach Personen.
- **Veraltete Einkaufsgruppendaten:** Die Zusammensetzung der Einkaufsgruppe und die Funktionszuweisungen ändern sich im Laufe der Zeit. Wenn Käufergruppen-Datensätze nicht regelmäßig aktualisiert werden, sind die Vollständigkeitsmetriken ungenau. Stellen Sie sicher, dass das Quellsystem ([!DNL Marketo Engage] oder [!DNL AJO] B2B edition) aktiv Kaufgruppendaten synchronisiert.
- **Ein einzelnes Arbeitsbereich-Projekt wird überlastet:** B2B-Analyse umfasst Interaktion, Pipeline, Attribution und Einkaufsgruppen. Der Versuch, alles in einem Projekt zu platzieren, führt zu langsamem Laden und verwirrender Navigation. Verwenden Sie mehrere fokussierte Projekte oder klar beschriftete Bedienfelder.

### Best Practices

- Beginnen Sie mit Option A (Account-zentriert), auch wenn Sie planen, Option B (Global Account) später zu verwenden. Account-Centric Analytics ist einfacher und validiert Ihr Datenmodell, bevor die Hierarchie komplexer wird.
- Erstellen Sie ein dediziertes Workspace-Projekt „B2B-Datenqualität“, das den Prozentsatz der Ereignisse mit Kontozuordnung, die Anzahl verwaister Konten und Kaufgruppen-Vollständigkeitsmetriken verfolgt. Führen Sie diese wöchentliche Sitzung aus, um Datenprobleme frühzeitig zu erkennen.
- Verwenden Sie abgeleitete Felder, um auf der Grundlage der Anzahl von Ereignissen auf Kontoebene Interaktionsbewertungsstufen (hoch/Medium/niedrig) zu erstellen. Dies vereinfacht die Analyse und macht Dashboards für technisch nicht versierte Stakeholder verwertbarer.
- Beginnen Sie bei der Konfiguration der B2B-Attribution mit der linearen Attribution als Baseline und vergleichen Sie sie dann mit U-förmigen Modellen und Modellen mit Zeitverfall. Die Unterschiede zwischen den Modellen zeigen häufig, ob Ihr Marketing-Mix auf Sensibilisierungs- oder Konversionsaktivitäten ausgerichtet ist.
- Veröffentlichen Sie eine mobile Scorecard „B2B-Zusammenfassung für Führungskräfte“ mit höchstens acht Kacheln, die die KPIs abdecken, die für Führungskräfte am wichtigsten sind. Konzentrieren Sie sich darauf - Executive Scorecards sollten die Frage beantworten: „Wie steht es um uns?“ nicht „Warum?“
- Kommentieren Sie wichtige Ereignisse (Produkteinführungen, wichtige Kampagnenstarts, Preisänderungen, Verkaufsprozessänderungen), um einen Kontext für Daten-Trends zu schaffen. B2B-Daten zeigen häufig Spitzen und Tiefpunkte, die ohne Ereigniskontext nicht erklärbar sind.
- Verwenden Sie bei der Veröffentlichung von B2B-Zielgruppen aus [!DNL CJA] die tägliche Aktualisierung für standardmäßige Aktivierungssegmente und eine 4-stündige Aktualisierung nur für zeitkritische Segmente. Häufige Aktualisierungen beanspruchen Verarbeitungsressourcen.

### Entscheidungen über Kompromisse

>[!NOTE]
>Die folgenden Entscheidungen sollten auf der Grundlage der spezifischen Anforderungen und Einschränkungen Ihres Unternehmens bewertet werden.

**Datenvollständigkeit vs. analytische Genauigkeit**

Die Einbeziehung aller Ereignisse auf Personenebene in die Kontoanalyse (auch solcher mit schwacher Kontozuordnung) verbessert die Vollständigkeit der Daten, kann jedoch die analytische Genauigkeit verringern, wenn die Kontozuordnung unzuverlässig ist.

- **Mit allen Ereignisfavoriten:** umfassende Interaktionsmessung, höhere Werte für die Interaktion mit Kunden, breitere Sichtbarkeit
- **Ausschließen nicht übereinstimmender Ereignis-Gefälligkeiten**: Präzise Metriken auf Kontoebene, vertrauenswürdige Attribution, zuverlässige Pipeline-Korrelation
- **Empfehlung:** Schließen Sie nicht übereinstimmende Ereignisse aus der Analyse auf Kontoebene aus, schließen Sie sie jedoch in eine separate Datenansicht auf Personenebene ein (Option C), um das vollständige Bild zu verstehen. Priorisieren Sie die Verbesserung der Qualität der Kontoverknüpfungsdaten als parallelen Arbeitsablauf.

**Länge des Lookback-Fensters der B2B-Attribution**

Längere Lookback-Fenster (13 Monate) erfassen mehr Touchpoints, können jedoch Marketing-Aktivitäten enthalten, die für die aktuelle Kaufentscheidung nicht mehr relevant sind.

- **Längere Lookback-Zeit (13 Monate) bevorzugt:** Erfassung der vollständigen B2B-Journey, Gutschrift von Sensibilisierungsaktivitäten, Berücksichtigung langer Verkaufszyklen
- **Kürzere Lookback-Favoriten (6 Monate):** Konzentration auf die Interaktion vor kurzem, Reduzierung des Lärms durch alte Touchpoints, bessere Spiegelung der aktuellen Kaufabsicht
- **Empfehlung:** Verwenden Sie den 13-monatigen Lookback für Unternehmenskonten mit langen Verkaufszyklen (ab 12 Monaten). Verwenden Sie den 6-monatigen Lookback für Mid-Market-Accounts mit kürzeren Zyklen. Erstellen Sie für jedes zu vergleichende Fenster separate berechnete Metriken.

**Eine umfassende Datenansicht im Vergleich zu mehreren fokussierten Datenansichten**

Eine Datenansicht mit allen B2B-Containern und -Dimensionen ist einfacher zu verwalten, kann Analysten jedoch mit Komplexität überfordern. Mehrere fokussierte Datenansichten (Interaktion, Pipeline, Attribution) sind einfacher zu verwenden, aber schwieriger zu verwalten.

- **Single View favorisiert:** Konsistenz, einfachere Wartung, domänenübergreifende Analyse innerhalb eines einzigen Projekts
- **Mehrere Ansichten :** für Analysten, schnellere Ladezeiten, maßgeschneiderte Komponentenlisten pro Anwendungsfall
- **Empfehlung** Beginnen Sie mit einer einzigen, umfassenden Datenansicht. Wenn Analysten Schwierigkeiten bei der Suche nach den richtigen Dimensionen und Metriken melden, erstellen Sie kuratierte Komponentengruppen innerhalb derselben Ansicht, bevor Sie sie in mehrere Ansichten aufteilen. Verwenden Sie Workspace-Vorlagen , um Analysten zu den richtigen Komponenten zu führen.

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten zusätzliche Informationen zur Implementierung dieses Anwendungsfallmusters.

**[!DNL CJA]B2B edition**

- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA-Leitplanken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

**Verbindungen**

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verwalten von Verbindungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

**Datenansichten**

- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Komponenteneinstellungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistenzeinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributionseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Formateinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Abgeleitete Felder](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Sitzungseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace und Analyse**

- [Übersicht über Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen eines Projekts](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freiformtabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flussvisualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Freigeben von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planen von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Aufschlüsselungsdimensionen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Komponenten**

- [Übersicht über Filter](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Erstellen von Filtern](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berechnete Metriken erstellen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Anmerkungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Datumsbereiche](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Zielgruppen**

- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Verwalten von Audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

**Dashboards und Scorecards**

- [Erstellen einer mobilen Scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Scorecards konfigurieren und kuratieren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-Dashboards - Leitfaden für Führungskräfte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Geführte Analyse**

- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trend-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Aufbewahrungsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [Übersicht über RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition-Schemata](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Übersicht über B2B-Quellen](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/sources/b2b)

**AEP Data Foundation**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)

**Data Governance und Lebenszyklus**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Erweitertes Data Lifecycle Management](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Tutorials und Handbücher**

- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
