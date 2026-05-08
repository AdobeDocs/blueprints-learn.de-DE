---
source-git-commit: f92cdf8d710acac28d29594f10713e055035cfe9
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---
# Leitplanken für Umfang: Architekturseite vs. Anwendungsfall-Musterseite

Die Blueprints-Site trennt **Architekturdiagrammseiten** von **Anwendungsfall-Musterseiten** da sie unterschiedlichen Leseranforderungen dienen. In diesem Dokument wird definiert, was wo hingehört und wie Inhalte verarbeitet werden, die über die Grenze hinweg driften.

## Die Hauptunterscheidung

- **Architekturdiagrammseiten** sind visuelle Verweise auf oberster Ebene. Sie antworten: *„Wie passen diese Systeme zusammen? Wo sind die Integrationspunkte? Wie sieht der Datenfluss aus?“* Leser kommen hierher, um sich zu orientieren.
- **Seiten mit Anwendungsfallmustern** sind Implementierungshandbücher. Sie antworten: *Wie baue ich diese Funktion auf? Welche Funktionen sind betroffen? Welche KPIs messen den Erfolg? Was sind meine Implementierungsoptionen?“* Leser kommen hierher, wenn sie einen Anwendungsfall haben und ihn versenden müssen.

## Gehört zu einer Architekturseite

| Kategorie | Beispiele |
| --- | --- |
| Architektur der obersten Ebene | Übersichtsdiagramme von AEP und Anwendungen, Experience Cloud-Marktektur, Hub und Edge-Topologie |
| Systemdatenfluss | Echtzeit- vs. Batch-Aufnahme-Pfade, Profilsynchronisierung zwischen Hub und Edge, Lookup vs. Aktivierungsflüsse |
| Integrationspunkte | Hierbei integriert sich AEP mit AJO, CJA, Target, Campaign, Marketo, Workfront; SDK-Grenzen; API-Oberflächen |
| Bereitstellungstopologie | Web SDK im Vergleich zur mobilen SDK-Bereitstellung, Server-seitige Weiterleitung, Platzierung von Edge-Knoten |
| Anwendungsarchitektur | Wie ein einzelnes Programm (AJO, CJA, RTCDP) intern auf Systemebene strukturiert ist |
| Hinweise zur Verwendung von Fallmustern | „Diese Architektur unterstützt die Muster X, Y, Z mit Links - die Architekturseite dupliziert **Inhalt**. |

## Gehört NICHT zu einer Architekturseite

Wenn Sie Folgendes schreiben, leiten Sie zu einer Anwendungsfall-Musterseite um (verwenden Sie die `use-case-pattern-builder` Kenntnisse):

| Kategorie | Warum es woanders hingehört |
| --- | --- |
| KPIs und Messformeln | Anwendungsfallmuster messen Ergebnisse; Architekturseiten nicht |
| Geschäftsziele, geschäftliche Auswirkungen | KBO-Inhalte befinden sich unter `/help/blueprints/business-objectives/`; Muster verweisen darauf |
| Beispiele für taktische Anwendungsfälle | „Warenkorbabbruch-Erinnerung“, „Personalisierter Startseiten-Held“ usw. - Dies sind Musterinhalte |
| Funktionsketten (`A > B > C > D`) | Das Funktionskettenkonstrukt ist Teil der Vorlage für Anwendungsfälle |
| Persönliche Erzählungen | „Maria, die Marketing-Expertin, möchte…“ Stilszenarien gehören in Muster, nicht in Architekturverweise |
| Implementierungsoptionen | Anleitungen für die Implementierung mehrerer Optionen (Best Practices, Funktionsweise, Vorteile, Einschränkungen) sind ein Musterkonstrukt |
| Grundlegende/unterstützende Funktionstabellen | Dies sind Abschnitte mit Musterseiten |
| Vorausgesetzte Checklisten pro Anwendungsfall | Muster verfolgen diese Architekturseiten. Stattdessen werden Seiten mit Mustern verknüpft |

## Trigger-Sätze, auf die geachtet werden muss

Wenn der/die Benutzende beim Beschreiben der neuen Seite eine dieser Phrasen bereitstellt, pausieren und überprüfen Sie den Umfang erneut:

- „KPIs“
- „Business Impact“ / „Business Outcomes“
- „Taktische Anwendungsfälle“ / „Beispielszenarien“
- „Funktionskette“
- „Implementierungsoptionen“
- „Am besten geeignet für“
- „Vorteile und Einschränkungen“
- „Voraussetzungen“
- „Personas“ / „Stakeholder“
- „Messung“

Diese disqualifizieren die Seite nicht automatisch - sie signalisieren jedoch, dass der Benutzer möglicherweise eine Anwendungsfall-Musterseite und keine Architekturseite wünscht. Bestätigen Sie die Absicht, bevor Sie generieren.

## Was zu tun ist, wenn Inhalte abweichen

1. **Identifizieren Sie die Abweichung.** Zeigen Sie auf den spezifischen Abschnitt oder Aufzählungszeichen, der die Begrenzung überschritten hat.
2. **Bieten Sie dem Benutzer zwei Optionen an:**
   - Schneiden Sie den Abschnitt auf der Architekturseite aus (am häufigsten - damit die Architekturseite fokussiert bleibt).
   - Halten Sie an und wechseln Sie zu `use-case-pattern-builder` für diesen Inhalt (wenn der Benutzer tatsächlich eine Musterseite haben möchte).
3. **Auf Bestätigung warten.** Inhalte nicht im Hintergrund neu schreiben oder ablegen.
4. **Wenn nur architekturspezifische Inhalte beibehalten werden** ersetzen Sie die tiefen Inhalte durch einen einzelnen Aufzählungszeichen unter `## Use case patterns supported` Verknüpfung mit dem relevanten Muster (vorhanden oder zu erstellen).

## Edge-Fälle

- **Seite ist halbe Architektur, halbes Muster.** In zwei Seiten unterteilt - eine Architekturseite (diese Kenntnis), eine Anwendungsfall-Musterseite (die `use-case-pattern-builder`). Verknüpfen Sie sie.
- **Die Seite „Architektur“ beschreibt einen einzelnen Anwendungsfall von Anfang bis Ende.** Dies ist ein Anwendungsfallmuster, keine Architekturseite. Zu `use-case-pattern-builder` umleiten.
- **Die Seite „Architektur“ muss Beispieldatenflüsse für ein bestimmtes Szenario anzeigen.** Akzeptiert, wenn das Szenario nur zur Veranschaulichung gedacht ist und der Großteil der Seite auf der Ebene der Systemarchitektur bleibt. Lassen Sie das Beispiel auf einen Absatz beschränkt und verknüpfen Sie ihn mit dem entsprechenden Muster, um weitere Details zu erhalten.

## Schnelltest

Fragen Sie vor der Generierung: *„Wenn ein Leser auf dieser Seite landet und eine Architekturreferenz der obersten Ebene erwartet, erhält er eine - oder wird er eine exemplarische Vorgehensweise für einen halb fertigen Anwendungsfall erhalten?“* Bei letzterem gehört die Seite in `use-case-pattern-builder`.
