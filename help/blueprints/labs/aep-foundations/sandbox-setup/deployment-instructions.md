---
title: Bereitstellungsanweisungen
description: Verwenden Sie die DEP-CLI, um die Schemata, Datensätze, Datenflüsse und Beispielprofildaten des AEP Foundations Lab Pack in Ihrer Sandbox bereitzustellen.
doc-type: article
solution: Experience Platform
exl-id: 9f2b6d4a-8e1c-4b7a-a3d5-6c9f0e2a4b8d
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 1%

---


# Bereitstellungsanweisungen

>[!NOTE]
>
>Dies ist nur erforderlich, wenn Sie die Labore in Ihrem eigenen Tempo bearbeiten. Wenn Sie sich an einem Live-Schulungskurs oder einer Live-Veranstaltung beteiligen, wurde Ihre Sandbox bereits für Sie bereitgestellt.

Das AEP Foundations Lab Pack wird mithilfe der DEP-CLI, einem Befehlszeilen-Tool zum Erstellen von Schemas, Datensätzen, Datenflüssen und Beispieldaten, die Sie in den Labs verwenden, in Ihrer Sandbox bereitgestellt.

## Bereitgestellte Komponenten

- 4 Identity-Namespaces
- 1 Schemaklasse, 13 Feldergruppen, 10 Schemata
- 12 Identitätsdeskriptoren, 6 Beziehungs-/Referenz-Deskriptoren, 3 Deskriptoren mit benutzerfreundlichen Namen
- 10 Katalogdatensätze
- 1 HTTP-API-Quellverbindung und 10 Datenflüsse
- Profildaten: ein einzelnes Depeche Mode-Profil (3 Trait-Datensätze, 7 Ereignis-Datensätze) plus 3 Lookup-Datensätze
- 2 Profilzusammenführungsrichtlinien und 1 Zielgruppe (beliebiges Ereignis-Streaming, innerhalb einer Stunde)

>[!NOTE]
>
>Die End-to-End-Bereitstellung dauert etwa 2 Stunden und 24 Minuten. Die meisten davon sind unbeaufsichtigte Wartezeiten zwischen den Schritten. Die CLI erzwingt diese Wartezeiten automatisch, sodass Sie selbst keine Zeit aufwenden müssen.

## Voraussetzungen

- **Lizenzberechtigungen.** Administratorrechte für eine IMS-Organisation mit Real-Time CDP (mit Streaming-Segmentierung)
- **Zugriffsrechte.** Eine Adobe Experience Platform-Rolle mit allen Berechtigungen für die Ziel-Sandbox, einschließlich der API-Anmeldedaten, die Sie im Setup von [Developer Console erstellt ](developer-console-setup.md).
- **Developer Console-Anmeldeinformationen.** Ein Projekt, das Adobe Experience Platform-APIs enthält. Wenn Sie diese noch nicht haben, befolgen Sie zuerst die Einrichtung von [Developer Console](developer-console-setup.md)
- **Eine Sandbox.** Leer, vom Typ `dev` und mindestens 60 Minuten lang im Status „Bereit“, bevor Sie die Bereitstellung starten
- **Node.js.** Jede neuere LTS-Version, unter Windows oder Mac

## &#x200B;1. Installieren des CLI

1. Klonen oder laden Sie das [dep-cli-Repository](https://github.com/adobe/dep-cli)
1. Führen Sie `npm install` im `dep-cli` aus.
1. Starten Sie die CLI mit `npm start`

>[!NOTE]
>
>Node.js ist erforderlich, bevor Sie die oben genannten Befehle ausführen. Wenn Sie Node.js noch nicht installiert haben, lesen Sie zuerst die Wiki-Seite [Node.js Setup](https://github.com/adobe/dep-cli/wiki/Nodejs-Setup). Vollständige Installationsdetails, einschließlich Screenshots und Informationen zum Aktualisieren einer vorhandenen Installation, finden Sie auf der Seite [Installation](https://github.com/adobe/dep-cli/wiki/Installation)wiki

## &#x200B;2. Konfigurieren der Umgebungsdatei

Die CLI wird in der Sandbox bereitgestellt, auf die Ihre Umgebungsdatei verweist. Daher muss diese ordnungsgemäß eingerichtet sein, bevor Sie etwas ausführen.

1. Kopieren Sie `envFiles/sample-env.json` und geben Sie ihm einen neuen Namen, z. B. `my-env.json`
1. Öffnen Sie die Datei und füllen Sie die folgenden Felder mit den Werten aus dem [Developer Console-Setup aus](developer-console-setup.md):

   | **Feld** | **Wert** |
   | --------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
   | `API_KEY` | Client-ID |
   | `CLIENT_SECRET` | Client-Geheimnis |
   | `IMS_ORG` | Organisations-ID |
   | `SCOPES` | Muss Experience Platform-API-Bereiche enthalten (openid, session, Adobe ID, read_organizations, additional_info.projectedProductContext) |
   | `SANDBOX_NAME` | Die Sandbox, die Sie anvisieren, muss leer sein und vom Typ `dev` sein |

1. Speichern und schließen Sie die Datei

>[!NOTE]
>
>Bei jeder Ausführung eines CLI-Befehls werden Sie aufgefordert, den Namen dieser Datei einzugeben, damit Sie sie in jedem nachfolgenden Schritt wiederverwenden können.

## &#x200B;3. Ausführen des AEP Foundation-Menüs

Wählen Sie im Hauptmenü **AEP Foundations** aus. Es gibt drei Schritte, und sie müssen der Reihe nach ausgeführt werden.

>[!WARNING]
>
>Die Sandbox muss sich vor der Ausführung von Schritt 1 mindestens 60 Minuten lang im Status „Bereit“ befinden.

| **Schritt** | **Was tut sie** | **Bevor Sie es ausführen** |
| ----------------------- | ------------------------------------------------------------------------------------------ | ------------------------------- |
| &#x200B;1. Profilbasis erstellen | Stellt Identity-Namespaces, Schemata, Datensätze, Zusammenführungsrichtlinien und Zielgruppen bereit | Sandbox „Bereit“ für über 60 Minuten |
| &#x200B;2. Profildaten laden | Erstellt Datenflüsse und Streams von Profil- und Lookup-Daten | Warten Sie 60 Minuten oder mehr nach Schritt 1 |
| &#x200B;3. Überprüfen der Profilkonsistenz | Überprüft, ob alle Daten korrekt geladen wurden | 15 Minuten oder mehr nach Schritt 2 warten |

Schritt 1 dauert etwa 2 Minuten, Schritt 2 etwa 6 Minuten, und Schritt 3 ist eine schnelle Validierung ohne eigene Wartezeit. Die 60- und 15-minütigen Lücken zwischen den Schritten bestehen darin, dass AEP die Daten hinter den Kulissen propagiert - das ist der Großteil Ihrer 2-Stunden-Zeitleiste.

>[!NOTE]
>
>Die CLI prüft diese Wartezeiten automatisch. Wenn man einen Schritt zu früh startet, blockiert er und sagt einem, wie viele Minuten noch übrig sind — man muss die Zeit nicht selbst nachverfolgen.

>[!NOTE]
>
>Schritt 2 kann sicher erneut ausgeführt werden, wenn ein Fehler auftritt. Vorhandene Eigenschaftsdatensätze werden überschrieben und doppelte Ereignisse werden übersprungen.

## Fehlerbehebung

>[!WARNING]
>
>**Konsistenzprüfung schlägt fehl mit fehlenden Ereignissen**. Einige Profildaten wurden noch nicht vollständig weitergegeben. Warten Sie weitere 15 Minuten und führen Sie die Konsistenzprüfung des Profils erneut aus. Wenn dies immer noch fehlschlägt, führen Sie „Profildaten laden“ erneut aus, warten Sie 15 Minuten und überprüfen Sie erneut.

**Etwas Anderes sieht falsch aus.** Als letzte Möglichkeit können Sie die Sandbox über das Menü Sandbox-Management der CLI zurücksetzen und ab Schritt 1 erneut bereitstellen.

>[!CAUTION]
>
>Das Zurücksetzen einer Sandbox ist destruktiv. Die CLI fordert Sie auf, den Sandbox-Namen einzugeben, um ihn zu bestätigen, bevor Sie fortfahren.
