---
title: Ereignisweiterleitung
description: Erfahren Sie, wie Sie über Edge Network erfasste Echtzeit-Ereignisdaten zur Analyse, Speicherung oder Werbung an Ziele weiterleiten, die nicht mit Adobe verbunden sind.
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# Ereignisweiterleitung

In diesem Handbuch wird das Anwendungsfallmuster für die Ereignisweiterleitung beschrieben, bei dem die Server-seitige Verarbeitung auf [!DNL Adobe Experience Platform] Edge Network verwendet wird, um Echtzeit-Ereignisdaten an Ziele zu verteilen, die nicht mit Adobe verbunden sind - z. B. Analyseplattformen von Drittanbietern, Cloud-Speicher-Endpunkte, Werbenetzwerke oder benutzerdefinierte Webhooks. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

## Anwendungsfallmuster

In diesem Abschnitt werden das Muster und der Ausführungsplan beschrieben, die zur Implementierung der Ereignisweiterleitung verwendet werden.

**Ereignisweiterleitung** - Weiterleiten von über Edge Network erfassten Echtzeit-Ereignisdaten an Nicht-Adobe-Ziele zu Analyse-, Speicher- oder Werbezwecken.

**Ausführungsplan:** Datenstromkonfiguration > Ereignisregeldefinition > Zielzuordnung > Weiterleitungsausführung > Überwachung

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

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Experience Platform] (Edge Network)** - Empfängt Echtzeit-Ereignisdaten von Web SDK, Mobile SDK oder der Server-API und leitet sie über konfigurierte Datenströme weiter.
- **[!DNL Adobe Experience Platform] (Ereignisweiterleitung)** - Stellt die Server-seitige Regel-Engine zum Auswerten, Filtern, Transformieren und Weiterleiten von Ereignisdaten an externe Ziele bereit
- **[!DNL Adobe Experience Platform] (Tags/Datenerfassung)** - Verwaltet den Lebenszyklus, die Erweiterungen, die Regeln und den Veröffentlichungs-Workflow der Ereignisweiterleitungs-Eigenschaft

## Verwandte Dokumentation

In den folgenden Ressourcen finden Sie weitere Details zu den Themen, die in diesem Handbuch behandelt werden.

**Ereignisweiterleitung**

- [Übersicht über die Ereignisweiterleitung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [Erste Schritte mit der Ereignisweiterleitung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/getting-started)
- [Überwachung der Ereignisweiterleitung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Geheimnisse für die Ereignisweiterleitung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**Erweiterungen für die Ereignisweiterleitung**

- [Katalog der Server-seitigen Erweiterungen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Adobe Cloud Connector-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions-API-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads Enhanced Conversions-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp-Erweiterung](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**Datenerfassung und Edge Network**

- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über Datenströme](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
