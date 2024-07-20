---
title: Adobe Commerce - RTCDP-Blueprint
description: Adobe Experience Platform-Integration mit Adobe Commerce , um eine zentrale Ansicht von Kunden zu erstellen und Erlebnisse in einem digitalen Storefront und kanalübergreifend intelligent zu personalisieren.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 80a4716a7ed64ec30b9c60b3444affc5bd8984e4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# Adobe Commerce und RTCDP

Die Erweiterung [!DNL Data Connection] unterstützt Adobe Commerce-Kunden bei der nahtlosen Integration in Adobe Experience Platform, um das Kundenprofil anzureichern und Erlebnisse in digitalen Storefront- und anderen Kanälen zu personalisieren.

## Technische Funktionen aktiviert

* Storefront-Daten (Client-seitig, z. B. zum Warenkorb hinzufügen, Warenkorbabbrüche usw.), die erfasst und an ein Adobe Experience Cloud-Produkt gesendet werden.
* Bestellstatus eines beliebigen Adobe Experience Cloud-Produkts im Büro wiederherstellen
* Historische Bestellungen von Back Office können an Adobe Experience Platform gesendet werden.
* RTCDP-Zielgruppen für Adobe Commerce freigeben und personalisieren

## Voraussetzungen

Um die Erweiterung [!DNL Data Connection] zu verwenden, müssen Sie über Folgendes verfügen:

* Adobe Commerce 2.4.4 oder höher
* Adobe ID- und Organisations-ID
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ACDL ist erforderlich, um Storefront-Ereignisdaten zu erfassen.

## Onboarding-Schritte

### Datenerfassung von Adobe Commerce nach Adobe Experience Platform

* [Installieren Sie](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html) die Erweiterung [!DNL Data Connection] .
* [ Melden Sie sich bei Ihrem Adobe-Konto an und zeigen Sie an, um Ihre Organisations-ID zu bestätigen. ](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge, gefolgt von @AdobeOrg (erforderlich).
* [Erstellen oder aktualisieren Sie](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html) Ihr XDM-Schema mit Commerce-spezifischen Feldergruppen.
* [Erstellen Sie einen Datensatz](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die von Ihnen gesendeten Commerce-Daten.
* [Erstellen Sie einen Datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
* [Verbindung zu Commerce Services herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).
* [Verbindung zu Adobe Experience Platform herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html).

### Verbindung zum Commerce-Ziel über Adobe Experience Platform für Zielgruppenfreigabe herstellen

Herstellen einer Verbindung zum Adobe Commerce-Ziel:

* Wechseln Sie in der Benutzeroberfläche [Adobe Experience Platform](https://experience.adobe.com/platform/) zu Ziele > Katalog.
* Wählen Sie Personalization aus.
* Wählen Sie das Adobe Commerce-Ziel aus, um es zu markieren, und wählen Sie dann Einrichten aus.
* Führen Sie die im Tutorial [Zielkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html) beschriebenen Schritte aus.

## Vordefinierte Daten

* Storefront-Ereignisse (Browser/App)
* Back-Office-Ereignisse
* Historische Bestelldaten

Eine vollständige Liste der unterstützten Ereignisse finden Sie unter [Commerce-Ereignisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)

## Architektur

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP-Architektur" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Verwandte Implementierungshandbücher

| Leitfaden | Link |
|:----|:----|
| Platform Connector | [Übersicht über den Adobe Commerce Experience Platform-Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html) |
| Commerce-Ziel | [Adobe Commerce-Verbindung in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html) |
| Edge Personalization | [Aktivieren von Zielgruppen für Edge-Personalisierungsziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html) |
