---
title: Customer Journey Analytics     Blueprints
description: Zusammenführung und Analyse von Daten und Kundenverhalten aus der gesamten Customer Journey.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
source-git-commit: d7901280f1bc23e6d37bcb285f20343c5ed8b46e
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 100%

---

# Customer Journey Analytics     Blueprints

„Customer Journey Analytics“ zeigt, wie Marken Kundendaten und -verhalten aus unterschiedlichen Interaktionskanälen und -quellen zusammenführen können, um eine Journey-basierte Ansicht aller Kundeninteraktionen zu erstellen. Berichte und Analysen können im Programm-Service Customer Journey Analytics erstellt werden, um Kundeninteraktionen und Verhaltensmuster zu evaluieren und Erkenntnisse daraus zu gewinnen.

Eine vollständige Liste der Anwendungsfälle für Customer Journey Analytics finden Sie hier in der Dokumentation zu Customer Journey Analytics.

## Anwendungsfälle für Customer Journey Analytics

[Häufige Anwendungsfälle sind:](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=de)

* Erstellen und Veröffentlichen von Zielgruppen in Real-time Customer Data Platform
* Obere/untere Konversionspfade
* Kanalinteraktion und Konversion
* Am häufigsten angezeigter Content
* Beste Kategorien und Produkte
* Kampagnen, die zu Konversion und mehr Interaktion führten
* Analyse der Tool-Nutzung zur Optimierung von Self-Service-Erlebnissen

## Architektur für Customer Journey Analytics

![Architekturdiagramm](assets/CJA.svg){zoomable=&quot;yes&quot;}

Beispiele für primäre Anwendungsfälle wie beispielsweise die folgenden.
| Blueprint | Beschreibung | Experience Cloud-Programme |
|---|---|---|
| **[Kanalübergreifende Journey-Analyse](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel.html?lang=de)**  | <ul><li>Erhalten Sie eine zentrale, konsolidierte Sicht auf Kundeninteraktionen auf verschiedenen Kanälen durch Zusammenführung von Daten aus verschiedenen Web-, Mobile- und Offline-Präsenzen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (optional)</li></ul>|
| **[Veröffentlichen von Zielgruppen in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=de)** | <ul><li>Erstellen und veröffentlichen Sie Zielgruppen, die in Customer Journey Analytics (CJA) identifiziert wurden, im Echtzeit-Kundenprofil in Adobe Experience Platform, um Zielgruppenbestimmung und Personalisierung durchzuführen. Ideal zur Erstellung von Zielgruppen mithilfe historischer Daten oder von präziseren Zielgruppen aus granularer Filterung und berechneten Feldern in Customer Journey Analytics.</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> |
| **[Analyse der Anrufabwendung während der Journey](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/call-center.html?lang=de)** | <ul><li>Ermitteln Sie, welche Verhaltensweisen am wahrscheinlichsten mit einem Anruf enden, indem Sie Callcenter-Daten mit Web-, Mobile- und anderen Interaktionsdaten zusammenführen.</li><li>Diese Erkenntnisse können verwendet werden, um das Kundenerlebnis zu verbessern und die Anzahl mitarbeitergestützter Interaktionen durch den Einsatz von Self-Service-Content und -Tools zu reduzieren.  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Leitliniendiagramm für die Blueprints zu Customer Journey Analytics

* Detaillierte Leitlinien und End-to-End-Latenzen finden Sie im Abschnitt [Leitlinien zur Implementierung](../experience-platform/deployment/guardrails.md)

![Leitlinien-Diagramm](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Verwandte Blog-Posts

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
