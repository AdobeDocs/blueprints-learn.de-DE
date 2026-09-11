---
hold: true
title: Bereitstellungsanweisungen
description: Verwenden Sie die DEP-CLI, um die Schemata, Datensätze, Datenflüsse und Beispieldaten des AJO Architectural Foundations Lab Pack in Ihrer Sandbox bereitzustellen.
doc-type: article
solution: Experience Platform
exl-id: 3d6e9a1c-7b2f-4e8a-9d0c-1f5a8b6c2e3d
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 1%

---


# Bereitstellungsanweisungen

>[!WARNING]
>
>Dies ist nur erforderlich, wenn Sie die Labore in Ihrem eigenen Tempo bearbeiten. Wenn Sie sich an einem Live-Schulungskurs oder einer Live-Veranstaltung beteiligen, wurde Ihre Sandbox bereits für Sie bereitgestellt.

Das AJO Architectural Foundations Lab Pack wird mit der DEP-CLI in Ihrer Sandbox bereitgestellt, einem Befehlszeilen-Tool, das die Schemas, Datensätze, Datenflüsse und Beispieldaten erstellt, die Sie in den Labs verwenden werden - sowohl im Profilspeicher als auch im relationalen AJO-Speicher, der für orchestrierte Kampagnen verwendet wird.

## Bereitgestellte Komponenten

**Profilspur**

- Identity-Namespaces (customerID, planID, productID)
- Für Profile aktivierte Standard-XDM-Feldergruppen, -Deskriptoren und -Schemata
- Für Profil aktivierte Katalogdatensätze
- Zusammenführungsrichtlinien und Zielgruppen
- Profildaten für drei Beispieldatensätze: Depeche-Modus (Eigenschaften + Ereignisse), Stranger Things (Eigenschaften) und Decisioning (Eigenschaften)

**Relationale Spur**

- Der Identity-Namespace der customerID
- 11 relationale XDM-Schemata mit Primärschlüssel-, Fremdschlüssel- und Versionsdeskriptoren
- 11 Datensätze für von AJO orchestrierte Kampagnen aktiviert
- 11 Datenflüsse, die Daten aus der Data Landing Zone laden

>[!NOTE]
>
>Die End-to-End-Bereitstellung dauert etwa 2 Stunden und 23 Minuten. Profil- und relationale Tracks werden parallel ausgeführt und meistens handelt es sich um unbeaufsichtigte Wartezeiten, die von der CLI automatisch erzwungen werden.

## Voraussetzungen

- **Lizenzberechtigungen.** Administratorrechte für eine IMS-Organisation mit Real-Time CDP (mit Streaming-Segmentierung) und Adobe Journey Optimizer (mit orchestrierten Kampagnen)
- **Zugriffsrechte.** Eine Experience Platform-Rolle mit allen Berechtigungen für die Ziel-Sandbox, einschließlich der API-Anmeldeinformationen, die Sie bei der Einrichtung von [Developer Console erstellt &#x200B;](developer-console-setup.md).
- **Developer Console-Anmeldeinformationen.** Ein Projekt, das sowohl Adobe Experience Platform-APIs als auch Adobe Journey Optimizer-APIs enthält. Wenn Sie diese noch nicht haben, befolgen Sie zuerst die Einrichtung von [Developer Console](developer-console-setup.md)
- **Eine Sandbox.** Leer, vom Typ `dev` und mindestens 120 Minuten lang im Status „Bereit“, bevor Sie die Bereitstellung starten
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
2. Öffnen Sie die Datei und füllen Sie die folgenden Felder mit den Werten aus dem [Developer Console-Setup aus](developer-console-setup.md):

| **Feld** | **Wert** |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `API_KEY` | Client-ID |
| `CLIENT_SECRET` | Client-Geheimnis |
| `IMS_ORG` | Organisations-ID |
| `SCOPES` | Muss sowohl Experience Platform-API- als auch Adobe Journey Optimizer-API-Bereiche enthalten <br />*(z. B. cjm.suppression\_service.client.delete, cjm.suppression\_service.client.all, openid, session, AdobeID, read\_organizations, additional\_info.projectedProductContext)* |
| `SANDBOX_NAME` | Die Sandbox, die Sie anvisieren, muss leer sein und vom Typ `dev` sein |

&#x200B;3. Speichern und schließen Sie die Datei

>[!NOTE]
>
>Bei jeder Ausführung eines CLI-Befehls werden Sie aufgefordert, den Namen dieser Datei einzugeben, damit Sie sie in jedem nachfolgenden Schritt wiederverwenden können.

## &#x200B;3. Ausführen des Menüs &quot;AJO Architectural Foundations“

Wählen Sie im Hauptmenü **AJO Arch Foundations** aus. Es sind sechs Stufen auf zwei Gleise verteilt.

### Profilspur (in der richtigen Reihenfolge)

>[!WARNING]
>
>Die Sandbox muss sich vor der Ausführung von Schritt 1 mindestens 60 Minuten lang im Status „Bereit“ befinden.

| **Schritt** | **Was tut sie** | **Bevor Sie es ausführen** |
| ------------------------ | ------------------------------------------------------------------------------------------- | ---------------------------------- |
| &#x200B;1. Profilbasis erstellen | Stellt Identity-Namespaces, Schemata, Datensätze, Zusammenführungsrichtlinien und Zielgruppen bereit | Sandbox „Bereit“ für über 60 Minuten |
| &#x200B;2. Profildaten laden | Erstellt Datenflüsse und streamt Depeche Mode, Stranger Things und Decisioning-Profildaten | Warten Sie 60 Minuten oder mehr nach Schritt 1 |
| &#x200B;3. Überprüfen der Profilkonsistenz | Überprüft, ob alle Profildaten korrekt geladen wurden | 15 Minuten oder mehr nach Schritt 2 warten |

Schritt 1 dauert etwa 2 Minuten, Schritt 2 etwa 6 Minuten.

>[!NOTE]
>
>Schritt 2 kann sicher erneut ausgeführt werden, wenn ein Fehler auftritt. Dabei werden vorhandene Eigenschaften überschrieben und doppelte Ereignisse übersprungen.

### Relationale Spur

>[!WARNING]
>
>Die Sandbox muss sich seit mindestens 120 Minuten im Status „Bereit“ befinden, bevor Sie Schritt 4 oder Schritt 6 ausführen.

| **Schritt** | **Was tut sie** | **Bevor Sie es ausführen** |
| ----------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| &#x200B;4. Relationale Basis erstellen | Erstellt den Namespace „customerID“ und relationale Schemata/Deskriptoren/Datensätze | Sandbox „Bereit“ für über 120 Minuten |
| &#x200B;5. Relationale Daten laden | Lädt 11 CSV-Dateien und erstellt die Datenflüsse, die sie laden | Läuft direkt nach Schritt 4 - kein manuelles Warten erforderlich |
| &#x200B;6. Bereitstellen relationaler Datenbanken und Daten | Kombiniert die Schritte 4 und 5 in einem einzigen Durchgang von ~5 Minuten | Sandbox „Bereit“ für über 120 Minuten |

>[!NOTE]
>
>Verwenden Sie Schritt 6, anstatt die Schritte 4 und 5 separat auszuführen - dies geschieht in einem Schritt genauso, wenn die Propagierungswartezeit für Sie gehandhabt wird.
> [!NOTE]
>
>Alle oben genannten Wartezeiten werden automatisch von der CLI überprüft. Wenn Sie einen Schritt zu früh ausführen, wird er blockiert und gibt an, wie lange Sie warten müssen.

## Fehlerbehebung

>[!WARNING]
>
>**Die Konsistenzprüfung des Profils schlägt fehl und es fehlen Ereignisse.** Einige Profildaten wurden noch nicht vollständig weitergegeben. Warten Sie weitere 15 Minuten und führen Sie die Konsistenzprüfung des Profils erneut aus. Wenn dies immer noch fehlschlägt, führen Sie „Profildaten laden“ erneut aus, warten Sie 15 Minuten und überprüfen Sie erneut.

>[!WARNING]
>
>**Das Laden relationaler Daten schlägt teilweise fehl.** Jeder API-Aufruf kann bis zu dreimal wiederholt werden. Wenn die Bereinigung weiterhin fehlschlägt, werden die Quellverbindungen, Zielverbindungen und Datenflüsse entfernt, die erstellt wurden, sodass Sie Schritt 5 (oder Schritt 6) sauber erneut ausführen können. Zuordnungssätze können nicht über die API gelöscht werden und bleiben möglicherweise zurück. Dies wirkt sich nicht auf die Neubereitstellung aus.

**Etwas Anderes sieht falsch aus.** Als letzte Möglichkeit können Sie die Sandbox über das Menü Sandbox-Management der CLI zurücksetzen und ab Schritt 1 erneut bereitstellen.

>[!CAUTION]
>
>Das Zurücksetzen einer Sandbox ist destruktiv. Die CLI fordert Sie auf, den Sandbox-Namen einzugeben, um ihn zu bestätigen, bevor Sie fortfahren.
