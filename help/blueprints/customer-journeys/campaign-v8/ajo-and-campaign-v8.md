---
title: 'Blueprint: Journey Optimizer mit Adobe Campaign v8'
description: Zeigt, wie Adobe Journey Optimizer mit Adobe Campaign verwendet werden kann, um nativ mithilfe des Echtzeit-Messaging-Servers in Campaign Nachrichten zu versenden
solution: Journey Optimizer, Campaign, Campaign v8, Campaign v8 Client Console
version: Campaign v8, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: 6ec61ae7e1cfe3bad7beff127dc2e80873424d53
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 52%

---

# Blueprint: Journey Optimizer mit Adobe Campaign v8

Veranschaulicht, wie Adobe [!DNL Journey Optimizer] nativ mit Adobe [!DNL Campaign] verwendet werden kann, um Nachrichten zu senden, indem der Echtzeit-Messaging-Server in [!DNL Campaign] verwendet wird.

## Architektur

<img src="images/ajo-campaign-v8-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>Die Verwendung sowohl von Journey Optimizer als auch von Campaign zum unabhängigen Versand von Nachrichten ist möglich, allerdings müssen dabei einige technische Überlegungen angestellt werden. Wenn Sie diese Route fortsetzen möchten, wenden Sie sich an Ihren Pre-Sales Enterprise Architect, um sicherzustellen, dass Sie wissen, was zur Unterstützung der Implementierung erforderlich ist

<br>

## Voraussetzungen

Überprüfen Sie für jedes Programm die folgenden Voraussetzungen.

### Adobe Experience Platform  

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für klassenbasierte Erlebnisereignis-Schemata die Feldergruppe „Orchestration eventID“ hinzu, wenn Sie ein Ereignis auslösen möchten, das kein regelbasiertes Ereignis ist
* Fügen Sie für einzelne profilklassenbasierte Schemata die Feldergruppe „Profiltestdetails“ hinzu, um Testprofile für die Verwendung mit Journey Optimizer laden zu können
* Journey Optimizer und Campaign werden in derselben IMS-Organisation bereitgestellt.

### Campaign v8

* Adobe Managed Cloud Services muss die Ausführungsinstanz des Echtzeit-Messaging-Services hosten (d. h. Message Center)
* Sämtliches Nachrichten-Authoring erfolgt direkt in der Campaign-Instanz.

## Leitlinien

* [Produktbeschränkungen für Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

* [Leitplanken und End-to-End-Latenzleitfäden](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Implementierungsschritte

Befolgen Sie die unten beschriebenen Implementierungen für jede Anwendung.

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=de) in Experience Platform basierend auf den von der Kundin oder dem Kunden angegebenen Daten.
1. (Optional) Erstellen Sie klassenbasierte Erlebnisereignis-Schemas für die Tabellen Broadlog, trackingLog und Nicht zustellbare Adressen von Adobe Campaign.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Journey-Nutzung.

#### Quellen/Ziele

1. [Aufnehmen von Daten in [!DNL Experience Platform]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=de) mithilfe von Streaming-APIs und Quell-Connectoren.

### Journey Optimizer  

1. Konfigurieren Sie Ihre [!DNL Experience Platform] Datenquelle und bestimmen Sie, welche Felder zwischengespeichert werden sollen
1. Streaming-Daten, die zur Initiierung einer Customer Journey genutzt werden, müssen zunächst in Journey Optimizer konfiguriert werden, um eine Orchestrierungs-ID zu erhalten. Die Orchestrierungs-ID wird dann an den Entwickler weitergegeben, der sie bei der Aufnahme nutzen kann.
1. Konfigurieren Sie externe Datenquellen.
1. Konfigurieren Sie benutzerdefinierte Aktionen für die Campaign-Instanz.

### Campaign v8

* Messaging-Vorlagen müssen mit dem entsprechenden Personalisierungskontext konfiguriert werden.
* Für [!DNL Campaign] Standard: Export-Workflows müssen so konfiguriert werden, dass die Transaktionsnachrichten-Protokolle zurück in die Experience Platform exportiert werden. Es wird empfohlen, höchstens alle vier Stunden zu laufen.
* Für [!DNL Campaign] v8.4 ist es möglich, den Adobe [!DNL Campaign] Managed Services Source Connector in Experience Platform zu nutzen, um Versand- und Tracking-Ereignisse von Campaign mit Experience Platform zu synchronisieren. Weitere Informationen finden Sie in der Dokumentation zum [Source](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=de)Connector.

### Mobilgeräte-Push-Konfiguration (optional)

1. Implementieren Sie [!DNL Experience Platform] Mobile SDK , um Push-Token und Anmeldeinformationen zu erfassen und so eine Verbindung zu bekannten Kundenprofilen herzustellen.
1. Nutzen Sie Adobe Tags und erstellen Sie eine Mobile-Präsenz mit der folgenden Erweiterung:
   * Adobe [!DNL Journey Optimizer] | Adobe [!DNL Campaign Classic] | Adobe [!DNL Campaign Standard]
   * Adobe [!DNL Experience Platform] [!DNL Edge Network]
   * Identität für [!DNL Edge Network]
   * Mobile Core
1. Stellen Sie sicher, dass Sie über einen dedizierten Datenstrom für Mobile-App-Bereitstellungen im Vergleich zu Web-Bereitstellungen verfügen.
1. Weitere Informationen finden Sie im [Adobe Journey Optimizer Mobile-Handbuch](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer/push-notification/).

   >[!IMPORTANT]
   >Mobile-Token müssen sowohl in Journey Optimizer als auch in Campaign erfasst werden, wenn Echtzeit-Kommunikation über Journey Optimizer gesendet werden soll und Push-Benachrichtigungen im Batch über Campaign übermittelt werden sollen. Campaign v8 erfordert die exklusive Verwendung des Campaign SDK für das Erfassen von Push-Tokens.

## Verwandte Dokumentation

* [Dokumentation zu Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=de)
* [Produktbeschreibung zu Journey Optimizer](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer.html)
* [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=de)
