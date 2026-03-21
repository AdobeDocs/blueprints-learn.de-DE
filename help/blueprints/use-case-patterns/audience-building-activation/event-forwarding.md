---
title: Ereignisweiterleitung
description: Erfahren Sie, wie Sie über Edge Network erfasste Echtzeit-Ereignisdaten zur Analyse, Speicherung oder Werbung an Ziele weiterleiten, die nicht mit Adobe verbunden sind.
solution: Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---


# Ereignisweiterleitung

In diesem Handbuch wird die Implementierung der Server-seitigen Ereignisweiterleitung mit [!DNL Adobe Experience Platform] Edge Network beschrieben. Sie wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die über die Edge Network erfasste Echtzeit-Ereignisdaten an Ziele weiterleiten müssen, die nicht mit Adobe verbunden sind - z. B. Analyseplattformen von Drittanbietern, Cloud-Speicher-Endpunkte, Werbenetzwerke oder benutzerdefinierte Webhooks.

Es werden alle praktikablen Ansätze zur Konfiguration der Ereignisweiterleitung vorgestellt, die Zielkonflikte zwischen ihnen erläutert und Links zu [!DNL Adobe Experience League] Dokumentation mit detaillierten Verfahrensanleitungen bereitgestellt.

## Anwendungsfall - Übersicht

Unternehmen, die Verhaltensdaten über [!DNL Adobe Experience Platform] Web SDK, Mobile SDK oder die Server-API erfassen, müssen diesen Ereignisstream häufig mit Nicht-Adobe-Systemen teilen - Analyseplattformen wie [!DNL Google Analytics] oder [!DNL Snowflake], Werbenetzwerken für Konversionsverfolgung, Data Warehouses für die langfristige Datenspeicherung oder benutzerdefinierten internen Services. Traditionell erforderte dies eine Client-seitige Verbreitung von Tags, die das Seitengewicht erhöht, zu Latenz führt und Datenschutz- und Governance-Risiken birgt.

Die Ereignisweiterleitung löst dies, indem sie Server-seitig auf der Edge Network ausgeführt wird. Wenn eine Besucherinteraktion ein Ereignis über die Web-SDK- oder -Server-API Trigger, wird dieses Ereignis über einen Datenstrom an die Edge Network weitergeleitet. Regeln für die Ereignisweiterleitung - konfiguriert in einer dedizierten Ereignisweiterleitungseigenschaft - werten die eingehenden Ereignisdaten aus und leiten sie selektiv an ein oder mehrere konfigurierte Ziele weiter. Dieser Server-seitige Ansatz reduziert den Client-seitigen Aufblähen von Tags, verbessert die Seitenleistung, zentralisiert die Data Governance und gibt dem Unternehmen die Kontrolle darüber, welche Daten das Adobe-Ökosystem verlassen.

Die Zielgruppe für dieses Muster umfasst Unternehmen, die die [!DNL Adobe Experience Platform] Web SDK- oder Server-API bereits für die Datenerfassung bereitgestellt haben (oder bereitstellen wollen) und diese Investition erweitern möchten, indem sie Ereignisdaten an Nicht-Adobe-Endpunkte verteilen, ohne Client-seitige JavaScript-Tags hinzuzufügen.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

### Verbesserung der Datenqualität und -verwaltung

Stellen Sie saubere, vollständige und konforme Daten für eine präzise Zielgruppenbestimmung, weniger Verschwendung und zuverlässige Analysen sicher. Die Ereignisweiterleitung zentralisiert die Datenverteilung auf der Serverseite. Dadurch erhält das Unternehmen einen einzigen Kontrollpunkt für die Daten, die mit externen Systemen freigegeben werden. So wird das Risiko von Datenverlusten reduziert, und es wird sichergestellt, dass Governance-Richtlinien angewendet werden, bevor Daten die [!DNL Adobe] Edge Network verlassen.

**KPIs:**, Kosteneinsparungen

Weitere Informationen finden Sie unter [Verbesserung der Datenqualität und der Governance](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Konsolidierung und Modernisierung der Marketing-Technologie

Reduzierung der Tool-Fragmentierung und der technischen Verschuldung durch Migration auf einheitliche, skalierbare Plattformen. Die Ereignisweiterleitung ermöglicht es Unternehmen, mehrere Client-seitige Anbieter-Tags durch einen einzigen Server-seitigen Datenverteilungsmechanismus zu ersetzen, wodurch der Seitenladeaufwand reduziert und der Technologie-Stack vereinfacht wird.

**KPIs:** Kosteneinsparungen, Effizienz, Markteinführungsgeschwindigkeit

Weitere Informationen finden Sie unter [Konsolidierung und Modernisierung der Marketing-Technologie](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md).

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie gängige taktische Szenarien, in denen dieses Anwendungsfallmuster gilt.

- **Anreicherung von Drittanbieteranalysen** - Leiten Sie Seitenansichten, Klicks und Konversionsereignisse in Echtzeit an [!DNL Google Analytics], [!DNL Snowflake] oder andere Analyseplattformen weiter, ohne Client-seitige Tags hinzuzufügen
- **Advertising-Konversionsverfolgung** - Senden Sie Kauf- und Lead-Generierungsereignisse an [!DNL Meta] Conversions-API, [!DNL Google Ads], [!DNL TikTok] oder [!DNL Snap] zur Server-seitigen Messung und Optimierung der Konversion
- **Data Warehouse-Streaming** - Routing von Rohdaten zu einem Cloud-Data Warehouse ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) für die langfristige Speicherung und Offline-Analyse
- **Benutzerdefinierte Webhook-Integration** - leitet gefilterte oder transformierte Ereignisdaten über HTTP-Endpunkte an interne Microservices, CRM-Systeme oder Partnerplattformen weiter
- **Tag-Reduzierung und Verbesserung der Seitenleistung** - Ersetzen Sie mehrere Client-seitige JavaScript-Tags von Anbietern durch eine einzige Web-SDK-Implementierung plus Server-seitige Ereignisweiterleitungsregeln, wodurch die Seitengröße reduziert und Core Web Vitals verbessert wird
- **Datenschutzkonforme Datenfreigabe** - Wenden Sie Datenfilter- und Feldebene-Redaktionsregeln Server-seitig an, bevor Sie Ereignisdaten für Dritte freigeben, um sicherzustellen, dass personenbezogene Daten entfernt oder gehasht werden, bevor sie externe Systeme erreichen
- **Multi-Cloud-Ereignisverteilung** - Leiten Sie denselben Ereignisstream gleichzeitig an mehrere Ziele (z. B. Analytics, Advertising und Data Warehouse) von einem einzigen Server-seitigen Regelsatz weiter
- **Signalweiterleitung für Betrugsfälle in Echtzeit** — Weiterleitung hochwertiger Transaktionsereignisse an Systeme zur Betrugserkennung zur Echtzeit-Risikobewertung und -warnung

## Wichtige Performance-Indikatoren

Die folgenden KPIs helfen, den Erfolg dieses Anwendungsfallmusters zu messen.

- **Verringerung der Seitenladezeit** - Gemessene Verbesserung der Seitenladegeschwindigkeit und von Core Web Vitals nach der Migration von Client-seitigen Tags zur Server-seitigen Ereignisweiterleitung
- **Erfolgsrate der Datenbereitstellung** - Prozentsatz der erfolgreich an Ziel-Endpunkte weitergeleiteten Ereignisse ohne Fehler oder Zeitüberschreitungen
- **Reduzierung der Tag-Anzahl** - Anzahl der Client-seitigen Anbieter-Tags, die nach der Implementierung serverseitiger Entsprechungen entfernt wurden
- **Datenaktualität/Latenz** - Zeit zwischen dem Auftreten eines Ereignisses auf dem Client und dem Eintreffen eines Ereignisses am Zielendpunkt (Ziel: Untersekunde bis Sekunden)
- **Governance-Compliance-Rate** - Prozentsatz der ausgehenden Datenfreigaben, die Server-seitige Filterregeln durchlaufen, sodass keine personenbezogenen Daten oder eingeschränkten Daten unbefugte Ziele erreichen
- **Betriebseffizienz** - Verringerung des Zeitaufwands für Entwickler für die Verwaltung Client-seitiger Tag-Bereitstellungen und die Fehlerbehebung bei Tag-Konflikten

## Anwendungsfallmuster

In diesem Abschnitt werden das Muster und die Funktionskette beschrieben, die zur Implementierung der Ereignisweiterleitung verwendet werden.

**Ereignisweiterleitung** - Weiterleiten von über Edge Network erfassten Echtzeit-Ereignisdaten an Nicht-Adobe-Ziele zu Analyse-, Speicher- oder Werbezwecken.

**Funktionskette:** Datenstromkonfiguration > Ereignisregeldefinition > Zielzuordnung > Weiterleitungsausführung > Überwachung

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Experience Platform] (Edge Network)** - Empfängt Echtzeit-Ereignisdaten von Web SDK, Mobile SDK oder der Server-API und leitet sie über konfigurierte Datenströme weiter.
- **[!DNL Adobe Experience Platform] (Ereignisweiterleitung)** - Stellt die Server-seitige Regel-Engine zum Auswerten, Filtern, Transformieren und Weiterleiten von Ereignisdaten an externe Ziele bereit
- **[!DNL Adobe Experience Platform] (Tags/Datenerfassung)** - Verwaltet den Lebenszyklus, die Erweiterungen, die Regeln und den Veröffentlichungs-Workflow der Ereignisweiterleitungs-Eigenschaft

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Eine Sandbox muss mit den entsprechenden konfigurierten Benutzerrollen und Berechtigungen aktiv sein. Benutzende, die die Ereignisweiterleitung verwalten, benötigen Datenerfassungsberechtigungen in [!DNL Adobe Admin Console], einschließlich Berechtigungen zum Verwalten von Eigenschaften, Erweiterungen und Regeln für die Ereignisweiterleitung. | [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | XDM-Schemata müssen für die Ereignisdaten definiert werden, die durch die Edge Network fließen. Der Datenstrom muss auf ein gültiges XDM ExperienceEvent-Schema verweisen, damit die Regeln für die Ereignisweiterleitung zum Filtern, Transformieren und Zuordnen auf strukturierte Felder zugreifen können. | [XDM-System - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home) |
| Datenquellen und Sammlung | Erforderlich | Ein Datenerfassungsmechanismus muss aktiv sein - Web SDK, Mobile SDK oder Edge Network Server API - und Ereignisse über einen konfigurierten Datenstrom senden. Der Datenstrom ist die grundlegende Routing-Ebene, die die Client-seitige Erfassung mit der Server-seitigen Ereignisweiterleitung verbindet. | [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure) |
| Identitäts- und Profilkonfiguration | Nicht zutreffend | Die Ereignisweiterleitung verarbeitet unformatierte Ereignisdaten auf Edge Network-Ebene, bevor die Identitätsauflösung oder Profilvereinheitlichung erfolgt. Identity-Namespaces und Zusammenführungsrichtlinien sind nicht erforderlich, es sei denn, die weitergeleiteten Ereignisse müssen auch zum Echtzeit-Kundenprofil beitragen (bei dem es sich um eine separate Datenstrom-Service-Konfiguration und nicht um eine Ereignisweiterleitung handelt). | |
| Zielgruppendefinition und Segmentierung | Nicht zutreffend | Die Ereignisweiterleitung verarbeitet einzelne Ereignisse in Echtzeit und bewertet die Zielgruppenzugehörigkeit nicht. Die zielgruppenbasierte Filterung ist nicht Teil der Funktionskette der Ereignisweiterleitung. Wenn eine zielgruppenbasierte Aktivierung erforderlich ist, finden Sie weitere Informationen im Referenzplan Audience Activation zu Zielen . | |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Nicht zutreffend | Die Ereignisweiterleitung basiert auf Rohdaten von Ereignissen, nicht auf berechneten Attributen auf Profilebene. Berechnete Attribute sind im Ereignisweiterleitungskontext nicht verfügbar. | |
| Data Lifecycle Management | Empfohlen | Wenn Ereignisdaten ebenfalls (über denselben Datenstrom) in AEP-Datensätze aufgenommen werden, sollten für diese Datensätze Richtlinien zur Datenaufbewahrung (Gültigkeit) konfiguriert werden, um die Speicherkosten und die Einhaltung behördlicher Auflagen zu verwalten. Die Ereignisweiterleitung selbst speichert keine Daten, der parallele Aufnahmepfad von AEP jedoch schon. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Während die Regeln für die Ereignisweiterleitung eine Filterung auf Feldebene ermöglichen (sodass Sie sensible Daten von weitergeleiteten Payloads ausschließen können), stellt das Anwenden von Datennutzungskennzeichnungen auf die zugrunde liegenden Schemata und Datensätze sicher, dass Governance-Richtlinien durchgesetzt werden, wenn dieselben Daten für die Aktivierung oder Personalisierung der Zielgruppe verwendet werden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Eingeschlossen | Überwachung ist für die Ereignisweiterleitung unerlässlich. Das Dashboard zur Überwachung der Ereignisweiterleitung bietet Einblicke in Erfolgsraten, Fehlerquoten und Ziel-Antwort-Codes für die Weiterleitung. Warnhinweise sollten für Zielfehler konfiguriert werden. | [Überwachung der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/monitoring) |
| Reporting und Analyse | Empfohlen | Wenn weitergeleitete Ereignisse eine Analyseplattform eines Drittanbieters verwenden, sollten Sie dieselben AEP-Ereignisdatensätze mit CJA verbinden, um eine einheitliche kanalübergreifende Ansicht zu erzielen. Dies ermöglicht einen Vergleich zwischen Adobe-seitigen und Third-Party-seitigen Analysen. | [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Adobe Experience Platform] (AEP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Datenstromkonfiguration | Phase 1: Konfiguration des Datenstroms | Konfigurieren eines Datenstroms für den Empfang von Edge Network-Ereignissen und Aktivieren des Ereignisweiterleitungs-Service |
| Einrichtung der Ereignisweiterleitungs-Eigenschaft | Phase 2: Ereignisweiterleitungseigenschaft und Erweiterungen | Erstellen Sie eine Ereignisweiterleitungseigenschaft und installieren Sie zielspezifische Erweiterungen |
| Definition der Ereignisregel | Phase 3: Definition der Ereignisregel | Regeln definieren, die eingehende Ereignisdaten auswerten und bestimmen, was weitergeleitet und wo |
| Zielzuordnung | Phase 3: Definition der Ereignisregel | Zuordnen von Ereignisdatenelementen zu zielspezifischen Payload-Formaten innerhalb von Weiterleitungsregeln |
| Weiterleitungsausführung | Phase 4: Veröffentlichung und Aktivierung | Veröffentlichen Sie die Ereignisweiterleitungskonfiguration zur Live-Ausführung in der Edge Network |
| Monitoring | Phase 5: Überwachung und Validierung | Überwachen der Erfolgsraten, Fehler-Codes und des Zielstatus der Weiterleitung |

## Voraussetzungen

Stellen Sie vor Beginn der Implementierung sicher, dass Folgendes vorhanden ist.

- [ ] [!DNL Adobe Experience Platform] mit Berechtigung für Edge Network und Ereignisweiterleitung
- [ ] in [!DNL Adobe Admin Console] konfigurierten Datenerfassungsberechtigungen (Eigenschaften, Erweiterungen, Regeln und Veröffentlichung für die Ereignisweiterleitung verwalten)
- [ ] Mindestens ein aktiver Datenerfassungsmechanismus (Web SDK, Mobile SDK oder Server API), der Ereignisse über einen Datenstrom sendet
- [ ] für die zu erfassenden Ereignisdaten definiertes XDM ExperienceEvent-Schema
- [ ] Datenstrom, der erstellt und mit dem Sammlungsmechanismus verknüpft ist
- [ ] Anmeldedaten für den Ziel-Endpunkt und Dokumentation sind verfügbar (z. B. Zugriffstoken der [!DNL Meta] Conversions-API, [!DNL Google Analytics]-Mess-ID, Webhook-URL, Cloud-Speicher-Anmeldedaten)
- [ ] Verständnis des Ereignisdatenmodells und der für jedes Ziel erforderlichen Felder/Ereignisse

## Implementierungsoptionen

In diesem Abschnitt werden die verfügbaren Ansätze zur Implementierung der Ereignisweiterleitung beschrieben und Anleitungen zur Auswahl der richtigen Option bereitgestellt.

### Option A: Erweiterungsbasierte Ereignisweiterleitung

**Am besten geeignet für:** Teams, die gut unterstützte Zielplattformen ([!DNL Meta], [!DNL Google], [!DNL AWS], [!DNL Azure], [!DNL Snowflake] usw.) mit vordefinierten Erweiterungen für die Ereignisweiterleitung, die im Datenerfassungskatalog verfügbar sind.

**Funktionsweise:**

Die erweiterungsbasierte Ereignisweiterleitung nutzt vorgefertigte Integrationen, die von Adobe oder Drittanbieterpartnern verwaltet werden. Jede Erweiterung ist für ein bestimmtes Ziel entwickelt und verarbeitet Authentifizierung, Payload-Formatierung und Endpunktkommunikation. Das Implementierungsprogramm installiert die Erweiterung in der Ereignisweiterleitungs-Eigenschaft, konfiguriert Authentifizierungsberechtigungen und erstellt Regeln, die XDM-Datenelemente den Aktionsfeldern der Erweiterung zuordnen.

Dieser Ansatz minimiert die benutzerdefinierte Entwicklung, da die Erweiterung die API-Anforderungen des Ziels abstrahiert. Beispielsweise übersetzt die API-Erweiterung für [!DNL Meta]-Konversionen XDM-Commerce-Ereignisse in das von [!DNL Meta] erwartete Format, verarbeitet das Hashing von PII-Feldern, Deduplizierungsparameter und verwaltet Zugriffstoken. Ebenso handhaben die [!DNL Google Cloud Platform]- oder [!DNL AWS]-Erweiterungen die Authentifizierung und Payload-Formatierung für ihre jeweiligen Cloud-Services.

Der Nachteil besteht darin, dass die Verfügbarkeit der Erweiterung bestimmt, welche Ziele unterstützt werden. Wenn für ein Ziel keine Erweiterung vorhanden ist, muss stattdessen Option B (benutzerdefinierter Webhook) verwendet werden.

**Wichtige Aspekte:**

- Verfügbarkeit der Erweiterungen variiert — prüfen Sie vor [&#x200B; Planung den &#x200B;](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/overview)Datenerfassungs-Erweiterungskatalog“.
- Erweiterungen werden von Adobe oder Partnern verwaltet; Aktualisierungen können grundlegende Änderungen mit sich bringen, die Regelanpassungen erfordern
- Einige Erweiterungen unterstützen nur bestimmte Ereignistypen oder erfordern bestimmte XDM-Feldzuordnungen
- Erweiterungen handhaben die Authentifizierung und die Verwaltung von Berechtigungen innerhalb ihrer Konfigurations-Benutzeroberfläche

**Vorteile:**

- Schnellste Zeit bis zur Implementierung für unterstützte Ziele
- Vordefinierte Payload-Formatierung reduziert Zuordnungsfehler
- Von der Erweiterung verarbeitete Authentifizierung und Verwaltung von Berechtigungen
- Von Adobe oder zertifizierten Partnern verwaltet und aktualisiert
- Reduzierter benutzerspezifischer Code und geringerer Wartungsaufwand

**Einschränkungen:**

- Auf Ziele mit verfügbaren Erweiterungen beschränkt
- Weniger Flexibilität bei der Anpassung von Payloads im Vergleich zu benutzerdefinierten Webhooks
- Erweiterungsaktualisierungen erfordern möglicherweise eine Neukonfiguration der Regel
- Einige Erweiterungen unterstützen möglicherweise nicht alle Ziel-API-Funktionen

**Experience League:**

- [Erweiterungskatalog für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/overview)
- [Meta Conversions-API-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/snowflake/overview)

### Option B: Benutzerdefinierter Webhook (Fetch-API)-Ereignisweiterleitung

**Am besten geeignet für:** Teams, die Ereignisse an Ziele ohne vordefinierte Erweiterung weiterleiten müssen oder die volle Kontrolle über die Payload der HTTP-Anfrage, die Kopfzeilen und den Authentifizierungsmechanismus benötigen.

**Funktionsweise:**

Benutzerdefinierte Webhook-basierte Ereignisweiterleitung verwendet die [!DNL Adobe Cloud Connector]-Erweiterung (standardmäßig enthalten), um beliebige HTTP-Anfragen an einen beliebigen Endpunkt zu senden. Das Implementierungsprogramm definiert Datenelemente, um Werte aus dem eingehenden XDM-Ereignis zu extrahieren und zu transformieren, und konfiguriert dann eine Regelaktion mit dem Aktionstyp „Abrufanforderung ausführen“ des Cloud-Connectors. Diese Aktion ermöglicht die vollständige Kontrolle über die HTTP-Methode, die URL, die Kopfzeilen und den Anfragetext.

Der Anfragetext wird normalerweise mit Datenelementen und benutzerdefiniertem Code erstellt, um die Payload entsprechend der API-Spezifikation des Ziels zu formatieren. Dieser Ansatz unterstützt alle HTTP-zugänglichen Endpunkte - REST-APIs, Webhooks, Cloud-Funktionen oder interne Services - und stellt somit die flexibelste Option dar.

Der Nachteil ist ein höherer Implementierungsaufwand und eine kontinuierliche Wartung. Der Implementierer muss die Ziel-API verstehen, die Authentifizierung manuell handhaben (z. B. das Festlegen von Autorisierungs-Headern, die Verwaltung der Token-Aktualisierung) und das Payload-Format beibehalten, wenn sich die Ziel-API weiterentwickelt.

**Wichtige Aspekte:**

- Erfordert Verständnis der Ziel-API-Spezifikation (HTTP-Methode, URL-Struktur, Payload-Format, Authentifizierung)
- Authentifizierungsberechtigungen müssen in Datenelementen oder geheimen Daten manuell verwaltet werden
- Benutzerdefinierter Code kann für die Payload-Transformation erforderlich sein (Hashing, Codierung, Umstrukturierung)
- Keine automatischen Aktualisierungen bei Änderung der Ziel-API - manuelle Wartung erforderlich
- Die Secrets-Funktion in der Datenerfassung kann API-Schlüssel und Token sicher speichern

**Vorteile:**

- Unterstützt alle HTTP-zugänglichen Endpunkte - keine Erweiterungsabhängigkeit
- Vollständige Kontrolle über Anfrage-Payload, Kopfzeilen und Authentifizierung
- Kann an interne Services, benutzerdefinierte APIs oder Nischenplattformen weiterleiten
- Ermöglicht komplexe Payload-Umwandlungen mithilfe von benutzerdefiniertem Code
- Kann Wiederholungslogik und Fehlerbehandlung in benutzerdefiniertem Code implementieren

**Einschränkungen:**

- Höherer anfänglicher Implementierungsaufwand
- Laufende Wartungsverantwortung für Payload-Format und Authentifizierung
- Keine vordefinierte Fehlerbehandlung oder Rotation der Anmeldeinformationen - muss manuell implementiert werden
- Erfordert Entwickler-Fachwissen in Bezug auf HTTP-Protokolle und Ziel-API-Besonderheiten

**Experience League:**

- [Adobe Cloud Connector-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Geheimnisse für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/secrets)

### Option C: Hybrid (Erweiterungen + benutzerdefinierte Webhooks)

**Optimiert für:** Organisationen, die Ereignisse an mehrere Ziele weiterleiten, wobei einige über vordefinierte Erweiterungen verfügen und andere eine benutzerdefinierte Integration erfordern.

**Funktionsweise:**

Der hybride Ansatz kombiniert die erweiterungsbasierte Weiterleitung für gut unterstützte Ziele mit benutzerdefinierten Webhook-Aktionen für Ziele, die keine Erweiterungen aufweisen. Eine einzelne Ereignisweiterleitungseigenschaft enthält mehrere Regeln - einige verwenden Erweiterungsaktionen (z. B. [!DNL Meta] Conversions-API-Erweiterung für das Advertising-Konversions-Tracking) und andere verwenden Cloud Connector-Fetch-Aktionen (z. B. die Weiterleitung an einen internen Data Lake-Endpunkt).

Dieser Ansatz maximiert die Abdeckung und minimiert gleichzeitig unnötige benutzerdefinierte Entwicklung. Jede Regel arbeitet unabhängig voneinander, sodass erweiterungsbasierte Regeln von vordefinierter Payload-Formatierung profitieren und benutzerdefinierte Regeln volle Flexibilität behalten.

**Wichtige Aspekte:**

- Die Komplexität von Eigenschaften steigt mit der Anzahl der Regeln und Ziele
- Beim Testen und Debuggen sind möglicherweise unterschiedliche Ansätze für erweiterungsbasierte statt für benutzerdefinierte Regeln erforderlich
- Veröffentlichungsänderungen wirken sich auf alle Regeln in der Eigenschaft aus - verwenden Sie Bibliotheken und Umgebungen, um Änderungen sicher in die Staging-Umgebung einzubringen
- Sie sollten Regeln mit klaren Benennungskonventionen organisieren, um erweiterungsbasierte von benutzerdefinierten Aktionen zu unterscheiden

**Vorteile:**

- Beste Abdeckung über verschiedene Zieltypen hinweg
- Nutzt vordefinierte Erweiterungen, sofern verfügbar, wodurch der Aufwand verringert wird
- Behält Flexibilität für benutzerdefinierte Ziele bei
- Die einzelne Ereignisweiterleitungseigenschaft verwaltet die gesamte Weiterleitungslogik

**Einschränkungen:**

- Höhere Eigenschaftenkomplexität bei mehreren Regeltypen
- Gemischtes Wartungsmodell - Einige Regeln werden automatisch über Erweiterungen aktualisiert, andere erfordern eine manuelle Pflege
- Das Debuggen erfordert Vertrautheit mit Erweiterungskonfigurationen und benutzerdefinierten Abrufmustern

**Experience League:**

- [Übersicht über die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/overview)
- [Erste Schritte mit der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/getting-started)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen verglichen.

| Kriterien | Option A: Erweiterungsbasiert | Option B: Benutzerdefinierter Webhook | Option C: Hybrid |
| --- | --- | --- | --- |
| Am besten geeignet für | Unterstützte Ziele ([!DNL Meta], [!DNL Google], [!DNL AWS] usw.) | Benutzerdefinierte Endpunkte, Nischenplattformen, interne Services | Mehrere Ziele mit gemischter Unterstützung |
| Komplexität | Niedrig | Medium-Hoch | Mittel |
| Zeit bis zur Implementierung | Tage | days-weeks | Variiert je nach Zielmix |
| Flexibilität | Auf Erweiterungsfunktionen beschränkt | Vollzugriff | Vollständige Kontrolle, wo erforderlich |
| Wartung | Niedrig (von Erweiterungen verwaltet) | Hoch (manuelle Wartung) | Gemischt |
| Erfordert | Erweiterung für Ziel verfügbar | Dokumentation zur Ziel-API | Beide, je nach Ziel |
| Benutzerdefinierter Code erforderlich | Minimal | mäßig-signifikant | Variiert |

### Wählen der richtigen Option

Beginnen Sie damit, Ihre Zielziele zu inventarisieren und zu überprüfen, ob für jedes Ziel vordefinierte Erweiterungen für die Ereignisweiterleitung vorhanden sind.

1. **Wenn alle Ziele Erweiterungen haben** — Wählen Sie Option A. Dadurch erhalten Sie die schnellste Implementierung mit dem geringsten Wartungsaufwand. Erweiterungen verwalten Authentifizierung, Payload-Formatierung und API-Versionsverwaltung.

2. **Wenn keine Ziele Erweiterungen haben oder Sie die vollständige Payload-Steuerung benötigen** — Wählen Sie Option B. Verwenden Sie die Cloud Connector-Erweiterung, um benutzerdefinierte HTTP-Anfragen an einen beliebigen Endpunkt zu senden. Dies ist auch die richtige Wahl, wenn Sie komplexe Umwandlungen, benutzerdefiniertes Hashing oder Sendungen an interne Services anwenden müssen.

3. **Wenn Sie eine Mischung aus unterstützten und nicht unterstützten Zielen haben** — Wählen Sie Option C. Verwenden Sie Erweiterungen für Plattformen wie [!DNL Meta], [!DNL Google] und [!DNL AWS] sowie benutzerdefinierte Webhooks für alles andere. Dies ist das häufigste Produktionsszenario für Unternehmen mit diversen Analyse- und Werbe-Stacks.

## Implementierungsphasen

Die folgenden Phasen beschreiben den End-to-End-Implementierungsprozess für die Ereignisweiterleitung.

### Phase 1: Konfiguration des Datenstroms

**Anwendungsfunktion:** AEP: Datenstromkonfiguration

**Was Sie konfigurieren werden:** Ein Datenstrom, der Ereignisse von Ihrer Web-SDK-, Mobile-SDK- oder Server-API-Implementierung empfängt und an den Edge Network weiterleitet, wo Ereignisweiterleitungsregeln sie verarbeiten können. Wenn die Ereignisweiterleitung zu einer vorhandenen Datenerfassungsbereitstellung hinzugefügt wird, aktivieren Sie die Ereignisweiterleitung für den vorhandenen Datenstrom.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Neuer Datenstrom im Vergleich zu vorhandenem Datenstrom**
>
>Sollten Sie einen neuen Datenstrom für die Ereignisweiterleitung erstellen oder die Ereignisweiterleitung für einen vorhandenen Datenstrom aktivieren?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Vorhandenen Datenstrom verwenden | Sie haben bereits eine Web-SDK- oder Server-API, die Ereignisse über einen Datenstrom sendet | Häufigstes Szenario: Die Ereignisweiterleitung wird einfach als zusätzlicher Service für den Datenstrom aktiviert. Es sind keine Client-seitigen Änderungen erforderlich. |
>| Neuen Datenstrom erstellen | Dies ist eine neue Implementierung ohne vorhandene Datenerfassung, oder Sie benötigen einen separaten Datenfluss für bestimmte Ereignistypen | Erfordert, dass die Client-seitige SDK-Konfiguration auf die neue Datenstrom-ID verweist. Ermöglicht eine isolierte Konfiguration. |

>[!NOTE]
>
>**Entscheidung: Welche AEP-Services sollen neben der Ereignisweiterleitung aktiviert werden**
>
>Der Datenstrom kann Ereignisse gleichzeitig an mehrere AEP-Services weiterleiten. Die Ereignisweiterleitung ist ein Service. Andere (AEP-Datenaufnahme, [!DNL Target], [!DNL Analytics]) können parallel ausgeführt werden.
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Ereignisweiterleitung | Sie müssen nur Ereignisse an Ziele weiterleiten, die nicht mit Adobe verbunden sind, und benötigen nicht die Daten in AEP-Datensätzen | Minimiert Datenverarbeitungskosten. Ereignisse fließen durch den Edge Network zu Weiterleitungsregeln, werden jedoch nicht in den Data Lake von AEP aufgenommen. |
>| Ereignisweiterleitung + AEP-Aufnahme | Sie benötigen dieselben Ereignisse sowohl in AEP (für Profile, Zielgruppen, Journey) als auch an externe Systeme weitergeleitet | Häufig für Organisationen, die [!DNL RT-CDP] oder [!DNL AJO] neben Analysen von Drittanbietern verwenden. Der Datenstrom sendet Ereignisse sowohl an AEP-Datensätze als auch an die Regeln für die Ereignisweiterleitung. |
>| Ereignisweiterleitung + mehrere Adobe-Services | Sie benötigen Ereignisse, die gleichzeitig an AEP, [!DNL Target], [!DNL Analytics] und externe Ziele weitergeleitet werden | Aktivieren Sie alle erforderlichen Services für den Datenstrom. Jeder Service erhält das Ereignis unabhängig. |

**UI-Navigation:** [!DNL Experience Platform] > Datenerfassung > Datenströme > Datenstrom auswählen oder erstellen

**Wichtige Konfigurationsdetails:**

- Für den Datenstrom muss die Ereignisweiterleitung unter den erweiterten Einstellungen oder der Service-Konfiguration aktiviert sein
- Verknüpfen der Ereignisweiterleitungseigenschaft (in Phase 2 erstellt) mit dem Datenstrom
- Bestätigen Sie, dass das dem Datenstrom zugewiesene XDM-Schema mit der Ereignisstruktur übereinstimmt, die Ihr Sammlungsmechanismus sendet

**Dokumentation zu Experience League:**

- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)
- [Übersicht über Datenströme](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/overview)
- [Übersicht über die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/overview)

### Phase 2: Ereignisweiterleitungseigenschaft und Erweiterungen

**Anwendungsfunktion:** AEP: Einrichtung der Ereignisweiterleitungs-Eigenschaft

**Was Sie konfigurieren werden:** Eine Ereignisweiterleitungs-Eigenschaft in der Datenerfassungs-Benutzeroberfläche zusammen mit den Erweiterungen, die für Ihre Zielziele erforderlich sind. Die Ereignisweiterleitungseigenschaft ist der Container für alle Regeln, Datenelemente und Erweiterungen, die Ihre Server-seitige Weiterleitungslogik definieren.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Einzelne Eigenschaft im Vergleich zu mehreren Eigenschaften**
>
>Sollten Sie eine Ereignisweiterleitungs-Eigenschaft für alle Ziele oder separate Eigenschaften verwenden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Einzelne Eigenschaft | Die meisten Implementierungen; alle Weiterleitungsregeln verwenden denselben Ereignis-Stream | Einfacher zu verwaltende, einzelne Veröffentlichungs-Workflows, alle Regeln werden für jedes Ereignis ausgewertet. Verwenden Sie Regelbedingungen, um zu filtern, welche Ereignisse zu welchen Zielen führen. |
>| Mehrere Eigenschaften | Sie benötigen verschiedene Teams, um verschiedene Zielintegrationen unabhängig zu verwalten, oder Sie haben strenge Anforderungen an die Umgebungsisolation | Jede Eigenschaft verfügt über einen eigenen Veröffentlichungs-Workflow und kann mit verschiedenen Datenströmen verknüpft werden. Erhöht den Verwaltungsaufwand, verbessert aber die Zugriffssteuerungsgrenzen. |

>[!NOTE]
>
>**Entscheidung: Welche Erweiterungen müssen installiert werden**
>
>Wählen Sie Erweiterungen basierend auf Ihren Zielgruppen und der ausgewählten Implementierungsoption (A, B oder C von oben).
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Zielspezifische Erweiterungen ([!DNL Meta], [!DNL Google], [!DNL AWS] usw.) | Das Ziel verfügt über eine vordefinierte Erweiterung und Sie möchten eine minimale benutzerdefinierte Konfiguration (Option A oder C) | Jede Erweiterung erfordert zielspezifische Anmeldeinformationen (API-Token, Mess-IDs, Konto-IDs). Lesen Sie die Erweiterungsdokumentation für unterstützte Ereignistypen und erforderliche Felder. |
>| Nur Cloud Connector-Erweiterung | Alle Ziele verwenden benutzerdefinierte HTTP-Anfragen (Option B) | Die Cloud Connector-Erweiterung wird standardmäßig installiert. Verwenden Sie die Secrets-Funktion, um API-Schlüssel und Authentifizierungstoken sicher zu speichern. |
>| Zielspezifischer und Cloud-Connector | Sie haben eine Mischung aus unterstützten und benutzerdefinierten Zielen (Option C) | Installieren Sie bestimmte Erweiterungen für gut unterstützte Ziele und verwenden Sie Cloud Connector für den Rest. |

**UI-Navigation:** [!DNL Experience Platform] > Datenerfassung > Ereignisweiterleitung > Eigenschaft erstellen (oder vorhandene auswählen)

**Wichtige Konfigurationsdetails:**

- Benennen Sie die Eigenschaft mit einer eindeutigen Konvention (z. B. „Ereignisweiterleitung - Produktion“ oder „EF - Analytics und Advertising„)
- Installieren der [!DNL Adobe Cloud Connector]-Erweiterung (standardmäßig für benutzerdefinierte Webhook-Aktionen enthalten)
- Installieren Sie zielspezifische Erweiterungen und konfigurieren Sie deren Anmeldeinformationen
- Verwenden Sie die Secrets-Funktion (Datenerfassung > Ereignisweiterleitung > Geheimnisse), um API-Schlüssel, Token und Anmeldeinformationen sicher zu speichern
- Konfigurieren von Umgebungen (Entwicklung, Staging, Produktion) für sichere Veröffentlichungs-Workflows

**Dokumentation zu Experience League:**

- [Erste Schritte mit der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/getting-started)
- [Erweiterungskatalog für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/overview)
- [Geheimnisse für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/secrets)
- [Adobe Cloud Connector-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 3: Definition der Ereignisregel

**Anwendungsfunktion:** AEP: Ereignisregeldefinition, AEP: Zielzuordnung

**Was Sie konfigurieren werden:** Regeln, die eingehende Ereignisdaten auswerten, Bedingungen anwenden, um zu filtern, welche Ereignisse weitergeleitet werden sollen, und Aktionen definieren, die die Daten an Ziel-Endpunkte senden. Jede Regel besteht aus Bedingungen (wann ausgelöst werden soll) und Aktionen (was zu tun ist). Datenelemente extrahieren und transformieren Werte aus der XDM-Ereignis-Payload zur Verwendung in Regelbedingungen und Aktionskonfigurationen.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Ereignisfilterstrategie**
>
>Wie sollten Sie bestimmen, welche Ereignisse an die einzelnen Ziele weitergeleitet werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Alle Ereignisse weiterleiten | Das Ziel benötigt einen vollständigen Ereignis-Stream (z. B. Data Warehouse für die Speicherung von Rohereignissen) | Einfachste Konfiguration - keine Bedingungen erforderlich. Hohe Datenmenge am Ziel. Berücksichtigen Sie die Kosten und Tarifbeschränkungen für das Ziel. |
>| Nach Ereignistyp filtern | Verschiedene Ziele benötigen unterschiedliche Ereignistypen (z. B. Käufe in der Werbung, Seitenansichten in Analytics) | Verwenden Sie Bedingungen, die auf `arc.event.xdm.eventType` oder ähnlichen XDM-Feldern basieren. Reduziert unnötige Daten am Ziel. |
>| Nach Ereignisattributen filtern | Nur bestimmte Ereignisse, die bestimmte Kriterien erfüllen, sollten weitergeleitet werden (z. B. Käufe über einem Schwellenwert oder Ereignisse aus bestimmten Seitenpfaden) | Verwenden Sie Datenelementwerte in Regelbedingungen. Komplexer, aber reduziert Lärm am Ziel. |

>[!NOTE]
>
>**Entscheidung: Ansatz der Datenumwandlung**
>
>Wie sollten XDM-Ereignisdaten für die Ziel-Payload transformiert werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Direkte XDM-Feldzuordnung über Datenelemente | Die Zielfelder werden klar XDM-Feldern zugeordnet (häufig bei der erweiterungsbasierten Weiterleitung) | Erstellen Sie Datenelemente, die auf XDM-Pfade verweisen (z. B. `arc.event.xdm.commerce.order.priceTotal`). Erweiterungen bieten häufig eine Zuordnungs-Benutzeroberfläche. |
>| Benutzerspezifische Code-Umwandlung | Das Ziel erfordert ein Payload-Format, das sich erheblich von XDM unterscheidet, oder Felder müssen gehasht, verkettet oder neu strukturiert werden | Verwenden Sie Datenelemente mit benutzerdefiniertem Code oder benutzerdefinierten Code auf Aktionsebene, um die Payload zu transformieren. Flexibler, aber schwieriger zu warten. |
>| Kombination von Datenelementen und benutzerdefiniertem Code | Einige Felder werden direkt zugeordnet, während andere umgewandelt werden müssen | Verwenden Sie Datenelemente für einfache Zuordnungen und benutzerdefinierte Codeblöcke für komplexe Transformationen. Balancieren Sie Wartbarkeit mit Flexibilität. |

>[!NOTE]
>
>**Entscheidung: Umgang mit personenbezogenen Daten in weitergeleiteten Daten**
>
>Wie sollten persönlich identifizierbare Informationen vor der Weiterleitung gehandhabt werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| PII-Felder vollständig ausschließen | Das Ziel benötigt keine personenbezogenen Daten und die Freigabe wird durch Governance-Richtlinien eingeschränkt | Konfigurieren Sie Regeln, um PII-Felder aus der weitergeleiteten Payload wegzulassen. Einfachster Ansatz für die Einhaltung von Datenschutzbestimmungen. |
>| Hash-PII-Felder vor der Weiterleitung | Das Ziel erfordert Hash-Kennungen (z. B. erfordert [!DNL Meta] SHA-256-Hash-E-Mail für die Konversions-API) | Verwenden Sie Datenelemente mit benutzerdefiniertem Code, um SHA-256-Hashing anzuwenden. Einige Erweiterungen verarbeiten Hashing automatisch. |
>| Forward PII mit vertraglicher Grundlage | Das Ziel verfügt über eine Datenverarbeitungsvereinbarung und die Rechtsgrundlage für die Freigabe von personenbezogenen Daten besteht | Stellen Sie sicher, dass Datennutzungskennzeichnungen und Governance-Richtlinien (S3) die Freigabe zulassen. Dokumentieren Sie die Rechtsgrundlage. |

**UI-Navigation:** [!DNL Experience Platform] > Datenerfassung > Ereignisweiterleitung > Eigenschaft auswählen > Datenelemente/Regeln

**Wichtige Konfigurationsdetails:**

- **Datenelemente** verweisen mithilfe des Pfadpräfix-`arc.event.xdm.` (z. B. `arc.event.xdm.web.webPageDetails.URL` für die Seiten-URL) auf das eingehende XDM-Ereignis
- **Regelbedingungen:** Datenelementwerte aus, um zu bestimmen, ob die Regel ausgelöst werden soll
- **Regelaktionen** Verwenden Sie erweiterungsspezifische Aktionen (für Option A) oder Cloud Connector-Aktionen „Abrufaufruf tätigen“ (für Option B), um Daten an Ziele zu senden
- Jede Regel kann über mehrere Aktionen verfügen, sodass ein einzelnes Ereignis an mehrere Ziele weitergeleitet werden kann
- Verwenden Sie die Regelreihenfolge, um die Reihenfolge der Auswertung zu steuern, wenn mehrere Regeln für dasselbe Ereignis ausgelöst werden können
- Testen Sie Regeln gründlich in der Entwicklungsumgebung, bevor Sie sie in der Produktionsumgebung veröffentlichen

**Wo die Optionen unterschiedlich sind:**

**Für Option A (erweiterungsbasiert):**

Konfigurieren Sie Regelaktionen mithilfe der vordefinierten Aktionstypen der Zielerweiterung. Beispielsweise stellt die Erweiterung der [!DNL Meta] Conversions-API eine Aktion „Ereignis senden“ bereit, bei der Sie XDM-Felder [!DNL Meta] Ereignisparametern (event_name, event_time, user_data, custom_data) zuordnen. Die Erweiterung verarbeitet Payload-Formatierung, Hashing und API-Kommunikation.

**Für Option B (benutzerdefinierter Webhook):**

Konfigurieren Sie Regelaktionen mithilfe der Aktion „Abruf durchführen“ der Cloud Connector-Erweiterung. Geben Sie die Ziel-URL, die HTTP-Methode (normalerweise POST) und die Anfrage-Header (einschließlich Autorisierung) an und erstellen Sie den Anfragetext mit Datenelementen und/oder benutzerdefiniertem Code. Sie sind dafür verantwortlich, das erwartete Payload-Format der Ziel-API genau abzugleichen.

**Für Option C (Hybrid):**

Erstellen Sie separate Regeln für jedes Ziel. Erweiterungsbasierte Regeln verwenden die Aktionstypen der Erweiterung. Benutzerdefinierte Regeln verwenden Cloud Connector-Fetching-Aufrufe. Alle Regeln koexistieren in derselben Eigenschaft und werden unabhängig voneinander für jedes eingehende Ereignis ausgewertet.

**Dokumentation zu Experience League:**

- [Regeln für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/overview)
- [Datenelemente in der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/ui/data-elements)
- [Regeln in der Datenerfassung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/ui/rules)
- [Adobe Cloud Connector-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Phase 4: Veröffentlichung und Aktivierung

**Anwendungsfunktion:** AEP: Ausführung der Weiterleitung

**Was Sie konfigurieren werden:** Der Veröffentlichungs-Workflow, der Ihre Ereignisweiterleitungsregeln von der Entwicklung über die Staging- zur Produktionsumgebung fördert. Die Ereignisweiterleitung verwendet dasselbe bibliotheksbasierte Veröffentlichungsmodell wie Tags, wobei Umgebungen und Build-Artefakte steuern, welche Konfiguration auf der Edge Network aktiv ist.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Strenge des Veröffentlichungs-Workflows**
>
>Wie streng sollte der Veröffentlichungsprozess sein?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Direkt zur Produktion (Entwicklung > Produktion) | Kleine Teams, Ziele mit geringem Risiko oder Proof-of-Concept-Implementierungen | Schnellere Bereitstellung, aber höheres Risiko für Produktionsprobleme. Geeignet für erste Tests mit unkritischen Zielen. |
>| Vollständiger Fortschritt der Umgebung (Entwicklung > Staging > Produktion) | Produktionsimplementierungen mit kritischen Zielen (Werbeplattformen, Data Warehouses) | Wird für alle Produktions-Anwendungsfälle empfohlen. Staging ermöglicht die Validierung mit echtem Traffic vor der Produktionsbereitstellung. |

**UI-Navigation:** [!DNL Experience Platform] > Datenerfassung > Ereignisweiterleitung > Eigenschaft auswählen > Veröffentlichungsfluss

**Wichtige Konfigurationsdetails:**

- Erstellen Sie eine Bibliothek mit allen zu veröffentlichenden Regeln, Datenelementen und Erweiterungskonfigurationen
- Erstellen und testen Sie zunächst in der Entwicklungsumgebung mithilfe des Überwachungs-Tools für die Ereignisweiterleitung , um zu überprüfen, ob Ereignisse korrekt weitergeleitet werden
- Zur Staging-Umgebung für die Validierung vor der Produktion mit Live-Traffic weiterleiten
- Nur nach Bestätigung eines erfolgreichen Versands in der Staging-Umgebung in der Produktion veröffentlichen
- Verwenden der Bibliotheksversionierung, um Änderungen zu verfolgen und bei Bedarf Rollback zu aktivieren

**Dokumentation zu Experience League:**

- [Publishing-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/tags/publish/overview)
- [Bibliotheken](https://experienceleague.adobe.com/de/docs/experience-platform/tags/publish/libraries)
- [Umgebungen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [Builds](https://experienceleague.adobe.com/de/docs/experience-platform/tags/publish/builds)

### Phase 5: Überwachung und Validierung

**Anwendungsfunktion:** AEP: Monitoring

**Was Sie konfigurieren werden:** Überwachung von Dashboards und Validierungsprozessen, um zu bestätigen, dass Ereignisse erfolgreich weitergeleitet werden, Fehler zu diagnostizieren und den Betriebszustand der Ereignisweiterleitungsbereitstellung aufrechtzuerhalten.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>
>**Entscheidung: Überwachungstiefe**
>
>Wie tief sollte die Ereignisweiterleitung überwacht werden?
>
>| Option | Zeitpunkt der Auswahl | Aspekte |
>| --- | --- | --- |
>| Nur Dashboard zur Überwachung der Ereignisweiterleitung | Einfache Überwachung für nicht kritische Ziele oder anfängliche Bereitstellungen | Bietet einen Überblick über Erfolgs-/Fehlerquoten bei der Weiterleitung und Ziel-Antwort-Codes. Ausreichend für die meisten Implementierungen. |
>| Überwachung der Ereignisweiterleitung und zielseitige Validierung | Kritische Ziele, bei denen die Datenvollständigkeit sich direkt auf Geschäftsergebnisse auswirkt (Werbe-Konversions-Tracking, Data Warehouse-Integrität) | Querverweis auf Adobe-seitige Weiterleitungsmetriken mit zielseitiger Empfangsbestätigung. Erfasst Edge-Fälle, in denen das Ziel die Anfrage akzeptiert, die Daten jedoch nicht verarbeitet. |
>| Vollständiger Beobachtbarkeits-Stack (Ereignisweiterleitungsüberwachung + Zielvalidierung + AEP-Warnhinweise) | Bereitstellungen im Unternehmensmaßstab mit SLA-Anforderungen an die Datenbereitstellung | Kombinieren Sie die Überwachung der Ereignisweiterleitung mit Warnhinweisen auf der AEP-Plattform, um eine umfassende Übersicht zu erhalten. Konfigurieren von Warnbenachrichtigungen für Fehlerschwellenwerte bei Weiterleitungen |

**UI-Navigation:** [!DNL Experience Platform] > Datenerfassung > Ereignisweiterleitung > Eigenschaft auswählen > Überwachung

**Wichtige Konfigurationsdetails:**

- Das Überwachungs-Tool für die Ereignisweiterleitung zeigt das Ereignisvolumen, die Erfolgsraten und Fehlerdetails pro Regel und Ziel an
- Überwachen von HTTP-Antwort-Codes von Zielen - 2xx zeigt Erfolg an, 4xx zeigt Client-Fehler (wahrscheinliche Payload- oder Authentifizierungsprobleme) an, 5xx zeigt Fehler auf der Zielseite an
- Verwenden Sie die [!DNL Adobe Experience Platform Debugger] Browser-Erweiterung, um Ereignisse zu überprüfen, die vom Client über die Edge Network zu den Ereignisweiterleitungsregeln fließen
- End-to-End-Validierung durch Überprüfung, ob weitergeleitete Ereignisse im Zielsystem angezeigt werden (z. B. Überprüfung [!DNL Google Analytics] Echtzeitberichte, [!DNL Meta] Events Manager oder Data Warehouse-Tabellen)
- Richten Sie AEP-Warnhinweise für Quell- und Datenflussfehler ein, um Upstream-Probleme zu erfassen, die verhindern würden, dass Ereignisse Ereignisweiterleitungsregeln erreichen

**Dokumentation zu Experience League:**

- [Überwachung der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/de/docs/experience-platform/debugger/home)
- [Warnhinweise - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/alerts/overview)

## Überlegungen bei der Implementierung

In diesem Abschnitt werden Leitplanken, häufige Fallstricke, Best Practices und Entscheidungen zu Kompromissen behandelt, die bei der Implementierung beachtet werden sollten.

### Leitplanken und Beschränkungen

- Die Ereignisweiterleitung verarbeitet Ereignisse in Echtzeit am Edge Network. Standardmäßig gibt es keinen Batch-Modus und keine Warteschlange für weitere Zustellversuche für fehlgeschlagene Sendungen
- Die Ratenbeschränkungen von Edge Network gelten für das gesamte pro Datenstrom verarbeitete Ereignisvolumen - [Edge Network-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- Regeln für die Ereignisweiterleitung werden Server-seitig ausgeführt und können nicht auf Client-seitige Ressourcen (DOM, Cookies, localStorage) zugreifen
- Benutzerdefinierter Code in Ereignisweiterleitungsregeln wird in einer Sandbox-Umgebung ausgeführt - nicht alle Browser-JavaScript-APIs sind verfügbar
- Der Cloud Connector-Abruf-Aufruf hat Zeitüberschreitungsbeschränkungen. Ziele, die langsam reagieren, können zu Zeitüberschreitungen führen
- Die Ereignisweiterleitung unterliegt dem geografischen Routing von Edge Network. -Ereignisse werden am nächsten Edge-Speicherort verarbeitet
- Die maximale Payload-Größe für weitergeleitete Anfragen wird durch Edge Network-Beschränkungen geregelt

### Häufige Fehler

- **Alle XDM-Felder ohne Filterung weiterleiten:** Senden der gesamten XDM-Ereignis-Payload an ein Ziel, das nur wenige Felder benötigt, wird Bandbreite verschwendet, erhöht die Zielkosten und kann unbeabsichtigt personenbezogene Daten freigeben. Ordnen Sie immer nur die erforderlichen Felder in Ihren Weiterleitungsregeln zu.

- **Anmeldeinformationen nicht mit Geheimnissen sichern:** Hartkodierung von API-Schlüsseln oder Token in Datenelementen oder Regelaktionen erzeugt ein Sicherheitsrisiko. Verwenden Sie immer die Funktion „Datenerfassungsgeheimnisse“, um Anmeldeinformationen sicher zu speichern und in Regeln darauf zu verweisen.

- **Ignorieren der Zielratenbeschränkungen:** Drittanbieterziele haben häufig API-Ratenbeschränkungen. Wenn Ihr Ereignisvolumen die Kapazität eines Ziels überschreitet, können Ereignisse gelöscht oder Ihr API-Zugriff gedrosselt werden. Lesen Sie die Zieldokumentation für Ratenbeschränkungen und implementieren Sie Filter, um das Ereignisvolumen bei Bedarf zu reduzieren.

- **Direkte Veröffentlichung in der Produktion ohne Staging:** Überspringen der Staging-Umgebung bedeutet, dass Fehler nur in der Produktion erkannt werden, was möglicherweise zu Datenverlust an kritischen Zielen führt. Immer zuerst mit Live-Traffic im Staging validieren.

- **HTTP-Antwort-Codes werden nicht überwacht** Eine Regel, die ohne Fehler ausgelöst wird, garantiert nicht, dass das Ziel die Daten erfolgreich verarbeitet hat. Überwachen Sie die Ziel-Antwort-Codes (verfügbar im Tool zur Überwachung der Ereignisweiterleitung) und untersuchen Sie alle Nicht-2xx-Antworten.

- **Falsch konfigurierte XDM-Pfadverweise:** Datenelemente verwenden das `arc.event.xdm.` Präfix, um auf eingehende Ereignisfelder zu verweisen. Ein falscher Pfad (z. B. ohne Verschachtelungsebene) erzeugt im Hintergrund Nullwerte, anstatt Fehler auszulösen. Überprüfen von Datenelementwerten mit dem Debugger.

### Best Practices

- **Beginnen Sie mit einem einzelnen Ziel und erweitern Sie** schrittweise: Validieren Sie die End-to-End-Ereignisweiterleitung mit einem Ziel, bevor Sie zusätzliche Regeln und Ziele hinzufügen. Dies vereinfacht das Debugging und schafft Vertrauen in die Infrastruktur.

- **Konsistente Benennungskonventionen verwenden** - Benennen Sie Datenelemente, Regeln und Bibliotheken mit einer eindeutigen Konvention, die das Ziel, den Ereignistyp und die Umgebung identifiziert (z. B. „Regel: Meta - Kaufereignisse“, „DE: Bestellsumme„).

- **Implementierung einer Filterung auf Feldebene für Datenschutz** - Selbst wenn das Ziel angibt, personenbezogene Daten ordnungsgemäß zu verarbeiten, wenden Sie eine Server-seitige Filterung an, um sensible Felder zu entfernen oder zu hashen, bevor sie die Edge Network verlassen. Dies ist der primäre Governance-Vorteil der Ereignisweiterleitung gegenüber Client-seitigen Tags.

- **Version Ihrer Konfigurationen** - Verwenden Sie den Workflow zum Veröffentlichen von Bibliotheken, um versionierte Momentaufnahmen Ihrer Ereignisweiterleitungskonfiguration zu beizubehalten. Dokumentieren Sie, was jede Bibliotheksversion für Audit- und Rollback-Zwecke enthält.

- **Mit Platform Debugger testen** - Die [!DNL Adobe Experience Platform Debugger]-Erweiterung bietet Einblicke in den Ereignislebenszyklus, von der Client-seitigen SDK bis zur Edge Network-Verarbeitung. Verwenden Sie sie während der Entwicklung und der Fehlerbehebung.

- **Regeln für die Ereignisweiterleitung an Ihrem XDM-Schema-Design ausrichten** - Wenn die Ereignisweiterleitung eine bekannte Anforderung ist, entwerfen Sie Ihr XDM-Schema und Ihre Ereignistaxonomie, um die Felder einzuschließen, die Ziele benötigen. Die Nachrüstung von Schemaänderungen nach der Bereitstellung ist umwälzender.

### Entscheidungen über Kompromisse

>[!NOTE]
>
>**Kompromiss: Einfachheit der Erweiterung vs. Webhook-Flexibilität**
>
>Vordefinierte Erweiterungen minimieren den Implementierungsaufwand und die Wartung, beschränken Sie jedoch auf die unterstützten Funktionen und Payload-Formate der Erweiterung. Benutzerdefinierte Webhooks bieten vollständige Kontrolle, erfordern jedoch mehr Entwicklung und laufende Wartung.
>
>- **Erweiterungsbasiert (Option A) bevorzugt:** Markteinführungsgeschwindigkeit, geringere Abhängigkeit von Entwicklern, automatische Verwaltung von Berechtigungen, geringere Wartung
>- **Webhook-basiert (Option B) bevorzugt:** vollständige Payload-Steuerung, Unterstützung für jeden HTTP-Endpunkt, benutzerdefinierte Transformationslogik, Unabhängigkeit von Versionszyklen von Erweiterungen
>- **Empfehlung:** Verwenden Sie Erweiterungen, falls verfügbar und ausreichend. Fallen Sie nur dann auf benutzerdefinierte Webhooks zurück, wenn dem Ziel eine Erweiterung fehlt oder wenn die Erweiterung die benötigten API-Funktionen nicht unterstützt. Der hybride Ansatz (Option C) ist für die meisten Organisationen die pragmatische Wahl.

>[!NOTE]
>
>**Kompromiss: Alle Ereignisse weiterleiten vs. selektive Filterung**
>
>Die Weiterleitung aller Ereignisse an ein Ziel stellt die Vollständigkeit sicher, erhöht jedoch das Datenvolumen, die Zielkosten und die Offenlegung des Datenschutzes. Durch selektive Filterung wird das Rauschen verringert, es besteht jedoch die Gefahr, dass wertvolle Ereignisse verpasst werden.
>
>- **Alle Ereignisse weiterleiten:** Datenvollständigkeit, Einfachheit, Zukunftssicherheit (die Daten sind bei Bedarf später vorhanden)
>- **Selektive Filterung begünstigt:** Kosteneffizienz, geringeres Datenschutzrisiko, sauberere Zieldaten, Einhaltung von Prinzipien zur Datenminimierung
>- **Empfehlung:** Standardeinstellung ist die selektive Filterung nach Ereignistyp und Geschäftsrelevanz. Nur die Ereignisse und Felder weiterleiten, die jedes Ziel tatsächlich benötigt. Dies entspricht den Grundsätzen der Datenminimierung (DSGVO, Artikel 5) und reduziert die Betriebskosten.

>[!NOTE]
>
>**Kompromiss: Einzelne Eigenschaft vs. mehrere Eigenschaften**
>
>Eine einzelne Ereignisweiterleitungs-Eigenschaft ist einfacher zu verwalten, bedeutet jedoch, dass alle Regeln einen Veröffentlichungs-Workflow gemeinsam haben. Mehrere Eigenschaften bieten Isolation, erhöhen jedoch den Verwaltungsaufwand.
>
>- **Einzelne Eigenschaft bevorzugt:** Einfachheit, einheitliche Veröffentlichung, freigegebene Datenelemente, einfacheres Debugging
>- **Mehrere Eigenschaften bevorzugen:** Zugriffskontrolle auf Team-Ebene, unabhängige Veröffentlichungskadenzen, Isolierung von Zielfehlern
>- **Empfehlung** Beginnen Sie bei den meisten Implementierungen mit einer einzigen Eigenschaft. Aufspaltung in mehrere Eigenschaften nur, wenn verschiedene Teams unterschiedliche Zielintegrationen besitzen und unabhängige Versionszyklen benötigen oder wenn die regulatorischen Anforderungen eine strikte Trennung zwischen den Datenflüssen erfordern.

## Verwandte Dokumentation

In den folgenden Ressourcen finden Sie weitere Details zu den Themen, die in diesem Handbuch behandelt werden.

**Ereignisweiterleitung**

- [Übersicht über die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/overview)
- [Erste Schritte mit der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/getting-started)
- [Überwachung der Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/monitoring)
- [Geheimnisse für die Ereignisweiterleitung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/event-forwarding/secrets)

**Erweiterungen für die Ereignisweiterleitung**

- [Katalog der Server-seitigen Erweiterungen](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/overview)
- [Adobe Cloud Connector-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions-API-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads Enhanced Conversions-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp-Erweiterung](https://experienceleague.adobe.com/de/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Datenerfassung und Edge Network**

- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/configure)
- [Übersicht über Datenströme](https://experienceleague.adobe.com/de/docs/experience-platform/datastreams/overview)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/de/docs/experience-platform/web-sdk/home)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/de/docs/experience-platform/edge-network-server-api/overview)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
