---
title: Aktivierung von Audience und Profil
description: Bieten Sie mit der Echtzeit-Kundendatenplattform zielgruppenaktivierte und profilorientierte Kundenerlebnisse.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: b5d8160235fb510642701ba066434d8bd226b464
workflow-type: tm+mt
source-wordcount: '1201'
ht-degree: 16%

---


# Aktivierung von Audience und Profil

Die Aktivierung von Audience und Profil ist der Schlüssel zum Erfolg in einer datengesteuerten Marketingwelt. Allerdings orientieren sich viele Marken bei der Aktivierung noch immer zunächst am Kanal, was häufig in inkonsistenter Reichweite und Personalisierung endet.

Wenn der Kanal an erster Stelle steht, fungiert jeder Kanal als Silo, in dem Personalisierung für Kunden erfolgt, die auf diesem Kanal mit der Marke interagieren. Diese Herangehensweise spiegelt nicht die Realität wider, in der Kunden über viele verschiedene Touchpoints hinweg mit der Marke interagieren. Audience und Profil-Aktivierung ermöglichen es Marken, Kundeninteraktionen über mehrere Kanal hinweg zu verbinden und ein zentralisiertes Profil und eine Audience zu liefern, die für alle Kanal aktiviert werden können.

| Blueprint | Beschreibung | Experience Cloud-Programme |
|---|---|---|
| **[Anonyme Audience Activation](anonymous.md)** | <ul><li>Identifizieren Sie Zielgruppen basierend auf anonymen und verhaltensbasierten Kundendaten über Web- und Werbekanäle hinweg.</li><li>Third-Party-Zielgruppendaten können für bessere Personalisierung integriert werden.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Online-/Offline-Audience Activation](online-offline.md)** | <ul><li>Aktivieren Sie bekannte Profil-basierte Ziele wie E-Mail-Anbieter, soziale Netzwerke und Werbeziele. </li><li>Verwenden Sie Offline-Attribute und -Ereignis, wie z. B. Offline-Bestellungen, Transaktionen, CRM-Daten oder Treuedaten, sowie Online-Verhalten für Online-Targeting und Personalisierung.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-Time Customer Data Platform]</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Aktivierung von Audience und Profil zu Unternehmenszielen](enterprise-destinations.md)** | <ul><li>Replikation und Aktualisierung von Profil- und Audience-Änderungen an Unternehmensdatenspeichern für Aktivierung- und Berichte-Anwendungsfälle. </li></ul><ul><li>Starten Sie eine Verkaufs- oder Supportaktion für den Kunden durch Benachrichtigung über eine Kundenaktion von der [!UICONTROL Echtzeit-Kundendatenplattform] zu Unternehmenssystemen und -anwendungen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-Time Customer Data Platform]</li><li>Experience Platform Aktivierung</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Customer Activity Hub](customer-activity.md)** | <ul><li>Besserer Verbraucherkontext für mitarbeitergestützte Interaktionen wie Support- und Vertriebserlebnisse. Mithilfe der Profil-Suche nach Experience Platformen können Kundendienstmitarbeiter mehr Kontexte erhalten, wie z. B. Einkäufe in letzter Zeit, Interaktionen mit Kampagnen, Eigenschaften, Mitgliedschaften in Audiencen und andere Attribute und Einblicke, die im Echtzeit-Kundenkonto gespeichert werden.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Grundzüge der Aktivierung für Audience und Profil

* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)

### Guardrail-Diagramm

<img src="assets/activation_guardrails.svg" alt="Guardrail-Diagramm für die Aktivierung der Audience und des Profils" style="border:1px solid #4a4a4a" />



### Leitlinien für die Segmentbewertung und -Aktivierung

| Segmenttyp | Anwendungsfälle | Häufigkeit | Durchsatz | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) | Aktivierung Nutzlast |
|--------------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Edge-Segmentierung | Web-/Mobile-Personalisierung (siehe Seite/Nächste Seite) | Die Edge-Segmentierung befindet sich derzeit in der Betaphase und ist noch nicht allgemein verfügbar. | - | Etwa 100 Millisekunden | Zielgruppe und Journey Optimizer:<ul><li>Direkt in derselben Personalisierungsanfrage verfügbar.</li></ul>Cookie-basierte Ziele:<ul><li>Verfügbar für Entscheidungen über die nächsten Seiten.</li></ul> | Edge Profil Lookups (Zielgruppe und Journey Optimizer):<ul><li>Audiencen</li><li>Profil-Attribute</li></ul>Cookie-basierte Ziele:<ul><li>Audiencen</li></ul> |
| Streaming-Segmentierung | Trigger-basiertes Marketing (Streaming) | Jedes Mal, wenn ein neues Streaming-Ereignis oder -Datensatz in das Echtzeit-Profil eines Kunden aufgenommen wird und die Segmentdefinition ein gültiges Streaming-Segment ist. <br>Anleitungen zur Segmentierungsdokumentation zu Streaming-Segmentkriterien finden Sie in der Dokumentation  [zur Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=de) | Bis zu 1500 Ereignis pro Sekunde | Etwa 5 Minuten, p95 | Streaming-Ziele:<ul><li>Etwa 1 Minute bis Audience Manager und Zielgruppe</li><li>Etwa 10 Minuten zu externen Zielen oder Mikrostapeln je nach Zielort.</li></ul>Geplante Ziele:<ul><li>Aktiviert für externe Ziele im Batch, basierend auf der geplanten Versand-Zielzeit.</li></ul> | Streaming-Ziele: <ul><li>Änderungen der Audience</li><li>Identitätswerte</li><li>Profil-Attribute</li></ul>Geplante Ziele:<ul><li>Änderungen der Audience</li><li>Identitätswerte</li><li>Profil-Attribute</li></ul> |
| Inkrementelle Segmentierung | <li>Batch-Messaging<li>Targeting von Kampagnen und Erlebnissen | Einmal pro Stunde für neue Daten, die seit der letzten inkrementellen oder Batch-Segmentbewertung in das Echtzeit-Profil des Kunden aufgenommen wurden. | Nicht anwendbar | Abhängig von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente. | Streaming-Ziele:<ul><li>Etwa 1 Minute bis Audience Manager und Zielgruppe</li><li>Etwa 10 Minuten zu externen Zielen oder Mikrostapeln je nach Zielort.</li></ul>Geplante Ziele:<ul><li>Aktiviert für externe Ziele im Batch, basierend auf der geplanten Versand-Zielzeit.</li></ul> | Streaming-Ziele: <ul><li>Änderungen der Audience</li><li>Identitätswerte</li></ul>Geplante Ziele:<ul><li>Änderungen der Audience</li><li>Identitätswerte</li><li>Profil-Attribute</li></ul> |
| Stapelsegmentierung | <ul><li>Batch-Messaging</li><li>Targeting von Kampagnen und Erlebnissen</li></ul> | Einmal pro Tag basierend auf einem vordefinierten Systemset-Plan oder manuell über API initiiert. | Nicht anwendbar | Abhängig von der Anzahl der Profil, der Größe der Profil und der Anzahl der zu evaluierenden Segmente.<ul><li>Etwa eine Stunde pro Arbeitsplatz für eine Speichergröße von bis zu 10 TB Profil</li><li>2 Stunden pro Arbeitsplatz für 10 TB bis 100 TB Profil Store Größe.</li></ul> | Streaming-Ziele:<ul><li>Etwa 1 Minute bis Audience Manager und Zielgruppe</li><li>Etwa 10 Minuten zu externen Zielen oder Mikrostapeln je nach Zielort.</li></ul>Geplante Ziele:<ul><li>Aktiviert für externe Ziele im Batch, basierend auf der geplanten Versand-Zielzeit.</li></ul> | Streaming-Ziele: <ul><li>Änderungen der Audience</li><li>Identitätswerte</li></ul>Geplante Ziele:<ul><li>Änderungen der Audience</li><li>Identitätswerte</li><li>Profil-Attribute</li></ul> |

### Leitlinien für den Austausch von Audiencen über verschiedene Anwendungen

| Audience Application Integrations | Anwendungsfälle | Häufigkeit | Durchsatz/Volumen | Latenz (Segmentbewertung) | Latenz (Segment-Aktivierung) |
|-|-|-|-|-|-|-|
| Echtzeit-Kundendatenplattform bis Audience Manager | Richten Sie die Werbung von Drittanbietern mit bekannten Profil-Audiencen ein. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | Abhängig vom Segmentierungstyp - siehe oben Tabelle mit Segmentierungsgarantien. | <ul><li>Innerhalb von Minuten nach Abschluss der Segmentbewertung.</li><li>Die anfängliche Audience der Konfigurationssynchronisierung zwischen RTCDP und AAM dauert etwa 4 Stunden.</li><li>Alle während der 4-Stunden-Audience durchgeführten Mitgliedschaften werden als &quot;bestehende&quot;Audiencen in AAM für den nachfolgenden Stapelsegmentierungsauftrag geschrieben.</li></ul> |
| Adobe Analytics bis Audience Manager | Richten Sie die Werbung von Drittanbietern mit detaillierten verhaltensbasierten Audiencen ein. |  | Standardmäßig können für jede Adobe Analytics Report Suite maximal 75 Audiencen freigegeben werden. Wenn eine Audience Manager-Lizenz verwendet wird, gibt es keine Beschränkung. |  |  |
| Adobe Analytics to Real-time Customer Data Platform | Aktuell nicht verfügbar. | Derzeit nicht verfügbar | Derzeit nicht verfügbar | Derzeit nicht verfügbar | Derzeit nicht verfügbar |


### Aktivieren von Attributen und Identitäten

* [!UICONTROL Die Echtzeit-Kundendatenplattform ] kann Audiencen-Mitgliedschaften sowie Attribut- und Identitätsänderungen aktivieren, die für Profil auftreten, die zu einer Aktivierung gehören. Wenn Sie Attribute oder Identitäten aktivieren möchten, müssen Sie ein globales Segment definieren, das alle Profil enthält, an die Attribute und Identitätsaktualisierungen gesendet werden. An diesem Punkt können Sie das Segment und die gewünschten Attribute auswählen, die im Rahmen der Zielkonfiguration aktiviert werden sollen.
* Beachten Sie, dass Batch-Ziele keine Aktivierung von Ereignissen unterstützen, die nur mit Attributen geändert werden. Vollständige oder inkrementelle Audiencen-Mitgliedschaften können zur Aktivierung zusammen mit den ausgewählten Attributen gesendet werden. Sie können jedoch keine Ereignis mit Nur-Attribut-Änderungen über Batch-Ziele aktivieren.

### Aktivieren von Stapelsegmenten in Streaming-Ziele

* Die Aktivierung des Stapelsegments auf Streaming-Ziele wird unterstützt. Stapelsegmentaufträge platzieren Meldungen in der Pipeline, sobald der Segmentauftrag für die Streaming-Aktivierung abgeschlossen ist

### Aktivieren von Streaming-Segmenten an Batch-Ziele

* Die Streaming-Segmentzielsetzung wird unterstützt. Der Stapelziel-Plan exportiert Profil-Segmentmitgliedschaften basierend auf dem Batch-Zielplan. Dies umfasst sowohl Segmentmitgliedschaften, die über Streaming- als auch Batch-Methoden bestimmt werden.

### Aktivieren von Erlebnis-Ereignissen

* Die Aktivierung von unverarbeiteten Erlebnis-Ereignissen wird nicht unterstützt. Zum Aktivieren gegen Erlebnis-Ereignis muss ein Segment mit den erforderlichen Ereignis-Regeln erstellt werden, die die Erlebnis-Logik einschließen oder ausschließen. Dadurch wird ein Segment erstellt, das für Erlebnis-Ereignis definiert wird, und die Segmentmitgliedschaft kann als Proxy zur Aktivierung von unformatierten Erlebnis-Ereignissen aktiviert werden. Erwägen Sie auch, [!UICONTROL Serverseite starten] zu verwenden, um über SDK erfasste unverarbeitete Erlebnis-Ereignis zu aktivieren.


## Verwandte Blog-Posts

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
