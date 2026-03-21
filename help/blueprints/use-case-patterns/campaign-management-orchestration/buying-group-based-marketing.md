---
title: Einkauf von gruppenbasiertem Marketing und Journey-Management
description: Erfahren Sie, wie Sie Journey auf Kontoebene entwickeln, die Leads zu Einkaufsgruppen qualifizieren, um die B2B-Marketing-Effektivität zu verbessern.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---


# Einkauf von gruppenbasiertem Marketing und Journey-Management

Dieses Handbuch bietet eine umfassende Implementierungsreferenz für das Kaufen von gruppenbasiertem Marketing und Journey-Management. Es wurde für Lösungsarchitekten, Marketing-Techniker und Implementierungstechniker entwickelt, die eine Journey-Orchestrierung auf Kontoebene mit Einkaufsgruppenverwaltung mithilfe von [!DNL Adobe Journey Optimizer B2B Edition] und [!DNL Real-Time CDP B2B Edition] implementieren müssen.

In diesem Dokument erfahren Sie, was zu konfigurieren ist, wo Implementierungsoptionen vorhanden sind und welche Kompromisse die einzelnen Entscheidungen fördern.

Im Gegensatz zu Journey-Mustern auf Personenebene funktioniert dieses Muster auf Kontoebene, qualifiziert individuelle Leads zu Einkaufsgruppen, die mit Lösungsinteressen verknüpft sind, bewertet die Interaktion auf der Einkaufsgruppenebene und orchestriert mehrstufige Account-Journey, die Accounts über Pipeline-Phasen in Richtung Verkaufsbereitschaft weiterleiten.

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

## Anwendungsfallmuster

**Kaufen von gruppenbasiertem Marketing und Journey-Management**

Entwickeln Sie Journey auf Kontoebene, die Leads zu Einkaufsgruppen qualifizieren, um die B2B-Marketing-Effektivität zu verbessern.

**Funktionskette:** Kontoidentifizierung > Einkaufsgruppendefinition > Lead-Qualifizierung > Ausführung der Account-Journey > Interaktionsbewertung > Berichterstellung

## Programme

Die folgenden Adobe-Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** - Orchestriert Journey auf Kontoebene, verwaltet Einkaufsgruppen mit Rollenvorlagen und Lösungsinteressen, bewertet die Interaktion auf Personen- und Einkaufsgruppenebene, verfasst B2B-E-Mail-Inhalte, sendet SMS-Nachrichten, konfiguriert Verkaufswarnungen und stellt B2B-Analytics-Dashboards bereit.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** - Vereinheitlicht Account-Profile aus B2B-Quelldaten, löst Personen-zu-Account-Beziehungen auf, bewertet Audiences auf Kontoebene, konfiguriert B2B-spezifische Ziele ([!DNL Marketo Engage], [!DNL LinkedIn], CRM) und erzwingt Data Governance für B2B-Daten.

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Erforderlich | Sandbox mit aktivierten Berechtigungen für [!DNL AJO B2B Edition] und [!DNL RT-CDP B2B Edition]. Rollen, die für B2B-Marketing-Experten, Vertriebsmitarbeiter und Administratoren mit entsprechenden Berechtigungen für die Einkaufsgruppenverwaltung, Account-Journey und CRM-Integrationseinstellungen konfiguriert sind. | [Sandbox-Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sandbox/home), [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | B2B-XDM-Schemata, die mit B2B-spezifischen Klassen konfiguriert wurden: XDM Business Account, XDM Business Opportunity, XDM Business Person (Lead/Kontakt), XDM Business Campaign und XDM Business Marketing List. Feldergruppen für Kontoattribute, Personenattribute und Aktivitäts-/Interaktionsdaten müssen vorhanden sein. Für jedes Schema wurden Datensätze erstellt und für das Profil aktiviert. | [XDM-Systemübersicht](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/home), [B2B-Schemaklassen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Datenquellen und Sammlung | Erforderlich | Einrichtung von B2B-Datenaufnahme-Pipelines, normalerweise über den [!DNL Marketo Engage]-Quell-Connector oder [!DNL Salesforce]/[!DNL Dynamics] CRM-Quell-Connectoren. Daten zu Konten, Personen, Opportunities, Kampagnen und Kampagnenmitgliedern müssen in AEP-Datensätze fließen. Verhaltensbezogene Interaktionsdaten (Web-Besuche, E-Mail-Interaktionen, Inhalts-Downloads) müssen ebenfalls zur Interaktionsbewertung aufgenommen werden. | [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home), [Marketo Engage-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identitäts- und Profilkonfiguration | Erforderlich | B2B-Identitätsauflösung, die zum Auflösen von Personen-Konto-Beziehungen konfiguriert ist. Identity-Namespaces für B2B-Kennungen ([!DNL Marketo] Personen-ID, [!DNL Salesforce] Lead/Kontakt-ID, Konto-ID) müssen vorhanden sein. Für die B2B-Profilvereinheitlichung konfigurierte Zusammenführungsrichtlinien. Kontoprofile müssen aus quellenübergreifenden Daten vereinheitlicht werden. | [Identity Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home), [B2B-Identitätsauflösung](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Zielgruppendefinitionen auf Kontoebene, die mit Kontoattributen, Personenattributen und Aktivitätsdaten erstellt wurden. Konto-Zielgruppen identifizieren, welche Konten in die Journey der Einkaufsgruppe eintreten. Die Batch-Auswertung ist in der Regel ausreichend für B2B-Account-Journey, obwohl die Streaming-Auswertung für Trigger der Echtzeit-Kontoqualifizierung verwendet werden kann. | [Segmentierungs-Service - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/home), [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Empfohlen | Berechnete Attribute können Interaktionsereignisse auf Personenebene (E-Mail-Öffnungen, Inhalts-Downloads, Webinar-Anwesenheit) in Interaktionsmetriken auf Kontoebene aggregieren, die die Logik der Einkaufsgruppenbewertung und Kontoqualifizierung unterstützen. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Die Einverständnisverwaltung ist für die B2B-E-Mail- und SMS-Kommunikation von entscheidender Bedeutung. Richtlinien zur Datensatzgültigkeit helfen beim Management des Lebenszyklus von Daten mit vorübergehender Interaktion und stellen die Einhaltung von Datenspeicherungsanforderungen sicher. | [Erweitertes Daten-Lifecycle-Management](https://experienceleague.adobe.com/de/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | B2B-Daten enthalten oft sensible Firmeninformationen und persönliche Daten von Geschäftskontakten. Data-Governance-Richtlinien stellen die konforme Nutzung von B2B-Daten über Ziele hinweg sicher, insbesondere bei der Aktivierung auf Werbeplattformen oder Drittanbietersystemen. | [Data Governance - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | Überwachung stellt sicher, dass B2B-Datenpipelines (CRM/[!DNL Marketo]-Synchronisationen) fehlerfrei sind, Kontoprofile aktualisiert werden und Account-Journey-Ausführungen ohne Fehler fortgesetzt werden. Warnhinweise bei Fehlern im Quelldatenfluss sind wichtig, um die Datenwährung aufrechtzuerhalten. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | B2B-Analytics-Dashboards in [!DNL AJO B2B Edition] bieten Kaufgruppeninteraktionen, Account-Journey-Performance und Pipeline-Metriken. [!DNL CJA B2B Edition] erweitert die -Analyse mit Analysis Workspace auf Kontoebene, Analyse der Einkaufsgruppe und Opportunity-Korrelation. | [Übersicht über CJA](https://experienceleague.adobe.com/de/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Konfiguration des Lösungsinteresses | Phase 1: Lösungsinteresse und Einrichtung der Einkaufsgruppe | Definieren von Lösungsinteressen, die Produkte oder Services den Kriterien für die Einkaufsgruppenqualifizierung zuordnen |
| Einkaufsgruppenverwaltung | Phase 1: Lösungsinteresse und Einrichtung der Einkaufsgruppe | Erstellen und verwalten Sie Einkaufsgruppen mit Rollenvorlagen, persönlicher Zuordnung und Definition des Lösungsinteresses |
| Account Journey Orchestration | Phase 3: Konzeption und Ausführung von Account-Journey | Entwerfen und verwalten Sie mehrstufige Account-Journey mit Bedingungen, Aktionen und interaktionsbasierter Verzweigung |
| Interaktionsbewertung | Phase 2: Lead-Qualifizierung und Interaktionsbewertung | Bewerten Sie die Interaktion auf Personenebene innerhalb von Einkaufsgruppen, um die Vollständigkeit und Bereitschaft der Einkaufsgruppen zu messen. |
| Kontoqualifizierung | Phase 2: Lead-Qualifizierung und Interaktionsbewertung | Verwenden Sie KI-gestützte Kontoqualifizierungsagenten, um die Kontobereitschaft und Pipeline-Qualität zu bewerten. |
| B2B-E-Mail-Authoring | Phase 3: Konzeption und Ausführung von Account-Journey | Erstellen von B2B-E-Mail-Inhalten mit Vorlagen, visuellen Fragmenten, Markenthemen und KI-gestützter Inhaltserstellung |
| SMS-Kanalverwaltung | Phase 3: Konzeption und Ausführung von Account-Journey | Konfigurieren und Verwalten der SMS-Kommunikation in B2B-Account-Journey |
| Konfiguration von Verkaufswarnhinweisen | Phase 4: Vertriebsausrichtung und CRM-Integration | Konfigurieren von Warnhinweis-E-Mails für den Verkauf, um Verkaufsteams über Meilensteine bei der Kundeninteraktion und Kaufsignale zu informieren |
| CRM-Vertriebserkenntnisse | Phase 4: Vertriebsausrichtung und CRM-Integration | Bereitstellung von CRM-interner Sichtbarkeit ([!DNL Salesforce], [!DNL Dynamics]) für den Kaufgruppenstatus, Interaktionsdaten und den Account-Journey-Fortschritt |
| B2B-Analytics-Dashboards | Phase 5: Reporting und Optimierung | Überwachen der Account-Journey-Performance, der Einkaufsgruppeninteraktion und der Pipeline-Metriken über intelligente Interaktions- und Interaktions-Dashboards |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kontoprofil-Vereinheitlichung | Phase 0: B2B-Datengrundlage | Konsolidierung quellenübergreifender B2B-Daten in einheitlichen Account-Profilen mithilfe spezialisierter XDM-B2B-Schemaklassen und Feldergruppen |
| B2B-Identitätsauflösung | Phase 0: B2B-Datengrundlage | Lösen Sie Personen-zu-Konto-Beziehungen mithilfe primärer Kennungen auf, die mehrstufige Kontohierarchien und Viele-zu-Viele-Personen-zu-Konto-Zuordnungen unterstützen |
| Evaluierung der Konto-Zielgruppe | Phase 0: B2B-Datengrundlage | Bewerten der Segmentzugehörigkeit auf Kontoebene, indem Kontoattribute, Personenattribute und Aktivitätsdaten kombiniert werden |
| Kontozielkonfiguration | Phase 4: Vertriebsausrichtung und CRM-Integration | Konfigurieren von Verbindungen zu B2B-spezifischen Zielen ([!DNL Marketo Engage], [!DNL LinkedIn], CRM-Systeme) mit Feld-Mapping auf Kontoebene |
| Account Audience Activation | Phase 4: Vertriebsausrichtung und CRM-Integration | Kontobasierte Zielgruppen für Ziele für kontobasiertes Targeting und Unterdrückung veröffentlichen |
| [!DNL Marketo Engage] Integration | Phase 0: B2B-Datengrundlage | Aufnehmen und Aktivieren von Daten bidirektional mit [!DNL Marketo Engage] mithilfe von nativen B2B-Quell- und Ziel-Connectoren |
| B2B-Data Governance | Phase 0: B2B-Datengrundlage | Durchsetzen von Datennutzungsrichtlinien und Einverständnis für die Prozesse zur Zentralisierung und Aktivierung von B2B-Kontodaten |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [!DNL AJO B2B Edition] Lizenz in der Ziel-Sandbox bereitgestellt und aktiviert
- [!DNL RT-CDP B2B Edition] Lizenz in der Ziel-Sandbox bereitgestellt und aktiviert
- CRM-System ([!DNL Salesforce] oder [!DNL Microsoft Dynamics 365]), auf das mit entsprechenden API-Anmeldedaten für die bidirektionale Datensynchronisation zugegriffen werden kann
- [!DNL Marketo Engage] Instanz ist (bei Verwendung von [!DNL Marketo] als Marketing-Automatisierungsplattform) mit konfiguriertem Quell-Connector verbunden
- Bereitgestellte B2B-XDM-Schemata: Konto-, Personen-, Opportunity-, Kampagnen- und Kampagnenmitgliedsklassen mit erforderlichen Feldergruppen
- Konto- und Personendaten, die in AEP aufgenommen werden, wobei die Personen-zu-Konto-Beziehungen aufgelöst werden
- Konfigurierter E-Mail-Kanal: Subdomain delegiert, IP-Pool erwärmt und Kanaloberfläche für B2B-E-Mail-Versand erstellt
- Konfigurierter SMS-Anbieter (wenn der SMS-Kanal in den Journey des Kontos verwendet wird): [!DNL Sinch], [!DNL Twilio] oder [!DNL Infobip] bereitgestellte Anmeldeinformationen
- In die CRM-Komponente „Sales Insights“ integriertes Vertriebsteam ([!DNL Salesforce] AppExchange-Paket oder [!DNL Dynamics] installierte Lösung)
- Vorbereitete Content-Assets: B2B-E-Mail-Vorlagen, Marken-Designs und visuelle Fragmente für E-Mails zu Pflege und Vertrieb
- Taxonomie der Lösungsinteressen definiert: Liste der Produkte/Services, die mit Einkaufsgruppen verknüpft sind
- Rollenvorlagen für Einkaufsgruppen wurden entworfen: Rollen und Rollen, die für jedes Lösungsinteresse erforderlich sind (z. B. Economic Buyer, Technical Evaluator, Champion)

## Implementierungsoptionen

In diesem Abschnitt werden die verfügbaren Implementierungsansätze beschrieben, die jeweils auf unterschiedliche organisatorische Anforderungen und Reifegrade zugeschnitten sind.

### Option A: Interesse an einer einzigen Lösung mit linearem Account-Journey

**Am besten geeignet für:** Organisationen, die noch nicht mit dem Einkaufsgruppenmanagement vertraut sind und mit einer einzigen Produktlinie oder einem einzigen Lösungsangebot beginnen, den Ansatz validieren und iterieren möchten, bevor sie auf mehrere Lösungsinteressen skalieren.

**Funktionsweise:**

Dieser Ansatz konzentriert sich auf ein Lösungsinteresse (ein Produkt oder eine Dienstleistung) mit einer Einkaufsgruppenvorlage. Eine lineare Account-Journey ist mit sequenziellen Phasen konzipiert: Kontoidentifizierung, Einkaufsgruppenbildung, Nurture-Interaktion, Interaktionsbewertungsschwelle und Verkaufsübergabe. Die Journey folgt einem einfachen Weg ohne komplizierte Verzweigungen oder Parallelspuren.

Leads werden beim Aufnehmen aus dem CRM oder [!DNL Marketo Engage] in Kauf-Gruppenrollen qualifiziert. Die Account-Journey sendet Nurture-E-Mails an unterbesetzte Rollen, überwacht die Interaktionswerte und benachrichtigt Trigger über einen Verkaufsalarm, wenn die kaufende Gruppe einen definierten Vollständigkeits- und Interaktionsschwellenwert erreicht. Dieser Ansatz bietet einen klaren, messbaren Konzeptnachweis, bevor er Komplexität einführt.

**Wichtige Aspekte:**

- Einfachere Implementierung und Validierung, sodass es für eine erste Bereitstellung geeignet ist
- Jeweils nur ein Produkt-/Dienstleistungskauf möglich
- Die lineare Journey-Struktur ist möglicherweise nicht für komplexe mehrstufige Kaufzyklen geeignet

**Vorteile:**

- Schnellste Amortisierungszeit bei minimaler Konfigurationskomplexität
- Klare Erfolgsmetriken, die an eine einzige Lösung gebunden sind
- Einfachere Erläuterung und höhere Akzeptanz im Unternehmen
- Einfaches Reporting und einfache KPI-Messung

**Einschränkungen:**

- Bezieht sich nicht auf Crosssell- oder Multi-Produkt-Szenarien
- Accounts, die an mehreren Lösungen interessiert sind, benötigen separate, unkoordinierte Journey
- Die Funktionen zur Verwaltung von Einkaufsgruppen können möglicherweise nicht vollständig genutzt werden

**Experience League:**

- [Übersicht über AJO B2B edition](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)
- [Erstellen von Einkaufsgruppen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### Option B: Verschiedene Lösungsinteressen mit Verzweigungskonto-Journeys

**Am besten geeignet für:** Unternehmen mit mehreren Produktlinien oder Service-Angeboten, die unterschiedliche Einkaufsgruppen je nach Lösungsinteresse verwalten müssen, wobei die Account-Journeys diese Filiale nach Maßgabe der Lösungsinteressen und der Dauer des Qualifizierungsprozesses für jede einzelne Einkaufsgruppe definieren.

**Funktionsweise:**

Es werden mehrere Lösungsinteressen definiert, die jeweils über eine eigene Vorlage für die Einkaufsgruppenrolle verfügen. Eine Account-Journey beginnt mit Account-Identifikation und bewertet anhand von Verhaltenssignalen, firmografischen Daten oder expliziten Absichten, welche Lösungsinteressen für jedes Account gelten. Die Journey-Verzweigungen adressieren jedes Interesse an einer aktiven Lösung und führen parallele Pflegespuren für verschiedene Einkaufsgruppen innerhalb desselben Accounts durch.

Die Interaktionsbewertung erfolgt unabhängig pro Einkaufsgruppe, sodass eine Einkaufsgruppe die Verkaufsbereitschaft erreicht, während eine andere noch gepflegt wird. Verkaufswarnungen werden gemäß dem Lösungsinteresse konfiguriert, sodass das entsprechende Vertriebsteam oder der Spezialist benachrichtigt wird, wenn eine bestimmte Einkaufsgruppe qualifiziert ist. CRM Insights zeigt alle aktiven Einkaufsgruppen für ein Konto auf und bietet dem Verkauf eine ganzheitliche Sicht.

**Wichtige Aspekte:**

- Erfordert eine klar definierte Lösungsinteressentaxonomie und separate Einkaufsgruppenvorlagen
- Die Journey-Komplexität steigt mit jedem zusätzlichen Lösungsinteresse
- Die gruppenübergreifende Koordinierung (z. B. gemeinsame Kontakte, die Rollen in mehreren Einkaufsgruppen haben) muss geplant werden

**Vorteile:**

- Unterstützt Cross-Selling- und Multi-Product-Account-Strategien
- Unabhängige Bewertung pro Einkaufsgruppe bietet granulare Pipeline-Sichtbarkeit
- Vertriebsteams erhalten zielgerichtete Warnhinweise pro Lösungsinteresse
- Maximiert [!DNL AJO B2B Edition] Funktionen zur Einkaufsgruppenverwaltung

**Einschränkungen:**

- Höhere Implementierungskomplexität und längere Bereitstellungszeit
- Mehr Content-Assets erforderlich (separate E-Mail-Tracks je nach Lösungsinteresse)
- Die Berichterstellung ist komplexer mit mehreren Einkaufsgruppen pro Konto
- Risiko von Kontakten, die sich in mehreren Einkaufsgruppen befinden und zu viel Nachrichten senden (erfordert Häufigkeitsmanagement)

**Experience League:**

- [Interessen an der Lösung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Account Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### Option C: KI-gestützte Kontoqualifizierung mit automatisiertem Journey-Fortschritt

**Am besten geeignet für:** Ausgereifte B2B-Unternehmen mit wichtigen historischen Daten, die KI-gestützte Kontoqualifizierungsagenten nutzen möchten, um die Bewertung der Kontobereitschaft zu automatisieren, den manuellen Qualifizierungsaufwand zu reduzieren und Journey-Pfade basierend auf KI-generierten Bereitschaftswerten dynamisch anzupassen.

**Funktionsweise:**

Dieser Ansatz baut auf der Multi-Solution-Interest-Grundlage von Option B auf, fügt jedoch eine KI-gestützte Kontoqualifizierung hinzu, um den Übergang zwischen Journey-Phasen zu automatisieren. Statt sich ausschließlich auf regelbasierte Interaktionsbewertungsschwellen zu verlassen, bewertet der KI-Qualifizierungsagent die Kontobereitschaft anhand eines breiteren Satzes von Signalen: Kaufgruppenvollständigkeit, Interaktionsgeschwindigkeit, firmografische Anpassung, historische Konversionsmuster und Intent-Daten.

Account-Journey verwenden die Ausgabe der KI-Qualifizierung, um die nächsten Schritte zu bestimmen: Accounts, die bei Bereitschaft hoch bewertet werden, werden schnell auf Sales-Warnhinweise verschoben, Accounts der mittleren Ebene werden intensiviert gepflegt, und Low-Readiness-Accounts werden in langfristige Bewusstseinsspuren platziert. Der KI-Agent wird bei Eintreffen neuer Interaktionsdaten kontinuierlich neu ausgewertet, was einen dynamischen Journey-Fortschritt ohne manuelles Eingreifen ermöglicht.

**Wichtige Aspekte:**

- Erfordert ausreichende historische Daten, um effektive Qualifizierungsmodelle zu trainieren
- KI-Ausgaben sollten vor der vollständigen Bereitstellung anhand der tatsächlichen Pipeline-Ergebnisse validiert werden
- Lässt sich gut mit [!DNL CJA B2B Edition] zur Analyse der Qualifikationsgenauigkeit und Pipeline-Korrelation kombinieren

**Vorteile:**

- Reduziert den manuellen Qualifizierungsaufwand und eliminiert willkürliche, auf Schwellenwerten basierende Übergaben
- Dynamische Anpassung an sich ändernde Verhaltens- und Interaktionsmuster von Konten
- Höhere Pipeline-Qualität durch Einbeziehung mehrerer Signale über einfache Interaktionswerte hinaus
- Kontinuierliche Neubewertung verhindert, dass Accounts in falschen Journey-Stadien stecken bleiben

**Einschränkungen:**

- Erfordert historische Konversionsdaten für aussagekräftiges KI-Training
- Qualifizierungsentscheidungen für „Black Box“ sind für Vertriebsteams zunächst möglicherweise schwieriger zu verstehen und zu vertrauen
- Komplexer bei der Fehlerbehebung, wenn Konten unerwartet oder gar nicht qualifiziert werden
- Abhängig von der Datenqualität und Vollständigkeit aller Eingangssignale

**Experience League:**

- [Kontoqualifizierung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [KI-Assistent in AJO B2B](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)

### Vergleich von Optionen

| Kriterien | Option A: Interesse an einer einzigen Lösung | Option B: Interessen mehrerer Lösungen | Option C: KI-gestützte Qualifizierung |
| --- | --- | --- | --- |
| Am besten geeignet für | Erste Bereitstellung, einzelne Produktlinie | Organisationen mit mehreren Produkten | Ausgereifte Organisationen mit historischen Daten |
| Komplexität | Niedrig | Medium-Hoch | Hoch |
| Time-to-Value | 2-4 Wochen | 4-8 Wochen | 6-12 Wochen |
| Interessen an der Lösung | 1 | Mehrere | Mehrere |
| Journey-Struktur | Linear | Verzweigung, parallele Spuren | Dynamische, KI-gesteuerte Progression |
| Scoring-Ansatz | Regelbasierte Schwellenwerte | Regelbasiert pro Einkaufsgruppe | KI-gestützte Qualifizierung + Regeln |
| Inhaltsanforderungen | Minimal (eine Pflegespur) | Hoch (pro Lösungsinteresse) | Hohe + dynamische Inhaltsauswahl |
| Vertriebsausrichtung | Workflow für einzelnen Warnhinweis | Warnungen vor Lösungsinteressen | Priorisierte Warnhinweise mit KI-Bewertung |
| Erfordert | Grundlegende B2B-Datengrundlage | Gut definierte Lösungstaxonomie | Historische Konversionsdaten + Taxonomie |

### Wählen der richtigen Option

Beginnen Sie mit diesen Fragen, um den besten Implementierungsansatz zu bestimmen:

1. **Wie viele verschiedene Produkte oder Dienstleistungen haben unabhängige Einkaufskomitees?** Wenn die Antwort 1 ist (oder das Unternehmen das Konzept zuerst beweisen möchte), beginnen Sie mit Option A. Wenn mehrere, gehen Sie zu Frage 2.

2. **Gibt es ausreichende historische Daten zu gewonnenen/verlorenen Angeboten, der Zusammensetzung von Einkaufskomitees und Interaktionsmustern?** Wenn ja und das Unternehmen die manuelle Qualifizierung minimieren möchte, bietet Option C den am meisten automatisierten Ansatz. Ist dies nicht der Fall, bietet Option B Unterstützung für mehrere Lösungsinteressen mit regelbasierter Bewertung.

3. **Wie ist die Änderungsmanagementkapazität der Organisation?** Die Optionen B und C erfordern eine stärker organisatorische Ausrichtung (Inhaltserstellung, Vertriebsunterstützung, funktionsübergreifende Koordinierung). Wenn die Kapazität begrenzt ist, mit Option A beginnen und erweitern.

Ein gängiger Progressionspfad ist: Beginnen Sie mit Option A, um das Konzept mit einem Lösungsinteresse zu beweisen, erweitern Sie auf Option B, indem Sie Lösungsinteressen hinzufügen, wenn die Konfidenz wächst, und fügen Sie dann die KI-Qualifizierung von Option C hinzu, sobald ausreichend historische Daten verfügbar sind, um die Modelle effektiv zu trainieren.

## Implementierungsphasen

Die folgenden Phasen beschreiben den schrittweisen Implementierungsprozess für dieses Anwendungsfallmuster.

### Phase 0: B2B-Datengrundlage

**Anwendungsfunktionen:** [!DNL RT-CDP B2B]: Vereinheitlichung von Account-Profilen, B2B-Identitätsauflösung, [!DNL Marketo Engage]-Integration, B2B-Data Governance, Evaluierung der Account-Zielgruppe

In dieser Phase wird die B2B-Dateninfrastruktur in [!DNL RT-CDP B2B Edition] aufgebaut. Sie vereinheitlichen Kontodaten aus CRM, Marketing-Automatisierung und anderen Quellen in einem einzigen Kontoprofil, lösen Personen-zu-Konto-Beziehungen auf, konfigurieren B2B-Data Governance und erstellen Zielgruppen auf Kontoebene, die in [!DNL AJO B2B Edition] Einkaufsgruppenverwaltung einfließen.

#### Entscheidung: Strategie für B2B-Datenquellen

Welche Systeme dienen als primäre Quellen für Konto-, Personen- und Interaktionsdaten?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Als primäre Quelle [!DNL Marketo Engage] | [!DNL Marketo] ist die Marketing-Automatisierungsplattform des Unternehmens mit einem reichen Interaktionsverlauf | Nativer bidirektionaler Connector vereinfacht die Einrichtung; Interaktionsdaten fließen automatisch; von [!DNL Marketo] übernommene Beziehungen zwischen Personen und Konten |
| CRM ([!DNL Salesforce]/[!DNL Dynamics]) als primäre Quelle | CRM ist das Aufzeichnungssystem für Konten und Kontakte; [!DNL Marketo] wird nicht verwendet | Erfordert die Konfiguration des CRM-Quell-Connectors; für Interaktionsdaten sind möglicherweise zusätzliche Quellen erforderlich; es sind Personen-zu-Konto-Beziehungen aus CRM-Account-Kontaktverknüpfungen erforderlich |
| Hybrid: CRM für Konten + [!DNL Marketo] für Interaktion | CRM besitzt Konto-/Kontakt-Stammdaten, während [!DNL Marketo] Verhaltensinteraktionen erfasst | Häufigstes Muster für Organisationen, die beide verwenden; erfordert eine sorgfältige Identitätsauflösung, um [!DNL Marketo] Personen mit CRM-Kontakten zu verknüpfen |

#### Entscheidung: Strategie für Konto-Zielgruppen

Wie sollten Konto-Zielgruppen für den Journey-Eintrag definiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Firmografisch basierte Konto-Zielgruppen | Targeting von Konten basierend auf Branche, Unternehmensgröße, Umsatzstufe oder Geografie | Gut für ABM-Ziellisten; erfordert keine Interaktionsdaten; kann umfangreich sein |
| Interaktionsbasierte Konto-Zielgruppen | Targeting von Konten, in denen Personen verhaltensbezogene Absichtssignale gezeigt haben | Erfordert den Fluss von Interaktionsdaten, eine präzisere Zielgruppenbestimmung und kann Konten mit latentem Interesse verpassen |
| Kombinierte Firmographie + Interaktion | Targeting von Konten, die dem idealen Kundenprofil entsprechen UND Interaktion zeigen | Sehr genau; erfordert beide Datentypen; wird für die qualifizierte Pipeline-Generierung empfohlen |

**UI-Navigation:** Platform > Quellen > Katalog > Quelle auswählen ([!DNL Marketo Engage], [!DNL Salesforce] usw.) > Einrichten des Datenflusses

**Wichtige Konfigurationsdetails:**

- Konfigurieren von B2B-XDM-Schemata für jede B2B-Entität (Konto, Person, Opportunity, Kampagne, Kampagnenmitglied) mit den erforderlichen Feldergruppen
- Einrichten von Quell-Connectoren für CRM und/oder [!DNL Marketo Engage] mit entsprechender Planung (in der Regel 1-4-Stunden-Intervalle für B2B-Daten)
- Konfigurieren von Identity-Namespaces für B2B-Kennungen ([!DNL Marketo] Personen-ID, SFDC-Lead-ID, SFDC-Kontakt-ID, Konto-ID)
- B2B-Identitätsauflösung aktivieren, um Personen mit Konten zu verknüpfen
- Erstellen Sie Zielgruppen auf Kontoebene mithilfe der Funktion „Konto-Zielgruppen“ in [!DNL RT-CDP]

**Dokumentation zu Experience League:**

- [Übersicht über RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B-Schemata in Real-Time CDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage-Quell-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Konto-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/segmentation/types/account-audiences)
- [B2B-Identitätsauflösung](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### Phase 1: Interesse an der Lösung und Einrichtung der Einkaufsgruppe

**Anwendungsfunktionen:** [!DNL AJO B2B]: Konfiguration von Lösungsinteressen, Einkaufsgruppenverwaltung

In dieser Phase werden die Lösungsinteressen (Produkte/Services) und Einkaufsgruppenvorlagen definiert, die den Kern des Einkaufsgruppenmanagementmodells bilden. Sie erstellen Lösungsinteressen, definieren Rollenvorlagen mit persönlichen Anforderungen und konfigurieren, wie Leads für Einkaufsgruppenrollen qualifiziert werden.

#### Entscheidung: Granularität des Lösungsinteresses

Auf welcher Ebene sollten Lösungsinteressen definiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Interessen an Lösungen auf Produktebene | Jedes einzelne Produkt hat eine eigene Einkaufsgruppe | Am detailliertesten; ermöglicht produktspezifische Einkaufsgruppenvorlagen; kann zu vielen Einkaufsgruppen pro Konto führen |
| Interessen auf Ebene der Lösungskategorien | Gruppieren verwandter Produkte in Lösungskategorien (z. B. &quot;Marketing Cloud&quot; anstelle von einzelnen Produkten) | Einfachere Verwaltung; weniger Einkaufsgruppen; Rollen können allgemeiner sein; für erste Bereitstellungen empfohlen |
| Interessen auf Anwendungsfallebene | Legen Sie Interessen rund um Geschäftsergebnisse und nicht um Produkte fest (z. B. „Digitale Transformation„). | Ist an den Verkauf bei Beratern ausgerichtet; Rollen in Einkaufsgruppen können mehrere Produkte umfassen; schwieriger auf CRM-Pipeline-Stadien abzubilden |

#### Entscheidung: Design der Vorlage für die Einkaufsgruppenrolle

Wie sollten Rollen innerhalb jeder Einkaufsgruppe definiert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Standardrollenvorlage | Verwenden eines gemeinsamen Satzes von Rollen für alle Lösungsinteressen (z. B. Economic Buyer, Technical Evaluator, Champion, Endbenutzer) | Konsistente Bewertung und Qualifizierung; einfacher zu verwalten; möglicherweise nicht lösungsspezifische Rollen |
| Lösungsspezifische Rollenvorlagen | Definieren Sie eindeutige Rollen pro Lösungsinteresse basierend auf dem tatsächlichen Kaufausschuss für dieses Produkt | Präzisere Qualifizierung; erfordert tiefere Kenntnisse der einzelnen Kaufprozesse; höhere Wartung |
| Mehrstufige Rollenvorlagen | Erforderliche Rollen (für Qualifizierung unverzichtbar) und optionale Rollen definieren (Vollständigkeit erhöhen, aber nicht erforderlich) | Balanciert Präzision mit Flexibilität; verhindert, dass überstrenge Qualifikationskriterien die Pipeline blockieren |

**UI-Navigation:** [!DNL AJO B2B Edition] > Einkaufsgruppen > Lösungsinteressen > Lösungsinteressen erstellen

**UI-Navigation:** [!DNL AJO B2B Edition] > Einkaufsgruppen > Rollenvorlagen > Rollenvorlage erstellen

**Wichtige Konfigurationsdetails:**

- Definieren Sie jedes Lösungsinteresse mit einem Namen, einer Beschreibung und dem Geschäftsergebnis, das angesprochen wird
- Erstellen Sie Rollenvorlagen, in denen die für jede Einkaufsgruppe erforderlichen Rollen angegeben sind (z. B. Entscheidungsträger, Influencer, Praktiker, Executive Sponsor).
- Konfigurieren von Qualifizierungskriterien für Leads in Rollen: Wie das System bestimmt, welcher Rolle ein Lead zugeordnet wird (basierend auf Stellenbezeichnung, Abteilung, Dienstalter oder benutzerdefinierten Attributen)
- Vollständigkeitsschwellen festlegen: Definieren Sie, wie viel Prozent der Rollen für eine Einkaufsgruppe ausgefüllt werden müssen, damit sie als „abgeschlossen“ betrachtet wird.
- Lösungsinteressen mit Account-Zielgruppen oder Account-Attributen verknüpfen, die auf potenzielles Interesse hinweisen

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Interesse an einer einzigen Lösung):**
Erstellen Sie eine Lösungsinteressante und eine Rollenvorlage. Konzentrieren Sie sich auf einen klaren, gut verständlichen Kaufvorgang für das primäre Produkt oder die primäre Dienstleistung Ihres Unternehmens.

**Für Option B (Interessen mehrerer Lösungen):**
Erstellen Sie mehrere Lösungsinteressen mit jeweils einer eigenen Rollenvorlage. Ordnen Sie jedes Lösungsinteresse dem entsprechenden CRM-Produkt-/Opportunity-Typ für das nachgelagerte Pipeline-Tracking zu.

**Für Option C (KI-unterstützte Qualifizierung):**
Konfigurieren Sie Lösungsinteressen und Rollenvorlagen wie in Option B, konfigurieren Sie jedoch zusätzlich den KI-Qualifizierungsagenten mit historischen Daten zu erfolgreichen Einkaufsgruppenzusammensetzungen und Geschäftsergebnissen, um das Qualifizierungsmodell zu trainieren.

**Dokumentation zu Experience League:**

- [Einkaufsgruppen - Übersicht](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Interessen an der Lösung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Rollenvorlagen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Erstellen von Einkaufsgruppen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### Phase 2: Lead-Qualifizierung und Interaktionsbewertung

**Anwendungsfunktionen:** [!DNL AJO B2B]: Interaktionsbewertung, Kontoqualifizierung

In dieser Phase wird das Interaktionsbewertungsmodell eingerichtet, das die Interaktion auf Personenebene innerhalb von Einkaufsgruppen misst und auf Kauf-, Gruppen- und Kontoebene aggregiert. Sie konfigurieren Bewertungsregeln, definieren Interaktionsschwellen für die Qualifizierung und aktivieren optional die KI-gestützte Kontoqualifizierung.

#### Entscheidung: Interaktions-Bewertungsmodell

Wie sollte die Interaktion auf Personen- und Einkaufsgruppenebene bewertet werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Aktivitätsbasierte Bewertung | Weisen Sie bestimmten Aktionen Punktwerte zu (E-Mail geöffnet = 5 Punkte, Inhalt herunterladen = 15 Punkte, Demo-Anfrage = 50 Punkte) | Transparent und leicht anzupassen; erfordert laufende Wartung, wenn sich Inhalte und Kanäle ändern; ist [!DNL Marketo] Benutzern am vertrautesten |
| Bewertung mit Gewichtung der Neuigkeit | Gewichtung der letzten Aktivitäten höher als bei älteren (Modell mit abnehmendem Score) | spiegelt die aktuelle Absicht besser wider, verhindert, dass überholte Highscores die Qualifikation aufblähen, ist komplexer zu konfigurieren |
| KI-gestützte Bewertung | Verwenden Sie den [!DNL AJO B2B] AI Qualification Agent, um Bereitschaftswerte auf der Grundlage der Mustererkennung zu generieren | Am ausgereiftesten; passt sich automatisch an; erfordert historische Daten; kann für Vertriebsteams anfänglich undurchsichtig sein |

#### Entscheidung: Ansatz der Qualifikationsschwelle

Wann sollte eine Einkaufsgruppe als bereit für eine Verkaufsübergabe angesehen werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Score-Schwellenwert | Die Einkaufsgruppe ist qualifiziert, wenn der aggregierte Interaktionswert einen definierten Wert überschreitet. | Einfach zu implementieren; Schwellenwert für Punktzahl muss im Laufe der Zeit möglicherweise angepasst werden; berücksichtigt nicht die Zusammensetzung der Rolle |
| Vollständigkeit + Score-Schwellenwert | Die Einkaufsgruppe qualifiziert sich, wenn sowohl die Mindestfunktionsabdeckung als auch der Bewertungsschwellenwert erreicht werden | Robustere Qualifizierung; verhindert Übergabe von Einkaufsgruppen mit hohen Punktzahlen, aber fehlenden Schlüsselrollen |
| KI-ermittelte Bereitschaft | KI-Qualifizierungs-Agent ermittelt Bereitschaft anhand mehrerer Signale über Score und Vollständigkeit hinaus | Am ausgereiftesten; berücksichtigt Kaufgeschwindigkeit, Wettbewerbssignale und historische Muster; nur Option C |

**UI-Navigation:** [!DNL AJO B2B Edition] > Einkaufsgruppen > Interaktionsbewertung > Bewertungsregeln konfigurieren

**Wichtige Konfigurationsdetails:**

- Definieren Sie Regeln für die Interaktionsbewertung: Weisen Sie Verhaltensereignissen Punktwerte zu (E-Mail-Öffnungen, Klicks, Web-Seitenbesuche, Inhalts-Downloads, Formularübermittlungen, Webinar-Anwesenheit, Demoanfragen)
- Konfigurieren der Gewichtung von Bewertungsabfall oder Neuigkeit bei Verwendung von zeitabhängiger Bewertung
- Aggregation der Punktzahl auf Einkaufsgruppenebene festlegen: So werden Personenbewertungen zu einem Einkaufsgruppenwert kombiniert (Summe, gewichteter Durchschnitt oder Mindestschwellenwert pro Rolle)
- Qualifizierungsschwellen definieren: die Score- und Vollständigkeitsstufen, die der Trigger bis zum nächsten Kaufschritt erreicht
- Konfigurieren des KI-Qualifizierungsagenten (Option C): Trainieren mit historischen Abschlussdaten, Definieren der Signale, die der Agent berücksichtigen soll, und Festlegen von Konfidenzschwellen

**Dokumentation zu Experience League:**

- [Interaktionsbewertung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Käufergruppenphasen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Kontoqualifizierung](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### Phase 3: Konzeption und Ausführung von Account-Journey

**Anwendungsfunktionen:** [!DNL AJO B2B]: Konto-Journey Orchestration, B2B-E-Mail-Authoring, SMS-Kanalverwaltung

In dieser Phase wird die Account-Journey entworfen und bereitgestellt, die die Interaktion mit kaufenden Gruppenmitgliedern koordiniert. Sie erstellen Account-Journey mit Eintrittsbedingungen, Aktionsknoten (E-Mail, SMS), Bedingungszweigen (basierend auf Kaufgruppenphase, Interaktionswert, Rollenabdeckung), Warteschritten und Beendigungskriterien.

#### Entscheidung: Journey Entry Trigger

Welches Ereignis oder welche Bedingung führt dazu, dass ein Konto auf die Journey gelangt?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Konto-Zielgruppen-Qualifizierung | Konto tritt ein, wenn es einer Zielgruppen-Konto beitritt | Batch-orientiert; gut für ABM-Listeneinträge; Zielgruppe muss vordefiniert sein |
| Erstellungsereignis der Einkaufsgruppe | Konto tritt ein, wenn eine Einkaufsgruppe für das Konto erstellt wird | Ereignisgesteuert; durch Lead-Qualifizierung in eine Einkaufsgruppenrolle ausgelöst; mehr in Echtzeit |
| Kontoattributänderung | Konto tritt ein, wenn sich ein bestimmtes Attribut ändert (z. B. Absichtswert, Kontoebene) | Erfordert, dass das Auslöseattribut in Echtzeit oder nahezu in Echtzeit aktualisiert wird |

#### Entscheidung: Kanalmix für B2B-Pflege

Welche Kanäle sollte die Account-Journey verwenden, um kaufende Gruppenmitglieder einzubinden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur E-Mail | Die meisten B2B-Interaktionen erfolgen per E-Mail. Es gibt keine Infrastruktur für die SMS-Anmeldung | Einfachste Konfiguration; häufigstes B2B-Muster; fehlende Mobile-First-Kontakte |
| E-Mail + SMS | Organisation verfügt über ein Opt-in für SMS von Geschäftskontakten; dringende Benachrichtigungen sind erforderlich | SMS, die für zeitkritische Warnhinweise wirksam sind (Ereigniserinnerungen, Besprechungsbestätigungen); erfordert die Konfiguration des SMS-Anbieters |
| E-Mail + SMS + Verkaufswarnungen | Vollständiges Spektrum: Marketing-Pflege per E-Mail/SMS plus Benachrichtigungen des Vertriebsteams | Am umfassendsten; erfordert die Annahme des Warnhinweis-Workflows durch das Vertriebsteam; koordiniert Marketing- und Sales-Touchpoints |

#### Entscheidung: Verzweigungsstrategie für Journey

Wie sollte die Journey-Verzweigung basierend auf dem Konto- und Einkaufsgruppenstatus aussehen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Staging-basierte Verzweigung | Zweigstelle basierend auf der Kaufgruppenphase (z. B. Sensibilisierung, Überlegungen, Entscheidung) | Stimmt mit herkömmlichen funnel-Stadien überein; Inhalt wird Stadien zugeordnet; Verlauf löschen |
| Rollenbasierte Verzweigung | Verzweigung zum Senden verschiedener Inhalte an verschiedene Rollen der Einkaufsgruppe (technische Inhalte an Gutachter, ROI-Inhalte an wirtschaftliche Käufer) | Personalisierter; erfordert rollenspezifische Inhaltselemente; höherer Aufwand bei der Inhaltserstellung |
| Interaktionsbasierte Verzweigung | Verzweigung basierend auf den Interaktionsbewertungsschwellen (niedrige Interaktion = erneute Interaktion, hohe Interaktion = Beschleunigung) | Dynamisch und responsiv; passt sich dem tatsächlichen Verhalten an; kann komplexe Verzweigungen erstellen |

**UI-Navigation:** [!DNL AJO B2B Edition] > Account-Journey > Journey erstellen

**Wichtige Konfigurationsdetails:**

- Erstellen Sie die Arbeitsfläche der Konto-Journey mit der ausgewählten Eingabebedingung
- Konto-Journey-Knoten hinzufügen: E-Mail-Aktionen, SMS-Aktionen, Warteschritte, Bedingungsaufteilungen und Pfadverzweigung
- Erstellen von B2B-E-Mail-Inhalten mit dem B2B-E-Mail-Designer mit Markendesigns, visuellen Fragmenten und KI-unterstützter Inhaltserstellung
- Konfigurieren von Personalisierungs-Token, die auf Kontoattribute, Personenattribute und Einkaufsgruppendaten verweisen
- Wartezeiten zwischen Touchpoints festlegen (B2B-Journey verwenden in der Regel längere Wartezeiten: 3-7 Tage zwischen E-Mails)
- Beendigungskriterien definieren: Bedingungen, unter denen Konten die Journey verlassen (Einkaufsgruppe erreicht Qualifikationsschwellenwert, im CRM erstellte Opportunity, Konto-Opt-out)
- Konfigurieren von SMS-Aktionen bei Verwendung des SMS-Kanals (erfordert die Konfiguration des SMS-Anbieters und das Opt-in des Kontakts)
- Testen der Journey mit Testkonten vor der Veröffentlichung

**Wo die Optionen unterschiedlich sind:**

**Für Option A (Interesse an einer einzigen Lösung):**
Entwerfen Sie eine lineare Journey mit sequenziellen Phasen. Die Eingabe basiert auf einer einzelnen Konto-Zielgruppe oder einem Erstellungsereignis für die kaufende Gruppe. Ein E-Mail-Pflege-Track mit steigender Dringlichkeit und Tiefe des Inhalts.

**Für Option B (Interessen mehrerer Lösungen):**
Entwerfen Sie eine Journey mit parallelen Verzweigungen pro Lösungsinteresse. Verwenden Sie Bedingungsknoten, um Konten basierend auf vorhandenen Einkaufsgruppen zum entsprechenden Pflegepfad weiterzuleiten. Jede Verzweigung verfügt über eigene Inhalte und Bewertungsschwellen.

**Für Option C (KI-unterstützte Qualifizierung):**
Entwerfen Sie einen Journey, bei dem Bedingungsknoten den KI-Qualifizierungswert anstatt (oder zusätzlich zu) regelbasierten Schwellenwerten bewerten. Dynamische Pfadauswahl einschließen, bei der die KI bestimmt, ob ein Konto beschleunigt, verwaltet oder seine Priorität aufgehoben werden soll.

**Dokumentation zu Experience League:**

- [Übersicht über Account Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Konto-Journey-Knoten](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [B2B-E-Mail-Authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS-Kanal in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [KI-Assistent für E-Mail-Authoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Phase 4: Sales Alignment und CRM-Integration

**Anwendungsfunktionen:** [!DNL AJO B2B]: Konfiguration von Verkaufswarnungen, CRM-Vertriebserkenntnisse; [!DNL RT-CDP B2B]: Kontozielkonfiguration, Konto-Audience Activation

In dieser Phase wird die Brücke zwischen Marketing und Vertrieb geschlagen, indem E-Mails zu Verkaufswarnungen konfiguriert, CRM-Vertriebserkenntnisse für In-CRM-Sichtbarkeit bereitgestellt und optional Account-Zielgruppen für B2B-Ziele ([!DNL LinkedIn], [!DNL Marketo], CRM-Systeme) aktiviert werden.

#### Entscheidung: Strategie für Sales Alert Trigger

Wann sollte der Verkauf über den Status der Einkaufsgruppe eines Kontos benachrichtigt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Meilensteinbasierte Warnhinweise | Vertrieb benachrichtigen, wenn die Einkaufsgruppe bestimmte Meilensteine erreicht (qualifizierte, vollständige, hohe Interaktion) | Klare, diskrete Benachrichtigungen; verhindert Alarmmüdigkeit; kann allmähliche Interaktionstrends übersehen |
| Schwellenwertbasierte Warnhinweise | Benachrichtigen des Vertriebs, wenn der Interaktionswert einen definierten Schwellenwert überschreitet | Kontinuierliche Überwachung; kann mehrere Warnhinweise in Trigger bringen, wenn die Werte nahe des Schwellenwerts schwanken |
| Warnhinweise für Stadienübergänge | Benachrichtigen Sie den Vertrieb, wenn Sie Gruppenwechsel zu einem neuen Stadium erwerben (z. B. von der Erwägung zur Entscheidung) | Stimmt mit den Pipeline-Stadien überein; deutlichstes Signal für Verkaufsaktionen; erfordert klar definierte Stadiendefinitionen |

#### Entscheidung: CRM-Integrationstiefe

Wie tief sollten Kaufgruppendaten im CRM angezeigt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Verkaufswarnungen (keine CRM-interne Komponente) | Das Unternehmen verwendet keine [!DNL Salesforce] oder [!DNL Dynamics], oder die CRM-Integration ist nicht möglich | Geringster Integrationsaufwand; Vertrieb erhält E-Mail-Benachrichtigungen, aber kein CRM-Dashboard; eingeschränkte Sichtbarkeit |
| CRM-Vertriebseinblicke-Dashboard | Das Unternehmen verwendet [!DNL Salesforce] oder [!DNL Dynamics] und möchte, dass der Status der Einkaufsgruppe im CRM sichtbar ist | Erfordert die Installation des CRM-Pakets „Sales Insights“; bietet umfassende Informationen auf Kontoebene; für die meisten Implementierungen empfohlen |
| Vollständige bidirektionale CRM-Synchronisation | Kaufen von Gruppenphasen und -bewertungen Zurückschreiben in CRM-Objekte, Beeinflussung von CRM-Workflow und -Reporting | Höchste Integrationskomplexität; ermöglicht CRM-natives Pipeline-Reporting; benutzerdefinierte CRM-Konfiguration erforderlich |

**UI-Navigation:** [!DNL AJO B2B Edition] > Administration > Konfiguration von Warnhinweisen für den Vertrieb

**UI-Navigation:** [!DNL AJO B2B Edition] > Administration > CRM-Vertriebseinblicke > Konfigurieren

**Wichtige Konfigurationsdetails:**

- Konfigurieren von E-Mail-Vorlagen für Verkaufswarnungen: Kaufgruppenstatus, engagierte Personas, Interaktionswert und empfohlene nächste Aktionen
- Definieren Sie Regeln für die Weiterleitung von Warnhinweisen: Welche Vertriebsmitarbeiter oder Teams erhalten Warnhinweise basierend auf Kontoeigentum, Gebiet oder Lösungsinteresse?
- Installieren und Konfigurieren von CRM Sales Insights für [!DNL Salesforce] oder [!DNL Dynamics 365]
- Ordnen Sie Einkaufs-Gruppendaten CRM-Objekten zu, damit der Vertrieb die Zusammensetzung, die Interaktion und den Journey-Fortschritt von Einkaufs-Gruppen innerhalb seines CRM-Workflows anzeigen kann
- Optional können Sie Kontozielverbindungen konfigurieren, um Kontozielgruppen für [!DNL LinkedIn] (für ABM-Werbung), [!DNL Marketo Engage] (für Follow-up auf Lead-Ebene) oder andere B2B-Ziele zu aktivieren

**Dokumentation zu Experience League:**

- [Warnungs-E-Mails für Verkauf](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM-Vertriebserkenntnisse](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [Übersicht über Ziele](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/home)
- [Ziel für abgeglichene LinkedIn-Zielgruppen](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/social/linkedin)

### Phase 5: Reporting und Optimierung

**Anwendungsfunktionen:** [!DNL AJO B2B]: B2B-Analytics-Dashboards

In dieser Phase wird ein Framework für das Reporting und die Analyse erstellt, um die Leistung der Einkaufsgruppe, die Effektivität beim Account-Journey und die Pipeline-Wirkung zu messen. [!DNL AJO B2B Edition] bietet integrierte Analytics-Dashboards; [!DNL CJA B2B Edition] erweitert die Analyse (falls lizenziert) um tiefere kanalübergreifende Einblicke auf Kontoebene.

#### Entscheidung: Berichterstattungsansatz

Welche Analytics-Tools sollten für die laufende Leistungsüberwachung konfiguriert werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur Dashboards [!DNL AJO B2B] | Die integrierten Dashboards von [!DNL AJO B2B Edition] reichen für den Kauf von Gruppen- und Journey-Metriken aus | Schnellste Konfiguration; deckt B2B-Kernmetriken ab; begrenzte benutzerdefinierte Analysefunktionen |
| [!DNL AJO B2B] Dashboards + [!DNL CJA B2B Edition] | Das Unternehmen benötigt eine tiefere kanalübergreifende Analyse, eine Analyse der Einkaufsgruppe, eine Korrelation der Chancen und eine benutzerdefinierte Attribution. | Erfordert [!DNL CJA B2B Edition] Lizenz; umfassendste; unterstützt Freiformanalyse auf Kontoebene |
| [!DNL AJO B2B] Dashboards + CRM-Berichte | Das Unternehmen zieht es vor, Pipeline-Berichte im CRM zu zentralisieren und Gruppenmetriken zu kaufen. | Erfordert die Entwicklung eines CRM-Dashboards, kombiniert Marketing- und Verkaufsmetriken an einem Ort und ist auf CRM-Reporting-Funktionen beschränkt |

**UI-Navigation:** [!DNL AJO B2B Edition] > Dashboards > Interaktionsübersicht / Intelligentes Dashboard

**Wichtige Konfigurationsdetails:**

- Greifen Sie auf das Dashboard für [!DNL AJO B2B]-Interaktionen zu, um die Bewertungen der Einkaufsgruppeninteraktion, Vollständigkeitsraten und die Staging-Verteilung zu überwachen
- Zugriff auf das intelligente Dashboard für KI-gesteuerte Insights in Bezug auf Kontobereitschaft und Pipeline-Qualität
- Bei Verwendung von [!DNL CJA B2B Edition]: Konfigurieren einer Account-basierten CJA-Verbindung einschließlich [!DNL AJO B2B] Datensätze, Einrichten einer B2B-Datenansicht mit Einkaufsgruppen- und Account-Containern und Erstellen einer Arbeitsbereichsanalyse für den Kaufgruppenfortschritt, die Opportunity-Korrelation und die Attribution
- Definieren der Berichtskadenz: wöchentliche Leistungsüberprüfungen der Einkaufsgruppe, monatliche Analyse der Pipeline-Auswirkungen, vierteljährliche Programmoptimierung
- Erstellen Sie Anmerkungen für wichtige Ereignisse (Kampagnenstarts, Inhaltsaktualisierungen, Änderungen des Bewertungsmodells), um sie mit Leistungstrends zu korrelieren

**Dokumentation zu Experience League:**

- [B2B-Analytics-Dashboards](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Interaktions-Dashboard](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligentes Dashboard](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [Übersicht über CJA B2B edition](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## Überlegungen bei der Implementierung

In den folgenden Abschnitten werden Leitplanken, häufige Fallstricke, Best Practices und Kompromissentscheidungen behandelt, die bei der Implementierung zu beachten sind.

### Leitplanken und Beschränkungen

- Die Limits für die Journey von [!DNL AJO B2B Edition]-Konten, einschließlich der maximalen Anzahl gleichzeitiger Journey-Konten und der maximalen Konten pro Journey, folgen den [!DNL AJO B2B Edition] Produkt-Leitplanken - [AJO B2B-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition] unterstützt bis zu 50 B2B-Schemaklassen und befolgt standardmäßige Profil- und Segmentierungsleitplanken [Echtzeit-Kundenprofil-Leitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)
- Die Evaluierung der Konto-Zielgruppe erfolgt nach Batch-Zeitplänen. Aktualisierungen der Echtzeit-Konto-Zielgruppe werden nicht für alle Segmenttypen unterstützt [Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- Die Aufnahme in den B2B-Quell-Connector hat minimale Zeitplanungsintervalle (in der Regel 15 Minuten für [!DNL Marketo], variierend für CRM-Quellen) [Aufnahme-Leitplanken](https://experienceleague.adobe.com/de/docs/experience-platform/ingestion/guardrails)
- E-Mail-Kanaloberflächen sind auf 10 pro Kanaltyp pro Sandbox beschränkt - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/get-started/guardrails)

### Häufige Fehler

- **Zu viele Rollen pro Einkaufsgruppe definieren:** Überhöhte Angabe von Rollen (z. B. 8-10 verschiedene Rollen erforderlich) macht es für Einkaufsgruppen fast unmöglich, Vollständigkeitsschwellen zu erreichen. Beginnen Sie mit 3-5 grundlegenden Rollen und erweitern Sie sie, wenn das Modell sich weiterentwickelt.
- **Festlegen von Schwellenwerten für Interaktionswerte auf zu hohe oder zu niedrige Werte:** Wenn die Schwellenwerte zu hoch sind, qualifizieren sich keine Einkaufsgruppen, wodurch die Pipeline ausgehungert wird. Wenn es zu niedrig ist, fluten unqualifizierte Accounts den Verkauf. Beginnen Sie mit der Analyse historischer Daten (falls verfügbar) und iterieren Sie basierend auf Vertriebs-Feedback.
- **Ignorieren der Qualität der Abwicklung von Personen zu Konten:** Wenn Personen nicht korrekt mit Konten verknüpft sind, fehlen in Einkaufsgruppen Mitglieder, selbst wenn die richtigen Personen eingestellt sind. Investieren Sie in die Qualität der Identitätsauflösung, bevor Sie Gruppen-Journey kaufen.
- **Übernachrichten von Kontakten in mehreren Einkaufsgruppen:** Ein einzelner Kontakt kann Rollen in mehreren Einkaufsgruppen innehaben (z. B. ein CTO, der ein technischer Gutachter für CRM- und Data Platform-Käufe ist). Ohne Frequenzverwaltung erhält diese Person E-Mails von jeder aktiven Journey. Implementieren Sie Cross-Journey-Häufigkeitsregeln.
- **Vernachlässigung der Vertriebsunterstützung:** Vertriebsteams müssen verstehen, wie Kaufgruppendaten, Interaktionswerte und Verkaufswarnungen zu interpretieren sind. Ohne Schulung und Übernahme schlägt die Übergabe von Marketing an den Verkauf unabhängig von der Datenqualität fehl.
- **Account-Journey wie Personen-Journey behandeln:** Account-Journey werden auf Kontoebene ausgeführt und senden E-Mails an Personen innerhalb der Einkaufsgruppen des Accounts. Beim Journey-Design muss berücksichtigt werden, dass mehrere Personen Nachrichten pro Ausführung des Kontoknotens erhalten, was sich grundlegend von den Journey auf [!DNL AJO] unterscheidet.

### Best Practices

- **Beginnen Sie mit einem Lösungsinteresse und erweitern Sie** - Prüfen Sie, ob das Modell für einen Kaufvorgang funktioniert, bevor Sie es auf mehrere Lösungsinteressen skalieren. Auf diese Weise kann das Team Rollenvorlagen, Bewertungsmodelle und Inhalte verfeinern, bevor sie die Komplexität erhöhen.
- **Einkaufsgruppenrollen an CRM-Vertriebsprozess anpassen** — Ordnen Sie die Einkaufsgruppenrollen den Personas zu, die das Vertriebsteam bereits erkennt. Dieselbe Sprache verwenden (Economic Buyer, Champion usw.) Die Übergabe erfolgt intuitiv.
- **Implementieren einer Feedback-Schleife mit dem Vertrieb** - Sammeln Sie regelmäßig Sales-Feedback zur Qualität von Marketing-qualifizierten Accounts. Verwenden Sie dieses Feedback, um die Schwellenwerte für die Interaktionsbewertung und die Kriterien für die Rollenqualifizierung anzupassen.
- **Inhalte für Rollen, nicht nur für Phasen, gestalten** - Verschiedene Rollen für Einkaufsgruppen benötigen unterschiedliche Inhalte: Führungskräfte wünschen sich einen ROI und eine strategische Wirkung, technische Gutachter wünschen sich Details zur Architektur und Integration, Endbenutzer wünschen sich benutzerfreundliche Demonstrationen. Ordnen Sie Inhaltselemente Rollen zu, um eine effektivere Pflege zu gewährleisten.
- **Vorzeitige Einrichtung von CRM-Vertriebserkenntnissen** - Warten Sie nicht, bis die vollständige Journey verfügbar ist, um die CRM-Sichtbarkeit bereitzustellen. Vertriebsteams müssen frühzeitig erkennen, wie sich die Daten der Einkaufsgruppe bilden, um Feedback zur Rollengenauigkeit und zum Account-Targeting zu geben.
- **Strategische Verwendung von Warteschritten** - B2B-Kaufzyklen sind lang. Account-Journey-Warteschritte sollten diese Realität widerspiegeln (5-14-tägige Intervalle zwischen Berührungen) und nicht die Dringlichkeit im Verbraucherstil (1-3 Tage).
- **Überwachen der Interaktionsgeschwindigkeit, nicht nur des Interaktionswerts** - Eine Einkaufsgruppe, die innerhalb von zwei Wochen von Score 20 auf 80 steigt, signalisiert eine stärkere Absicht als eine, die innerhalb von sechs Monaten 80 erreicht. Konfigurieren Sie Scoring und Qualifizierung entsprechend der Geschwindigkeit.

### Entscheidungen über Kompromisse

Die folgenden Kompromisse sollten auf der Grundlage der spezifischen Anforderungen Ihres Unternehmens bewertet werden.

#### Vollständigkeit der Einkaufsgruppe im Vergleich zum Pipeline-Volumen

Das Erfordernis, dass alle Rollen erfüllt sein müssen, bevor eine Einkaufsgruppe qualifiziert wird, maximiert die Pipeline-Qualität, kann aber das Volumen qualifizierter Konten stark einschränken, insbesondere für neue Produkte oder Märkte, in denen die Datenbank des Unternehmens nur begrenzt abgedeckt ist.

- **Höhere Vollständigkeits-Schwellenwerte:** Pipeline-Qualität; Verkäufe erhalten voll gebildete Einkaufsgruppen; höhere Gewinnraten pro Konto
- **Niedrigere Vollständigkeits-Schwellenwerte für Vorteile:** Pipeline-Volumen; mehr Konten erreichen den Umsatz; breitere Abdeckung; höheres Volumen, aber möglicherweise geringere Qualität
- **Empfehlung:** Beginnen Sie mit einem moderaten Schwellenwert (60-70 % Rollenabdeckung) und passen Sie ihn auf der Grundlage der tatsächlichen Gewinnratendaten an. Steigern Sie bei etablierten Märkten mit guter Datenabdeckung auf über 80 %. Akzeptieren Sie für neue Märkte zunächst 50-60 % und verwenden Sie Kampagnen zur Vervollständigung der Käufergruppe, um Lücken zu schließen.

#### Scoring-Granularität im Vergleich zu einfacher Bedienung

Hochgradig granulare Scoring-Modelle (mit Dutzenden von Aktivitätstypen, Neuheitsgewichtung und rollenspezifischer Scoring) liefern präzisere Qualifizierungssignale, sind jedoch schwieriger zu verwalten, zu erklären und Fehler zu beheben.

- **Höhere Granularität begünstigt** Präzision der Qualifizierung; differenzierte Differenzierung zwischen den Accounts; bessere Abstimmung mit komplexen Einkaufsprozessen
- **Geringere Granularität begünstigt:** Einfachheit des Betriebs; einfacher zu pflegen und dem Vertrieb zu erklären; schnellere Implementierung; weniger Randfälle
- **Empfehlung:** Beginnen Sie mit einem einfachen Scoring-Modell (10-15 Aktivitätstypen, einheitliche Punktwerte) und fügen Sie Komplexität nur dann hinzu, wenn das einfache Modell nicht in der Lage ist, die Kontenqualität zu unterscheiden. Dokumentieren Sie das Scoring-Modell sorgfältig für die Vertriebsausrichtung.

#### Einzelne Journey und mehrere spezialisierte Journey

Eine einzige, umfassende Account-Journey, die alle Phasen und Lösungsinteressen auf einer Arbeitsfläche verarbeitet, bietet einheitliche Kontrolle, kann aber unhandlich werden. Mehrere spezialisierte Journey (eine pro Stufe oder Interesse an einer Lösung) sind einfacher, aber schwieriger zu koordinieren.

- **Einzel-Journey bevorzugt:** ganzheitliche Betrachtung; einfacher für konsistentes Timing und Messaging; einfacher zu überwachen; ein Ort für alle Logiken
- **Mehrere Journey bevorzugen:** Modularität; einfacher zu aktualisieren, ohne andere zu beeinflussen; verschiedene Teams können verschiedene Journey besitzen; saubereres Canvas-Design
- **Empfehlung:** Für Option A ist eine einzige Journey geeignet. Verwenden Sie für die Optionen B und C eine primäre „Orchestrierungs“-Journey, die Konten an spezialisierte Unter-Journey je nach Lösungsinteresse oder Kaufphase weiterleitet.

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
- [Quellen - Übersicht](https://experienceleague.adobe.com/de/docs/experience-platform/sources/home)
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
