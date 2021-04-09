---
title: Custom Data Science for Profil Anreicherung Blueprint
description: Dieser Entwurf zeigt, wie der Data Science Workspace von Adobe Experience Platform Daten innerhalb der Experience Platform verwenden kann, um Modelle auszubilden, bereitzustellen und zu bewerten, um Einblicke in das maschinelle Lernen aus den Daten zu erhalten.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: 2343151a1ed5374c299fb9317f6282c232d5d23b
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Custom Data Science for Profil Anreicherung Blueprint

Custom Data Science for Profil Anreicherung Blueprint veranschaulicht, wie Daten in Adobe Experience Platform in [!UICONTROL Data Science Workspace] verwendet werden können, um Modelle zu schulen, bereitzustellen und zu bewerten, um Einblicke in das maschinelle Lernen zu erhalten. Diese Modelle können direkt in einen Datensatz ausgegeben werden, der für [!UICONTROL Echtzeit-Kundendaten] aktiviert ist, um die Profil der Kunden weiter zu bereichern. Diese Einblicke können dann für die Personalisierung verwendet werden. Beispiele für Einblicke in das maschinelle Lernen sind die Bewertung des Lebenszeitwerts, die Affinität von Produkten und Kategorien, die Neigung zu Konversionen oder die Neigung zum Absturz.

## Anwendungsfälle

* Extrahieren Sie Einblicke und entdecken Sie Muster aus Kundendaten in der Experience Platform. Zug- und Score-Modelle aus diesen Daten.
* Erweitern Sie das [!UICONTROL Echtzeit-Profil des Kunden] mit modellbasierten Einblicken und Attributen für eine detailliertere Personalisierung und optimierte Journey.
* Train- und Score-Modelle zur Ermittlung von Kundeneinblicken wie Lebenszeitwert, Konversions- oder Abstoßungsneigung, Produkt- und Content-Affinitäten und Interaktionswerte.

## Architektur

<img src="assets/datascience.svg" alt="Referenzarchitektur für das Konzept der benutzerdefinierten Datenwissenschaft für die Anreicherung von Profilen" style="border:1px solid #4a4a4a" />

## Implementierungsschritte

1. Erstellen Sie Schema und Datensätze.
1. Daten in die Experience Platform aufnehmen.
1. Erstellen Sie ein DSW-Notebook.
1. Wählen Sie eine Sprache. Python und PySpark werden unterstützt.
1. Autorenmodell in Notebook.
1. Zug das Modell.
1. Bewerten Sie das Modell, um Prognosen mit den Daten zur Zielgruppe zu erstellen.
1. Aktivieren Sie den Modellergebnisdatensatz für Profil, wenn Sie die Modellergebnisse an das [!UICONTROL Echtzeit-Profil des Kunden] verschieben.

## Verwandte Dokumentation

* [Produktbeschreibung für Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Data Science ] Workspace-Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [[!UICONTROL Data Science ] Workspaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Verwandte Blog-Beiträge

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
