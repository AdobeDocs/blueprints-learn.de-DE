---
title: Datenerfassung bei der Ereignisweiterleitung für mehrere Sandboxes
description: Erfahren Sie, wie Sie mit den Experience Platform Web- und Mobile-SDKs erfasste Daten so konfigurieren können, dass sie ein einzelnes Ereignis erfassen und an mehrere Experience Platform-Sandboxes weiterleiten.
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 55%

---

# Datenerfassung bei der Ereignisweiterleitung für mehrere Sandboxes

Dieser Blueprint zeigt, wie mit [!DNL Experience Platform] Web- und Mobile-SDKs erfasste Daten so konfiguriert werden können, dass sie ein einzelnes Ereignis erfassen und an mehrere AEP-Sandboxes weiterleiten. Diese Blueprint ist ein spezifisches Anwendungsbeispiel für die Datenerfassung für mehrere Sandboxes, wobei dieses Ziel mithilfe der [!UICONTROL Ereignisweiterleitung] erreicht wird.

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

[!UICONTROL Ereignisweiterleitung] gilt nicht als HIPAA-fähig und sollte in HIPAA-Anwendungsfällen, in denen HIPAA-Daten erfasst werden, nicht verwendet werden.

Die für die [!UICONTROL Ereignisweiterleitung“ verwendete Infrastruktur ] jedoch als HIPAA-fähig eingestuft und liegt allein im Ermessen des Kunden. Während sich Ihre Tag-Eigenschaft für die [!UICONTROL Ereignisweiterleitung] im System für die [!UICONTROL Ereignisweiterleitung] befindet, wird die gesamte erfasste Daten-Payload zur Verarbeitung an das System für die [!UICONTROL Ereignisweiterleitung] gesendet. Dieser Prozess macht [!UICONTROL Ereignisweiterleitung] für HIPAA-Anwendungsfälle möglich. Wenn die gesamte Payload an das System [!UICONTROL Ereignisweiterleitung] gesendet wird, enthält dieser Prozess alle HIPAA-Werte. Obwohl die Regeln [!UICONTROL Ereignisweiterleitung] diese Daten filtern, bevor sie an ihr Ziel gesendet werden, werden diese HIPAA-Daten dennoch an eine nicht HIPAA-fähige Infrastruktur gesendet. Die Payload-Daten werden jedoch nie gespeichert und dienen lediglich als Pass-Through.

### Verschiedene Datenströme und Streaming-Endpunkte

Da Daten durch Datenströme aus dem [!DNL Platform Edge Network] fließen, müssen Sie bei Verwendung der [!UICONTROL Ereignisweiterleitung] an eine andere AEP-Sandbox grundsätzlich nicht denselben Datenstrom oder Streaming-Endpunkt wie der Datenstrom verwenden, aus dem die ursprüngliche Sammlung stammt. Dies kann sich nachteilig auf die AEP-Instanz auswirken und möglicherweise eine DoS-Situation auslösen.

### Geschätzte Traffic-Volumina

Traffic-Volumina sind in jedem Anwendungsfall für die Überprüfung erforderlich. Dies ist wichtig, da hohe Volumina zu einer Drosselung führen können, über die Kundschaft entsprechend benachrichtigt wird.

## Architektur

![[!UICONTROL Ereignisweiterleitung für mehrere Sandboxes]](assets/multi-sandbox-data-collection.png)

1. Das Erfassen und Senden von Ereignisdaten an den [!DNL Platform Edge Network] ist erforderlich, um die [!UICONTROL Ereignisweiterleitung“ ] verwenden. Sie können Adobe-Tags für die Client-seitige oder die [!DNL Platform Edge Network Server API] für die Server-zu-Server-Datenerfassung verwenden.

   Die [!DNL Platform Edge Network API] kann eine Server-zu-Server-Sammelfunktion bereitstellen. Dies erfordert jedoch die Implementierung eines anderen Programmiermodells. Siehe [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de).

1. Erfasste Payloads werden von der Tag-Implementierung an den [!DNL Platform Edge Network] an den Service [!UICONTROL Ereignisweiterleitung] gesendet und von seinen eigenen [!UICONTROL Datenelementen], [!UICONTROL Regeln] und [!UICONTROL Aktionen] verarbeitet. Weitere Informationen zu den Unterschieden finden Sie unter [Tags und [!UICONTROL Ereignisweiterleitung]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de#differences-from-tags).

1. Eine [!UICONTROL Ereignisweiterleitung]-Eigenschaft ist auch erforderlich, um erfasste Ereignisdaten von der [!DNL Platform Edge Network] zu empfangen, unabhängig davon, ob diese Ereignisdaten von einer bereitgestellten Tags-Implementierung oder einer Server-zu-Server-Sammlung an die [!DNL Platform Edge Network] gesendet wurden.

   Autoren definieren die Datenelemente, Regeln und Aktionen, die zur Anreicherung der Ereignisdaten vor der Weiterleitung an die zweite Sandbox verwendet werden. Erwägen Sie die Verwendung des [!DNL JavaScript]-Datenelements „Benutzerspezifischer Code“, um Ihre Daten für die Sandbox-Aufnahme zu strukturieren. In Kombination mit den Datenvorbereitungsfunktionen von Platform haben Sie mehrere Möglichkeiten, Ihre Datenstruktur zu verwalten.

1. Derzeit ist die Verwendung der Adobe [!UICONTROL Cloud Connector-Erweiterung] in der Eigenschaft für die [!UICONTROL Ereignisweiterleitung] erforderlich. Nachdem die Regeln die Ereignisdaten verarbeitet oder angereichert haben, wird [!UICONTROL Cloud-Connector] in einem für eine POST konfigurierten Abrufaufruf verwendet, wobei die Payload an die zweite Sandbox gesendet wird.

1. Für die zweite Sandbox ist ein Streaming-Endpunkt für die Datenaufnahme erforderlich. Sie können auch Funktionen [!UICONTROL Datenvorbereitung) in AEP in Betracht ziehen] um die Aufnahme und Zuordnung von Payloads [!UICONTROL Ereignisweiterleitung] zu XDM zu erleichtern. Weitere Informationen finden Sie in der AEP-Dokumentation zum [Erstellen einer HTTP-API-Streaming-Verbindung über die Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=de)
