---
title: Einkauf von gruppenbasiertem Marketing und Journey-Management
description: Erfahren Sie, wie Sie Journey auf Kontoebene entwickeln, die Leads zu Einkaufsgruppen qualifizieren, um die B2B-Marketing-Effektivität zu verbessern.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# Einkauf von gruppenbasiertem Marketing und Journey-Management

In diesem Handbuch wird das Anwendungsfallmuster für den Kauf von gruppenbasiertem Marketing und Journey-Management beschrieben, bei dem [!DNL Adobe Journey Optimizer B2B Edition] und [!DNL Real-Time CDP B2B Edition] verwendet werden, um die Journey-Orchestrierung auf Kontoebene mit der Einkaufsgruppenverwaltung zu implementieren. Er wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die verstehen müssen, was dieses Muster bewirkt, welche Geschäftsziele es unterstützt, welche taktischen Anwendungsfälle es ermöglicht und welche Adobe-Anwendungen beteiligt sind.

Im Gegensatz zu Journey-Mustern auf Personenebene funktioniert dieses Muster auf Kontoebene, qualifiziert individuelle Leads zu Einkaufsgruppen, die mit Lösungsinteressen verknüpft sind, bewertet die Interaktion auf der Einkaufsgruppenebene und orchestriert mehrstufige Account-Journey, die Accounts über Pipeline-Phasen in Richtung Verkaufsbereitschaft weiterleiten.

## Anwendungsfallmuster

**Kaufen von gruppenbasiertem Marketing und Journey-Management**

Entwickeln Sie Journey auf Kontoebene, die Leads zu Einkaufsgruppen qualifizieren, um die B2B-Marketing-Effektivität zu verbessern.

**Ausführungsplan:** Kontoidentifizierung > Einkaufsgruppendefinition > Lead-Qualifizierung > Ausführung der Konto-Journey > Interaktionsbewertung > Berichterstellung

## Anwendungsfall - Übersicht

B2B-Organisationen stehen vor einer grundlegenden Herausforderung: Kaufentscheidungen werden selten von einer Person getroffen. Komplexe B2B-Käufe beziehen mehrere Stakeholder ein - Entscheidungsträger, Influencer, Champions, Budgetverantwortliche und technische Gutachter - die zusammen eine „Einkaufsgruppe“ bilden. Traditionelles Lead-basiertes Marketing behandelt jede Person unabhängig, ohne das entscheidende Signal, ob die richtige Kombination von Rollen innerhalb eines Accounts engagiert und kaufbereit ist.

Beim Kauf von gruppenbasiertem Marketing und Journey-Management wird dies behoben, indem die Einheit der Orchestrierung von einzelnen Leads zu Accounts und Einkaufsgruppen verschoben wird. Das Muster ermöglicht es B2B-Marketing-Experten, Lösungsinteressen (die verkauften Produkte oder Services) zu definieren, Einkaufsgruppenvorlagen zu erstellen, die angeben, welche Rollen für eine Kaufentscheidung erforderlich sind, eingehende Leads für diese Rollen zu qualifizieren, die Interaktion auf der Einkaufsgruppenebene zu bewerten und Account-Journey zu koordinieren, die auf die Vollständigkeit der Einkaufsgruppe und Bereitschaftssignale reagieren.

Das gewünschte Ergebnis ist eine verbesserte Pipeline-Qualität und -Geschwindigkeit: Das Marketing liefert Konten nur dann an den Verkauf, wenn die richtigen Personen innerhalb des Kontos interagieren und die kaufende Gruppe ausreichend vollständig ist, wodurch verschwendeter Verkaufsaufwand reduziert und der Abschlussfortschritt beschleunigt wird.

## Wichtige Geschäftsziele

Dieses Anwendungsfallmuster unterstützt die folgenden Geschäftsziele.

### Verbessern der Lead-Qualifizierung und -Konversion

Erhöhen Sie die Lead-Qualität und beschleunigen Sie den Pipeline-Fortschritt durch Bewertung, Pflege und personalisierte Nachverfolgung.

**KPIs:** Lead-Konversion, Interessenten-/Lead-Konversion, Effizienz

[Erfahren Sie mehr über die Verbesserung der Lead-Qualifizierung und -Konversion](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Lead-Generierung erhöhen

Generieren Sie durch Formulare, Ereignisse, Inhalte und kanalübergreifende Interaktionen besser qualifizierte Leads für die Vertriebs-Pipeline.

**KPIs:** Interessenten, Kosten pro Lead, Lead-Konversion

[Weitere Informationen zur Steigerung der Lead-Generierung](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Umsatz und Umsatz steigern

Steigern Sie Ihre Umsätze auf höchstem Niveau durch optimierte Digitalkanäle, Kampagnen und Journey.

**KPIs:** Umsatzwachstum, Pipeline-Geschwindigkeit, Abschlussrate der Abschlüsse

[Erfahren Sie mehr über Umsatzsteigerung und Umsatzsteigerung](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Beispiele für taktische Anwendungsfälle

Im Folgenden finden Sie spezifische Szenarien, in denen dieses Muster angewendet werden kann.

- **Lösungsspezifische Einkaufsgruppenqualifizierung** - Definieren Sie Einkaufsgruppen für jede Produktlinie (z. B. „Enterprise CRM“, „Data Platform“, „Security Suite„) mit Rollenvorlagen, in denen die erforderlichen Rollen angegeben sind (wirtschaftlicher Käufer, technischer Bewerter, Champion, Endbenutzer), und qualifizieren Sie Leads aus dem CRM- und Marketing-Automatisierungssystem für diese Rollen.
- **Account-Journey für Pipeline-Beschleunigung** - Orchestrieren Sie eine mehrstufige Account-Journey, die zielgerichtete Nurture-E-Mails an unterbesetzte Rollen innerhalb einer Einkaufsgruppe sendet, Verkaufswarnungen an Trigger sendet, wenn die Interaktionsschwellen erreicht sind, und das Account in eine verkaufsbereite Phase überführt.
- **Kampagnen zur Vollständigkeit der Einkaufsgruppe** - Ermitteln Sie Konten, bei denen Einkaufsgruppen fehlende Rollen haben (z. B. kein wirtschaftlicher Käufer identifiziert), und starten Sie zielgerichtete Akquisekampagnen, um die richtigen Personen in diesen Konten einzubinden.
- **Crosssell Account Journey** - Nach Abschluss eines ersten Deals neue Einkaufsgruppen für ergänzende Lösungsinteressen erstellen und Account Journey koordinieren, die den erweiterten Einkaufsausschuss unterstützen.
- **Erneute Interaktion für aufgehaltene Angebote** - Erkennen Sie Konten, in denen der Wert der Gruppeninteraktion für den Kauf gesunken ist, und Journey, die die Interaktion mit Triggern wiederaufnehmen, mit neuen Inhalten, Interaktionen mit Führungskräften oder Ereigniseinladungen.
- **Vertriebs- und Marketing-Ausrichtung über CRM Insights** - Der Status der Einkaufsgruppe, Interaktionsdaten und der Account-Journey-Fortschritt werden direkt innerhalb von [!DNL Salesforce] oder [!DNL Dynamics 365] angezeigt, sodass Vertriebsmitarbeiter einen Echtzeitüberblick über Marketing-qualifizierte Accounts erhalten.
- **Ereignisgesteuerte Updates für Einkaufsgruppen** - Automatische Aktualisierung der Kauf-Gruppenmitgliedschaft und Interaktionswerte, wenn Leads an Webinaren teilnehmen, Whitepapers herunterladen, Preisseiten besuchen oder Demos anfordern.
- **Multi-Region-Kontokoordination** - Verwalten Sie Einkaufsgruppen über globale Konten hinweg, bei denen verschiedene regionale Kontakte unterschiedliche Rollen innehaben, und vereinheitlichen Sie die Interaktionsbewertung über Ländergrenzen hinweg.

## Wichtige Performance-Indikatoren

Mit den folgenden KPIs kann die Effektivität dieses Anwendungsfallmusters gemessen werden.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Abschlussrate der Einkaufsgruppe | Prozentsatz der Einkaufsgruppen mit allen erforderlichen Funktionen | [!DNL AJO B2B] Analytics-Dashboards: Rollenabdeckung pro Einkaufsgruppe verfolgen |
| Bewertung der Einkaufsgruppeninteraktion | Aggregierte Interaktionsbewertung für alle Mitglieder einer Einkaufsgruppe | [!DNL AJO B2B] Interaktionsbewertung: Punktzahlen auf Personenebene, aggregiert nach Einkaufsgruppe |
| Tarif für qualifiziertes Marketing-Konto (MQA) | Prozentsatz der Konten, die den Schwellenwert für Marketing-Qualifizierungen erreichen | Beendigungskriterien für Konto-Journey: Konten, die in das verkaufsbereite Stadium übergehen |
| Pipeline-Geschwindigkeit | Durchschnittliche Zeit vom Kauf der Gruppenerstellung bis zur verkaufsqualifizierten Opportunity | CRM-Integration: Verfolgen Sie Stadienübergänge von der [!DNL AJO B2B] zur CRM-Pipeline |
| Qualifikationsrate Lead-zu-Buying-Gruppe | Prozentsatz der Leads, die sich erfolgreich für Einkaufsgruppenrollen qualifiziert haben | [!DNL AJO B2B] Buying Group Management: Quotient aus qualifiziertem und nicht qualifiziertem Lead |
| Reaktionsrate bei Warnhinweisen für Verkäufe | Prozentualer Anteil der Verkaufswarnungen, die zu Folgeaktivitäten im Vertrieb führen | CRM-Vertriebseinblicke: Konvertierung von Warnhinweisen in Aktivitäten verfolgen |
| Abschlussrate für Konto-Journey | Prozentsatz der Konten, die den vorgesehenen Journey-Pfad abschließen | [!DNL AJO B2B] Analytics-Dashboards: Journey-Abschlussmetriken |
| E-Mail-Interaktionsrate (B2B) | Öffnungs- und Klickraten für B2B-Nurture-E-Mails | [!DNL AJO B2B]-Reporting: Metriken zum E-Mail-Versand und zur Interaktion |

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** - Orchestriert Journey auf Kontoebene, verwaltet Einkaufsgruppen mit Rollenvorlagen und Lösungsinteressen, bewertet die Interaktion auf Personen- und Einkaufsgruppenebene, verfasst B2B-E-Mail-Inhalte, sendet SMS-Nachrichten, konfiguriert Verkaufswarnungen und stellt B2B-Analytics-Dashboards bereit.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** - Vereinheitlicht Account-Profile aus B2B-Quelldaten, löst Personen-zu-Account-Beziehungen auf, bewertet Audiences auf Kontoebene, konfiguriert B2B-spezifische Ziele ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) und erzwingt Data Governance für B2B-Daten.

## Verwandte Dokumentation

Die folgenden Ressourcen enthalten weitere Details zu den Programmen und Funktionen, auf die in diesem Handbuch verwiesen wird.

### [!DNL AJO B2B Edition]

- [Dokumentation zu AJO B2B edition - Startseite](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)
- [Einkaufsgruppen - Übersicht](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Interessen an der Lösung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Rollenvorlagen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Erstellen von Einkaufsgruppen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Käufergruppenphasen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Übersicht über Account Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Konto-Journey-Knoten](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [Warnungs-E-Mails für Verkauf](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM-Vertriebserkenntnisse](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B-E-Mail und -Inhalte

- [B2B-E-Mail-Authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS-Authoring in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [KI-Assistent für E-Mail-Authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B-Analysen und Dashboards

- [Dashboard für Einkaufsgruppen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Interaktions-Dashboard](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligentes Dashboard](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [Übersicht über RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b)
- [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage-Quell-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Datengrundlage

- [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home)
- [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
- [Überblick über Quellen](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home)

### Kanalkonfiguration

- [Erste Schritte mit der E-Mail-Konfiguration](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-Kanal konfigurieren](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Data Governance und Datenschutz

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home)
- [Erweitertes Data Lifecycle Management](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home)

### Ziele

- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Zielkatalog](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/overview)
- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)

### Leitlinien

- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- [Schutzmaßnahmen bei der Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Schutzmaßnahmen bei der Aufnahme](https://experienceleague.adobe.com/de/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)

### Tutorials und Erste Schritte

- [Erste Schritte mit AJO B2B edition](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP-B2B edition-Tutorial](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
