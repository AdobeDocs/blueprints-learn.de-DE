---
title: Zugriffstoken
description: Generieren eines OAuth-Server-zu-Server-Zugriffstoken in Postman und Verstehen der erforderlichen Kopfzeilen zum Authentifizieren von AEP-API-Aufrufen.
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%
---

# Zugriffstoken

## API-Sicherheitsübersicht



Um eine sichere API-Verbindung zu einem Adobe-Produkt herzustellen, stellt Adobe die Erstellung einer OAuth-Server-zu-Server-Anmeldedaten bereit. Dazu müssen Sie zunächst ein Entwicklerprojekt in der Adobe Developer Console erstellen. Um Zugriff auf die Developer Console zu erhalten, benötigen Sie Entwicklerrechte in der Adobe Admin Console. Sobald Sie über diese Rechte verfügen, erstellen Sie Entwicklerprojekte, die verschiedene produktbezogene APIs von Adobe verwenden. Sie verwenden an dieser Stelle die OAuth Server-zu-Server-Anmeldedaten. Um ein Zugriffs-Token zu generieren, müssen Sie einen bestimmten Anspruchssatz an den Identity Management Service (IMS) von Adobe übergeben. Bei OAuth-Server-zu-Server-Anmeldeinformationen sieht ein Beispielaufruf wie folgt aus:

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>Erfahren Sie mehr über den e2e-Prozess zum Erstellen des Entwicklerprojekts mit OAuth-Server-zu-Server-Anmeldeinformationen [hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens). Für das Bootcamp wird dieser Schritt absichtlich vereinfacht.



## Adobe Experience Platform + Adobe IMS

Jede Anfrage an einen Adobe-Service muss das Zugriffstoken in der Autorisierungs-Kopfzeile zusammen mit dem Client-Geheimnis enthalten, das bei der Erstellung des Entwicklerprojekts generiert wurde. Darüber hinaus benötigen Experience Platform und die zugehörigen Programme bei jeder Anfrage zwei weitere Header-Parameter.

- `x-gw-ims-org-id` - Dieser Parameter gibt den `IMS Org` an, zu dem die Anfrage gehört, und stellt sicher, dass die Verarbeitung der Anfragen in die entsprechende SaaS-Umgebung aufgelöst wird
- `x-sandbox-name` - Dieser Parameter gibt an, welche Sandbox die Anfrage in der Experience Platform verarbeiten soll

Nachdem Sie nun ein wenig darüber wissen, wie Adobe seine APIs sichert und was für die Zusammenarbeit mit ihnen erforderlich ist, verwenden Sie sie jetzt.

>[!CAUTION]
>
>Wenn Sie den `x-sandbox-name` nicht angeben, schlägt die Anfrage nicht fehl. Stattdessen wird die Anfrage standardmäßig in die `default`-Sandbox übertragen, die automatisch mit jeder Experience Platform-Umgebung bereitgestellt wird

>[!NOTE]
>
>Dieses Bootcamp enthält ein Entwicklerprojekt und eine Postman-Umgebungsdatei mit allen notwendigen Werten, um ein `access_token` anzufordern. Diese Umgebungsdatei haben Sie in den vorherigen Schritten des Labors hochgeladen

## Mit Postman authentifizieren

1. Starten Sie Postman, navigieren Sie zum Verzeichnis mit dem Titel `IMS Authenticate` und öffnen Sie die Anfrage durch Klicken darauf
1. Als Nächstes sehen Sie in der oberen rechten Ecke von Postman ein Dropdown-Menü Umgebung . Wählen Sie die `AEP Bootcamp` aus der Dropdown-Liste aus
1. Führen Sie nun den Aufruf aus, indem Sie auf die Schaltfläche „Senden“ klicken

![Postman-Anfrage nach dem Senden des IMS-Authentifizierungsaufrufs zum Generieren eines Zugriffs-Tokens](assets/access-token-execute-ims-authenticate-request.png)

Eine erfolgreiche Antwort sollte wie folgt aussehen:

```none
200 OK Successful Authentication
```

Erfolgreiche Antwort

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` - ist immer vom Typ Träger

`access_token` - Prüft die Autorisierung und ist in der Autorisierungskopfzeile aller API-Aufrufe erforderlich

`expires_in` - Millisekunden, bis das Zugriffstoken abläuft (heute 24-stündiger Gültigkeitszeitraum)

>[!SUCCESS]
>
>Herzlichen Glückwunsch! Sie haben sich erfolgreich authentifiziert und Ihr Zugriffs-Token wird jetzt in Ihrer Umgebungsdatei gespeichert



## Häufige Fehler

### Ungültiges Token

Dieser Fehler tritt auf, wenn die `private_key` in Ihrer Umgebungsdatei fehlerhaft oder nicht mehr gültig ist. Wenn dieser Fehler angezeigt wird, müssen Sie den gesamten Schlüssel einschließlich der Zeilenumbrüche kopiert haben

Beispiel:

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>Nur anwendbar bei Verwendung der JWT-basierten Authentifizierung

### Ungültige IMS-Organisation

Dieser Fehler tritt auf, wenn Sie vergessen haben, Ihre Postman-Umgebung aus der Dropdown-Liste festzulegen

![IMS_ORG nicht in aktiver Umgebung gefunden - Fehler, wenn keine Postman-Umgebung ausgewählt ist](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>Vergessen Sie nicht, beim Ausführen von API-Aufrufen Ihre Postman-Umgebung einzurichten
>
>![Auswählen der AEP Bootcamp-Umgebung aus der Dropdown-Liste &quot;Postman-Umgebung“](assets/access-token-set-postman-environment.png)
