---
title: '[!DNL Journey Optimizer] - Ausgelöste Nachrichten und Adobe Experience Platform-Blueprint'
description: Führen Sie ausgelöste Nachrichten und Erlebnisse mit Adobe Experience Platform als Zentrale für gestreamte Daten, Kundenprofile und Segmentierung aus.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: f8b9cc115739b53bba71d06b228dcce57df9dd7b
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 53%

---

# [!DNL Journey Optimizer] Blueprints

Adobe [!DNL Journey Optimizer] ist ein speziell entwickeltes System, mit dem Marketing-Teams in Echtzeit auf Kundenverhalten reagieren und sie dort treffen können, wo sie sich befinden. Die Data-Management-Funktionen wurden auf die Adobe [!DNL Experience Platform] verschoben, sodass sich Marketing-Teams auf das konzentrieren können, was sie am besten erreichen: die Erstellung von erstklassigem Journey und personalisierten Konversationen.

In diesem Blueprint werden die technischen Funktionen der Anwendung beschrieben und die verschiedenen architektonischen Komponenten, aus denen [!DNL Journey Optimizer] besteht, werden eingehend erläutert.

## Anwendungsfälle

* Trigger-basierte Nachrichten
* Begrüßung und Registrierungsbestätigungen
* Abgebrochene Warenkörbe und Anmeldeformulare
* Standortbasierte Nachrichten
* Erlebnisse im Stadion
* Erlebnisse in Touristik und Gastgewerbe vor der Ankunft und während des Aufenthalts

## Architektur

<img src="assets/ajo-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Blueprint-Szenarios

| Szenario | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [Drittanbieter-Messaging](3rd-party-messaging.md) | Veranschaulicht, wie Adobe [!DNL Journey Optimizer] mit Drittanbieter-Messaging-Systemen verwendet werden kann, um personalisierte Nachrichten zu orchestrieren und zu senden | Stellen Sie in Echtzeit personalisierte 1:1-Kommunikationen für Kunden bereit, während diese mit Ihrer Marke oder Ihrem Unternehmen interagieren.<br><br>Überlegungen:<br><ul><li>Drittanbietersystem muss Inhaber-Token für die Authentifizierung unterstützen</li><li>Keine Unterstützung für statische IPs aufgrund der Mehrmandanten-Architektur</li><li>Beachten Sie Einschränkungen der Architektur bei Drittanbietersystemen hinsichtlich API-Aufrufen pro Sekunde. Möglicherweise muss der Kunde beim Drittanbieter zusätzliche Mengen kaufen, um das Volumen von [!DNL Journey Optimizer] zu unterstützen.</li><li>Entscheidungs-Management wird in Nachrichten oder Payloads nicht unterstützt</li></ul> |

<br>

## Integrationsmuster

| Integration | Beschreibung | Funktionen |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] mit Adobe Campaign](ajo-and-campaign.md) | Zeigt, wie Sie Adobe [!DNL Journey Optimizer] verwenden können, um 1:1-Erlebnisse mithilfe des Echtzeit-Kundenprofils zu orchestrieren und das native Adobe Campaign-Transaktionsnachrichtensystem zu nutzen, um die Nachricht zu senden | Nutzen Sie das Echtzeit-Kundenprofil und die Leistungsfähigkeit von [!DNL Journey Optimizer], um im Moment Erlebnisse zu orchestrieren und gleichzeitig die nativen Echtzeit-Messaging-Funktionen von Adobe Campaign zu nutzen, um die letzte Meilenkommunikation durchzuführen.<br><br>Zu beachten:<br><ul><li>Campaign muss v7, Build >21.1 oder v8 sein</li><li>Messaging-Durchsatz</li><ul><li>Campaign v7 - bis zu 50.000 pro Stunde</li><li>Campaign v8 - bis zu 1 Mio. pro Stunde</li><li>Campaign Standard - bis zu 50.000 pro Stunde</li></ul><li>Es wird kein Throttling durchgeführt, Anwendungsfälle erfordern also eine technische Überprüfung durch einen Enterprise Architect</li><li>Keine Unterstützung für die Verwendung von Entscheidungs-Management in von Campaign versendeten Nachrichten</li></ul> |

<br>

## Voraussetzungen

Adobe [!DNL Experience Platform]:

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie [!DNL Journey Optimizer]-Datenquellen konfigurieren können
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für klassenbasierte Einzelprofile die Feldergruppe &quot;Profiltestdetails&quot;hinzu, um Testprofile zur Verwendung mit [!DNL Journey Optimizer] laden zu können.

E-Mail:

* Eine Subdomain muss verfügbar sein, die für den Versand von Nachrichten verwendet werden kann
* Die Subdomain kann entweder komplett an Adobe delegiert werden (empfohlen) oder CNAMEs können zum Verweis an Adobe-spezifische DNS-Server (benutzerdefiniert) verwendet werden
* Für jede Subdomain ist ein Google-TXT-Datensatz erforderlich, um gute Zustellbarkeit sicherzustellen

Mobile Push:

* Der Kunde muss über einen Mobile-Entwickler verfügen, der die Mobile App erstellen kann
* Adobe Experience Platform Mobile SDK

## Leitlinien

[[!DNL Journey Optimizer] Schutzmechanismen - Produktlink](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[Limits und Ende-zu-Ende-Latenzrichtlinien](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Verwandte Dokumentation

* [[!DNL Experience Platform] Dokumentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [[!DNL Experience Platform] Dokumentation zu Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de)
* [[!DNL Experience Platform Mobile SDK] Dokumentation](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
* [[!DNL Journey Optimizer] Dokumentation](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [[!DNL Journey Optimizer] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
