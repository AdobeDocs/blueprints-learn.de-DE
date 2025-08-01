---
title: 'Blueprint: B2B – Aktivierung von Zielgruppen und Profilen'
description: Stellen Sie mit Real-time Customer Data Platform Account-basierte Zielgruppen und profilorientierte Kundenerlebnisse bereit.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 0509c5a8ce92c25040262130a5f583cdd7f08e59
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 52%

---

# Blueprint: B2B – Aktivierung von Zielgruppen und Profilen

Verwenden Sie Account-, Opportunity- und Lead-Informationen, die mit einem einzelnen Kundinnen bzw. Kunden verknüpft sind, um verwertbare B2B-Profile für verbesserte Personalisierung und Targeting auf allen Kanälen zu erstellen.

## Anwendungsfälle

* Erstellen Sie Zielgruppen von Personen für Targeting und Personalisierung auf allen Kanälen anhand von B2B-Daten zu Accounts Opportunities und Leads.
* Aktivieren Sie Zielgruppen für Targeting und Personalisierung für beliebige Experience Platform-Ziele.
* Erstellen Sie Zielgruppen von Konten (z. B. Unternehmenslisten) und richten Sie sich an diese Unternehmen über Ziele wie LinkedIn, die Listen von Unternehmen als Eingabe akzeptieren oder als Ziel für das Targeting und die Verkaufsförderung in Cloud-Speicher-Ziele exportieren.

## Programme

* Real-time Customer Data Platform B2B Edition

## Integrationsmuster

* B2B-Datenquellen (Marketo, Salesforce usw.) -> Real-time Customer Data Platform B2B edition -> Ziele
* Verschiedene B2B-Datenquellen können verwendet werden, um Account-, Lead-, Opportunity- und Personendaten der B2B edition von Real-time Customer Data Platform zuzuordnen.

## Architektur

![Referenzarchitektur für den B2B-Aktivierungs-Blueprint](assets/b2b-activation.png)

## Leitlinien

* Beachten Sie, dass Leitlinien und Implementierungsschritte für Marketo Engage nur relevant sind, wenn Marketo Engage als Quelle und/oder Ziel verwendet wird.

* Weitere Informationen zu Datenmodellen, Größe und Segmentierung sowie Leitplanken finden Sie im Dokument [Bereitstellungsleitplanken](../experience-platform/guardrails.md)


### Unterstützung mehrerer Instanzen und IMS-Organisationen:

Im Folgenden werden die unterstützten Muster für die Zuordnung von Experience Platform- und Marketo Engage-Instanzen beschrieben.

#### Marketo als Datenquelle für Experience Platform:

* Mehrere Marketo Engage-Instanzen für eine Experience Platform-Instanz werden unterstützt.
* Eine Marketo Engage-Instanz für mehrere Experience Platform-Instanzen wird nicht unterstützt.
* Eine Marketo Engage-Instanz für eine Experience Platform-Instanz und mehrere Sandboxes werden unterstützt.

#### Marketo als Ziel für Experience Platform:

* Experience Platform für mehrere Marketo Engage-Instanzen wird unterstützt
* Mehrere Experience Platform-Instanzen für eine Marketo Engage-Instanz werden unterstützt

#### Leitlinien für Profile und Segmentierung in Experience Platform:

* Die Leitlinien für Profil und Segmentierung in Experience Platform finden Sie unter [Leitlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* B2B-Segmente, die Accounts, Leads und Opportunities enthalten, verwenden Beziehungen mit mehreren Entitäten, die dazu führen, dass die Segmentbewertung in Batches erfolgt. Streaming-Segmentierung wird für Segmente unterstützt, die auf Personen und Ereignisse beschränkt sind.
* Schließen Sie ein Batch-B2B-Segment als Eingabe in ein Streaming- oder Edge-Segment ein, um Anwendungsfälle für Streaming-B2B-Segmente zu unterstützen. Die Batch-Segmentzugehörigkeit basiert auf dem neuesten täglichen Ergebnis der Batch-Segmentierungsauswertung.

#### Experience Platform - Marketo Engage-Quell-Connector:

* Die historische Aufstockung kann je nach Datenvolumen bis zu 7 Tage dauern.
* Laufende Datenaktualisierungen und -änderungen von Marketo werden über die Streaming-API an Experience Platform gesendet. Diese kann für das Profil bis zu etwa 10 Minuten lang latent sein und je nach Volumen bis zu 60 Minuten für den Data Lake dauern.

#### Experience Platform - Marketo-Ziel-Connector:

* Das Streaming der Segmentfreigabe von Real-time Customer Data Platform an Marketo Engage kann nach der Segmentbewertung bis zu 15 Minuten dauern. Das Aufstocken von Profilen, die bereits vor der ersten Aktivierung im Segment vorhanden waren, kann bis zu 24 Stunden dauern.
* Die Batch-Segmentierung wird einmal täglich basierend auf dem Segmentierungsplan von Experience Platformen freigegeben. B2B-Segmente, die Beziehungen mit mehreren Entitäten verwenden, z. B. Segmente, die Daten im Konto und in Opportunity-Objekten verwenden, werden immer im Batch-Modus ausgeführt.

#### Marketo Engage-Leitlinien:

* Kontakte und Leads müssen direkt in Marketo Engage aufgenommen und definiert werden, damit die Real-time Customer Data Platform-Zielgruppe mit einem Marketo Engage-Kontakt und -Lead übereinstimmt.
* Das RTCDP Marketo-Ziel kann optional neue Leads in Marketo für Kunden erstellen, die sich in einem Segment befinden, aber nicht in Marketo vorhanden sind.

#### Ziel-Leitlinien

* Spezifische Anweisungen zu Zielen finden Sie in der Dokumentation zu Zielen. [Ziel-Leitlinien](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=de)


## Implementierungsschritte

Eine Anleitung zur Implementierung und Konfiguration der B2B Edition von Real-time Customer Data Platform finden Sie in der Dokumentation zur B2B Edition von Real-time Customer Data Platform. [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=de)

Es gibt zwei mögliche Implementierungsmuster. Einerseits die Möglichkeit, B2B-Daten und -Profile aus Marketo Engage aufzunehmen, andererseits die Möglichkeit, B2B-Daten aus anderen CRM-Datenquellen zu aufzunehmen.

## Überlegungen bei der Implementierung

Anleitung zu wichtigen Erwägungen und Konfigurationen der Blueprint.

* CRM-Integration mit und ohne Marketo:
Wenn die Implementierung Marketo Engage als Quelle verwendet und Marketo Engage mit dem CRM verbunden ist, fließen die CRM-Daten automatisch über dieselbe Verbindung, sodass das CRM direkt mit Platform verbunden werden muss, es sei denn, es gibt zusätzliche CRM-Datenobjekte, die nicht über Marketo weitergeleitet werden. Verwenden Sie den Experience Platform-Quell-Connector, wenn zusätzliche Tabellen aufgenommen werden müssen. Wenn für die Implementierung nicht Marketo Engage als Quelle verwendet wird, verbinden Sie die CRM-Quelle mithilfe des CRM-Quell-Experience Platform-Connectors direkt mit Platform.
* Der Marketo Engage-Ziel-Connector für Platform, der Zielgruppen zur Aktivierung an Marketo Engage weiterleitet, gibt basierend auf übereinstimmenden E-Mail-Adressen und ECIDs Zielgruppenmitglieder frei. Sie hat die Möglichkeit, einen neuen Lead zu erstellen, wenn der Kontakt noch nicht vorhanden ist. Beim Erstellen eines neuen Leads können bis zu 50 Profilattribute (Nicht-Array- oder Zuordnungsattribute) in der Real-time Customer Data Platform den Personenfeldern in Marketo zugeordnet werden.

## Verwandte Dokumentation

* [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=de)
* [Erste Schritte mit Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Leitplanken für Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=de)
* [Adobe Experience Platform - Marketo-Quell-Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=de)
* [Adobe Experience Platform - Marketo-Ziel-Connector](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=de)
