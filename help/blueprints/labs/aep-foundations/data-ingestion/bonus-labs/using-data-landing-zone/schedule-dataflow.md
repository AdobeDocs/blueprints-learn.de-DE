---
hold: true
title: Datenfluss planen
description: Konfigurieren Sie einen wiederkehrenden 15-minütigen Datenflusszeitplan mit aktivierter Aufstockung und verstehen Sie, wie sich UTC-Startzeiten auf Ausführungen auswirken.
doc-type: article
solution: Experience Platform
exl-id: 9865b1eb-0d98-4cae-a928-69ea897607ca
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Datenfluss planen

Im Schritt **Planung**:

1. Stellen Sie die **Häufigkeit** auf Minute ein.
1. Stellen Sie **Intervall** auf 15 ein, d. h. auf 15 Minuten.
1. Aktivieren Sie **Option** Aufstockung“.

>[!NOTE]
>
>Beachten Sie, dass **Startzeit** in UTC angegeben ist.
>
>Coordinated Universal Time (UTC) ist ein globaler Zeitstandard, der als Bezugspunkt für die Zeitmessung weltweit verwendet wird. Für ein global verteiltes Team stellt sie eine gemeinsame Referenz für verschiedene Regionen und Länder bereit, was die Koordination von Aktivitäten und die Planung von Ereignissen über verschiedene Zeitzonen hinweg erleichtert.
>
>In verschiedenen Teilen der AEP-Benutzeroberfläche wird UTC-Zeit als Grundlage für die Zeitplanung angezeigt. UTC Time ist 1 Stunde hinter London Time. Wenn Sie sich bezüglich der UTC-Zeit nicht sicher sind, googeln Sie einfach „UTC-Zeit jetzt“.

>[!NOTE]
>
>In der Praxis führt **Option** Aufstockung“ eine einmalige Aufstockung aller Dateien durch, und die nachfolgenden Ausführungen nehmen neue Dateien auf.

![Planen der Datenflussausführung mit den festgelegten Häufigkeit-, Intervall- und Aufstockungsoptionen](assets/schedule-dataflow-scheduling-dataflow-run.png "Planen der Datenflussausführung")

Überprüfen Sie den Datenfluss und klicken Sie auf **Beenden.**

![Überprüfen der endgültigen Datenflusskonfiguration vor dem Klicken auf Beenden](assets/schedule-dataflow-review-final-dataflow.png "Überprüfen des endgültigen Datenflusses")

>[!CAUTION]
>
>Wenn Sie die Option **Einmal ausführen** für Ihren Datenfluss auswählen, können Sie diesen Zeitplan nicht bearbeiten oder den Datenfluss später aktualisieren. Sie können den Datenfluss jedoch bei Bedarf ausführen, d. h. erneut ausführen, wenn Sie neue Daten aufnehmen müssen.

Nachdem Sie auf **Beenden** geklickt haben, gelangen Sie zurück zum Bildschirm **Datenflüsse**. Es sollte einige Minuten dauern, bis der Datenfluss erstellt ist. Beachten Sie, dass der letzte Ausführungsstatus für den Datenfluss &quot;**Ausführungen“**. Der erste Durchgang sollte in ein paar Minuten beginnen.

![Datenflussbildschirm, der den neuen Datenfluss mit dem Status „Keine Ausführungen“ anzeigt](assets/schedule-dataflow-dataflows-screen-no-runs-status.png "Datenflussquellen-Bildschirm")

&#x200B;> [!NOTE]
>
>Sie müssen die Seite kontinuierlich aktualisieren, um die Statusaktualisierung anzuzeigen, da das Backend keine Aktualisierungen an die Benutzeroberfläche sendet.

>[!NOTE]
>
>Wenn Sie alle Warnhinweise aktiviert haben, erhalten Sie einen Warnhinweis in Ihrem Browser in der oberen rechten Ecke Ihres Browsers, wenn der Fluss zu laufen beginnt und erfolgreich abgeschlossen wird oder fehlschlägt
