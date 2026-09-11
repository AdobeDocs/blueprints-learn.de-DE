---
hold: true
title: Einrichten der Entwicklerkonsole
description: Erstellen Sie ein Adobe Developer Console-Projekt mit OAuth-Server-zu-Server-Anmeldedaten für die DEP-CLI, um sich bei Ihrer Sandbox zu authentifizieren.
doc-type: article
solution: Experience Platform
exl-id: 4a7c9e2b-1d3f-4a6e-8b9c-2d5e7f1a3c6b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Einrichten der Entwicklerkonsole

> [!NOTE]
>
>Dies ist nur erforderlich, wenn Sie die Labore in Ihrem eigenen Tempo bearbeiten. Wenn Sie sich an einem Live-Schulungskurs oder einer Live-Veranstaltung beteiligen, wurde Ihre Sandbox bereits für Sie bereitgestellt.

Die DEP-CLI authentifiziert sich mithilfe von OAuth-Server-zu-Server-Anmeldeinformationen aus einem Adobe Developer Console-Projekt bei Ihrer Sandbox. Diese Seite führt Sie durch die Erstellung dieses Projekts. Sie müssen dies nur einmal tun. Dieselben Anmeldeinformationen funktionieren sowohl in den AEP Foundations als auch in den AJO Architectural Foundations-Tracks, sofern Sie beide unten beschriebenen APIs hinzufügen.

>[!NOTE]
>
>Wenn Sie bereits über ein Developer Console-Projekt mit Anmeldeinformationen für Adobe Experience Platform (und, falls erforderlich, Adobe Journey Optimizer) verfügen, überspringen Sie diesen Abschnitt und navigieren Sie direkt zu [Bereitstellungsanweisungen](deployment-instructions.md).

## Voraussetzungen

- Eine Adobe ID mit Entwicklerzugriff auf Ihr Unternehmen
- Eine leere Adobe Experience Platform-Sandbox vom Typ `dev`
- Eine Adobe Experience Platform-Rolle mit allen für diese Sandbox gewährten Berechtigungen (fragen Sie Ihren Systemadministrator, wenn Sie sich nicht sicher sind)

## Erstellen des Projekts

1. Wechseln Sie zu [Adobe Developer Console](https://developer.adobe.com/console) und melden Sie sich an
1. Wenn Sie Zugriff auf mehr als ein Unternehmen haben, wählen Sie mit dem Organisationsschalter oben rechts das richtige Unternehmen aus
1. Wählen Sie **Neues Projekt erstellen**
1. Benennen Sie das Projekt in etwas um, das Sie später erkennen werden (z. B. `DEP Sandbox`)

## Experience Platform-API hinzufügen

1. Wählen Sie in der Projektübersicht die Option **API hinzufügen**
1. Wählen Sie das Produktsymbol **Adobe Experience Platform** und dann **Adobe Experience Platform-API aus**
1. Wählen Sie **Weiter**
1. Wählen Sie **OAuth Server-zu-Server** als Authentifizierungstyp aus und klicken Sie auf **Weiter**
1. Geben Sie der Berechtigung einen Namen und wählen Sie **Weiter**
1. Wählen Sie das Produktprofil aus, das der zu verwendenden Sandbox entspricht, und wählen Sie dann **Konfigurierte API speichern**

## Werte erfassen

Öffnen Sie die Übersichtsseite **OAuth Server-zu-Server** Ihrer Berechtigung. Sie benötigen vier Werte für die CLI-Umgebungsdatei:

| **Wert der Dev-Konsole** | **Env-Dateifeld** |
| --------------------- | ------------------------------- |
| Client-ID | `API_KEY` |
| Client-Geheimnis | `CLIENT_SECRET` |
| Organisations-ID | `IMS_ORG` (endet in `@AdobeOrg`) |
| Bereiche | `SCOPES` |

>[!NOTE]
>
>Kopieren Sie die Standardbereiche, die auf der Seite mit den Anmeldedaten angezeigt werden - Sie müssen keine Elemente manuell hinzufügen. Wenn Sie beide oben genannten APIs hinzugefügt haben, enthält die Bereichsliste automatisch beide.

Lassen Sie diese Seite geöffnet, oder kopieren Sie diese vier Werte an einen sicheren Ort. Sie fügen sie im nächsten Schritt des Einrichtungshandbuchs Ihres Tracks in die CLI-Umgebungsdatei ein.
