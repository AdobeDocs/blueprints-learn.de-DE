---
source-git-commit: 2ed15399073fce5ebd1c2ba07b1cf70ec706452c
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 2%
---
# Migrationsstatus â€&quot; Blueprints für Anwendungsfälle

Dieses Dokument erfasst den Status des Blueprint-Reorganisationsvorgangs, damit er sitzungsübergreifend sauber fortgesetzt werden kann.

**Zuletzt aktualisiert:** 2026-09-24

## Wo wir gerade sind

Der B2B-Abschnitt wurde nicht mehr angehalten. Der Umfang der veröffentlichten Architektur ist jetzt auf die Seiten „Zielgruppe/Profil“ und „Kontoaktivierung“ beschränkt, wobei eingestellte Seiten zur Kategorieübersicht weitergeleitet werden.

**Aktueller Status:** Die Bereinigung der B2B-Architektur ist abgeschlossen. Die Seiten für Zielgruppe/Profil und Kontoaktivierung verbleiben in der Kategorie „Architecture-Diagrams“; die anderen Seiten für die B2B-Architektur wurden eingestellt und zur Kategorieübersicht weitergeleitet.

## Arbeitsansatz

> Der unten beschriebene Arbeitsansatz ist historisch; der B2B-Abschnitt wurde seitdem wie oben beschrieben angeordnet.

Das auf dieser Tagung vereinbarte derzeitige Arbeitsmuster lautet:

1. **Blueprints am Leben erhalten** â€&quot; Keine Einstellung. Jeder Blueprint bleibt als architekturorientierte Seite vorhanden.
2. **Verknüpfungs-TIPP hinzufügen** zu jedem Blueprint mit einem verwandten/überlappenden Anwendungsfallmuster, unmittelbar nach dem H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Diagramme migrieren** â€&quot; Wenn ein Blueprint über ein Architekturdiagramm verfügt, das dem zugehörigen Muster fehlt, fügen Sie dem Muster einen `## Architecture` Abschnitt hinzu, der über den absoluten Pfad auf dieselbe SVG verweist. Das Asset bleibt am ursprünglichen Speicherort (keine Dateikopien).
4. **Zuschneiden von Implementierungsschritten** aus dem Blueprint, sofern im Muster behandelt. Zu entfernende Abschnitte umfassen normalerweise: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, manchmal `## Prerequisites`. Urteilsfindung pro Blueprint verwenden.
5. **Schritt für Schritt** â€&quot; Änderungen pro Blueprint vorschlagen, Benutzerzustimmung einholen, dann anwenden.

### Allgemeine Regeln

- Der Wortlaut der verknüpften TIPP ist konsistent: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- Neue Dateien (während der Migration erstellte Anwendungsfallmuster) **enthalten keine`exl-id`** â€&quot; Diese werden von Adobe zugewiesen.
- Bildverweise in neu erstellten Dateien verwenden absolute Pfade (`/help/blueprints/...`), keine relativen.
- Vorhandene `exl-id` auf vorhandenen Seiten werden beibehalten.
- Umleitungen in `redirects.csv` folgen dem Format `source,dest` mit `/en/docs/...` Pfaden (keine `.html`).

## Phasen aâ€„E (erste bauliche Arbeiten) â€&quot; ABGESCHLOSSEN

| Phase | Ergebnis |
| --- | --- |
| A | `B2B Activation & Marketing` Anwendungsfall-Musterkategorie erstellt. Verlagerte 3 vorhandene Muster (`b2b-audience-activation` â†’ `b2b/account-audience-activation`, `buying-group-based-marketing` â†’ `b2b/buying-group-marketing`, `b2b-analytics` â†’ `b2b/account-analytics`). 3 Weiterleitungen hinzugefügt. |
| B | 4 B2B-Blueprints nach `use-case-patterns/b2b/` kopiert (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | 4 Nicht-B2B-Blueprints kopiert (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | 2 Aufspaltungs-Blueprints (`audience-sharing-with-target`, `third-party-messaging`) kopiert. |
| E | Es wurde eine Verknüpfungs-TIPP zu 9 doppelt klassifizierten Blueprints hinzugefügt. |

Anwendungsfallmuster insgesamt nach Aâ€„E: **26 Mustern** in 6 Kategorien.

## Abschnittsweise Anleitung (in Bearbeitung)

In der exemplarischen Vorgehensweise wird der Ansatz der Querverbindung / Diagrammmigration / impl-trim auf jeden Blueprint angewendet, der einzeln von Benutzenden überprüft wird.

### âoe… Zielgruppe und Profilaktivierung â€&quot; 8/8 abgeschlossen

| # | Blueprint | Durchgeführte Aktion |
| --- | --- | --- |
| 1 | `audience-manager.md` | Verknüpfen von TIPP + Diagramm, das zu Muster (`anonymous-visitor-web-personalization`) + RTCDP migriert wurde Impl-Schritte entfernt |
| 2 | `enterprise-destinations.md` | Verknüpfen von TIPP + Diagramm nach Muster migriert (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Impl Schritte entfernt (99 â†’ 35 Zeilen) |
| 4 | `customer-activity.md` | Impl Schritte entfernt (51 â†’ 40 Zeilen) |
| 5 | `data-science.md` | Einfache Überlegungen entfernt (46 â†’ 40 Zeilen) |
| 6 | `real-time-lookup.md` | PreEqs + impl Muster/Schritte/Überlegungen entfernt (156 â†’ 73 Zeilen) |
| 7 | `segment-match.md` | **Keine Änderungen** (der Benutzer hat sich dafür entschieden, die Seite unverändert zu lassen) |
| 8 | `rtcdp-target.md` | Impl-Muster + Überlegungen entfernt (99 â†’ 74 Zeilen) |

### ð Wir sind bei der B2B-Aktivierung und dem Marketing â€&quot; 1/10 in Bearbeitung

| # | Blueprint | Status |
| --- | --- | --- |
| 1 | `b2b/overview.md` | Abgeschlossen - B2B-Kategorieübersicht aktualisiert |
| 2 | `b2b/b2bactivation.md` | Eingestellt - ersetzt durch die Architekturdiagramm-Zielgruppe/Profilseite |
| 3 | `b2b/b2b-account-activation.md` | Beibehalten - Migration zur Kategorie „Architektur-Diagramme B2B“ |
| 4 | `b2b/b2b-buying-group-journeys.md` | Retired |
| 5 | `b2b/b2b-journeys-with-marketo.md` | Retired |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | Retired |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | Retired |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | Retired |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | Retired |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | Retired |

### âšª Customer Journey Analytics â€&quot; 0/5 noch nicht gestartet

Dateien: `overview.md`, `b2b-cja.md` (Phase E duplizieren, Querverbindung hinzugefügt), `cja-rtcdp.md` (Gruppe 2 â€&quot; Querverbindung zu `customer-analytics-insight-generation` empfehlen), `cja-ajo.md` (Gruppe 2 â€&quot; dasselbe), `analysis.md` (Gruppe 3, möglicherweise zu Experience-Platform/ verschieben).

### âšª Kunden-Journey â€&quot; Auslaufbereinigung abgeschlossen; Migration der gespeicherten Seite ausstehend

Dateien: `overview.md`; `journey-optimizer/` (4 Dateien: Übersicht, Journey [Phase E], Kampagnen [Phase E], Nachrichten von Drittanbietern [Phase D]); `campaign-v8/` (3 Dateien: Übersicht [Phase C], rtcdp-and-v8, ajo-and-v8). `decision-management/` und `campaign-v7/` wurden vollständig eingestellt. Ihre historischen Einträge verbleiben beim Audit und ihre URLs werden zu den genehmigten Übersichtsseiten weitergeleitet.

### âšª Experience Platform â€&quot; 0/6 noch nicht gestartet

Dateien: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. Alle wurden im Audit als Nur-Diagramm mit 0 Mustersignalen bewertet. **Wahrscheinlich alle „keine Änderung“** â€&quot; sind sie grundlegende Architektur, mit der sich kein Anwendungsfallmuster überschneidet.

Die Entscheidungen zum Entscheidungs-Management und zur Außerkraftsetzung von Campaign v7 sind abgeschlossen. Ihre offenen Fragen
sind nur historische Daten und sollten die verbleibenden Migrationsarbeiten nicht blockieren.

## Referenzdateien

| Datei | Zweck |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Audit-Tabelle pro Blueprint (43 Zeilen) mit Empfehlungen |
| [rubric.md](rubric.md) | Zur Klassifizierung von Blueprints verwendete Bewertungsrubrik |
| [migration-redirects.csv](migration-redirects.csv) | Staging-Weiterleitungen von der Migration |
| [redirects.csv](../redirects.csv) | Kanonische Weiterleitungsdatei (3 Zeilen in Phase A hinzugefügt) |

## Offene Fragen noch ungelöst (aus Prüfung)

&#x200B;2. **`journey-optimizer-journeys.md`** â€&quot; als unsicheres Duplikat von `event-triggered-messaging` gekennzeichnet; Umfang vor dem Zuschneiden überprüfen.
&#x200B;3. **`customer-journey-analytics/analysis.md`** â€&quot;-Inhalt handelt von Experience Platform Query Service, nicht von CJA. Ziehen Sie einen Umzug nach `experience-platform/` in Betracht.
&#x200B;4. **`customer-success-stories.md`** â€&quot; nur-Links-Seite; Bestätigung der Navigationsklassifizierung.
&#x200B;5. Historische TOC-Anker-Frage durch die abgeschlossene B2B-Architektur-Disposition ersetzt.

## Fortsetzen

Öffnen Sie eine neue Claude Code-Sitzung in diesem Repository und sagen Sie:

> Setzen wir die Blueprint-Migration fort. Lesen Sie `_evaluation/migration-status.md`, um dort weiterzumachen, wo wir aufgehört haben.

Die Bereinigung der B2B-Architektur ist abgeschlossen. Fahren Sie nach der Validierung mit der nächsten geplanten Architekturkategorie fort.
