---
title: B2B-Analyse
description: Erfahren Sie, wie Sie Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden einbeziehen.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 2%

---

# B2B-Analyse

In diesem Handbuch wird das Anwendungsfallmuster für B2B-Analytics beschrieben, bei dem [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition und [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition verwendet werden, um Informationen auf B2B-Kontoebene in die kanalübergreifende Journey-Analyse für Kunden einzubinden. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

B2B Analytics erweitert die standardmäßigen [!DNL CJA] mit Account-basierten Verbindungen, B2B-spezifischen Containern (Account, Global Account, Opportunity, Buying Group) und Reporting auf Kontoebene. Diese Funktion ermöglicht es Unternehmen, Marketing- und Vertriebsaktivitäten auf Kontoebene zu analysieren, den Verlauf von Opportunitys zu verfolgen, die Vollständigkeit von Käufen zu messen und den Umsatz Marketing-Touchpoints über erweiterte B2B-Verkaufszyklen hinweg zuzuordnen.

## Anwendungsfallmuster

**B2B-Analyse**

Binden Sie Informationen auf B2B-Kontoebene in die kanalübergreifende Analyse von Kunden-Journey ein.

**Ausführungsplan:** B2B-Datenverbindung > Konfiguration der Kontodatenansicht > Workspace Analysis > Dashboard-Veröffentlichung

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

## Programme

Die folgenden Anwendungen werden verwendet, um dieses Anwendungsfallmuster zu implementieren.

- **[!DNL Customer Journey Analytics]B2B edition** - Bietet Account-basierte Verbindungen, B2B-spezifische Datenansichts-Container, Workspace-Analysen auf Kontoebene, Einkaufsgruppenanalysen, Opportunity-Analysen, B2B-Segmentierung und B2B-Attribution mit erweiterten Lookback-Fenstern
- **[!DNL Real-Time CDP]B2B edition** - Bietet die B2B-Datengrundlage einschließlich der Vereinheitlichung von Account-Profilen, B2B-Identitätsauflösung, B2B-Schemaklassen (Account, Opportunity, Buying Group) und [!DNL Marketo Engage] Integration für die Aufnahme von B2B-Interaktionsdaten

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
- [Überblick über Quellen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
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
