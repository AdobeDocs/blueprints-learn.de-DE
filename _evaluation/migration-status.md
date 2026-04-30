---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---
# Migrationsstatus - Blueprints für Anwendungsfallmuster

Dieses Dokument erfasst den Status des Blueprint-Reorganisationsvorgangs, damit er sitzungsübergreifend sauber fortgesetzt werden kann.

**Zuletzt aktualisiert:** 2026-04-29

## Wo wir gerade sind

**Derzeit angehalten am:** `b2b/overview.md` (B2B-Abschnitt-Blueprint-#1 von 10) - wartet auf eine Entscheidung darüber, ob der Status beibehalten werden soll, fügt einen Querverweis zum neuen Abschnitt „B2B-Aktivierungs- und Marketing-Muster“ hinzu oder aktualisiert die Tabelle, um alle Blueprints aufzulisten + Querverweis hinzufügen.

**Fortsetzen:** antworten mit **A** (unverändert lassen, empfohlen), **B** (Querverweis hinzufügen) oder **C** (Tabelle aktualisieren + Querverweis hinzufügen). Fahren Sie dann mit der Blueprint-#2 (`b2b/b2bactivation.md`) fort.

## Arbeitsansatz

Das auf dieser Tagung vereinbarte derzeitige Arbeitsmuster lautet:

1. **Blueprints am Leben erhalten** — keine Einstellung. Jeder Blueprint bleibt als architekturorientierte Seite vorhanden.
2. **Verknüpfungs-TIPP hinzufügen** zu jedem Blueprint mit einem verwandten/überlappenden Anwendungsfallmuster, unmittelbar nach dem H1:

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **Diagramme migrieren** - Wenn ein Blueprint über ein Architekturdiagramm verfügt, das dem zugehörigen Muster fehlt, fügen Sie dem Muster einen `## Architecture` Abschnitt hinzu, der über den absoluten Pfad auf dieselbe SVG verweist. Das Asset bleibt am ursprünglichen Speicherort (keine Dateikopien).
4. **Zuschneiden von Implementierungsschritten** aus dem Blueprint, sofern im Muster behandelt. Zu entfernende Abschnitte umfassen normalerweise: `## Implementation steps`, `## Implementation patterns`, `## Implementation considerations`, manchmal `## Prerequisites`. Urteilsfindung pro Blueprint verwenden.
5. **Nacheinander durchgehen** - Änderungen pro Blueprint vorschlagen, Benutzerzustimmung einholen und dann anwenden.

### Allgemeine Regeln

- Der Wortlaut der verknüpften TIPP ist konsistent: `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- Neue Dateien (während der Migration erstellte Anwendungsfallmuster) **enthalten keine`exl-id`** - diese werden von der Adobe-Veröffentlichung zugewiesen.
- Bildverweise in neu erstellten Dateien verwenden absolute Pfade (`/help/blueprints/...`), keine relativen.
- Vorhandene `exl-id` auf vorhandenen Seiten werden beibehalten.
- Umleitungen in `redirects.csv` folgen dem Format `source,dest` mit `/en/docs/...` Pfaden (keine `.html`).

## Phasen A-E (erste strukturelle Arbeiten) — ABGESCHLOSSEN

| Phase | Ergebnis |
| --- | --- |
| A | `B2B Activation & Marketing` Anwendungsfall-Musterkategorie erstellt. 3 vorhandene Muster wurden neu angeordnet (`b2b-audience-activation` → `b2b/account-audience-activation`, `buying-group-based-marketing` → `b2b/buying-group-marketing`, `b2b-analytics` → `b2b/account-analytics`). 3 Weiterleitungen hinzugefügt. |
| B | 4 B2B-Blueprints nach `use-case-patterns/b2b/` kopiert (`marketo-data-journeys`, `paid-media-orchestration`, `campaign-intake-and-creation`, `campaign-review-and-approval`). |
| C | 4 Nicht-B2B-Blueprints kopiert (`real-time-profile-lookup`, `data-science-profile-enrichment`, `edge-profile-access`, `campaign-v8-orchestration`). |
| D | 2 Aufspaltungs-Blueprints (`audience-sharing-with-target`, `third-party-messaging`) kopiert. |
| E | Es wurde eine Verknüpfungs-TIPP zu 9 doppelt klassifizierten Blueprints hinzugefügt. |

Anwendungsfallmuster insgesamt nach A-E: **26 Muster** in 6 Kategorien.

## Abschnittsweise Anleitung (in Bearbeitung)

In der exemplarischen Vorgehensweise wird der Ansatz der Querverbindung / Diagrammmigration / impl-trim auf jeden Blueprint angewendet, der einzeln von Benutzenden überprüft wird.

### ✅ Zielgruppe und Profilaktivierung - 8/8 abgeschlossen

| # | Blueprint | Durchgeführte Aktion |
| --- | --- | --- |
| 1 | `audience-manager.md` | Verknüpfen von TIPP + Diagramm, das zu Muster (`anonymous-visitor-web-personalization`) + RTCDP migriert wurde Impl-Schritte entfernt |
| 2 | `enterprise-destinations.md` | Verknüpfen von TIPP + Diagramm nach Muster migriert (`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | Impl Schritte entfernt (99 → 35 Zeilen) |
| 4 | `customer-activity.md` | Impl Schritte entfernt (51 → 40 Zeilen) |
| 5 | `data-science.md` | Impl-Überlegungen entfernt (46 → 40 Zeilen) |
| 6 | `real-time-lookup.md` | PreEqs + impl Muster/Schritte/Überlegungen entfernt (156 → 73 Zeilen) |
| 7 | `segment-match.md` | **Keine Änderungen** (der Benutzer hat sich dafür entschieden, die Seite unverändert zu lassen) |
| 8 | `rtcdp-target.md` | Impl-Muster + entfernte Überlegungen (99 → 74 Zeilen) |

### 🟡 B2B-Aktivierung und -Marketing - 1/10 in Bearbeitung

| # | Blueprint | Status |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **PAUSED** - wartet auf Entscheidung A/B/C (siehe „Wo wir gerade sind“ oben) |
| 2 | `b2b/b2bactivation.md` | Ausstehend — Phase E dupliziert; Querverbindung hinzugefügt; Überprüfung für Diagramm + Kürzung erforderlich |
| 3 | `b2b/b2b-account-activation.md` | Ausstehend - Diagramm klassifiziert; muss mit `b2b/account-audience-activation.md` verknüpft werden + Überlegungen zur Diagrammmigration |
| 4 | `b2b/b2b-buying-group-journeys.md` | Ausstehend — Phase E dupliziert; Querverbindung hinzugefügt; muss überprüft werden |
| 5 | `b2b/b2b-journeys-with-marketo.md` | Ausstehend - Phase B-Kopie; Muster ist eine Kopie; erfordert einfaches Zuschneiden |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | Ausstehend - Phase B-Kopie; erfordert einfaches Zuschneiden |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | Ausstehend - Abschnitt-Landingpage |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | Ausstehend - Phase B-Kopie; erfordert einfaches Zuschneiden |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | Ausstehend - Phase B-Kopie; erfordert einfaches Zuschneiden |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | Ausstehend - Nur-Link-Seite (Audit als Navigation gekennzeichnet) |

### ⚪ Customer Journey Analytics - 0/5 noch nicht gestartet

Dateien: `overview.md`, `b2b-cja.md` (Phase E duplizieren, Querverbindung hinzugefügt), `cja-rtcdp.md` (Gruppe 2 — Querverbindung zu `customer-analytics-insight-generation` empfehlen), `cja-ajo.md` (Gruppe 2 — identisch), `analysis.md` (Gruppe 3, evtl. zu Experience-Platform/).

### ⚪ Kunden-Journey - 0/14 noch nicht gestartet

Dateien: `overview.md`; `journey-optimizer/` (4 Dateien: Übersicht, Journey [Phase E], Kampagnen [Phase E], Nachrichten von Drittanbietern [Phase D]); `decision-management/` (3 Dateien: Übersicht, Edge [Phase E], Hub [Phase E]); `campaign-v8/` (3 Dateien: Übersicht [Phase C], rtcdp-and-v8, ajo-and-v8); `campaign-v7/` (3 veraltete Dateien).

### ⚪ Experience Platform - 0/6 noch nicht gestartet

Dateien: `experience-cloud.md`, `platform-applications.md`, `platform-data-flow.md`, `guardrails.md`, `deployment/websdk.md`, `deployment/appsdk.md`. Alle wurden im Audit als Nur-Diagramm mit 0 Mustersignalen bewertet. **Wahrscheinlich alle „keine Änderung“** - es handelt sich um eine grundlegende Architektur, mit der sich kein Anwendungsfallmuster überschneidet.

## Referenzdateien

| Datei | Zweck |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | Audit-Tabelle pro Blueprint (43 Zeilen) mit Empfehlungen |
| [rubric.md](rubric.md) | Zur Klassifizierung von Blueprints verwendete Bewertungsrubrik |
| [migration-redirects.csv](migration-redirects.csv) | Staging-Weiterleitungen von der Migration |
| [redirects.csv](../redirects.csv) | Kanonische Weiterleitungsdatei (3 Zeilen in Phase A hinzugefügt) |

## Offene Fragen noch ungelöst (aus Prüfung)

1. **Entscheidungs-Management-Edge + -Hub** - beide vernetzen sich derzeit mit `offer-decisioning`. Soll die Konsolidierung in einem einzigen Bereitstellungsoptionendiagramm erfolgen?
2. **`journey-optimizer-journeys.md`** — als unsicheres Duplikat von `event-triggered-messaging` gekennzeichnet; Überprüfung des Umfangs vor dem Zuschneiden.
3. **`customer-journey-analytics/analysis.md`** - Bei Inhalten geht es um den Experience Platform Query Service, nicht um CJA. Ziehen Sie einen Wechsel zu `experience-platform/` in Betracht.
4. **Campaign v7 (3 veraltete Dateien)** - Migration, Verlassen oder Entfernen aus dem Inhaltsverzeichnis?
5. **`customer-success-stories.md`** — Nur-Link-Seite; Bestätigung der Navigationsklassifizierung.
6. **Inhaltsverzeichnisanker** für neuen B2B-Abschnitt ist `{#b2b-patterns}` - bestätigen Sie dies, bevor Sie eine Produktions-Umleitung erstellen.

## Fortsetzen

Öffnen Sie eine neue Claude Code-Sitzung in diesem Repository und sagen Sie:

> Setzen wir die Blueprint-Migration fort. Lesen Sie `_evaluation/migration-status.md`, um dort weiterzumachen, wo wir aufgehört haben.

Der nächste konkrete Schritt: Reaktion auf die `b2b/overview.md` Entscheidung (A/B/C). Fahren Sie dann mit der Blueprint-#2 (`b2b/b2bactivation.md`) fort und fahren Sie mit dem B2B-Abschnitt fort, gefolgt von Customer Journey Analytics, Kunden-Journey und Experience Platform.
