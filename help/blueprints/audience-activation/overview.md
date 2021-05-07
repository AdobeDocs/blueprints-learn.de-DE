---
title: Aktivierung von Zielgruppen und Profilen
description: Stellen Sie mit Real-Time Customer Data Platform zielgruppenaktivierte und profilorientierte Kundenerlebnisse bereit.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 5471d9c0f6fdef6fbac72d5d35f32353ea5a5ee8
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 91%

---


# Aktivierung von Zielgruppen und Profilen

Die Zielgruppen- und Profilaktivierung ist der Schlüssel zum Erfolg in der Welt des Data-driven Marketing. Allerdings orientieren sich viele Marken bei der Aktivierung noch immer zunächst am Kanal, was häufig in inkonsistenter Reichweite und Personalisierung endet.

Wenn der Kanal an erster Stelle steht, fungiert jeder Kanal als Silo, in dem Personalisierung für Kunden erfolgt, die auf diesem Kanal mit der Marke interagieren. Diese Herangehensweise spiegelt nicht die Realität wider, in der Kunden über viele verschiedene Touchpoints hinweg mit der Marke interagieren. Mit Zielgruppen- und Profilaktivierung können Marken Kundeninteraktionen über verschiedene Kanäle hinweg miteinander verknüpfen und so Content für eine zentrale Zielgruppe bereitstellen, die auf allen Kanälen aktiviert werden kann.

| Blueprint | Beschreibung | Experience Cloud-Programme |
|---|---|---|
| **[Anonyme Zielgruppenaktivierung](anonymous.md)** | <ul><li>Identifizieren Sie Zielgruppen basierend auf anonymen und verhaltensbasierten Kundendaten über Web- und Werbekanäle hinweg.</li><li>Third-Party-Zielgruppendaten können für bessere Personalisierung integriert werden.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Online-/Offline-Zielgruppenaktivierung](online-offline.md)** | <ul><li>Aktivierung für bekannte, profilbasierte Ziele, wie E-Mail-Anbieter, Social Media und Werbeziele. </li><li>Nutzung von Offline-Attributen und -Ereignissen, wie Offline-Bestellungen, Transaktionen, CRM- oder Treuedaten gemeinsam mit Online-Verhaltensdaten für Online-Targeting und -Personalisierung.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-Time Customer Data Platform]</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Zielgruppen- und Profilaktivierung für Unternehmensziele](enterprise-destinations.md)** | <ul><li>Replikation und Aktualisierung von Profil- und Zielgruppenänderungen in Unternehmensdatenspeichern für Aktivierungs- und Reporting-Anwendungsfälle. </li></ul><ul><li>Einleitung einer Verkaufs- oder Support-Aktion für Kunden durch die Benachrichtigung über eine Kundenaktion von [!UICONTROL Real-Time Customer Data Platform] an Unternehmenssysteme und -programme.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-Time Customer Data Platform]</li><li>Experience Platform Activation</li><li>Adobe Audience Manager (optional)</li></ul> |
| **[Aktivierung von Audiencen und Profilen mit Experience Cloud-Anwendungen](platform-and-applications.md)** | </ul><li>Profil und Audiencen in der Experience Platform verwalten und für Experience Cloud-Anwendungen freigeben</li><li>Erstellen und teilen Sie umfangreiche Kundensegmente und Einblicke in die Experience Platform und teilen Sie diese mit Experience Cloud-Anwendungen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-Time Customer Data Platform]</li><li>Experience Platform Aktivierung</li><li>Experience Cloud-Programme</li></ul> |
| **[Customer Activity Hub](customer-activity.md)** | <ul><li>Besserer Verbraucherkontext für mitarbeitergestützte Interaktionen wie Support- und Vertriebserlebnisse. Durch die Profilsuche in Experience Platform erhalten Mitarbeiter Kontext zum Verbraucher wie kürzlich durchgeführte Käufe, Kampagneninteraktionen, Neigungen, Zielgruppenzugehörigkeiten und andere Attribute sowie Erkenntnisse, die im Echtzeit-Kundenprofil gespeichert sind.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |



## Grundzüge der Aktivierung für Audience und Profil

* [Richtlinien für Profile und Segmentierung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)


### Aktivieren von Attributen und Identitäten

* [!UICONTROL Real-Time Customer Data Platform] kann Zielgruppenzugehörigkeiten sowie Attribut- und Identitätsänderungen für Profile aktivieren, die zu Segmenten gehören, die zur Aktivierung ausgewählt sind. Wenn Sie Attribute oder Identitäten aktivieren möchten, müssen Sie ein globales Segment definieren, das alle Profile enthält, an die Attribut- und Identitätsaktualisierungen gesendet werden. An diesem Punkt können Sie das Segment und die gewünschten Attribute auswählen, die im Zuge der Zielkonfiguration aktiviert werden sollen.
* Beachten Sie, dass Batch-Ziele nicht die Aktivierung von Ereignissen unterstützen, bei denen nur Attribute geändert werden. Vollständige oder inkrementelle Zielgruppenzugehörigkeiten können zur Aktivierung zusammen mit den ausgewählten Attributen gesendet werden. Sie können jedoch keine Ereignisse über Batch-Ziele aktivieren, bei denen nur Attribute geändert werden.

### Aktivieren von Batch-Segmenten für Streaming-Ziele

* Die Aktivierung von Batch-Segmenten für Streaming-Ziele wird unterstützt. Bei Batch-Segmentvorgängen werden Nachrichten in der Pipeline platziert, nachdem der Segmentvorgang für die Streaming-Aktivierung abgeschlossen ist.

### Aktivieren von Streaming-Segmenten für Batch-Ziele

* Die Streaming-Segmentzielsetzung wird unterstützt. Profil-Segmentzugehörigkeiten werden gemäß dem Batch-Ziel-Zeitplan exportiert. Dies umfasst Segmentzugehörigkeiten, die sowohl über Streaming- als auch über Batch-Methoden bestimmt werden.

### Aktivieren von Erlebnisereignissen

* Die Aktivierung von unverarbeiteten Erlebnisereignissen wird nicht unterstützt. Zum Aktivieren für Erlebnisereignisse muss ein Segment mit den erforderlichen Regeln erstellt werden, die die Erlebnisereignis-Logik ein- oder ausschließen. Dadurch wird ein Segment erstellt, das für Erlebnisereignisse definiert wird. Die Segmentzugehörigkeit kann dann als Proxy zur Aktivierung von unverarbeiteten Erlebnisereignissen aktiviert werden. Sie können auch [!UICONTROL Launch Server Side] verwenden, um über das SDK erfasste unverarbeitete Erlebnisereignisse zu aktivieren.


## Verwandte Blog-Posts

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
