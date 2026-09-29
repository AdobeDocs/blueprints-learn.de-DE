---
title: Verwenden der Data Landing Zone
description: Installieren und konfigurieren Sie Azure Storage Explorer mit einer SAS-URL, um eine Verbindung zur Adobe Experience Platform Data Landing Zone herzustellen.
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%
---

# Verwenden der Data Landing Zone

## Voraussetzungen

Wenn Sie Azure Storage Explorer nicht heruntergeladen haben, tun Sie dies jetzt, da dies für dieses Labor erforderlich ist.  Den Download finden Sie unter folgendem Link:

[Herunterladen von Azure Storage Explorer](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. Installieren des Programms
1. Akzeptieren Sie beim ersten Öffnen der Anwendung die Endbenutzer-Lizenzvereinbarung

![Bildschirm mit der Endbenutzer-Lizenzvereinbarung im Azure Storage Explorer](assets/overview-end-user-license-agreement-screen.png " Bildschirm mit der Endbenutzer-Lizenzvereinbarung")


## Konfigurieren von Azure Storage Explorer mit Experience Platform

1. Öffnen Sie Azure Storage Explorer, klicken Sie auf das Symbol **Ressource auswählen** und wählen Sie dann **ADLS Gen2-Container oder -Verzeichnis**

   ![Auswählen des ADLS Gen2-Containers oder -Verzeichnisses als Ressource im Azure Storage Explorer](assets/overview-choose-the-resource-as-shown-above.png)



1. Wählen Sie **Shared Access Signature URL (SAS)** und klicken Sie auf **Weiter**

   ![Auswählen der SAS-URL-Option als Verbindungsmodus](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "Wählen Sie die SAS-URL-Option als Verbindungsmodus")



1. Geben Sie den Anzeigenamen als **Data Landing Zone“**

   >[!NOTE]
   >
   >Sie können mit diesem Schritt nicht fortfahren, bis Sie die SAS-URL angeben.  Sie erhalten dies von der Experience Platform, die Sie im nächsten Schritt sehen.

   ![Benennen der Verbindung Data Landing Zone](assets/overview-name-the-connection.png "Benennen Sie die Verbindung")



1. Gehen Sie zu Adobe Experience Platform und navigieren Sie wie folgt zur Data Landing Zone:

   - Navigieren Sie zu **Quellen -> Katalog**
   - Wählen Sie **Cloud-Speicher** unter den Quellen aus.
   - Suchen Sie als Nächstes die Karte **Data Landing Zone** .
   - Klicken Sie auf die Karte Data Landing Zone und dann auf **Anmeldedaten anzeigen** in der rechten Leiste

   ![Quellkarte der Data Landing Zone mit der Option Anmeldedaten anzeigen in der Source-Karte der &#x200B;](assets/overview-data-landing-zone-view-credentials.png " Data Landing Zone von Adobe Experience PlatformAccess in Adobe Experience Platform")



1. Kopieren Sie den **SASUri** aus dem modalen Fenster, das angezeigt wird.

   Navigieren Sie zurück zum Azure-Speicher-Explorer und fügen Sie den **SASUri-Wert** in den **Blob-Container oder Verzeichnis-SAS-URL** ein, den Sie im vorherigen Schritt leer gelassen haben

   ![Kopieren des SASUri-Werts aus Experience Platform in Azure Storage Explorer](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "Kopieren Sie die SAS-URL-Anmeldeinformationen aus Adobe Experience Platform und kopieren Sie sie in Azure Storage Explorer")



1. Klicken Sie **Weiter** um fortzufahren

   ![Kopieren von SAS-URL-Anmeldeinformationen in den SAS-URL-Abschnitt der Verbindungsinformationen](assets/overview-copy-sas-url-into-connection-info.png " Kopieren Sie SAS-URL-Anmeldeinformationen in den SAS-URL-Abschnitt in den Verbindungsinformationen")



1. Klicken Sie im Bildschirm Zusammenfassung auf **Verbinden**

![Zusammenfassungsbildschirm mit Schaltfläche „Verbinden](assets/overview-connect-screen.png "Bildschirm „Verbinden“")



Jetzt sollte ein Bildschirm angezeigt werden, der wie folgt aussieht

![Azure Storage Explorer zeigt das erfolgreich verbundene Data Landing Zone-Konto an](assets/overview-successfully-connected-account.png)

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie haben Azure Storage Explorer erfolgreich konfiguriert
