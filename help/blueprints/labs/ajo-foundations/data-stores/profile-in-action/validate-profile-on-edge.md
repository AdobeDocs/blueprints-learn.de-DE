---
title: Profil auf Edge validieren
description: Erfahren Sie, wie Sie auf der Registerkarte "Edge-Profilspeicher“ und „Zielgruppenmitgliedschaft“ den Profilstatus im Edge-Netzwerk überprüfen.
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Profil auf Edge validieren

## Lernziel

Vergewissern Sie sich, dass das Profil nicht im Edge-Netzwerkprofilspeicher vorhanden ist.

## Überprüfen des Edge-Profils

1. Klicken Sie auf die **Attribute** und das Optionsfeld **Edge**, um das Edge-Profil anzuzeigen

![Edge-Profil, angezeigt auf der Registerkarte „Attribute“](assets/validate-profile-on-edge-attributes-tab.png)

>[!NOTE]
>
>Es ist möglich, dass Sie eine „abgespeckte“ Version des Profils sehen, die nur aus den Identitäten besteht, je nachdem, wie viel Zeit vergangen ist.



2. Klicken Sie auf die Registerkarte Zielgruppenmitgliedschaft .  Es wird **leer**.

![Registerkarte „Zielgruppenmitgliedschaft leeren“ im Edge-Profil](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**Warum keine Edge-Mitgliedschaft?**
>
>Hätten wir nicht sehen sollen **dep: Any Event Edge (innerhalb einer Stunde)** qualifiziert?
>
>Obwohl wir eine Zielgruppe haben, die eine Edge-Bewertung hat, gibt es diese Zielgruppe auf der Edge nicht, da wir keinen Grund dafür haben… noch nicht.
>
>Wenn wir diese Zielgruppe verwenden (z. B. Entscheidungsfindung oder Ziele), werden die Zielgruppenregeln an die Edge gepusht und beim nächsten Streaming eines Ereignisses an die Edge wird diese Zielgruppe ausgewertet.
>
>Außerdem haben wir die Segmentierungs-Services von Edge nicht aktiviert.



## Zusammenfassung

Das Profil existiert (noch) nicht in Edge
