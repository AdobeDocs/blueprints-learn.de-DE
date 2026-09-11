---
title: Rangfolgeformeln
description: Erfahren Sie, wie Rangfolgeformeln den Prioritätswert eines Entscheidungselements pro Profil mithilfe bedingter mathematischer Ausdrücke dynamisch anpassen.
doc-type: article
solution: Experience Platform
exl-id: 08183f1a-8db6-43c5-8b2e-05fa3d9c0f8d
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Rangfolgeformeln

## Lernziel

Am Ende dieser Lektion können Sie:

- Definieren Sie eine Rangfolgenformel und erklären Sie, was sie anpasst
- Erläuterung der If/Then-Struktur einer Rangfolgenformel
- Erläuterung, warum für jede Rangfolgenformel eine Standardformel erforderlich ist
- Ergebnis bestimmen, wenn zwei Entscheidungselemente auf demselben angepassten Prioritätswert landen

## Benötigte Materialien

- 12 Spielkarten (Bube, Dame, König aus jeder Farbe)
- 12 Haftnotizen, die sowohl mit dem Attributnamen als auch mit Werten aus früheren Lektionen gefüllt sind

## Vortrag

In dieser Lektion werden die Karten in mehreren Runden von Hand neu angeordnet - zuerst nach der ursprünglichen Priorität und dann nach zwei verschiedenen Rangfolgeformeln, die auf verschiedene Musterprofile angewendet werden. So können Sie sehen, wie sich die gleichen Elemente je nach Frage neu anordnen.

>[!VIDEO](https://video.tv.adobe.com/v/3502209/)

## Wichtige Erkenntnisse

- Eine Rangfolgenformel passt den Prioritätswert eines Entscheidungselements dynamisch pro Profil basierend auf Profilattributen oder dem auslösenden Erlebnisereignis an
- Formeln unterstützen eine einfache Mathematik (Hinzufügen, Subtrahieren, Multiplizieren, Dividieren) und können den ursprünglichen Prioritätswert des Entscheidungselements als Variable referenzieren
- Die Regellogik: Wenn eine Bedingung für das Profil oder den Treffer wahr ist, passen Sie die Priorität für Entscheidungselemente an, die bestimmte Elementkriterien erfüllen
- Jede Einrichtung einer Rangfolgenformel benötigt eine Standardformel für Entscheidungselemente, die von keiner Anpassungsregel berührt werden
- Wenn zwei Entscheidungselemente auf demselben angepassten Prioritätswert landen, werden sie in der Entscheidungsfindung zufällig sortiert
