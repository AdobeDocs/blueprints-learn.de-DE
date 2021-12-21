---
title: Telekommunikationsbranche - Journey Optimizer für ausgelöste Nachrichten
description: Bereitstellung maßgeschneiderter Angebote in Echtzeit bei gleichzeitigem effizienten Onboarding von Kunden für langfristige Kundentreue.
solution: Experience Platform, Journey Optimizer
kt: 9486
source-git-commit: 7a81ea5d71355323a784e12207542fb7dd6b286b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 12%

---


# Geschäftliche Herausforderung der Telekommunikationsbranche

Vor der Implementierung dieses Blueprints stützten sich die E-Mail-Kampagnen des Telekommunikationsunternehmens auf die Frage, ob der Benutzer konvertiert hatte und danach erst nach einer Wartezeit von 7 Tagen überprüft wurde. Sobald diese Kriterien erfüllt sind, wurden weitere Touchpoints initiiert.

Diese Einschränkung musste behoben werden, um eine schnellere Weiterverfolgung für Benutzer einzuleiten, die eine Zeile vor der aktuellen Status-Wartezeit von 7 Tagen hinzufügen wollten.

## Adobe

* Adobe Analytics-Daten zur Identifizierung von Benutzern, die nicht konvertiert werden konnten, um eine neue Zeile hinzuzufügen, werden als Datenquelle zur Verwendung durch Adobe Journey Optimizer eingefügt.
* Adobe Journey Optimizer verwendet eine Regel, die immer dann angewendet wird, wenn Kunden eine benutzerdefinierte &quot;Abbruch&quot;-Nachricht erhalten, die einen Kunden zur Konversion anregen soll, indem eine neue Zeile zu seinem Konto hinzugefügt wird.


## Geschäftlicher Wert bereitgestellt

| Ziele | Taktik | Wert entschlüsselt |
|---|---|---|
| **Erhöhte Kampagnenkonversionsraten **<br></br>**Jährliche Kontoeinnahmen erhöhen**</ul> | <ul><li>Erstellen Sie ein neues Segment nahezu in Echtzeit für Benutzer, die Interesse am Hinzufügen einer Zeile gezeigt, aber noch nicht konvertiert haben.</li><li>Fördern Sie das Follow-up für nicht konvertierte Kunden mit einem zweiten Touchpoint für interessierte Nicht-Konverter. </li><li>Verwenden Sie eine Teststrategie, um die Journey-Performance zu messen und die Konversion per E-Mail zu optimieren.</li></ul> | <ul><li><strong>Hohe Qualität, relevante Erlebnisse:</strong> Mit der Journey-Orchestrierung erhalten Kunden relevantere Botschaften, die die Abwanderung von E-Mail-Listen verringern.</li><li><strong>Journey Orchestration bei Skalierung:</strong>Es kann eine personalisierte und zeitlichere Journey erstellt werden, um die Konversionen und den Gesamtumsatz zu steigern.</li></ul> |

## Key Blueprint: Zielgruppe und Aktivierung mit Experience Cloud-Anwendungen

<strong>Beschreibung</strong>
<ul><li>Ausführen von Trigger-basiertem und Streaming-Messaging mit Adobe Experience Platform als Zentrale für Streaming-Daten, Kundenprofile und Segmentierung mit Journey Orchestration für die Orchestrierung der Streaming-Journey und der Messaging-Bereitstellung</li></ul>

<strong>Experience Cloud-Programme</strong>
<ul><li>Adobe Journey Optimizer</li></ul> 
<br>

### Blueprint-Architektur

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=de"><img alt="Das Miniaturbild für ein Telekommunikationsunternehmen bietet maßgeschneiderte Angebote in Echtzeit bei effizientem Onboarding von Kunden für langfristige Loyalität." src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>





