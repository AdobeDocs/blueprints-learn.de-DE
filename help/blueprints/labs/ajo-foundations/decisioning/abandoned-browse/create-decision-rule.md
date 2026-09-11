---
hold: true
title: Entscheidungsregel erstellen
description: Erstellen Sie eine Entscheidungsregel, die die Berechtigung für Premium-Telefonangebote auf Kunden mit höherrangigen Plänen beschränkt.
doc-type: article
solution: Experience Platform
exl-id: 1c1e2d82-ca09-4074-813d-3b29af77388b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# Entscheidungsregel erstellen

## Ziel

Da die Eignung einer der wichtigsten Bausteine eines Angebots ist, besteht der erste Schritt darin, die erforderlichen Entitäten zu erstellen, um es zu unterstützen. In vielen Fällen ist die Zielgruppenzugehörigkeit der entscheidende Faktor, aber in diesem Fall verwenden wir Entscheidungsregeln. Mit Connection 5G kann iPhone 17s der höheren Klasse nur für Benutzer mit einem High-Tier-Plan aktiviert werden. Daher verwenden wir eine Entscheidungsregel, um sicherzustellen, dass Angebote für High-End-Telefone nur denjenigen zur Verfügung stehen, die einen ausreichend hohen Plan haben.

## Entscheidungsregel erstellen

1. Melden Sie sich bei Bedarf bei Adobe Experience Cloud an und navigieren Sie zu **Adobe Journey Optimizer.**
2. Erweitern Sie bei Bedarf den **Decisioning**-Menüeintrag in der linken Leiste und klicken Sie auf **Strategie einrichten.**

>[!WARNING]
>
>Stellen Sie sicher, dass Sie sich im Menü Entscheidungsfindung und NICHT im Menü Entscheidungs-Management befinden. Wenn das Menü Entscheidungs-Management erweitert ist, reduzieren Sie es, um Verwirrung bei der Navigation während dieses Labors zu vermeiden.

3. Klicken Sie **Menü &quot;**&quot; auf „Entscheidungsregeln“, gefolgt von der Schaltfläche **Regel erstellen** in der oberen rechten Ecke.

![Seite „Entscheidungsregeln“ mit der Schaltfläche „Regel erstellen“](assets/create-decision-rule-create-rule-button.png)

4. Dadurch wird ein Bildschirm geöffnet, der der Segment Builder-Benutzeroberfläche ähnelt. Fügen Sie das Attribut Plan-ID zur Arbeitsfläche für Regeln hinzu, indem Sie auf **Individuelles XDM-Profil > DEP >** klicken und dann das Attribut **Plan-ID** auf die Arbeitsfläche ziehen.
5. Ändern Sie die Dropdown-Liste von gleich in **enthält.**
6. Geben Sie den Text **2** in das Feld ein, drücken Sie die **Tab**-Taste, um den Wert 2 zu akzeptieren, und geben Sie dann einen **3 ein.** drücken Sie **Tab** erneut, sodass die Regel nach Plan-IDs sucht, die eine 2 oder 3 enthalten
7. Verwenden Sie das **Name** in der rechten Leiste, um die Entscheidungsregel zu benennen **Upper Tier Plans**. Fügen Sie eine Beschreibung hinzu, wenn Sie möchten. Nach Abschluss sollte Ihre Entscheidungsregel wie folgt aussehen:

![Entscheidungsregel für abgeschlossene Pläne der oberen Ebene mit Plan-ID mit 2 oder 3](assets/create-decision-rule-upper-tier-plans-finished.png "Entscheidungsregel für abgeschlossene Pläne der oberen Ebene mit Plan-ID mit 2 oder 3")

8. Sobald die Regel korrekt ist, klicken Sie auf die blaue Schaltfläche **Erstellen** in der oberen rechten Ecke und Sie werden zur Seite „Strategie einrichten“ zurückgeleitet, auf der die soeben erstellte Entscheidungsregel als einzige Entscheidungsregel aufgeführt ist.

>[!NOTE]
>
>Warum sollte ich eine Entscheidungsregel anstelle einer Zielgruppe verwenden? In der Praxis wären die Hauptgründe dafür, dass Sie für das Entscheidungspaket spezifische Eignungskriterien oder Attribute der Angebote in den Kriterien benötigten. Angebotsattribute sind in Audience Builder nicht in verfügbaren Feldern verfügbar.
>
>Die in diesem Labor verwendete Entscheidungsregel für Pläne der oberen Ebene wäre wahrscheinlich eine tatsächliche Zielgruppe in einer realen Implementierung, da sie wahrscheinlich außerhalb von Decisioning wiederverwendet werden kann. Hier wurde jedoch eine Entscheidungsregel zu pädagogischen Zwecken verwendet, um ihre Funktionalität und die verschiedenen Möglichkeiten zur Anwendung der Berechtigung zu präsentieren.

## Zusammenfassung

Sie haben jetzt eine wiederverwendbare Entscheidungsregel erstellt, die Sie für die Angebotseignung verwenden werden.
