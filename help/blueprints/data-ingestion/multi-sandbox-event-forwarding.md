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

Dieser Blueprint zeigt, wie Daten mit [!DNL Experience Platform] Web- und Mobile-SDKs können so konfiguriert werden, dass sie ein einzelnes Ereignis erfassen und an mehrere AEP-Sandboxes weiterleiten. Diese Blueprint ist ein spezifisches Anwendungsbeispiel für die Datenerfassung für mehrere Sandboxes, wobei dieses Ziel mithilfe der [!UICONTROL Ereignisweiterleitung] erreicht wird.

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

[!UICONTROL Ereignisweiterleitung] wird nicht als HIPAA-bereit betrachtet und sollte nicht in HIPAA-Anwendungsfällen verwendet werden, in denen HIPAA-Daten erfasst werden.

Die für [!UICONTROL Ereignisweiterleitung] wird als HIPAA-bereit betrachtet und liegt ausschließlich im Ermessen des Kunden. Während sich Ihre Tag-Eigenschaft für die [!UICONTROL Ereignisweiterleitung] im System für die [!UICONTROL Ereignisweiterleitung] befindet, wird die gesamte erfasste Daten-Payload zur Verarbeitung an das System für die [!UICONTROL Ereignisweiterleitung] gesendet. Dieser Prozess [!UICONTROL Ereignisweiterleitung] für HIPAA-Anwendungsfälle. Mit der gesamten Payload, die an die [!UICONTROL Ereignisweiterleitung] -System, würde dieser Prozess alle HIPAA-Werte einschließen. Auch wenn die [!UICONTROL Ereignisweiterleitung] -Regeln filtern diese Daten, bevor sie an ihr Ziel gesendet werden, und stellen fest, dass HIPAA-Daten weiterhin an eine nicht HIPAA-bereite Infrastruktur gesendet werden. Die Payload-Daten werden jedoch nie gespeichert und sind lediglich ein Pass-Through.

### Verschiedene Datenströme und Streaming-Endpunkte

Als Daten fließen durch Datenspeicher von der [!DNL Platform Edge Network]bei Verwendung von [!UICONTROL Ereignisweiterleitung] in eine andere AEP-Sandbox zu übertragen, ist es erforderlich, niemals denselben Datastream oder Streaming-Endpunkt zu verwenden wie den Datastream, der die ursprüngliche Sammlung erstellt. Dies kann sich nachteilig auf die AEP-Instanz auswirken und möglicherweise eine DoS-Situation auslösen.

### Geschätzte Traffic-Volumina

Traffic-Volumina sind in jedem Anwendungsfall für die Überprüfung erforderlich. Dies ist wichtig, da hohe Volumina zu einer Drosselung führen können, über die Kundschaft entsprechend benachrichtigt wird.

## Architektur

![[!UICONTROL Ereignisweiterleitung für mehrere Sandboxes]](assets/multi-sandbox-data-collection.png)

1. Erfassen und Senden von Ereignisdaten an die [!DNL Platform Edge Network] muss verwendet werden [!UICONTROL Ereignisweiterleitung]. Sie können Adobe-Tags für Client-seitig oder die [!DNL Platform Edge Network Server API] für die Server-zu-Server-Datenerfassung.

   Die [!DNL Platform Edge Network API] kann eine Server-zu-Server-Erfassungsfunktion bereitstellen. Dies erfordert jedoch ein anderes Programmiermodell zur Implementierung. Siehe [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de).

1. Die erfassten Payloads werden von der Tag-Implementierung an die [!DNL Platform Edge Network] der [!UICONTROL Ereignisweiterleitung] Dienst und Verarbeitung durch eigene [!UICONTROL Datenelemente], [!UICONTROL Regeln], und [!UICONTROL Aktionen]. Weitere Informationen zu den Unterschieden finden Sie unter [Tags und [!UICONTROL Ereignisweiterleitung]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de#differences-from-tags).

1. Ein [!UICONTROL Ereignisweiterleitung] -Eigenschaft ist auch erforderlich, um erfasste Ereignisdaten aus der [!DNL Platform Edge Network], ob diese Ereignisdaten an die [!DNL Platform Edge Network] durch eine bereitgestellte Tag-Implementierung oder eine Server-zu-Server-Sammlung.

   Autoren definieren die Datenelemente, Regeln und Aktionen, die zur Anreicherung der Ereignisdaten vor der Weiterleitung an die zweite Sandbox verwendet werden. Erwägen Sie die Verwendung des [!DNL JavaScript]-Datenelements „Benutzerspezifischer Code“, um Ihre Daten für die Sandbox-Aufnahme zu strukturieren. In Kombination mit den Datenvorbereitungsfunktionen von Platform haben Sie mehrere Möglichkeiten, Ihre Datenstruktur zu verwalten.

1. Derzeit ist die Verwendung der Adobe [!UICONTROL Cloud Connector-Erweiterung] in der Eigenschaft für die [!UICONTROL Ereignisweiterleitung] erforderlich. Nachdem die Regeln die Ereignisdaten verarbeitet oder anreichert haben, wird die [!UICONTROL Cloud Connector] wird innerhalb eines für eine POST konfigurierten Abruf-Aufrufs verwendet, der die Payload an die zweite Sandbox sendet.

1. Für die zweite Sandbox ist ein Streaming-Endpunkt für die Datenerfassung erforderlich. Sie können auch [!UICONTROL Datenvorbereitung] Funktionen in AEP zur Unterstützung der Erfassung und Zuordnung von [!UICONTROL Ereignisweiterleitung] Payloads an XDM. Weitere Informationen finden Sie in der AEP-Dokumentation zum [Erstellen einer HTTP-API-Streaming-Verbindung über die Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=de)
