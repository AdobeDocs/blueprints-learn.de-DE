---
title: 'Blueprint: Datenerfassung bei Ereignisweiterleitung für mehrere Sandboxes'
description: Streamen erfasster Daten von  [!DNL Experience Platform] AEP)-SDKs an mehrere Sandboxes mithilfe der Ereignisweiterleitung
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 60%

---

# Datenerfassungs-Blueprint für Multi-Sandbox-Ereignisweiterleitung

Datenerfassungs-Blueprint für Multi-Sandbox-Ereignisweiterleitung zeigt, wie mit Adobe [!DNL Experience Platform] Web- und Mobile-SDKs erfasste Daten so konfiguriert werden können, dass sie ein einzelnes Ereignis erfassen und an mehrere [!DNL Experience Platform]-Sandboxes (AEP) weiterleiten. Diese Blueprint ist ein spezielles Anwendungsbeispiel, das die Ereignisweiterleitungsfunktion von Adobe Tags verwendet.

Zusätzlich zur Replikation des Ereignisses können Sie mithilfe der Ereignisweiterleitungsfunktionen die ursprünglich erfassten Daten ergänzen, filtern oder bearbeiten, die Anforderungen für andere Sandboxes erfüllen. Beispielsweise muss Sandbox A alle Ereignisdatenelemente empfangen und Sandbox B soll nur Nicht-PII-Daten empfangen.

Die Ereignisweiterleitung verwendet eine separate Tag-Eigenschaft, die die für Ihre Datenanforderungen erforderlichen Datenelemente, Regeln und Erweiterungen enthält. Bei einem eingehenden Ereignis kann Ihre Ereignisweiterleitungs-Eigenschaft die Daten erfassen und bei Bedarf vor der Weiterleitung verwalten.

Ihre Ziel-Sandbox benötigt einen konfigurierten HTTP-Streaming-Endpunkt, der von der HTTPS-Erweiterung für die Ereignisweiterleitung verwendet wird.

## Anwendungsfälle

* Globales Daten-Reporting: Bei der Verwendung mehrerer Sandboxes zum Isolieren von Betriebsumgebungen und der Notwendigkeit, die Datenerfassung in einer Sandbox zu konsolidieren, um das Sandbox-übergreifende Reporting zu vereinfachen. Mit der Ereignisweiterleitung an eine Reporting-Sandbox kann jede Sandbox-Betriebsumgebung in Echtzeit erfasste Daten an eine Reporting-Sandbox senden
* Verwalten Sie die Datenerfassung Sandbox-übergreifend basierend auf unterschiedlichen Datenregeln für die einzelnen Sandbox-Betriebsumgebungen. Betriebsumgebungen, bei denen sensible Daten gefiltert werden müssen, z. B. im Gesundheitswesen und Finanzsektor

## Programme

* Adobe [!DNL Experience Platform] Datenerfassung

## Architektur

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Referenzarchitektur für Ereignisweiterleitung mit mehreren Sandboxes" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

1. Tag-Autoren definieren sowohl eine Tag-Eigenschaft als auch eine Ereignisweiterleitungs-Eigenschaft. Hier definieren Autoren die Datenelemente, Regeln und Aktionen, die die Datenerfassung verwalten. Beachten Sie, dass Tag-Eigenschafts-Code auf dem Client ausgeführt und von einem CDN-Host verteilt wird. Der [!UICONTROL Ereignisweiterleitungs-Eigenschaft]-Code wird auf dem Adobe-[!DNL Edge Server] ausgeführt.

1. Auf dem Client erfasste Daten werden an den [!DNL Edge Network] gesendet. Kunden haben außerdem die Möglichkeit, Daten als Methode der Server-seitigen Erfassung zunächst an ihren eigenen Server zu senden. Das Web SDK kann eine Server-zu-Server-Erfassungsfunktion bereitstellen. Dies erfordert jedoch ein anderes Programmiermodell zur Implementierung. Weitere Informationen finden Sie in der Dokumentation **[!DNL Edge Network]Server-API - Übersicht** unten

1. Platform [!DNL Edge Network] empfängt Datenerfassungs-Payloads und orchestriert den Datenfluss zu den erforderlichen Systemen wie Target und Analytics.

1. Datenelemente der Ereignisweiterleitungs-Eigenschaft werden verwendet, um auf Ereignisdaten zuzugreifen, die in die Payload eingehen. Regeln können auch verwendet werden, um die Ereignisdaten vor der Weiterleitung nach Bedarf anzupassen. Beispielsweise können die Daten in das für die Streaming-Datenaufnahme erforderliche XDM formatiert werden

1. Die Ereignisweiterleitung stellt die HTTPS-Erweiterung zur Verfügung, mit der Ihre Ereignisdaten an einen HTTPS-Endpunkt weitergeleitet werden können.

1. Sandbox 2 wird mit einem Streaming-Endpunkt konfiguriert, der das weitergeleitete Ereignis empfängt.

## Verwandte Dokumentation

* [Dokumentation zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de)
* [Videos zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=de)
* [Lektion zur Ereignisweiterleitung](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html?lang=de) des Web SDK-Tutorials
* [[!DNL Experience Platform] Übersicht über Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=de)
* [[!DNL Edge Network] Server-API - Übersicht](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)

## Verwandte Blog-Posts

* [Verbesserung der Leistung von Websites mit Adobe [!DNL Experience Platform] Web SDK und [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Lösen von Implementierungsproblemen mit Adobe [!DNL Experience Platform] Web SDK und [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe [!DNL Experience Platform] Web SDK für die Zielgruppenverwaltung](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] Web SDK - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe [!DNL Experience Platform] Web SDK-Migrationsszenarios für Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Vereinheitlichen Sie Ihre Adobe [!DNL Experience Platform] Services mit Adobe [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Beschleunigen der Entwicklung von Mobile Apps mit Adobe [!DNL Experience Platform] Mobile SDK und Launch](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Vereinfachung von Kunden-Workflows mit Adobe Experience Platform Web SDK](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
