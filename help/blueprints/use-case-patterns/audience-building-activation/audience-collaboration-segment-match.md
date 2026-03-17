---
title: Zielgruppen-Collaboration mit Segment Match
description: Erfahren Sie, wie Sie Zielgruppensegmente mithilfe von Segment Match in Sandboxes oder Organisationen freigeben und abgleichen können.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6238'
ht-degree: 1%

---


# Audience-Zusammenarbeit mit Segment Match

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für die Zusammenarbeit mit Zielgruppen unter Verwendung von [!DNL Segment Match] in [!DNL Real-Time CDP] und [!DNL Adobe Experience Platform]. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die Zielgruppensegmente über Sandboxes oder Organisationen hinweg auf datenschutzsichere Weise freigeben und abgleichen müssen.

Verwenden Sie diesen Plan, um die verfügbaren Ansätze zu verstehen, Kompromisse zu bewerten und [!DNL Adobe Experience League] für detaillierte Konfigurationsanweisungen zu navigieren.

[!DNL Segment Match] können zwei oder mehr [!DNL Experience Platform] (oder Sandboxes innerhalb einer Organisation) an Zielgruppendaten zusammenarbeiten, indem Informationen zur Segmentzugehörigkeit freigegeben werden, ohne die zugrunde liegenden personenbezogenen Daten offenzulegen. Die Teilnehmer können Überschneidungen schätzen, Audiences freigeben und übereinstimmende Profile für nachgelagerte Ziele aktivieren.

## Anwendungsfall - Übersicht

Unternehmen müssen in zunehmendem Maße mit Partnern, Tochtergesellschaften oder über Geschäftsbereiche hinweg an Zielgruppendaten zusammenarbeiten, während gleichzeitig strenge Datenschutzkontrollen beibehalten werden. Die Zusammenarbeit mit Zielgruppen erfüllt diese Anforderung, indem sie die sichere Segmentfreigabe über [!DNL Segment Match] ermöglicht - eine Funktion in [!DNL Real-Time CDP], mit der zwei oder mehr [!DNL Experience Platform] Organisationen (oder Sandboxes) Informationen über die Zielgruppenzugehörigkeit mithilfe von gehashten, datenschutzsicheren Kennungen austauschen können.

Das Geschäftsszenario umfasst in der Regel eine Organisation (den Absender), die ein wertvolles Zielgruppensegment erstellt hat und dieses für eine Partnerorganisation (den Empfänger) freigeben möchte, um es gemeinsam anzusprechen, zu unterdrücken oder anzureichern. Vor der Freigabe können beide Parteien die Zielgruppenüberschneidung schätzen, um den Wert zu bewerten. Nach der Freigabe kann die empfangende Organisation die übereinstimmende Zielgruppe über ihre eigenen Ziele aktivieren.

Dieses Muster unterscheidet sich von der standardmäßigen Zielgruppenaktivierung, da es zwischen Organisationen oder Sandboxes und nicht zu externen Werbe- oder Marketing-Zielen funktioniert. Es unterscheidet sich auch von Data Clean Rooms oder Kollaborationsplattformen von Drittanbietern, da es nativ innerhalb des Adobe-Ökosystems unter Verwendung [!DNL Experience Platform] Identitätsinfrastruktur betrieben wird.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Neue Kunden gewinnen

Erweitern Sie den Kundenstamm durch zielgerichtete Akquise-Kampagnen, Lookalike-Zielgruppen und Paid-Media-Optimierung. Die Zusammenarbeit mit Zielgruppen ermöglicht es Unternehmen, neue Interessentenpools zu entdecken, indem sie ihre Segmente mit den Partnerzielgruppen abgleichen, hochwertige Überschneidungen identifizieren und neue Kunden durch gemeinsame Aktivierung erreichen.

- **KPIs:** Neukunden, Kosten für Kundenakquise, Interessenten-/Lead-Konversion
- [Neue Kunden gewinnen](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Reduzierung der Kosten für die Kundenakquise

Verbessern Sie die Targeting-Effizienz, unterdrücken Sie Bestandskunden von Akquise-Kampagnen und optimieren Sie die Medienausgaben. Durch die gemeinsame Nutzung von Unterdrückungssegmenten in Unternehmen oder Geschäftsbereichen können Teams verschwendete Ausgaben für bereits konvertierte Kunden vermeiden und Budgets auf wirklich neue Interessenten konzentrieren.

- **KPIs:** Kosten für Kundenakquise, Kosten pro Lead, Effizienz
- [Reduzierung der Kosten für die Kundenakquise](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### Marketing-Ausgaben und -ROI optimieren

Verbessern Sie den ROI Ihrer Marketing-Investitionen durch bessere Zielgruppenbestimmung, Attribution, Unterdrückung von Zielgruppen und Budgetzuweisung. [!DNL Segment Match] Ermöglicht eine organisationsübergreifende Unterdrückung von Zielgruppen und gemeinsames Targeting, wodurch Duplikate reduziert und die Präzision verbessert werden.

- **KPIs:** Kosteneinsparungen, Kosten für die Kundenakquise, inkrementelle Einnahmen
- [Marketing-Ausgaben und -ROI optimieren](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Beispiele für taktische Anwendungsfälle

- **Zielgruppenvergleich zwischen Publisher und Advertiser** - Eine Marke teilt ihr hochwertiges Kundensegment mit einem Medienherausgeber, um Überschneidungen zu schätzen und abgestimmte Benutzende mit personalisierten Anzeigen anzusprechen, wodurch die Kampagnenrelevanz verbessert wird, ohne personenbezogene Daten offenzulegen.
- **Markenübergreifende Unterdrückung innerhalb einer Holdinggesellschaft** - Mehrere Marken unter einer übergeordneten Organisation teilen Kundensegmente, um bestehende Kunden von Schwestermarken aus Akquisitionskampagnen zu unterdrücken und so Werbeverschwendung zu reduzieren.
- **Zielgruppenerweiterung im Retail-**: Ein retailer teilt kaufbasierte Segmente mit CPG-Markenpartnern, sodass die Marken bewährte Käufer im retailer-Mediennetzwerk mit höheren Konversionsraten ansprechen können.
- **Co-Marketing-Partner-Zielgruppenfindung** - Zwei nicht konkurrierende Marken bewerten Zielgruppenüberschneidungen, um das Partnerschaftspotenzial zu bewerten, bevor eine gemeinsame Kampagne gestartet wird. Zur Validierung der Zielgruppenausrichtung wird eine Überschneidungsschätzung verwendet.
- **Datenkooperative Segmentfreigabe**: Organisationen in einer Datenkooperative teilen gehashte Zielgruppensegmente, um die Zielgruppenreichweite zu erweitern und gleichzeitig die Einhaltung von Datenschutzbestimmungen und Data Governance-Kontrollen zu gewährleisten.
- **Multi-Sandbox Audience Federation** - Ein globales Unternehmen teilt Zielgruppensegmente über regionale Sandboxes hinweg, um eine konsistente Zielgruppenbestimmung auf verschiedenen Märkten zu ermöglichen und gleichzeitig die regionalen Anforderungen an den Datenwohnsitz zu erfüllen.
- **Partnerübergreifende Aktivierung des Treueprogramms** - Eine Treuekonalition teilt Treuestufensegmente mit teilnehmenden Händlern, sodass jeder Partner dem gemeinsamen Kundenstamm geeignete Werbeaktionen anbieten kann.
- **Zusammenarbeit bei Messung und Attribution** - Ein Werbetreibender gibt ein Konversionssegment an einen Medienpartner weiter, damit der Partner die Kampagneneffektivität messen kann, indem er exponierte Benutzende mit Konvertern abgleicht.

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg von Implementierungen der Audience-Zusammenarbeit zu messen.

| KPI | Beschreibung | Messverfahren |
| --- | --- | --- |
| Rate der Zielgruppenüberschneidungen | Prozentsatz der Profile im freigegebenen Segment, die zwischen Absender und Empfänger übereinstimmen | Bericht [!DNL Segment Match] Überschneidungsschätzung |
| Übereinstimmende Zielgruppengröße | Anzahl der Profile, die erfolgreich abgeglichen wurden und für die Aktivierung verfügbar sind | [!DNL Segment Match] Freigabestatus und Anzahl der Zielgruppen |
| Neue Kundenakquise durch übereinstimmende Zielgruppen | Neue Kunden durch Kampagnen gewinnen, die auf übereinstimmende Segmente abzielen | Konversionsverfolgung bei Kampagnen mit übereinstimmenden Audiences |
| Reduzierung der Kundenakquisitionskosten | Kostensenkung pro Akquise bei Verwendung abgeglichener Zielgruppen im Vergleich zum breiten Targeting | Analyse der Kampagnenkosten beim Vergleich von übereinstimmenden und nicht übereinstimmenden Zielgruppen |
| Einsparungen durch Unterdrückung | Durch die Unterdrückung bekannter Kunden aus Akquise-Kampagnen eingesparte Medienausgaben | Vergleich der Medienausgaben vor/nach der Unterdrückung |
| Leistungssteigerung bei Kampagnen | Verbesserung der Konversionsrate, Klickrate oder Interaktion für Kampagnen, die übereinstimmende Audiences verwenden | A/B-Test zum Vergleich von übereinstimmenden Zielgruppenkampagnen mit Kontrolle |
| Zeit bis Collaboration | Verstrichene Zeit von der Initiierung der Segmentfreigabe bis zur Aktivierungsbereitschaft | [!DNL Segment Match] Workflow-Zeitstempel |

## Anwendungsfallmuster

Dieser Anwendungsfall folgt dem Audience Collaboration-Muster.

Freigeben und Abgleichen von Zielgruppensegmenten über Sandboxes oder Organisationen hinweg mithilfe von [!DNL Segment Match].

**Funktionskette:** Segmentauswahl > Übereinstimmungskonfiguration > Überschneidungsschätzung > Zielgruppenfreigabe > Aktivierung

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Real-Time CDP]** - Bietet die [!DNL Segment Match] für die datenschutzfreundliche Freigabe von Zielgruppen, die Evaluierung von Zielgruppen für die Segmenterstellung und die Zielaktivierung für die nachgelagerte Verwendung übereinstimmender Zielgruppen.
- **[!DNL Adobe Experience Platform]** - Bietet die grundlegende Dateninfrastruktur, einschließlich Identitätsauflösung, Profilvereinheitlichung, Data Governance und Einverständnisdurchsetzung, von der [!DNL Segment Match] abhängt.

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Sowohl für Absender- als auch für Empfängerorganisationen müssen Sandboxes mit entsprechenden Rollen und Berechtigungen bereitgestellt werden. Benutzer, die [!DNL Segment Match] verwalten, müssen über Berechtigungen zum Anzeigen und Freigeben von Segmenten, zum Konfigurieren von Verbindungen und zum Verwalten von Partner-Feeds verfügen. ABAC-Richtlinien sollten so konfiguriert werden, dass gesteuert wird, welche Benutzenden Segmentfreigaben initiieren und akzeptieren können. | [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Angenommen an Ort und Stelle | XDM-Schemata für Profile und Ereignisse müssen mit den erforderlichen Feldergruppen vorhanden sein. Profil- und Ereignisdatensätze müssen erstellt und für die [!DNL Real-Time Customer Profile] aktiviert werden. Das Datenmodell muss die Identity-Namespaces unterstützen, die für den Segmentabgleich verwendet werden (normalerweise gehashte E-Mails oder gehashte Telefonnummern). | [XDM-System - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Datenquellen und Sammlung | Angenommen an Ort und Stelle | Kundendaten müssen aktiv über konfigurierte Datenquellen (SDKs, Quell-Connectoren, Batch-Aufnahme) in [!DNL Experience Platform] fließen. Profile müssen mit den Identitätstypen gefüllt werden, die für die [!DNL Segment Match] verwendet werden (z. B. gehashte E-Mail). | [Quellen - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | Identity-Namespaces müssen für die Kennungen konfiguriert werden, die beim Segmentabgleich verwendet werden. Sowohl Absender als auch Empfänger müssen kompatible Identity-Namespaces verwenden. Zusammenführungsrichtlinien müssen konfiguriert werden, um Profile korrekt zu vereinheitlichen. Es sollten Regeln für die Identitätsverknüpfung festgelegt werden, um eine genaue Profilauflösung zu gewährleisten. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Source-Zielgruppen müssen definiert und ausgewertet werden, bevor sie über [!DNL Segment Match] freigegeben werden können. Zielgruppen sollten mithilfe von [!DNL Segment Builder] oder [!DNL Audience Composition] erstellt werden, wobei die Batch-Auswertung abgeschlossen sein sollte. Die Freigabe von [!DNL Segment Match] ist nur für Batch-ausgewertete Zielgruppen möglich. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute wie der lebenslange Kaufwert, der Interaktionswert oder die Produktaffinität können präzisere Segmente für die Freigabe erstellen. Hochwertigere Eingabesegmente führen zu einer wertvolleren Zusammenarbeit mit den Zielgruppen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Einverständnis- und Datenspeicherungsrichtlinien stellen sicher, dass freigegebene Segmente die Datenschutzbestimmungen einhalten. Richtlinien zur Datensatzgültigkeit helfen beim Verwalten des Lebenszyklus der empfangenen Zielgruppendaten. Die Durchsetzung des Einverständnisses verhindert die Freigabe von Profilen, die sich abgemeldet haben. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Eingeschlossen | Data-Governance-Richtlinien müssen vor der Freigabe von Segmenten evaluiert werden, um die Einhaltung der Vorgaben sicherzustellen. Kennzeichnungen für Identitätsfelder und Profilattribute bestimmen, was freigegeben werden kann. Die Durchsetzung von Governance verhindert, dass nicht autorisierte Daten in Segmentfreigaben aufgenommen werden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | Durch die Überwachung des [!DNL Segment Match], der Überschneidungsschätzungsvorgänge und der Aktivierungsdatenflüsse können Fehler frühzeitig erkannt werden. Warnhinweise können für Freigabefehler oder unerwartet niedrige Übereinstimmungsraten konfiguriert werden. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Empfohlen | Die Messung der Leistung von Kampagnen, die übereinstimmende Zielgruppen verwenden, bestätigt den Wert der Zusammenarbeit. [!DNL Customer Journey Analytics] Die Analyse kann die Leistung der abgeglichenen Audience-Kampagnen mit den Kontrollgruppen vergleichen. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Real-Time CDP]

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 1: Segmentauswahl und -vorbereitung | Bewerten Sie die Segmentzugehörigkeit mithilfe der Batch-Auswertung, um die Zielgruppen zu erstellen, die über [!DNL Segment Match] freigegeben werden |
| Audience-Komposition | Phase 1: Segmentauswahl und -vorbereitung | Erstellen Sie optional abgeleitete Zielgruppen (Rang, Aufspaltung, Ausschluss, Anreicherung), um zielgerichtetere Segmente für die Freigabe zu erstellen |
| Durchsetzung von Einverständnis und Governance | Phase 2: Konfiguration und Governance von Übereinstimmungen | Erzwingen von Datennutzungsrichtlinien und Einverständnisvoreinstellungen vor der Freigabe von Segmenten, um die Einhaltung von Richtlinien sicherzustellen |
| Zielgruppen-Aktivierung | Phase 5: Abgestimmtes Audience Activation | Veröffentlichen Sie übereinstimmende Zielgruppen, die über [!DNL Segment Match] empfangen wurden, an externe Ziele zum Targeting oder zur Unterdrückung |
| Zielkonfiguration | Phase 5: Abgestimmtes Audience Activation | Konfigurieren von Verbindungen zu externen Zielen, bei denen übereinstimmende Zielgruppen aktiviert werden |

## Voraussetzungen

- Sowohl Absender- als auch Empfängerorganisationen [!DNL Real-Time CDP] über [!DNL Segment Match] Berechtigungen verfügen
- [!DNL Segment Match] ist für die Organisationen oder Sandboxes aktiviert, die an der Zusammenarbeit teilnehmen
- Es wurde eine Partnerverbindung zwischen der Absender- und der Empfängerorganisation in der [!DNL Segment Match]-Benutzeroberfläche hergestellt
- Beide Organisationen verwenden kompatible Identity-Namespaces (z. B. haben beide gehashte E-Mails konfiguriert)
- Source-Zielgruppen wurden mit Populationen ungleich null definiert und ausgewertet
- Data-Governance-Richtlinien werden konfiguriert und Datennutzungskennzeichnungen werden auf relevante Datensätze und Felder angewendet
- Benutzer auf beiden Seiten verfügen über die erforderlichen Berechtigungen zum Verwalten von [!DNL Segment Match] Verbindungen, Freigaben und Feeds
- Einverständnisfelder werden in Profilen ausgefüllt, um die einverständnisbasierte Filterung vor der Freigabe zu ermöglichen

## Implementierungsoptionen

Die folgenden Optionen beschreiben verschiedene Ansätze zur Implementierung der Audience-Zusammenarbeit mit [!DNL Segment Match]. Wählen Sie die Option aus, die am besten zu Ihrer Organisationsstruktur und Ihren Anforderungen an die Zusammenarbeit passt.

### Option A: Direkte Segmentfreigabe (Eins-zu-eins)

Diese Option eignet sich am besten für bilaterale Partnerschaften zwischen zwei bestimmten Organisationen, z. B. einem Werbetreibenden und einem Herausgeber, oder für zwei Marken, die an einer Co-Marketing-Vereinbarung beteiligt sind.

**Funktionsweise:**

Bei einer direkten Eins-zu-eins-Segmentfreigabe wählt die Absenderorganisation eine oder mehrere ausgewertete Zielgruppen aus, initiiert eine Freigabe für eine bestimmte Partnerorganisation, und der Empfänger akzeptiert die Freigabe. Die Überschneidungsschätzung wird automatisch ausgeführt, um beiden Parteien den Prozentsatz und das Volumen der übereinstimmenden Profile anzuzeigen, bevor die Freigabe abgeschlossen ist.

Der Absender definiert, welche Identity-Namespaces für den Abgleich verwendet werden sollen, und wählt die freizugebenden Segmente aus. Der Empfänger prüft die eingehende Freigabe, akzeptiert sie und die übereinstimmende Zielgruppe wird in ihrer Zielgruppenliste zur nachgelagerten Aktivierung verfügbar. Es werden nur Hash-Identitätsüberschneidungen ausgetauscht - keine zugrunde liegenden PII- oder Profilattributdaten überschreiten die Organisationsgrenzen.

Dieser Ansatz ist einfach und bietet beiden Parteien volle Kontrolle. Der Absender wählt genau aus, was und mit wem geteilt werden soll, und der Empfänger hat die Möglichkeit, jede Freigabe zu akzeptieren oder abzulehnen.

**Wichtige Aspekte:**

- Erfordert die explizite Einrichtung der Partnerverbindung zwischen den beiden Organisationen
- Beide Organisationen müssen sich zur Zuordnung auf Identity-Namespaces einigen
- Überschneidungsschätzung sorgt für Transparenz vor der Verpflichtung
- Jede Freigabe muss einzeln verwaltet und überwacht werden

**Vorteile:**

- Einfacher, gut verständlicher bilateraler Workflow
- Vollständige Transparenz durch Überschneidungsschätzung vor der Freigabe
- Granulare Steuerung - Absender wählt genau die Segmente aus, die freigegeben werden sollen
- Datenschutz-sicher - für den Abgleich werden nur Hash-Kennungen verwendet
- Der Empfänger kann Shares selektiv akzeptieren oder ablehnen

**Einschränkungen:**

- Ist bei gleichzeitiger Zusammenarbeit mit vielen Partnern nicht effizient skalierbar
- Jede Partnerschaft erfordert separate Verbindungseinrichtung und -verwaltung
- Die Freigabekonfiguration muss für jedes neue Segment wiederholt werden

**Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Fehlerbehebung bei Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Option B: Segmentverteilung über mehrere Partner (Eins-zu-Viele)

Diese Option eignet sich am besten für Unternehmen, die Segmente gleichzeitig für mehrere Partner freigeben müssen, z. B. ein Retail-Mediennetzwerk, das kaufbasierte Segmente mit mehreren Markenwerbern teilt, oder eine Holdinggesellschaft, die Segmente an Tochtermarken vertreibt.

**Funktionsweise:**

Bei einem Eins-zu-Viele-Verteilungsmodell stellt die Absenderorganisation [!DNL Segment Match] Verbindungen mit mehreren Partnerorganisationen her und teilt dieselben oder verschiedene Segmente mit jeder Organisation. Der Absender verwaltet ein Portfolio von Partnerverbindungen und kann basierend auf der Beziehung und dem Anwendungsfall selektiv verschiedene Zielgruppensegmente mit verschiedenen Partnern teilen.

Jede Partnerverbindung funktioniert unabhängig voneinander - Überschneidungsschätzung, Freigabeakzeptanz und Aktivierung werden pro Partner verwaltet. Der Absender kann steuern, welche Segmente jeder Partner erhält, was differenzierte Kooperationsstrategien ermöglicht (z. B. erhalten Premium-Partner granularere Segmente, Standard-Partner umfassendere).

Bei diesem Ansatz wird derselbe zugrunde liegende [!DNL Segment Match] wie bei Option A verwendet, jedoch im großen Maßstab mit einem operativen Rahmen für die Verwaltung mehrerer paralleler Partnerschaften.

**Wichtige Aspekte:**

- Erfordert robuste operative Prozesse für die Verwaltung mehrerer Partnerschaften
- Governance-Richtlinien müssen die gemeinsame Nutzung derselben Segmente mit mehreren externen Parteien berücksichtigen
- Jeder Partner kann verschiedene Identity-Namespaces verwenden, was eine flexible Konfiguration erfordert
- Die Überschneidungsraten variieren je nach Partner und erfordern eine Bewertung durch den jeweiligen Partner

**Vorteile:**

- Skaliert die Zusammenarbeit der Zielgruppen über ein Ökosystem von Partnern hinweg.
- Differenzierte Freigabestrategien pro Partner
- Zentralisierte Verwaltung aller ausgehenden Segmentfreigaben von einer Organisation
- Jede Partnerschaft unterhält unabhängige Governance- und Zustimmungskontrollen

**Einschränkungen:**

- Die betriebliche Komplexität steigt mit jedem weiteren Partner
- Überwachung und Fehlerbehebung müssen pro Partner erfolgen
- Governance-Überprüfung für jede neue Partnerverbindung erforderlich
- Partner sehen weder die Daten noch den Freigabestatus der anderen Seite

**Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Option C: Sandbox-übergreifende Zielgruppen-Federation

Diese Option eignet sich am besten für große Unternehmen mit mehreren [!DNL Experience Platform]-Sandboxes (z. B. regionalen Sandboxes, markenspezifischen Sandboxes oder umgebungsspezifischen Sandboxes), die Zielgruppensegmente über interne Grenzen hinweg freigeben müssen, ohne Rohdaten zu verschieben.

**Funktionsweise:**

Anstatt die Freigabe zwischen separaten Organisationen vorzunehmen, verwendet der Sandbox-übergreifende Zielgruppenverbund [!DNL Segment Match], um Zielgruppensegmente zwischen Sandboxes innerhalb derselben Organisation freizugeben. Dies ermöglicht es einem globalen Marketing-Team, ein Segment in einer zentralen Sandbox zu erstellen und es für regionale Sandboxes freizugeben, oder ermöglicht es markenspezifischen Sandboxes, Unterdrückungslisten miteinander zu teilen.

Der Workflow entspricht der direkten Segmentfreigabe (Option A), funktioniert jedoch innerhalb der Organisationsgrenze. Sandbox-zu-Sandbox-Verbindungen werden über [!DNL Segment Match] hergestellt und Segmente werden mithilfe desselben datenschutzsicheren Abgleichsprozesses freigegeben. Die Empfangs-Sandbox ruft die übereinstimmende Zielgruppe als neue Zielgruppe ab, die über ihre eigenen lokal konfigurierten Ziele aktiviert werden kann.

Dieser Ansatz ist besonders nützlich, wenn Anforderungen an den Datenresidenz das Verschieben von rohen Kundendaten zwischen Regionen verhindern, aber eine Zusammenarbeit auf Zielgruppenebene zulässig ist.

**Wichtige Aspekte:**

- Erfordert [!DNL Segment Match] Berechtigung, die die Sandbox-übergreifende Freigabe unterstützt
- Identity-Namespaces müssen über Sandboxes hinweg konsistent sein
- Zusammenführungsrichtlinien in jeder Sandbox können Profile unterschiedlich auflösen, was sich möglicherweise auf die Übereinstimmungsraten auswirkt
- Governance-Richtlinien werden unabhängig pro Sandbox angewendet

**Vorteile:**

- Ermöglicht die Zusammenarbeit mit der Zielgruppe, ohne Rohdaten über Sandbox-Grenzen hinweg zu verschieben
- Unterstützt Anforderungen an die Datenresidenz und die regionale Compliance
- Nutzung vorhandener Identitätsinfrastrukturen des Unternehmens
- Einfachere Governance-Überprüfung, da die Freigabe innerhalb derselben Organisation erfolgt

**Einschränkungen:**

- Erfordert eine konsistente Identity-Namespace-Konfiguration über Sandboxes hinweg
- Die Übereinstimmungsraten hängen von der Konsistenz der Zusammenführungsrichtlinien zwischen Sandboxes ab
- Erfüllt nicht die Anforderungen an eine unternehmensübergreifende Zusammenarbeit
- Möglicherweise sind Sandbox-Tools erforderlich, um Schema und Konfiguration zu synchronisieren

**Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: Direct Segment Share | Option B: Verteilung an mehrere Partner | Option C: Sandbox-übergreifende Federation |
| --- | --- | --- | --- |
| Am besten geeignet für | Bilaterale Partnerschaften | Zusammenarbeit auf Ökosystemebene | Interne Sandbox-übergreifende Freigabe |
| Komplexität | Niedrig | Hoch | Mittel |
| Anzahl Partner | 1 | Viele | Interne Sandboxes |
| Governance-Overhead | Niedrig | Hoch (Überprüfung durch den Partner) | Medium (innerhalb des Unternehmens) |
| Betriebsführung | Einfach | Erfordert Partner-Management-Framework | mittelmäßig |
| Unterstützung für Data Residency | N. z. | Hängt von der Partneradresse ab | stark |
| Erfordert | Einrichten der Partnerverbindung | Mehrere Partnerverbindungen | Sandbox-übergreifende [!DNL Segment Match] |

### Wählen der richtigen Option

Verwenden Sie die folgenden Entscheidungshilfen, um den geeigneten Implementierungsansatz auszuwählen:

1. **Arbeiten Sie mit einer externen Organisation oder innerhalb Ihrer eigenen Organisation zusammen?**
   - Externe Organisation: Fahren Sie mit Frage 2 fort.
   - Innerhalb Ihrer eigenen Organisation (Sandbox-übergreifend): Wählen Sie **Option C** (Sandbox-übergreifende Föderation) aus.

2. **Mit wie vielen externen Partnern werden Sie zusammenarbeiten?**
   - Ein Partner: Wählen Sie **Option A** (Direct Segment Share).
   - Mehrere Partner: Wählen Sie **Option B** (Multi-Partner-Verteilung).

3. **Gibt es Einschränkungen hinsichtlich der Datenresidenz, die verhindern, dass Rohdaten über Regionen hinweg verschoben werden?**
   - Ja: Wählen Sie **Option C**, unabhängig davon, ob die Partner intern oder extern sind - verwenden Sie die Sandbox-übergreifende Freigabe, um die Datenlokalität zu gewährleisten.

## Implementierungsphasen

In den folgenden Phasen wird der End-to-End-Implementierungsprozess für die Audience-Zusammenarbeit mit [!DNL Segment Match] beschrieben.

### Phase 1: Segmente auswählen und vorbereiten

**Anwendungsfunktion:** [!DNL Real-Time CDP]: Zielgruppenauswertung, [!DNL Real-Time CDP]: Zielgruppenkomposition

In dieser Phase werden die Zielgruppensegmente definiert und ausgewertet, die über [!DNL Segment Match] freigegeben werden. Die Quellsegmente müssen mit Populationen ungleich null vollständig ausgewertet werden, bevor sie zur Freigabe ausgewählt werden können. In dieser Phase wird auch die optionale Komposition von Audiences behandelt, um Segmente vor der Freigabe zu verfeinern.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Ansatz zur Zielgruppendefinition**
>
>Wie sollten die Quell-Zielgruppen für die Freigabe erstellt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Segment Builder (Segmentregeln) | Standardmäßige Zielgruppendefinitionen basierend auf Profilattributen, Ereignissen oder Segmentzugehörigkeit | Unterstützt Batch-, Streaming- und Edge-Auswertung; am flexibelsten zum Definieren von Kriterien |
>| Audience-Komposition | Abgeleitete Zielgruppen, für die Rang-, Aufspaltungs-, Ausschluss- oder Anreicherungsvorgänge für vorhandene Segmente erforderlich sind | Unterstützt nur die Batch-Auswertung; auf 10 Kompositions-Arbeitsflächen pro Sandbox beschränkt |
>| Federated Audience-Komposition | Zielgruppen, die aus externen Data Warehouse-Abfragen erstellt wurden, ohne Daten in [!DNL Experience Platform] aufzunehmen | Erfordert [!DNL Federated Audience Composition] Berechtigung; Daten verbleiben im Warehouse |

>[!NOTE]
>
>**Entscheidung: Methode zur Zielgruppenauswertung**
>
>[!DNL Segment Match] erfordert Batch-ausgewertete Zielgruppen. Wie sollte die Auswertung geplant werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Geplante Batches (täglich) | Standardmäßige Anwendungsfälle, bei denen eine tägliche Aktualisierung der Zielgruppe ausreicht | Standard-Auswertungszeitplan; am einfachsten zu verwalten |
>| On-Demand-Batch | Ad-hoc-Freigabe dort, wo Sie die aktuelle Zielgruppe sofort freigeben möchten | Erfordert manuellen Trigger; nützlich für zeitkritische Zusammenarbeit |
>| Benutzerdefinierter Zeitplan | Spezifische Zeitanforderungen, die mit den Zeitfenstern für die Partneraktivierung abgestimmt sind | Konfigurieren eines benutzerdefinierten Cron-Zeitplans, komplexer, aber präziser |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen (für [!DNL Segment Builder]) oder Zielgruppe erstellen (für [!DNL Audience Composition])

**Wichtige Konfigurationsdetails:**

- Zielgruppenkriterien mithilfe von Profilattributen, Verhaltensereignissen und/oder Segmentzugehörigkeit definieren
- Stellen Sie sicher, dass die Zielgruppe eine Zusammenführungsrichtlinie verwendet, die mit den Identity-Namespaces kompatibel ist, die für [!DNL Segment Match] verwendet werden
- Überprüfen, ob die Zielgruppen-Population nach der Auswertung ungleich null ist
- Wenden Sie Unterdrückungsregeln an, um Profile auszuschließen, die nicht freigegeben werden sollen (z. B. Profile, die sich gegen die Datenfreigabe entschieden haben)

**Wo die Optionen unterschiedlich sind:**

**Für Option A (direkte Segmentfreigabe):**
Bereiten Sie die spezifischen Segmente vor, die Sie für Ihren einzelnen Partner freigeben möchten. Konzentrieren Sie sich auf Qualität statt Quantität - kuratieren Sie Segmente, die der Partnerschaft einen klaren Wert bieten.

**Für Option B (Verteilung an mehrere Partner):**
Erstellen Sie ein Portfolio von Segmenten, die mit verschiedenen Partnern geteilt werden können. Erwägen Sie die Erstellung partnerspezifischer Segmente, wenn verschiedene Partner unterschiedliche Zielgruppendefinitionen benötigen. Verwenden Sie konsistente Benennungskonventionen, um Segmente partnerschaftsübergreifend zu verwalten.

**Für Option C (Sandbox-übergreifender Verbund):**
Stellen Sie sicher, dass die Quell-Zielgruppen in der Sende-Sandbox Identity-Namespaces verwenden, die in der Empfangs-Sandbox vorhanden sind. Stellen Sie sicher, dass Zusammenführungsrichtlinien über Sandboxes hinweg ausgerichtet sind.

**Dokumentation zu Experience League:**

- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Auswertungsmethoden](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Phase 2: Konfigurieren von Abgleich und Governance

**Anwendungsfunktion:** [!DNL Real-Time CDP]: Durchsetzung von Einverständnis und Governance

Diese Phase stellt die [!DNL Segment Match] Verbindung zwischen Organisationen oder Sandboxes her, konfiguriert die für den Abgleich verwendeten Identity-Namespaces und stellt sicher, dass Data-Governance-Richtlinien die Freigabe zulassen. Die Durchsetzung von Governance dient als Richtlinientext, der vor der Freigabe von Segmentdaten genehmigt werden muss.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Identity-Namespace für die Zuordnung**
>
>Welcher Identity-Namespace wird für die Zuordnung von Profilen zwischen Absender und Empfänger verwendet?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Hash-E-Mail (SHA-256) | Beide Organisationen erfassen E-Mail-Adressen und können sie konsistent hashen | Häufigster übereinstimmender Schlüssel; hohe Übereinstimmungsraten für Anwendungsfälle von Verbrauchern; beide Seiten müssen denselben Hash-Algorithmus verwenden |
>| Hash-Telefonnummer | E-Mail ist nicht durchgängig verfügbar, aber Telefonnummern sind | Geringere Abdeckung als E-Mail in vielen Märkten; nützlich für „Mobile-First“-Zielgruppen |
>| Benutzerdefinierter Namespace (z. B. gehashte Treueprogramm-ID) | Organisationen verwenden eine gemeinsame ID für Treue- oder Mitgliedschaftsprogramme. | Höchste Übereinstimmungsraten für bekannte, gemeinsam genutzte Kundenbasen; erfordert bereits bestehende gemeinsame ID-Infrastruktur |
>| Mehrere Namespaces | Die Maximierung der Übereinstimmungsrate ist wichtig, und beide Organisationen verfügen über mehrere konsistente Kennungen | Erhöht Übereinstimmungsraten, erhöht jedoch die Komplexität. Jeder Namespace muss unabhängig konfiguriert werden. |

>[!NOTE]
>
>**Entscheidung: Überprüfung der Data Governance**
>
>Welche Governance-Prüfungen müssen vor der Freigabe durchgeführt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Standard-Governance-Evaluierung | Typischer Anwendungsfall mit standardmäßigen Datennutzungskennzeichnungen und -richtlinien | Marketing-Aktion „Export an Dritte“ mit Datensatzkennzeichnungen auswerten; Verstöße vor der Freigabe beheben |
>| Verbesserte Governance mit Einverständnisfilterung | Weitergabe an externe Partner, bei denen das Einverständnis explizit überprüft werden muss | Fügen Sie eine einverständnisbasierte Filterung hinzu, um Profile ohne Freigabe von Einverständnis auszuschließen (z. B. consents.share.val = &#39;n&#39;); strenger, aber sicherer |
>| Interne Überprüfung der Unternehmensführung | Sandbox-übergreifende Freigabe innerhalb derselben Organisation | Geringere Governance-Anforderungen, da Daten innerhalb der Organisationsgrenzen bleiben; Datennutzungskennzeichnungen werden weiterhin überprüft |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Segment Match > Partnerverbindungen

**Wichtige Konfigurationsdetails:**

- Erstellen einer Partnerverbindung durch Austauschen von Verbindungskennungen zwischen Absender- und Empfängerorganisationen
- Identity-Namespaces konfigurieren, die für den Abgleich auf beiden Seiten verwendet werden
- Führen Sie die Bewertung der Data Governance-Richtlinien mit der Marketing-Aktion aus, die mit der Segmentfreigabe verknüpft ist.
- Vergewissern Sie sich, dass die Einverständnisfelder für Profile ausgefüllt werden und dass Profile ohne Freigabe von Einverständnis ausgeschlossen werden
- Überprüfen Sie die Datennutzungsbeschriftungen für die Datensätze und Schemafelder, die in der Freigabe enthalten sind

**Wo die Optionen unterschiedlich sind:**

**Für Option A (direkte Segmentfreigabe):**
Eine einzige Partnerverbindung herstellen. Konfigurieren von Identity-Namespaces mit Ihrem spezifischen Partner. Die Governance-Überprüfung konzentriert sich auf die bilateralen Beziehungen.

**Für Option B (Verteilung an mehrere Partner):**
Erstellen und Verwalten mehrerer Partnerverbindungen. Jeder Partner kann eine separate Überprüfung der Unternehmensführung erfordern. Dokumentieren Sie die Governance-Genehmigung für jede Partnerschaft. Erwägen Sie die Erstellung einer Checkliste für die Governance, um das Onboarding von Partnern zu optimieren.

**Für Option C (Sandbox-übergreifender Verbund):**
Erstellen Sie Sandbox-zu-Sandbox-Verbindungen innerhalb der Organisation. Die Governance ist in der Regel einfacher, da die Freigabe intern erfolgt. Stellen Sie sicher, dass Identity-Namespaces in allen Sandboxes konsistent sind.

**Dokumentation zu Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### Phase 3: Überschneidung schätzen

**Anwendungsfunktion:** [!DNL Real-Time CDP]: Zielgruppenbewertung (zum Schätzen von Überschneidungen)

In dieser Phase wird die Überschneidungsschätzung zwischen den Segmenten des Absenders und der Profilbasis des Empfängers durchgeführt. Die Überschneidungsschätzung liefert beiden Parteien das erwartete Übereinstimmungsvolumen und den erwarteten Prozentsatz, bevor sie sich zur vollständigen Segmentfreigabe verpflichten, was fundierte Entscheidungen über den Wert der Zusammenarbeit ermöglicht.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Überschneidungsschwelle für das Verfahren**
>
>Welche minimale Überschneidungsrate rechtfertigt die Fortführung der vollständigen Segmentfreigabe?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Kein Mindestschwellenwert | Sondierende Partnerschaften oder wenn Überschneidungen nützlich sind | Geeignet für die erste Zusammenarbeit, bei der Sie die Beziehung testen |
>| Niedriger Schwellenwert (1-5 %) | Zusammenarbeit mit großen Zielgruppen, bei der bereits geringe Überschneidungen ein erhebliches Volumen darstellen | Häufig für Publisher-Advertiser-Beziehungen mit großen Zielgruppen |
>| Medium-Schwellenwert (5-20 %) | Standard-Partnerschaften, bei denen eine bedeutende Überschneidung erwartet wird | Typisch für Co-Marketing oder Zusammenarbeit in der gleichen Branche |
>| Hoher Schwellenwert (20 %+) | Partnerschaften, bei denen eine starke Ausrichtung der Zielgruppen eine Voraussetzung ist | Gemeinsam für Loyalitätskoalitionen oder eng integrierte Markenpartnerschaften |

**UI-Navigation:** Kunde > Zielgruppen > Segment Match > Freigaben > Überschneidung schätzen

**Wichtige Konfigurationsdetails:**

- Segmente auswählen, die in die Überschneidungsschätzung aufgenommen werden sollen
- Überprüfen Sie den Überschneidungsbericht mit der Anzahl und dem Prozentsatz der übereinstimmenden Profile.
- Teilen Sie die Ergebnisse der Überschneidungsschätzung mit den Stakeholdern auf beiden Seiten zur Genehmigung
- Dokumentieren Sie die Überschneidungsmetriken als Grundlage für die Messung der Effektivität der Zusammenarbeit
- Wenn die Überschneidung unter dem akzeptablen Schwellenwert liegt, sollten Sie die Segmentdefinitionen oder die Konfiguration des Identitätsabgleichs anpassen, bevor Sie fortfahren

**Dokumentation zu Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Phase 4: Audiences freigeben

**Anwendungsfunktion:** [!DNL Real-Time CDP]: Zielgruppenauswertung (für die Ausführung von Freigaben)

In dieser Phase wird die tatsächliche Segmentfreigabe vom Absender zum Empfänger ausgeführt. Der Absender initiiert die Freigabe für die ausgewählten Segmente, und der Empfänger akzeptiert die eingehende Freigabe. Nach der Annahme wird die übereinstimmende Zielgruppe in der Zielgruppenliste des Empfängers als neue Zielgruppe angezeigt, die für die nachgelagerte Aktivierung verfügbar ist.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Freigaberichtung**
>
>Was ist das Freigabemodell für diese Zusammenarbeit?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einwegfreigabe (Sender an Empfänger) | Asymmetrische Partnerschaft, bei der nur eine Partei Zielgruppendaten bereitstellt | Einfaches Modell; Absenderfreigaben, Empfänger werden aktiviert; häufig in Advertiser-Publisher-Beziehungen |
>| bidirektionale Freigabe | Beide Parteien profitieren vom Austausch ihrer Zielgruppen untereinander | Beide Organisationen agieren gleichzeitig als Absender und Empfänger. Erfordert zwei Freigabekonfigurationen. Wird in Co-Marketing-Partnerschaften verwendet. |

>[!NOTE]
>
>**Entscheidung: Aktualisierungskadenz freigeben**
>
>Wie oft sollte die freigegebene Zielgruppe mit aktualisierter Segmentzugehörigkeit aktualisiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einmalige Freigabe | Testen der Zusammenarbeit oder für eine bestimmte Kampagne mit einer festen Zielgruppe | Einfachste, keine laufende Wartung; Zielgruppe veraltet im Laufe der Zeit |
>| Wiederkehrende Freigabe (abgestimmt auf die Batch-Auswertung) | Laufende Partnerschaften, bei denen sich die Zielgruppenzugehörigkeit ändert und aktuell gehalten werden muss | Erfordert die Überwachung des Aktualisierungsstatus, am häufigsten bei Zusammenarbeit in der Produktion |

**UI-Navigation:** Kunde > Zielgruppen > Segment Match > Freigaben > Freigabe erstellen (Absender) oder Freigabe akzeptieren (Empfänger)

**Wichtige Konfigurationsdetails:**

- Absender wählt die freizugebenden Segmente aus und initiiert die Freigabe für den konfigurierten Partner
- Empfänger prüft die eingehenden Freigabedetails (Segmentnamen, geschätzte Größe, verwendete Identity-Namespaces)
- Receiver akzeptiert die Freigabe, um die passende Zielgruppe in der Sandbox zu erstellen
- Überprüfen Sie, ob die übereinstimmende Zielgruppe in der Zielgruppenliste des Empfängers mit der erwarteten Population angezeigt wird
- Vergewissern Sie sich, dass die übereinstimmende Zielgruppe für das Governance-Tracking entsprechend gekennzeichnet ist

**Wo die Optionen unterschiedlich sind:**

**Für Option A (direkte Segmentfreigabe):**
Führen Sie eine einzelne Freigabe für Ihren Partner aus. Überwachen Sie den Freigabestatus und überprüfen Sie die übereinstimmende Zielgruppe auf der Empfängerseite.

**Für Option B (Verteilung an mehrere Partner):**
Führt Freigaben für jeden Partner unabhängig aus. Verfolgen Sie den Freigabestatus in allen Partnerschaften. Zur Verwaltung der Verarbeitungslast sollte die Freigabe zeitlich gestaffelt initiiert werden.

**Für Option C (Sandbox-übergreifender Verbund):**
Ausführen der Sandbox-übergreifenden Freigabe. Die übereinstimmende Zielgruppe wird in der Zielgruppenliste der empfangenden Sandbox angezeigt. Vergewissern Sie sich, dass die empfangende Sandbox über die erforderlichen Zielkonfigurationen für die nachgelagerte Aktivierung verfügt.

**Dokumentation zu Experience League:**

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Fehlerbehebung bei Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Phase 5: Aktivieren übereinstimmender Zielgruppen

**Anwendungsfunktion:** [!DNL Real-Time CDP]: Zielkonfiguration, [!DNL Real-Time CDP]: Audience Activation

In dieser Phase wird die übereinstimmende Zielgruppe (auf der Empfängerseite) für externe Ziele zum Targeting, zur Unterdrückung oder zur nachgelagerten Verwendung aktiviert. Die übereinstimmende Zielgruppe wird wie jede andere Zielgruppe in der Sandbox des Empfängers behandelt und kann über den standardmäßigen Zielaktivierungs-Workflow aktiviert werden.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Zieltyp für übereinstimmende Zielgruppe**
>
>Wo soll die passende Zielgruppe aktiviert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Advertising-Ziele (Google, Meta, Trade Desk) | Verwenden übereinstimmender Zielgruppen für das Anzeigen-Targeting oder die Unterdrückung | Erfordert Zielverbindung und -authentifizierung; unterliegt zielspezifischen Ratenbeschränkungen und Formatanforderungen |
>| Cloud-Speicher-Ziele (S3, Azure, GCS) | Exportieren übereinstimmender Zielgruppen als Dateien zur Verwendung in externen Systemen | Unterstützt die Anpassung von Dateiformaten; Batch-Exportplan erforderlich; flexibel für die nachgelagerte Verarbeitung |
>| CRM-/Marketing-Automatisierungsziele | CRM-Datensätze anreichern oder automatisierte Marketing-Workflows mit übereinstimmenden Zielgruppendaten auslösen | Erfordert die Feldzuordnung zum CRM-Schema; nützlich für die Ausrichtung von Vertrieb und Marketing |
>| Personalization-Ziele (Web, App) | Verwenden einer übereinstimmenden Zielgruppenzugehörigkeit für die Personalisierung vor Ort | Erfordert eine Edge-Auswertung der übereinstimmenden Zielgruppe oder Streaming-Aktivierung; die Latenz variiert je nach Ziel |

>[!NOTE]
>
>**Entscheidung: Aktivierungsplan**
>
>Wie oft sollte die übereinstimmende Zielgruppe an das Ziel exportiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Täglicher inkrementeller Export | Standardaktivierung mit regelmäßigen Zielgruppen-Updates | Exportiert nur geänderte Profile; geringeres Datenvolumen; am häufigsten bei laufenden Kampagnen |
>| Täglicher vollständiger Export | Ziele, für die jedes Mal eine vollständige Zielgruppendatei erforderlich ist | Höheres Datenvolumen; stellt sicher, dass das Ziel den vollständigen Zielgruppenstatus hat; einige Ziele erfordern vollständige Exporte |
>| Aktivierung bei Bedarf | Ad-hoc-Kampagnenstarts oder zeitabhängige Aktivierungen | Manueller Trigger; planmäßige Kadenz wird umgangen; nur für Batch-Ziele verfügbar |

**Benutzeroberflächennavigation:** Verbindungen > Ziele > Katalog (für die Zieleinrichtung) oder Durchsuchen > Ziel auswählen > Zielgruppen aktivieren (für die Aktivierung)

**Wichtige Konfigurationsdetails:**

- Konfigurieren der Zielverbindung mit entsprechenden Authentifizierungsberechtigungen
- Profilattribute aus der übereinstimmenden Zielgruppe Zielfeldern zuordnen (Identitätsfelder, Profilattribute, Segmentzugehörigkeit)
- Konfigurieren des Exportzeitplans (inkrementell vs. voll, täglich vs. benutzerdefiniert)
- Überwachen des Aktivierungsdatenflusses, um zu bestätigen, dass übereinstimmende Zielgruppenprofile erfolgreich exportiert wurden
- Überprüfen von Aktivierungsmetriken (exportierte Profile, fehlgeschlagene Datensätze) in der Zielüberwachungsansicht

**Wo die Optionen unterschiedlich sind:**

**Für Option A (direkte Segmentfreigabe):**
Der Empfänger aktiviert die übereinstimmende Zielgruppe über den standardmäßigen Ziel-Workflow. Über die normale Zielaktivierung hinaus ist keine spezielle Konfiguration erforderlich.

**Für Option B (Verteilung an mehrere Partner):**
Jede Empfängerorganisation aktiviert übereinstimmende Zielgruppen unabhängig über ihre eigenen Ziele. Der Absender hat keine Einsicht in die empfängerseitige Aktivierung.

**Für Option C (Sandbox-übergreifender Verbund):**
Die empfangende Sandbox muss über eigene Zielkonfigurationen verfügen. Ziele können nicht über Sandboxes hinweg freigegeben werden. Stellen Sie sicher, dass in der Empfangs-Sandbox die erforderlichen Zielverbindungen hergestellt wurden.

**Dokumentation zu Experience League:**

- [Übersicht über Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Überlegungen bei der Implementierung

Lesen Sie die folgenden Überlegungen vor und während der Implementierung, um häufige Probleme zu vermeiden und die Zusammenarbeit mit Ihren Zielgruppen zu optimieren.

### Leitplanken und Beschränkungen

- [!DNL Segment Match] verwendet Hash-Kennungen für den Abgleich - keine personenbezogenen Daten überschreiten die Organisationsgrenzen. Siehe [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview).
- Nur im Batch ausgewertete Zielgruppen können über [!DNL Segment Match] freigegeben werden. Streaming- und Edge-ausgewertete Segmente müssen vor der Freigabe in eine Batch-Auswertung konvertiert werden.
- Maximal 4.000 Segmentdefinitionen pro Sandbox gelten sowohl für Quell- als auch für empfangene Segmente. Siehe [Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).
- Die Genauigkeit der Überschneidungsschätzung hängt vom Volumen der übereinstimmenden Kennungen ab. Kleine Zielgruppen zeigen möglicherweise weniger präzise Schätzungen an.
- Aktivierungsleitplanken gelten für übereinstimmende Zielgruppen genauso wie für jede andere Zielgruppe - maximal 100 Datenflüsse pro Ziel. Siehe [Aktivierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Zusammengestellte Zielgruppen werden nach einem Batch-Zeitplan ausgewertet und sind auf 10 Kompositions-Arbeitsflächen pro Sandbox beschränkt. Siehe [Leitplanken für die Zielgruppenkomposition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails).

### Häufige Fehler

- **Inkonsistentes Identitäts-Hashing zwischen Absender und Empfänger:** Wenn beide Organisationen E-Mail-Adressen hashen, aber unterschiedliche Hashing-Algorithmen, Normalisierungsregeln oder Salzwerte verwenden, liegen die Übereinstimmungsraten nahe null. Beide Seiten müssen sich auf die genaue Hash-Spezifikation einigen (z. B. SHA-256 für E-Mails in Kleinbuchstaben, gekürzt), bevor die Verbindung hergestellt wird.
- **Freigabe von Zielgruppen ohne Governance-Überprüfung:** Initiieren einer Segmentfreigabe ohne Auswertung von Datennutzungsrichtlinien kann zu Verstößen gegen die Compliance führen. Führen Sie immer eine Governance-Richtlinienbewertung für die Marketing-Aktion „Export an Dritte“ durch, bevor Sie Segmente für externe Organisationen freigeben.
- **Niedrige Übereinstimmungsraten aufgrund von Lücken in der Identitätsabdeckung:** Wenn die Zielgruppe des Absenders in erster Linie durch ECID (anonymes Cookie) identifiziert wird, der übereinstimmende Namespace jedoch aus E-Mail-Hash-Daten besteht, ist die Übereinstimmungsrate sehr niedrig, da anonyme Profile keine E-Mail-Adressen haben. Stellen Sie sicher, dass die Quell-Zielgruppen über eine ausreichende Abdeckung des konfigurierten übereinstimmenden Identity-Namespace verfügen.
- **Akzeptieren der Freigabe auf Empfängerseite wird vergessen:** Die freigegebene Zielgruppe wird erst in der Zielgruppenliste des Empfängers angezeigt, wenn die Freigabe ausdrücklich akzeptiert wird. Abstimmung mit dem Empfänger, um eine rechtzeitige Annahme sicherzustellen, insbesondere für zeitkritische Kampagnen.
- **Veraltete übereinstimmende Zielgruppen aufgrund einer Fehlausrichtung des Auswertungsplans:** Wenn die Quellzielgruppe des Absenders täglich ausgewertet wird, die [!DNL Segment Match] jedoch wöchentlich aktualisiert wird, spiegelt die übereinstimmende Zielgruppe auf Empfängerseite möglicherweise nicht die neueste Mitgliedschaft wider. Bewertung ausrichten und Aktualisierungskadenzen freigeben.

### Best Practices

- Erstellen Sie vor der Konfiguration von [!DNL Segment Match] eine formelle Datenfreigabevereinbarung zwischen Organisationen. Dies sollte zulässige Anwendungsfälle, Data-Governance-Anforderungen, Zustimmungspflichten und Beendigungsverfahren abdecken.
- Verwenden Sie die Überschneidungsschätzung als Validierungstool vor jeder größeren Kampagne - führen Sie die Schätzung vor der Zusage durch, um sicherzustellen, dass die passende Zielgruppe die Mindestgröße und die Qualitätsschwellen erreicht.
- Wenden Sie beschreibende Benennungskonventionen auf freigegebene Segmente an, die den Partnernamen, den Anwendungsfall und das Datum enthalten (z. B. „PartnerX_HighValue_Suppression_2026Q1„), um die Klarheit zwischen den Unternehmen zu wahren.
- Überwachen Sie Übereinstimmungsraten im Zeitverlauf. Sinkende Übereinstimmungsraten können auf eine Beeinträchtigung der Identitätsabdeckung, Probleme mit der Datenqualität oder Änderungen im Kundenstamm des Partners hinweisen.
- Segmentquellen-Zielgruppen, um Profile auszuschließen, ohne dass der entsprechende Identity-Namespace ausgefüllt ist. Dadurch werden die Übereinstimmungsratenprozentsätze verbessert und genauere Überschneidungsschätzungen bereitgestellt.
- Bestimmen Sie bei bidirektionalen Freigabepartnerschaften die eindeutige Eigentümerschaft an Segmentwartungs- und -aktualisierungszeitplänen, um Verwirrung darüber zu vermeiden, welche Organisation für die Aktualisierungen verantwortlich ist.

### Entscheidungen über Kompromisse

>[!NOTE]
>
>**Kompromiss: Übereinstimmungsrate vs. Datenschutzkontrolle**
>
>Die Verwendung von mehr Identity-Namespaces (gehashte E-Mail, gehashte Telefonnummer, Geräte-IDs) für den Abgleich erhöht die Übereinstimmungsraten, erweitert aber die Oberfläche für eine potenzielle erneute Identifizierung. Die Verwendung von weniger Namespaces (nur Hash-E-Mails) bietet einen stärkeren Datenschutz, kann jedoch die Größe der entsprechenden Zielgruppe verringern.
>
>- **Mehrere Namespaces bevorzugen** Höhere Übereinstimmungsraten, größere übereinstimmende Zielgruppen, mehr Wert für das Kampagnen-Targeting
>- **Ein einziger Namespace begünstigt:** Stärkere Datenschutzhaltung, einfachere Governance-Überprüfung, geringeres Compliance-Risiko
>- **Empfehlung:** Beginnen Sie mit einem einzigen Namespace (gehashte E-Mail ist die häufigste Variante) und fügen Sie zusätzliche Namespaces nur hinzu, wenn die Übereinstimmungsraten für den Anwendungsfall unzureichend sind. Dokumentieren Sie die Auswirkungsbewertung für Datenschutz für jeden hinzugefügten Namespace.

>[!NOTE]
>
>**Kompromiss: Segmentgranularität vs. Einfachheit der Bedienung**
>
>Die gemeinsame Nutzung vieler granularer, zielgerichteter Segmente mit einem Partner bietet mehr Flexibilität beim Kampagnen-Targeting, erhöht jedoch die betriebliche Komplexität sowohl für Absender als auch für Empfänger. Durch die Freigabe von weniger, breiteren Segmenten wird die Verwaltung vereinfacht, aber die Genauigkeit der Zielgruppenbestimmung verringert.
>
>- **Granulare Segmente begünstigen** Präzises Targeting, differenzierte Kampagnen, höhere Relevanz
>- **Große Segmente sprechen sich für** einfacheres Management, weniger zu überwachende Anteile und einen geringeren Betriebsaufwand aus
>- **Empfehlung:** Beginnen Sie mit einer kleinen Anzahl von hochwertigen Segmenten (2-5) für eine neue Partnerschaft. Erhöhen Sie die Granularität, wenn die Partnerschaft heranreift und operative Prozesse etabliert werden. Verwenden Sie Namenskonventionen und Dokumentation, um die Komplexität mit wachsender Segmentanzahl zu verwalten.

>[!NOTE]
>
>**Kompromiss: Häufigkeit der Aktualisierung vs. Verarbeitungskosten**
>
>Durch häufigeres Aktualisieren freigegebener Zielgruppen wird die übereinstimmende Zielgruppe auf dem neuesten Stand gehalten, die Verarbeitungslast wird jedoch erhöht, und es kann mehr Lizenzkapazität verbraucht werden. Weniger häufige Aktualisierungen reduzieren die Kosten, sorgen aber dafür, dass die passende Zielgruppe veraltet ist.
>
>- **Häufige Aktualisierungsfavoriten:** aktuelle Zielgruppenzugehörigkeit, höhere Kampagnenrelevanz, bessere Unterdrückungsgenauigkeit
>- **Unregelmäßige Aktualisierungsvorteile:** Niedrigere Verarbeitungskosten, einfachere Überwachung, reduzierter Lizenzverbrauch
>- **Empfehlung:** tägliche Aktualisierung ist für die meisten Produktions-Kollaborationen geeignet. Bei zeitabhängigen Anwendungsfällen (z. B. Flash-Verkäufe, ereignisbasierte Kampagnen) sollten Sie eine On-Demand-Neubewertung und -Freigabe unmittelbar vor dem Start der Kampagne in Betracht ziehen.

## Verwandte Dokumentation

Die folgenden Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

### [!DNL Segment Match]

- [Übersicht zu Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Fehlerbehebung bei Segment Match](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentierung und Audiences

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Zielgruppenkomposition - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identität und Profil

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Data Governance und Einverständnis

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Datennutzungs-Labels – Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/labels/overview)
- [Durchsetzung von Richtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Einverständnis und Einstellungen](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### Ziele und Aktivierung

- [Übersicht über Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Überwachen von Datenflüssen für Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### Datenmodellierung und Schema

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Verwaltung und Zugriffskontrolle

- [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home)

### Überwachung und Beobachtbarkeit

- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Leitlinien

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Aktivierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Tutorials

- [Erstellen eines Schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Aktivieren eines Datensatzes für Profil](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
