---
title: Multi-Sandbox-Ereignisweiterleitungs-Datenerfassung
description: Erfahren Sie, wie mit Experience Platform Web- und Mobile-SDKs erfasste Daten so konfiguriert werden können, dass sie ein einzelnes Ereignis erfassen und an mehrere Experience Platformen-Sandboxes weitergeleitet werden.
solution: Data Collection
kt: 7202
source-git-commit: e9a9abeaa722bb2f9a232f4e861b1b5eae86edd1
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 4%

---


# Multi-Sandbox-Ereignisweiterleitungs-Datenerfassung

Dieser Blueprint zeigt, wie mit Experience Platform Web- und Mobile-SDKs erfasste Daten so konfiguriert werden können, dass sie ein einzelnes Ereignis erfassen und an mehrere AEP-Sandboxes weiterleiten. Dieser Blueprint ist spezifisch für die Multi-Sandbox-Datenerfassung, die [!UICONTROL Ereignisweiterleitung] um dieses Ziel zu erreichen.

Zusätzlich zur Replikation des Ereignisses mit [!UICONTROL Ereignisweiterleitung] -Funktionen können Sie die ursprünglich erfassten Daten, die Anforderungen für andere Sandboxes erfüllen, hinzufügen, filtern oder bearbeiten.

[!UICONTROL Ereignisweiterleitung] verwendet eine separate -Eigenschaft, die [!UICONTROL Datenelemente], [!UICONTROL Regeln]und [!UICONTROL Erweiterungen] für Ihre Datenanforderungen erforderlich sind. Bei einem eingehenden Ereignis [!UICONTROL Ereignisweiterleitung] -Eigenschaft kann die Daten erfassen und bei Bedarf vor der Weiterleitung verwalten.

Ihre Ziel-Sandbox erfordert einen konfigurierten HTTP-Streaming-Endpunkt, der von der Adobe verwendet wird [!UICONTROL Cloud Connector] -Erweiterung.

## Anwendungsfälle

* Globale Datenberichte : Bei der Verwendung mehrerer Sandboxes zum Isolieren von Betriebsumgebungen und der Notwendigkeit, die Datenerfassung zu einer Sandbox zu konsolidieren, um die Sandbox-Berichterstattung zu vereinfachen. Routing eines Erlebnis-Edge-Ereignisses durch [!UICONTROL Ereignisweiterleitung] an eine Berichts-Sandbox übergeben, kann jede Sandbox-Betriebsumgebung Daten senden, da diese in Echtzeit an eine Berichterstellungs-Sandbox erfasst werden.

* Verwalten Sie die Datenerfassung Sandbox-übergreifend basierend auf unterschiedlichen Datenregeln für die einzelnen Sandbox-Betriebsumgebungen.

## Programme

* [!DNL Experience Platform] Datenerfassung
* [!UICONTROL Ereignisweiterleitung]
* AEP [!UICONTROL Erweiterung]
* [!UICONTROL Cloud Connector-Erweiterung]

## Allgemeine Überlegungen

Mit [!UICONTROL Ereignisweiterleitung] als Ansatz zum Senden von Daten an mehrere Sandboxes dienen, müssen Überlegungen in Ihrer Lösungsarchitektur berücksichtigt werden.

### Keine HIPAA-Daten

[!UICONTROL Ereignisweiterleitung] wird nicht als HIPAA-bereit betrachtet und sollte nicht in HIPAA-Anwendungsfällen verwendet werden, in denen HIPAA-Daten erfasst werden. Die für [!UICONTROL Ereignisweiterleitung] wird als HIPAA-bereit betrachtet und liegt ausschließlich im Ermessen des Kunden. Während [!UICONTROL Ereignisweiterleitung] Die Tag-Eigenschaft befindet sich im [!UICONTROL Ereignisweiterleitung] -System wird die gesamte erfasste Daten-Payload an die [!UICONTROL Ereignisweiterleitung] System zur Verarbeitung. Es ist dieser Prozess, der [!UICONTROL Ereignisweiterleitung] für HIPAA-Anwendungsfälle. Mit der gesamten Payload, die an die [!UICONTROL Ereignisweiterleitung] -System, würde dies alle HIPAA-Werte einschließen. Auch wenn die [!UICONTROL Ereignisweiterleitung] -Regeln filtern diese Daten, bevor sie an ihr Ziel gesendet werden, sodass HIPAA-Daten weiterhin an eine nicht HIPAA-bereite Infrastruktur gesendet werden. Die Payload-Daten werden jedoch nie gespeichert und sind lediglich ein Durchlauf.

### Verschiedene Datenspeicher und Streaming-Endpunkte

Als Daten fließen durch Datenspeicher von der [!UICONTROL Platform Edge Network]bei Verwendung von [!UICONTROL Ereignisweiterleitung] in eine andere AEP-Sandbox zu übertragen, ist es erforderlich, niemals denselben Datastream oder Streaming-Endpunkt zu verwenden wie den Datastream, der die ursprüngliche Sammlung erstellt. Dies kann sich nachteilig auf die AEP-Instanz auswirken und möglicherweise eine DoS-Situation auslösen.

### Geschätzte Traffic-Volumen

Traffic-Volumen sind für die Überprüfung mit jedem Anwendungsfall erforderlich. Dies ist wichtig, da hohe Volumina zu einer Drosselung führen können und Kunden benachrichtigt werden, wenn dies eintritt.

## Architektur

![Multi-Sandbox [!UICONTROL Ereignisweiterleitung]](assets/multi-sandbox-data-collection.png)

1. Erfassen und Senden von Ereignisdaten an die [!UICONTROL Platform Edge Network] erforderlich ist, um [!UICONTROL Ereignisweiterleitung]. Kunden können Adoben-Tags für Client-seitig oder die [!UICONTROL Platform Edge Network Server-API] für die Server-zu-Server-Datenerfassung. Die [!UICONTROL Platform Edge Network-API] kann eine Server-zu-Server-Erfassungsfunktion bereitstellen. Dies erfordert jedoch ein anderes Programmiermodell zur Implementierung. Siehe [Übersicht über die Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. Die erfassten Payloads werden von der Tag-Implementierung an die [!UICONTROL Platform Edge Network] der [!UICONTROL Ereignisweiterleitung] Dienst und Verarbeitung [!UICONTROL Datenelemente], [!UICONTROL Regeln] und [!UICONTROL Aktionen]. Weitere Informationen zu den Unterschieden [Tags und [!UICONTROL Ereignisweiterleitung]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. Ein [!UICONTROL Ereignisweiterleitung] -Eigenschaft ist auch erforderlich, um erfasste Ereignisdaten aus der [!UICONTROL Platform Edge Network]. Ob diese Ereignisdaten durch eine bereitgestellte Tag-Implementierung oder eine Server-zu-Server-Sammlung an das Platform Edge Network gesendet wurden. Autoren definieren die Datenelemente, Regeln und Aktionen, die zur Anreicherung der Ereignisdaten vor der Weiterleitung an die zweite Sandbox verwendet werden. Erwägen Sie die Verwendung des benutzerspezifischen Codes [!DNL JavaScript] -Datenelement zur Strukturierung Ihrer Daten für die Sandbox-Erfassung. In Kombination mit den Funktionen für die Datenvorbereitung in Platform haben Sie mehrere Möglichkeiten, Ihre Datenstruktur zu verwalten.

1. Derzeit wird die Adobe [!UICONTROL Cloud Connector-Erweiterung] ist innerhalb der [!UICONTROL Ereignisweiterleitung] Eigenschaft. Sobald die Regeln die Ereignisdaten verarbeiten oder anreichern, wird der Cloud Connector in einem Abruf verwendet, der für eine POST konfiguriert ist, die die Payload an die zweite Sandbox sendet

1. Für die zweite Sandbox ist ein Streaming-Endpunkt für die Datenerfassung erforderlich. Sie können auch die Datenvorbereitungsfunktionen in AEP berücksichtigen, um die Erfassung und Zuordnung von [!UICONTROL Ereignisweiterleitung] Payloads an XDM. Weitere Informationen finden Sie in der AEP-Dokumentation Erstellen einer [HTTP-API-Streaming-Verbindung über die Benutzeroberfläche](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=de)
