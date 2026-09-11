---
title: Durchsuchen von Schemata
description: Erfahren Sie, wie Sie relationale Schemata durchsuchen und Entitätsbeziehungsdiagramme in Adobe Experience Platform anzeigen, um die in Kampagnen verwendeten Schemabeziehungen zu verstehen.
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# Durchsuchen von Schemata

## Ziel

Im nächsten Satz von Schritten navigieren Sie in der Benutzeroberfläche, um die Schemata und ihre Beziehungen anzuzeigen.  Dies ist wichtig, um sich mit den Schemata und Beziehungen vertraut zu machen, die beim Erstellen Ihrer Kampagne verfügbar sind.

## Anzeigen von Schemata

Das relationale Datenmodell Connection 5G wurde bereits für Sie erstellt. Sie können die Schemata selbst anzeigen, indem Sie in der Benutzeroberfläche zur Seite **Schemata ->**&quot; navigieren.

Geben Sie im Suchfeld `dep-rel` ein, um alle Schemata anzuzeigen.

![Suchergebnisse mit allen tiefen relationalen Schemata](assets/browse-schemas-search-results.png)

>[!NOTE]
>
>Beachten Sie, dass der Typ aller Schemata &quot;*&quot;*



## Beziehungsdiagramm anzeigen

Mit relationalen XDM-Schemata können Sie das Entitätsbeziehungsdiagramm (Entity Relationship Diagram, ERD) einfach anzeigen, indem Sie ein beliebiges Schema auswählen und auf die Schaltfläche Beziehungsdiagramm anzeigen klicken.

Gehen Sie folgendermaßen vor:

1. Klicken Sie auf die **Beziehungen** und dann auf die Schaltfläche **Beziehungsdiagramm anzeigen**.

![Registerkarte „Beziehungen“ mit der Schaltfläche „Beziehungsdiagramm anzeigen“](assets/browse-schemas-relationships-tab.png)



&#x200B;2. Klicken Sie auf **Schemata auswählen**
&#x200B;3. Wählen Sie im Popup-Fenster die Option `dep-rel: Customer Account` und klicken Sie dann auf **Bestätigen**

![Popup „Schemata auswählen“ mit Dep-rel: ausgewähltes Kundenkonto](assets/browse-schemas-select-schema-popup.png)



&#x200B;4. Klicken Sie im ERD auf die **3 Punkte** und wählen Sie **Zugehörige Elemente anzeigen**

![Option „Zugehörige Entitäten anzeigen“ im ERD-Kontextmenü](assets/browse-schemas-show-related-entities.png)



&#x200B;5. Zeigen Sie das ERD mit allen Tabellen an, die sich direkt auf Dep-rel: Kundenkonto beziehen. Optional können Sie das ERD als PNG-Datei herunterladen.

![Entitätsbeziehungsdiagramm mit Tabellen, die sich auf das Kundenkonto beziehen](assets/browse-schemas-erd-diagram.png)

>[!TIP]
>
>Ziemlich cool, eh?!

## Zusammenfassung

Sie haben jetzt gesehen, wie einfach die Navigation in der Benutzeroberfläche für Schemas und Beziehungen ist.  Sie können bestimmte Schemata auswählen und zu den Beziehungen navigieren, um die Daten in der Kampagnenorchestrierung besser zu verstehen und zu verwenden.

Weitere Informationen finden [&#x200B; (hier](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/data-management/get-started-schemas) wenn Sie Interesse haben.
