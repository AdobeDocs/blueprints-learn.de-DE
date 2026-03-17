---
title: Web-Personalization für anonyme Besucher
description: Erfahren Sie, wie Sie nicht identifizierten Besuchern auf der Grundlage von Verhaltenssignalen während der Sitzung personalisierte Webinhalte bereitstellen können.
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: ccfd8c987a0090ca690e15a4bd89f4d96ec9c01f
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 1%

---

# Web-Personalisierung für anonyme Besucher

Dieser Referenzplan bietet Implementierungshandbücher für die Bereitstellung personalisierter Web-Inhalte für anonyme (nicht identifizierte) Besucher basierend auf Verhaltenssignalen in der Sitzung. Es deckt den gesamten Implementierungslebenszyklus ab - von der [!DNL Web SDK] und der Definition der Edge-Zielgruppe über die Bereitstellung von Inhalten bis hin zum Performance-Reporting - und ist für Lösungsarchitekten, Marketing-Technologen und Implementierungstechniker konzipiert, die mit [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) und [!DNL Adobe Experience Platform] (AEP) arbeiten.

Verwenden Sie diesen Plan, um die Architektur zu verstehen, Implementierungsoptionen zu bewerten, fundierte Konfigurationsentscheidungen zu treffen und die entsprechende Experience League-Dokumentation für jede Implementierungsphase zu finden.

Das Muster funktioniert mit begrenzten Daten - nur was in der aktuellen Sitzung beobachtet werden kann und alle anonymen Edge-Profile, die von vorherigen Besuchen mit demselben Gerät oder Cookie gesammelt wurden. Dadurch eignet er sich für die Top-of-funnel-Personalisierung, bei der der Besucher über kein Konto verfügt oder sich nicht authentifiziert hat.

## Anwendungsfall - Übersicht

Die Web-Personalization für anonyme Besucher erfüllt die geschäftlichen Anforderungen, relevante, personalisierte Inhalte für Website-Besuchende bereitzustellen, die noch nicht identifiziert wurden - sie haben sich nicht angemeldet, haben keine bekannte Identität und können nicht in ein einheitliches Kundenprofil aufgelöst werden. Trotz dieser Einschränkung ist eine sinnvolle Personalisierung mithilfe von Verhaltenssignalen in der Sitzung erreichbar: angezeigte Seiten, Besuchszeit vor Ort, Bildlauftiefe, Verweisquelle, geografischer Standort, Gerätetyp und UTM-Kampagnenparameter.

Dieses Muster verwendet Web-Kanaloberflächen und Code-basierte Erlebnisse von AJO, um Seiteninhalte in Echtzeit zu ändern. Die Edge-Segmentierung ist die primäre Auswertungsmethode, da Entscheidungen mit einer Latenz von Untersekunden getroffen werden müssen, wenn der Besucher auf der Website navigiert. Der [!DNL Web SDK] erfasst Verhaltenssignale und sendet sie an den [!DNL AEP Edge Network], wo die von Edge ausgewerteten Zielgruppenregeln bestimmen, welche Inhaltsvariante bereitgestellt werden soll.

Im Gegensatz zur Web-/App-Personalisierung für bekannte Besucher, die das vollständige einheitliche Profil und die Segmentzugehörigkeit nutzt, ist dieses Muster auf Daten beschränkt, die in der aktuellen Sitzung beobachtet werden können, sowie auf alle anonymen Edge-Profile, die mit der ECID des Besuchers verknüpft sind ([!DNL Experience Cloud ID]). Diese Unterscheidung ist für die Implementierungsplanung von entscheidender Bedeutung: Die für die Personalisierung verfügbaren Verhaltenssignale sind auf das beschränkt, was der [!DNL Web SDK] erfasst und was über die Cookie-basierte ECID sitzungsübergreifend im Edge-Profilspeicher beibehalten wird.

## Wichtige Geschäftsziele

Die folgenden Geschäftsziele werden durch dieses Anwendungsfallmuster unterstützt.

**[Website-Interaktion steigern](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Verbesserung der Besuchszeit auf der Site, der Seiten pro Sitzung und der Interaktion mit Web-Inhalten durch relevante Erlebnisse, die auf anonyme Besuchersignale zugeschnitten sind.

| KPIs |
| --- |
| Time On (Web)-Seite |
| Interaktion |
| Konversionsraten |

**[Bereitstellen personalisierter Kundenerlebnisse](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Passen Sie Inhalte, Angebote und Nachrichten an individuelle Vorlieben, Verhaltensweisen und Lebenszyklusphasen an - auch für Besuchende, die sich noch nicht identifiziert haben.

| KPIs |
| --- |
| Interaktion |
| Konversionsraten |
| Kundenzufriedenheit (CSAT) |

**[Erhöhung der Konversionsraten](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbessern Sie den Prozentsatz der Besucher und potenziellen Kunden, die die gewünschten Aktionen wie Käufe, Anmeldungen oder Formularübermittlungen durchführen, indem Sie die relevantesten Inhalte basierend auf dem Verhaltenskontext präsentieren.

| KPIs |
| --- |
| Konversionsraten |
| Lead-Konversion |
| Kosten pro Lead |

## Beispiele für taktische Anwendungsfälle

Die folgenden Beispiele veranschaulichen spezifische Szenarien, in denen dieses Muster angewendet werden kann.

- **Überschriften-A/B-Test der Landingpage basierend auf der Empfehlungsquelle** - Testen Sie verschiedene Überschriften für Besucher, die aus Google, Social Media oder Direct Traffic kommen, um die Interaktion durch den Akquisekanal zu optimieren
- **Empfehlungen zur Kategorieaffinität basierend auf dem Durchsuchungsverhalten** — Anzeige von Produkt- oder Inhaltsempfehlungen basierend auf in der aktuellen Sitzung betrachteten Seiten, um die Erkennung und Konversion zu verbessern
- **Exitintent-Angebot für Besucher, die gerade die Website verlassen** — Präsentieren Sie ein Werbeangebot oder ein Lead-Erfassungsformular, wenn Verhaltenssignale darauf hindeuten, dass der Besucher die Website verlassen wird.
- **Geozielgerichtetes Werbebanner** - Zeigt standortspezifische Werbeaktionen, Store-Locator-Inhalte oder regionale Angebote basierend auf dem geografischen Standort des Besuchers an
- **Gerätespezifische Inhaltslayoutoptimierung** - Passen Sie das Inhaltslayout, die Bildgrößen und die CTA-Platzierung an, je nachdem, ob sich der Besucher auf dem Desktop, Tablet oder Mobilgerät befindet
- **Willkommensnachrichten für neue und wiederkehrende Besucher** — Differenzierung des Erlebnisses für Erst- und wiederkehrende anonyme Besucher mithilfe der ECID-Persistenz über Sitzungen hinweg
- **Inhaltsempfehlungen basierend auf angezeigten Seiten in der aktuellen Sitzung** - Dynamisches Aufdecken verwandter Artikel, Produkte oder Ressourcen basierend auf den Seiten, die der Besucher bereits angesehen hat
- **Dynamisches Hero-Banner basierend auf UTM-Kampagnenparametern** - Personalisieren Sie das Hero-Banner so, dass es der Botschaft oder dem Kreativen aus der verweisenden Kampagne entspricht.

## Wichtige Performance-Indikatoren

Verwenden Sie die folgenden KPIs, um die Effektivität dieses Anwendungsfallmusters zu messen.

| KPI | Beschreibung | Messansatz |
| --- | --- | --- |
| Personalization-Impressionsrate | Prozentsatz der zulässigen Seitenansichten, bei denen personalisierte Inhalte bereitgestellt wurden | AJO-Kampagnenbericht: Impressionen/Seitenansichten insgesamt |
| Clickthrough-Rate (CTR) | Prozentsatz der personalisierten Inhaltsimpressionen, die zu einem Klick führen | AJO-Kampagnenbericht: Klicks/Impressionen |
| Interaktionssteigerung | Verlängerung der Zeit auf der Seite, Seiten pro Sitzung oder Bildlauftiefe für personalisierte bzw. Standardinhalte | Vergleich von CJA Workspace: Personalisierte Kohorte vs. Kontrolle |
| Konversionsrate | Prozentsatz der Besucherinnen und Besucher, die personalisierten Inhalten ausgesetzt sind und eine gewünschte Aktion durchführen | CJA funnel Analysis: Impression > Interaction > Conversion |
| Absprungrate | Rückgang der Single Page Sessions für Besucher, die personalisierte Inhalte erhalten | CJA-Sitzungsanalyse: Delta der Absprungrate für personalisierte vs. standardmäßige Sitzungen |
| Erfolgsrate des Experiments | Prozentsatz der A/B-Tests, die einen statistisch signifikanten Gewinner ergeben | AJO-Experimentbericht: Experimente erreichen Konfidenzschwellenwert |

## Anwendungsfallmuster

Im Folgenden werden das Kernmuster und die Funktionskette für diesen Anwendungsfall beschrieben.

**Web-Personalization für anonyme Besucher**

Bereitstellen personalisierter Inhalte, die auf sitzungsinternen Verhaltenssignalen für nicht identifizierte Besuchende basieren, über den AJO-Webkanal.

**Funktionskette: Konfiguration der**-Web-Oberfläche > Auswertung von Verhaltensregeln > Inhaltsbereitstellung > Impression-Tracking > Berichterstellung

## Programme

Die folgenden Anwendungen werden in diesem Anwendungsfallmuster verwendet.

- **[!DNL Adobe Journey Optimizer] (AJO)** - Konfiguration der Web-Kanaloberfläche, Inhaltserstellung (Web- und Code-basierte Erlebnisse), Kampagnenausführung, Inhaltsexperimente (A/B-Tests), Entscheidungsfindung (dynamische Inhaltsauswahl) und Reporting
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** - Edge-Segmentierung für die Echtzeit-Zielgruppenbewertung auf der Grundlage von Verhaltenssignalen in der Sitzung; Verwaltung anonymer Edge-Profile
- **[!DNL Adobe Experience Platform] (AEP)** - [!DNL Web SDK] für die Erfassung von Verhaltenssignalen, [!DNL Edge Network] für das Echtzeit-Datenrouting und die Bereitstellung von Personalisierung, Konfiguration des Datenstroms

## Grundlegende Funktionen

Für dieses Anwendungsfallmuster müssen die folgenden grundlegenden Funktionen vorhanden sein. Für jede Funktion gibt der Status an, ob sie normalerweise erforderlich ist, als vorkonfiguriert gilt oder nicht.

| Grundfunktion | Status | Was muss vorhanden sein? | Experience League-Referenz |
| --- | --- | --- | --- |
| Administration und Governance | Angenommen an Ort und Stelle | AJO-Sandbox mit konfigurierten Web-Kanal-Berechtigungen. [!DNL Web SDK] Implementierungsberechtigungen und Datenstromzugriff, die dem Implementierungs-Team gewährt werden. Benutzende mit Rollen, die die Konfiguration von Web-Kanälen, die Verwaltung von Audiences und die Ausführung von Kampagnen ermöglichen. | [Zugriffskontrolle - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Datenmodellierung und -vorbereitung | Erforderlich | Erlebnisereignis-Schema, das Web-Verhaltenssignale erfasst (Seitenansichten, Klicks, Bildlauftiefe, Verweisdaten, UTM-Parameter). Das Schema muss Standardfeldgruppen für Web-Interaktionen enthalten und für das Edge-Profil aktiviert sein, um die Echtzeitauswertung zu unterstützen. Ein entsprechender Datensatz muss erstellt und für das Profil aktiviert werden. | [XDM-System - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Datenquellen und Sammlung | Erforderlich | [!DNL Web SDK] muss in allen Ziel-Web-Eigenschaften implementiert werden. Dabei muss ein Datenstrom konfiguriert sein, um Daten an [!DNL AEP Edge Network] weiterzuleiten. Für den Datenstrom müssen die [!DNL Adobe Experience Platform]- und [!DNL Adobe Journey Optimizer]-Services aktiviert sein. Dies ist eine kritische Abhängigkeit - ohne [!DNL Web SDK] ist keine Erfassung von Verhaltenssignalen oder die Bereitstellung von Erlebnissen möglich. | [Web SDK - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Identitäts- und Profilkonfiguration | Erforderlich | ECID ([!DNL Experience Cloud ID]), konfiguriert als primärer Identity-Namespace für anonyme Besucher. Die Edge-Zusammenführungsrichtlinie muss mit `isActiveOnEdge: true` konfiguriert werden, um anonyme Profildaten am Edge aufzulösen. Pro Sandbox kann nur eine Zusammenführungsrichtlinie am Edge aktiv sein. | [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Zielgruppendefinition und Segmentierung | Erforderlich | Von Edge ausgewertete Zielgruppensegmente, die auf Grundlage von Verhaltenssignalen während der Sitzung definiert wurden. Die Edge-Segmentierung ist für die Latenz der Auswertung von Untersekunden obligatorisch. Segmentregeln dürfen nur Edge-fähige Segmentregelausdrücke verwenden (einfache Attributprüfungen und Segmentzugehörigkeit - keine Zeitreihenabfragen oder komplexen Aggregationen). | [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Unterstützende Funktionen

Die folgenden Funktionen ergänzen dieses Anwendungsfallmuster, sind aber für die Ausführung der Kernkomponente nicht erforderlich.

| Unterstützende Funktion | Status | Warum es wichtig ist | Experience League-Referenz |
| --- | --- | --- | --- |
| Erstellung berechneter/abgeleiteter Attribute | Nicht zutreffend | Begrenzter Wert für anonyme Besucher, da nur minimale historische Profildaten zu aggregieren sind. Kann anwendbar werden, wenn das Edge-Profil aussagekräftige Verhaltensdaten aus früheren anonymen Besuchen über mehrere Sitzungen hinweg sammelt. | [Berechnete Attribute - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Data Lifecycle Management | Empfohlen | Ablauf von pseudonymen Profilen sollte für anonyme Edge-Profile konfiguriert werden, um Speicher zu verwalten und Datenschutzanforderungen zu erfüllen. Reine ECID-Profile können so eingestellt werden, dass sie zwischen 14 und 365 Tagen ablaufen. Cookie-Einverständnisrichtlinien sollten für die Erfassung von Verhaltensdaten durchgesetzt werden. | [Erweitertes Daten-Lifecycle-Management - Überblick](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Datennutzungskennzeichnung und -durchsetzung | Empfohlen | Governance-Kennzeichnungen für Verhaltensdaten stellen die Einhaltung der Vorschriften sicher, insbesondere für Geo-Targeting (S2-sensible geografische Kennzeichnung) und gerätebasierte Personalisierung. Kennzeichnungen verhindern, dass eingeschränkte Verhaltensdaten in nicht autorisierten Personalisierungskontexten verwendet werden. | [Data Governance - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Überwachung und Beobachtbarkeit | Empfohlen | [!DNL Edge Network] und [!DNL Web SDK] Datenflussüberwachung können Probleme beim Versand von Personalisierungen erkennen. Konfigurieren Sie Warnhinweise für Datenstromfehler, Aufnahmefehler und Anomalien der Edge-Bereitstellung. Kritisch für Produktionsbereitstellungen, bei denen Personalisierungsfehler das Besuchererlebnis beeinträchtigen. | [Observability Insights - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Reporting und Analyse | Eingeschlossen | Die Leistungsberichterstattung für Personalization ist Teil der Funktionskette (Phase 5). Die CJA-Analyse der Effektivität der Personalisierung anonymer Besucher ermöglicht tiefgehende funnel-Analysen, Kohortenvergleiche und Messungen der Konversionsauswirkungen, die über die nativen Berichte von AJO hinausgehen. | [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Anwendungsfunktionen

Dieser Plan führt die folgenden Funktionen aus dem Anwendungsfunktionskatalog aus. Funktionen werden Implementierungsphasen und nicht nummerierten Schritten zugeordnet.

### [!DNL Journey Optimizer] (AJO)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Kanalkonfiguration | Phase 1: Konfiguration der Web-Oberfläche | Konfigurieren von Web-Kanaloberflächen, die definieren, wo personalisierte Inhalte in den Ziel-Web-Eigenschaften bereitgestellt werden |
| Verfassen von Nachrichten | Phase 3: Inhaltserstellung und Variantenerstellung | Erstellen personalisierter Inhaltsvarianten für Web-Oberflächen mit dem Web-Designer, dem Code-basierten Erlebnis-Editor oder Inhaltsvorlagen |
| Kampagnenausführung | Phase 4: Konfiguration von Kampagnen und Sendungen | Erstellen und aktivieren Sie Web-Kampagnen, die Audiences, Inhalte und Versandkonfigurationen binden |
| Entscheidungsfindung | Phase 3: Inhaltserstellung und Variantenerstellung (Option C) | Konfigurieren Sie Entscheidungsrichtlinien, Eignungsregeln und Rangfolgestrategien für die dynamische Inhaltsauswahl basierend auf Verhaltenssignalen |
| Inhaltsexperiment | Phase 3: Inhaltserstellung und Variantenerstellung (Option B) | Konfigurieren von A/B- und multivariaten Inhaltsexperimenten mit Traffic-Zuordnung, Erfolgsmetriken und Konfidenzschwellen |
| Reporting und Leistungsanalyse | Phase 5: Reporting und Leistungsanalyse | Überwachen von Personalisierungsmetriken, Varianteneffektivität, Experimentergebnissen und Auswirkungen auf die Konversion |

### [!DNL Real-Time CDP] (RT-CDP)

| Funktion | Implementierungsphase | Beschreibung |
| --- | --- | --- |
| Zielgruppenauswertung | Phase 2: Definition der verhaltensbezogenen Zielgruppe | Definieren und bewerten Sie Edge-basierte Zielgruppensegmente mithilfe von Verhaltenssignalen in der Sitzung für das Targeting mit Personalisierung in Echtzeit |

## Voraussetzungen

Führen Sie folgende Schritte aus, bevor Sie mit der Implementierung beginnen.

- [ ] [!DNL Web SDK] wird in allen Ziel-Web-Eigenschaften implementiert, wobei `sendEvent` Aufrufe Seitenansichten, Klicks und relevante Verhaltensinteraktionen erfassen
- [ ] Datenstrom wird in der Datenerfassungs-Benutzeroberfläche mit aktivierten [!DNL Adobe Experience Platform]- und [!DNL Adobe Journey Optimizer] konfiguriert
- [ ] Erlebnisereignis-Schema ist mit Web-Interaktions-Feldergruppen (Seitenansichten, Verweisdaten, UTM-Parameter, Gerätekontext) vorhanden und für das Profil aktiviert
- [ ] ECID-Identity-Namespace wird konfiguriert und im Web Behavioral Event-Schema als primäre Identität festgelegt
- [ ] Edge-Zusammenführungsrichtlinie wird mit `isActiveOnEdge: true` in der Ziel-Sandbox konfiguriert
- [ ] AJO-Webkanal ist in der Ziel-Sandbox bereitgestellt und zugänglich
- [ ] Inhaltsvarianten (Kopie, Bilder, CTAs) werden für jeden Personalisierungs-Anwendungsfall entworfen und genehmigt
- [ ] Erfolgsmetriken werden definiert (was ein Konversions- oder Interaktionsereignis zur Messung darstellt).
- [ ] Cookie-Einverständnismechanismus wird auf der Website implementiert, um die Datenschutzbestimmungen einzuhalten, bevor Verhaltensdaten erfasst werden

## Implementierungsoptionen

In diesem Abschnitt werden drei Implementierungsansätze beschrieben. Wählen Sie die Option aus, die Ihren Personalisierungsanforderungen am besten entspricht.

### Option A: Regelbasierte Web-Personalisierung

**Optimiert für:** Einfache, deterministische Personalisierung - Geotargeting-Banner, verweisquellenspezifische Überschriften, gerätespezifische Layouts, Nachrichten von neuen oder wiederkehrenden Besuchern. Wählen Sie diese Option, wenn die Inhaltsvariante durch eine einfache Bedingungslogik bestimmt werden kann (wenn Bedingung X, Inhalt Y anzeigen).

**Funktionsweise:**

Die regelbasierte Personalisierung nutzt kantenausgewertete Zielgruppensegmente, um zu bestimmen, welche Inhaltsvariante ein Besucher sieht. Jedes Zielgruppensegment wird über in der Kampagne definierte bedingte Regeln einer bestimmten Inhaltsvariante zugeordnet. Wenn ein Besucher eine Seite lädt, sendet der [!DNL Web SDK] Verhaltenssignale an den [!DNL Edge Network], der das Edge-Profil des Besuchers anhand der definierten Zielgruppenregeln in Millisekunden auswertet. Die übereinstimmende Inhaltsvariante wird in der [!DNL Edge Network] Antwort zurückgegeben und auf der Seite gerendert.

Dieser Ansatz erfordert die Definition verschiedener Zielgruppensegmente in RT-CDP (z. B. „Besucher aus der Google-Suche“, „Besucher aus Kalifornien“, „Besucher über Mobilgeräte„) und die Erstellung entsprechender Inhaltsvarianten in AJO. Die Kampagne bindet jede Audience an ihre Inhaltsvariante mithilfe von bedingten Inhaltsregeln oder separaten Kampagnen pro Segment. Es ist kein KI-Ranking oder Traffic-Aufteilung beteiligt. Die Beziehung zwischen Zielgruppe und Inhalt ist deterministisch.

**Wichtige Aspekte:**

- Erfordert klar definierte Zielgruppenkriterien, die als Edge-fähige Segmentregelausdrücke ausgedrückt werden können
- Inhaltsvarianten müssen für jedes Zielgruppensegment vorab erstellt werden
- Das Hinzufügen neuer Personalisierungsregeln erfordert das Erstellen neuer Zielgruppensegmente und Inhaltsvarianten
- Bietet keine statistische Messung der Effektivität von Inhaltsvarianten

**Vorteile:**

- Einfachste Implementierung und einfaches Verständnis - Klare Ursache-Wirkungs-Beziehung zwischen Zielgruppe und Inhalt
- Kein Experimentier-Overhead oder Traffic-Aufteilung erforderlich
- Deterministisches Verhalten macht Tests und Qualitätssicherung einfach
- Niedrige Latenz, da die Edge-Evaluierung rein regelbasiert ist
- Funktioniert gut, wenn das Unternehmen bereits weiß, welche Inhalte für jedes Segment am besten funktionieren

**Einschränkungen:**

- Kein integrierter Mechanismus zur Messung, ob die Personalisierung die Ergebnisse gegenüber den Standardinhalten verbessert
- Erfordert manuelle Entscheidungen darüber, welcher Inhalt für jedes Segment angezeigt werden soll
- Passt sich nicht an oder optimiert im Laufe der Zeit - statische Regeln, bis sie manuell geändert werden
- Die Skalierung auf viele Segmente und Varianten erhöht die Konfigurationskomplexität.

**Experience League:**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Option B: Experimentbasierte Web-Personalisierung

**Am besten geeignet für:** A/B- und Multivariate Testing - zum Testen von Überschriftenvarianten, CTA-Schaltflächenfarben, Layout-Alternativen, Werbeangeboten - mit statistischer Signifikanzmessung. Wählen Sie diese Option, wenn Sie überprüfen müssen, welche Inhaltsvariante am besten funktioniert, bevor Sie sich zu einer dauerhaften Personalisierungsregel verpflichten.

**Funktionsweise:**

Die experimentbasierte Personalisierung nutzt AJO Content Experimentation , um Besuchende nach dem Zufallsprinzip Inhaltsbehandlungsgruppen zuzuordnen und zu messen, welche Variante mit einer definierten Erfolgsmetrik am besten abschneidet. Der Traffic wird auf verschiedene Varianten aufgeteilt (z. B. 50/50 für A/B, 33/33/34 für A/B/C) und die Leistung wird verfolgt, bis statistische Signifikanz erreicht ist.

Das Experiment ist in eine AJO-Web-Kampagne eingebettet. Wenn ein Besucher eine Seite lädt, weist der [!DNL Edge Network] sie basierend auf der konfigurierten Traffic-Zuordnung einer Abwandlungsgruppe zu. Der Besucher sieht für die Dauer des Experiments durchgängig dieselbe Behandlung (Persistenz auf Sitzungs- oder Besucherebene je nach Konfiguration). Erfolgsmetriken (Klicks, Konversionen, Interaktionsereignisse) werden über [!DNL Web SDK] verfolgt und im AJO-Experimentbericht gemeldet.

Für diese Option sind keine vordefinierten Zielgruppensegmente für das Targeting erforderlich. Alle Besucher (oder eine ausgewählte Untergruppe) sind am Experiment beteiligt. Das Ziel besteht darin herauszufinden, welcher Inhalt am besten funktioniert, und nicht darin, bekannte Segmente mit vorab festgelegten Inhalten anzusprechen.

**Wichtige Aspekte:**

- Erfordert ein ausreichendes Traffic-Volumen, um innerhalb eines angemessenen Zeitraums statistische Signifikanz zu erreichen
- Die Experimente verwenden ein Bayes&#39;sches Statistikmodell mit jederzeit gültigen Konfidenzintervallen
- Es wird eine neutrale Gruppe (die keine personalisierten Inhalte erhält) empfohlen, um die inkrementelle Steigerung zu messen
- Pro Kampagne kann immer nur ein Experiment aktiv sein
- Änderungen am Experiment erfordern das Anhalten und Neustarten der Kampagne

**Vorteile:**

- Bietet eine statistisch strenge Messung der Effektivität von Inhaltsvarianten
- Entfernt Rätselraten aus Personalisierungsentscheidungen - datengesteuerte Inhaltsauswahl
- Unterstützt Holdout-Gruppen für die Messung der tatsächlichen inkrementellen Steigerung
- Integrierte Experimentberichte mit Konfidenzintervallen und Gewinnererklärung
- Die Ergebnisse können in die zukünftige regelbasierte Personalisierung (Option A) einfließen, indem die erfolgreichsten Varianten ermittelt werden

**Einschränkungen:**

- Erfordert aussagekräftiges Traffic-Volumen - Seiten mit geringem Traffic können Wochen dauern, bis sie signifikant werden
- Traffic-Aufteilung bedeutet, dass einige Besucher während des Testzeitraums suboptimale Inhalte sehen
- Während des Experiments können nicht nach Segment personalisiert werden (alle Besucher oder eine Teilmenge können gleich teilnehmen)
- Maximal 10 Behandlungsvarianten pro Experiment
- Keine kontinuierliche Optimierung - Experimente sind diskret mit Beginn und Ende

**Experience League:**

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Option C: Entscheidungsbasierte Web-Personalisierung

**Am besten geeignet für:** Dynamische Inhaltsauswahl - Kategorieaffinitätsempfehlungen, Exitintent-Angebote, Verhaltensempfehlungen - bei der eine Entscheidungsrichtlinie Sitzungssignale auswertet und den optimalen Inhalt aus einem Katalog der geeigneten Elemente auswählt. Wählen Sie diese Option aus, wenn die Logik zur Inhaltsauswahl für einfache Regeln zu komplex ist, wenn Sie eine KI-Rangfolgenoptimierung wünschen oder wenn der Satz geeigneter Inhaltselemente groß und dynamisch ist.

**Funktionsweise:**

Die entscheidungsbasierte Personalisierung nutzt AJO Decisioning, um Verhaltenssignale zu bewerten und die beste Inhaltsvariante für jede Besucherin und jeden Besucher aus einem verwalteten Katalog von Inhaltselementen (Angeboten) auszuwählen. Jedes Inhaltselement verfügt über Eignungsregeln (wer qualifiziert ist), Darstellungen (wie der Inhalt in jeder Platzierung aussieht) und optionale Begrenzungsbeschränkungen (wie oft er angezeigt werden kann). Eine Entscheidungsrichtlinie verknüpft Platzierungen (bei denen Inhalte auf der Seite angezeigt werden) mit Sammlungen von Inhaltselementen und wendet eine Rangfolgestrategie an, um die beste Option auszuwählen.

Wenn ein Besucher eine Seite lädt, sendet der [!DNL Web SDK] eine [!DNL Edge Network]-Anfrage, die den Entscheidungsumfang enthält. Die Decisioning-Engine wertet das Edge-Profil des Besuchers anhand der Eignungsregeln für Inhaltselemente aus, wendet die Rangfolgestrategie (prioritätsbasiert, formularbasiert oder KI-rangiert) an und gibt das erfolgreichste Inhaltselement zurück. Dies geschieht am Edge mit einer Latenz von Untersekunden.

Die Rangfolgestrategie bestimmt, wie geeignete Inhaltselemente sortiert werden. Die prioritätsbasierte Rangfolge verwendet manuell zugewiesene Prioritätswerte. Die formularbasierte Rangfolge verwendet einen benutzerdefinierten Ausdruck (z. B. Gewichtung der Neuigkeit von Seitenansichten). Das KI-Ranking verwendet ein maschinelles Lernmodell, das im Laufe der Zeit für die ausgewählte Erfolgsmetrik optimiert wird, für das Training jedoch mindestens 1.000 Konversionsereignisse erforderlich sind.

**Wichtige Aspekte:**

- Erfordert das Einrichten der Entscheidungskomponenten: Platzierungen, Eignungsregeln, Inhaltselemente, Fallback-Elemente, Sammlungen und Entscheidungsrichtlinien
- KI-Rangfolgestrategien erfordern ein ausreichendes Konversionsvolumen (mehr als 1.000 Ereignisse), um das Modell zu trainieren
- Edge-Entscheidungen sind auf Profilattribute beschränkt, die im Edge-Profilspeicher verfügbar sind
- Inhaltselemente müssen in der Entscheidungsbibliothek verwaltet und gepflegt werden
- Fallback-Inhalt muss für Fälle definiert werden, in denen kein personalisiertes Element geeignet ist

**Vorteile:**

- Skalierung auf große Inhaltskataloge, ohne dass eine individuelle Zuordnung von Zielgruppe zu Inhalt erforderlich ist
- KI-Rangfolgestrategien optimieren die Inhaltsauswahl kontinuierlich basierend auf der beobachteten Leistung
- Eignungsregeln und Begrenzungsregeln bieten eine präzise Kontrolle der Inhaltsbereitstellung
- Unterstützt komplexe Geschäftslogik, die als Zielgruppensegmente schwer auszudrücken wäre
- Wiederverwendbar über verschiedene Kanäle hinweg - dieselbe Entscheidungsrichtlinie kann für die Personalisierung von Web, E-Mail und Mobilgeräten verwendet werden

**Einschränkungen:**

- Höhere Implementierungskomplexität - erfordert das Einrichten des vollständigen Entscheidungskomponenten-Stacks
- Das KI-Ranking erfordert ein erhebliches Konversionsvolumen und Zeit, um effektiv zu trainieren.
- Einschränkungen bei Profildaten in Edge beschränken die Komplexität von Eignungsregeln für anonyme Besucher
- Mehraufwand für die Verwaltung von Inhaltselementen - Jedes Element benötigt Darstellungen, Eignungsregeln und Wartung
- Das Debuggen der Entscheidungslogik ist komplexer als regelbasierte Ansätze

**Experience League:**

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### Vergleich von Optionen

In der folgenden Tabelle werden die drei Implementierungsoptionen anhand von Schlüsselkriterien verglichen.

| Kriterien | Option A: Regelbasiert | Option B: Experimentieren | Option C: Entscheidung |
| --- | --- | --- | --- |
| Am besten geeignet für | Bekannte Zuordnungen von Segmenten zu Inhalten | Ermitteln, welche Inhalte am besten funktionieren | Dynamische Inhaltsauswahl aus großen Katalogen |
| Komplexität | Niedrig | Mittel | Hoch |
| Latenz | Sub-Sekunde (Edge) | Sub-Sekunde (Edge) | Sub-Sekunde (Edge) |
| Personalization Precision | Segmentebene (Zielgruppenregeln) | Besucherebene (zufällige Zuweisung) | Besucherebene (Berechtigung + Rangfolge) |
| Inhaltsoptimierung | Manuell (keine Messung) | Statistische Tests (A/B) | Fortlaufend (KI-Rangfolge) oder manuell (Priorität) |
| Zielgruppensegmente erforderlich | Ja (Edge-evaluiert) | Nein (Traffic-Aufteilung) | Optional (für Eignungsregeln) |
| Messbarkeit | Keine integriert (CJA erforderlich) | Integrierte Experimentberichte | Integrierte Entscheidungsberichte |
| Größe des Inhaltskatalogs | Klein (1:1 Segment-zu-Inhalt) | Klein (2-10 Varianten) | Groß (unbegrenzte Anzahl förderfähiger Elemente) |
| Erfordert | Edge-Zielgruppen, Inhaltsvarianten | Kampagne mit aktiviertem Experiment | Entscheidungskomponenten (Platzierungen, Angebote, Richtlinien) |

### Wählen der richtigen Option

Verwenden Sie die folgende Entscheidungslogik, um die entsprechende Implementierungsoption auszuwählen:

1. **Wissen Sie bereits, welche Inhalte für jedes Besuchersegment angezeigt werden sollen?**
   - Ja: Beginnen Sie mit **Option A (regelbasiert)**. Sie haben Inhaltsstrategien pro Segment festgelegt und benötigen eine deterministische Bereitstellung.
   - Nein: Fahren Sie mit Frage 2 fort.

2. **Müssen Sie eine kleine Anzahl von Inhaltsvarianten testen, um die beste Leistung zu finden?**
   - Ja: Wählen Sie **Option B (Experiment)**. Sie benötigen statistische Validierung, bevor Sie sich zu einer Inhaltsstrategie verpflichten.
   - Nein: Fahren Sie mit Frage 3 fort.

3. **Verfügen Sie über einen großen Katalog mit Inhaltselementen mit komplexen Eignungs- und Ranking-Anforderungen?**
   - Ja: Wählen Sie **Option C (Entscheidung)**. Sie benötigen eine dynamische Inhaltsauswahl, die über einfache Regeln hinaus skaliert werden kann.
   - Nein: Beginnen Sie mit **Option A (regelbasiert)** der Einfachheit, entwickeln Sie dann zu Option B oder C, wenn die Anforderungen steigen.

**Kombinieren von Optionen** Diese Optionen schließen sich nicht gegenseitig aus. Eine häufige Entwicklung besteht darin, mit Option B (Experimentieren) zu beginnen, um die erfolgreichsten Inhalte zu ermitteln, und dann die Gewinner mithilfe von Option A (Regelbasiert) für die fortlaufende Bereitstellung bereitzustellen. Option C (Decisioning) kann für Anwendungsfälle, die eine dynamische katalogbasierte Auswahl erfordern, überlagert werden, während Option A einfachere deterministische Regeln verarbeitet.

## Implementierungsphasen

In den folgenden Phasen wird der End-to-End-Implementierungs-Workflow beschrieben.

### Phase 1: Konfigurieren von Web-Oberflächen

**Anwendungsfunktion:** AJO: Kanalkonfiguration

Definieren Sie die Web-Kanaloberflächen, die angeben, wo auf Ihrer Website personalisierte Inhalte bereitgestellt werden. Eine Web-Oberfläche identifiziert eine bestimmte Seiten-URL oder ein bestimmtes URL-Muster und die Position auf der Seite (CSS-Selektor oder Code-basierte Erlebnisoberfläche), an der AJO Inhalte einfügen oder ersetzen kann.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Oberflächentyp** - Wie sollten personalisierte Inhalte auf der Seite bereitgestellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Webkanal (Visual Editor) | Die Personalisierung umfasst die Änderung sichtbarer Seitenelemente (Banner, Überschriften, Bilder, CTAs) mithilfe eines visuellen Drag-and-Drop-Editors | Erfordert die Web-Designer-Browser-Erweiterung. Optimiert für Änderungen an Inhalten unter Federführung von Marketing-Experten. Beschränkung auf visuelle Änderungen vorhandener Seitenelemente. |
| Code-basiertes Erlebnis | Die Personalisierung erfordert das Einfügen strukturierter Daten (JSON), die der Code der Website-Anwendung nutzt und rendert | Erfordert, dass die Entwicklerimplementierung die JSON-Payload nutzt. Maximale Flexibilität für komplexe Personalisierung. Optimiert für SPAs, dynamische Komponenten und programmgesteuertes Rendering. |
| Beide (Hybrid) | Verschiedene Personalisierungen auf derselben Site erfordern unterschiedliche Bereitstellungsmechanismen | Verwenden Sie den Webkanal für einfache visuelle Änderungen und Code-basierte Erlebnisse für das programmgesteuerte Rendering. Erhöht die Komplexität der Implementierung, maximiert aber die Abdeckung. |

>[!NOTE]
>**Entscheidung: Oberflächenbereich** - Welchen URL-Bereich sollte die Web-Oberfläche abdecken?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Exakte URL-Übereinstimmung | Personalization ist auf eine bestimmte Seite ausgerichtet (z. B. Homepage, Landingpage) | Präzise Zielgruppenbestimmung. Für jede Seite sind separate Oberflächen erforderlich. |
| URL-Muster mit Platzhaltern | Personalization gilt für eine Kategorie von Seiten (z. B. alle Produktseiten, alle Blog-Artikel) | Reduziert den Overhead für das Oberflächenmanagement. Inhaltsvarianten müssen so konzipiert sein, dass sie auf allen übereinstimmenden Seiten funktionieren. |
| Oberfläche für Single Page Application (SPA) | Die Website ist eine SPA, bei der URL-Änderungen nicht den Trigger vollständiger Seitenneuladungen umfassen | Erfordert eine SPA-fähige [!DNL Web SDK] mit `sendEvent` Aufrufen bei Ansichtsänderungen. Oberflächendefinitionen verwenden den SPA-Ansichtsnamen anstelle der URL. |

**UI-Navigation:** [!DNL Journey Optimizer] > Administration > Kanäle > Web-Konfiguration

**Wichtige Konfigurationsdetails:**

- Seiten-URL oder URL-Muster für die Oberfläche definieren
- Angeben des CSS-Selektors oder Oberflächen-URI für die Inhaltsplatzierung
- Definieren Sie für Code-basierte Erlebnisse den Namen der Oberfläche, auf die der Programm-Code verweisen soll
- Verknüpfen Sie die Oberfläche mit der AJO-Sandbox, in der Kampagnen erstellt werden

**Dokumentation zu Experience League:**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-basierter Erlebniskanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-basierte Erlebniskonfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### Phase 2: Festlegen von Verhaltens-Audiences

**Anwendungsfunktion:** RT-CDP: Zielgruppenauswertung

Definieren Sie von Edge ausgewertete Zielgruppensegmente basierend auf Verhaltenssignalen in der Sitzung, die das Personalisierungs-Targeting fördern. Diese Zielgruppen bestimmen, welche Besucher für jedes personalisierte Erlebnis qualifiziert sind. Die Edge-Auswertung ist für dieses Muster obligatorisch, da Personalisierungsentscheidungen in Zeitrahmen von weniger als zwei Sekunden getroffen werden müssen, wenn der Besucher auf der Website navigiert.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Verhaltenssignalauswahl** - Welche Sitzungssignale sollten das Personalisierungs-Targeting fördern?

| Signal | Verwendungszeitpunkt | Edge-Berechtigung |
| --- | --- | --- |
| Verweisquelle / UTM-Parameter | Kampagnenspezifische Landingpage-Personalisierung | Berechtigt - Einfache Attributprüfung des aktuellen Ereignisses |
| Geografische Lage (Land, Region, Stadt) | Regionale Werbeaktionen, sprachspezifische Inhalte, Store-Locator | Qualifizierbar - Prüfung der Profilattribute |
| Gerätetyp (Desktop, Mobilgerät, Tablet) | Geräteoptimierte Inhaltslayouts und CTAs | Qualifizierbar - Prüfung der Profilattribute |
| In Sitzung angezeigte Seiten | Kategorieaffinität, Inhaltsempfehlungen | Berechtigt mit Einschränkungen - nur Prüfungen der einfachen Ereignisanzahl |
| Neuer und wiederkehrender Besucher | Willkommensbotschaft, progressive Interaktion | Berechtigt - ECID-Persistenz zeigt den wiederkehrenden Besucher an |
| Zeit vor Ort / Bildlauftiefe | Interaktionsbasierte Angebote mit Exitintent | Erfordert möglicherweise eine benutzerdefinierte Implementierung - nicht nativ Edge-fähig |

>[!NOTE]
>**Entscheidung: Methode zur Zielgruppenauswertung** - Alle Zielgruppen für dieses Muster müssen eine Kantenauswertung verwenden. Bestätigen Sie die Eignung, bevor Sie Segmente definieren.

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Edge-Auswertung | Erforderlich für dieses Muster | Segmentregelausdrücke müssen Edge-fähig sein: einfache Attributvergleiche, Segmentzugehörigkeitsprüfungen, keine Zeitreihenabfragen oder Aggregationsfunktionen. Auswertungslatenz für die Untersekunde. |
| Streaming-Auswertung (Fallback) | Wenn der Segmentregelausdruck nicht Edge-fähig ist, aber nahezu in Echtzeit akzeptiert wird | Latenz von Sekunden zu Minuten. Unterstützt komplexere Segmentregelausdrücke. Kann zu einer merklichen Verzögerung bei der Bereitstellung der Personalisierung führen. |

**Benutzeroberflächennavigation:** Kunde > Zielgruppen > Zielgruppe erstellen > Regel erstellen

**Wichtige Konfigurationsdetails:**

- Verwenden Sie Segment Builder, um Zielgruppenregeln mithilfe von Verhaltensattributen zu definieren
- Überprüfen Sie die Edge-Eignung, indem Sie bestätigen, dass der Segmentregelausdruck nur unterstützte Funktionen verwendet (einfache Attributvergleiche, Segmentzugehörigkeit)
- Legen Sie die Zusammenführungsrichtlinie auf die in F4 konfigurierte Edge-aktive Zusammenführungsrichtlinie fest.
- Vorschau der Zielgruppenpopulation zur Validierung des Segments liefert erwartete Ergebnisse
- Verwenden Sie für Zielgruppen, die auf Seitenansichten auf Sitzungsebene basieren, Attribute auf Ereignisebene aus der aktuellen Sitzung anstelle von Zeitreihenabfragen

**Wo die Optionen unterschiedlich sind:**

**Für Option A (regelbasiert):**
Erstellen Sie für jede Inhaltsvariante unterschiedliche Zielgruppensegmente. Jedes Segment stellt eine bestimmte Verhaltensbedingung dar (z. B. wird „Empfehlung = Google AND Geo = US“ der Inhaltsvariante A zugeordnet). Die Anzahl der Zielgruppen entspricht der Anzahl der Personalisierungsregeln.

**Für Option B (Experiment):**
Die Zielgruppendefinition ist optional. Wenn das Experiment alle Besucherinnen und Besucher anspricht, ist keine Zielgruppe erforderlich - die Traffic-Aufteilung übernimmt die Zuweisung von Varianten. Wenn das Experiment auf eine bestimmte Untergruppe ausgerichtet ist (z. B. nur mobile Besucher), definieren Sie eine einzelne Zielgruppe als Eignung für das Experiment.

**Für Option C (Entscheidung):**
Audiences definieren, die als Eignungsregeln für Inhaltselemente verwendet werden können. Diese Zielgruppen bestimmen, welche Besucher für welche Inhaltselemente in der Entscheidungsrichtlinie qualifiziert sind. Die Decisioning-Engine verwaltet die Inhaltsauswahl aus den zulässigen Elementen.

**Dokumentation zu Experience League:**

- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Phase 3: Erstellen von Inhalten und Erstellen von Varianten

**Anwendungsfunktion:** AJO: Nachrichtenbearbeitung, AJO: Inhaltsexperiment (Option B), AJO: Entscheidungsfindung (Option C)

Erstellen Sie die personalisierten Inhaltsvarianten, die den Besuchern auf der Grundlage der Zielgruppenzugehörigkeit (Option A), der Experimentzuweisung (Option B) oder der Entscheidungslogik (Option C) bereitgestellt werden. In dieser Phase wird die Inhaltserstellung mit dem AJO Web Designer oder dem Code-basierten Erlebnis-Editor sowie die Experiment- oder Entscheidungskonfiguration behandelt, die steuert, wie Inhalte ausgewählt werden.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Inhaltserstellungsansatz** - Wie sollten Web-Inhaltsvarianten erstellt werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Visueller Web-Editor | Marketing-Team kann Seitenelemente visuell ohne Code ändern | Browser-Erweiterung erforderlich. Optimiert für Text-, Bild- und CTA-Änderungen. Beschränkung auf das Ändern vorhandener Seitenelemente. |
| Code-basierter Erlebnis-Editor | Inhalte erfordern strukturierte Daten (JSON), die vom Anwendungs-Code gerendert werden | Maximale Flexibilität. Erfordert, dass die Payload von einer Entwicklerimplementierung genutzt wird. Optimiert für dynamische Komponenten und SPAs. |
| HTML/CSS-Code-Editor | Inhaltsänderungen erfordern benutzerdefinierte HTML oder CSS | Direkte Code-Steuerung. Erfordert HTML/CSS-Kenntnisse. Optimiert für komplexe Layout-Änderungen. |

>[!NOTE]
>**Entscheidung: Personalization-Token** - Sollen Inhalte eine dynamische Personalisierung enthalten, die Profil- oder kontextuelle Attribute verwendet?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Statische Inhaltsvarianten | Jede Variante ist ein festes Inhaltselement ohne dynamische Token | Einfachster Ansatz. Inhalte sind vorhersehbar und lassen sich einfach überprüfen. Kein Risiko, dass Attributwerte fehlen. |
| Dynamische Inhalte mit Personalisierungsausdrücken | Inhalte enthalten Token im Handlebars-Stil, die in Profil- oder Ereignisattribute aufgelöst werden (z. B. Stadtname, Verweisquelle). | Mehr relevante Inhalte. Erfordert Fallback-Werte für Attribute, die bei anonymen Profilen null sein können. Verwenden Sie `{{profile.homeAddress.city}}` Syntax mit Helfern. |
| Bedingte Inhaltsbausteine | Verschiedene Inhaltsblöcke werden basierend auf Attributbedingungen innerhalb einer einzigen Variante gerendert | Reduziert die Anzahl der erforderlichen eindeutigen Varianten. Erhöht die Komplexität von Inhalten. Gut geeignet für kleinere Varianten innerhalb eines freigegebenen Layouts. |

**UI-Navigation:** [!DNL Journey Optimizer] > Kampagnen > Kampagne auswählen > Inhalt bearbeiten

**Wichtige Konfigurationsdetails:**

- Erstellen von Inhalten mit dem Web-Designer (visuelle Änderungen) oder dem Code-basierten Erlebnis-Editor (JSON-Payload)
- Verwenden Sie den Ausdruckseditor für die Personalisierung, um dynamische Token aus Edge-Profilattributen einzufügen
- Konfigurieren von Fallback-Inhalt für Personalisierungs-Token, die in anonymen Profilen leer sein können
- Vorschau von Inhalten mit Testprofilen zur Überprüfung des Renderings in verschiedenen Szenarien

**Wo die Optionen unterschiedlich sind:**

**Für Option A (regelbasiert):**
Erstellen Sie für jedes in Phase 2 definierte Zielgruppensegment eine eigene Inhaltsvariante. Binden Sie jede Variante mithilfe von Regeln für bedingte Inhalte in der Kampagnenkonfiguration an ihre Zielgruppe. Stellen Sie sicher, dass für Besuchende, die keiner Zielgruppenregel entsprechen, eine Standardinhaltsvariante vorhanden ist.

**Für Option B (Experiment):**
Abwandlungsvarianten erstellen (A, B, C usw.) für das Experiment. Aktivieren Sie Inhaltsexperimente für die Kampagne, definieren Sie Abwandlungsvarianten mit ihrem Inhalt, legen Sie Traffic-Zuordnungsprozentsätze fest und konfigurieren Sie die Erfolgsmetrik.

- Definieren von 2-10 Abwandlungsvarianten mit unterschiedlichem Inhalt
- Festlegen der Traffic-Zuordnung (z. B. 50/50 für A/B oder gewichtete Aufspaltung für Tests mit niedrigerem Risiko)
- Optional eine neutrale Gruppe einschließen (z. B. 10 % erhält Standardinhalt), um die inkrementelle Steigerung zu messen
- Wählen Sie die Erfolgsmetrik aus: Einzelöffnungen, Einzelklicks, Konversionen oder benutzerdefinierte Metrik
- Legen Sie die Konfidenzschwelle fest: 95 % für Standardtests, 99 % für Entscheidungen mit hohen Einsätzen, 90 % für direktionales Lernen
- **UI-Navigation:** Campaign > Inhaltsexperiment > Abwandlung hinzufügen > Traffic-Zuordnung > Erfolgsmetrik

**Für Option C (Entscheidung):**
Richten Sie den Entscheidungskomponenten-Stack ein und integrieren Sie ihn in die Kampagne.

1. **Platzierungen erstellen** - Festlegen, wo auf der Seite Inhaltselemente angezeigt werden (Web HTML, Web JSON, Web-Bild)
   - **UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Platzierungen
2. **Eignungsregeln definieren** - Erstellen Sie Regeln auf der Grundlage von Edge-Profilattributen, die bestimmen, welche Besucher für jedes Inhaltselement qualifiziert sind
   - **UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Regeln
3. **Erstellen von Inhaltselementen (Angeboten)** Erstellen Sie personalisierte Inhaltselemente mit Darstellungen für jede Platzierung, Eignungsregeln, Priorität und optionale Begrenzung
   - **UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Angebote > Angebot erstellen
4. **Fallback-Inhalt erstellen** - Definiert ein Fallback-Element, das zurückgegeben wird, wenn kein personalisiertes Element qualifiziert ist
   - **UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Angebote > Fallback-Angebot erstellen
5. **In Sammlungen organisieren** - Gruppieren von Inhaltselementen mithilfe von Sammlungsqualifizierern (Tags) und Erstellen von Sammlungen
   - **Benutzeroberflächennavigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Sammlungsqualifizierer/Sammlungen
6. **Entscheidungsrichtlinie erstellen** — Platzierungen mit Sammlungen verknüpfen und die Rangfolgestrategie auswählen (prioritätsbasiert, formularbasiert oder KI-Rangfolge)
   - **UI-Navigation:** [!DNL Journey Optimizer] > Komponenten > Entscheidungs-Management > Entscheidungen > Entscheidung erstellen

**Dokumentation zu Experience League:**

- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-basierter Erlebniskanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Phase 4: Konfigurieren von Kampagne und Versand

**Anwendungsfunktion:** AJO: Kampagnenausführung

Erstellen und aktivieren Sie die AJO-Web-Kampagne, die die Web-Oberfläche (Phase 1), die Zielgruppen-Targeting- oder Experimentkonfiguration (Phasen 2-3) und die Inhaltsvarianten (Phase 3) zu einer Einheit bindet, die Ergebnisse liefert. Die Kampagne steuert, wann und wie Besuchern personalisierte Inhalte bereitgestellt werden.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Kampagnentyp** - Wie sollte die Kampagne ausgelöst werden?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Geplante Kampagne (immer aktiv) | Personalization sollte für alle qualifizierten Besucher kontinuierlich ausgeführt werden | Legen Sie ein Startdatum ohne Enddatum für die zeitlose Personalisierung fest. Die Zielgruppenauswertung erfolgt am Edge in Echtzeit. Am häufigsten für die Web-Personalisierung. |
| Geplante Kampagne (zeitlich begrenzt) | Personalization ist an einen bestimmten Aktionszeitraum oder ein saisonales Ereignis gebunden | Legen Sie ein explizites Start- und Enddatum fest. Campaign wird am Enddatum automatisch deaktiviert. Gut für Werbekampagnen. |
| API-ausgelöste Kampagne | Der Personalization-Versand muss durch ein externes Systemereignis ausgelöst werden | Erfordert API-Integration. Seltener bei der anonymen Web-Personalisierung. Wird verwendet, wenn ein Backend-System steuern muss, wann die Personalisierung aktiv ist. |

**UI-Navigation:** [!DNL Journey Optimizer] > Kampagnen > Kampagne erstellen

**Wichtige Konfigurationsdetails:**

- Wählen Sie den Webkanal und die in Phase 1 konfigurierte Web-Oberfläche aus
- Binden Sie die Zielgruppe (für Option A) oder konfigurieren Sie Experimenteinstellungen (für Option B) oder betten Sie die Entscheidung ein (für Option C)
- Festlegen des Kampagnenkalenders (Startdatum, Enddatum oder immer aktiv)
- Konfigurieren der Frequenzlimitierung auf Kampagnenebene, falls zutreffend
- Alle Konfigurationen überprüfen und die Kampagne aktivieren

**Wo die Optionen unterschiedlich sind:**

**Für Option A (regelbasiert):**
Erstellen Sie für jede Personalisierungsregel eine Kampagne, von der jede auf eine andere Edge-Zielgruppe mit der entsprechenden Inhaltsvariante abzielt. Alternativ können Sie eine einzelne Kampagne mit bedingten Inhaltsregeln verwenden, die die Zielgruppenzugehörigkeit innerhalb einer Kampagne Inhaltsvarianten zuordnen.

**Für Option B (Experiment):**
Erstellen Sie eine einzelne Kampagne mit aktiviertem Inhaltsexperiment. Die Experimentkonfiguration (Varianten, Traffic-Zuordnung, Erfolgsmetrik) wurde in Phase 3 definiert. Aktivieren Sie die Kampagne, um das Experiment zu starten.

**Für Option C (Entscheidung):**
Erstellen Sie eine Kampagne, in die die in Phase 3 konfigurierte Entscheidungsrichtlinie eingebettet ist. Die Inhaltsaktion der Kampagne verweist auf den Entscheidungsumfang, der die Entscheidungs-Engine am Edge Trigger. Aktivieren Sie die Kampagne, um mit der Bereitstellung entscheidungsbasierter Inhalte zu beginnen.

**Dokumentation zu Experience League:**

- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Phase 5: Leistungsberichte und -analysen

**Anwendungsfunktion:** AJO: Reporting und Leistungsanalyse

Überwachen Sie die Personalisierungsleistung mit den integrierten Berichten von AJO und erweitern Sie optional die Analyse mit CJA, um tiefere kanalübergreifende Einblicke zu erhalten. Diese Phase umfasst den Zugriff auf Live- und historische Kampagnenberichte, die Überprüfung der Experimentergebnisse und die Erstellung benutzerdefinierter Analyse-Arbeitsbereiche.

**Entscheidungspunkte in dieser Phase:**

>[!NOTE]
>**Entscheidung: Berichtstiefe** - Wie tief sollte die Leistungsanalyse gehen?

| Option | Zeitpunkt der Auswahl | Aspekte |
| --- | --- | --- |
| Nur native AJO-Berichte | Grundlegende Versand- und Interaktionsmetriken sind ausreichend | Bietet standardmäßig Impressionen, Klicks, CTR und Konversionsmetriken. Sofort in der Campaign-Benutzeroberfläche verfügbar. Eingeschränkte Anpassung |
| AJO-Berichte und CJA-Analyse | Detaillierte funnel-Analysen, Kohortenvergleiche oder Cross-Channel-Wirkungsmessungen sind erforderlich | Erfordert eine Verbindung mit CJA und eine Datenansicht, die mit AJO-Datensätzen verknüpft sind. Ermöglicht Freiformanalyse, benutzerdefinierte berechnete Metriken, Attributionsmodellierung und Zielgruppenveröffentlichung. |

**UI-Navigation:** [!DNL Journey Optimizer] > Kampagnen > Kampagne auswählen > Bericht anzeigen

**Wichtige Konfigurationsdetails:**

- Zugreifen auf den Live-Bericht während aktiver Kampagnen zur Überwachung des Echtzeit-Versands (wird alle 60 Sekunden aktualisiert, zeigt die letzten 24 Stunden)
- Zugriff auf den historischen Bericht (alle Zeiten) nach Abschluss der Kampagne für eine umfassende Analyse (kann bis zu 2 Stunden dauern, bis er vollständig ausgefüllt ist)
- Für Option B (Experiment): Überprüfen Sie den Experimentbericht auf Abwandlungs-Performance-Vergleich, Konfidenzintervalle und Gewinnererklärung
- Für die CJA-Analyse: Stellen Sie sicher, dass eine CJA-Verbindung AJO-Erlebnisereignis-Datensätze enthält und eine Datenansicht mit Web-Personalisierungsmetriken konfiguriert ist

**Wo die Optionen unterschiedlich sind:**

**Für Option A (regelbasiert):**
Überprüfen Sie die Kampagnenberichte für jedes Zielgruppensegment, um Versand- und Interaktionsmetriken über personalisierte Inhaltsvarianten hinweg zu vergleichen. Verwenden Sie CJA, um einen Vergleichsarbeitsbereich zu erstellen, der die Konversionswirkung von personalisierten Inhalten im Vergleich zu Standardinhalten misst.

**Für Option B (Experiment):**
Überprüfen Sie den Experimentbericht auf statistische Konfidenz, Behandlungserhöhung und Gewinneridentifizierung. Warten Sie, bis der Konfidenzschwellenwert erreicht ist, bevor Sie den Gewinner bekannt geben. Gewinner-Inhalte als permanente Variante anwenden (Übergang zu Option A für die fortlaufende Bereitstellung).

- **UI-Navigation:** Campaign > Inhaltsexperiment > Bericht anzeigen
- **Experience League:** [Inhaltsexperimentbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

**Für Option C (Entscheidung):**
Überprüfen Sie die Metriken zur Entscheidungsleistung, einschließlich der Impressionsraten von Angeboten, der Auswahlhäufigkeit und der Konversionsattribution pro Inhaltselement. Analysieren Sie die Leistung von Ranking-Strategien und ob Fallback-Inhalte zu häufig bereitgestellt werden (was darauf hinweist, dass die Eignungsregeln zu restriktiv sind).

**Dokumentation zu Experience League:**

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Statistische Berechnungen im Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## Überlegungen bei der Implementierung

In diesem Abschnitt werden Leitplanken, häufige Fallstricke, Best Practices und Entscheidungen bei der Abwägung für dieses Anwendungsfallmuster behandelt.

### Leitplanken und Beschränkungen

Überprüfen Sie die folgenden Leitplanken vor und während der Implementierung.

- Edge-Segmente sind auf einfache Attributprüfungen und Segmentzugehörigkeit beschränkt - keine Zeitreihenabfragen oder komplexen Aggregationen - [Berechtigung für die Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Pro Sandbox kann nur eine Zusammenführungsrichtlinie am Edge aktiv sein ([Profilleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximal 4.000 Segmentdefinitionen pro Sandbox - [Segmentierungsleitplanken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximal 500 aktive Live-Kampagnen pro Sandbox - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 10 Abwandlungsvarianten pro Inhaltsexperiment — [Grenzwerte für Inhaltsexperimente](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 10.000 genehmigte personalisierte Angebote pro Sandbox (Option C) - [Leitplanken für das Entscheidungs-Management](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximal 30 Platzierungen pro Entscheidung (Option C) - [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- KI-Ranking-Modelle erfordern mindestens 1.000 Konversionsereignisse für das Training (Option C)
- [!DNL Edge Network] Reaktionszeit SLA: &lt; 200 ms für Edge-ausgewertete Segmente
- Ablauf pseudonymer Profile: Konfigurierbar von 14 bis 365 Tagen für Profile, die nur auf ECID basieren
- Live-Berichte werden alle 60 Sekunden aktualisiert und zeigen die Daten der letzten 24 Stunden an
- Es kann bis zu 2 Stunden dauern, bis historische Berichte nach Abschluss der Kampagne vollständig ausgefüllt sind

### Häufige Fehler

Vermeiden Sie die folgenden häufigen Implementierungsfehler.

- **[!DNL Web SDK]keine Verhaltenssignale an AEP zu senden** Überprüfen Sie, ob der [!DNL Adobe Experience Platform]-Service für den Datenstrom aktiviert ist und der Ereignisdatensatz korrekt zugeordnet ist. Ohne diese Angabe werden keine Edge-Profile ausgefüllt und die Zielgruppen-Auswertung schlägt leise fehl - der Besucher erhält Standardinhalte ohne Fehleranzeige.
- **Edge-Zielgruppe, die keine Qualifikationen zurückgibt:** Die Edge-Segmentierung hat strenge Eignungsanforderungen. Zeitreihenabfragen, Aggregationsfunktionen und Abfragen mit mehreren Entitäten sind nicht Edge-fähig. Schreiben Sie den Segmentregelausdruck mithilfe einfacher Attributvergleiche oder Segmentzugehörigkeitsprüfungen neu.
- **Zusammenführungsrichtlinie in Edge nicht aktiv:** Wenn die vom Zielgruppensegment verwendete Zusammenführungsrichtlinie nicht `isActiveOnEdge: true` ist, schlagen die Suchen von Edge-Profilen fehl und die Personalisierung wird nicht bereitgestellt. Es kann nur eine Zusammenführungsrichtlinie pro Sandbox im Randbereich aktiv sein - stellen Sie sicher, dass kein Konflikt besteht.
- **Personalization flackert beim Laden der Seite:** Der [!DNL Web SDK] `sendEvent`-Aufruf, der Personalisierungsvorschläge abruft, muss ausgeführt werden, bevor die Seite den Zielinhaltsbereich rendert. Implementieren Sie das Vorab-Ausblenden von Snippets oder das asynchrone Rendering, um zu verhindern, dass der Standardinhalt aufblitzt, bevor der personalisierte Inhalt geladen wird.
- **Inhalte werden bei SPA-Routenänderungen nicht gerendert:** Single Page Applications erfordern bei Routenänderungen explizite `sendEvent` mit aktualisierten Ansichtsinformationen. Ohne diese Angabe bewertet der [!DNL Edge Network] die Personalisierung für die neue Ansicht nicht neu.
- **Experiment erreicht keine statistische Signifikanz:** Unzureichendes Traffic-Volumen oder zu viele Behandlungsvarianten verdünnen die Stichprobengröße pro Variante. Verringern Sie die Anzahl der Varianten oder erhöhen Sie die Experimentdauer. Stoppen Sie Experimente nicht vorzeitig - die Ergebnisse können irreführend sein.
- **Entscheidungsfindung gibt nur Fallback-Inhalte zurück** Überprüfen Sie, ob personalisierte Inhaltselemente innerhalb ihres Gültigkeitsdatumsbereichs genehmigt wurden und die Eignungsregeln mit den Edge-Profilattributen des anonymen Besuchers übereinstimmen. Stellen Sie auch sicher, dass die Begrenzungen nicht erreicht wurden.

### Best Practices

Befolgen Sie diese Empfehlungen für eine erfolgreiche Implementierung.

- **Einfach beginnen und dann iterieren:** Beginnen Sie mit Option A (regelbasiert) für die anfängliche Personalisierung, verwenden Sie dann Option B (Experimentieren), um Annahmen zu validieren, und Option C (Entscheidung) für erweiterte Anwendungsfälle. Jede Option basiert auf der grundlegenden Infrastruktur.
- **Vorab-Ausblendung zur Vermeidung von Flackern verwenden** Implementieren Sie das AEP-Code-Fragment zum Vorab-Ausblenden auf Seiten, auf denen die Personalisierung bereitgestellt wird. Dadurch wird der Zielinhaltsbereich ausgeblendet, bis der personalisierte Inhalt bereit zum Rendern ist, wodurch ein visuelles Flackern verhindert wird.
- **Fallback-Inhalt absichtlich entwerfen:** Der Standardinhalt (nicht personalisiert) sollte für sich genommen ein hochwertiges Erlebnis darstellen. Besucherinnen und Besucher, die sich nicht für die Personalisierung qualifizieren - oder wenn die [!DNL Edge Network] Antwort verzögert ist - sollten kein eingeschränktes Erlebnis erhalten.
- **Validieren der Edge-Eignung vor dem Erstellen von Zielgruppen:** Bevor Sie in die Entwicklung von Zielgruppenregeln investieren, überprüfen Sie in Experience League die Eignungskriterien, ob der Segmentregelausdruck Edge-geeignet ist. Nicht auswählbare Ausdrücke greifen für dieses Muster ohne Nachfrage auf die Batch- oder Streaming-Auswertung mit inakzeptabler Latenz zurück.
- **Überwachen der Versandleistung am Edge** Richten Sie die Überwachung von Warnhinweisen für [!DNL Edge Network] Antwortzeiten und Fehler bei der Personalisierung ein. Edge-Bereitstellungsprobleme sind für Besuchende nicht sichtbar (sie sehen Standardinhalte) und können ohne proaktive Überwachung unentdeckt bleiben.
- **Ablauf pseudonymer Profile konfigurieren:** Legen Sie geeignete Ablaufzeiträume für anonyme Edge-Profile fest, um die sitzungsübergreifende Personalisierung (Erkennung wiederkehrender Besucher) mit der Einhaltung von Datenschutzbestimmungen und der Speicherverwaltung in Einklang zu bringen.
- **Test mit repräsentativen Profilen:** Verwenden Sie bei der Vorschau personalisierter Inhalte Testprofile, die die tatsächlichen Szenarien anonymer Besucher darstellen (keine CRM-Daten, eingeschränkter Verhaltensverlauf, verschiedene geografische Standorte und Geräte).

### Entscheidungen über Kompromisse

Beachten Sie bei der Planung Ihrer Implementierung die folgenden Kompromisse.

>[!NOTE]
>**Kompromiss: Personalization-Breite vs. Implementierungskomplexität**
>
>Eine granularere Personalisierung (viele Zielgruppen, viele Inhaltsvarianten) führt zu relevanteren Erlebnissen, erhöht jedoch die Komplexität der Konfiguration und den Mehraufwand für die Inhaltserstellung.
>
>- **Umfassende Personalisierung begünstigt:** Einfachheit, schnellere Markteinführung, niedrigere Produktionskosten für Inhalte. Eine geringe Anzahl von Zielgruppen und Varianten deckt die Mehrheit der Besucher mit sinnvoller Personalisierung ab.
>- **Granulare Personalisierung begünstigt:** Maximale Relevanz, höhere Interaktionsrate, bessere Konversionsraten. Viele Zielgruppen und Varianten adressieren bestimmte Verhaltenssignale mit maßgeschneiderten Inhalten.
>- **Empfehlung:** Beginnen Sie mit 3-5 wirkungsvollen Personalisierungsregeln, die auf die häufigsten Besuchersegmente abzielen (z. B. Verweisquelle, Gerätetyp, geografische Region). Messen Sie die Auswirkungen und erweitern Sie dann auf detailliertere Regeln, die auf der beobachteten Leistung und dem beobachteten Geschäftswert basieren.

>[!NOTE]
>**Kompromiss: Regelbasierter Determinismus vs. KI-gesteuerte Optimierung**
>
>Regelbasierte Ansätze (Option A) geben dem Unternehmen die volle Kontrolle darüber, welche Inhalte jeder Besucher sieht. KI-bewertete Ansätze (Option C) optimieren die Inhaltsauswahl im Laufe der Zeit, reduzieren jedoch die Sichtbarkeit der Gründe für die Auswahl bestimmter Inhalte.
>
>- **Regelbasierte Gefälligkeiten:** Vorhersehbarkeit, Prüfbarkeit, Geschäftskontrolle. Marketing-Teams wissen genau, welche Inhalte jedes Segment erhält, und können die Logik den Stakeholdern erklären.
>- **KI-gesteuerte Vorteile:** Leistungsoptimierung, Skalierbarkeit, kontinuierliche Verbesserung. Das KI-Modell erkennt Affinitäten zwischen Inhaltsbesuchern, die das Erstellen menschlicher Regeln verpassen könnte.
>- **Empfehlung:** Verwenden Sie die regelbasierte Entscheidungsfindung für wichtige Inhaltsentscheidungen, bei denen Markenkonsistenz und Stakeholder-Transparenz von größter Bedeutung sind. Verwenden Sie KI-Rangfolgen für große Inhaltskataloge, bei denen das manuelle Regelmanagement umständlich wird und kontinuierliche Optimierung messbare Steigerung bietet.

>[!NOTE]
>**Kompromiss: Anonyme Profilpersistenz vs. Einhaltung von Datenschutzbestimmungen**
>
>Ein längerer Ablauf pseudonymer Profile ermöglicht eine bessere sitzungsübergreifende Personalisierung (Erkennung wiederkehrender Besucher, Aufbau eines Verhaltenskontexts im Laufe der Zeit). Ein kürzerer Ablauf verbessert die Einhaltung von Datenschutzbestimmungen und senkt die Speicherkosten.
>
>- **Längere Gültigkeitsdauer:** anonyme Profile, eine bessere Erkennung wiederkehrender Besucher, mehr Daten für Personalisierungsentscheidungen. Legen Sie die Gültigkeit auf 90 bis 365 Tage fest.
>- **Kürzere Gültigkeitsdauern:** Datenschutz-Compliance (DSGVO, CCPA), reduzierte Speicherkosten, minimiertes Risiko veralteter Profildaten. Gültigkeit auf 14-30 Tage festlegen.
>- **Empfehlung:** Sie die Gültigkeit an die Cookie-Einverständnisrichtlinie und die Datenschutzanforderungen Ihrer Organisation an. Bei den meisten Implementierungen bieten 30 bis 90 Tage ein angemessenes Gleichgewicht zwischen dem Wert der Personalisierung und der Einhaltung von Datenschutzbestimmungen.

## Verwandte Dokumentation

Die folgenden Experience League-Ressourcen bieten zusätzliche Details zu den in diesem Anwendungsfallmuster verwendeten Funktionen.

**Web-Kanal- und Code-basierte Erlebnisse**

- [Erste Schritte mit dem Web-Kanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Erstellen von Web-Erlebnissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-basierter Erlebniskanal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Code-basierte Erlebniskonfiguration](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Zielgruppen und Segmentierung**

- [Übersicht über den Segmentierungs-Service](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handbuch zur Benutzeroberfläche von Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming-Segmentierung](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-Referenz](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization und Inhalte**

- [Hinzufügen von Personalisierung](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-Syntax](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische Inhalte](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Arbeiten mit Inhaltsvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Arbeiten mit Inhaltsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**Inhaltsexperiment**

- [Erste Schritte mit einem Inhaltsexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Erstellen eines Inhaltsexperiments](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Bericht zu Inhaltsexperimenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische Berechnungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Entscheidungs-Management**

- [Überblick über das Entscheidungs-Management](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Erstellen von Platzierungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Entscheidungsregeln erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Personalisierte Angebote erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Erstellen von Fallback-Angeboten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Erstellen von Sammlungen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Entscheidungen erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangfolgestrategien](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Versand von Angeboten in Nachrichten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Kampagnen**

- [Erste Schritte mit Kampagnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Erstellen einer Kampagne](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]und Datenerfassung**

- [Übersicht über Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Installieren von Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Konfigurieren von Datenströmen](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Übersicht über Tags](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identität und Profil**

- [Identity Service - Übersicht](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Übersicht über Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)
- [Übersicht über Zusammenführungsrichtlinien](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**Datenmodellierung**

- [XDM-Systemübersicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grundlagen der Schemakomposition](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**Reporting und Analysen**

- [Kampagnen-Live-Bericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaler Kampagnenbericht](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Arbeiten mit Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Übersicht über Analysis Workspace](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Übersicht über CJA](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**Data Governance und Datenschutz**

- [Übersicht zur Daten-Governance](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Erweiterte Übersicht über die Verwaltung des Datenlebenszyklus](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Feldgruppe „Einverständnis und Voreinstellungen“](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Leitplanken**

- [Journey Optimizer-Leitplanken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Leitplanken für Echtzeit-Kundenprofile](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Leitplanken für Identity Service](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
