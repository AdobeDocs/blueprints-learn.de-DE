---
title: Passthrough-Zuordnungen korrigieren
description: Identifizieren und korrigieren Sie falsche KI-/ML-Passthrough-Zuordnungen, z. B. doppelte oder nicht übereinstimmende Zielfeldzuweisungen, bevor Sie eine Validierung durchführen.
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Passthrough-Zuordnungen korrigieren

## Spezifische Zuordnungen ablegen

Einige der Quelldaten, die Sie haben, müssen mit berechneten Feldern verarbeitet werden.  Um diese zu beheben, ziehen Sie sie aus den Zuordnungen und überprüfen Sie die Zuordnungen erneut.

1. Folgende Quelldaten aus den Zuordnungen ablegen:
   - Geburtsdatum
   - Quelle
   - sms\_optIn
1. Validieren Sie die Zuordnungen erneut, indem Sie auf die Schaltfläche Validieren klicken

![Schaltfläche „Validieren“ wird verwendet, um Zuordnungen nach dem Ablegen von Feldern erneut zu validieren](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png " Zuordnungen mithilfe der Schaltfläche „Validieren“ erneut zu validieren")

>[!NOTE]
>
>Nach dem Klicken auf Validieren sind möglicherweise weiterhin Fehler vorhanden



## Beispiele für falsche Zuordnungen

KI/ML-Empfehlungen sind zwar hilfreich, liegen aber manchmal falsch.  Wenn Sie Ihre Empfehlungen überprüfen, können diese Fehlertypen auftreten, die Sie beheben müssen

>[!NOTE]
>
>Im Folgenden finden Sie einige Beispiele für ungültige Zuordnungen, die Sie möglicherweise in Ihrer eigenen Sandbox sehen. Möglicherweise werden auch andere Fehler angezeigt.

## Doppelte Zuordnungen

In diesem Szenario sehen Sie, dass der KI/ML-Recommender zwei verschiedene Quellfelder demselben Zielfeld (person.name **lastName) zugeordnet**



![Zwei verschiedene Quellfelder, die demselben Zielfeld „person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName“ zugeordnet sind, werden in dieser Zuordnung zweimal zugeordnet")

![Beispiel für doppelte Passthrough-Zuordnung mit Beteiligung des plan_name-Felds](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)



## Fehlerhafte Zuordnungen

Diese Zuordnung sieht richtig aus, ist aber bei näherer **(**) nicht dasselbe wie **emailFormat**

![Zuordnung, bei der E-Mail falsch zugeordnet ist, anstelle von &#x200B;](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "-Mail scheint korrekt zugeordnet zu sein, ist jedoch gemäß den Anforderungen falsch")

Hier wird **email\_optIn** fälschlicherweise dem falschen Einverständnisobjekt zugeordnet

![email_optIn, das falsch dem falschen Einverständnisobjekt zugeordnet ist](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn scheint korrekt zugeordnet zu sein, ist aber gemäß den Anforderungen falsch")



## Beheben von Passthrough-Zuordnungen

Führen Sie die folgenden Schritte aus, um Passthrough-Zuordnungen zu beheben, die fälschlicherweise auf das falsche Zielfeld verweisen.

### Beispiel

1. Beginnen Sie mit einer ungültigen Zuordnung und klicken Sie auf das Feld Zielfeld . In der folgenden Zuordnung wird beispielsweise das Feld **person.name.lastName** nicht korrekt zugeordnet und **planName**
1. Wählen Sie im rechts geöffneten Bedienfeld Zielschema das entsprechende Zielfeld aus und klicken Sie auf **\_devbc.plan.name**
1. Das Zielfeld sollte jetzt im Zielfeld aktualisiert werden
1. Nachdem Sie jeden dieser Fehler behoben haben, sollten Sie auf die Schaltfläche **Validieren** klicken, um sicherzustellen, dass Sie diese Fehlerarten reduzieren und keine neuen einführen.



![Bearbeiten der Zuordnungsliste zur Behebung jedes Zuordnungsfehlers](assets/fix-passthrough-mappings-work-through-mapping-errors.png "Arbeiten Sie sich durch die Zuordnung und beheben Sie die Zuordnungsfehler")



![Bedienfeld „Target-Schema“ für die Auswahl des richtigen Felds, um eine Passthrough-Zuordnung zu beheben](assets/fix-passthrough-mappings-choose-correct-target-field.png " Wählen Sie das richtige Zielfeld aus und überprüfen Sie, ob es den Passthrough-Anforderungen entspricht")

>[!WARNING]
>
>Fahren Sie erst mit dem nächsten Schritt fort, wenn Sie alle Zuordnungsfehler behoben haben
