---
title: Generierung von Customer Analytics und Insight
description: Erfahren Sie, wie Sie kanalübergreifende Analyse-Arbeitsbereiche, berechnete Metriken und Dashboards für die Verhaltens- und Leistungsanalyse erstellen.
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 3%

---

# Generierung von Kundenanalysen und insight

In diesem Handbuch wird das Anwendungsfallmuster der Kundenanalyse- und insight-Generierung beschrieben, das [!DNL Adobe Experience Platform] Datensätze mit [!DNL Customer Journey Analytics] verbindet, um Datenansichten, Freiformanalyse-Arbeitsbereiche, berechnete Metriken, Dashboards und mobile Scorecards zu erstellen und optional CJA-definierte Zielgruppen zur Aktivierung wieder in [!DNL Adobe Experience Platform] zu veröffentlichen.

Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Im Gegensatz zu anderen Mustern in der Taxonomie, die sich auf Aktivierung und Interaktion konzentrieren (Senden von Nachrichten, Personalisieren von Inhalten, Aktivieren von Zielgruppen), konzentriert sich dieses Muster auf das Verständnis - die Analyse des Kundenverhaltens, die Messung der Kampagnenleistung, die Identifizierung von Trends und die Generierung von Einblicken, die in Strategie- und Optimierungsentscheidungen einfließen.

## Anwendungsfallmuster

**Generierung von Kundenanalysen und insight**

Erstellen Sie kanalübergreifende Analyse-Arbeitsbereiche, berechnete Metriken und Dashboards, um das Kundenverhalten und die Kampagnenleistung zu verstehen.

**Ausführungsplan:** Datenverbindung > Konfiguration der Datenansicht > Workspace Analysis > Dashboard-Veröffentlichung

## Anwendungsfall - Übersicht

Unternehmen müssen verstehen, wie sich Kundinnen und Kunden kanalübergreifend verhalten, wie Kampagnen funktionieren, wo Kundinnen und Kunden in ihren Journey abbrechen, welche Inhalte nachhallen und wie verschiedene Segmente im Laufe der Zeit erhalten. Die Generierung von Customer Analytics und insight erfüllt diese Anforderung, indem die umfangreichen kanalübergreifenden Daten in [!DNL Adobe Experience Platform] mit [!DNL Customer Journey Analytics] verbunden werden. Dort können Analysten Freiform-Arbeitsbereiche erstellen, benutzerdefinierte Metriken erstellen, Attributionsmodelle konfigurieren und Dashboards für die Nutzung durch Stakeholder veröffentlichen.

Das Muster richtet sich an mehrere Zielgruppen: Marketing-Analysten, die eine gründliche Analyse benötigen, Kampagnen-Manager, die Performance-Dashboards benötigen, Produkt-Manager, die Interaktion und Kundenbindungseinblicke benötigen, und Führungskräfte, die KPI-Scorecards auf einen Blick benötigen. Der Implementierungsansatz variiert je nach primärem analytischen Schwerpunkt - Kampagnenleistungsmessung, Cross-Channel-Journey-Analyse, analysegesteuerte Zielgruppenaktivierung oder angeleitete Produkterkenntnisse.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**Verbesserung von Analyse und Reporting**

Verbessern Sie die Reporting-Funktionen für schnellere, umsetzbarere Marketing-Einblicke durch einheitliche Dashboards und Self-Service-Tools.

- **KPIs:**, Produktivität

Weitere [&#x200B; zu diesem Geschäftsziel finden Sie unter &#x200B;](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)Verbesserung von Analysen und Reporting“.

**Datengesteuerte Entscheidungsfindung aktivieren**

Ermöglichen Sie Teams durch Self-Service-Analysen, Echtzeit-Kundeneinblicke und KI-gestützte Prognosen eine Strategie.

- **KPIs:**, Produktivität

Weitere [&#x200B; zu diesem Geschäftsziel finden Sie &#x200B;](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md) „Datengesteuerte Entscheidungsfindung aktivieren“.

**Marketing-Attribution**

Die Auswirkungen von Marketing-Touchpoints, Kanälen und Kampagnen auf Konversions- und Umsatzergebnisse genau messen.

- **KPIs:**, inkrementeller Umsatz

Weitere [&#x200B; zu diesem Geschäftsziel finden &#x200B;](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md) unter „Marketing-Attribution verbessern“.

**Marketing-Ausgaben und -ROI optimieren**

Optimieren Sie die Zuweisung von Marketing-Budgets, indem Sie verstehen, welche Kanäle und Kampagnen die höchste Rendite erbringen.

- **KPIs:**, inkrementeller Umsatz

Weitere [&#x200B; zu diesem Geschäftsziel finden Sie unter &#x200B;](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md) von Marketingausgaben und -renditen .

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie Beispiele für taktische Anwendungsfälle, die mit diesem Muster implementiert werden können.

- Dashboard zur Kampagnenleistung - Versandmetriken, Interaktionsraten, Konversion und Umsatzzuordnung für E-Mail-, SMS-, Push- und Paid-Media-Kampagnen
- Fallout-Analyse für Kunden-Journey - Identifizieren Sie, wo Kundinnen und Kunden bei Käufen, Registrierungen oder Onboarding-Trichtern ablegen
- Kohortenbeibehaltungsanalyse - misst, wie gut verschiedene Akquise-Kohorten über Wochen, Monate und Quartale hinweg binden.
- Attributionsmodellierung für Kanäle - Vergleichen Sie die Attribution für Erstkontakt, Letztkontakt, Linear und Zeitverfall, um zu verstehen, welche Kanäle Konversionen fördern
- Analyse der Content-Performance - Ermitteln Sie, welche Inhalte nach Segment, Kanal und Lebenszyklusphase am meisten Resonanz finden
- Analyse der Produktnutzung und -übernahme - Verfolgen Sie die Implementierung von Funktionen, die Interaktionsfrequenz und das Benutzerwachstum
- Analyse des Kundenlebenszyklus-Stadiums - Segmentieren und Analysieren von Kunden nach Lebenszyklus-Stadium (neu, aktiv, gefährdet, abgelaufen)
- Marketing-Mix-Optimierungs-Dashboard - Kanalinvestitionen mit dem Umsatzbeitrag vergleichen
- Bewertung und Reporting für kanalübergreifende Interaktionen - Erstellen von zusammengesetzten Interaktionswerten aus Web-, App-, E-Mail- und Kampagneninteraktionen

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Effizienz | Verkürzung der Time-to-insight und des manuellen Reporting | Verfolgen der mit der Berichterstellung vor und nach der CJA-Implementierung verbrachten Zeit der Analysten |
| Produktivität | Anzahl der von Business-Anwendern erstellten Self-Service-Analysen | Überwachen der Erstellung und Verwendung von Workspace-Projekten |
| Inkrementeller Umsatz | Umsatz, der erkenntnisgesteuerten Optimierungsentscheidungen zugeschrieben wird | Messung des Umsatzanstiegs aus Kampagnen, die auf der Grundlage von CJA-Analysen optimiert wurden |
| Konversionsraten | Funnel-Abschlussraten in allen wichtigen Kunden-Journey | Verfolgen Sie Fallout-Raten bei jedem Journey-Schritt mithilfe der CJA-Fallout-Visualisierung |
| Interaktion | Tiefe und Häufigkeit der kanalübergreifenden Kundeninteraktion | Erstellen von berechneten Metriken für die Interaktionsbewertung in CJA |
| Treue | Kundenrenditen über bestimmte Zeiträume | Verwenden der CJA-Kohortenanalyse zur Messung der Kundenbindungskurven |

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Customer Journey Analytics] (CJA)** - Verbindungen, Datenansichten, Workspace-Analyse, geführte Analyse, berechnete Metriken, Dashboards, Zielgruppenveröffentlichung und Inhaltsanalyse
- **[!DNL Adobe Experience Platform] (AEP)** - Data Lake, Datensätze, XDM-Schemata, Profil- und Ereignisdaten, die CJA-Verbindungen nutzen

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten zusätzliche Informationen zu diesem Anwendungsfallmuster.

### [!DNL Customer Journey Analytics] - Erste Schritte

- [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA-Leitplanken](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-admin/guardrails)

### Verbindungen

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-connections/overview)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-connections/create-connection)
- [Verwalten von Verbindungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-connections/manage-connections)

### Datenansichten

- [Übersicht über Datenansichten](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/data-views)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Komponenteneinstellungen - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistenzeinstellungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributionseinstellungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Formateinstellungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplizierung der Metrik](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Werte ein-/ausschließen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Sitzungseinstellungen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Abgeleitete Felder](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace und Analyse

- [Übersicht über Workspace](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen eines Projekts](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freiformtabelle](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flussvisualisierung](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Aufschlüsselungsdimensionen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Freigeben von Projekten](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planen von Projekten](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Exportübersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Geführte Analyse

- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trend-Ansicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Interaktionsfrequenzansicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Aufbewahrungsansicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Aktive Wachstumsansicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Ansicht der Auswirkungen der Version](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/impact/release)
- [Auswirkungsansicht für erste Verwendung](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Zeitleisten-Ansicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Komponenten

- [Übersicht über Filter](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Erstellen von Filtern](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berechnete Metriken erstellen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funktionen für berechnete Metriken](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Anmerkungen - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/annotations/overview)
- [Datumsbereiche](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Metrikkomponente](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Zielgruppenveröffentlichung

- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/audiences/publish)
- [Verwalten von Audiences](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-components/audiences/manage)

### Inhaltsanalyse

- [Content Analytics](https://experienceleague.adobe.com/de/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics-Konfiguration](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboards und Scorecards

- [Erstellen einer mobilen Scorecard](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Scorecards konfigurieren und kuratieren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-Dashboards - Leitfaden für Führungskräfte](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualisierung der Zusammenfassungszahl](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP Foundations

- [Übersicht über Datensätze](https://experienceleague.adobe.com/de/docs/experience-platform/catalog/datasets/overview)
- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Überblick über Quellen](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Zielgruppen-Portal - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/audience-portal)

### Berichtsintegration für AJO

- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [E-Mail-Bericht zu Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Journey Email Report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutorials und Handbücher

- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/schema/composition)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)
