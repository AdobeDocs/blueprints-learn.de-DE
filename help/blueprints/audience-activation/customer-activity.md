---
title: Hub-Blueprint zur Aktivität von Kunden
description: '[!UICONTROL Echtzeit-] Kundenprofilen, um Kontext für Support und Vertrieb durch Mitarbeiter bereitzustellen.'
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: f217273f29e1091a121a60c2a19d71190df0f0ff
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Hub-Blueprint zur Aktivität von Kunden

Hub-Blueprint für Kunden-Aktivitäten zeigt, wie externe Anwendungen auf das [!UICONTROL Echtzeit-Kundendienstprogramm ] von Adobe Experience Platform zugreifen können.

Externe Anwendungen können mit einer API-GET auf Profil zugreifen. Attribute, Ereignis, Segmentmitgliedschaften und modellgesteuerte Funktionen, die im Profil gespeichert sind, können dann in diesen externen Anwendungen ohne Adobe verwendet werden.

Mit dieser Funktion können Sie einen umfangreichen Kontext aufdecken, wenn ein Kunde Ihr Call-Center anruft. Support-Mitarbeiter könnten z. B. den Lebenszeitwert des Kunden, die Tendenz zur Kehrtwende oder die Exposition gegenüber Marketing-Kampagnen erkennen. Vertriebsmitarbeiter können auch von mehr Kontext oder Einblick in ihren Kunden profitieren.

>[!NOTE]
>
>Die aktuelle Latenz, die von der Profil Lookup API unterstützt wird, beträgt etwa 500 Millisekunden, sodass dieser Ansatz nicht für die Integration des Profils mit Entscheidungsmaschinen in Echtzeit geeignet ist, wie z. B. der Personalisierung von Websites oder Mobilgeräten mit derselben Seite.

## Anwendungsfälle

* Stellen Sie einen tieferen Kontext für den Kunden bei von Agenten unterstützten Interaktionen bereit, z. B. bei Support- und Verkaufserlebnissen. Mithilfe der Profil-Suche nach der Experience Platform können Kundendienstmitarbeiter mehr Kontexte erhalten, z. B. Einkäufe in letzter Zeit, Interaktionen mit Kampagnen, Tendenzen, Mitgliedschaften in Audiencen und andere Attribute und Einblicke, die im Echtzeit-Kundenkonto gespeichert werden.

## Architektur

<img src="assets/cah.svg" alt="Referenzarchitektur für das Hub-Konzept für die Aktivität von Kunden" style="border:1px solid #4a4a4a" />

## Guardraht

* [Leitlinien für  [!UICONTROL Echtzeit-Kundenprofildaten ] in Echtzeit](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementierungsschritte

1. Konfigurieren von Datensätzen und Schemas.
1. Konfigurieren Sie [!UICONTROL Echtzeit-Profil]: konfigurieren Sie das Schema und den Datensatz für [!UICONTROL Echtzeit-Kundenkonto] und richten Sie eine Richtlinie und Identitäten für die Zusammenführung ein.
1. Daten in Plattform einbeziehen und auf [!UICONTROL Echtzeit-Kundenkonto] verarbeiten.
1. Verwenden Sie die Entitäts-API zum Nachschlagen eines Profil-Attributs, entweder von der Datensatzentität oder der Experience Ereignis-Entität.

## Verwandte Dokumentation

* [Adobe Experience Platform Aktivierung - Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL Dokumentation ] zum Kundenprofil in Echtzeit](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [Profil Guardrads](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Profil Lookup-API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
