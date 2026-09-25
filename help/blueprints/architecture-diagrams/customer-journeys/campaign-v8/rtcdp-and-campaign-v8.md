---
title: Muster für die Integration von Real-Time CDP mit Adobe Campaign v8
description: Zeigt, wie Adobe Experience Platform und das Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign v8 genutzt werden können, um personalisierte Konversationen bereitzustellen
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
TQID: https://experienceleague.adobe.com/LANKBKui1B5RfyNI8ufsgjrC98TXpAf74IB-alwDTnk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 79738031788419872e32b8f754febacbfd18cc06
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 72%
---
# [!DNL Real-Time CDP] mit dem Integrationsmuster für Adobe [!DNL Campaign] v8

Zeigt, wie die Adobe-[!DNL Experience Platform] und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign verwendet werden können, um personalisierte Konversationen bereitzustellen.

## Programme

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architektur

![Referenzarchitektur für das Integrationsmuster von Batch-Messaging und Adobe Experience Platform](images/campaign-v8-with-rtcdp.png){width="1000" zoomable="yes"}

<br>

## Voraussetzungen

* Der Kunde muss über eine gültige IMS Org für Experience Cloud verfügen
* Es wird empfohlen, Adobe Experience Platform und [!DNL Campaign] in derselben IMS-Organisation für eine einzige Anmelde-URL bereitzustellen
* Kunde muss über die v8-Instanz von [!DNL Campaign] verfügen
* Der Kunde muss über eine Berechtigung und den Zugriff auf die Quellen und Ziele von Real-Time Customer Data Platform verfügen.
* Adobe [!DNL Campaign]-Produktkontext muss vorhanden sein

<br>

## Implementierungsschritte

Weitere Informationen zum Konfigurieren des Quell-Connectors von Campaign v8 für Adobe Experience Platform und des Ziel-Connectors von Real-time Customer Data Platform für Campaign v8 finden Sie in der folgenden Dokumentation.
[Campaign- und AEP-Connectoren](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=de)

## Leitlinien

### Adobe Campaign

* Weitere Informationen finden Sie in der Dokumentation zum Quell-Connector von Campaign – [Campaign-Quell-Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=de)
* Unterstützt nur die Bereitstellung einzelner Organisationseinheiten von Adobe Campaign


### Segmentfreigabe in Experience Platform Real-time Customer Data Platform

* Siehe den Ziel-Connector von Real-time Customer Data Platform für Campaign – [Verbindung von Real-time Customer Data Platform mit Campaign](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=de)

* Siehe Leitlinien für die Profil- und Datenaufnahme für AEP – [Link](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
