---
title: Customer Journey Analytics mit Real-time Customer Data Platform-Blueprint
description: Vereinheitlichen und analysieren Sie in Customer Journey Analytics Daten und Kundenverhalten von der gesamten Customer Journey und veröffentlichen Sie in CJA identifizierte Zielgruppe in RTCDP.
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 94%

---

# Customer Journey Analytics mit Real-time Customer Data Platform-Blueprint

Erstellen und veröffentlichen Sie Zielgruppen, die in Customer Journey Analytics (CJA) identifiziert wurden, im Echtzeit-Kundenprofil in Adobe Experience Platform, um Zielgruppenbestimmung und Personalisierung durchzuführen. Ideal zur Erstellung von Zielgruppen mithilfe historischer Daten oder von präziseren Zielgruppen aus granularer Filterung und berechneten Feldern in Customer Journey Analytics.

## Handbuch zur Veröffentlichung von Customer Journey Analytics-Zielgruppen

In der folgenden Dokumentation finden Sie Anleitungen zur Implementierung und Konfiguration nach der Veröffentlichung von Zielgruppen von Customer Journey Analytics in Real-time Customer Data Platform. [Dokumentation](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=de)

## Architektur für die Blueprints zu Customer Journey Analytics

![Architekturdiagramm](assets/CJA.svg){zoomable="yes"}

## Leitliniendiagramm für die Blueprints zu Customer Journey Analytics

* Detaillierte Leitlinien und End-to-End-Latenzen finden Sie im Abschnitt [Leitlinien zur Implementierung](../experience-platform/deployment/guardrails.md)

![Leitliniendiagramm](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Häufig gestellte Fragen

* Wird, wenn für ein von CJA gesendetes Profil kein entsprechendes Profil in RTCDP existiert, ein neues Profil erstellt oder werden Zielgruppen in CJA nur für bereits vorhandene Profile aufgezeichnet? Ja, ein neues Profil wird erstellt. Wenn die RTCDP-Implementierung nur für bekannte Kunden verwendet werden soll, müssen die CJA-Zielgruppenregeln so formuliert werden, dass ausschließlich nach Profilen mit bekannten Identitäten gefiltert wird. So wird sichergestellt, dass sich die Zahl der RTCDP-Profile nicht durch anonyme Profile erhöht, wenn dies nicht gewünscht ist.

* Welche Identitäten übermittelt CJA? CJA übermittelt sämtliche Identitäten, die während der CJA-Konfiguration als „Personen-ID“ konfiguriert wurden.

* Was wird als primäre Identität festgelegt? Die Identität, die der Benutzer beim Einrichten von Customer Journey Analytics als primäre „Personen“-ID ausgewählt hat.

* Verarbeitet der Identitäts-Service auch die CJA-Nachrichten? Kann CJA also einem Profilidentitätsdiagramm durch Zielgruppenfreigabe Identitäten hinzufügen? Nein, der Identitäts-Service verarbeitet die CJA-Nachrichten nicht.