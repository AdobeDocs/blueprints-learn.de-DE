---
title: 'Blueprint: Benutzerdefinierte Datenwissenschaft zur Profilanreicherung'
description: Erfahren Sie, wie datenwissenschaftsbasierte Einblicke in aufgenommen werden können [!DNL Experience Platform]  um das Echtzeit-Kundenprofil zu bereichern.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 69%

---

# Benutzerdefinierte Datenwissenschaft für den Blueprint zur Profilanreicherung

Der Blueprint Benutzerdefinierte Datenwissenschaft für die Profilanreicherung veranschaulicht, wie Daten zum Trainieren, Bereitstellen und Bewerten von Modellen verwendet werden können, um Einblicke in maschinelles Lernen in [!DNL Experience Platform] und die [!DNL Real-Time Customer Data Platform] aus Datenwissenschaft und Tools für maschinelles Lernen zu bieten.

Modellierte Einblicke können in [!DNL Experience Platform] aufgenommen werden, um das Echtzeit-Kundenprofil zu bereichern. Beispiele für ML-Erkenntnisse sind Lebenszeitwertbewertung, Produkt- und Kategorieaffinität, Konversions- oder Abwanderungsneigung.

## Anwendungsfälle

* Extrahieren Sie Erkenntnisse und entdecken Sie Muster in Kundendaten und trainieren und bewerten Sie Modelle anhand dieser Daten.
* Anreichern des [!UICONTROL Echtzeit-Kundenprofils] mit modellgestützten Erkenntnissen und Attributen für detailliertere Personalisierung und Journey-Optimierung.
* Trainieren und Bewerten von Modellen, um Kundenerkenntnisse wie Kunden-Lebenszeitwert, Konversions- oder Abwanderungsneigung, Produkt- und Content-Affinität und Interaktionswerte zu ermitteln.

## Architektur

<img src="assets/data_science.svg" alt="Referenzarchitektur für die Blueprint „Benutzerdefinierte Datenwissenschaft zur Profilanreicherung“" style="width:90%; border:1px solid #4a4a4a" />

## Leitlinien

* Detaillierte Informationen zu Leitplanken und End-to-End-Latenzen bei der Aufnahme datenwissenschaftlicher Ergebnisse in [!DNL Experience Platform] und das Echtzeit-Kundenprofil finden Sie in den Leitplanken für die Datenaufnahme und im Latenzdiagramm, auf das im Dokument [Bereitstellungsleitplanken“ verwiesen ](../experience-platform/deployment/guardrails.md).

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?lang=de&recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Daten ](https://experienceleague.adobe.com/?lang=de&recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in [!DNL Experience Platform] aufnehmen.

Damit Modellergebnisse in das Echtzeit-Kundenprofil aufgenommen werden, müssen Sie vor der Aufnahme von Daten folgende Schritte ausführen:

1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).

## Überlegungen bei der Implementierung

* In den meisten Fällen muss das Modellergebnis als Profilattribute und nicht als Erlebnisereignisse erfasst werden. Bei den Modellergebnissen kann es sich um einfache Attributzeichenfolgen handeln. Wenn mehrere Modellergebnisse aufgenommen werden sollen, wird empfohlen, ein Feld vom Typ Array oder Zuordnung zu verwenden.
* Der tägliche Datensatz mit dem Profil-Schnappschuss, der einen täglichen Export der einheitlichen Profilattributdaten darstellt, kann genutzt werden, um Modelle für Profilattributdaten zu trainieren. Die Dokumentation zu Profildatensätzen ist [hier](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=de#profile-attribute-datasets) verfügbar.
* Zum Extrahieren von Daten aus [!DNL Experience Platform] können die folgenden Methoden verwendet werden
   * Data Access SDK
      * Daten liegen als Rohdaten vor
      * Profil-Ereigniserlebnis-Daten bleiben im nicht einheitlichen Rohzustand.
   * RTCDP-Ziele
      * Es können Profilattribute und Segmentmitgliedschaften ausgegeben werden.

## Verwandte Dokumentation

* [Adobe [!DNL Experience Platform] Intelligence-Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Abfrage-Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)

## Verwandte Blog-Posts

* [Content- und Commerce-KI: Personalisierung der Interaktionen mit Kunden anhand von Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Einführungsvorschau zur explorativen Datenanalyse auf Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Nutzung verschiedener Adobe Experience-Produkte mit maschinellem Lernen für bessere Kundenerlebnisse](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)