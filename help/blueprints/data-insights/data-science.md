---
title: Custom Data Science for Profil Anreicherung Blueprint
description: Dieser Entwurf zeigt, wie der Data Science Workspace von Adobe Experience Platform Daten innerhalb der Experience Platform verwenden kann, um Modelle auszubilden, bereitzustellen und zu bewerten, um Einblicke in das maschinelle Lernen aus den Daten zu erhalten.
solution: Experience Platform, Data Collection
kt: 7203
exl-id: f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
translation-type: tm+mt
source-git-commit: 3f27f27159d9fb07124f289164dd85941ec58a25
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Custom Data Science for Profil Anreicherung Blueprint

In diesem Blueprint wird gezeigt, wie die Daten in Adobe Experience Platform von Data Science Workspace verwendet werden, um Modelle für maschinelles Lernen zu schulen, bereitzustellen und zu bewerten. Diese Modelle können direkt in einen Datensatz ausgegeben werden, der für Echtzeit-Kundendaten aktiviert ist. Beispiele für Einblicke in das maschinelle Lernen sind Lebenszeitwert, Produkt- und Kategorie-Affinität, Konversionneigung oder Absturzneigung.

## Anwendungsfälle

* Extrahieren Sie Einblicke und entdecken Sie Muster aus Kundendaten in der Experience Platform. Zug- und Score-Modelle aus diesen Daten.
* Erweitern Sie das Echtzeit-Kundenerlebnis mit modellbasierten Einblicken und Attributen für eine granulärere Personalisierung und optimierte Journey-Optimierung.
* Train- und Score-Modelle zur Ermittlung von Kundeneinblicken wie Lebenszeitwert, Konversions- oder Abstoßungsneigung, Produkt- und Content-Affinitäten und Interaktionswerte.

## Szenarien

| Szenario | Szenariobeschreibung | Experience Cloud-Anwendungen |
|---|---|---|
| Forschungsdatenwissenschaften | <ul><li>Discover-Signale, Vollständigkeit, Richtigkeit der Daten</li><li>Entdecken Sie neue Erkenntnisse mithilfe der Werkzeuge der Datenwissenschaft</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |
| Profil-Anreicherung mit AI/ML<br> - Batch | <ul><li>Modelle für Discover, Autor, Schulung, Bereitstellung, Bewertung und Operationalisierung</li><li>Push-Modellvorhersage an Profil oder an den Datensee zur Batch-basierten Aktivierung.</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |

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
1. Aktivieren Sie den Modellergebnisdatensatz zum Profil, wenn Sie die Modellergebnisse an das Echtzeit-Profil des Kunden senden.

## Verwandte Dokumentation

* [Produktbeschreibung für Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Dokumentation zum Data Science Workspace](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [Übungen zum Arbeitsbereich für Datenwissenschaften](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Verwandte Blog-Beiträge

* [Vereinfachung des Datenlebenszyklus mit Adobe Platform Experience](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [Content- und Commerce-API: Personalisieren Ihrer Interaktionen mit Kunden mithilfe von Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Gewinnen eines tieferen Verständnisses von Churn mithilfe von Data Science Workspace](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [Die Datenwissenschaft in Adobe Experience Platform](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [Einführung zur Analyse von Sondierungsdaten über Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Effiziente Nutzung von maschinellem Lernen durch Adobe Experience Products](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Modellieren von XDM-Daten für Datenwissenschaften im Maßstab unter Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI: Automatisierte Audience-Clustering als Dienst in Adobe Experience Platform](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [Neugestaltung von Jupyter-Notebooks im Enterprise-Stil](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [Beschleunigung intelligenter Einblicke mit dem Adobe Experience Platform Data Science Workspace](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [Eine Vorschau von Zeitreihen-Prognosen mit Adobe Experience Platform](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [Effiziente Nutzung von maschinellem Lernen durch Adobe Experience Products](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
