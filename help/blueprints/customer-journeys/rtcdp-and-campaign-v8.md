---
title: Integrationsmuster von Real-Time CDP mit Adobe Campaign v8
description: zeigt, wie die Adobe Experience Platform und ihr Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign v8 für personalisierte Konversationen genutzt werden können.
solution: Real-time Customer Data Platform, Campaign
source-git-commit: f8116387105cf1fe0adfc148562529d62ca90cfc
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 45%

---

# Integrationsmuster von Real-Time CDP mit Adobe Campaign v8

Zeigt, wie Adobe Experience Platform und das Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign genutzt werden können, um personalisierte Konversationen bereitzustellen

<br>

## Programme

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## Architektur

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Referenzarchitektur für das Integrationsmuster für Batch-Messaging und Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

* Der Kunde muss über eine gültige IMS Org für Experience Cloud verfügen
* Es wird empfohlen, Adobe Experience Platform und Campaign in derselben IMS-Organisation für die einmalige Anmelde-URL bereitzustellen
* Der Kunde muss über die V8-Instanz von Campaign verfügen
* Der Kunde muss berechtigt sein und Zugriff auf RTCDP, Quellen, Ziele haben.
* Adobe Campaign-Produktkontext muss vorhanden sein

<br>

## Implementierungsschritte

Weitere Informationen zum Konfigurieren des Quell-Connectors für Campaign v8 mit Adobe Experience Platform und zum Real-time Customer Data Platform-Ziel-Connector mit Campaign v8 finden Sie in der folgenden Dokumentation.
[Campaign und AEP Connectors](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## Leitlinien

### Adobe Campaign

* Weitere Informationen finden Sie in der Dokumentation zum Quell-Connector von Campaign - [Campaign Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* Unterstützt nur die Bereitstellung einzelner Organisationseinheiten von Adobe Campaign
* Adobe Campaign ist die zentrale Datenquelle für alle aktiven Profile. Das heißt, die Profile müssen in Adobe Campaign vorhanden sein und neue Profile dürfen nicht basierend auf Experience Platform-Segmenten erstellt werden.


### Segmentfreigabe in Experience Platform Real-time Customer Data Platform

* Siehe Zielanschluss der RTCDP-Kampagne - [RTCDP-Kampagnenverbindung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)
* Begrenzung auf 50 Segmente empfohlen
* Beachten Sie, dass die Realisierung der Segmentzugehörigkeit von AEP sowohl für Batch (1 pro Tag) als auch für Streaming (~5 Minuten) latent ist und auf dem Zeitplan für die Segmentbewertung basiert.
* Die Aktivierungslatenz beträgt mindestens 3 Stunden
* Nur Vereinigungsschema-Attribute sind für die Aktivierung verfügbar (keine Unterstützung von Array/Karten/Erlebnisereignisse)
* Begrenzung auf 20 Attribute pro Segment empfohlen
* Eine Datei pro Segment von allen Profilen mit „realisierter“ Segmentzugehörigkeit ODER, wenn Segmentzugehörigkeit als Attribut in der Datei hinzugefügt wird, sowohl „realisierte“ als auch „verlassene“ Profile
* Schrittweise und vollständige Segment-Exporte werden unterstützt
* Datei-Verschlüsselung wird nicht unterstützt
* Siehe Limits für die Profil- und Datenerfassung für AEP - [Link](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)