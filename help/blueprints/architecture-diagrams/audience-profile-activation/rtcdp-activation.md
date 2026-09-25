---
title: Adobe Real-Time CDP-Aktivierung
description: Architekturreferenz zum Aktivieren von Zielgruppen und Profildaten von Adobe Real-Time CDP für Werbung, Social Media, Cloud-Speicher und Unternehmensziele.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%
---
# Adobe Real-Time CDP-Aktivierung

Diese Architektur zeigt, wie Adobe [!DNL Real-Time Customer Data Platform] ([!DNL Real-Time CDP]) Zielgruppen- und Profildaten durch Streaming- und Batch-Datenflüsse für Werbung, Social Media, Cloud-Speicher und Unternehmensziele aktiviert.

## Zielgruppe und Profilaktivierung

Die Architektur veranschaulicht den freigegebenen Aktivierungspfad von [!DNL Real-Time CDP] Zielgruppen und Profilen zu den Zielanwendungen. Dazu gehören die Zielaktivierung für Werbe- und Social-Media-Plattformen sowie Unternehmensziele, die für Speicher-, Analyse- und nachgelagerte Anwendungs-Workflows verwendet werden.

![Adobe Real-Time CDP-Zielgruppe und Profilaktivierungsarchitektur](assets/real_time_cdp_activation.png){width="1000" zoomable="yes"}

## Unterstützte Anwendungsfallmuster

Die obige Architektur unterstützt die folgenden Anwendungsfallmuster:

- [Zielgruppenaktivierung für Ziele](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) - Aktivieren Sie ausgewertete Zielgruppen für Werbung, Social Media, Cloud-Speicher, CRM und andere Unternehmensziele.
- [Anonyme Besucher-Web-Personalisierung](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) - Unterstützt die Aktivierung von Zielgruppen und die profilbasierte Personalisierung über digitale Kanäle hinweg.

## Primäre Datenflüsse und Integrationspunkte

- Nehmen Sie Kundendaten aus verschiedenen Quellen in [!DNL Real-Time CDP] auf.
- Vereinheitlichen von Identitäts- und Profilattributen in [!DNL Real-Time Customer Profile].
- Bewerten Sie Profile in Zielgruppen zur Aktivierung.
- Streamen oder Batch-Zielgruppen- und Profiländerungen an Werbe-, Social-Media-, Cloud-Speicher- und Unternehmenszielen.
- Verwenden Sie aktivierte Profil- und Zielgruppendaten in nachgelagerten Marketing-, Verkaufs-, Support-, Analytics- und Personalisierungs-Workflows.

## Weitere Informationen

- [Adobe Real-Time CDP-Ziele](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Zielgruppen für Ziele aktivieren](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Adobe Real-Time CDP-Leitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview)
