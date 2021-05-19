---
title: 'Blueprint: Customer Activity Hub'
description: Suchvorgänge im [!UICONTROL Echtzeit-Kundenprofil] bieten Kontext für mitarbeitergestützten Support und Vertrieb.
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: ht
source-git-commit: d6eaf978a8f587b881480c14f192cb9e29e3c7e2
workflow-type: ht
source-wordcount: '384'
ht-degree: 100%

---

# Blueprint: Customer Activity Hub

Die Blueprint „Customer Activity Hub“ zeigt, wie externe Programme auf das [!UICONTROL Echtzeit-Kundenprofil] von Adobe Experience Platform zugreifen können.

Externe Programme können über API-GET-Anfragen auf Profile zugreifen. Attribute, Ereignisse, Segmentzugehörigkeiten und modellgestützte Funktionen, die im Profil gespeichert sind, können dann in diesen externen Drittanbieterprogrammen verwendet werden.

Mit dieser Funktion können Sie auf umfangreichen Kontext zugreifen, wenn ein Kunde im Callcenter anruft. Der Support-Mitarbeiter hat beispielsweise Einblick in den Lebenszeitwert des Kunden, seine Abwanderungsneigung und die ihm bekannten Marketing-Kampagnen. Vertriebsmitarbeiter können ebenfalls von mehr Kontext und Erkenntnissen über Kunden profitieren.

>[!NOTE]
>
>Die derzeit von der API für die Profilsuche unterstützte Latenz beträgt etwa 500 Millisekunden. Somit ist diese Herangehensweise für die Integration des Profils mit Echtzeit-Entscheidungs-Engines wie die Same-Page-Web- oder Mobile-Personalisierung nicht geeignet.

## Anwendungsfälle

* Besserer Verbraucherkontext für mitarbeitergestützte Interaktionen wie Support- und Vertriebserlebnisse. Dank der Profilsuche in Experience Platform erhalten Mitarbeiter Kontext zum Verbraucher wie kürzlich durchgeführte Käufe, Kampagneninteraktionen, Neigungen, Zielgruppenzugehörigkeiten und andere Attribute sowie Erkenntnisse, die im Echtzeit-Kundenprofil gespeichert sind.

## Architektur

<img src="assets/customer_activity_hub.svg" alt="Referenzarchitektur für Blueprint „Customer Activity Hub“" style="border:1px solid #4a4a4a" />


## Leitlinien

* [Leitlinien für [!UICONTROL Echtzeit-Kundenprofildaten]](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

## Implementierungsschritte

1. [Erstellen Sie Schemas](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=de) für die zu erfassenden Daten.
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) für die zu erfassenden Daten.
1. [Konfigurieren Sie die korrekten Identitäten und Identitäts-Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de) im Schema, um sicherzustellen, dass aufgenommene Daten zu einem einheitlichen Profil zusammengefügt werden können.
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Aufnehmen der Daten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de) in Experience Platform.
1. [Richten Sie Zusammenführungsrichtlinien ein](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de).
1. Verwenden Sie die [Entitäten-API, um entweder in der Datensatzentität oder der Erlebnisereignisentität nach einem Profilattribut zu suchen](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=de).

## Verwandte Dokumentation

* [Produktbeschreibung zu Adobe Experience Platform Activation](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-platform0.html)
* Dokumentation zum [[!UICONTROL Echtzeit-Kundenprofil]](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=de)
* [Leitlinien zum Profil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
* [API für die Profilsuche](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
