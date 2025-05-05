---
title: B2B-Kontoaktivierung für Advertising-Ziele und Dateiziele
description: Verwenden Sie die Account-basierte Interaktion, um Audiences zu erstellen und sie über Ziele anzusprechen.
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: c8538554c936bb1cb95c39fcab4597b1321f1688
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 4%

---

# B2B-Kontoaktivierung für Werbeziele und Dateiziele

Account-Based Engagement ermöglicht es B2B-Marketing-Experten, Zielgruppen von Konten (d. h. Unternehmenslisten) zu erstellen und diese Unternehmen über Ziele wie LinkedIn anzusprechen, die Listen von Unternehmen als Eingabe akzeptieren oder zur Zielsetzung von Cloud-Speicher für Targeting und Verkaufsförderung in exportieren.

## Anwendungsfälle

Durch Account-basierte Interaktion können Marketing-Experten drei wichtige Anwendungsfälle erschließen:

* **Lücken in der Einkaufsgruppe schließen:** Ein Marketer kann auf Konten werben, auf denen er noch keine Kontakte für die CMO- oder CIO-Rollen hat. Sie können zunächst eine Audience von Accounts ohne Kontakt mit dem Titel „CMO“ oder „CIO“ erstellen und dann die Audience auf LinkedIn aktivieren. Innerhalb des Ziels, LinkedIn, können sie dann eine Kampagne starten, die auf diese Zielgruppe und bestimmte Personen mit „CMO“- oder „CIO“-Stellenbezeichnungen abzielt, um diese neuen Kontakte zu erreichen und die Vorteile ihrer Angebote hervorzuheben.
* **Upsell oder Crosssell an andere Abteilungen eines Unternehmens, das ein bestehender Kunde ist:** Ein Marketing-Experte kann eine Account-Zielgruppe erstellen, die Produkt X vor 3 bis 9 Monaten gekauft hat, aber noch kein Produkt Y besitzt. Anschließend können sie aktiviert und die Vorteile von Produkt Y für diese Zielgruppe hervorgehoben werden.
* **Targeting von Unternehmen, die konkurrierende Produkte verwenden:** Ein Marketing-Experte kann Konten vermarkten, um die Produkte eines Konkurrenten zu verdrängen, selbst wenn er bei diesen Konten keine Kontakte hat. Sie können eine Zielgruppe von Konten erstellen, die auf Partnerdaten basiert, aus denen die Eigentümerschaft oder Nutzung des Produkts eines Mitbewerbers hervorgeht, und dann über LinkedIn aktivieren, um Kontakte bei Zielkonten für die Erweiterung zu beschaffen.

## Programme

* Real-time Customer Data Platform B2B Edition

## Integrationsmuster

* B2B-Datenquellen (Marketo, Salesforce usw.) -> Real-time Customer Data Platform B2B edition -> Ziele.
* Verschiedene B2B-Datenquellen können verwendet werden, um Account-, Lead-, Opportunity- und Personendaten der B2B edition von Real-time Customer Data Platform zuzuordnen.

## Architektur

![Referenzarchitektur für B2B-Konto-Audience Activation-Blueprint](assets/b2b-blueprint-account-audience-activation.png)

## Konten-Audience-Ziele

* (Firmen) Abgestimmte Zielgruppen in LinkedIn
* Cloud-Speicher-Ziele
   * Azure Data Lake
   * Data Landing Zone
   * SFTP
   * Azure Blob
   * AWS S3

## Leitlinien

* Begrenzt auf 50 Kontosegmente pro Sandbox.
* Bewertung der Batch-Segmentierung.
   * Wird automatisch alle 24 Stunden nach Abschluss der Batch-Audience-Ausführung und der Profilexportvorgänge ausgewertet.
   * Keine Unterstützung für Edge-, Streaming- oder Ad-hoc-Auswertungen.
* Kontoattribute sind für den Export verfügbar.
* Ereignisse von Personen.
   * Bis zu 30 Tage Ereignis-Lookback, keine Sortierung von Ereignis-Eigenschaften.
   * UND/ODER werden unterstützt (sodass Sie sagen können: „A und B müssen passieren,“  aber man kann nicht sagen „A muss 3 Tage vor B passieren„).
* Bei Cloud-Speicher-Zielen unterstützt der Exportzeitplan die Option „Nach der Segmentevaluierung“.
* [Leitplanken für B2B-Profile und ](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Implementierungsschritte für Real-time Customer Data Platform B2B edition, Erstellung und Aktivierung von Konto-Zielgruppen

* Implementierungsschritte für Real-time Customer Data Platform B2B edition finden Sie in der Dokumentation [Erste Schritte mit Real-time Customer Data Platform B2B Editions](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial) .
* Schritte zum Erstellen von Konto-Zielgruppen finden Sie in der Dokumentation [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/account-audiences) .
* Die Schritte zum Account-Audience Activation finden Sie in der [Activate Account Audiences](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-account-audiences)-Dokumentation.
   * Erforderliche Zuordnung für das Ziel [Firmen) mit LinkedIn Matched Audiences](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Überlegungen bei der Implementierung

Für von linkedIn übereinstimmende Zielgruppen gelten einige Anforderungen, darunter die Mindestgröße der Zielgruppe von 300 übereinstimmenden Mitgliedern. Wenn die für das Ziel der verknüpften übereinstimmenden Zielgruppe des Unternehmens aktivierte Zielgruppe des Kontos die Anforderung nicht erfüllt, muss die Zielgruppendefinition geändert werden, um die Zielgruppengröße für den Start einer LinkedIn-Kampagne zu erhöhen.

## Verwandte Dokumentation

* [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Tutorial zum Erstellen und Aktivieren von Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [Konto-Zielgruppen erstellen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/ui/account-audiences)
* [Kontozielgruppen aktivieren](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn-Ziel-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)
