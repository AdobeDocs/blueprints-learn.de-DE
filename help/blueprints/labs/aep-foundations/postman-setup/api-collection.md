---
title: API-Sammlung
description: Laden Sie die Postman-API-Sammlung von Bootcamp herunter und importieren Sie sie, die die in den AEP Foundations-Labs verwendeten Anfragen enthält.
doc-type: article
solution: Experience Platform
exl-id: 18d820c5-56ad-46b8-a9cf-f725555d2db3
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---

# API-Sammlung

## Postman-API-Sammlungsdatei

Datei herunterladen - [AEP Foundations Bootcamp (Labs).postman_collection.json](assets/aep-foundations-bootcamp-labs.postman_collection.json)



## API-Sammlung importieren

1. Öffnen Sie die `Postman API Collection File` von oben in Ihrem Browser, indem Sie auf die Datei klicken
1. URL der Datei in die Zwischenablage kopieren
1. Starten Sie Postman auf Ihrem lokalen Computer und klicken Sie in Ihrem Arbeitsbereich auf die Schaltfläche `Import` .
1. Fügen Sie die URL der `Postman API Collection File` in das Textfeld „Modal importieren“ ein. Dadurch wird ein automatischer Import Trigger

![Klicken Sie im Postman-Arbeitsbereich auf die Schaltfläche „Importieren“, um die API-Sammlung/](assets/api-collection-click-import-button.png " zu importieren")



![Einfügen der URL der API-Sammlungsdatei in das Textfeld „Modal importieren“ von Postman &#x200B;](assets/api-collection-import-modal-paste-url.png "modales Textfeld „Schaltfläche importieren“")

Jetzt wird in der linken Seitenleiste auf der Registerkarte &quot;`Collections`&quot; eine Sammlung namens &quot;`AEP Foundations Bootcamp`&quot; angezeigt



![Bootcamp-Sammlung zu AEP Foundations, die auf der Registerkarte „Seitenleiste“ der Postman-Sammlungen ausgefüllt ist](assets/api-collection-imported-collection-in-sidebar.png)

## Übersicht über die Bootcamp-Sammlung in AEP Foundations

Die von Ihnen importierte API-Sammlung enthält alle erforderlichen API-Aufrufe, die Sie für Labs im gesamten Bootcamp benötigen.  Jedes Labor ist in einen bestimmten Ordner mit eigenen APIs unterteilt.  Beachten Sie diese Ordnerstruktur, wenn Sie diese Woche Labs abschließen.

Details zu den einzelnen Ordnern finden Sie unten:

- **IMS Authenticate** - enthält eine einzelne Anfrage zum Generieren eines Zugriffs-Tokens, das beim Arbeiten mit einer der Adobe Experience Platform-APIs erforderlich ist
- **XDM Schema Lab** - enthält eine Reihe von Anfragen zum Erstellen der XDM-Komponenten, die zum Erstellen und Konfigurieren eines Schemas für das Echtzeit-Kundenprofil erforderlich sind
- **Datenaufnahme-Lab** - enthält eine Reihe von Anfragen für das Streaming von Daten an Experience Platform
- **Profil-Lab** - Enthält eine Reihe von Anfragen zum Anzeigen der Eigenschaften und Verhaltensweisen des Echtzeit-Kundenprofils

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie haben die Postman-Sammlung des Bootcamps erfolgreich importiert
