---
title: Datenzugriffs- und Export-Blueprint
description: Dieser Blueprint bietet einen Überblick über alle Methoden, mit denen Daten aus Adobe Experience Platform und Anwendungen abgerufen und exportiert werden können.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
source-git-commit: 67e66068bb8a2106dd8aa9784b5a39377225c045
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 4%

---

# Datenzugriffs- und Export-Blueprint

Im Blueprint Datenzugriff und -export werden alle möglichen Methoden beschrieben, mit denen Daten aus Adobe Experience Platform und Anwendungen abgerufen oder exportiert werden können.

Das Blueprint ist in zwei Kategorien unterteilt, in denen der Datenzugriff über Experience Platformen und Anwendungen möglich ist. Erstens Konzepte für die Datenauswertung aus Experience Platformen und Anwendungen; Dies würde als eine Methode der Datenausgabe vom Typ Push betrachtet. Zweitens: Ansätze für den Zugriff auf Daten aus Experience Platformen und Anwendungen; dies würde als Methode für den Datenzugriff vom Typ Pull betrachtet.

Datenzugriffsansätze

* [Echtzeit-Kundenprofil-Zugriffs-API](#rtcp-profile-access-api)
* [Data Access API](#data-access-api)
* [Abfrage-Service](#query-service)

Datenexportansätze

* [Client-seitige Tags](#client-side-tags-extensions)
* [Ereignisweiterleitung](#event-forwarding)
* [Real-time Customer Data Platform-Ziele](#RTCDP-destinations)
* [Benutzerdefinierte Journey Optimizer-Aktionen](#jo-custom-actions)

## Architektur mit Datenzugriff und -export - Überblick

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Referenzarchitektur für Blueprint „Datenvorbereitung und -aufnahme“" style="width:90%; border:1px solid #4a4a4a" />

## Ansätze für den Datenzugriff

### Echtzeit-Kundenprofil-Zugriffs-API {#rtcp-profile-access-api}

Kunden können über die Echtzeit-Kundenprofil-API auf einzelne einheitliche Profile zugreifen, einschließlich aller Profilidentitäten, Zielgruppenmitgliedschaften, Attribute und Erlebnisereignisse.

Siehe Abschnitt [Echtzeit-Kundenprofil-Zugriffs-API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) Dokumentation für weitere Informationen.

#### Anwendungsfälle

* Suchen Sie nach einem einzelnen Profil, um der Kundeninteraktion des Agenten Kontext hinzuzufügen, z. B. eine Support-Interaktion über Chat und Callcenter oder eine Verkaufsinteraktion an der Verkaufsstelle.
* Fügen Sie einer Personalisierungsbeschreibung eines externen Systems, z. B. einem Web-Personalisierungssystem oder einem Entscheidungssystem für Angebote, Kontext hinzu.

#### Überlegungen

* Echtzeit-Kundenprofil [Limits](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) gelten.
* Für die Suche nach einzelnen Profilen auf einmal entwickelt. Wird nicht für den Massenzugriff auf Profile oder den Download der gesamten Profilpopulation für die Verwendung von Analyse oder Datenwissenschaft verwendet.
* Die Antwortzeit für die Profilsuche hängt von den Profilsicherungen ab. Geringe Latenzanforderungen - z. B. für dieselben Anforderungen an die Seitenpersonalisierung sollten die Edge-Profil- oder Kundenpersonalisierungsziele für den Zugriff auf Profile mit geringer Latenz nutzen. [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en).

### Data Access API {#data-access-api}

Mit der Data Access API können Kunden direkt auf die Rohdatensatzdateien zugreifen, die im Data Lake der Experience Platform gespeichert sind.

* Weitere Informationen zur Verwendung der Data Access API finden Sie im Abschnitt [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Anwendungsfälle

* Rufen Sie Rohdaten und verarbeitete Datendateien aus Experience Platform ab, um sie in Unternehmensumgebungen zu speichern und zu bewerten.

#### Überlegungen

* Da auf Daten asynchron im Batch-Modus zugegriffen wird, ist der Zugriff auf die Daten im Vergleich zu Streaming-Datenausgangsansätzen wie der Automatisierung von Tags, der Ereignisweiterleitung oder RTCDP-Zielen von Natur aus latent.
* Datendateien werden bei der Verarbeitung in Experience Platform als Dateisammlungen in Stapeln gespeichert und im Parquet-Format komprimiert und gespeichert. Daher müssen beim Zugreifen auf und Herunterladen der Dateien in eine andere Umgebung sie systematisch von ihrem Batch und ihrer Datei aufgerufen werden, im Gegensatz zu einem ganzen Datensatz, und alle Vorgänge auf den Daten müssen die Dateien berücksichtigen, die im Parquet-Format komprimiert werden.

### Abfrage-Service {#query-service}

Mithilfe der Experience Platform Query Service können Kunden Datensätze in Experience Platform abfragen und die Ergebnisse der Abfrage beibehalten. Ein SQL-Client kann verwendet werden, um die Abfrageantwort im gewünschten Speicherziel abzufragen und beizubehalten, das der SQL-Client unterstützen kann. Die Query Service-Benutzeroberfläche kann verwendet werden, um das SQL-Ergebnis in einem Zieldatensatz in der Experience Platform zu speichern, oder die Ergebnisse können auf dem lokalen Computer gespeichert werden.

* Weitere Informationen zur Verbindung mit SQL-Clients zum Beibehalten von SQL-Ergebnissen aus Experience Platform Query Service finden Sie in den folgenden Abschnitten [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Anwendungsfälle

* Rufen Sie Rohdaten aus den Experience Platform-Datensätzen ab und behalten Sie die Abfrageergebnisse bei.
* Abfragen des Profilmomentdatensatzes, um Einblicke in das Echtzeit-Kundenprofil zu gewinnen. [Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* Speichern Sie die Abfrageergebnisse in einem separaten Datensatz für den Zugriff oder in einem profilaktivierten Datensatz, der später über RTCDP und andere Experience Cloud-Anwendungen, die auf das Echtzeit-Kundenprofil zugreifen, egresdiert werden kann.

#### Überlegungen

* Da Daten asynchron im Batch-Modus abgefragt werden, ist der Zugriff auf die Daten im Vergleich zu Streaming-Datenausgangsansätzen wie der Automatisierung von Tags, der Ereignisweiterleitung oder RTCDP-Zielen von Natur aus latent.
* Mit dem Abfragedienst können nur Daten abgefragt werden, die im Experience Platform Data Lake verfügbar sind. Der Echtzeit-Kundenprofilspeicher, das Identitätsdiagramm, der Customer Journey Analytics können nicht direkt mit dem Abfragedienst abgefragt werden. Nur wenn Datensätze in den Data Lake exportiert werden, können diese Datensätze abgefragt werden, wie im Beispiel des Profil-Snapshot-Datensatzes.
* Beachten Sie, dass die Limits für die Anzahl der Abfrageergebnisse und die Zeitüberschreitung der Abfrage gelten, wie im Abschnitt [Limits für Query Services](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) Dokumentation.

## Ansätze für den Datenexport

### Client-seitige Tags-Erweiterungen {#client-side-tags-extensions}

Erweiterungen können mit der Tags-Lösung von Adobe bereitgestellt werden. Sobald eine Erweiterung bereitgestellt ist, werden Datenanforderungen direkt in einem Client-Browser oder einer Anwendung bereitgestellt und es kann eine Anfrage aufgerufen werden, um Daten und Anforderungen an das gewünschte Ziel zu senden.

Siehe Abschnitt [Übersicht über Tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) Dokumentation für weitere Informationen.

#### Anwendungsfälle

* Erfassen Sie Roh-Streaming-Informationen direkt aus Client-seitigen Umgebungen mithilfe von Tagging.

#### Überlegungen

* Kein direkter Zugriff auf serverseitige Informationen wie das Echtzeit-Kundenprofil der Experience Platform und die Zielgruppenmitgliedschaften.
* Das Hinzufügen zusätzlicher Datenerfassungs-Tags zur Seite kann die Seitenladezeiten erhöhen.
* Möglichkeit, Regeln einzurichten, die nur Daten anfordern, wenn bestimmte Kriterien erfüllt sind.
* Daten werden direkt vom Client erfasst, wodurch die Arten von Transformationen und Anreicherungen begrenzt werden, die vor der Datenerfassung durchgeführt werden können.

### Ereignisweiterleitung {#event-forwarding}

Datenerfassungsanfragen werden direkt an das Edge Network der Adobe erfasst. Von den Edge Network-Anfragen an externe RESTful-Endpunkte können konfiguriert werden, um diese Anfragen an das externe Ziel weiterzuleiten.

Siehe Folgendes [Ereignisweiterleitung](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) Dokumentation für weitere Informationen.

#### Anwendungsfälle

* Erfassen Sie Roh-Streaming-Informationen direkt von Client-seitigen Umgebungen zu einem Enterprise-Endpunkt mithilfe der serverseitigen Ereignisweiterleitung von Adobe.

#### Überlegungen

* Um die Ereignisweiterleitung zu verwenden, müssen Daten mithilfe des WebSDK oder MobileSDK an das Edge-Netzwerk gesendet werden.
* Der Ansatz der Ereignisweiterleitung reduziert die Seitenladezeit und -gewichtung aufgrund zusätzlicher Tags, die auf der Seite hinzugefügt werden.
* Derzeit wird keine Anreicherung vom Edge-Profil oder anderen Datenquellen unterstützt.
* Eingeschränkte Datenfilterung und einfache Zuordnungstransformationen werden unterstützt.

### Real-time Customer Data Platform-Ziele {#RTCDP-destinations}

Profilattributdaten und Daten zur Zielgruppenmitgliedschaft können für Unternehmens- und Werbeziele aktiviert werden. Das bedeutet, dass die ausgegebenen Daten in das Echtzeit-Kundenprofil der Experience Platform aufgenommen werden müssen.

Siehe Abschnitt [Real-time Customer Data Platform-Ziele](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) Dokumentation für weitere Informationen.

#### Anwendungsfälle

* Aktivieren Sie Profilattributinformationen, einschließlich Zielgruppenmitgliedschaft in einem internen Unternehmensdatenspeicher, Analysetool, E-Mail-System oder Supportsystem.
* Aktivieren Sie die Profil-Zielgruppenmitgliedschaft bei einem externen Werbeanbieter, um Inhalte auf das Profil auszurichten und zu personalisieren.

#### Überlegungen

* Profilattribute und Zielgruppenmitgliedschaften können aktiviert werden. Rohe Erlebnisereignisse können derzeit nicht als Teil von RTCDP-Zielen aktiviert werden.
* Aktivierungen erfolgen im Streaming- oder Batch-Modus, je nach Art der Segmentbewertung und der Art des Aufnahmeprotokolls, das das Ziel akzeptiert.

### Benutzerdefinierte Journey Optimizer-Aktionen {#jo-custom-actions}

Mit Journey Optimizer können Kunden eine benutzerdefinierte Aktion von der Journey-Arbeitsfläche aus aufrufen, um eine Payload oder Nachricht an einen konfigurierten externen API-Endpunkt zu senden. Eine Aktion kann für jeden Dienst eines beliebigen Anbieters konfiguriert werden, der über eine REST-API mit einer JSON-formatierten Payload aufgerufen werden kann. Diese Payload kann Ereignisinformationen, Profilattribute und frühere Ereignisdaten, Transformationen und Anreicherungen enthalten, die in der Journey konfiguriert sind.

Siehe Abschnitt [Benutzerdefinierte Journey Optimizer-Aktionen](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) Dokumentation für weitere Informationen.

#### Anwendungsfälle

* Aktivierungsereignisse aus Experience Platform und Journey Optimizer, die zusätzliche Informationen aus dem Echtzeit-Kundenprofil enthalten.
* Informieren Sie externe Systeme, wenn ein Kunde einen bestimmten Punkt einer Journey erreicht hat.

#### Überlegungen

* Limits auf den von [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) und Anreicherungen, die von der [Echtzeit-Kundenprofil](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) gelten.
* Benutzerdefinierte Aktionen können nacheinander für jedes Ereignis oder Profil in einer Journey ausgeführt werden. Massenvorgänge oder Massendatenaussendungen in Form von Dateien oder aggregierten Anforderungen in kundenübergreifenden Journey können nicht ausgeführt werden.
* Streaming-Zugriff auf Attribute des Echtzeit-Kundenprofils und Erlebnisereignisse, die in die Aktivierungs-Payload aufgenommen werden können.
* Ereignisdaten können gefiltert und einfache Zuordnungstransformationen angewendet werden, bevor Ereignisse an externe Ziele gesendet werden.










