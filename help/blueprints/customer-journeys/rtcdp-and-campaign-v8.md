---
title: Integrationsmuster von Real-Time CDP mit Adobe Campaign v8
description: Zeigt, wie Adobe Experience Platform und das Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign v8 genutzt werden können, um personalisierte Konversationen bereitzustellen
solution: Real-time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 85%

---

# Integrationsmuster von Real-Time CDP mit Adobe Campaign v8

Zeigt, wie Adobe Experience Platform und das Echtzeit-Kundenprofil sowie das zentralisierte Segmentierungs-Tool mit Adobe Campaign genutzt werden können, um personalisierte Konversationen bereitzustellen

<br>

## Programme

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## Architektur

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Referenzarchitektur für das Integrationsmuster Batch Messaging und Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Voraussetzungen

* Der Kunde muss über eine gültige IMS Org für Experience Cloud verfügen
* Es wird empfohlen, bei Verwendung einer einzigen Anmelde-URL Adobe Experience Platform und Campaign in derselben IMS-Organisation bereitzustellen
* Der Kunde muss über die v8-Instanz von Campaign verfügen
* Der Kunde muss über eine Berechtigung und den Zugriff auf die Quellen und Ziele von Real-time Customer Data Platform verfügen.
* Adobe Campaign-Produktkontext muss vorhanden sein

<br>

## Implementierungsschritte

Weitere Informationen zum Konfigurieren des Quell-Connectors von Campaign v8 für Adobe Experience Platform und des Ziel-Connectors von Real-time Customer Data Platform für Campaign v8 finden Sie in der folgenden Dokumentation.
[Campaign- und AEP-Connectoren](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=de)

## Leitlinien

### Adobe Campaign

* Weitere Informationen finden Sie in der Dokumentation zum Quell-Connector von Campaign – [Campaign-Quell-Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=de)
* Unterstützt nur die Bereitstellung einzelner Organisationseinheiten von Adobe Campaign
* Adobe Campaign ist die zentrale Datenquelle für alle aktiven Profile. Das heißt, die Profile müssen in Adobe Campaign vorhanden sein und neue Profile dürfen nicht basierend auf Experience Platform-Segmenten erstellt werden.


### Segmentfreigabe in Experience Platform Real-time Customer Data Platform

* Siehe den Ziel-Connector von Real-time Customer Data Platform für Campaign – [Verbindung von Real-time Customer Data Platform mit Campaign](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=de)
* Begrenzung auf 50 Segmente empfohlen
* Beachten Sie, dass die Bestimmung der Segmentzugehörigkeit in AEP sowohl für Batch-Vorgänge (1 pro Tag) als auch für Streaming (~5 Minuten) verzögert ist und auf dem Segmentevaluierungs-Zeitplan basiert.
* Die Aktivierungslatenz beträgt mindestens 3 Stunden
* Nur Vereinigungsschema-Attribute sind für die Aktivierung verfügbar (keine Unterstützung von Array/Karten/Erlebnisereignisse)
* Begrenzung auf 20 Attribute pro Segment empfohlen
* Eine Datei pro Segment aller Profile mit &quot;realisierter&quot;Segmentzugehörigkeit ODER wenn die Segmentzugehörigkeit als Attribut in der Datei sowohl &quot;realisierte&quot;als auch &quot;ausgehende&quot;Profile hinzugefügt wird
* Schrittweise und vollständige Segment-Exporte werden unterstützt
* Datei-Verschlüsselung wird nicht unterstützt
* Siehe Leitlinien für die Profil- und Datenaufnahme für AEP – [Link](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
