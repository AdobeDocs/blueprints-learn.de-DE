---
title: B2B-Aktivierung
description: Stellen Sie mit Real-time Customer Data Platform ​ kontobasierte Zielgruppen und profilorientierte Kundenerlebnisse bereit.
solution: Experience Platform, Real-time Customer Data Platform
kt: 9311
exl-id: null
source-git-commit: d811d82418d477372caa9e5b0b67af197275d459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 5%

---

# B2B-Zielgruppe und Profilaktivierung

Verwenden Sie Konto-, Opportunities- und Lead-Informationen, die an einen einzelnen Kunden gebunden sind, um umsetzbare b2b-Profile zu erstellen, um die Personalisierung und das Targeting kanalübergreifend zu verbessern.

## Anwendungsfälle

* Erstellen Sie Zielgruppen von Personen für die kanalübergreifende Zielgruppenbestimmung und Personalisierung anhand von B2B-Daten, einschließlich Konten, Chancen und Leads.
* Aktivieren Sie Zielgruppen für Targeting und Personalisierung in allen Experience Platform-Zielen.

## Programme

* Real-Time Customer Data Platform B2B Edition

## Integrationsmuster

* B2B-Datenquellen (Marketo, Salesforce usw.) -> Real-time Customer Data Platform B2B Edition -> Ziele Verschiedene B2B-Datenquellen können verwendet werden, um Konto-, Lead-, Opportunity- und Personendaten der B2B Edition von Real-time Customer Data Platform zuzuordnen.

## Architektur

<img src="assets/b2b-activation.svg" alt="Referenzarchitektur für das B2B Activation Blueprint" style="border:1px solid #4a4a4a" />
<br>

## Leitlinien

Beachten Sie, dass Marketo Engage-bezogene Limits und Implementierungsschritte nur relevant sind, wenn Marketo Engage als Quelle und/oder Ziel verwendet wird.

### Unterstützung mehrerer Instanzen und IMS-Organisation:

Im Folgenden werden die unterstützten Muster für die Zuordnung von Experience Platform- und Marketo Engage-Instanzen beschrieben.

#### Marketo als Datenquelle für die Experience Platform:

* Mehrere Marketo Engage-Instanzen in einer Experience Platform-Instanz werden unterstützt.
* Mehrere Marketo Engage-Instanzen zu vielen Experience Platform-Instanzen werden nicht unterstützt.
* Eine Marketo Engage-Instanz zu vielen Experience Platform-Instanzen wird nicht unterstützt.
* Eine Marketo Engage-Instanz zu einer Experience Platform-Instanz und mehrere Sandboxes werden unterstützt.

#### Marketo als Ziel für die Experience Platform:

* Experience Platform zu vielen Marketo Engage-Instanzen wird unterstützt
* Es werden viele Experience Platform-Instanzen zu einer Marketo Engage-Instanz unterstützt

#### Limits für das Experience Platform-Profil und die Segmentierung:

* Profils- und SegmentierungsLimits für die Experience Platform anzeigen - [Profil- und Segmentierungsrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* B2B-Segmente, die Konten, Leads und Chancen enthalten, verwenden Beziehungen mit mehreren Entitäten, die dazu führen, dass die Segmentbewertung zu Batches wird. Streaming-Segmentierung wird für Segmente unterstützt, die auf Personen und Ereignisse beschränkt sind.

#### Experience Platform - Marketo Engage Source Connector:

* Die frühere Aufstockung kann je nach Datenvolumen bis zu 7 Tage dauern.
* Laufende Datenaktualisierungen und -änderungen aus Marketo werden über die Streaming-API an Experience Platform gesendet, die je nach Volumen bis zu 5 Minuten und ca. 15 Minuten bis zum Data Lake reichen kann.

#### Experience Platform - Marketo Destination Connector:

* Die Freigabe von Streaming-Segmenten von Real-time Customer Data Platform nach Marketo Engage kann bis zu 5 Minuten dauern.
* Die Batch-Segmentierung wird einmal täglich basierend auf dem Zeitplan für die Segmentierung von Experience Platformen freigegeben. B2B-Segmente, die Konten, Leads und Chancen enthalten, verwenden Beziehungen mit mehreren Entitäten, die dazu führen, dass das Segment Batch wird.

#### Marketo Engage-Limits:

* Kontakte und Leads müssen direkt in Marketo Engage erfasst und definiert werden, damit die Real-time Customer Data Platform-Audience mit einem Marketo Engage-Kontakt und -Lead übereinstimmt.

#### Ziel-Limits

* Spezifische Anweisungen zu Zielen finden Sie in der Zieldokumentation . [Zielrichtlinien](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en)


## Implementierungsschritte

Eine Anleitung zur Implementierung und Konfiguration der B2B Edition der Real-time Customer Data Platform finden Sie in der Dokumentation zu B2B Edition der Real-time Customer Data Platform. [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Es gibt zwei mögliche Implementierungsparameter. Sowohl die Möglichkeit, B2B-Daten und -Profile aus Marketo Engage zu erfassen, als auch die Möglichkeit, B2B-Daten aus anderen CRM-Datenquellen zu erfassen.

## Überlegungen bei der Implementierung

Anleitung zu wichtigen Erwägungen und Konfigurationen des Blueprints.

* CRM-Integration mit und ohne Marketo: Wenn die Implementierung Marketo Engage als Quelle verwendet und Marketo Engage mit dem CRM verbunden ist, verwenden Sie den Marketo-Quell-Connector in Experience Platform, um die CRM-Daten in Experience Platform aufzunehmen. Verwenden Sie den Quell-Connector der Experience Platform , wenn zusätzliche Tabellen erfasst werden müssen. Wenn in der Implementierung Marketo Engage nicht als Quelle verwendet wird, verbinden Sie die CRM-Experience Platform über den Connector der CRM-Quellquelle direkt mit AEP.
* Lead-Initiierung und Pflege aus der B2B Edition von Real-time Customer Data Platform allein wird nicht empfohlen. Für diesen Anwendungsfall wird die Verwendung eines Bleistiftungs-Tools (wie Marketo Engage) empfohlen.
* Der Marketo Engage-Ziel-Connector für AEP, der Zielgruppen zur Aktivierung an Marketo Engage sendet, E-Mail-Adressen und ECIDs nur sendet. Es wird kein neuer Lead erstellt, wenn der Kontakt noch nicht vorhanden ist. Daher muss er das Profil erfassen und Daten in Marketo Engage einfügen.

## Verwandte Dokumentation

* [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=de)
* [Adobe Experience Platform - Marketo Destination Connector](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)