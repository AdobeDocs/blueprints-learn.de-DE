---
title: Blueprint für den Datenzugriff und Datenexport
description: Diese Blueprint bietet einen Überblick über alle Methoden, mit denen Daten aus Adobe Experience Platform und den zugehörigen Anwendungen abgerufen und exportiert werden können.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: c0fe0e94e30351f593e32ea0e6809dd832f976ad
workflow-type: ht
source-wordcount: '1513'
ht-degree: 100%

---

# Blueprint für den Datenzugriff und Datenexport

Im Blueprint für den Datenzugriff und Datenexport werden alle möglichen Methoden beschrieben, mit denen Daten aus Adobe Experience Platform und den zugehörigen Anwendungen abgerufen oder exportiert werden können.

Die Blueprint beinhaltet zwei Arten von Datenzugriff über Experience Platform und die zugehörigen Anwendungen. Einerseits werden Methoden zum Export von Daten aus Experience Platform und den zugehörigen Anwendungen beschrieben. Hierbei wird eine Push-Methode verwendet. Andererseits werden Methoden für den Zugriff auf Daten in Experience Platform und den zugehörigen Anwendungen beschrieben. Hierzu wird eine Pull-Methode verwendet.

Methoden für den Datenzugriff

* [Real-time Customer Profile Access API](#rtcp-profile-access-api)
* [Data Access API](#data-access-api)
* [Abfrage-Service](#query-service)

Methoden für den Datenexport

* [Client-seitige Tags](#client-side-tags-extensions)
* [Ereignisweiterleitung](#event-forwarding)
* [Real-time Customer Data Platform-Ziele](#RTCDP-destinations)
* [Benutzerdefinierte Journey Optimizer-Aktionen](#jo-custom-actions)

## Architektur für den Datenzugriff und Datenexport im Überblick

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Referenzarchitektur für die Blueprint „Datenvorbereitung und -aufnahme“" style="width:90%; border:1px solid #4a4a4a" />

## Methoden für den Datenzugriff

### Real-time Customer Profile Access API {#rtcp-profile-access-api}

Kunden können über die Real-time Customer Profile Access API auf einzelne einheitliche Profile im Echtzeit-Kundenprofil-Datenspeicher zugreifen, einschließlich aller Profilidentitäten, Zielgruppen-Zugehörigkeiten, Attribute und Erlebnisereignisse.

Weitere Informationen finden Sie in der Dokumentation zur [Real-time Customer Profile Access API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=de).

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
* Abfrage des Profil-Snapshot-Datensatzes, um Insights zum Echtzeit-Kundenprofil zu erhalten. [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=de#profile-attribute-datasets).
* Speichern von Abfrageergebnissen in einem separaten Datensatz, um später darauf zuzugreifen, oder in einem profilaktivierten Datensatz, der später über RTCDP und andere Experience Cloud-Anwendungen, die auf das Echtzeit-Kundenprofil zugreifen können, abgerufen werden kann.

#### Allgemeine Überlegungen

* Da die Datenabfrage asynchronen im Batch-Modus erfolgt, ist der Zugriff auf die Daten im Vergleich zu Streaming-Datenausgabemethoden, wie der Verwendung von Tags, der Ereignisweiterleitung oder RTCDP-Zielen, von Natur aus latent.
* Mit dem Abfrage-Service können nur Daten abgefragt werden, die im Data Lake von Experience Platform verfügbar sind. Der Echtzeit-Kundenprofil-Speicher, das Identitätsdiagramm und Customer Journey Analytics können nicht direkt mit dem Abfrage-Service abgefragt werden. Nur wenn Datensätze in den Data Lake exportiert werden, können diese Datensätze abgefragt werden, wie beim Beispiel des Profil-Snapshot-Datensatzes.
* Beachten Sie, dass für Abfragen Limits für die Anzahl der Abfrageergebnisse und eine maximale Wartezeit gelten. Diese werden in der Dokumentation zu den [Leitlinien für Abfrage-Services](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=de) beschrieben.

## Methoden für den Datenexport

### Client-seitige Tags-Erweiterungen {#client-side-tags-extensions}

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

Datenerfassungsanfragen werden direkt im Edge Network von Adobe erfasst. Im Edge Network können Anfragen an externe RESTful-Endpunkte konfiguriert werden, sodass diese Anfragen an das externe Ziel weitergeleitet werden.

Weitere Informationen finden Sie in der folgenden Dokumentation zur [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=de).

#### Anwendungsfälle

* Erfassen von Roh-Streaming-Daten direkt in Client-seitigen Umgebungen und Weiterleitung an einen Unternehmens-Endpunkt mithilfe der Server-seitigen Ereignisweiterleitung von Adobe.

#### Allgemeine Überlegungen

* Um die Ereignisweiterleitung zu verwenden, müssen die Daten mithilfe des WebSDK oder MobileSDK an das Edge Network gesendet werden.
* Durch die Ereignisweiterleitung werden die Seitenladezeit und -last reduziert, da zusätzliche Tags zur Seite hinzugefügt werden.
* Derzeit wird keine Anreicherung über das Edge-Profil oder andere Datenquellen unterstützt.
* Eingeschränkte Datenfilterung und einfache Mapping-Umwandlungen werden unterstützt.

### Real-time Customer Data Platform-Ziele {#RTCDP-destinations}

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
