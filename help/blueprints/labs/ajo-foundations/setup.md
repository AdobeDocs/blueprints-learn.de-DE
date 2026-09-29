---
title: Einrichtung
description: Führen Sie die erforderlichen Konfigurationsschritte für die Sandbox-Bereitstellung und die Postman aus, bevor Sie AJO Foundations Labs starten.
doc-type: article
solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 1%
---

# Einrichtung

Bevor Sie die AJO Foundations-Labs starten, führen Sie die folgenden Einrichtungsschritte aus. Welche Schritte Sie benötigen, hängt davon ab, wie Sie dieses Bootcamp nehmen.

## Sandbox-Setup

>[!NOTE]
>
>Wenn Sie an einem Live-Schulungskurs oder einer Live-Veranstaltung teilnehmen, wurde Ihre Sandbox bereits für Sie bereitgestellt. Überspringen Sie diesen Abschnitt und navigieren Sie direkt zur Postman-Einrichtung unten.

Wenn Sie noch keine funktionierende Sandbox mit den bereitgestellten Lab-Assets haben, führen Sie die folgenden Schritte aus:

- [Developer Console-Setup](sandbox-setup/developer-console-setup.md)
- [Bereitstellungsanweisungen](sandbox-setup/deployment-instructions.md)

## Postman-Setup

Für die Labs in diesem Kurs ist Postman erforderlich, unabhängig davon, wie Ihre Sandbox bereitgestellt wurde. Führen Sie vor dem Fortfahren Folgendes aus:

- [Postman-Installation](postman-setup/postman-installation.md)
- [Umgebungsdatei importieren](postman-setup/import-environment-file.md)
- [API-Sammlung importieren](postman-setup/import-api-collection.md)

## On-Demand-Bereitschaft

Bevor Sie die Labs starten, schließen Sie die oben beschriebene Postman-Konfiguration ab. Lernende zum Selbststudium benötigen außerdem eine delegierte Subdomain für die E-Mail-abhängigen Labs und SMS-Anmeldeinformationen für das Startlabor des Flaggschifftelefons.

## Voraussetzungen für den Kanal

Zwei Labs später in diesem Bootcamp hängen von externen Konten ab, die nur Lernende zum Selbststudium arrangieren müssen - wenn Sie sich in einem Live-Schulungskurs oder einer Veranstaltung befinden, sind diese bereits für Sie bereitgestellt.

### Delegierte Subdomain

Für das [Konfigurieren von E](data-stores/configure-email-channels/overview.md)Mail-Kanälen - und alles, was davon abhängt ([Nachrichtenversand in Aktion](orchestrated-campaigns/message-delivery-in-action/overview.md), [Begeisterung nach dem Kauf](journeys/post-purchase-excitement/overview.md) und [AJO Brands](content-authoring-with-ai/overview.md)) - ist eine Subdomain erforderlich, die zum Senden von E-Mails an Adobe delegiert wurde. Wenn Sie noch keine Domain haben, registrieren Sie eine bei einer Domain-Registrierungsstelle (z. B. Namecheap). Um dann eine Subdomain davon (z. B. `email.yourdomain.com`) an Adobe zu delegieren, folgen Sie den Anweisungen [Subdomain-Delegierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain) von Adobe.

>[!NOTE]
>
>Es kann einige Zeit dauern, bis die Subdomain-Zuweisung propagiert wird. Starten Sie diese Delegierung lange, bevor Sie das Labor E-Mail-Kanäle konfigurieren erreichen möchten.

### SMS-Anmeldedaten

Das [Flagship Phone Launch](orchestrated-campaigns/flagship-phone-launch/overview.md) Lab konfiguriert einen SMS-Kanal über Twilio. Es werden keine Nachrichten gesendet, aber Sie benötigen funktionierende Anmeldeinformationen, um die Konfiguration abzuschließen. Die einfachste Option ist ein kostenloses [Twilio-Testkonto](https://www.twilio.com/try-twilio) - siehe Twilio[Erste Schritte-Handbuch](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account), wie Sie sich anmelden und Ihre Konto-SID und Ihr Authentifizierungs-Token finden.
