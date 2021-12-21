---
title: Telekommunikationsbranche - Journey Optimizer für ausgelöste Nachrichten
description: Bereitstellung maßgeschneiderter Angebote in Echtzeit bei gleichzeitigem effizienten Onboarding von Kunden für langfristige Kundentreue.
solution: Experience Platform, Journey Optimizer
kt: 9486
source-git-commit: c393d73d2fa7acd4e5c2d99c098503b023b6115d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 12%

---


# Geschäftliche Herausforderung der Telekommunikationsbranche

Vor der Implementierung dieses Blueprints stützten sich die E-Mail-Kampagnen des Telekommunikationsunternehmens auf die Frage, ob der Benutzer konvertiert hatte und danach erst nach einer Wartezeit von 7 Tagen überprüft wurde. Sobald diese Kriterien erfüllt sind, wurden weitere Touchpoints initiiert.

Diese Einschränkung musste behoben werden, um eine schnellere Weiterverfolgung für Benutzer einzuleiten, die eine Zeile vor der aktuellen Status-Wartezeit von 7 Tagen hinzufügen wollten.

## Adobe

* Adobe Analytics-Daten zur Identifizierung von Benutzern, die nicht konvertiert werden konnten, um eine neue Zeile hinzuzufügen, werden als Datenquelle zur Verwendung durch Adobe Journey Optimizer eingefügt.
* Adobe Journey Optimizer verwendet eine Regel für die Zeit, in der der Kunde eine benutzerdefinierte &quot;Abbruch&quot;-Nachricht erhält, um einen Kunden zur Konversion anzuregen, indem eine neue Zeile zu seinem Konto hinzugefügt wird.


## Geschäftlicher Wert bereitgestellt

| Ziele | Taktik | Wert entsperrt |
|---|---|---|
| **Erhöhte Kampagnenkonversionsraten **<br></br>**Jährliche Kontoeinnahmen erhöhen**</ul> | <ul><li>Erstellen Sie ein neues Segment nahezu in Echtzeit für Benutzer, die Interesse am Hinzufügen einer Zeile gezeigt, aber noch nicht konvertiert haben.</li><li>Fördern Sie das Follow-up für nicht konvertierte Kunden mit einem zweiten Touchpoint für interessierte Nicht-Konverter. </li><li>Verwenden Sie eine Teststrategie, um die Journey-Performance zu messen und die Konversion per E-Mail zu optimieren.</li></ul> | <ul><li><strong>Hohe Qualität, relevante Erlebnisse:</strong> Mit der Journey-Orchestrierung erhalten Kunden relevantere Botschaften, die die Abwanderung von E-Mail-Listen verringern.</li><li><strong>Journey Orchestration bei Skalierung:</strong>Es kann eine personalisierte und zeitlichere Journey erstellt werden, um die Konversionen und den Gesamtumsatz zu steigern.</li></ul> |

## Primäres Blueprint: Zielgruppe und Aktivierung mit Experience Cloud-Anwendungen

### Beschreibung

<ul><li>Ausführen von Trigger-basiertem und Streaming-Messaging mit Adobe Experience Platform als Zentrale für Streaming-Daten, Kundenprofile und Segmentierung mit Journey Orchestration für die Orchestrierung der Streaming-Journey und der Messaging-Bereitstellung</li></ul>

### Experience Cloud-Programme

<ul><li>Adobe Journey Optimizer</li></ul>

### Blueprint-Architektur

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=de"><img alt="Das Miniaturbild für ein Telekommunikationsunternehmen bietet maßgeschneiderte Angebote in Echtzeit bei effizientem Onboarding von Kunden für langfristige Loyalität." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>





