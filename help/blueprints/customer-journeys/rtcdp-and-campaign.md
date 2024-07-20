---
title: Real-Time CDP mit [!DNL Campaign] v7 und Campaign Standard-Integrationsmuster
description: Veranschaulicht, wie die Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe [!DNL Campaign] zur Bereitstellung personalisierter Konversationen genutzt werden können.
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 258aea64f6ff2f620b1adaa0c9ba4b02b47acce9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 42%

---

# [!DNL Real-Time Customer Data Platform] mit [!DNL Campaign] Integrationsmuster

Veranschaulicht, wie die Adobe [!DNL Experience Platform] und das Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe [!DNL Campaign] verwendet werden können, um personalisierte Konversationen bereitzustellen.

## Programme

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 oder [!DNL Campaign Standard]

## Architektur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referenzarchitektur für das Integrationsmuster für Batch-Messaging und Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Voraussetzungen

* Es wird empfohlen, Experience Platform und [!DNL Campaign] in derselben IMS-Organisation bereitzustellen und Adobe Admin Console für den Benutzerzugriff zu verwenden. Dies stellt auch sicher, dass Kunden den Lösungsschalter innerhalb der Marketing-UI verwenden können

## Leitlinien

In den folgenden Abschnitten werden die Limits für diese Integration beschrieben.

### Adobe [!DNL Campaign]

* Nur Adobe [!DNL Campaign] einzelne Organisationseinheiten wird unterstützt
* Adobe [!DNL Campaign] ist die &quot;Source of Truth&quot; für alle aktiven Profile, d. h. Profile müssen in Adobe [!DNL Campaign] vorhanden sein und neue Profile sollten nicht auf der Grundlage von Experience Platform-Segmenten erstellt werden.
* [!DNL Campaign] Export-Workflows, die maximal alle vier Stunden ausgeführt werden
* XDM-Schema und -Datensätze für Adobe [!DNL Campaign] broadLog, trackingLogs und nicht zustellbare Adressen sind nicht vorkonfiguriert und müssen entworfen und erstellt werden

### Segmentfreigabe in Real-time Customer Data Platform

* Siehe RTCDP [!DNL Campaign] Destination Connector - [RTCDP Campaign Connection](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=de)

* Siehe [Standardsicherungen für  [!DNL Real-Time Customer Profile Data] und die Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de) .

## Implementierungsschritte

In den folgenden Abschnitten werden die Implementierungsschritte für jede Anwendung beschrieben.

### Adobe Experience Platform

#### Schema/Datensätze

1. [Konfigurieren Sie das individuelle Profil, das Erlebnisereignis und Schemas mit mehreren Einheiten](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=de) in Experience Platform basierend auf den von der Kundin oder dem Kunden angegebenen Daten.
1. Erstellen Sie Adobe [!DNL Campaign] -Schemata für broadLog, trackingLog, nicht zustellbare Adressen und Profilvoreinstellungen (optional).
1. [Erstellen Sie Datensätze](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=de) in Experience Platform für die aufzunehmenden Daten.
1. [Fügen Sie dem Datensatz in Experience Platform Datennutzungskennzeichnungen hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=de), um ordnungsgemäße Governance zu gewährleisten.
1. [Erstellen Sie Richtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=de), um die Governance an den Zielen umzusetzen.

#### Profil/Identität

1. [Erstellen Sie sämtliche kundenspezifischen Namespaces](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Fügen Sie Identitäten zu Schemas hinzu](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=de).
1. [Aktivieren Sie die Schemas und Datensätze für Profile](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=de).
1. [Richten Sie Zusammenführungsrichtlinien](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=de) für unterschiedliche Ansichten des [!UICONTROL Echtzeit-Kundenprofils] ein (optional).
1. Erstellen Sie Segmente für die Verwendung von Adobe [!DNL Campaign].

#### Quellen/Ziele

1. [Experience Platform und [!DNL Campaign] Standardquellen und -ziele](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=de)
1. [Experience Platform und [!DNL Campaign] v7 Quellen und Ziele](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=de)
1. [Nehmen Sie Daten mit Streaming-APIs und Quell-Connectoren in Experience Platform auf.](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=de)
1. Konfigurieren Sie das [!DNL Azure] Blob Storage-Ziel für die Verwendung mit Adobe [!DNL Campaign].

#### Adobe [!DNL Campaign]

1. Konfigurieren Sie Schemas für das Profil, Suchdaten und relevante Personalisierungsdaten für die Bereitstellung.

>[!IMPORTANT]
>
>Es ist wichtig, an dieser Stelle zu verstehen, was das Datenmodell für Profil- und Ereignisdaten in der Experience Platform ist, damit Sie wissen, welche Daten in Adobe [!DNL Campaign] erforderlich sind.

#### Workflows für den Import

1. Laden und erfassen Sie vereinfachte Profildaten auf Adobe [!DNL Campaign] sFTP.
1. Laden und erfassen Sie Orchestrierungs- und Messaging-Personalisierungsdaten auf Adobe [!DNL Campaign] sFTP.
1. Nehmen Sie Experience Platform-Segmenten aus dem [!DNL Azure]-Blob über Workflows auf.

#### Workflows für den Export

1. Senden Sie alle vier Stunden Adobe [!DNL Campaign] Logs zurück an Experience Platform über Workflows (broadLog, trackingLog, nicht zustellbare Adressen).
1. Senden Sie Profileinstellungen über Consulting-Workflows alle vier Stunden an Experience Platform (optional).

### Mobilgeräte-Push-Konfiguration

* Zwei unterstützte Ansätze für die Integration mit Mobilgeräten für Push-Benachrichtigungen:
   * Experience Platform Mobile SDK
   * [!DNL Campaign] Mobile SDK
* Vorgehensweise für Experience Platform Mobile SDK:
   * Verwenden Sie Adobe-Tags und die [!DNL Campaign Classic] -Erweiterung, um Ihre Integration mit dem Experience Platform Mobile SDK einzurichten.
   * Erfahrung im Umgang mit Adobe Tags und Datenerfassung nötig
   * Erfahrung bei der Mobile-Entwicklung mit Push-Benachrichtigungen sowohl für Android als auch iOS erforderlich zur Implementierung des SDK, Integration mit FCM (Android) und APNS (iOS), um Push-Token zu erhalten, Konfiguration der Mobile App zum Erhalt von und Umgang mit Push-Benachrichtigungen
* [!DNL Campaign] Mobile SDK
   * Siehe die Dokumentation zum [Campaign Classic SDK](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/) .

>[!IMPORTANT]
>
>Wenn Sie das SDK [!DNL Campaign] bereitstellen und mit anderen Experience Cloud-Applikationen arbeiten, ist die Verwendung des Experience Platform Mobile SDK für die Datenerfassung erforderlich. Dadurch werden duplizierte Client-seitige Aufrufe auf dem Gerät erstellt.

## Verwandte Dokumentation

* [Adobe [!DNL Experience Platform] documentation](https://experienceleague.adobe.com/docs/experience-platform.html?lang=de)
* [[!DNL Campaign Classic] Dokumentation](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=de)
* [[!DNL Campaign Standard] Dokumentation](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=de)
* [[!DNL Experience Platform] Launch-Dokumentation](https://experienceleague.adobe.com/docs/launch.html?lang=de)
* [[!DNL Experience Platform] Mobile SDK-Dokumentation](https://experienceleague.adobe.com/docs/mobile.html?lang=de)
