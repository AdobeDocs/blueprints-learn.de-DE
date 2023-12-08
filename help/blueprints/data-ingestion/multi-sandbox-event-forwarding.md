---
title: Datenerfassung bei der Ereignisweiterleitung für mehrere Sandboxes
description: Erfahren Sie, wie Sie mit den Experience Platform Web- und Mobile-SDKs erfasste Daten so konfigurieren können, dass sie ein einzelnes Ereignis erfassen und an mehrere Experience Platform-Sandboxes weiterleiten.
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 3d6a2416cdb9956e59be4b2918ba19f88cd2150b
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 100%

---

# Datenerfassung bei der Ereignisweiterleitung für mehrere Sandboxes

Diese Blueprint zeigt, wie mit den Experience Platform Web- und Mobile-SDKs erfasste Daten so konfiguriert werden können, dass sie ein einzelnes Ereignis erfassen und an mehrere AEP-Sandboxes weiterleiten. Diese Blueprint ist ein spezifisches Anwendungsbeispiel für die Datenerfassung für mehrere Sandboxes, wobei dieses Ziel mithilfe der [!UICONTROL Ereignisweiterleitung] erreicht wird.

Zusätzlich zur Replikation des Ereignisses mithilfe der Funktionen für die  [!UICONTROL Ereignisweiterleitung] können Sie die ursprünglich erfassten Daten ergänzen, filtern oder bearbeiten, die Anforderungen für andere Sandboxes erfüllen.

Die [!UICONTROL Ereignisweiterleitung] verwendet eine separate Eigenschaft, die die für Ihre Datenanforderungen erforderlichen [!UICONTROL Datenelemente], [!UICONTROL Regeln] und [!UICONTROL Erweiterungen] enthält. Bei einem eingehenden Ereignis kann Ihre Eigenschaft für die [!UICONTROL Ereignisweiterleitung] die Daten erfassen und bei Bedarf vor der Weiterleitung verwalten.

Ihre Ziel-Sandbox erfordert einen konfigurierten HTTP-Streaming-Endpunkt, der von der Adobe [!UICONTROL Cloud Connector]-Erweiterung verwendet wird.

## Anwendungsfälle

* Globales Daten-Reporting : Bei der Verwendung mehrerer Sandboxes zum Isolieren von Betriebsumgebungen und der Notwendigkeit, die Datenerfassung in einer Sandbox zu konsolidieren, um das Sandbox-übergreifende Reporting zu vereinfachen. Mit der Weiterleitung eines Experience Edge-Ereignisses über die [!UICONTROL Ereignisweiterleitung] an eine Reporting-Sandbox kann jede Sandbox-Betriebsumgebung in Echtzeit erfasste Daten an eine Reporting-Sandbox senden.

* Verwalten Sie die Datenerfassung Sandbox-übergreifend basierend auf unterschiedlichen Datenregeln für die einzelnen Sandbox-Betriebsumgebungen.

## Programme

* [!DNL Experience Platform] Datenerfassung
* [!UICONTROL Ereignisweiterleitung]
* AEP-[!UICONTROL Erweiterung]
* [!UICONTROL Cloud Connector-Erweiterung]

## Allgemeine Überlegungen

Bei der [!UICONTROL Ereignisweiterleitung] als Ansatz zum Senden von Daten an mehrere Sandboxes müssen bestimmte Überlegungen in der Lösungsarchitektur berücksichtigt werden.

### Keine HIPAA-Daten

[!UICONTROL Die Ereignisweiterleitung gilt nicht als HIPAA-fähig und sollte nicht in HIPAA-Anwendungsfällen verwendet werden, in denen HIPAA-Daten erfasst werden. ] Die für die [!UICONTROL Ereignisweiterleitung] verwendete Infrastruktur gilt jedoch als HIPAA-fähig und kann von der Kundschaft in deren Ermessen genutzt werden. Während sich Ihre Tag-Eigenschaft für die [!UICONTROL Ereignisweiterleitung] im System für die [!UICONTROL Ereignisweiterleitung] befindet, wird die gesamte erfasste Daten-Payload zur Verarbeitung an das System für die [!UICONTROL Ereignisweiterleitung] gesendet. Dieser Prozess macht die [!UICONTROL Ereignisweiterleitung] für HIPAA-Anwendungsfälle schwierig. Wenn die gesamte Payload an das System für die [!UICONTROL Ereignisweiterleitung] gesendet wird, enthält dies auch alle HIPAA-Werte. Auch wenn die Regeln zur [!UICONTROL Ereignisweiterleitung] diese Daten vor dem Senden an ihr Ziel filtern, werden diese HIPAA-Daten dennoch an eine nicht HIPAA-fähige Infrastrukturen gesendet. Die Payload-Daten werden jedoch nie gespeichert und lediglich durchgeleitet.

### Verschiedene Datenströme und Streaming-Endpunkte

Wenn Daten durch Datenströme vom [!UICONTROL Platform Edge Network] fließen, besteht bei der Verwendung der [!UICONTROL Ereignisweiterleitung] an eine andere AEP-Sandbox eine-Anforderung darin, Nie denselben Datenstrom oder Streaming-Endpunkt zu verwenden wie der Datenstrom, der die ursprüngliche Sammlung erstellt. Dies kann sich nachteilig auf die AEP-Instanz auswirken und möglicherweise eine DoS-Situation auslösen.

### Geschätzte Traffic-Volumina

Traffic-Volumina sind in jedem Anwendungsfall für die Überprüfung erforderlich. Dies ist wichtig, da hohe Volumina zu einer Drosselung führen können, über die Kundschaft entsprechend benachrichtigt wird.

## Architektur

![[!UICONTROL Ereignisweiterleitung für mehrere Sandboxes]](assets/multi-sandbox-data-collection.png)

1. Zur Verwendung der [!UICONTROL Ereignisweiterleitung] ist das Erfassen und Senden von Ereignisdaten an das [!UICONTROL Platform Edge Network] erforderlich. Kunden können Adobe Tags für die Client-seitige Datenerfassung oder die [!UICONTROL Platform Edge Network Server-API] für die Server-zu-Server-Datenerfassung verwenden. Die [!UICONTROL Platform Edge Network-API] kann eine Server-zu-Server-Erfassungsfunktion bereitstellen. Dies erfordert jedoch ein anderes Programmiermodell zur Implementierung. Siehe [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de).

1. Die erfassten Payloads werden von der Tags-Implementierung an das [!UICONTROL Platform Edge Network] und an den Service für die [!UICONTROL Ereignisweiterleitung] gesendet und von eigenen [!UICONTROL Datenelementen], [!UICONTROL Regeln] und [!UICONTROL Aktionen] verarbeitet. Erfahren Sie mehr zu den Unterschieden zwischen [[!UICONTROL Tags und Ereignisweiterleitung]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de#differences-from-tags).

1. Eine Eigenschaft für die [!UICONTROL Ereignisweiterleitung] ist auch erforderlich, um erfasste Ereignisdaten vom [!UICONTROL Platform Edge Network] zu empfangen. Ob diese Ereignisdaten durch eine bereitgestellte Tags-Implementierung oder eine Server-zu-Server-Sammlung an das Platform Edge Network gesendet wurden. Autoren definieren die Datenelemente, Regeln und Aktionen, die zur Anreicherung der Ereignisdaten vor der Weiterleitung an die zweite Sandbox verwendet werden. Erwägen Sie die Verwendung des [!DNL JavaScript]-Datenelements „Benutzerspezifischer Code“, um Ihre Daten für die Sandbox-Aufnahme zu strukturieren. In Kombination mit den Datenvorbereitungsfunktionen von Platform haben Sie mehrere Möglichkeiten, Ihre Datenstruktur zu verwalten.

1. Derzeit ist die Verwendung der Adobe [!UICONTROL Cloud Connector-Erweiterung] in der Eigenschaft für die [!UICONTROL Ereignisweiterleitung] erforderlich. Sobald die Regeln die Ereignisdaten verarbeiten oder anreichern, wird der Cloud Connector in einem Abruf verwendet, der für eine POST-Sendung der Payload an die zweite Sandbox konfiguriert ist

1. Für die zweite Sandbox ist ein Streaming-Endpunkt für die Datenaufnahme erforderlich. Sie können auch die Datenvorbereitungsfunktionen in AEP berücksichtigen, um die Aufnahme und Zuordnung von Payloads für die [!UICONTROL Ereignisweiterleitung] an XDM zu unterstützen. Weitere Informationen finden Sie in der AEP-Dokumentation zum [Erstellen einer HTTP-API-Streaming-Verbindung über die Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=de)
