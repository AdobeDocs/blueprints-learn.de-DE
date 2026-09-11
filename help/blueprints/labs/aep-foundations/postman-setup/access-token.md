---
title: Zugriffstoken
description: Generieren eines OAuth-Server-zu-Server-Zugriffstoken in Postman und Verstehen der erforderlichen Kopfzeilen zum Authentifizieren von AEP-API-Aufrufen.
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Zugriffstoken

## API-Sicherheitsübersicht



Um eine sichere API-Verbindung zu einem Adobe-Produkt herzustellen, erstellt Adobe OAuth-Server-zu-Server-Anmeldedaten. Dazu müssen Sie zunächst ein Entwicklerprojekt in der Adobe Developer Console erstellen. Um Zugriff auf die Developer Console zu erhalten, benötigen Sie Entwicklerrechte in der Adobe Admin Console. Sobald Sie über diese Rechte verfügen, können Sie Entwicklerprojekte mit den verschiedenen produktbezogenen APIs von Adobe erstellen. Hier kommen die OAuth Server-zu-Server-Anmeldedaten ins Spiel. Um ein Zugriffs-Token zu generieren, müssen Sie einen bestimmten Anspruchssatz an den Identity Management Service (IMS) von Adobe übergeben. Bei OAuth-Server-zu-Server-Anmeldeinformationen würde ein Beispielaufruf wie folgt aussehen:

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>Weitere Informationen zum e2e-Prozess zum Erstellen des Entwicklerprojekts mithilfe von OAuth-Server-zu-Server-Anmeldeinformationen [&#x200B; Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens). Für das Bootcamp werden wir diesen Schritt des Prozesses „per Hand winken“ 😄



## Adobe Experience Platform + Adobe IMS

Jede Anfrage an einen Adobe-Service muss das Zugriffstoken in der Autorisierungs-Kopfzeile zusammen mit dem Client-Geheimnis enthalten, das bei der Erstellung des Entwicklerprojekts generiert wurde. Darüber hinaus erfordern die Experience Platform und die zugehörigen Anwendungen, dass bei jeder Anfrage zwei weitere Header-Parameter vorhanden sind.

- `x-gw-ims-org-id` - Dieser Parameter gibt den `IMS Org` an, zu dem die Anfrage gehört, und stellt sicher, dass die Verarbeitung der Anfragen in die entsprechende SaaS-Umgebung aufgelöst wird
- `x-sandbox-name` - Dieser Parameter gibt an, welche Sandbox die Anfrage in der Experience Platform verarbeiten soll

Nachdem Sie nun ein wenig darüber wissen, wie Adobe seine APIs sichert und was für die Zusammenarbeit mit ihnen erforderlich ist, verwenden Sie sie jetzt.

>[!CAUTION]
>
>Wenn Sie den `x-sandbox-name` nicht angeben, schlägt die Anfrage nicht wie erwartet fehl. Stattdessen wird die zu verarbeitende Anfrage standardmäßig in die `default`-Sandbox übertragen, die automatisch mit jeder Experience Platform-Umgebung bereitgestellt wird

>[!NOTE]
>
>Im Rahmen dieses Bootcamps haben wir ein Entwicklerprojekt erstellt und Ihnen eine Postman-Umgebungsdatei mit allen notwendigen Werten zur Anfrage eines `access_token` zur Verfügung gestellt. Dies haben Sie in den vorherigen Schritten des Labors hochgeladen

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

`token_type` - immer vom Typ Träger

`access_token` - Prüft die Autorisierung und ist in der Autorisierungskopfzeile aller API-Aufrufe erforderlich

`expires_in` - Millisekunden, bis das Zugriffs-Token abläuft (heutiger Ablaufzeitraum von 24 Stunden)

>[!TIP]
>
>Herzlichen Glückwunsch! Sie haben sich erfolgreich authentifiziert und Ihr Zugriffs-Token wird jetzt in Ihrer Umgebungsdatei gespeichert



## Häufige Fehler

### Ungültiges Token

Dies tritt auf, wenn die `private_key` in Ihrer Umgebungsdatei fehlerhaft oder nicht mehr gültig ist. Wenn diese Option angezeigt wird, stellen Sie sicher, dass Sie den gesamten Schlüssel einschließlich der Zeilenumbrüche kopiert haben

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
