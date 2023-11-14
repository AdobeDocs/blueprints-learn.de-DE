---
title: Adobe Commerce - RTCDP-Blueprint
description: Adobe Experience Platform-Integration mit Adobe Commerce , um eine zentrale Ansicht von Kunden zu erstellen und Erlebnisse in einem digitalen Storefront und kanalübergreifend intelligent zu personalisieren.
solution: Real-Time Customer Data Platform, Commerce
source-git-commit: abb946358ceeee1af427c5b362ed2f48f733a6c9
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Adobe Commerce und RTCDP

Dieses integrierte Erlebnis hilft Adobe Commerce-Kunden bei der nahtlosen Intergration mit Adobe Experience Platform, um das Kundenprofil anzureichern und Erlebnisse in digitalen Storefront- und anderen Kanälen zu personalisieren.

## Technische Funktionen aktiviert

* Storefront-Daten (clientseitig), die erfasst und an ein Adobe Experience Cloud-Produkt gesendet werden. (Zum Warenkorb hinzufügen, Warenkorbabbrüche usw.)
* Bestellstatus eines beliebigen Adobe Experience Cloud-Produkts im Büro wiederherstellen
* Historische Bestellungen von Back Office können an Adobe Experience Platform gesendet werden.
* RTCDP-Zielgruppen für Adobe Commerce freigeben und personalisieren

## Voraussetzungen

Um den Experience Platform-Connector zu verwenden, müssen Sie über Folgendes verfügen:

* Adobe Commerce 2.4.4 oder höher
* Adobe ID- und Organisations-ID
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=en). ACDL ist erforderlich, um Storefront-Ereignisdaten zu erfassen.

## Onboarding-Schritte

### Datenerfassung von Adobe Commerce nach Adobe Experience Platform

* [Installieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) die Experience Platform-Connector-Erweiterung.
* [Anmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) auf Ihr Adobe-Konto klicken und anzeigen, um Ihre Organisations-ID zu bestätigen. Die Organisations-ID ist die ID, die Ihrem bereitgestellten Experience Cloud-Unternehmen zugeordnet ist. Diese ID besteht aus einer 24-stelligen alphanumerischen Zeichenfolge, gefolgt von @AdobeOrg (erforderlich).
* [Erstellen oder aktualisieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/update-xdm.html?lang=en) Ihr XDM-Schema mit Commerce-spezifischen Feldergruppen.
* [Datensatz erstellen](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=en#create-a-dataset) basierend auf dem von Ihnen erstellten oder aktualisierten Schema. Dieser Datensatz enthält die von Ihnen gesendeten Commerce-Daten.
* [Erstellen eines Datenspeichers](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) und wählen Sie das XDM-Schema aus, das die Commerce-spezifischen Feldergruppen enthält.
* [Verbindung zu Commerce Services herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en).
* [Verbindung zu Adobe Experience Platform herstellen](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/connect-data.html?lang=en).

### Verbindung zum Commerce-Ziel über Adobe Experience Platform für Zielgruppenfreigabe herstellen

Herstellen einer Verbindung zum Adobe Commerce-Ziel:

* Im [Adobe Experience Platform-Benutzeroberfläche](https://experience.adobe.com/platform/), navigieren Sie zu Ziele > Katalog .
* Wählen Sie Personalisierung aus.
* Wählen Sie das Adobe Commerce-Ziel aus, um es zu markieren, und wählen Sie dann Einrichten aus.
* Führen Sie die im Abschnitt [Tutorial zur Zielkonfiguration](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=en).

## Vordefinierte Daten

* Storefront(Browser/App)-Ereignisse
* Back-Office-Ereignisse
* Historische Bestelldaten

Eine vollständige Liste der unterstützten Ereignisse finden Sie unter [Commerce-Ereignisse](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/event-forwarding/events.html?lang=en)

## Architektur

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP-Architektur" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Verwandte Implementierungshandbücher

| Handbuch  | Link |
|:----|:----|
| Platform Connector | [Übersicht über den Adobe Commerce Experience Platform-Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/overview.html?lang=en) |
| Commerce-Ziel | [Adobe Commerce-Verbindung in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=en) |
| Edge-Personalisierung | [Aktivieren von Zielgruppen für Edge-Personalisierungsziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=en) | |
