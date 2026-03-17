---
title: Anwendungsfallkatalog
description: Durchsuchen Sie branchenspezifische Anwendungsfälle nach Vertikal, Reifegrad oder Implementierungsmuster, um den richtigen Ausgangspunkt für Ihren Adobe Experience Platform-Journey zu finden.
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# Anwendungsfallkatalog

Erkunden Sie branchenspezifische Anwendungsfälle für [!DNL Adobe Experience Platform] und Anwendungen. Durchsuchen Sie die Seite nach Branche, um Anwendungsfälle für Ihre vertikale Umgebung, nach Reifegrad und nach dem richtigen Ausgangspunkt für Ihr Unternehmen zu finden, oder nach Implementierungsmuster, um zu verstehen, welcher technische Ansatz Ihren Anforderungen entspricht.

Jeder Anwendungsfall ist über ein Anwendungsfallmuster mit detaillierten Implementierungshandbüchern verknüpft, die die Funktionskette, Entscheidungspunkte und Konfigurationsschritte beschreiben, die zum Erreichen des Anwendungsfalls erforderlich sind.

## Nach Branche durchsuchen

>[!BEGINTABS]

>[!TAB Einzelhandel]

Einzelhandelsunternehmen verwenden [!DNL Adobe Experience Platform], um Kundendaten aus Online-Shops, physischen Standorten und Treueprogrammen in einer einzigen Ansicht jedes Kunden zu vereinheitlichen.

| | Nutzungsszenario | Beschreibung | Reife | Muster |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Personalisierte Produktempfehlung" width="40"> | [Personalisierte Produktempfehlungen](retail/retail-overview.md#personalized-product-recommendations) | Anzeigen personalisierter Produkte basierend auf dem Browse- und Kaufverlauf | [!BADGE Emerging]{type=Informative} | [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Transaktionsabbruch" width="40"> | [E-Mail-Wiederherstellung bei Transaktionsabbruch](retail/retail-overview.md#abandoned-cart-email-recovery) | Senden personalisierter Erinnerungen an Transaktionsabbrüche | [!BADGE Foundation]{type=Neutral} | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Dringlichkeit des Inventars" width="40"> | [Inventarbasierte Dringlichkeitskampagnen](retail/retail-overview.md#inventory-based-urgency-campaigns) | Echtzeit-Warnhinweise für Trigger bei niedrigem Produktbestand | [!BADGE Foundation]{type=Neutral} | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crosssell-Upsell" width="40"> | [Crosssell- und Upsell-Empfehlungen](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Anzeigen relevanter Crosssell- und Upsell-Produkte an der Kasse und in E-Mails | [!BADGE Erweitert]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Begrüßungsreihe" width="40"> | [Neue Kunden-Begrüßungsreihe](retail/retail-overview.md#new-customer-welcome-series) | Automatisieren einer Willkommensserie mit mehreren E-Mails und personalisierten Empfehlungen | [!BADGE Emerging]{type=Informative} | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Preissturz" width="40"> | [Warnhinweise bei Preisverfall](retail/retail-overview.md#price-drop-alerts) | Kunden benachrichtigen, wenn Wunschliste oder angezeigte Artikel im Preis fallen | [!BADGE Foundation]{type=Neutral} | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Nachfüllen" width="40"> | [Erinnerungs-](retail/retail-overview.md#replenishment-reminders) | Senden automatischer Erinnerungen für regelmäßig gekaufte Verbrauchsgüter | [!BADGE Emerging]{type=Informative} | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Kategorieseiten" width="40"> | [Personalisierte Kategorieseiten](retail/retail-overview.md#personalized-category-pages) | Kategorieseiten basierend auf den Voreinstellungen jedes Kunden dynamisch neu anordnen | [!BADGE Emerging]{type=Informative} | [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Nach dem Kauf" width="40"> | [Follow-up-Kampagnen nach dem Kauf](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Senden von Tipps zur Pflege, Überprüfungsanfragen und zugehörigen Produktvorschlägen | [!BADGE Emerging]{type=Informative} | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Exklusive VIP-Kundenangebote](retail/retail-overview.md#vip-customer-exclusive-offers) | Exklusive Angebote und frühzeitiger Zugriff auf hochwertige Kunden | [!BADGE Erweitert]{type=Caution} | [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [Nicht vorrätige Benachrichtigungen](retail/retail-overview.md#out-of-stock-notifications) | Kunden benachrichtigen, wenn nicht vorrätige Produkte verfügbar werden | [!BADGE Foundation]{type=Neutral} | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Anzeigen personalisierter Bewertungen und Bewertungen basierend auf dem Kundenprofil | [!BADGE Emerging]{type=Informative} | [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Finanzdienstleistungen]

Anwendungsfälle für Finanzdienstleistungen kommen bald. [Zeigen Sie aktuelle Anwendungsfälle für Financial Services an](financial-services/financial-services-overview.md).

>[!TAB Gesundheitswesen]

Anwendungsfälle für das Gesundheitswesen werden bald verfügbar sein. [Aktuelle Anwendungsfälle für das Gesundheitswesen anzeigen](healthcare/healthcare-overview.md).

>[!TAB Automotive]

Automotive-Anwendungsfälle kommen bald. [Zeigen Sie aktuelle Anwendungsfälle für die Automobilindustrie an](automotive/automotive-overview.md).

>[!TAB Reisen und Gastgewerbe]

Anwendungsfälle für Reisen und Gastgewerbe werden bald verfügbar sein. [Aktuelle Anwendungsfälle für Reisen und Gastgewerbe ](travel-hospitality/travel-hospitality-overview.md).

>[!TAB Telekommunikation]

Anwendungsfälle für die Telekommunikation folgen in Kürze. [Zeigen Sie aktuelle Telekommunikations-Anwendungsfälle an](telecommunications/telecommunications-overview.md).

>[!TAB Medien und Unterhaltung]

Anwendungsfälle für Medien und Unterhaltung werden bald verfügbar sein. [Aktuelle Anwendungsfälle für Medien und Unterhaltung anzeigen](media-entertainment/media-entertainment-overview.md).

>[!TAB Versicherung]

Anwendungsfälle für Versicherungen werden bald verfügbar sein. [Aktuelle Anwendungsfälle für Versicherungen anzeigen](insurance/insurance-overview.md).

>[!TAB B2B]

B2B-Anwendungsfälle werden bald verfügbar sein. [Zeigen Sie aktuelle B2B-Anwendungsfälle an](b2b/b2b-overview.md).

>[!ENDTABS]

## Nach Reifegrad durchsuchen

>[!BEGINTABS]

>[!TAB Foundation]

Grundlegende, bewährte Muster bei Verwendung der Einkanal-Bereitstellung. Ideale Ausgangspunkte für Unternehmen, die mit dem [!DNL Experience Platform] Journey beginnen.

| | Nutzungsszenario | Branche | Auswirkung auf den Betrieb | Muster |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Transaktionsabbruch" width="40"> | [E-Mail-Wiederherstellung bei Transaktionsabbruch](retail/retail-overview.md#abandoned-cart-email-recovery) | Einzelhandel | 25-35 % Warenkorb-Wiederherstellungsrate | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Dringlichkeit des Inventars" width="40"> | [Inventarbasierte Dringlichkeitskampagnen](retail/retail-overview.md#inventory-based-urgency-campaigns) | Einzelhandel | 30-40 % mehr Konversion | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Preissturz" width="40"> | [Warnhinweise bei Preisverfall](retail/retail-overview.md#price-drop-alerts) | Einzelhandel | Konversionsrate von 20-30 % | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [Nicht vorrätige Benachrichtigungen](retail/retail-overview.md#out-of-stock-notifications) | Einzelhandel | Konversionsrate von 40-50 % | [Ereignisausgelöstes Messaging](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB Emerging]

Multi-Channel- und Multi-Step-Muster, die auf grundlegenden Funktionen mit KI-gesteuerter Personalisierung und orchestrierten Journey aufbauen.

| | Nutzungsszenario | Branche | Auswirkung auf den Betrieb | Muster |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Produkt Recommendations" width="40"> | [Personalisierte Produktempfehlungen](retail/retail-overview.md#personalized-product-recommendations) | Einzelhandel | 20-30 % Steigerung der CTR, 15-25 % Steigerung der Konversionsrate | [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Kategorieseiten" width="40"> | [Personalisierte Kategorieseiten](retail/retail-overview.md#personalized-category-pages) | Einzelhandel | 25-35 % mehr Interaktion | [Verhaltensempfehlung](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Begrüßungsreihe" width="40"> | [Neue Kunden-Begrüßungsreihe](retail/retail-overview.md#new-customer-welcome-series) | Einzelhandel | Interaktionsrate von 40-50 % | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Nachfüllen" width="40"> | [Erinnerungs-](retail/retail-overview.md#replenishment-reminders) | Einzelhandel | Wiederholungsrate von 30-40 % | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Nach dem Kauf" width="40"> | [Follow-up-Kampagnen nach dem Kauf](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Einzelhandel | 15-20 % Überprüfungsrate, 10-15 % Wiederholungskauf | [Mehrstufige orchestrierte Journey](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Einzelhandel | Steigerung der Konversionsrate um 10-15 % | [Web-/App-Personalization für bekannte Besucher](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB Erweitert]

Kanalübergreifende Orchestrierung mit Echtzeit-Entscheidungsfindung und KI-gesteuerter Angebotsauswahl für anspruchsvollste Kundenerlebnisse.

| | Nutzungsszenario | Branche | Auswirkung auf den Betrieb | Muster |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crosssell-Upsell" width="40"> | [Crosssell- und Upsell-Empfehlungen](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Einzelhandel | AOV-Steigerung um 25 bis 75 USD, Umsatzsteigerung um 10 bis 15 % | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [Exklusive VIP-Kundenangebote](retail/retail-overview.md#vip-customer-exclusive-offers) | Einzelhandel | Interaktionsrate von VIPs von 50-70 % | [Cross-Channel-Journey mit Decisioning](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## Nach Implementierungsmuster durchsuchen

>[!BEGINTABS]

>[!TAB Kampagnenverwaltung und -orchestrierung]

### Ereignisausgelöstes Messaging

Reagieren Sie auf Verhaltensereignisse in Echtzeit mit zeitnahen Einzelkanal-Nachrichten.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Transaktionsabbruch" width="40"> | [E-Mail-Wiederherstellung bei Transaktionsabbruch](retail/retail-overview.md#abandoned-cart-email-recovery) | Einzelhandel | [!BADGE Foundation]{type=Neutral} | 25-35 % Warenkorb-Wiederherstellungsrate |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Dringlichkeit des Inventars" width="40"> | [Inventarbasierte Dringlichkeitskampagnen](retail/retail-overview.md#inventory-based-urgency-campaigns) | Einzelhandel | [!BADGE Foundation]{type=Neutral} | 30-40 % mehr Konversion |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Preissturz" width="40"> | [Warnhinweise bei Preisverfall](retail/retail-overview.md#price-drop-alerts) | Einzelhandel | [!BADGE Foundation]{type=Neutral} | Konversionsrate von 20-30 % |
| | [Nicht vorrätige Benachrichtigungen](retail/retail-overview.md#out-of-stock-notifications) | Einzelhandel | [!BADGE Foundation]{type=Neutral} | Konversionsrate von 40-50 % |

### Mehrstufige orchestrierte Journey

Führen Sie Kunden durch Multi-Touch-Sequenzen, die sich basierend auf Interaktion und Verhalten anpassen.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Begrüßungsreihe" width="40"> | [Neue Kunden-Begrüßungsreihe](retail/retail-overview.md#new-customer-welcome-series) | Einzelhandel | [!BADGE Emerging]{type=Informative} | Interaktionsrate von 40-50 % |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Nachfüllen" width="40"> | [Erinnerungs-](retail/retail-overview.md#replenishment-reminders) | Einzelhandel | [!BADGE Emerging]{type=Informative} | Wiederholungsrate von 30-40 % |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Nach dem Kauf" width="40"> | [Follow-up-Kampagnen nach dem Kauf](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Einzelhandel | [!BADGE Emerging]{type=Informative} | 15-20 % Überprüfungsrate, 10-15 % Wiederholungskauf |

### Cross-Channel-Journey mit Decisioning

Orchestrieren Sie kanalübergreifende Erlebnisse mit Offer Decisioning in Echtzeit an jedem Touchpoint.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| | [Exklusive VIP-Kundenangebote](retail/retail-overview.md#vip-customer-exclusive-offers) | Einzelhandel | [!BADGE Erweitert]{type=Caution} | Interaktionsrate von VIPs von 50-70 % |

>[!TAB Personalization]

### Verhaltensempfehlung

Verwenden Sie KI-gesteuerte Modelle, um personalisierte Inhalte und Produkte basierend auf Verhaltenssignalen darzustellen.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Produkt Recommendations" width="40"> | [Personalisierte Produktempfehlungen](retail/retail-overview.md#personalized-product-recommendations) | Einzelhandel | [!BADGE Emerging]{type=Informative} | 20-30 % Steigerung der CTR, 15-25 % Steigerung der Konversionsrate |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Kategorieseiten" width="40"> | [Personalisierte Kategorieseiten](retail/retail-overview.md#personalized-category-pages) | Einzelhandel | [!BADGE Emerging]{type=Informative} | 25-35 % mehr Interaktion |

### Offer Decisioning

Verwenden Sie eine zentralisierte Entscheidungslogik, um das beste Angebot für jeden Kunden und Kontext zu bewerten und auszuwählen.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crosssell-Upsell" width="40"> | [Crosssell- und Upsell-Empfehlungen](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Einzelhandel | [!BADGE Erweitert]{type=Caution} | AOV-Steigerung um 25 bis 75 USD, Umsatzsteigerung um 10 bis 15 % |

### Web-/App-Personalization für bekannte Besucher

Personalisieren von Web- und App-Inhalten für identifizierte Besucher basierend auf Profil, Voreinstellungen und Browserkontext.

| | Nutzungsszenario | Branche | Reife | Auswirkung auf den Betrieb |
| --- | --- | --- | --- | --- |
| | [Social Proof Personalization](retail/retail-overview.md#social-proof-personalization) | Einzelhandel | [!BADGE Emerging]{type=Informative} | Steigerung der Konversionsrate um 10-15 % |

>[!ENDTABS]
