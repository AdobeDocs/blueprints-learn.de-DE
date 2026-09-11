---
hold: true
title: Erstellen eines Code-basierten Erlebniskanals
description: Konfigurieren Sie einen Code-basierten Erlebniskanal in Adobe Journey Optimizer, der JSON-Angebotsdaten an jedes Web-, Mobil- oder IoT-System zurückgibt, das eine Entscheidung anfordert.
doc-type: article
solution: Experience Platform
exl-id: c3353d3d-cd97-46b7-8ef8-c72fa9e7dfe5
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Erstellen eines Code-basierten Erlebniskanals

## Ziel

Denken Sie daran, dass die Geschäftsanforderungen darin bestehen, dass jedes der Systeme von Connection 5G in der Lage sein sollte, ein entsprechendes Angebot zurückzugeben. Unabhängig davon, ob es sich um den Computer eines Kundenagenten, einen Kiosk in einem Geschäft, eine mobile App oder die Website handelt, sollte der Kunde dasselbe Angebotserlebnis erhalten. Der einzige AJO-Kanal, der dies tun kann, ist ein Code-basiertes Erlebnis (CBE), einer der eingehenden AJO-Kanäle. Während ein CBE HTML zurückgeben kann, besteht seine Hauptfunktion darin, Informationen darüber zurückzugeben, welches Angebot dem empfangenden System unterbreitet werden soll, wobei dieses System weiß, was mit diesen Angebotsinformationen zu tun ist. Im Gegensatz zum Webkanal werden CBEs nicht automatisch gerendert oder gemeldet. Während es für den Kunden etwas mehr manuelle Arbeit ist, bieten sie viel Flexibilität, da sie so konfiguriert werden können, dass sie JSON zurückgeben, das jedes mobile, Web- oder IoT-System verwenden kann, um Entscheidungen auszuführen.

1. Erweitern Sie bei Bedarf das **Administration** Menüelement in der linken Leiste (Sie müssen wahrscheinlich nach unten scrollen) und klicken Sie auf **Kanäle**. Sie landen auf der Seite „Kanalkonfigurationen“.
2. Klicken Sie auf **blaue Schaltfläche „Kanalkonfiguration erstellen**.
3. Benennen Sie den Kanal auf der Seite „Kanalkonfigurationsdetails“ **jsonOffer\_cbe**

>[!NOTE]
>
>Da ein CBE von einer beliebigen Anzahl von Clients auf einer *N* Anzahl von Plattformen aufgerufen werden kann, benennen wir diesen CBE etwas Allgemeines für den Standort, aber spezifisch für die Tatsache, dass er Angebote im JSON-Format zurückgibt.

4. Legen Sie **Dropdown-** „Kanal auswählen“ auf **Code-basiertes Erlebnis“ fest**

>[!WARNING]
>
>Wir werden in diesem Labor keine Marketing-Aktion festlegen, da sie die Demonstration unnötig komplexer macht. Da jedoch auf CBEs von einer beliebigen Anzahl von Systemen zugegriffen werden kann, würden Sie in einem echten Anwendungsfall alle möglichen Marketing-Aktionen für diesen Kanal festlegen, damit DULE-Kennzeichnungen durchgesetzt werden.

5. Markieren Sie das **Web** im Bereich „Code-basierte Erlebniseinstellungen“ und lassen Sie die Option **Einzelseite** ausgewählt.
6. Geben **im Textfeld** Seiten-URL“ den `https://connection5g.com/home` ein
7. Geben **im Textfeld &quot;** auf Seite“ den Text **jsonOfferContainer**

>[!NOTE]
>
>Nicht jedes Erlebnisereignis, das an Edge-Trigger gesendet wird, enthält eine Anfrage für personalisierte Angebote. Sie erstellen eine Journey im nächsten Abschnitt, in dem dieser CBE mit der soeben konfigurierten Auswahlstrategie konfiguriert wird. Die Einstellung „Standort auf Seite“ ist der Name des in Erlebnisereignissen übergebenen Parameters, der Experience Edge anweist, alle Angebote zurückzugeben, die diesem CBE zugewiesen sind. Sie wird auch oft als Oberfläche bezeichnet. Ob es sich um eine Mobile App, eine Web-Seite oder ein anderes IoT-Gerät handelt: Wenn der Wert „jsonOfferContainer“ zusammen mit dem richtigen eventType über ein Erlebnisereignis an die Edge übergeben wird, führt die Edge die bisher im Labor konfigurierte Logik aus und gibt das entsprechende Angebot zurück.

8. Klicken Sie auf **Optionsfeld** JSON“ im Abschnitt „Format“. Wenn Sie fertig sind, sollte Ihre CBE-Kanalkonfiguration wie folgt aussehen:

![Code-basierte Konfiguration des Erlebniskanals mit ausgewähltem JSON-Format wurde abgeschlossen](assets/create-code-based-experience-channel-completed-config.png)

&#x200B;9. Sobald alles korrekt aussieht, klicken Sie auf die blaue **Senden**-Schaltfläche in der oberen rechten Ecke.

>[!TIP]
>
>Sobald er gespeichert wurde, gelangen Sie zurück zur Seite für die Kanalkonfiguration, wo Sie den neu erstellten CBE sehen.

## Zusammenfassung

Auf dieser Seite haben Sie einen Code-basierten Erlebniskanal (CBE) konfiguriert und einen neuen eingehenden Kanal eingerichtet, der Angebotsentscheidungen im JSON-Format zurückgeben kann, damit externe Systeme (wie Web-Seiten, Apps oder Kiosks) die entsprechenden Angebote basierend auf der zuvor erstellten Auswahlstrategie anfordern und empfangen können.
