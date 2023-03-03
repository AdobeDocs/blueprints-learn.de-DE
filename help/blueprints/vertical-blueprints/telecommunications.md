---
title: Telekommunikationsbranche – Journey Optimizer für automatisch ausgelöstes Messaging
description: Bereitstellung maßgeschneiderter Angebote in Echtzeit bei gleichzeitigem effizientem Onboarding von Kunden, das für langfristige Kundentreue sorgt.
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: 1a0ce987fc615080bb78fb8ecf60c96e362a95c0
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---

# Telekommunikationsbranche – geschäftliche Herausforderung

Vor der Implementierung dieser Blueprint basierten die E-Mail-Kampagnen des Telekommunikationsunternehmens mit Werbung für eine neue Leitung darauf, dass der Benutzer einen Kauf getätigt hatte. Überprüft wurde dies erst nach einer Wartezeit von sieben Tagen. Sobald diese Kriterien erfüllt waren, wurden weitere Touchpoints initiiert.

Diese Einschränkung musste beseitigt werden, um ein schnelleres Follow-up bei Benutzern zu ermöglichen, die schon vor der aktuellen Wartezeit von sieben Tagen eine weitere Leitung erwerben wollten.

## Lösungsansatz von Adobe

* Adobe Analytics-Daten zur Identifizierung von Benutzerinnen und Benutzern, die keine neue Leitung gekauft haben, werden Adobe Journey Optimizer als Datenquelle hinzugefügt.
* Adobe Journey Optimizer verwendet eine Regel, anhand der der Zeitpunkt festgelegt wird, zu dem Kundinnen und Kunden eine benutzerdefinierte „Abbruch“-Nachricht erhalten. Diese soll die Kundinnen und Kunden ermutigen, ihrem Konto eine neue Leitung hinzuzufügen und den Kauf zu tätigen.


## Realisierter geschäftlicher Wert

| Ziele | Taktik | Erzielter Wert |
|---|---|---|
| **Erhöhung der Kampagnen-Konversionsraten **<br></br>** Steigerung des jährlichen Umsatzes pro Account**</ul> | <ul><li>Erstellen eines neuen Segments nahezu in Echtzeit für Benutzer, die durch Hinzufügen einer Leitung Interesse gezeigt, aber noch nicht gekauft haben.</li><li>Follow-up bei Kunden, die keinen Kauf getätigt haben, mit einem zweiten Touchpoint für interessierte Nicht-Käufer. </li><li>Verwenden einer Teststrategie, um die Journey-Performance zu messen und Konversionsraten über den E-Mail-Kanal zu optimieren.</li></ul> | <ul><li><strong>Hochqualitative, relevante Erlebnisse:</strong> Mit Journey Orchestration erhalten Kunden relevante Botschaften, wodurch sich weniger Personen von E-Mail-Listen abmelden.</li><li><strong>Skalierbare Journey-Orchestrierung:</strong> Durch die Bereitstellung einer personalisierten und zeitnahen Customer Journey können die Konversionen und der Gesamtumsatz gesteigert werden.</li></ul> |

## Primäre Blueprint: Zielgruppen und Aktivierung mit Experience Cloud-Programmen

### Beschreibung

<ul><li>Ausführen von Trigger-basiertem und Streaming-Messaging mit Adobe Experience Platform als Zentrale für Streaming-Daten, Kundenprofile und Segmentierung mit Journey Orchestration für die Orchestrierung der Streaming-Journey und der Messaging-Bereitstellung</li></ul>

### Experience Cloud-Programme

<ul><li>Adobe Journey Optimizer</li></ul>

### Blueprint-Architektur

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=de"><img alt="Bild für ein Telekommunikationsunternehmen, das maßgeschneiderte Angebote in Echtzeit bei gleichzeitigem effizientem Onboarding von Kunden bietet, was für langfristige Kundentreue sorgt." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/ajo-architecture.svg"/></a>
