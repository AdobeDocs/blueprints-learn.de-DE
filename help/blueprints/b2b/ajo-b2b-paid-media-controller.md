---
title: Bezahlter AJO B2B-Medien-Controller
description: Priorität von Kampagnen und Aktivierung von Konten für Paid-Media-Ziele
solution: Journey Optimizer B2B Edition
source-git-commit: dff5608af92fa1140419d6834d8374df75de98d3
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Überblick

Marketing-Teams, die skalierte, bezahlte B2B-Medien betreiben, stehen vor einem wiederkehrenden Problem: **Konten landen gleichzeitig in mehreren Kampagnen** (Persona, Kategorieerkennung, lösungsgesteuert, Verfolgung), was das Messaging verwässert, zu Zielgruppenermüdung führt und manuelle Listenarbeit - Uploads, Ausschlüsse und Unterdrückung - über LinkedIn Account Match (Account-Ziel) erzwingt. Ohne **Wasserfallpriorisierung** und **automatisierte Kampagnenzuweisung** kann nicht an einer Stelle entschieden werden, welches Konto welche Nachricht erhält, und Vorgänge werden nicht skaliert.

Der **Paid Media Controller** ist eine perfekte Lösung für dieses Problem. Sie verwendet **Adobe Journey Optimizer B2B edition (AJO B2B)** und **Adobe Experience Platform (AEP)** gemeinsam: Eine **Account-Journey** liest eine Zielgruppe mit qualifiziertem Account aus Real-Time CDP, wendet **Split-Path (Waterfall)-Logik** an, um jedes Account genau einer Kampagnenebene zuzuweisen, und **aktiviert jeden Pfad direkt** auf Paid-Media-Ziele (**z. B. LinkedIn Matched Audiences**) - ohne manuelle Listenübergaben. Das Ergebnis ist Präzisionskontrolle, weniger Überschneidungen und ein wiederholbares Muster für die Mehrkanal-Orchestrierung bezahlter B2B-Medien.

## Anwendungsfall: Eine Story für Marketing-Experten: Warum ein Controller wichtig ist

*Maya führt bezahlte Medien für eine globale B2B-Marke. Ihr Team führt Dutzende von Kampagnen durch: Grundlagenbewusstsein, Kategorieabsicht (Journey, Daten, Inhalte), lösungsorientierte Programme, Personenkampagnen und gewinnbringende Aktivitäten. Sie hat ein Problem.*

**Das Problem:** Konten werden in mehreren Kampagnen angezeigt. Ein Journey-Account mit einer hohen Absicht befindet sich ebenfalls in einer breiten Bewusstseinsliste; ein Verfolgungskonto erhält weiterhin persönliche Anzeigen. Listen-Uploads und -Ausschlüsse erfolgen manuell. Jedes Mal, wenn Sales eine „Must-Win“-Liste oder eine neue Persona-Kampagne startet, exportiert ihr Team Zielgruppen erneut, gleicht Überschneidungen in Tabellen ab und lädt sie erneut auf LinkedIn und andere Plattformen hoch. Sie ist langsam, fehleranfällig und nicht skalierbar.

**Was sie möchte:** Ein Ort, an dem jedes qualifizierte Konto einmal ausgewertet wird, der *relevantesten* Kampagne mit klaren Prioritätsregeln (Wasserfall) zugewiesen und automatisch an das richtige Paid-Media-Ziel gesendet wird. Keine manuellen Listenübergaben. Wenn sich Daten oder Strategien ändern, werden Konten neu ausgewertet und zwischen Kampagnen verschoben, ohne dass ihr Team Listen berührt.

**Antwort von Adobe:** Wenn **AJO B2B und AEP zusammenarbeiten** kann Maya einen einzigen **Paid Media Controller**-Journey ausführen: AEP und Real-Time CDP halten die Daten und eine primäre Zielgruppe für „qualifizierte Konten“. AJO B2B führt eine Account-Journey durch, die **Split-Path-Logik** (Wasserfall) verwendet, um jedes Konto in die richtige Ebene zu leiten - z. B. Targeting → Lösungsorientiert → Persona → Category Awareness → Foundation Awareness - und **Activate to Destination** jeden Pfad an die richtige LinkedIn-Kampagne (oder eine andere) sendet. Eine Journey, eine Quelle der Wahrheit, keine manuellen Listenexporte. Das ist das Paid-Media-Controller-Muster - und so ermöglicht Adobe Präzision und Skalierung für bezahlte B2B-Medien.

## Warum es für B2B-Unternehmen wichtig ist:

Unternehmen, die dieses Muster übernehmen, können die manuelle Unterdrückungs- und Ausschlusslogik vollständig eliminieren (z. B. 100 % der Überschneidungsauflösung, die im Journey verarbeitet wird), auf **Zehntausende von Konten** über einen einzigen Controller skalieren und eine **zentrale Datenquelle** für welches Konto welche Kampagne verwendet wird, beibehalten. Das System **passt sich automatisch an** wenn sich der Kampagnenfokus, die Zielgruppen und die Verkaufsziele ändern, ohne dass Listen erneut exportiert oder erneut auf jede Plattform hochgeladen werden müssen. Für B2B-Unternehmen, die mehrere Kampagnen mit bezahlten Medien ausführen, bietet das Paid-Media-Controller-Muster die Klarheit, Kontrolle und Automatisierung, die manuelle Listen-Workflows nicht bieten können.

Die folgenden KPIs stimmen gut mit der Messung des Erfolgs überein:

- **Awareness:** sehen Zielgruppen-Accounts die richtigen Anzeigen und wechseln schneller zu den richtigen Kampagnen?
- **Interaktion:** sind Interaktion und Konversion besser, wenn Überschneidungen entfernt werden?
- **Effizienz:** Wie viel hat die manuelle Listenarbeit (Uploads, Ausschlüsse, Unterdrückung) verringert?
- **Kosten:** ändern sich die Kosten pro erworbenem Konto oder Opportunity durch die automatisierte Orchestrierung?

## Paid Media Journey-Orchestrierung

Ein gängiges Anwendungsbeispiel, und der Schwerpunkt dieses Blueprints, ist **B2B Paid Media Journey Orchestration**: Es wird sichergestellt, dass jedes qualifizierte Konto genau einer Kampagnenebene zugewiesen und für das richtige Paid-Media-Ziel aktiviert wird, ohne Überschneidungen oder manuelle Übergaben.

Die Controller-Journey **liest** eine Zielgruppe mit qualifiziertem Konto (integriert in Real-Time CDP aus AEP-Daten), **bewertet** jedes Konto anhand von Split-Path-(Waterfall-)Bedingungen - z. B. Verfolgung → lösungsgeführten → Persona → Category Intent → Foundation - und **aktiviert** jeden Pfad zum entsprechenden Ziel (z. B. LinkedIn Matched Audiences für jede Kampagne).

**Account-orientierte Lösung:** Der Schwerpunkt des Paid Media Controllers liegt **Accounts** und deren **Kampagnenzuweisung**. Die technische Einrichtung unterstützt die Daten und Zielgruppen, die qualifizierte Konten darstellen, sowie deren Attribute (z. B. Absicht, Segment, Persona). Dies ist für eine erfolgreiche Segmentierung auf Kontoebene und eine Journey-basierte Orchestrierung erforderlich.

## Anforderungen

Für die Lösung mit Schwerpunkt auf Kunden sind die folgenden Anwendungen und Services erforderlich:

- **Adobe Journey Optimizer B2B edition** - Account-Journey, Split-Path-Logik (Wasserfall), Für Ziel aktivieren.
- **Adobe Real-time Customer Data Platform (RTCDP) B2B edition** - Kontoprofile, Kontozielgruppen (z. B. qualifizierte Konten für bezahlte Medien).

## Architektur

Allgemeiner Fluss:

1. **Daten und Zielgruppen** - AEP speichert Profile und Ereignisse; Real-Time CDP B2B erstellt Account-Zielgruppen (z. B. „Paid Media Eligible Accounts„), die als Journey-Einstiegs-Zielgruppe verwendet werden.
2. **Orchestration** — AJO B2B-Account-Journey: **Zielgruppe lesen** (qualifizierte Konten) → **Aufspaltungspfad** (Wasserfall: z. B. Verfolgung → lösungsgeführtes → Persona → Category → Foundational) → **Für Ziel aktivieren** (pro Pfad zu LinkedIn oder anderen bezahlten Medien).
3. **Ziele** - Bezahlte Medienkanäle (z. B. LinkedIn Matched Audiences) erhalten eine Aktivierung auf Kontoebene von jedem Journey-Pfad; keine manuellen Listen-Uploads.

## Architekturdiagramm

<img src="assets/ajo-b2b-paid-media-activation-architecture.svg" alt="Architektur mit bezahltem B2B-Medien-Controller in AJO" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Datenmodellierung in B2B-AEP

Bei jeder datengesteuerten Orchestrierung ist der Entwurf eines Schemas wichtig. Account- und Personenprofile in AEP/RTCDP müssen die in **Split-Path-Bedingungen** verwendeten Attribute enthalten (z. B. Verfolgungs-Flag, Lösungsinteresse, Persona, Absichtskategorie, Interaktionswert). B2B-Schemas (XDM Business Account, XDM Individual Profile, relationale) sollten Ihre Hierarchie und Datenquellen darstellen. Weitere Informationen finden Sie unter [RTCDP B2B-](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) und in der [AJO B2B-Dokumentation](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/home).

**Hinweis** Die Split-Path-Logik auf der Journey verwendet Profildaten und, sofern unterstützt, relationale Daten. Stellen Sie sicher, dass die Felder, die Sie für die Wasserfalllogik benötigen, auf der Journey verfügbar sind.

### Leitlinien

- **Journey Optimizer B2B edition** - In der [Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-journey-optimizer-b2b.html) finden Sie Informationen zu Journey-Beschränkungen, Knotenbeschränkungen und Ziel-Unterstützung.
- **Real-Time CDP** - Siehe [RTCDP](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/guardrails/overview)Leitplanken für Segmentierungs- und Aktivierungsbeschränkungen.

## Implementierung

Die folgenden Schritte enthalten Anleitungen für die Implementierung des Paid Media Controllers mit AJO B2B und AEP.

### Vorausgesetzte Schritte

1. **Definieren von Konto-Zielgruppen und Datenmodellen in Real-Time CDP B2B.**

   Erstellen Sie die **Zielgruppe mit qualifiziertem Konto** (z. B. „Berechtigte Paid-Media-Konten„), die auf die Controller-Journey gelangen. Verwenden Sie Segment Builder und die Konto-/Personenattribute, die die Eignung definieren (z. B. Geografie, Segment, MQA-Status). Diese Zielgruppe ist der einzige Einstiegspunkt für die Journey.

2. **Definieren der Kampagnenhierarchie und der Aufspaltungslogik.**

   Dokumentieren Sie die Wasserfallreihenfolge (z. B. Verfolgung → lösungsorientiert → Persona → Category → Foundational) und die Bedingungen für jeden Pfad (welche Attribute oder Zielgruppen ein Konto qualifizieren). Stellen Sie sicher **dass sich Bedingungen in der richtigen** gegenseitig ausschließen (von oben nach unten): Ein Konto sollte höchstens mit einem Pfad übereinstimmen, dem ersten, der „true“ auswertet.

3. **Konfigurieren von Zielen.**

   Richten Sie Paid-Media-Ziele (z. B. abgeglichene LinkedIn-Zielgruppen) in AEP/RTCDP ein und stellen Sie sicher, dass sie für die Aktivierung über AJO B2B verfügbar sind. Ordnen Sie jedem Ziel Kontokennungen und alle erforderlichen Attribute zu.

### Paid Media Controller-Konfiguration

1. **Erstellen Sie die Controller-Journey in AJO B2B.**

   - **Zielgruppe lesen:** Wählen Sie die Zielgruppe mit qualifiziertem Konto aus Real-Time CDP aus.
   - **Aufspaltungspfad:** Fügen Sie Knoten in der Wasserfallreihenfolge hinzu. Jeder Knoten bewertet Bedingungen (z. B. „Verfolgung der Zielgruppe“, „Lösungsinteresse = X“, „Persona = Y“, „Absichtskategorie = Z„). Konten, die der entsprechenden Aktivierung entsprechen, werden getrennt. Andere gehen zur nächsten Aufteilung über.
   - **Für Ziel aktivieren:** Fügen Sie für jeden Pfad den Knoten Für Ziel aktivieren zur richtigen LinkedIn-Kampagne/zum richtigen Ziel (oder einer anderen) hinzu.

2. **Gegenseitige Exklusivität validieren.**

   - Bestätigen Sie, dass jedes Konto nur einen Pfad eingibt (die erste übereinstimmende Bedingung).
   - Überprüfen Sie die Aktivierung: Konten erscheinen im richtigen Ziel und werden wie vorgesehen von Kampagnen mit niedrigerer Priorität ausgeschlossen.

## Implementierungsdiagramm

<img src="assets/ajo-b2b-paid-media-controller-canvas.svg" alt="Arbeitsfläche des bezahlten AJO B2B-Medien-Controllers" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

### 4.2.3. Zielgruppenaktivierung

1. **Für LinkedIn aktivieren (und andere Ziele).**

   Verwenden Sie auf der Journey „Für Ziel aktivieren“, um jeden Pfad an die richtige Paid-Media-Zielgruppe zu senden. Kein manueller Export oder Upload von Listen; die Journey-Laufwerke aktivieren, da Konten durch Pfade fließen.

2. **Überwachen und Optimieren.**

   Verwenden Sie das Journey-Reporting, um Volumes pro Pfad zu überwachen.

## Zusammenfassung

Der Blueprint **Paid Media Controller** zeigt, wie **AJO B2B und AEP** zusammenarbeiten, um B2B-Marketing-Experten eine einzige, automatisierte Möglichkeit zu bieten, Konten Kampagnen zuzuweisen und für bezahlte Medien zu aktivieren: eine Master-Zielgruppe, eine Journey, eine Wasserfall-Split-Logik und eine direkte Aktivierung für Ziele - keine manuellen Listenübergaben. Es etabliert ein wiederholbares Muster für die Paid-Media-Orchestrierung im B2B-Bereich für mehrere Kanäle und hilft bei der Reduzierung von Überschneidungen, der Verbesserung der Relevanz und der Skalierung von Vorgängen.

## Verwandte Dokumentation

- [Kaufen von Blueprint für gruppenbasiertes Marketing und Journey-Management](https://experienceleague.adobe.com/de/docs/blueprints-learn/architecture/b2b-activation/b2b-buying-group-journeys) — Konto- und Kaufen von Journey-Gruppen in AJO B2B.
- [Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b) - Produktdokumentation.
- [Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) - Kontozielgruppen und -aktivierung.
