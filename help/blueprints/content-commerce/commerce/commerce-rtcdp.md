---
title: Adobe Commerce - RTCDP-Blueprint
description: Integration von Adobe Experience Platform mit Adobe Commerce, um eine einheitliche Sicht auf Kunden zu schaffen und Erlebnisse in einer digitalen Storefront und kanalübergreifend intelligent zu personalisieren.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 80a4716a7ed64ec30b9c60b3444affc5bd8984e4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# Adobe Commerce und RTCDP

Die [!DNL Data Connection]-Erweiterung unterstützt Kunden von Adobe Commerce bei der nahtlosen Integration in Adobe Experience Platform, um das Kundenprofil zu erweitern und Erlebnisse in digitalen Storefronts und anderen Kanälen zu personalisieren.

## Aktivierte technische Funktionen

* Storefront-Daten (Client-seitig, z. B. zum Warenkorb hinzufügen, Warenkorbabbrüche usw.) werden erfasst und an ein beliebiges Adobe Experience Cloud-Produkt gesendet.
* Back-Office-Bestellstatus für jedes Adobe Experience Cloud-Produkt
* Historische Back-Office-Bestellungen können an Adobe Experience Platform gesendet werden
* Freigeben und Personalisieren von RTCDP-Zielgruppen in Adobe Commerce

## Voraussetzungen

Um die [!DNL Data Connection]-Erweiterung verwenden zu können, müssen Sie über Folgendes verfügen:

* Adobe Commerce 2.4.4 oder neuer
* Adobe ID und Organisations-ID
* Adobe Experience Platform/RTCDP
* [Adobe-Client-Datenschicht (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=de). Die ACDL ist erforderlich, um Storefront-Ereignisdaten zu erfassen.

## Onboarding-Schritte

### Datenerfassung von Adobe Commerce an Adobe Experience Platform

* [Installieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html?lang=de) der [!DNL Data Connection].
* [Melden Sie sich ](https://helpx.adobe.com/de/manage-account/using/access-adobe-id-account.html) Ihrem Adobe-Konto an und zeigen Sie an, um Ihre Organisations-ID zu bestätigen. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge gefolgt von @AdobeOrg (zwingend erforderlich).
* [Erstellen oder aktualisieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html?lang=de) Sie Ihr XDM-Schema mit Commerce-spezifischen Feldergruppen.
* [Erstellen eines Datensatzes](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=de#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die gesendeten Commerce-Daten.
* [Erstellen Sie einen Datenstrom](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=de) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
* [Verbindung zu Commerce Services herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=de).
* [Verbindung zu Adobe Experience Platform herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html?lang=de).

### Herstellen einer Verbindung zum Commerce-Ziel über Adobe Experience Platform für die Zielgruppenfreigabe

So stellen Sie eine Verbindung mit dem Adobe Commerce-Ziel her:

* Navigieren Sie in der [Adobe Experience Platform](https://experience.adobe.com/platform/)Benutzeroberfläche zu Ziele > Katalog.
* Wählen Sie Personalization aus.
* Wählen Sie das Adobe Commerce-Ziel aus, um es zu markieren, und wählen Sie dann Einrichten aus.
* Führen Sie die im Abschnitt [Tutorial zur Zielkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=de) beschriebenen Schritte aus.

## Vorkonfigurierte Daten

* Storefront (Browser/App)-Ereignisse
* Back-Office-Ereignisse
* Historische Bestelldaten

Eine vollständige Liste der unterstützten Ereignisse finden Sie unter [Commerce-Ereignisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html?lang=de)

## Architektur

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP-Architektur" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Verwandte Implementierungshandbücher

| Leitfaden | Link |
|:----|:----|
| Platform-Connector | [Übersicht über den Adobe Commerce Experience Platform-Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html?lang=de) |
| Commerce-Ziel | [Adobe Commerce-Verbindung in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=de) |
| Edge Personalization | [Aktivieren von Zielgruppen für Edge-Personalisierungsziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=de) |
