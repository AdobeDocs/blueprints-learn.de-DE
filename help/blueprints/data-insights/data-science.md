---
title: 'Blueprint: Benutzerdefinierte Datenwissenschaft für Profilanreicherung'
description: Diese Blueprint zeigt, wie Data Science Workspace in Adobe Experience Platform Daten in Experience Platform nutzen kann, um Modelle zu trainieren, bereitzustellen und zu bewerten, um ML-Erkenntnisse aus Daten zu gewinnen.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 63%

---

# Blueprint: Benutzerdefinierte Datenwissenschaft für Profilanreicherung

Custom Data Science for Profil Anreicherung Blueprint veranschaulicht, wie Daten in Adobe Experience Platform in [!UICONTROL Data Science Workspace] verwendet werden können, um Modelle zu schulen, bereitzustellen und zu bewerten, um Einblicke in das maschinelle Lernen zu erhalten. Diese Modelle können direkt in einen Datensatz ausgegeben werden, der für [!UICONTROL Echtzeit-Kundendaten] aktiviert ist, um die Profil der Kunden weiter zu bereichern. Diese Einblicke können dann für die Personalisierung verwendet werden. Beispiele für Einblicke in das maschinelle Lernen sind die Bewertung des Lebenszeitwerts, die Affinität von Produkten und Kategorien, die Neigung zu Konversionen oder die Neigung zum Absturz.

## Anwendungsfälle

* Extrahieren von Erkenntnissen und Aufdecken von Mustern mit Kundendaten in Experience Platform. Trainieren und Bewerten von Modellen mit diesen Daten.
* Erweitern Sie das [!UICONTROL Echtzeit-Profil des Kunden] mit modellbasierten Einblicken und Attributen für eine detailliertere Personalisierung und optimierte Journey.
* Trainieren und Bewerten von Modellen, um Kundenerkenntnisse wie Kunden-Lebenszeitwert, Konversions- oder Abwanderungsneigung, Produkt- und Content-Affinität und Interaktionswerte zu ermitteln.

## Architektur

<img src="assets/data_science.svg" alt="Referenzarchitektur für Blueprint „Benutzerdefinierte Datenwissenschaft für Profilanreicherung“" style="border:1px solid #4a4a4a" />

## Implementierungsschritte

1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) Schemata für Daten, die aufgenommen werden sollen.
1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) Datensätze, damit Daten erfasst werden.
1. [Aufnehmen der Daten in Experience Platform.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. Erstellen eines DSW-Notebooks.
1. Auswählen einer Sprache. Python und PySpark werden unterstützt.
1. Erstellen des Modells im Notebook.
1. Trainieren des Modells.
1. Bewerten des Modells, um Vorhersagen mit den Zieldaten zu generieren.
1. Aktivieren Sie den Modellergebnisdatensatz für Profil, wenn Sie die Modellergebnisse an das [!UICONTROL Echtzeit-Profil des Kunden] verschieben.

## Verwandte Dokumentation

* [Produktbeschreibung zu Adobe Experience Platform Intelligence](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Dokumentation zu Data Science Workspace](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=de)
* [Tutorials zu Data Science Workspace](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html?lang=de)

## Verwandte Blog-Posts

* [[!DNL Simplifying the Data Science Lifecycle with Adobe Platform Experience]](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL Gaining a Deeper Understanding of Churn Using Data Science Workspace]](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [[!DNL Understanding Data Science In Adobe Experience Platform]](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [[!DNL Reimagining Jupyter Notebooks for Enterprise Scale]](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [[!DNL Accelerate Intelligent Insights with Adobe Experience Platform Data Science Workspace]](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [[!DNL A Preview of Time Series Forecasting with Adobe Experience Platform]](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
