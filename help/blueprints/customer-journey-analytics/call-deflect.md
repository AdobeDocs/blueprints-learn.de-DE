---
title: Konzept für die Analyse der Call-Deflection
description: Analysieren Sie das Kundenverhalten, bevor Sie das Call-Center kontaktieren.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Blueprint der Journey-Analyse

Analysieren Sie das Verhalten eines Kunden auf Desktop- und Mobilgeräten, bevor er das Call-Center kontaktiert. Finden Sie heraus, welche Möglichkeiten zur Verbesserung der Journey bestehen, indem Sie verstehen, welche Aktionen Ihre Kunden durchführen möchten, welche Ansichten sie bearbeiten und welche Begriffe sie suchen, bevor sie sich an den Kundensupport wenden. Bestimmen Sie die Content- und Selbstbedienungstools, die verbessert werden können, um Ihren Kunden bei der Lösung von Problemen zu helfen, ohne vorher anrufen zu müssen.

## Anwendungsfälle

* Analysieren Sie das Kundenverhalten, bevor Sie sich an den Support wenden.
* Entdecken Sie Möglichkeiten zur Verbesserung der Selbstbedienungsfunktionen.

## Anwendungen

* Adobe Experience Platform
* Customer Journey Analytics

## Integrationsmuster

* Adobe Experience Platform → Customer Journey Analytics

## Architektur

<img src="assets/CJA.svg" alt="Referenzarchitektur für das Customer Journey Analytics-Blueprint" style="border:1px solid #4a4a4a" />

## Guardraht

Dateneinbettung in Customer Journey Analytics:

* Datenaufnahme zum See: API ~ 7 GB/Stunde, Quellanschluss ~ 200 GB/Stunde, Streaming zum See ~ 15 Minuten, Analytics-Quellanschluss zum See ~ 45 Minuten.
* Nach der Veröffentlichung der Daten im Data Lake kann die Verarbeitung bis zu 90 Minuten dauern.

## Implementierungsschritte

1. Konfigurieren von Datensätzen und Schemas.
1. Daten in Plattform aufnehmen
Die Daten müssen vor der Erfassung in Customer Journey Analytics in Platform aufgenommen werden.
1. Analysieren Sie Kanal-Ereignis-Datensätze.
In Vereinigung analysierte Datensätze müssen über eine gemeinsame Namensraum-ID verfügen oder durch die feldbasierte Heftfunktion von Customer Journey Analytics neu keyiert werden. 

   >[!NOTE]
   >
   >Customer Journey Analytics verwendet derzeit nicht das Experience Platform-Profil oder die Identitätsdienste zum Verbinden.

1. Führen Sie eine benutzerspezifische Datenvorbereitung oder Verwendung der feldbasierten Identitätszuordnung auf den Daten durch, um sicherzustellen, dass ein gemeinsamer Schlüssel über Zeitreihendatensätze hinweg in den Customer Journey Analytics aufgenommen wird.
1. Geben Sie eine primäre ID für Nachschlagedaten an, die mit einem Feld in den Ereignis-Daten verknüpft werden können. Zählt bei der Lizenzierung als Zeilen.
1. Legen Sie dieselbe primäre ID für Profil-Daten wie die primäre ID der Ereignis-Daten fest.
1. Konfigurieren Sie eine Datenverbindung, um Daten von Experience Platform zu Customer Journey Analytics zu erfassen. Nachdem Daten in den Datensee gelangen, werden sie innerhalb von 90 Minuten in Customer Journey Analytics verarbeitet.
1. Konfigurieren Sie eine Ansicht der Daten für die Verbindung, um die spezifischen Dimensionen und Metriken auszuwählen, die in die Ansicht aufgenommen werden sollen. Zuordnungs- und Zuordnungseinstellungen werden auch in der Ansicht der Daten konfiguriert. Diese Einstellungen werden zur Berichtszeit berechnet.
1. Erstellen Sie ein Projekt, um Dashboard und Berichte in Analysis Workspace zu konfigurieren.

## Überlegungen zur Implementierung

### Überlegungen zur Identitätsanpassung

* Zeitreihendaten, die geteilter werden sollen, müssen in jedem Datensatz denselben ID-Namensraum aufweisen. Um Call-Center-Daten mit anonymen Gerätedaten zu verbinden, muss die digitale ID mit der aufrufenden ID verknüpft sein. Diese Kopplung kann durch mehrere mögliche Mechanismen erfolgen:
   * Die Wählnummer ist eine eindeutige Wählnummer für diesen Besucher für diesen Zeitraum zusammen mit einer Suchtabelle zur Verfolgung der Beziehung.
   * Der Benutzer muss sich authentifizieren, bevor er Unterstützung anfordert, und diese Authentifizierung mit einem vom Anrufagenten bestimmten Bezeichner (z. B. Telefonnummer oder E-Mail) verknüpfen.
   * Verwenden Sie einen Onboarding-Partner, um Online-Geräte-IDs mit bekannten Identifikatoren einzugeben, die mit der Supportanfrage verknüpft sind.
* Für die Vereinigung unterschiedlicher Datensätze ist ein gemeinsamer primärer Personen-/Entitätsschlüssel für alle Datensätze erforderlich.
* Sekundär wichtige Vereinigungen werden derzeit nicht unterstützt.
* Der feldbasierte Identitätszuordnungsprozess ermöglicht die erneute Eingabe von Identitäten in Zeilen anhand nachfolgender transienter ID-Datensätze, z. B. einer Authentifizierungs-ID. Dieser Vorgang ermöglicht die Auflösung unterschiedlicher Datensätze in eine einzelne ID zur Analyse auf der Ebene der Person und nicht auf der Geräte- oder Cookie-Ebene.
* Das Sticken erfolgt einmal in der Woche, wobei das Wiederholen nach dem Stich erfolgt.

## Häufig gestellte Fragen

* Welche Auswirkungen haben die Datenmodelle auf den Customer Journey Analytics?

   Objekte und Attribute desselben XDM-Felds werden in einem Customer Journey Analytics zu einer Dimension zusammengeführt. Um mehrere Attribute aus verschiedenen Datasets mit derselben CJA-Dimension zusammenzuführen, sollten die Datensätze auf dasselbe XDM-Feld oder -Schema verweisen.

## Verwandte Dokumentation

* [Produktbeschreibung für Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Dokumentation zum Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics-Lernprogramme](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
