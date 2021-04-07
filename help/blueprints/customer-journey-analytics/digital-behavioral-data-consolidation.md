---
title: Konzept zur Konsolidierung digitaler Verhaltensdaten
description: Analysieren und extrahieren Sie Einblicke aus Kundeninteraktionen über die Journey.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Konzept zur Konsolidierung digitaler Verhaltensdaten

Sie erhalten eine konsolidierte Ansicht des Kundenverhaltens über verschiedene Kanal hinweg, indem Sie Daten aus verschiedenen Web-, Mobil- und Offlineeigenschaften zusammenführen.

## Anwendungsfälle

* Analysieren Sie Kundeninteraktionen auf Desktop- und Mobilgeräten, um das Kundenverhalten zu verstehen und Einblicke zu gewinnen, um digitale Kundenerlebnisse zu optimieren.
* Analysieren Sie Kundeninteraktionen auf allen Kanälen, einschließlich digitaler und offline-Kanal wie Supportinteraktionen und Einkäufe im Geschäft, um die Journey der Kunden besser zu verstehen und zu optimieren. 

## Anwendungen

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (optional)

## Integrationsmuster

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architektur

<img src="assets/CJA.svg" alt="Referenzarchitektur für das Customer Journey Analytics-Blueprint" style="border:1px solid #4a4a4a" />

## Guardraht

Dateneinbettung in Customer Journey Analytics:

* Datenaufnahme zum See: API ~ 7 GB/h, Quellanschluss ~ 200 GB/Stunde, Streaming zum See ~ 15 Minuten, Adobe Analytics-Quellanschluss zum See ~ 45 Minuten.
* Nach der Veröffentlichung der Daten im Data Lake kann die Verarbeitung bis zu 90 Minuten dauern.

## Implementierungsschritte

1. Konfigurieren von Datensätzen und Schemas.
1. Daten in Plattform aufnehmen
Die Daten müssen vor der Verarbeitung zu Customer Journey Analytics in Platform aufgenommen werden.
1. Analysieren Sie Kanal-übergreifende Ereignis-Datensätze, die in Vereinigung analysiert werden sollen, um sicherzustellen, dass sie über eine gemeinsame Namensraum-ID verfügen oder durch die feldbasierte Heftfunktion von Customer Journey Analytics neu keyiert werden. 

   >[!NOTE]
   >
   >Customer Journey Analytics verwendet derzeit nicht das Experience Platform-Profil oder die Identitätsdienste zum Verbinden.

1. Führen Sie eine benutzerspezifische Datenvorbereitung oder Verwendung der feldbasierten Identitätszuordnung auf den Daten durch, um sicherzustellen, dass ein gemeinsamer Schlüssel über Zeitreihendatensätze hinweg in den Customer Journey Analytics aufgenommen wird.
1. Weisen Sie den Suchdaten eine primäre ID zu, die mit einem Feld in den Ereignis-Daten verknüpft werden kann. Zählt bei der Lizenzierung als Zeilen.
1. Legen Sie dieselbe primäre ID für Profil-Daten wie die primäre ID der Ereignis-Daten fest.
1. Konfigurieren Sie eine Datenverbindung, um Daten von Experience Platform zu Customer Journey Analytics zu erfassen. Nachdem Daten in den Datensee gelangen, werden sie innerhalb von 90 Minuten in Customer Journey Analytics verarbeitet.
1. Konfigurieren Sie eine Ansicht der Daten für die Verbindung, um die spezifischen Dimensionen und Metriken auszuwählen, die in die Ansicht aufgenommen werden sollen. Zuordnungs- und Zuordnungseinstellungen werden auch in der Ansicht der Daten konfiguriert. Diese Einstellungen werden zur Berichtszeit berechnet.
1. Erstellen Sie ein Projekt, um Dashboard und Berichte in Analysis Workspace zu konfigurieren.

## Überlegungen zur Implementierung

### Überlegungen zur Identitätsanpassung

* Zeitreihendaten, die geteilter werden sollen, müssen in jedem Datensatz denselben ID-Namensraum aufweisen.
* Für die Vereinigung unterschiedlicher Datensätze ist ein gemeinsamer primärer Personen-/Entitätsschlüssel für alle Datensätze erforderlich.
* Sekundär wichtige Vereinigungen werden derzeit nicht unterstützt.
* Der feldbasierte Identitätszuordnungsprozess ermöglicht die erneute Eingabe von Identitäten in Zeilen anhand nachfolgender transienter ID-Datensätze, z. B. einer Authentifizierungs-ID. Dadurch können unterschiedliche Datensätze zu einer einzigen ID aufgelöst werden, um sie auf der Ebene der Person und nicht auf der Geräte- oder Cookie-Ebene Analyse.
* Das Sticken erfolgt einmal in der Woche, wobei das Wiederholen nach dem Stich erfolgt.

## Häufig gestellte Fragen

* Welche Auswirkungen haben die Datenmodelle auf den Customer Journey Analytics?

   Objekte und Attribute desselben XDM-Felds werden in einem Customer Journey Analytics zu einer Dimension zusammengeführt. nach  mehrere Attribute aus verschiedenen Datensätzen in derselben Dimension des Customer Journey Analytics zusammenführen, sollten die Datensätze auf dasselbe XDM-Feld oder -Schema verweisen.

## Verwandte Dokumentation

* [Produktbeschreibung für Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Dokumentation zum Customer Journey Analytics](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics-Lernprogramme](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
