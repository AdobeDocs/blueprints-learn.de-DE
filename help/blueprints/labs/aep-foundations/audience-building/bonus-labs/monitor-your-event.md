---
title: Überwachen des Ereignisses
description: Verwenden Sie Adobe Experience Platform Assurance, um eine Debug-Sitzung zu erstellen, ein validiertes Ereignis über Postman zu senden und die Edge-Ereignisverarbeitungsprotokolle zu überprüfen.
doc-type: article
solution: Experience Platform
exl-id: 94b200c0-6714-4996-a266-119cc8f7f4e2
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 1%

---


# Überwachen des Ereignisses

## Zu Assurance navigieren

[Adobe Experience Platform Assurance](https://experienceleague.adobe.com/de/docs/experience-platform/assurance/home) ist ein Produkt von Adobe Experience Cloud, mit dem Sie die Datenerfassung in Adobe Experience Platform Edge untersuchen, testen, simulieren und validieren können.

1. Gehen Sie zu Adobe Experience Platform > Assurance > Sitzung erstellen .

![Navigieren Sie zu Adobe Experience Platform Assurance und erstellen Sie eine Sitzung](assets/monitor-your-event-navigate-to-assurance-create-session.png)



2. Klicken Sie auf die Schaltfläche **Starten**.

![Klicken Sie auf die Schaltfläche Start , um mit der Konfiguration der Assurance-Sitzung zu beginnen](assets/monitor-your-event-click-start-button.png)



## Konfigurieren einer Sitzung

1. Name —> \[Sandbox] Edge-Sitzung
1. URL —> https\://www\.adobe.com
   - Beachten Sie, dass diese URL durch die tatsächliche Website Ihres Kunden ersetzt wird
1. Klicken Sie auf die Schaltfläche Weiter

![Klicken Sie auf Weiter , nachdem Sie den Sitzungsnamen und die URL eingegeben haben](assets/monitor-your-event-click-next-button.png)

4. Kopieren Sie den Link an eine Stelle, auf die Sie später verweisen können.

5. Klicken Sie auf **Fertig**-Schaltfläche

![Kopieren Sie den Link Assurance-Sitzung und klicken Sie auf Fertig](assets/monitor-your-event-copy-link.png)



6. Navigieren Sie zu **Einstellungen**

![Navigieren Sie in der Assurance-Sitzung zur Registerkarte Einstellungen ](assets/monitor-your-event-navigate-to-settings.png " klicken Sie auf Einstellungen")



7. Aktivieren Sie **Ereignistransaktionen** und **Edge Delivery**, indem Sie auf die Schaltfläche **+** und dann **Fertig**

![Ereignistransaktionen und Edge Delivery aktivieren und dann auf „Fertig“ klicken](assets/monitor-your-event-enable-event-transactions-and-edge-delivery.png)


## Postman öffnen

Wechseln Sie zu Postman -> Web-Ereignis-Edge erstellen (keine Authentifizierung) -> Kopfzeilen

1. Fügen Sie den Headern **x-adobe-aep-validation**-token mit dem oben aus Assurance kopierten Link hinzu. Erfassen Sie **nur die ID**-Wert nach dem = in der Relation, die Sie aus Assurance kopiert haben. z. B. [https://www.adobe.com/?adb\_validation\_sessionid=](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)[`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)
1. Wir würden nur den [`efa4a9ed-02d8-4647-80fa-f01a5be273d0`](https://www.adobe.com/?adb_validation_sessionid=efa4a9ed-02d8-4647-80fa-f01a5be273d0)-Wert verwenden, nicht die vollständige URL

![Fügen Sie die Kopfzeile „x-adobe-aep-validation-token“ mit der Assurance-Sitzungs-ID in Postman hinzu](assets/monitor-your-event-populate-the-x-adobe-aep-validation-token.png)



3. Speichern und führen Sie in Postman die Anfrage **Web-Ereignis-Edge erstellen (keine Authentifizierung)** aus



## Assurance-Protokolle anzeigen

Kehren Sie zu Assurance zurück. Dort sollten Sie eine Reihe von Ereignissen sehen. Filtern Sie nach nur relevanten Ereignistypen, indem Sie Ihre Datenstrom-ID in die Suche einfügen

![Filtern Sie Assurance-Ereignisse, indem Sie nach Ihrer Datenstrom-ID suchen](assets/monitor-your-event-filter-using-search.png)



Wählen Sie ein Ereignis aus und öffnen Sie bei Bedarf alle Nachrichten in der rechten Leiste.

![Wählen Sie ein Ereignis aus und erweitern Sie seine Nachrichten in der rechten Leiste](assets/monitor-your-event-expand-messages.png)

Ereignistypen, nach denen gesucht werden soll:

- hitReceived (zeigt die Payload an, die von der Edge empfangen wurde)
- EvaluatingRule (wenn Sie SSF einrichten, zeigt die ausgewerteten Regeln an)
- firedestinations (Ziele, an die das gesendet wurde)
- Segmente gefunden (konnte er für beliebige Edge-Segmente qualifiziert werden)
- com.adobe.experience\_platform.edge\_segmentation/response (mit welchen Segmenten hat sie geantwortet)

![Wählen Sie jeden Ereignistyp aus, um zu sehen, wie Assurance ihn interpretiert](assets/monitor-your-event-select-each-event.png)

Erkunden Sie diese und sehen Sie, wie die einzelnen Schritte von Assurance interpretiert werden.
