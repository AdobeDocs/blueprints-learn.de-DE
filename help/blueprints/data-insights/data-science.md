---
title: 'Blueprint: Benutzerdefinierte Datenwissenschaft zur Profilanreicherung'
description: Diese Blueprint zeigt, wie datenwissenschaftliche Erkenntnisse in Experience Platform integriert werden können, um das Echtzeit-Kundenprofil anzureichern.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 802507291f54dc3f253d469e7a64d78e34b75c6a
workflow-type: ht
source-wordcount: '500'
ht-degree: 100%

---

# Blueprint: Benutzerdefinierte Datenwissenschaft zur Profilanreicherung

Die Blueprint „Benutzerdefinierte Datenwissenschaft zur Profilanreicherung“ veranschaulicht, wie Daten zum Trainieren, Bereitstellen und Bewerten von Modellen verwendet werden können, um mithilfe von Datenwissenschafts- und Machine-Learning-Tools Erkenntnisse zu Experience Platform und Real-time Customer Data Platform zu erhalten. Modellierte Erkenntnisse können in Experience Platform integriert werden, um das Echtzeit-Kundenprofil anzureichern. Beispiele für ML-Erkenntnisse sind Lebenszeitwertbewertung, Produkt- und Kategorieaffinität, Konversions- oder Abwanderungsneigung.

## Anwendungsfälle

* Extrahieren Sie Erkenntnisse und entdecken Sie Muster in Kundendaten und trainieren und bewerten Sie Modelle anhand dieser Daten.
* Anreichern des [!UICONTROL Echtzeit-Kundenprofils] mit modellgestützten Erkenntnissen und Attributen für detailliertere Personalisierung und Journey-Optimierung.
* Trainieren und Bewerten von Modellen, um Kundenerkenntnisse wie Kunden-Lebenszeitwert, Konversions- oder Abwanderungsneigung, Produkt- und Content-Affinität und Interaktionswerte zu ermitteln.

## Architektur

<img src="assets/data_science.svg" alt="Referenzarchitektur für die Blueprint „Benutzerdefinierte Datenwissenschaft zur Profilanreicherung“" style="width:90%; border:1px solid #4a4a4a" />

## Leitlinien

* Detaillierte Leitlinien und End-to-End-Latenzen bei der Aufnahme von datenwissenschaftlichen Ergebnissen in Experience Platform und in das Echtzeit-Kundenprofil finden Sie in den Leitlinien zur Datenaufnahme und im Latenzdiagramm im [Dokument zu den Implementierungsleitlinien](../experience-platform/deployment/guardrails.md).

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.

Damit Modellergebnisse in das Echtzeit-Kundenprofil aufgenommen werden, müssen Sie vor der Aufnahme von Daten folgende Schritte ausführen:

1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).

## Überlegungen bei der Implementierung

* In den meisten Fällen muss das Modellergebnis als Profilattribute und nicht als Erlebnisereignisse erfasst werden. Bei den Modellergebnissen kann es sich um einfache Attributzeichenfolgen handeln. Wenn mehrere Modellergebnisse aufgenommen werden sollen, wird empfohlen, ein Feld vom Typ Array oder Zuordnung zu verwenden.
* Der tägliche Datensatz mit dem Profil-Schnappschuss, der einen täglichen Export der einheitlichen Profilattributdaten darstellt, kann genutzt werden, um Modelle für Profilattributdaten zu trainieren. Die Dokumentation zu Profildatensätzen ist [hier](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=de#profile-attribute-datasets) verfügbar.
* Für das Extrahieren von Daten aus Experience Platform können die folgenden Methoden verwendet werden:
   * Data Access SDK
      * Daten liegen als Rohdaten vor
      * Profil-Ereigniserlebnis-Daten bleiben im nicht einheitlichen Rohzustand.
   * RTCDP-Ziele
      * Es können Profilattribute und Segmentmitgliedschaften ausgegeben werden.

## Verwandte Dokumentation

* [Produktbeschreibung zu Adobe Experience Platform Intelligence](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Abfrage-Service von Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de)

## Verwandte Blog-Posts

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)