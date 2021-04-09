---
title: Datenerfassung und -vorbereitung
description: Dieser Entwurf zeigt alle Methoden, mit denen Daten in Adobe Experience Platform erfasst und vorbereitet werden können.
solution: Experience Platform, Data Collection
kt: 7204
thumbnail: null
exl-id: 5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: cbc9c48041d00c45fc75d3bb65bd865f1f7ecc9c
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Datenerfassung und -vorbereitung

Die Datenerfassung und -vorbereitung umfasst alle Methoden, mit denen Daten vorbereitet und in Adobe Experience Platform aufgenommen werden können. Neben der Möglichkeit, Daten an das Adobe Experience Platform Edge Network zu erfassen und anschließend Daten über die Seitenweiterleitung an Unternehmensziele zu übermitteln.

Die Datenvorbereitung umfasst die Zuordnung von Quelldaten zum Experience Data Model (XDM)-Schema. Dazu gehören auch die Durchführung von Datentransformationen, einschließlich Datumsformatierung, Feldteilungs-/Verkettungs-/Konvertierungen und das Verbinden/Zusammenführen/erneute Keying von Datensätzen. Die Datenvorbereitung hilft bei der Vereinheitlichung von Kundendaten, um eine aggregierte/gefilterte Analyse bereitzustellen, einschließlich Berichte oder der Vorbereitung von Daten für die Zusammenstellung/Datenwissenschaft/Aktivierung von Profilen.

| Blueprint | Beschreibung | Experience Cloud-Anwendungen |
|---|---|---|
| **[Datenaufbereitung und Ingestion](ingestion.md)** | <ul><li>Datenaufbereitung und Ingestion Blueprint umfassen alle Methoden, mit denen Daten in Adobe Experience Platform vorbereitet und aufgenommen werden können.</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[Serverseitige Erfassung von Unternehmensdaten](server-side-collection.md)** | <ul><li>Aktivieren Sie bekannte Profil-basierte Ziele wie E-Mail-Anbieter, soziale Netzwerke und Werbeziele. </li><li>Verwenden Sie Offline-Attribute und Ereignis wie Offline-Bestellungen, Transaktionen, CRM-Daten oder Treuedaten zusammen mit Online-Verhalten für Online-Targeting und Personalisierung.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Echtzeit-Kundendatenplattform]</li><li>Adobe Audience Manager (optional)</li></ul> |
