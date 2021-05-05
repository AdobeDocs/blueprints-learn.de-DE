---
title: Konzept für die Analyse der Call-Deflection
description: Analyse des Kundenverhaltens, bevor Kunden das Callcenter kontaktieren.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 93%

---

# Blueprint der Journey-Analyse

Analysieren Sie das Kundenverhalten über Desktop und Mobile hinweg, bevor der Kunde das Callcenter kontaktiert. Identifizieren Sie Möglichkeiten zur Verbesserung der Customer Journey, indem Sie verstehen, welche Aktionen Ihre Kunden abschließen möchten, welchen Content sie anzeigen und nach welchen Begriffen sie suchen, bevor sie den Kunden-Support kontaktieren. Ermitteln Sie, welcher Content und welche Self-Service-Tools verbessert werden können, um Kunden bei der Behebung von Problemen zu helfen, ohne dass sie das Callcenter anrufen müssen.

## Anwendungsfälle

* Analyse des Kundenverhaltens vor dem Anruf beim Support
* Aufdeckung von Möglichkeiten zur Verbesserung des Self-Service

## Programme

* Adobe Experience Platform
* Customer Journey Analytics

## Integrationsmuster

* Adobe Experience Platform → Customer Journey Analytics

## Architektur

<img src="assets/CJA.svg" alt="Referenzarchitektur für Blueprint „Customer Journey Analytics“" style="border:1px solid #4a4a4a" />

## Implementierungsschritte

1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) Schemata für Daten, die aufgenommen werden sollen.
1. [Erstellen Sie ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) Datensätze, damit Daten erfasst werden.
1. [Aufnehmen der Daten in Experience Platform.
](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
Die Daten müssen in Platform aufgenommen werden, bevor sie in Customer Journey Analytics aufgenommen werden können
1. Analyse der kanalübergreifenden Ereignis-Datensätze.
Datensätze, die zusammen analysiert werden, müssen eine gemeinsame Namespace-ID haben oder über das feldbasierte Stitching in Customer Journey Analytics einen neuen Schlüssel erhalten. 

   >[!NOTE]
   >
   >Customer Journey Analytics verwendet derzeit weder das Experience Platform-Profil noch Identity Service für das Stitching.

1. Führen Sie eine beliebige benutzerdefinierte Datenvorbereitung durch oder wenden Sie das feldbasierte Identitäts-Stitching auf die Daten an, um sicherzustellen, dass ein gemeinsamer Schlüssel in den Zeitreihen-Datensätzen in Customer Journey Analytics aufgenommen wird.
1. Stellen Sie eine primäre ID für die Suchdaten bereit, die einem Feld in den Ereignisdaten zugeordnet werden kann. Zählt bei der Lizenzierung als Zeilen.
1. Setzen Sie die für Profildaten dieselbe primäre ID wie für die Ereignisdaten.
1. Konfigurieren Sie ein Datenverbindung, um Daten aus Experience Platform in Customer Journey Analytics aufzunehmen. Nachdem die Daten im Data Lake angekommen sind, werden sie innerhalb von 90 Minuten in Customer Journey Analytics verarbeitet.
1. Konfigurieren Sie eine Datenansicht für die Verbindung, um die spezifischen Dimensionen und Metriken auszuwählen, die in der Ansicht angezeigt werden sollen. Die Einstellungen für Attribution und Zuordnung werden auch in der Datenansicht konfiguriert. Diese Einstellungen werden zum Zeitpunkt der Berichterstellung berechnet.
1. Erstellen Sie ein Projekt, um Dashboards und Berichte in Analysis Workspace zu konfigurieren.

## Überlegungen bei der Implementierung

### Überlegungen beim Identitäts-Stitching

* Die Zeitreihendaten, die zusammengeführt werden sollen, müssen für jeden Datensatz dieselbe Namespace-ID haben. Um alle Callcenter-Daten mit anonymen Gerätedaten zu verbinden, muss die digitale ID mit der Calling-ID verknüpft werden. Diese Verknüpfung kann über verschiedene Mechanismen erstellt werden:
   * Die Anrufnummer ist eine eindeutige Anrufnummer für diesen Besucher zu diesem Zeitpunkt. Die Beziehung kann anhand einer Suchtabelle nachvollzogen werden.
   * Fordern Sie den Benutzer auf, sich vor der Support-Anfrage zu authentifizieren, und verknüpfen Sie diese Authentifizierung mit einer Kennung, die vom Agenten bestimmt wird (z. B. Telefonnummer oder E-Mail).
   * Verwenden Sie einen Onboarding-Partner, der Sie bei der Eingabe Online-Gerätekennungen unterstützt, wenn bekannte Kennungen mit der Support-Anfrage verknüpft sind.
* Der Zusammenführungsprozess für getrennte Datensätze erfordert einen gemeinsamen, datensatzübergreifenden primären Personen-/Einheitsschlüssel.
* Sekundäre schlüsselbasierte Zusammenführungen werden derzeit nicht unterstützt.
* Der feldbasierte ID-Stitching-Prozess erlaubt die erneute ID-Schlüsselvergabe in Zeilen, die auf aufeinanderfolgenden, vorübergehenden ID-Einträgen basieren, wie eine Authentifizierungs-ID. Dieser Prozess erlaubt es, ungleiche Einträge zu einer ID zusammenzuführen, sodass eine Analyse auf Personen- statt Geräte- oder Cookie-Ebene möglich ist.
* Das Stitching erfolgt einmal pro Woche mit einer Wiederholung nach dem Zusammenfügen.

## Häufig gestellte Fragen

* Welche Downstream-Auswirkungen haben Datenmodelle in Customer Journey Analytics?

   Objekte und Attribute desselben XDM-Felds werden in Customer Journey Analytics zu einer Dimension zusammengeführt. Um mehrere Attribute aus unterschiedlichen Datensätzen in derselben CJA-Dimension zusammenzuführen, sollten die Datensätze das gleiche XDM-Feld oder Schema referenzieren.

## Verwandte Dokumentation

* [Produktbeschreibung zu Customer Journey Analytics](https://helpx.adobe.com/de/legal/product-descriptions/customer-journey-analytics.html)
* [Dokumentation zu Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=de)
* [Tutorials zu Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=de)
