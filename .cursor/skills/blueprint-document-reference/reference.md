---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---
# Blueprint-Dokumentreferenz — Detailliertes Handbuch

## Dokumenttypen

| Typ | Zweck | Standort/Beispiel |
|------|---------|--------------------|
| **Übersicht/Hub** | Einführung in ein Produkt oder einen Bereich; Links zu Szenario-Blueprints | z. B. `overview.md`, `journey-optimizer-overview.md` |
| **Szenario-Blueprint** | Einzelner Anwendungsfall: Architektur, Schritte, Leitplanken | z. B. `real-time-lookup.md`, `journey-optimizer-journeys.md` |
| **TOC** | Navigation; nicht als Inhaltsvorlage verwenden | `help/blueprints/TOC.md` |

&#x200B;---

## Vollständiger Abschnitt

### Titel und Beschreibung (frontmatter)

- **title**: Kurz, spezifisch. Verwenden Sie `[!DNL Product Name]` für Produktnamen (z. B. `[!DNL Journey Optimizer]`).
- **description**: Ein Satz. Beschreiben Sie, was der Blueprint zeigt, und beschreiben Sie das Ergebnis (z. B. „Echtzeit-Kundenprofil-Zugriff am Edge für Web- und Mobile-Personalisierung„).

### Hauptteil

| Abschnitt | Einschließen | Inhaltsanleitung |
|---------|-----------------|-------------------|
| **Anwendungen** | Immer für Szenario-Blueprints | Liste aller beteiligten Adobe-Produkte/-Lösungen (z. B. Real-time Customer Data Platform, Datenerfassung) |
| **Anwendungsfälle** | Immer | Aufzählung der geschäftlichen/technischen Anwendungsfälle, die diese Blueprint unterstützt. |
| **Voraussetzungen** | Wenn eine Einrichtung erforderlich ist | Produkte, Subdomains, SDKs, Konfiguration, die vorhanden sein müssen. Link zu Experience League für Einrichtungsschritte. |
| **Architekturdiagramm** | Immer | Einzelnes Primärdiagramm (SVG wird empfohlen). Verwenden Sie einen einheitlichen Stil: `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`. Geben Sie einen aussagekräftigen `alt` an. |
| **Leitplanken** | Immer, wenn das Produkt Leitplanken hat | Link zu den offiziellen Experience League-Leitplanken. Fügen Sie Blueprint-spezifische Beschränkungen (z. B. TTL, Ratenbeschränkungen) als Aufzählungszeichen hinzu. |
| **Implementierungsmuster** | Wenn mehrere Ansätze existieren | Benennen Sie jedes Muster (z. B. „Muster 1: Zielgruppenzugehörigkeitsbasiert mit Web SDK„). Verwenden Sie Aufzählungszeichen für Verwendungszwecke und Kompromisse. |
| **Implementierungsschritte** | Für Szenario-Blueprints mit einem definierten Pfad | Nummerierte Liste. Jeder Schritt: Aktion + Link zu Experience League, wo das Verfahren lebt. Kopieren Sie nicht die vollständigen Verfahren. |
| **Überlegungen bei der Implementierung** | Wenn es wichtige Einschränkungen gibt | Unterabschnitte (z. B. Überlegungen zur Identität, attributbasierte Personalisierung). Aufzählungszeichen oder kurze Absätze; für Tiefe verknüpfen. |
| **Verwandte Dokumentation** | Immer | Gruppierte Links zu Experience League (und optional developer.adobe.com). Siehe &quot;Experience League Link Groups“ unten. |

### Überblick/Hub-Seiten

- Beginnen Sie mit 1-2 Absätzen über das Produkt/den Bereich und darüber, was die Blueprints abdecken.
- **Anwendungsfälle**: Kann `>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]` für mehrere Kategorien verwenden.
- **Architektur**: Ein Hauptdiagramm.
- **Blueprint-Szenarien** oder **Integrationsmuster**: Tabelle mit Szenarionamen, Kurzbeschreibung und Link zur Szenario-Blueprint.
- **Voraussetzungen**, **Leitplanken**, **Verwandte Dokumentation**: Wie oben; kurz halten.

&#x200B;---

## Adobe Experience League - Agenten-Anleitungen

### Wann auf Experience League verwiesen werden sollte

- **Produktdokumentation**: Funktionsweise eines Produkts, Benutzeroberflächen-Abläufe, Konzepte.
- **APIs**: Endpunkte, Parameter, Beispiele (Experience Platform, Edge usw.).
- **Leitplanken**: Offizielle Leitplankenseiten für das Produkt oder den Service.
- **Tutorials**: Schritt-für-Schritt-Anleitungen (z. B. Erstellen von Schemata, Aktivieren von Zielen).
- **Konfiguration**: Datenströme, Ziele, Zusammenführungsrichtlinien, Identitäten usw.

Fügen Sie keine langen Vorgänge aus Experience League in den Blueprint ein. Zusammenfassen und verknüpfen.

### URL-Muster

| Inhaltstyp | Basis-URL | Beispielpfad |
|--------------|----------|--------------|
| Experience Platform-Dokumente | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`, `.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/de/docs/` | Gleiche Struktur wie oben bei `/en/`. |
| Journey Optimizer   | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`, `.../commands/command-responses.html` |
| Edge Network Server-API | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`, `.../guardrails.html` |
| Mobile SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`, `.../edge/adobe-journey-optimizer-decisioning/` |
| Tags | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Platform-Tutorials | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

Verwenden Sie den kanonischen Pfad, der mit der aktuellen Experience League-Site übereinstimmt (bevorzugen Sie `/en/docs/`, wenn der englische Pfad bekannt ist).

### Link-Formatierung im Markdown

- **Text des beschreibenden Links**: `[Create schemas](https://experienceleague.adobe.com/de...)` „hier klicken“.
- **Produktnamen im Text**: Verwenden Sie `[!DNL Product Name]` nach Adobe-Stil (z. B. `[!DNL Real-time Customer Profile]`).
- **Externe Links**: Fügen Sie `{target="_blank"}` nur hinzu, wenn die Vorlage oder Pipeline dies erfordert (überprüfen Sie vorhandene Blueprints im Repository).

### Ergänzende Dokumentation — Empfohlene Gruppen

Verwenden Sie diese Gruppen, wenn sie gelten:

1. **Zielkonfigurationen** (für Blueprints zur Aktivierung/Edge-Personalisierung)
2. **Dokumentation zu SDK** (Web SDK, Mobile SDK, Edge Network Server API, Tags)
3. **Profil und Segmentierung** (Echtzeit-Kundenprofil, Zusammenführungsrichtlinien, Segmentierung)
4. **Tutorials** (plattformspezifische oder produktspezifische schrittweise Anleitungen)
5. **Produktdokumentation** (Hauptproduktdokument, Startseite oder wichtige Unterabschnitte)
6. **Leitplanken** (falls nicht bereits im Abschnitt „Leitplanken“ enthalten)

Beispiel:

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/de/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=de)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=de)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=de)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
```

&#x200B;---

## Repository und Inhaltsverzeichnis

- **Blueprint-**: `help/blueprints/` (mit Unterordnern nach Bereich, z. B. `audience-activation/`, `customer-journeys/journey-optimizer/`).
- **Assets**: Verwenden Sie die Blueprint (z. B. `assets/`, `images/`) oder einen freigegebenen Ordner (z. B. `experience-platform/assets/`).
- **TOC**: `help/blueprints/TOC.md` beim Hinzufügen, Umbenennen oder Verschieben von Blueprint-Seiten bearbeiten. Bewahren Sie die Frontansicht (`user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`) und die `+` Hierarchie auf.

&#x200B;---

## Beispielverweise in diesem Repository

- **Szenario-Blueprint (lange Form)**: `help/blueprints/audience-activation/real-time-lookup.md`
- **Übersicht/Hub mit Registerkarten und Tabellen**: `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **Leitplanken-fokussiert**: `help/blueprints/experience-platform/guardrails.md`
- **Navigation**: `help/blueprints/TOC.md`, `help/blueprints/overview.md`

Verwenden Sie diese als Muster für die Abschnittsreihenfolge, die Schriftart, die Diagrammplatzierung und die Verwendung von Experience League-Links.
