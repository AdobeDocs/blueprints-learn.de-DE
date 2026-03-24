---
title: Anwendungsfälle für Technologien
description: Erfahren Sie, wie Technologieunternehmen Adobe Experience Platform zur Vereinheitlichung der Datenerfassung, Weiterleitung von Ereignissen in Echtzeit und zur Bereitstellung von Analysen und Aktivierungen für digitale Produkte verwenden.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 77908fd8a9f4309cbe66063cd33f065424697e55
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Anwendungsfälle für Technologien

Technologieunternehmen verwenden Adobe Experience Platform, um die Datenerfassung aus Web-, Mobile- und Produktoberflächen zu zentralisieren und Echtzeit-Ereignisse an die Analyse-, Data Warehouse- und Aktivierungsziele zu verteilen, die ihre Produkte und Marketing-Programme unterstützen. Durch die Konsolidierung der Ereigniserfassung am Edge reduzieren Technologie-Teams die Client-seitige Komplexität, verbessern die Datenqualität und stellen sicher, dass alle nachgelagerten Systeme konsistente Verhaltensdaten aus einer einzigen, maßgeblichen Quelle erhalten.

## Echtzeit-Ereignisweiterleitung

Leiten Sie über Edge Network erfasste Verhaltensereignisse in Echtzeit zur Anreicherung und Aktivierung an Analysen, Data Warehouses und Partnerplattformen von Drittanbietern weiter. Durch die Zentralisierung der Ereigniserfassung am Edge und die Weiterleitung an mehrere Ziele wird der Client-seitige Tag-Overhead reduziert, die Datenqualität verbessert und sichergestellt, dass alle nachgelagerten Systeme konsistente Ereignisdaten aus einer einzigen autorisierenden Quelle erhalten.

### Auswirkung auf den Betrieb

Technologieunternehmen, die die Ereignisweiterleitung in Echtzeit implementieren, reduzieren die Client-seitige Tag-Belastung und den damit verbundenen Leistungsaufwand und verbessern gleichzeitig die Konsistenz der Ereignisdaten über Analytics-, Data Warehouse- und Aktivierungsziele hinweg. Die Server-seitige Weiterleitung reduziert außerdem die Seitengewichtung und verbessert die Ladeleistung, was direkt den Benutzererlebnismetriken zugute kommt.

### Implementieren

Verwenden Sie das [Ereignisweiterleitung](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)-Muster, um von Adobe Experience Platform Web SDK erfasste Ereignisse über Edge Network zu konfigurierten Server-seitigen Zielen zu leiten. Dies ist das richtige Muster, wenn das Ziel die Server-zu-Server-Ereignisverteilung von einem einzigen Sammlungspunkt ist - anstatt separate Tags für jedes Ziel auf der Client-Seite zu verwalten, was die Seitengewichtung erhöht und zu Dateninkonsistenz über Systeme hinweg führt.

### Technische Überlegungen

- Die Edge Network-Ereignisweiterleitung erfordert die Migration der Ereigniserfassung zu Adobe Experience Platform Web SDK oder Mobile SDK. Vorhandene Tag-basierte Implementierungen müssen auf Kompatibilität geprüft werden, bevor Weiterleitungsziele konfiguriert werden.
- Weiterleitungsregeln müssen so konfiguriert werden, dass nur die für jedes Ziel erforderlichen Felder gesendet werden. So wird vermieden, dass vollständige XDM-Payloads an Ziele weitergeleitet werden, die nur eine kleine Untergruppe von Feldern benötigen, da dies die Kosten für die Datenübertragung erhöht und zu Compliance-Risiken führt.
- Ziel-Connectoren müssen Fehler ordnungsgemäß beheben. Ereignisweiterleitungs-Pipelines sollten eine Wiederholungslogik und Warnhinweise für Ziele implementieren, die nicht mehr verfügbar sind, um Datenverlust bei Ausfällen zu verhindern.
- Data-Governance-Richtlinien müssen für jedes Weiterleitungsziel überprüft werden, um sicherzustellen, dass die am Edge erfassten Benutzereinverständnisvoreinstellungen in der Weiterleitungskonfiguration berücksichtigt werden.
