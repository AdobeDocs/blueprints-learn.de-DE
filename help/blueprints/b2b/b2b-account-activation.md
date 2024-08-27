---
title: B2B-Kontoaktivierung für Advertising-Ziele und Dateiziele
description: Verwenden Sie die kontobasierte Interaktion, um Zielgruppen zu erstellen und über Ziele anzusprechen.
solution: Real-Time Customer Data Platform
source-git-commit: 074edca2f061459935d5f8b5e59e8cbd69b0fe4f
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 5%

---

# Aktivierung des B2B-Kontos für Werbeziele und Dateiziele

Mit der kontobasierten Interaktion können B2B-Marketer Zielgruppen von Konten erstellen (d. h. Unternehmenslisten) und diese Unternehmen über Ziele wie LinkedIn ansprechen, die Unternehmenslisten als Eingabe- oder Exportlisten für Cloud-Speicher akzeptieren, um Zielgruppen zu bestimmen und Zielgruppen für den Vertrieb zu erreichen.

## Anwendungsfälle

Mithilfe der kontobasierten Interaktion können Marketing-Experten drei wichtige Anwendungsfälle entsperren:

* **Füllen Sie die Lücken in der Einkaufsgruppe:** Ein Marketing-Experte kann auf Konten werben, auf denen er noch keine Kontakte für die CMO- oder CIO-Rollen hat. Sie können zunächst eine Audience von Konten erstellen, ohne mit dem Titel &quot;CMO&quot;oder &quot;CIO&quot;in Kontakt zu treten, und dann die Audience in LinkedIn aktivieren. Innerhalb des Ziels LinkedIn können sie dann eine Kampagne starten, die auf diese Zielgruppe und bestimmte Personen mit den Titeln &quot;CMO&quot;oder &quot;CIO&quot;abzielt, um diese neuen Kontakte zu erreichen und die Vorteile ihrer Angebote hervorzuheben.
* **Upsell oder Crosssell in andere Abteilungen eines Unternehmens, das ein bestehender Kunde ist:** Ein Marketing-Experte kann eine Konto-Zielgruppe erstellen, die vor 3 bis 9 Monaten Produkt X gekauft hat, aber noch kein Produkt Y besitzt. Anschließend können sie aktivieren und die Vorteile von Produkt Y für diese Zielgruppe hervorheben.
* **Unternehmen ansprechen, die konkurrierende Produkte verwenden:** Ein Marketing-Experte kann Konten vermarkten, um die Produkte eines Konkurrenten zu vermarkten, selbst wenn auf diesen Konten keine Kontakte bestehen. Sie können eine Zielgruppe von Konten basierend auf Partnerdaten erstellen, die das Eigentum oder die Verwendung des Produkts eines Konkurrenten zeigen, und dann über LinkedIn aktivieren, um Kontakte über Zielkonten für die Erweiterung zu erhalten.

## Programme

* Real-time Customer Data Platform B2B Edition

## Integrationsmuster

* B2B: Datenquellen (Marketo, Salesforce usw.) -> Real-time Customer Data Platform B2B Edition -> Ziele.
* Verschiedene B2B-Datenquellen können verwendet werden, um Konto-, Lead-, Opportunity- und Personendaten der B2B Edition von Real-time Customer Data Platform zuzuordnen.

## Architektur

![Referenzarchitektur für B2B-Konto-Audience Activation-Blueprint](assets/b2b-blueprint-account-audience-activation.png)

## Zielgruppenziele für Konten

* (Unternehmen) LinkedIn Matched Audiences
* Cloud-Speicher-Ziele
   * Azure Data Lake
   * Data Landing Zone
   * SFTP
   * Azure Blob
   * AWS S3

## Leitlinien

* Auf 50 Kontosegmente pro Sandbox begrenzt.
* Batch-Segmentierungsbewertung.
   * Automatisch alle 24 Stunden nach Abschluss der Batch-Zielgruppenausführung und der Profilexportvorgänge ausgewertet.
   * Keine Unterstützung für Edge-, Streaming- oder Ad-hoc-Bewertungen.
* Kontoattribute sind für den Export verfügbar.
* Ereignisse von Menschen.
   * Bis zu 30 Tage nach Ereignis-Lookback, keine Reihenfolge der Ereigniseigenschaften.
   * UND/ODER werden unterstützt (Sie können also sagen, &quot;A und B müssen stattfinden&quot;,  aber Sie können nicht sagen &quot;A muss 3 Tage vor B geschehen&quot;).
* Bei Cloud-Speicher-Zielen unterstützt der Exportplan die Option &quot;Nach der Segmentauswertung&quot;.
* [Limits für B2B-Profile und Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Implementierungsschritte für Real-time Customer Data Platform B2B Edition, Erstellung von Konto-Zielgruppen und Aktivierung

* Informationen zu den Implementierungsschritten von Real-time Customer Data Platform B2B Edition finden Sie in der Dokumentation [Erste Schritte mit Real-time Customer Data Platform B2B Editiond](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial) .
* Informationen zu den Schritten zur Erstellung von Kontozielgruppen finden Sie in der Dokumentation zu [Kontozielgruppen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences) .
* Informationen zum Audience Activation von Konten finden Sie in der Dokumentation zu [Kontozielgruppen aktivieren](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences) .
   * Erforderliche Zuordnung für das Ziel &quot;[(Unternehmen) LinkedIn Matched Audiences&quot;](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Überlegungen bei der Implementierung

LinkedIn-übereinstimmende Zielgruppen haben einige Anforderungen, darunter die minimale Zielgruppengröße von 300 passenden Mitgliedern. Wenn die Zielgruppe des Kontos, das für das verknüpfte Zielgruppen-Ziel des Unternehmens aktiviert wurde, die Anforderung nicht erfüllt, muss die Zielgruppendefinition geändert werden, um die Zielgruppengröße zu erhöhen und eine LinkedIn-Kampagne zu starten.

## Verwandte Dokumentation

* [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Tutorial zum Erstellen und Aktivieren der Audience von Konten-Tutorial Video](https://experienceleague.adobe.com/de/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [Erstellen von Kontozielgruppen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)
* [Kontozielgruppen aktivieren](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn Destination Connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
