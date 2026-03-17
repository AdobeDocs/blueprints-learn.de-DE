---
title: Generierung von Customer Analytics und Insight
description: Erfahren Sie, wie Sie kanalübergreifende Analyse-Arbeitsbereiche, berechnete Metriken und Dashboards für die Verhaltens- und Leistungsanalyse erstellen.
solution: Customer Journey Analytics, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 1%

---


# Generierung von Kundenanalysen und insight

Dieses Handbuch bietet eine vollständige Implementierungsreferenz für die Generierung von Kundenanalysen und insight. Es wird beschrieben, wie Sie [!DNL Adobe Experience Platform] Datensätze mit [!DNL Customer Journey Analytics] verbinden, Datenansichten konfigurieren, Freiformanalysearbeitsbereiche erstellen, berechnete Metriken erstellen, Dashboards und mobile Scorecards veröffentlichen und optional CJA-definierte Zielgruppen zur Aktivierung wieder in [!DNL Adobe Experience Platform] veröffentlichen.

Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die alle praktikablen Implementierungspfade, die Kompromisse zwischen ihnen und die in jeder Phase erforderlichen Konfigurationsentscheidungen verstehen müssen.

Im Gegensatz zu anderen Mustern in der Taxonomie, die sich auf Aktivierung und Interaktion konzentrieren (Senden von Nachrichten, Personalisieren von Inhalten, Aktivieren von Zielgruppen), konzentriert sich dieses Muster auf das Verständnis - die Analyse des Kundenverhaltens, die Messung der Kampagnenleistung, die Identifizierung von Trends und die Generierung von Einblicken, die in Strategie- und Optimierungsentscheidungen einfließen. Es ist das am häufigsten zusammengestellte Muster und paart sich mit fast jedem Aktivierungs- oder Personalisierungsmuster.

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

## Anwendungsfallmuster

**Generierung von Kundenanalysen und insight**

Erstellen Sie kanalübergreifende Analyse-Arbeitsbereiche, berechnete Metriken und Dashboards, um das Kundenverhalten und die Kampagnenleistung zu verstehen.

**Funktionskette:** Datenverbindung > Konfiguration der Datenansicht > Workspace Analysis > Erstellung berechneter Metriken > Dashboard-Veröffentlichung

Eine Anleitung zur Komposition finden [&#x200B; im Abschnitt &#x200B;](#implementation-options)Implementierungsoptionen“.

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Customer Journey Analytics] (CJA)** - Verbindungen, Datenansichten, Workspace-Analyse, geführte Analyse, berechnete Metriken, Dashboards, Zielgruppenveröffentlichung und Inhaltsanalyse
- **[!DNL Adobe Experience Platform] (AEP)** - Data Lake, Datensätze, XDM-Schemata, Profil- und Ereignisdaten, die CJA-Verbindungen nutzen

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | CJA-Produktprofil mit Zugriffsberechtigungen für Arbeitsbereich-Erstellung und Datenansicht bereitgestellt. AEP-Datensätze, auf die über die CJA-Verbindung zugegriffen werden kann. Benutzende, denen entsprechende CJA-Rollen zugewiesen sind. | [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | XDM-Schemata und Datensätze, die mit CJA verbunden werden, müssen in AEP vorhanden sein. Das Schema-Design wirkt sich direkt darauf aus, welche Dimensionen und Metriken in CJA-Datenansichten verfügbar sind. Ereignisschemata benötigen Zeitstempelfelder; Lookup-Schemata benötigen Schlüsselfelder. | [XDM-System - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Datenquellen und Sammlung | Erforderlich | Daten müssen in AEP-Datensätze fließen - Web-Ereignisse über Web SDK, App-Ereignisse über Mobile SDK, AJO-Kampagnenereignisse, CRM-Daten über Quell-Connectoren. Die Fülle der Analysen hängt von der Breite der erfassten Daten ab. | [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | Die Personen-ID-Konfiguration in der CJA-Verbindung bestimmt, wie Ereignisse über Datensätze hinweg zugeordnet werden. Die geräteübergreifende Identitätszuordnung in AEP verbessert die Fähigkeit von CJA, vollständige Kunden-Journey zu erstellen. Identity-Namespace muss für das Feld Personen-ID konfiguriert werden. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Zielgruppendefinition und Segmentierung | Nicht zutreffend | CJA erstellt im Analysekontext eigene Filter und Audiences. RT-CDP-Zielgruppen sind keine Voraussetzung, obwohl CJA Zielgruppen über die Zielgruppenveröffentlichung wieder in AEP veröffentlichen kann (Option C). | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete AEP-Attribute können die mit CJA verbundenen Datensätze anreichern und zusätzliche Dimensionen und Metriken für die Analyse bereitstellen (z. B. Lebensdaueranzahl der Käufe, Tage seit der letzten Aktivität). Diese Aggregationen auf Profilebene werden als Dimensionen in CJA-Datenansichten verfügbar. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Richtlinien zur Datensatzaufbewahrung beeinflussen, welche historischen Daten in CJA verfügbar sind. Eine lange Datenaufbewahrung wird in der Regel für Analysen gewünscht, um Vergleiche über das Jahr hinweg und langfristige Trendanalysen zu ermöglichen. Konfigurieren von Datensatz-TTLs, um eine angemessene Verlaufstiefe sicherzustellen. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für sensible Felder können einschränken, was in CJA-Datenansichten angezeigt wird. Wenn personenbezogene Daten oder vertrauliche Daten in der CJA-Verbindung enthalten sind, stellen Data Governance-Kennzeichnungen den konformen Zugriff sicher und verhindern das unbefugte Eindringen in freigegebene Dashboards. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | Der Zustand der CJA-Verbindung und die Datenfrische sollten überwacht werden. Konfigurieren Sie Warnhinweise für Fehler im Quelldatenfluss und Aufnahmeprobleme, um sicherzustellen, dass die Daten für CJA zuverlässig und aktuell sind. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Dies ist die Reporting- und Analyseimplementierung. Wenn ein Referenzplan für ein anderes Muster S5 enthält, verwenden Sie diesen Kundenanalysen- und insight-Generierungsplan für die Analytics-Implementierung. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Customer Journey Analytics] (CJA)

In der folgenden Tabelle sind die in diesem Muster verwendeten CJA-Anwendungsfunktionen aufgeführt.

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Datenverbindung | Phase 1: Datenverbindung | Binden von AEP-Datensätzen an eine CJA-Verbindung für kanalübergreifende Analysen, Konfigurieren von Datensatztypen und Personen-ID für die Zuordnung von Datensätzen untereinander |
| Konfiguration der Datenansicht | Phase 2: Konfiguration der Datenansicht | Definieren von Dimensionen, Metriken, Attributionsmodellen, Persistenzeinstellungen, Sitzungsparametern und abgeleiteten Feldern, die die analytische Perspektive formen |
| Workspace-Analyse | Phase 3: Analyse und Erstellung von Metriken | Erstellen von Freiformanalyse-Projekten mit Tabellen, Visualisierungen, Filtern, Anmerkungen und Dimensionsaufschlüsselungen (Optionen A, B, C) |
| Angeleitete Analyse | Phase 3: Analyse und Erstellung von Metriken | Verwenden strukturierter geführter Workflows für die Analyse von funnel, Trends, Kundenbindung, Benutzerwachstum und Interaktionshäufigkeit (Option D) |
| Erstellung berechneter Metriken | Phase 3: Analyse und Erstellung von Metriken | Definieren Sie berechnete Metriken mithilfe von Formeln, Filtern und Funktionen für wiederverwendbare KPIs wie Konversionsrate, Interaktionswert und Umsatz pro Besuch |
| Dashboard- und Scorecard-Veröffentlichung | Phase 4: Dashboard-Veröffentlichung | Erstellen und Freigeben interaktiver Dashboards und mobiler Scorecards für das Reporting von Stakeholdern |
| Zielgruppenveröffentlichung | Phase 5: Zielgruppenveröffentlichung (nur Option C) | CJA-definierte Zielgruppen zur nachgelagerten Aktivierung wieder im AEP-Echtzeit-Kundenprofil veröffentlichen |
| Content Analytics | Phase 3: Analyse und Erstellung von Metriken | Analysieren von Trends, Anomalien und Ermüdungserscheinungen in digitalen Eigenschaften (wenn die Inhaltsanalyse im Fokus steht) |

### [!DNL Adobe Experience Platform] (AEP)

In der folgenden Tabelle sind die in diesem Muster verwendeten AEP-Anwendungsfunktionen aufgeführt.

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Data Lake und Datensätze | Voraussetzung (F2, F3) | Geben Sie die Quellereignis-, Profil- und Lookup-Datensätze an, die die CJA-Verbindung speisen |
| Identity Service | Voraussetzung (F4) | Bereitstellen der Konfiguration von Identity-Namespaces für die Personen-ID-Zuordnung zwischen Datensätzen in der CJA-Verbindung |

## Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, bevor Sie dieses Anwendungsfallmuster implementieren.

- Die Produktberechtigung für CJA wurde für das Unternehmen bereitgestellt.
- CJA-Produktprofile werden mit dem entsprechenden Benutzerzugriff konfiguriert (Erstellung von Arbeitsbereichen, Zugriff auf Datenansichten)
- Die AEP-Sandbox enthält die Zieldatensätze mit Datenfluss (Web-Ereignisse, App-Ereignisse, Kampagnendaten, CRM-Datensätze)
- XDM-Schemata werden für alle Quelldatensätze mit entsprechenden Feldergruppen definiert
- Das Feld Personen-ID ist identifiziert und steht konsistent für alle Datensätze zur Verfügung, die verbunden werden
- Identity-Namespaces werden in AEP für die Personen-ID konfiguriert, die beim Zusammenfügen von CJA-Verbindungen verwendet wird
- Die Anforderungen der Stakeholder werden dokumentiert - welche KPIs, welche Zielgruppen Dashboards nutzen werden, welcher Detaillierungsgrad
- Für mobile Scorecards: Die [!DNL Adobe Analytics] Dashboards für die beteiligten Personen sind in der mobilen App installiert
- Für Option C (Zielgruppenveröffentlichung): AEP Echtzeit-Kundenprofil ist in der Ziel-Sandbox aktiviert
- Für Option D (Geführte Analyse): CJA SKU enthält Funktionen zur geführten Analyse

## Implementierungsoptionen

In diesem Abschnitt werden die verfügbaren Implementierungsoptionen für dieses Anwendungsfallmuster beschrieben.

### Option A: Leistungsanalysen für Campaign

**Best for:** Messen und Optimieren der Kampagnen- und Journey-Effektivität - E-Mail-Kampagnen-Dashboards, Journey-funnel-Analyse, Kanalleistungsvergleich und Marketing-ROI-Reporting.

**Funktionsweise:**

Diese Option verbindet AJO-Kampagnen- und Journey-Datensätze mit CJA, konfiguriert Datenansichten mit Versand- und Interaktionsmetriken (Sendungen, Sendungen, Öffnungen, Klicks, Bounces, Abmeldungen), erstellt Kampagnenleistungs-Dashboards und veröffentlicht Scorecards für Marketing-Stakeholder. Der Schwerpunkt liegt auf dem Verständnis der Leistung von Marketing-Kampagnen über Kanäle und im Zeitverlauf.

Die Datenansicht wird mit kampagnenspezifischen Dimensionen (Kampagnenname, Journey-Name, Kanaltyp, Nachrichtenvariante) und Versandmetriken konfiguriert. Berechnete Metriken werden für abgeleitete Kennzahlen erstellt, z. B. Öffnungsrate, Clickthrough-Rate, Konversionsrate und Umsatz pro Nachricht. In Dashboards werden diese KPIs mit Vergleichszeiträumen für die Trendanalyse angezeigt.

**Wichtige Aspekte:**

- Erfordert AJO-Kampagnen- und Journey-Ereignis-Datensätze in AEP
- Attributionsmodelle sollten mit der Kampagnenmessphilosophie des Unternehmens übereinstimmen.
- Erwägen Sie, sowohl native AJO-Berichte (für operative Bereitstellungsmetriken) als auch CJA (für kanalübergreifende Geschäftsauswirkungen) einzubeziehen

**Vorteile:**

- Speziell für die Messung und Optimierung von Kampagnen entwickelt
- Aktiviert den kampagnenübergreifenden Vergleich und die Analyse des Kanal-Mix
- Berechnete Metriken bieten standardisierte KPI-Definitionen für alle Kampagnen
- Mobile Scorecards bieten Marketing-Führungskräften eine übersichtliche Leistung

**Einschränkungen:**

- Auf Kampagnen- und Journey-Daten beschränkt; bietet keinen vollständigen Kunden-Journey-Kontext
- Umfasst keine Journey-Pathing-, Fallout- oder Kohortenanalyse
- Die Attribution bezieht sich auf Kampagnen-Touchpoints und nicht auf die vollständige Kunden-Journey

**Experience League:**

- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Übersicht über Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Option B: Customer Journey Analytics

**Am besten geeignet für:** Verstehen von Cross-Channel-Kunden-Journey - Fallout-Analyse, Pfadanalyse, Kohortenbeibehaltung, Attributionsmodellierung und Lebenszyklus-Staging-Analyse über Web-, App-, E-Mail-, CRM- und Offline-Touchpoints hinweg.

**Funktionsweise:**

Diese Option verbindet mehrere AEP-Datensätze (Web-Ereignisse, App-Ereignisse, CRM-Daten, Kampagneninteraktionen, Transaktionsdatensätze), um eine einheitliche kanalübergreifende Ansicht der Kunden-Journey zu erstellen. Die Datenansicht wird mit Dimensionen und Metriken konfiguriert, die alle Kanäle umfassen. Mit den Fluss-, Fallout-, Kohorten- und Attributionsvisualisierungen von CJA wird analysiert, wie Kunden Journey durchlaufen, wo sie abbrechen, wie verschiedene Segmente beibehalten werden und welche Kanäle für Konversionen gutgeschrieben werden sollten.

Insight Dies ist die umfassendste Analysemöglichkeit, die eine umfassende Einblicke in das End-to-End-Kundenerlebnis bietet. Sie ist auch am komplexesten zu implementieren und erfordert eine sorgfältige Konfiguration der Personen-ID für die Datensatzübergreifende Zuordnung und ein durchdachtes Design der Datenansichten, um die richtigen Dimensionen und Metriken offenzulegen.

**Wichtige Aspekte:**

- Erfordert eine konsistente Personen-ID für alle verbundenen Datensätze für eine genaue kanalübergreifende Analyse
- Das Schema-Design in AEP wirkt sich direkt auf die Qualität und Tiefe der CJA-Analyse aus
- Mehr Datensätze in der Verbindung bedeuten umfassendere Analysen, aber längere Aufstockungszeiten
- Die Attributionsmodellierung erfordert klare Konversionsereignisdefinitionen

**Vorteile:**

- Vollständige kanalübergreifende Sichtbarkeit der Kunden-Journey
- Vollständige Suite von CJA-Visualisierungen: Fluss, Fallout, Kohorte, Attribution, Freiformtabellen
- Ermöglicht die Erkennung von Insights, die in Single-Channel-Reporting unsichtbar sind
- Unterstützt komplexe analytische Fragen zum Kundenverhalten und Lebenszyklus

**Einschränkungen:**

- Höhere Implementierungskomplexität aufgrund von Verbindungen mit mehreren Datensätzen und Cross-Channel-Stitching
- Erfordert eine stärkere Vorausplanung für die Konfiguration von Datenansichten und abgeleiteten Feldern
- Die Aufstockung für große Verbindungen mit mehreren Datensätzen kann Tage dauern
- Die Qualität der Analyse hängt von der Vollständigkeit und Konsistenz der zugrunde liegenden Daten ab

**Experience League:**

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Flussvisualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### Option C: Analytics mit Zielgruppenveröffentlichung

**Am besten geeignet für:** Analysis-gesteuerte Aktivierung - Entdecken Sie interessante Segmente mithilfe von CJA Analysis und veröffentlichen Sie sie dann wieder in AEP zur Aktivierung über RT-CDP-Ziele, AJO-Kampagnen oder AJO-Journey.

**Funktionsweise:**

Diese Option erweitert Option A oder Option B mit Zielgruppenveröffentlichung aus CJA. Analysten erstellen Segmente in CJA mithilfe kanalübergreifender Verhaltensdaten und der vollen Analysefähigkeit der CJA-Filter und veröffentlichen diese Zielgruppen dann im AEP Echtzeit-Kundenprofil zur nachgelagerten Aktivierung. Dadurch wird die Lücke zwischen insight und Action geschlossen - Segmente, die während der explorativen Analyse erkannt werden, werden zu verwertbaren Zielgruppen, ohne dass eine manuelle Neuerstellung in AEP Segment Builder erforderlich ist.

Veröffentlichte Zielgruppen werden im AEP-Zielgruppenportal mit dem Ursprung &quot;CJA&quot; angezeigt und können für jedes RT-CDP-Ziel aktiviert, als Kampagnenziele in AJO verwendet oder als Journey-Einstiegsbedingungen verwendet werden.

**Wichtige Aspekte:**

- Erfordert, dass AEP Echtzeit-Kundenprofil in der Ziel-Sandbox aktiviert ist
- Die CJA-Verbindung muss über eine gültige Personen-ID verfügen, die in einen AEP-Identity-Namespace aufgelöst wird
- Veröffentlichte Zielgruppen werden bei der AEP-Zielgruppenberechtigung des Unternehmens mitgezählt
- Die Aktualisierungskadenz muss entsprechend den Aktivierungsanforderungen konfiguriert werden (einmal, alle 4 Stunden, täglich, wöchentlich)

**Vorteile:**

- Schließt den Kreislauf zwischen Analyse und Aktivierung
- Ermöglicht die Erkennung hochwertiger Segmente mithilfe der kanalübergreifenden Verhaltensdaten von CJA
- In CJA definierte Zielgruppen können Dimensionen und Filter nutzen, die in AEP Segment Builder nicht verfügbar sind
- Unterstützt die iterative Verfeinerung von Zielgruppenkriterien basierend auf analytischen Einblicken

**Einschränkungen:**

- Maximal 75 veröffentlichte Zielgruppen pro CJA-Kunde
- Die erste Auswertung einer Zielgruppe kann bei großen Datensätzen bis zu 24 Stunden dauern
- In CJA veröffentlichte Zielgruppen können nicht in AEP bearbeitet werden. Änderungen müssen in CJA vorgenommen werden
- Erfordert über die grundlegende Analyse hinaus einen zusätzlichen Identity-Namespace und eine Profilkonfiguration

**Experience League:**

- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### Option D: Geführte Analyse für Produkt-Teams

**Best for:** Product Experience Insights - Funktionsübernahme, Benutzerinteraktions-Trends, Bindungsanalyse, funnel-Konversion und Versionswirkungsanalyse mithilfe der geführten Analyse-Workflows von CJA, ohne dass eine komplexe Freiform-Workspace-Projekteinrichtung erforderlich ist.

**Funktionsweise:**

Diese Option verwendet die geführte Analyse von CJA für die strukturierte, vorlagenbasierte insight-Generierung. Die geführte Analyse bietet vordefinierte Analysetypen - funnel, Trends, Kundenbindung, Benutzerwachstum, Interaktionsfrequenz, Auswirkungen auf die Veröffentlichung, erste Verwendung und Zeitleiste -, die Analysten durch einen strukturierten Workflow führen, um spezifische Produkt- und Erlebnisfragen zu beantworten. Es eignet sich ideal für Produkt-Manager und Analysten, die schnelle, fokussierte Einblicke benötigen, ohne Freiformprojekte von Grund auf neu zu erstellen.

Die Implementierung verbindet AEP-Datensätze mit CJA, konfiguriert eine Datenansicht mit Dimensionen und Metriken auf Ereignisebene und verwendet dann geführte Analyse-Workflows, um Einblicke zu generieren. Die Ergebnisse können zur weiteren Anpassung in Workspace-Projekten als Bedienfelder gespeichert werden.

**Wichtige Aspekte:**

- Geführte Analyse erfordert CJA-Produktberechtigungen, die Funktionen für geführte Analysen enthalten
- Am besten geeignet für Produkt- und Erlebnisanalysen statt für die Messung der Kampagnenleistung
- Bietet strukturierte Workflows, die für Nicht-Analyst-Benutzer leichter zugänglich sind
- Kann zur genaueren Untersuchung mit der Freiform-Workspace-Analyse kombiniert werden

**Vorteile:**

- Niedrigere Eintrittsbarriere - Strukturierte Workflows führen Benutzer durch die Analyse
- Speziell für Fragen zu Produkterlebnissen entwickelt (funnel, Kundenbindung, Wachstum, Auswirkungen)
- Schnellere Time-to-insight für häufige Analysefragen
- Gespeicherte Analysen können zusammen mit der Freiformanalyse in Workspace-Projekte eingebettet werden

**Einschränkungen:**

- Weniger flexibel als Freiform-Workspace-Analyse
- Auf die vordefinierten Analysetypen beschränkt (funnel, Trends, Kundenbindung, Wachstum, Häufigkeit, Auswirkungen, Zeitleiste)
- Segmentvergleiche unterstützen bis zu 3 Segmente gleichzeitig
- Die funnel-Analyse unterstützt maximal 15 Schritte

**Experience League:**

- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Aufbewahrungsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### Vergleich von Optionen

In der folgenden Tabelle werden die verfügbaren Implementierungsoptionen verglichen.

| Kriterien | Option A: Kampagnenleistung | Option B: Kunden-Journey | Option C: Analytics + Aktivierung | Option D: Geführte Analyse |
| --- | --- | --- | --- | --- |
| Am besten geeignet für | Messung und Optimierung von Kampagnen | Kanalübergreifendes Journey-Verständnis | Insight-gesteuerte Zielgruppenaktivierung | Einblicke in Produkterlebnisse |
| Komplexität | Low-Medium | Hoch | Hoch | Niedrig |
| Erforderliche Datensätze | AJO Campaign-/Journey-Ereignisse | Mehrere kanalübergreifende Datensätze | Wie A oder B plus Profilidentität | Ereignis-Datensätze mit Produktinteraktionen |
| Wichtige Visualisierungen | Freiformtabellen, Zusammenfassungsnummern, Trendlinien | Fluss, Fallout, Kohorte, Attribution | Wie A oder B, plus Zielgruppenveröffentlichung | Funnel, Trends, Kundenbindung, Wachstum |
| Aktivierungsfunktion | Nein (nur Reporting) | Nein (nur Reporting) | Ja (veröffentlicht Zielgruppen in AEP) | Nein (nur Reporting) |
| Zielgruppe erforderlich | Marketing-Analysten, Kampagnen-Manager | Datenanalysten, Journey-Architekten | Analysten + Aktivierungsteams | Produkt-Manager, Wachstumsanalysten |
| Verwendete CJA-Funktionen | Verbindung, Datenansicht, Workspace, Berechnete Metriken, Dashboard | Verbindung, Datenansicht, Workspace, Berechnete Metriken, Dashboard | Wie A oder B plus Zielgruppenveröffentlichung | Verbindung, Datenansicht, geführte Analyse, Dashboard |
| Zeit bis zum ersten insight | Tage | Wochen | Wochen | Stunden-Tage |

### Wählen der richtigen Option

Verwenden Sie die folgenden Anleitungen, um die Implementierungsoption auszuwählen, die Ihren Anforderungen am besten entspricht.

- **Wenn Ihr Hauptziel die Messung der Kampagneneffektivität ist** Sie AJO-Kampagnendaten in AEP übertragen haben, beginnen Sie mit **Option A**. Sie bietet die schnellste Time-to-Value für Berichte zur Marketing-Leistung.

- **Wenn Sie die vollständige Kunden-Journey** über Web-, App-, E-Mail- und Offline-Touchpoints hinweg verstehen müssen und mehrere Datensätze mit einer konsistenten Personen-ID haben, wählen Sie **Option B**. Es bietet die tiefsten analytischen Funktionen, erfordert jedoch mehr Vorabinvestitionen in die Konfiguration von Datenansichten.

- **Wenn Sie auf Einblicke reagieren möchten** indem Sie von CJA entdeckte Segmente zur Aktivierung in RT-CDP oder AJO zurück in AEP veröffentlichen, wählen Sie **Option C**. Dies erweitert Option A oder B mit Zielgruppenveröffentlichung und erfordert die Konfiguration von AEP Echtzeit-Kundenprofilen.

- **Wenn Ihr Team schnelle, strukturierte** benötigt, ohne die Komplexität von Freiform-Workspace-Projekten, und Ihre CJA-SKU eine geführte Analyse enthält, wählen Sie **Option D**. Dies ist der schnellste Weg, um spezifische Fragen zum Produkterlebnis zu beantworten.

- **Viele Unternehmen implementieren mehrere Optionen**: Option A für Kampagnen-Dashboards des Marketing-Teams, Option B für die kanalübergreifende Analyse des Analytics-Teams und Option D für Self-Service-Einblicke des Produkt-Teams. Diese Optionen nutzen dieselbe CJA-Verbindungs- und Datenansichtsinfrastruktur.

## Implementierungsphasen

In diesem Abschnitt werden die schrittweisen Implementierungsphasen für dieses Anwendungsfallmuster beschrieben.

### Phase 1: Datenverbindung

**Anwendungsfunktion:** CJA: Datenverbindung

In dieser Phase wird eine CJA-Verbindung konfiguriert, die einen oder mehrere AEP-Datensätze zur Analyse an CJA bindet. Die -Verbindung definiert, welche Datensätze in CJA einfließen, wie Ereignisse über die Personen-ID mit den Datensätzen verknüpft werden und wie Verlaufs- und Streaming-Daten aufgenommen werden. Dies ist die grundlegende Verbindung zwischen dem Data Lake von AEP und CJA.

#### Entscheidungspunkte

In dieser Phase müssen folgende Entscheidungen getroffen werden.

>[!NOTE]
>**Entscheidung: Sandbox-Auswahl in AEP**
>
>Welche AEP-Sandbox enthält die Quelldatensätze?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Produktions-Sandbox | Live-Kundendaten für Produktions-Reporting | Verwendung für Produktions-Dashboards und Stakeholder-Reporting |
>| Entwicklungs-Sandbox | Testen und Iteration vor der Produktionsbereitstellung | Für Erstkonfiguration und Validierung vor dem Weiterleiten an die Produktion verwenden |

>[!NOTE]
>**Entscheidung: Datensatzauswahl und Typenbezeichnung**
>
>Welche AEP-Datensätze sollten in der Verbindung enthalten sein, und welcher Typ sollte jeweils zugewiesen werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Ereignis-Datensätze | Verhaltensdaten mit Zeitstempel (Web-Interaktionen, App-Ereignisse, Kampagnen-Interaktionen, Transaktionen) | Zeitstempelfeld erforderlich; bildet den Kern der meisten Analysen |
>| Datensätze nachschlagen | Schlüsselwert-Referenzdaten (Produktkatalog, Kampagnenmetadaten, Speicherorte) | Mit Ereignisdaten über einen freigegebenen Schlüssel verbunden; nur der neueste Status wird verwendet. |
>| Profildatensätze | Attribute auf Personenebene (Treuestufe, Lebenszeitwert, CRM-Attribute) | Anreicherung auf Personenebene bereitstellen; nur der neueste Status wird verwendet |

>[!NOTE]
>**Entscheidung: Personen-ID-Konfiguration**
>
>Welches Feld dient als Personen-ID für die Zuordnung zwischen Datensätzen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| CRM-ID | Organisation verfügt kanalübergreifend über eine konsistente CRM-Kennung | Bietet die genaueste Cross-Channel-Zuordnung für bekannte Kunden |
>| ECID (Experience Cloud ID) | Primäres Analysieren des anonymen Web-/App-Verhaltens | Geräte-seitiger Bereich; nicht über Geräte hinweg ohne Identitätsauflösung zusammenfügen |
>| E-Mail (gehasht) | E-Mail ist die allgemeine Kennung aller Datensätze | Funktioniert gut, wenn E-Mails konsistent über Touchpoints hinweg erfasst werden |
>| Benutzerdefinierter Namespace | Organisation verwendet eine proprietäre Kennung | Muss mit einem AEP-Identity-Namespace für die Zielgruppenveröffentlichung übereinstimmen (Option C) |

>[!NOTE]
>**Entscheidung: Aufstockungsbereich**
>
>Wie viele historische Daten sollten in die Verbindung importiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Alle vorhandenen Daten | Maximale historische Tiefe, die für Vergleiche mit dem Vorjahr und langfristige Trends erforderlich ist | Die Aufstockung großer Datensätze (Milliarden von Datensätzen) kann Tage dauern |
>| Benutzerdefinierter Datumsbereich | Nur die jüngste Geschichte ist relevant, oder die Speicheroptimierung ist ein Problem | Beschränkt die für die Analyse verfügbare historische Tiefe |
>| Keine Aufstockung | Es ist nur eine vorausschauende Analyse erforderlich | Schnellste Verbindungseinrichtung; keine historischen Daten verfügbar, bis neue Daten in fließen |

>[!NOTE]
>**Entscheidung: Streaming-Aktivierung**
>
>Sollten neue Daten nahezu in Echtzeit in CJA fließen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Streaming aktivieren | Es ist ein Reporting nahezu in Echtzeit erforderlich (Daten sind innerhalb von ~90 Minuten nach der Aufnahme durch AEP verfügbar) | Am häufigsten für Produktionsverbindungen; ermöglicht zeitnahe Analysen |
>| Nur Batch | Eine regelmäßige Aktualisierung ist ausreichend und Streaming ist nicht erforderlich | Einfachere Konfiguration; Daten nach Batch-Verarbeitung verfügbar |

#### Konfigurieren der Datenverbindung

**UI-Navigation:** CJA > Verbindungen > Neue Verbindung erstellen

Wichtige Konfigurationsdetails:

- Name und Beschreibung der Verbindung sollten den Benennungskonventionen des Unternehmens entsprechen
- Die durchschnittliche Anzahl der täglichen Ereignisse wird für die Kapazitätsplanung von CJA verwendet
- Alle Datensätze in einer Verbindung müssen aus derselben AEP-Sandbox stammen
- Personen-ID-Felder müssen über alle Datensätze hinweg konsistent sein, um eine präzise Zuordnung zwischen verschiedenen Datensätzen zu ermöglichen
- Überprüfen Sie, ob das Feld Personen-ID vorhanden ist und in jedem Datensatz ausgefüllt ist, bevor Sie es zur Verbindung hinzufügen

**Dokumentation zu Experience League:**

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verwalten von Verbindungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA-Leitplanken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Phase 2: Konfiguration der Datenansicht

**Anwendungsfunktion:** CJA: Datenansichtskonfiguration

In dieser Phase wird eine Datenansicht konfiguriert, die definiert, wie Verbindungsdaten in der Analyse angezeigt werden. Die Datenansicht bestimmt, welche Schemafelder als Dimensionen und Metriken bereitgestellt werden, wie Werte zugeordnet und beibehalten werden, wie Sitzungen definiert werden und welche abgeleiteten Felder Rohdaten in analysefähige Komponenten umwandeln. Aus einer Verbindung können mehrere Datenansichten für verschiedene analytische Perspektiven erstellt werden.

#### Entscheidungspunkte

In dieser Phase müssen folgende Entscheidungen getroffen werden.

>[!NOTE]
>**Entscheidung: Container-Benennung**
>
>Welche Terminologie sollten die Container verwenden, um mit der Unternehmens-Domain abzugleichen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Standard (Person / Sitzung / Ereignis) | Das Team versteht die standardmäßige Analytics-Terminologie | Funktioniert bei den meisten Implementierungen |
>| Benutzerdefinierte Namen (z. B. Käufer/Besuch/Interaktion) | Geschäftsbereichsspezifische Terminologie verbessert die Benutzerakzeptanz | Hilft nicht-technischen Stakeholdern, den Umfang der Analyse zu verstehen |
>| B2B-Namen (z. B. Konto/Interaktion/Touchpoint) | B2B-Analyse, bei der Analyse auf Kontoebene im Mittelpunkt steht | Ausrichtung des Container-Umfangs an B2B-Geschäftskonzepten |

>[!NOTE]
>**Entscheidung: Sitzungs-Timeout**
>
>Wie lange dauert die Inaktivität, um eine Sitzungsgrenze festzulegen?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| 30 Minuten (Standard) | Standardmäßige Web Analytics-Sitzungsdefinition | Branchenstandard; entspricht den meisten Analytics-Benchmarks |
>| 15 Minuten | Kurzform-Inhalte oder Transaktions-Sites, auf denen Benutzer Aufgaben schnell erledigen können | Erstellt mehr Sitzungen; erfasst möglicherweise besser unterschiedliche Benutzerinteressen |
>| 60 Minuten oder länger | Langformatige Inhalte, komplexe B2B-Interaktionen oder forschungsintensive Journey | Weniger Sitzungen; Erfassung erweiterter Recherchen als einzelne Sitzungen |
>| Benutzerdefiniert mit neuen Sitzungsereignissen | Bestimmte Ereignisse (z. B. App-Start, Kampagnen-Clickthrough) sollten immer eine neue Sitzung starten | Bietet geschäftslogikgesteuerte Sitzungsgrenzen |

>[!NOTE]
>**Entscheidung: Attributionsmodell-Standardeinstellungen**
>
>Welches standardmäßige Attributionsmodell sollte auf Konversionsmetriken angewendet werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Letztkontakt (Standard) | Die Gutschrift sollte vor der Konversion an den letzten Touchpoint gehen. | Einfach und intuitiv; unterschätzt möglicherweise die Sensibilisierungskanäle |
>| First Touch | Zu verstehen, welche Kanäle die anfängliche Wahrnehmung und Akquise fördern | Nützlich für Akquise-Analysen; ignoriert Nurture Touchpoints |
>| Linear | Alle Touchpoints sollten gleichermaßen gutgeschrieben werden | Faire Verteilung; kann die Auswirkungen wichtiger Touchpoints vermindern |
>| Zeitverfall | Jüngste Touchpoints sollten stärker angerechnet werden als entfernte Touchpoints | Saldiert Aktualität mit historischem Beitrag |
>| U-förmig | Die ersten und letzten Touchpoints verdienen höchste Anerkennung. | Gut zum Verständnis von Akquise- und Abschlusskanälen |
>| Algorithmisch | Datengesteuerte Attribution mithilfe der KI-Modelle von CJA | Höchste Genauigkeit, aber ausreichendes Konversionsdatenvolumen erforderlich |

>[!NOTE]
>**Entscheidung: Abgeleitete Feldlogik**
>
>Sind benutzerdefinierte Geschäftsregeln erforderlich, um Rohdaten in analysefähige Dimensionen umzuwandeln?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Marketing-Kanal-Klassifizierung (wenn Fall) | Unformatierte Trackingcodes müssen in Kanalgruppen klassifiziert werden | Häufigster Anwendungsfall für abgeleitete Felder; wichtig für die Kanalanalyse |
>| Wert-Bucketing | Fortlaufende Werte müssen in Bereiche gruppiert werden (z. B. in Reihenfolgenwerten). | Vereinfacht die Analyse kontinuierlicher Metriken |
>| Zusammenführung von Feldern | Mehrere Quellfelder sollten zu einer einzigen Dimension kombiniert werden | Nützlich, wenn dasselbe Konzept in verschiedenen Schemapfaden über Datensätze hinweg vorhanden ist |
>| Regex-basierte Extraktion | Strukturierte Werte müssen analysiert werden (z. B. Extrahieren des Kampagnentyps aus dem Kampagnen-Code) | Leistungsstark, erfordert jedoch ein sorgfältiges Regex-Design |

#### Datenansicht konfigurieren

**Benutzeroberflächennavigation:** CJA > Datenansichten > Neue Datenansicht erstellen

Wichtige Konfigurationsdetails:

- Auswahl der in Phase 1 erstellten übergeordneten Verbindung
- Konfigurieren von Zeitzone und Kalendertyp entsprechend den Reporting-Anforderungen
- Zuordnen von XDM-Schemafeldern zu Dimensionen mit entsprechenden Einstellungen für Persistenz (Zuordnung und Gültigkeit)
- Zuordnen von XDM-Schemafeldern zu Metriken mit Format- (Dezimal, Ganzzahl, Währung, Prozentsatz, Zeit) und Attributionseinstellungen
- Ein-/Ausschlussregeln für Dimensionen konfigurieren, um irrelevante Werte herauszufiltern
- Aktivieren Sie bei Bedarf Metrik-Deduplizierung, um eine doppelte Zählung zu verhindern
- Erstellen abgeleiteter Felder für die Marketing-Kanal-Klassifizierung, Wert-Bucketing oder die Feldzusammenführung
- Maximal 5.000 Dimensionen und 5.000 Metriken pro Datenansicht
- Maximal 100 abgeleitete Felder pro Datenansicht

#### Wo die Optionen auseinander gehen

**Für Option A (Campaign-Leistungsanalyse):**

Kampagnenspezifische Dimensionen zuordnen: Kampagnenname, Journey-Name, Kanaltyp, Nachrichtenvariante, Betreffzeile. Versandmetriken zuordnen: Sendungen, Sendungen, Öffnungen, Klicks, Bounces, Abmeldungen. Konfigurieren der Attribution auf Konversionsmetriken basierend auf der Messphilosophie der Kampagne.

**Für Option B (Kunden-Journey-Analyse):**

Cross-Channel-Dimensionen zuordnen: Seitenname, App-Bildschirm, Kanal, Kampagne, Produkt, Content-Typ. Ordnen Sie Interaktions- und Konversionsmetriken kanalübergreifend zu. Konfigurieren Sie mehrere Attributionsmodelle für die Vergleichsanalyse. Abgeleitete Felder zur Kanalklassifizierung und Journey-Stadienidentifizierung erstellen.

**Für Option D (Geführte Analyse):**

Ordnen Sie für die Analyse von Produkterlebnissen relevante Dimensionen und Metriken auf Ereignisebene zu: Funktionsname, Benutzeraktion, Interaktionstyp. Konzentrieren Sie sich auf Ereignisse, die funnel-Schritte, Aufbewahrungskriterien und Wachstumssignale definieren.

**Dokumentation zu Experience League:**

- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Komponenteneinstellungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistenzeinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributionseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Formateinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplizierung der Metrik](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Werte ein-/ausschließen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Sitzungseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Abgeleitete Felder](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Phase 3: Analyse und Erstellung von Metriken

**Anwendungsfunktion:** CJA: Workspace Analysis, CJA: Geführte Analyse, CJA: Erstellung berechneter Metriken

In dieser Phase werden die Analyse-Arbeitsbereiche (Freiformprojekte oder geführte Analysen), berechnete Metriken für abgeleitete KPIs, Filter für die segmentierte Analyse und Anmerkungen für wichtige Ereignisse erstellt. Hier wird der analytische Wert realisiert - durch den Aufbau der Tabellen, Visualisierungen und Metriken, die geschäftliche Fragen beantworten.

#### Entscheidungspunkte

In dieser Phase müssen folgende Entscheidungen getroffen werden.

>[!NOTE]
>**Entscheidung: Analyseverfahren**
>
>Sollte diese Analyse Freiform-Workspace-Projekte oder angeleitete Analyse-Workflows verwenden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Freiform-Workspace (Optionen A, B, C) | Tiefe explorative Analyse, benutzerdefinierte Layouts, komplexe Aufschlüsselungen, erweiterte Visualisierungen | Maximale Flexibilität; erfordert Analyst-Fähigkeiten; unterstützt alle Visualisierungstypen |
>| Geführte Analyse (Option D) | Strukturierte Produkteinblicke, schnelle Antworten auf spezifische Fragen, weniger technische Anwender | Schnellere Time-to-insight; auf vordefinierte Analysetypen beschränkt; Speicherung in Workspace zur weiteren Anpassung |
>| Beide | Die Organisation benötigt sowohl tiefe Analysen als auch schnelle strukturierte Einblicke | Geführte Analyse für häufige Fragen verwenden; Workspace für gründliche Untersuchung |

>[!NOTE]
>**Entscheidung: Visualisierungstypen**
>
>Welche Visualisierungen vermitteln die Einblicke für diesen Anwendungsfall am besten?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Freiformtabelle | Detaillierte Datenexploration mit Dimensionsaufschlüsselungen | Grundlage der meisten Analysen; unterstützt bis zu 10 Aufschlüsselungsebenen |
>| Flussvisualisierung | Grundlegendes zum Pfadverhalten (Seitenfluss, Kanalübergänge) | Hervorragend für die Journey-Pfadsuche geeignet; kann komplex sein und eine hohe Kardinalität aufweisen |
>| Fallout-Visualisierung | Konversionsmessung über eine definierte Folge von Touchpoints | Optimiert für die funnel-Analyse; zeigt Abbruch bei jedem Schritt deutlich an |
>| Kohortentabelle | Bindungsanalyse im Zeitverlauf nach Akquise-Kohorte | Zeigt, wie gut verschiedene Gruppen beibehalten werden; wichtig für die Lebenszyklusanalyse |
>| Attributionsbedienfeld | Attributionsmodelle für Konversionsmetriken vergleichen | Paralleler Modellvergleich; erfordert eine klare Definition des Konversionsereignisses |
>| Zusammenfassungsnummer/Änderung | Anzeige von Executive-KPIs mit Vergleich der Zeiträume | Saubere, übersichtliche Anzeige von Metriken; ideal für Dashboard-Kopfzeilen |

>[!NOTE]
>**Entscheidung: Formeln für berechnete Metriken**
>
>Welche geschäftlichen KPIs erfordern berechnete Metriken, die über die grundlegenden Datenansichtsmetriken hinausgehen?
>
>| Metrikmuster | Formelbeispiel | Verwendungszeitpunkt |
>| --- | --- | --- |
>| Verhältnis/Rate | Bestellungen/Besuche | Konversionsrate, Clickthrough-Rate, Bounce-Rate |
>| Gefilterte Metrik | Umsatz (wobei Kanal = „E-Mail„) | Kanalspezifische oder segmentspezifische Maßnahmen |
>| Durchschnitt pro Element | Umsatz/Bestellungen | Durchschnittlicher Bestellwert, Umsatz pro Besuch |
>| Zusammengesetzte Formel | (Umsatz - Kosten)/Umsatz | Spanne in Prozent, ROI-Berechnungen |
>| Interaktionsbewertung | Gewichtete Summe der Interaktionen | Zusammengesetzte Interaktionsbewertung über Kanäle hinweg |

#### Konfigurieren von Analysen und Metriken

**Navigation in der Benutzeroberfläche:**

- Workspace: CJA > Workspace > Projekte > Projekt erstellen > Leeres Projekt
- Geführte Analyse: CJA > Startseite > Geführte Analyse (oder Workspace > Erstellen > Geführte Analyse)
- Berechnete Metriken: CJA > Komponenten > Berechnete Metriken > Erstellen
- Filter: CJA > Komponenten > Filter > Filter erstellen

Wichtige Konfigurationsdetails:

- Wählen Sie die in Phase 2 erstellte Datenansicht als Projektdatenansicht aus
- Legen Sie die entsprechenden Datumsbereiche und Vergleichszeiträume für die Analyse fest
- Erstellen von Freiformtabellen durch Ziehen von Dimensionen in Zeilen und Metriken in Spalten
- Fügen Sie Dimensionsaufschlüsselungen hinzu, um Daten auf tieferen Ebenen zu untersuchen (z. B. Kanal für Kampagne, Seite für Produkt)
- Erstellen wiederverwendbarer Filter (Segmente) für die zielgruppenspezifische Analyse (Bereich auf Personen-, Sitzungs- oder Ereignisebene)
- Fügen Sie Anmerkungen hinzu, um wichtige Geschäftsereignisse (Produkteinführungen, Kampagnen, Vorfälle) zu markieren
- Festlegen des Formats der berechneten Metrik (Dezimalzahl, Prozentsatz, Währung, Zeit) und der Polarität (Aufwärts ist gut / Aufwärts ist schlecht)
- Freigeben von Arbeitsbereich-Projekten für CJA-Benutzende mit Anzeige- oder Bearbeitungsberechtigungen

#### Wo die Optionen auseinander gehen

**Für Option A (Campaign-Leistungsanalyse):**

Erstellen Sie Freiformtabellen mit Kampagnendimensionen, die nach Versand- und Interaktionsmetriken aufgeschlüsselt sind. Erstellen Sie berechnete Metriken für Öffnungsrate, Clickthrough-Rate, Konversionsrate, Umsatz pro Nachricht und Kampagnen-ROI. Hinzufügen von Trend-Visualisierungen zur Verfolgung der Kampagnenleistung im Zeitverlauf. Vergleichen von Kampagnenvarianten mit dem Segmentvergleich.

**Für Option B (Kunden-Journey-Analyse):**

Erstellen Sie Fallout-Visualisierungen zur Identifizierung von Journey-Abfallpunkten. Erstellen Sie Flussvisualisierungen, um Navigationsmuster über Kanäle hinweg zu entdecken. Erstellen Sie Kohortentabellen, um die Kundenbindung nach Akquise-Kohorte zu messen. Konfigurieren Sie das Attributionsbedienfeld, um Attributionsmodelle für Konversionsmetriken zu vergleichen. Erstellen Sie berechnete Metriken für die Journey-Abschlussrate, den Cross-Channel-Interaktionswert und die Konversion der Lebenszyklusphase.

**Für Option C (Analytics mit Zielgruppenveröffentlichung):**

Erstellen Sie die Analyse-Arbeitsbereiche aus Option A oder B und identifizieren Sie dann während der Analyse Segmente mit hohem Wert oder geringer Leistung. Erstellen Sie CJA-Filter, die diese Segmente für die Veröffentlichung in Phase 5 erfassen.

**Für Option D (Geführte Analyse):**

Wählen Sie den entsprechenden Typ der geführten Analyse basierend auf der Geschäftsfrage aus. Konfigurieren Sie wichtige Ereignisse, Datumsbereiche, Zählmethoden und Segmentvergleiche. Speichern Sie abgeschlossene Analysen als Bedienfelder in Workspace-Projekten zur weiteren Anpassung.

**Dokumentation zu Experience League:**

- [Übersicht über Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen eines Projekts](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freiformtabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flussvisualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Aufschlüsselungsdimensionen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Übersicht über Filter](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Erstellen von Filtern](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Anmerkungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berechnete Metriken erstellen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funktionen für berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trend-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Aufbewahrungsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Aktive Wachstumsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Interaktionsfrequenzansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Ansicht der Auswirkungen der Version](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/de/docs/analytics-platform/using/content-analytics/content-analytics)

### Phase 4: Dashboard-Veröffentlichung

**Anwendungsfunktion:** CJA: Dashboard- und Scorecard-Veröffentlichung

In dieser Phase werden interaktive Dashboards (Workspace-Projekte) und mobile Scorecards erstellt, die den Stakeholdern KPI-Sichtbarkeit bieten. Dashboards bieten Executive- und operative Sichtbarkeit durch Zusammenfassungszahlen, Trendlinien, Aufschlüsselungen und Anmerkungen. Mobile Scorecards liefern Leistungsdaten auf einen Blick über die Mobile App von [!DNL Adobe Analytics] Dashboards.

#### Entscheidungspunkte

In dieser Phase müssen folgende Entscheidungen getroffen werden.

>[!NOTE]
>**Entscheidung: Dashboard-Typ**
>
>Handelt es sich um ein Desktop-Workspace-Dashboard, eine mobile Scorecard oder um beides?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Workspace-Projekt (Desktop) | Detaillierte interaktive Dashboards für Analysten und Marketing-Experten | Vollständige Visualisierungsfunktionen; unterstützt Bedienfelder, Tabellen und komplexe Layouts |
>| Mobile Scorecard | Übersichtliche KPIs für Führungskräfte und Stakeholder auf Mobilgeräten | Auf 16 Kacheln begrenzt; Zusammenfassungszahlen mit Trend-Sparklines; erfordert Mobile App |
>| Beide | Das Unternehmen benötigt sowohl detaillierte Analysen als auch mobile Berichte auf Führungsebene | Trennen Sie Artefakte, aber Sie können dieselbe Datenansicht und berechnete Metriken verwenden. |

>[!NOTE]
>**Entscheidung: Modell zur gemeinsamen Nutzung**
>
>Wer sollte das Dashboard erhalten und wie?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Für bestimmte Benutzer freigeben | Eingeschränkte Zielgruppe mit spezifischen Zugriffsanforderungen | Detaillierteste Steuerung; erfordert individuelle Benutzerverwaltung |
>| Für Produktprofilgruppe freigeben | Zugriff auf Team-Ebene entsprechend den Rollen der Organisation | Effizient für die teamweite Verteilung; über CJA-Produktprofile verwaltet |
>| E-Mail-Versand planen | Wiederkehrende PDF-/CSV-Berichte für Stakeholder, die sich nicht bei CJA anmelden | Automatisierter Versand; maximale Häufigkeit ist stündlich; PDF- und CSV-Formate |

>[!NOTE]
>**Entscheidung: Sichtbarkeit von Anmerkungen**
>
>Sollen Schlüsselereignisse in Dashboard-Trendlinien kommentiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Ja - Anmerkungen erstellen | Größere Kampagnen, Produkteinführungen, Site-Vorfälle oder saisonale Ereignisse können die Datentrends erklären | Anmerkungen werden als Markierungen in Liniendiagrammen und Scorecard-Trends angezeigt. Stellen Sie den Kontext für Datenspitzen oder Tiefpunkte bereit. |
>| Nein | Die Dashboard-Zielgruppe ist mit dem Geschäftskontext vertraut, und Anmerkungen würden für Unordnung sorgen | Einfachere visuelle Darstellung |

#### Konfigurieren von Dashboards

**Navigation in der Benutzeroberfläche:**

- Workspace-Dashboards: CJA > Workspace > Projekt erstellen
- Mobile Scorecards: CJA > Projekte > Erstellen > Mobile Scorecard
- Freigabe: CJA > Workspace > Freigeben > Für Workspace-Benutzende freigeben
- Geplanter Versand: CJA > Workspace > Freigeben > Projekt planen

Wichtige Konfigurationsdetails:

- Erstellen Sie für mobile Scorecards Kacheln mit einer einzelnen Metrik und einer Zusammenfassungsnummer sowie einem Sparkline-Trend
- Konfigurieren Sie standardmäßige Datumsbereiche und Vergleichszeiträume (z. B. letzte 30 Tage im Vergleich zum vorherigen Zeitraum oder Monat für Monat)
- Hinzufügen von Filtern für die Zielgruppe, die Führungskräfte in mobilen Scorecards umschalten können
- Konfigurieren des geplanten E-Mail-Versands für wiederkehrende PDF- oder CSV-Berichte
- Maximal 16 Kacheln pro mobile Scorecard; maximal 15 Bedienfelder pro Workspace-Projekt
- Anmerkungen sind auf 100 pro Datenansicht beschränkt

**Dokumentation zu Experience League:**

- [Erstellen einer mobilen Scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Scorecards konfigurieren und kuratieren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-Dashboards - Leitfaden für Führungskräfte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Freigeben von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planen von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Visualisierung der Zusammenfassungszahl](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [Datumsbereiche](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### Phase 5: Zielgruppenveröffentlichung (nur Option C)

**Anwendungsfunktion:** CJA: Zielgruppenveröffentlichung

In dieser Phase wird die CJA-Zielgruppenveröffentlichung konfiguriert, um von der Analyse erkannte Segmente zurück an das AEP-Echtzeit-Kundenprofil zu pushen, damit sie nachgelagert in RT-CDP-Zielen, AJO-Kampagnen oder AJO-Journey aktiviert werden können.

#### Entscheidungspunkte

In dieser Phase müssen folgende Entscheidungen getroffen werden.

>[!NOTE]
>**Entscheidung: Aktualisierungskadenz**
>
>Wie oft sollte die Zielgruppenzugehörigkeit aktualisiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einmalig (Momentaufnahme) | Kampagnenspezifische Zielgruppe, die nicht fortlaufend aktualisiert werden muss | Keine laufende Verarbeitung; muss für Aktualisierungen erneut veröffentlicht werden |
>| Alle 4 Stunden | Anforderungen an die Fast-Echtzeit-Aktivierung | Höhere Verarbeitungskosten; am besten geeignet für zeitkritische Zielgruppen |
>| Täglich | Standard-Marketing-Aktivierungskadenz | Ausgewogene Frische und Kosten; häufigste Wahl |
>| Wöchentlich | Stabile, sich langsam ändernde Zielgruppen | Minimale Verarbeitung; geeignet für langfristige Segmente |

>[!NOTE]
>**Entscheidung: Identity-Namespace**
>
>Welchen Identity-Namespace sollte CJA für die Auflösung von Zielgruppenmitgliedern verwenden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| CRM-ID | Primäre Kundenkennung der Organisation | Beste Genauigkeit beim bekannten Kundenabgleich |
>| ECID | Hauptsächlich Web-/App-basierte Zielgruppen | Gerätebezogen; wird möglicherweise nicht auf alle Profildatensätze aufgelöst |
>| E-Mail (gehasht) | Die allgemeine Kennung für die Aktivierung ist E-Mail | Muss mit dem in der AEP-Identitätskonfiguration verwendeten Namespace übereinstimmen |
>| Benutzerdefinierter Namespace | Im gesamten Unternehmen verwendete proprietäre Kennung | Muss im AEP Identity Service konfiguriert werden |

#### Zielgruppenveröffentlichung konfigurieren

**Benutzeroberflächennavigation:** CJA > Komponenten > Zielgruppen > Zielgruppe veröffentlichen

Wichtige Konfigurationsdetails:

- Definieren von Zielgruppenkriterien mithilfe von CJA-Filtern (Container-Umfang für Person, Sitzung oder Ereignis)
- Datenansicht und Filter zur Veröffentlichung auswählen
- Konfigurieren des Identity-Namespace für die AEP-Profilauflösung
- Festlegen der Aktualisierungskadenz basierend auf den Aktivierungsanforderungen
- Überwachen des Veröffentlichungsstatus in der CJA-Zielgruppenliste (Spalte Komponenten > Zielgruppen > Status )
- Überprüfen, ob die Zielgruppe im AEP-Zielgruppenportal angezeigt wird (Zielgruppen > Durchsuchen > Nach Herkunft filtern &quot;CJA„)
- Maximal 75 veröffentlichte Zielgruppen pro CJA-Kunde (über alle Sandboxes hinweg)
- Die erste Auswertung einer Zielgruppe kann bei großen Datensätzen bis zu 24 Stunden dauern

**Dokumentation zu Experience League:**

- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Verwalten von Audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [Zielgruppen-Portal - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## Überlegungen bei der Implementierung

In diesem Abschnitt werden Leitplanken, häufige Fallstricke, Best Practices und Entscheidungen bei der Abwägung für dieses Anwendungsfallmuster behandelt.

### Leitplanken und Beschränkungen

Die folgenden Leitplanken und Einschränkungen gelten für diese Implementierung.

- **Verbindungsbeschränkungen:** Die maximale Anzahl von Verbindungen pro Organisation ist durch die CJA SKU-Berechtigung begrenzt. Eine einzelne Verbindung kann Datensätze aus nur einer AEP-Sandbox enthalten. — [CJA-Leitplanken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **Datenansichtsbeschränkungen:** Maximal 5.000 Dimensionen und 5.000 Metriken pro Datenansicht. Maximal 100 abgeleitete Felder pro Datenansicht mit bis zu 5 Ebenen verschachtelter Funktionen.
- **Workspace-Beschränkungen:** Maximal 40 Bedienfelder pro Projekt. Freiformtabellen unterstützen Aufschlüsselungen von bis zu 10 Dimensionen. Maximal 50.000 Zeilen pro Berichtsanfrage.
- **Scorecard-Beschränkungen:** Maximal 16 Kacheln pro mobiler Scorecard.
- **Streaming-Latenz:** Streaming-Daten sind in der Regel innerhalb von 90 Minuten nach der Aufnahme in AEP in CJA verfügbar.
- **Zielgruppenveröffentlichungsbeschränkungen:** Maximal 75 veröffentlichte Zielgruppen pro CJA-Kunde. Die minimale Aktualisierungskadenz beträgt alle 4 Stunden.
- **Geführte Analyse-Limits** Die Funnel-Analyse unterstützt maximal 15 Schritte. Segmentvergleiche unterstützen bis zu 3 Segmente gleichzeitig.

### Häufige Fehler

Beachten Sie bei der Implementierung dieses Musters die folgenden häufigen Probleme.

- **Personen-ID stimmt nicht über Datensätze hinweg überein:** Alle Datensätze in einer Verbindung müssen ein konsistentes Personen-ID-Feld für die Analyse von datensatzübergreifenden Datensätzen verwenden. Nicht übereinstimmende Personen-IDs führen zu fragmentierten Kundenansichten, bei denen dieselbe Person als mehrere Personen angezeigt wird. Überprüfen Sie die Konsistenz der Personen-ID, bevor Sie die Verbindung erstellen.

- **Aufstockung dauert unerwartet lange:** Aufstockung großer Datensätze mit Milliarden von Datensätzen kann Tage dauern. Planen Sie dies während der Implementierungszeitpläne ein und starten Sie die Aufstockung frühzeitig. Überwachen Sie den Fortschritt in der Ansicht „Verbindungsdetails“.

- **Datenansicht, die für die meisten Dimensionswerte „Nicht angegeben“ anzeigt:** Das zugeordnete Schemafeld ist in den Quelldaten möglicherweise dünn befüllt. Prüfen Sie den Quelldatensatz auf Datenqualität, bevor Sie von einem Konfigurationsfehler ausgehen. Erwägen Sie die Verwendung eines abgeleiteten Felds zur Verarbeitung von Nullwerten.

- **Die Anzahl der Sitzungen scheint falsch zu sein:** Einstellungen für Sitzungs-Timeouts wirken sich erheblich auf sitzungsbezogene Metriken aus. Eine sehr kurze Zeitüberschreitung führt zu mehr Sitzungen. Eine sehr lange Zeitüberschreitung führt zu weniger Sitzungen. Durch neue Sitzungsstartereignisse können Sitzungen auch unerwartet fragmentiert werden. Überprüfen und testen Sie die Sitzungseinstellungen auf bekannte Benutzerverhaltensmuster.

- **Attributionsmodell wird nicht wie erwartet angewendet** Attributionsmodelle gelten nur für Metriken, nicht für Dimensionen. Stellen Sie sicher, dass das Lookback-Fenster für den Geschäftszyklus geeignet ist. In kurzen Lookback-Fenstern fehlen möglicherweise frühzeitige funnel-Touchpoints.

- **Berechnete Metriken, die Nullen oder unerwartete Werte zurückgeben:** Stellen Sie sicher, dass die Basismetriken, auf die in der Formel verwiesen wird, Daten in der Zieldatenansicht für den ausgewählten Datumsbereich enthalten. Auf Division durch Null in Verhältnismetriken prüfen. Rufen Sie die Metrikdefinition ab und überprüfen Sie die Formelstruktur.

- **Zielgruppenveröffentlichung schlägt fehl (Option C):** Die CJA-Verbindung muss über eine gültige Personen-ID verfügen, die in einen AEP-Identity-Namespace aufgelöst wird. Überprüfen Sie die Konfiguration des Identity-Namespace und stellen Sie sicher, dass das Echtzeit-Kundenprofil von AEP in der Ziel-Sandbox aktiviert ist.

### Best Practices

Befolgen Sie diese Best Practices für eine erfolgreiche Implementierung.

- **Mit einer einzigen, umfassenden Verbindung beginnen** Erstellen Sie eine Verbindung, die alle relevanten Datensätze enthält, und erstellen Sie dann mehrere Datenansichten für verschiedene analytische Perspektiven. Dies vermeidet eine Überlastung der Verbindungswege und vereinfacht die Verwaltung.

- **Verwenden abgeleiteter Felder für die Marketing-Kanal-Klassifizierung:** Erstellen Sie abgeleitete Felder mit Case When-Logik, um Traffic in Marketing-Kanäle zu klassifizieren, anstatt sich auf unformatierte Trackingcodes zu verlassen. Dadurch wird ein konsistentes kanalübergreifendes Reporting für alle Analysen sichergestellt.

- **Metrikwörterbuch erstellen:** Dokumentieren Sie alle berechneten Metriken mit ihren Formeln, dem Verwendungszweck und den erwarteten Wertebereichen. Geben Sie dieses Wörterbuch für das Analyse-Team frei, um eine projektübergreifende konsistente Verwendung von Metriken sicherzustellen.

- **Datenansichten für Ihre Audience entwerfen:** Erstellen Sie separate Datenansichten für verschiedene Stakeholder-Gruppen - eine Marketing-Datenansicht mit kampagnenfokussierten Dimensionen und Metriken und eine Produktdatenansicht mit Funktions- und Interaktionsdimensionen. Dadurch werden die Komponentenlisten für jede Benutzergruppe vereinfacht.

- **Alles kommentieren:** Erstellen Sie Anmerkungen für Kampagnenstarts, Site-Änderungen, technische Vorfälle, die Saisonabhängigkeit und jedes Ereignis, das Datentrends erklären könnte. Anmerkungen bieten einen wichtigen Kontext, wenn Dashboards Monate später überprüft werden.

- **Testen berechneter Metriken anhand manueller Berechnungen:** Führen Sie vor der Verwendung einer berechneten Metrik für Dashboards einen Bericht mit der berechneten Metrik und ihren Basiskomponenten nebeneinander aus. Überprüfen Sie, ob die berechneten Werte mit einer manuellen Berechnung übereinstimmen.

- **Filter strategisch verwenden:** Erstellen wiederverwendbarer Filter für gängige Segmentierungsmuster (neu vs. wiederkehrend, mobil vs. Desktop, nach Geografie). Wenden Sie diese als Filter auf Bereichsebene an, anstatt sie in jede Freiformtabelle einzubetten.

- **Verbindungszustand regelmäßig überwachen:** Überprüfen Sie die Ansicht „Verbindungsdetails“ auf übersprungene Datensätze, fehlgeschlagene Batches und Streaming-Verzögerungen. Probleme mit der Datenqualität auf Verbindungsebene wirken sich auf alle nachgelagerten Analysen aus.

### Entscheidungen über Kompromisse

Beachten Sie bei der Planung Ihrer Implementierung die folgenden Kompromisse.

>[!NOTE]
>**Kompromiss: Analysetiefe vs. Zeit bis zur insight**
>
>Option B (Customer Journey Analytics) bietet die tiefsten kanalübergreifenden Einblicke, erfordert jedoch erhebliche Vorabinvestitionen in die Verbindungskonfiguration, das Design von Datenansichten und die Erstellung abgeleiteter Felder. Option D (Geführte Analyse) ermöglicht eine schnellere insight-Einführung mit strukturierten Workflows, bietet jedoch weniger Flexibilität bei der Analyse.
>
>- **Option B bevorzugt:** Umfassendes Verständnis, komplexe Multi-Channel-Analyse, Attributionsmodellierung, benutzerdefinierte KPI-Entwicklung
>- **Option D bevorzugt:** Geschwindigkeit, Barrierefreiheit für Nicht-Analyst-Benutzer, Fragen zum strukturierten Produkterlebnis
>- **Empfehlung:** Mit Option D beginnen, um sofortige Produkteinblicke zu erhalten, während die Option B-Infrastruktur parallel aufgebaut wird. Viele Unternehmen führen beide gleichzeitig für verschiedene Teams aus.

>[!NOTE]
>**Kompromiss: Vollständigkeit der Aufstockung vs. Verbindungsbereitschaft**
>
>Der Import aller historischen Daten bietet die maximale Analysetiefe für Jahresvergleiche und langfristige Trendanalysen, aber die Aufstockung großer Datensätze kann Tage dauern. Durch das Beschränken der Aufstockung auf einen aktuellen Zeitraum wird die Verbindung schneller hergestellt, aber die historische Analyse wird eingeschränkt.
>
>- **Alle Daten:** Langfristige Trendanalyse, Jahresvergleiche, Kohortenanalyse mit erweiterter Historie
>- **Begrenzte Vorteile bei der Aufstockung:** Schnellere Verbindungsbereitschaft, kürzere Zeit bis zum ersten Dashboard, Speicheroptimierung
>- **Empfehlung:** Aufstockung aller Daten für Produktionsverbindungen, die die strategische Analyse unterstützen. Verwenden Sie eingeschränkte Aufstockung für Entwicklungsverbindungen und Implementierungen von Machbarkeitsstudien.

>[!NOTE]
>**Kompromiss: Eine umfassende Datenansicht im Vergleich zu mehreren fokussierten Datenansichten**
>
>Eine einzelne Datenansicht mit allen Dimensionen und Metriken bietet einen einheitlichen analytischen Arbeitsbereich, kann Benutzer jedoch mit Komponentenlisten überfordern. Mehrere fokussierte Datenansichten (eine pro Team oder Anwendungsfall) vereinfachen das Komponenten-Erlebnis, erfordern jedoch die Pflege mehrerer Konfigurationen.
>
>- **Bevorzugung einzelner Datenansichten** Einheitliche Analyse, Domain-übergreifende Aufschlüsselung, einfacheres Management
>- **Bevorzugung mehrerer Datenansichten:** Komponentenlisten, teamspezifische Terminologie, verschiedene Sitzungsdefinitionen pro Anwendungsfall
>- **Empfehlung** Beginnen Sie mit einer primären Datenansicht und erstellen Sie dann zusätzliche fokussierte Datenansichten, wenn die Komplexität der Komponentenliste zu einem Hindernis für die Einführung wird. Alle Datenansichten können auf dieselbe Verbindung verweisen.

>[!NOTE]
>**Kompromiss: Echtzeit-Streaming vs. Batch-Aufnahme**
>
>Durch die Aktivierung von Streaming über die CJA-Verbindung werden nahezu Echtzeitdaten bereitgestellt (innerhalb von ca. 90 Minuten nach der AEP-Aufnahme), Daten werden jedoch fortlaufend verarbeitet. Die Batch-Aufnahme verarbeitet Daten regelmäßig und kann zu Verzögerungen führen.
>
>- **Streaming-Vorteile:** Zeitnahes Reporting, Überwachung aktiver Kampagnen, nahezu in Echtzeit ausgeführte Dashboards
>- **Nur-Batch-Vorteile:** Einfachere Konfiguration, vorhersehbare Verarbeitungsfenster, ausreichend für wöchentliche oder monatliche Berichte
>- **Empfehlung:** Aktivieren von Streaming für Produktionsverbindungen. Die inkrementellen Verarbeitungskosten sind minimal im Vergleich zum Wert zeitnaher Daten für die aktive Kampagnenüberwachung und die operativen Dashboards.

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten zusätzliche Informationen zu diesem Anwendungsfallmuster.

### [!DNL Customer Journey Analytics] - Erste Schritte

- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA-Leitplanken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Verbindungen

- [Verbindungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Erstellen oder Bearbeiten einer Verbindung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verwalten von Verbindungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### Datenansichten

- [Übersicht über Datenansichten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Datenansicht erstellen oder bearbeiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Komponenteneinstellungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistenzeinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributionseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Formateinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Deduplizierung der Metrik](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Werte ein-/ausschließen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Sitzungseinstellungen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Abgeleitete Felder](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace und Analyse

- [Übersicht über Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Erstellen eines Projekts](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Freiformtabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Flussvisualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Fallout-Visualisierung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Kohortentabelle](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Attributionsbedienfeld](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Aufschlüsselungsdimensionen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Freigeben von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Planen von Projekten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Exportübersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Geführte Analyse

- [Geführte Analyse - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trend-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Interaktionsfrequenzansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Aufbewahrungsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Aktive Wachstumsansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Ansicht der Auswirkungen der Version](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Auswirkungsansicht für erste Verwendung](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Zeitleisten-Ansicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Komponenten

- [Übersicht über Filter](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Erstellen von Filtern](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Übersicht über berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berechnete Metriken erstellen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Funktionen für berechnete Metriken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Anmerkungen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Datumsbereiche](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Metrikkomponente](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Zielgruppenveröffentlichung

- [Zielgruppen - Übersicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Erstellen und Veröffentlichen von Zielgruppen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Verwalten von Audiences](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### Inhaltsanalyse

- [Content Analytics](https://experienceleague.adobe.com/de/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics-Konfiguration](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboards und Scorecards

- [Erstellen einer mobilen Scorecard](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Scorecards konfigurieren und kuratieren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-Dashboards - Leitfaden für Führungskräfte](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualisierung der Zusammenfassungszahl](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP Foundations

- [Übersicht über Datensätze](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Zielgruppen-Portal - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### Berichtsintegration für AJO

- [Handbuch zur Integration von AJO und CJA](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [E-Mail-Bericht zu Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [Journey Email Report](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Tutorials und Handbücher

- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
