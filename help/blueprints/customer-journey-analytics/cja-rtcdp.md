---
title: Customer Journey Analytics mit Real-time Customer Data Platform   Blueprint
description: Vereinheitlichen und analysieren Sie in Customer Journey Analytics Daten und Kundenverhalten von der gesamten Customer Journey und veröffentlichen Sie in CJA identifizierte Zielgruppe in RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 2d7d2fff6c430b66e4a2935d4c68b5a8b9ecfae2
workflow-type: ht
source-wordcount: '398'
ht-degree: 100%

---

# Customer Journey Analytics mit Real-time Customer Data Platform   Blueprint

Erstellen und veröffentlichen Sie Zielgruppen, die in Customer Journey Analytics (CJA) identifiziert wurden, im Echtzeit-Kundenprofil in Adobe Experience Platform, um Zielgruppenbestimmung und Personalisierung durchzuführen. Ideal zur Erstellung von Zielgruppen mithilfe historischer Daten oder von präziseren Zielgruppen aus granularer Filterung und berechneten Feldern in Customer Journey Analytics.

## Handbuch zur Veröffentlichung von Customer Journey Analytics-Zielgruppen

In der folgenden Dokumentation finden Sie Anleitungen zur Implementierung und Konfiguration nach der Veröffentlichung von Zielgruppen von Customer Journey Analytics in Real-time Customer Data Platform. [Dokumentation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=de)

## Architektur für die Blueprints zu Customer Journey Analytics

![Architekturdiagramm](assets/CJA.svg){zoomable=&quot;yes&quot;}

## Leitliniendiagramm für die Blueprints zu Customer Journey Analytics

* Detaillierte Leitlinien und End-to-End-Latenzen finden Sie im Abschnitt [Leitlinien zur Implementierung](../experience-platform/deployment/guardrails.md)

![Leitliniendiagramm](../experience-platform/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Häufig gestellte Fragen

* Wird, wenn für ein von CJA gesendetes Profil kein entsprechendes Profil in RTCDP existiert, ein neues Profil erstellt oder werden Zielgruppen in CJA nur für bereits vorhandene Profile aufgezeichnet? Ja, ein neues Profil wird erstellt. Wenn die RTCDP-Implementierung nur für bekannte Kunden verwendet werden soll, müssen die CJA-Zielgruppenregeln so formuliert werden, dass ausschließlich nach Profilen mit bekannten Identitäten gefiltert wird. So wird sichergestellt, dass sich die Zahl der RTCDP-Profile nicht durch anonyme Profile erhöht, wenn dies nicht gewünscht ist.

* Übermittelt CJA die Zielgruppendaten als Pipeline-Ereignisse oder als Flatfile, das auch an den Data Lake gesendet wird? CJA-Zielgruppen werden über die Pipeline an den RTCDP-Profil-Service gestreamt, die Daten werden jedoch auch als Datensatz im Data Lake gespeichert.

* Welche Identitäten übermittelt CJA? CJA übermittelt sämtliche Identitäten, die während der CJA-Konfiguration als „Personen-ID“ konfiguriert wurden.

* Was wird als primäre Identität festgelegt? Die Identität, die der Benutzer beim Einrichten von Customer Journey Analytics als primäre „Personen“-ID ausgewählt hat.

* Verarbeitet der Identitäts-Service auch die CJA-Nachrichten? Kann CJA also einem Profilidentitätsdiagramm durch Zielgruppenfreigabe Identitäten hinzufügen? Nein, der Identitäts-Service verarbeitet die CJA-Nachrichten nicht.

## Verwandte Blog-Posts

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184)
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17)
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1)
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281)
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34)
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9)
