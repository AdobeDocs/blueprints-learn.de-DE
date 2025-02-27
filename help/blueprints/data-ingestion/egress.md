---
title: 'Blueprint: Datenzugriff und Datenexport'
description: Erfahren Sie, mit welchen Methoden der Zugriff auf und der Export von Daten aus Adobe Experience Platform und Programmen möglich ist.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-Time Customer Data Platform, Data Collection
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 90%

---

# Blueprint für Datenzugriff und -export

Der Datenzugriffs- und Exportierungs-Blueprint umreißt alle möglichen Methoden, mit denen Daten von [!DNL Experience Platform] und Programmen aufgerufen oder exportiert werden können.

Der Blueprint ist für den Datenzugriff von [!DNL Experience Platform] und Programmen in zwei Kategorien unterteilt.

Die erste umfasst Ansätze für die Ausgabe von Daten aus [!DNL Experience Platform] und Programmen. Dies würde als Methode vom _Push_-Typ des Datenausgangs betrachtet.

Das zweite umfasst Ansätze für den Zugriff auf Daten aus [!DNL Experience Platform] und Programmen. Dies wäre eine _-_-Methode für den Datenzugriff.

Ansätze für den Datenzugriff:

* [Real-Time Customer Profile Access API](#rtcp-profile-access-api)
* [Data Access API](#data-access-api)
* [Abfrage-Service](#query-service)

Methoden für den Datenexport:

* [Client-seitige Tags](#client-side-tags-extensions)
* [Ereignisweiterleitung](#event-forwarding)
* [Ziele für Real-time Customer Data Platform](#RTCDP-destinations)
* [Benutzerdefinierte Journey Optimizer-Aktionen](#jo-custom-actions)

## Architektur für Datenzugriff und Exportübersicht

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Referenzarchitektur für die Blueprint „Datenvorbereitung und -aufnahme“" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## Datenzugriffs- und Exportmethoden

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1133px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1133px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Streaming-Ziele</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Methode</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Häufige Anwendungsfälle</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protokolle</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Allgemeine Überlegungen</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de" style="color:#0563c1; text-decoration:underline">Ereignisweiterleitung</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Weiterleitung von über Adobe SDKs erfassten Rohdaten zur Analyse und Erfassung in Unternehmenssystemen</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geringfügiges Tagging für die Erfassung von Third-Party-Daten<sup></sup> über Erweiterungen</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Rohereignisse auf niedriger Ebene</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Keine Hinzufügung von Aggregation oder vorherigem Datensatzkontext</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=de#:~:text=containing%20profile%20exports.-,Streaming%20segment%20export%20destinations,-Segment%20export%20destinations" style="color:#0563c1; text-decoration:underline">RTCDP – Exporte von Streaming-Segmenten</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aktivierung von Zielgruppen über RTCDP für Marketing und Werbung, Systeme etc.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aggregierte Daten repräsentieren Zielgruppenzugehörigkeit</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Keine Aktivierung der Rohdaten von Erlebnisereignissen</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=de#:~:text=file%2Dbased)%20destinations-,Streaming%20profile%20export%20destinations%20(enterprise%20destinations),-IMPORTANT" style="color:#0563c1; text-decoration:underline">RTCDP – Profilexport-Ziele</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Nutzung von umfassenden Verhaltensprofilen und Zielgruppen von RTCDP, um Kundenerlebnisse und das Marketing zu verbessern.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aktivierung von Zielgruppen und Profilattributen über RTCDP für Marketing und Werbung sowie Systeme, die mit Zielgruppen und Profilattributen arbeiten. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aktivierung von AEP-Profilen für E-Mail-Dienstanbieter, Lead-Nurturing- und CRM-Systeme.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aggregierte Daten repräsentieren die Zielgruppenzugehörigkeit und Profil-Datensatzattribute</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Keine Aktivierung der Rohdaten von Erlebnisereignissen</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=de" style="color:#0563c1; text-decoration:underline">RTCDP – Personalisierungsziele</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Zugriff auf das Echtzeit-Kundenprofil für Browser- und Client-seitige Erlebnisse, um die kundenseitige Personalisierung zu verbessern. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Erfordert die Bereitstellung des WebSDK</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-sdk/overview.html?lang=de" style="color:#0563c1; text-decoration:underline">RTCDP – Destination SDK</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Konfigurieren einer benutzerdefinierten Zielkarte in den RTCDP-Zielen.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Unterstützt Datei- und Streaming-Ziele</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Ermöglicht Partnern und Marken die Konfiguration benutzerdefinierter Zielkarten</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=de" style="color:#0563c1; text-decoration:underline">RTCDP – Profile Lookup Hub API</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Zugriff auf Profile zur Verbesserung von Erlebnissen im Kundenservice wie z. B. bei Interaktionen mit dem Support oder dem Vertrieb.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Hub-Lookup nur ideal für Anwendungsfälle mit über 500 ms</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">RTCDP - Edge-API zur Profilsuche</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Zugriff auf Profile im Edge Network, um Kundenerlebnisse für Echtzeit-Erlebnisse mit weniger als 200 ms zu verbessern, z. B. für Personalisierung oder Angebotsentscheidungen im Web und auf Mobilgeräten.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Für Echtzeit-Erlebnisse und Server-zu-Server-Integrationen</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=de" style="color:#0563c1; text-decoration:underline">Benutzerdefinierte Journey Optimizer-Aktionen</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aktivierung von 1:1-Journey-Ereignissen und von Triggern zur Benachrichtigung eines externen Systems. Warenkorbabbrüche, Anmeldungsabbrüche, Registrierungen.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Aktivierung eines einzelnen Ereignisses für ein bestimmtes Profil. Nicht für Aggregations- oder Massenvorgänge</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>

<p> </p>

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1132px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1132px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Batch-Ziele</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Methode</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Häufige Anwendungsfälle</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protokolle</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Allgemeine Überlegungen</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/data-access/api.html?lang=de" style="color:#0563c1; text-decoration:underline">Data Access API</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Zugriff auf Rohdaten für Datenwissenschafts- und ML-Workflows außerhalb von Experience Platform.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Parquet-Dateien</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Erfordert Entwicklungsprozesse, um auf Parquet-Dateien zugreifen und aus ihnen nutzbare Datensätze machen zu können</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=de" style="color:#0563c1; text-decoration:underline">Abfrage-Service</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Beibehalten von Abfrageergebnissen aus Datensätzen für aggregierte Einblicke und Berichte. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Pull</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">PostgreSQL </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">SQL Client</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Nur aggregierte Daten. Abfragelimit von 10 Minuten.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/export-datasets.html?lang=de" style="color:#0563c1; text-decoration:underline">Datensatzexport</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Exportieren von Experience Platform-Ereignisdaten für den Zugriff in externen Reporting-, Analyse- und Data-Science-Tools. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Export von aggregierten Profileinblicken und Zielgruppenzugehörigkeit für externe Reporting-, Analyse- und Data-Science-Tools. </span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST-API </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Untergruppen von Datensätzen werden unterstützt, wie in der Produktdokumentation beschrieben.</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>



## Methoden für den Datenzugriff

### Real-Time Customer Profile Access API {#rtcp-profile-access-api}

Kunden können über die Real-Time Customer Profile Access API auf einzelne einheitliche Profile im Echtzeit-Kundenprofil-Datenspeicher zugreifen, einschließlich aller Profilidentitäten, Zielgruppen-Zugehörigkeiten, Attribute und Erlebnisereignisse.

Weitere Informationen finden Sie in der Dokumentation zur [Real-Time Customer Profile Access API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=de).

#### Anwendungsfälle

* Suche nach einem einzelnen Profil, um Kontext zur Kundeninteraktion mit dem Kundenservice hinzuzufügen, z. B. zu einer Support-Anfrage über das Chat- und Callcenter oder einem Einkauf im Geschäft.
* Hinzufügen von zusätzlichem Kontext zu einer von einem externen System durchgeführten Personalisierungsentscheidung, z. B. einem Web-Personalisierungssystem oder einem Angebotsentscheidungssystem.

#### Allgemeine Überlegungen

* Es gelten die [Leitlinien](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de) zum Echtzeit-Kundenprofil.
* Geeignet für die Suche nach einem einzelnen Profil. Nicht geeignet für den Massenzugriff auf oder -Download der gesamten Profilpopulation für die Analyse oder datenwissenschaftliche Zwecke.
* Die Antwortzeit bei der Profilsuche hängt von den Profilleitlinien ab. Anforderungen für geringe Latenz in Echtzeit – z. B. sollten Anforderungen für Personalisierung auf derselben Seite das Edge-Profil für die [Adobe Target-Verbindung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=de) oder die [Verbindung für benutzerdefinierte Personalisierung](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=de) nutzen, um in Browser und Mobile App in Echtzeit auf das Profil zuzugreifen.

### Data Access API {#data-access-api}

Mit der Data Access API können Kunden direkt auf die Rohdatensatzdateien im Data Lake von Experience Platform zugreifen.

* Weitere Informationen zur Verwendung der Data Access API finden Sie in der [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=de).

#### Anwendungsfälle

* Abrufen von Dateien mit Rohdaten und verarbeiteten Daten aus Experience Platform, um sie in Unternehmensumgebungen zu speichern und auszuwerten.

#### Allgemeine Überlegungen

* Da der Datenzugriff asynchron im Batch-Modus erfolgt, ist der Zugriff auf die Daten im Vergleich zu Streaming-Datenausgabe-Methoden, wie der Verwendung von Tags, der Ereignisweiterleitung oder RTCDP-Zielen, von Natur aus latent.
* Datendateien werden bei der Verarbeitung in Experience Platform als Dateisammlungen in Batches abgelegt und im Parquet-Format komprimiert und gespeichert. Daher erfordert der Zugriff und Download von Daten in eine andere Umgebung einen systematischen Zugriff nach Batch und Datei im Gegensatz zu einem ganzen Datensatz, und bei allen Datenvorgängen muss die Komprimierung im Parquet-Format berücksichtigt werden.

### Abfrage-Service {#query-service}

Mithilfe des Abfrage-Service von Experience Platform können Kunden Datensätze in Experience Platform abfragen und die Ergebnisse der Abfrage speichern. Ein SQL-Client kann für die Abfrage und die Speicherung der Abfrageantwort im gewünschten, vom SQL-Client unterstützten Speicherziel verwendet werden. Die Benutzeroberfläche des Abfrage-Service kann verwendet werden, um das SQL-Ergebnis in einem Zieldatensatz in Experience Platform oder auf einem lokalen Rechner zu speichern.

* Weitere Informationen zur Verbindung mit SQL-Clients zum Speichern von SQL-Ergebnissen über den Experience Platform-Abfrage-Service finden Sie in der folgenden [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=de).

#### Anwendungsfälle

* Abfrage von Rohdaten aus Experience Platform-Datensätzen und Speicherung der Abfrageergebnisse.
* Abfrage des Profil-Snapshot-Datensatzes, um Erkenntnisse zum Echtzeit-Kundenprofil zu erhalten. [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=de#profile-attribute-datasets).
* Speichern von Abfrageergebnissen in einem separaten Datensatz, um später darauf zuzugreifen, oder in einem profilaktivierten Datensatz, der später über RTCDP und andere Experience Cloud-Anwendungen, die auf das Echtzeit-Kundenprofil zugreifen können, abgerufen werden kann.

#### Allgemeine Überlegungen

* Da die Datenabfrage asynchronen im Batch-Modus erfolgt, ist der Zugriff auf die Daten im Vergleich zu Streaming-Datenausgabemethoden, wie der Verwendung von Tags, der Ereignisweiterleitung oder RTCDP-Zielen, von Natur aus latent.
* Mit dem Abfrage-Service können nur Daten abgefragt werden, die im Data Lake von Experience Platform verfügbar sind. Der Echtzeit-Kundenprofil-Speicher, das Identitätsdiagramm und Customer Journey Analytics können nicht direkt mit dem Abfrage-Service abgefragt werden. Nur wenn Datensätze in den Data Lake exportiert werden, können diese Datensätze abgefragt werden, wie beim Beispiel des Profil-Snapshot-Datensatzes.
* Beachten Sie, dass für Abfragen Limits für die Anzahl der Abfrageergebnisse und eine maximale Wartezeit gelten. Diese werden in der Dokumentation zu den [Leitlinien für Abfrage-Services](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de) beschrieben.

## Methoden für den Datenexport

### Client-seitige Tag-Erweiterungen {#client-side-tags-extensions}

Erweiterungen können mit der Tags-Lösung von Adobe bereitgestellt werden. Nach der Implementierung einer Erweiterung werden Datenanfragen direkt in einem Client-Browser oder einer Anwendung durchgeführt. Mit einer Anfrage können Daten und Anfragen an das gewünschte Ziel gesendet werden.

Weitere Informationen finden Sie in der Dokumentation zur [Übersicht über Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=de).

#### Anwendungsfälle

* Erfassen von Roh-Streaming-Informationen direkt in Client-seitigen Umgebungen mithilfe von Tags.

#### Allgemeine Überlegungen

* Es besteht kein direkter Zugriff auf Server-seitige Informationen wie das Echtzeit-Kundenprofil von Experience Platform und die Zielgruppen-Zugehörigkeit.
* Durch das Hinzufügen zusätzlicher Datenerfassungs-Tags zur Seite können sich die Seitenladezeiten verlangsamen.
* Möglichkeit, Regeln einzurichten, um nur Daten anfordern, wenn bestimmte Kriterien erfüllt sind.
* Daten werden direkt beim Client erfasst, wodurch die Arten der Umwandlungen und Anreicherungen begrenzt werden, die vor der Datenerfassung durchgeführt werden können.

### Ereignisweiterleitung {#event-forwarding}

Datenerfassungsanfragen werden direkt an die Adobe-[!DNL Edge Network] erfasst. Von den [!DNL Edge Network] an externe RESTful-Endpunkte können Sie so konfiguriert werden, dass diese Anfragen an das externe Ziel weitergeleitet werden.

Weitere Informationen finden Sie in der folgenden Dokumentation zur [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de).

#### Anwendungsfälle

* Erfassen von Roh-Streaming-Daten direkt in Client-seitigen Umgebungen und Weiterleitung an einen Unternehmens-Endpunkt mithilfe der Server-seitigen Ereignisweiterleitung von Adobe.

#### Allgemeine Überlegungen

* Um die Ereignisweiterleitung zu verwenden, müssen Daten mithilfe von Web SDK oder Mobile SDK an den [!DNL Edge Network] gesendet werden.
* Durch die Ereignisweiterleitung werden die Seitenladezeit und -last reduziert, da zusätzliche Tags zur Seite hinzugefügt werden.
* Derzeit wird keine Anreicherung über das Edge-Profil oder andere Datenquellen unterstützt.
* Eingeschränkte Datenfilterung und einfache Mapping-Umwandlungen werden unterstützt.

### Ziele für Real-time Customer Data Platform {#RTCDP-destinations}

Profilattributdaten und Zielgruppen-Zugehörigkeitsdaten können für Unternehmens- und Werbeziele aktiviert werden. Das bedeutet, dass die exportierten Daten in das Echtzeit-Kundenprofil von Experience Platform aufgenommen werden müssen.

Weitere Informationen finden Sie in der Dokumentation zu [Real-time Customer Data Platform-Zielen](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=de).

#### Anwendungsfälle

* Aktivierung von Profilattribut-Informationen, einschließlich der Zielgruppen-Zugehörigkeit für interne Unternehmensdatenspeicher, Analyse-Tools, E-Mail-Systeme oder Support-Systeme.
* Aktivierung der Profil-Zielgruppen-Zugehörigkeit für einen externen Werbeanbieter, um Inhalte auf das Profil auszurichten und zu personalisieren.

#### Allgemeine Überlegungen

* Profilattribute und Zielgruppen-Zugehörigkeiten können aktiviert werden. Roh-Erlebnisereignisse können derzeit nicht als Teil von RTCDP-Zielen aktiviert werden.
* Aktivierungen erfolgen im Streaming- oder Batch-Modus, abhängig von der Art der Segmentauswertung und vom Typ des Aufnahmeprotokolls, das vom Ziel akzeptiert wird.

### Benutzerdefinierte Journey Optimizer-Aktionen {#jo-custom-actions}

Mit Journey Optimizer können Kunden eine benutzerdefinierte Aktion über die Journey-Arbeitsfläche ausführen, um eine Payload oder Nachricht an einen konfigurierten externen API-Endpunkt zu senden. Eine Aktion kann für jeden beliebigen Service eines jeden beliebigen Anbieters konfiguriert werden, der über eine REST-API mit einer JSON-formatierten Payload aufgerufen werden kann. Diese Payload kann Ereignisinformationen, Profilattribute und frühere Ereignisdaten, Umwandlungen und Anreicherungen enthalten, die in der Journey konfiguriert sind.

Weitere Informationen finden Sie in der Dokumentation zu [benutzerdefinierten Journey Optimizer-Aktionen](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=de).

#### Anwendungsfälle

* Aktivierungsereignisse in Experience Platform und Journey Optimizer, die zusätzliche Informationen vom Echtzeit-Kundenprofil enthalten.
* Benachrichtigung externer Systeme, wenn ein Kunde einen bestimmten Punkt einer Journey erreicht hat.

#### Allgemeine Überlegungen

* Es gelten Limits bezüglich des von [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=de) unterstützten Durchsatzes und der vom [Echtzeit-Kundenprofil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de) unterstützten Anreicherungen.
* Benutzerdefinierte Aktionen können für jedes Ereignis oder Profil in einer Journey per Streaming nacheinander ausgeführt werden. Vorgänge oder Datenexporte im Bulk-Modus in Form von Dateien oder aggregierten Anfragen in Customer Journeys können nicht ausgeführt werden.
* Es besteht Streaming-Zugriff auf Echtzeit-Kundenprofil-Attribute und Erlebnisereignisse, die in die Aktivierungs-Payload integriert werden können.
* Ereignisdaten können gefiltert und einfache Mapping-Umwandlungen können angewendet werden, bevor Ereignisse an externe Ziele gesendet werden.
