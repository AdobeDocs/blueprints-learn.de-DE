---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League — Referenz zu genehmigten Metadatenfeldern

*Abgerufen vom Adobe ExL Authoring Guide (crawlen im Februar 2026) + Repo Analysis of blueprints-learn.de*

---

## Metadaten-Hierarchie

Metadaten-Kaskaden in dieser Reihenfolge (Artikel überschreibt Inhaltsverzeichnis, Inhaltsverzeichnis überschreibt Repository):
1. Artikelvorderseite (höchste Priorität)
2. TOC.md im Benutzerhandbuch
3. metadata.md im Repository-Stamm (niedrigste Priorität)

---

## Felder auf Artikelebene

### ERFORDERLICH

| Feld | Beschreibung | Format/Einschränkungen |
|-------|-------------|----------------------|
| `title` | SEO Seitentitel. Erscheint in den Suchergebnissen. | Maximal ~60 Zeichen; Title Case; `[!DNL Product]` für Produktnamen verwenden; H1 NICHT exakt duplizieren, es sei denn, dies ist beabsichtigt |
| `description` | Meta-Beschreibung für Suchmaschinen und ExL-Empfehlungen. | 150-160 Zeichen; idealerweise beginnt „Lernen, wie man…“ oder „Weitere Informationen …“; die Validierung schlägt fehl, wenn/null |
| `exl-id` | Systemspezifische eindeutige Kennung. Wird für das Content-Tracking verwendet. | UUID-Format (z. B. `70573eb9-cd69-4fe6-b2ae-dae81665a308`); **beim Kopieren einer Datei löschen** — wird automatisch zugewiesen; niemals dateiübergreifend duplizieren |

### DRINGEND EMPFOHLEN

| Feld | Beschreibung | Gültige Werte |
|-------|-------------|--------------|
| `solution` | Adobe-Produkte, auf die sich der Artikel bezieht. Wird für die ExL-Suche/Filterung und Inhaltsempfehlungen verwendet. | Kommagetrennt; Unterscheidung zwischen Groß- und Kleinschreibung; muss mit der genehmigten Enumeration übereinstimmen (siehe Gültige Lösungswerte unten) |

### OPTIONAL — ALLGEMEIN

| Feld | Beschreibung | Gültige Werte/Notizen |
|-------|-------------|----------------------|
| `kt` | JIRA-Nummer des Wissensartikels. Wird für das Analytics-Tracking verwendet. | Ganze Zahl (z. B. `7207`); leer; zulässig; `null` zulässig |
| `thumbnail` | Referenz für Miniaturbilder für Recommendations/Analysen. | Dateinamenzeichenfolge oder `null` oder leer |
| `version` | Filter für Produktversion. Wird hauptsächlich für AEM- und Campaign-Blueprints verwendet. | E.g. `Campaign v8`, `Campaign v8 Client Console`; muss mit version.yml übereinstimmen |
| `doc-type` | Inhaltsklassifizierung, die in Repository/Analysen verwendet wird. | `blueprint`, `overview-page`, `Video`, `Tutorial`, `Troubleshooting` (vorzugsweise in Kleinbuchstaben) |
| `feature` | Auf ExL-Seiten werden Themen-Tags als „Themen“ angezeigt. | 1-2 pro Artikel; Title Case; muss feature.yml entsprechen; durch Komma getrennt |
| `feature-set` | Übergeordnete Anwendung für die Funktionsüberprüfung. | Muss mit feature.yml-Werten übereinstimmen |
| `role` | Zielgruppen-Rolle. Wird als „Erstellt für“ auf ExL angezeigt. | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | Benutzererlebnis-Ebene. Wird als „Erstellt für“ auf ExL angezeigt. | `Beginner`, `Intermediate`, `Experienced` (Title Case) |
| `topic` | Produktübergreifende Themen für die Suche/Filterung. | Title case; muss mit topic.yml übereinstimmen; durch Kommata getrennt |
| `type` | Handbuch zur Klassifizierung. | `Documentation` (Standard), `Tutorial`, `Troubleshooting` |
| `last-substantial-update` | Zeigt Inhalte in Widgets für „Neue Funktionen“ an. | Format: `YYYY-MM-DD` |
| `hide` | Schließt die Seite aus allen Suchvorgängen und Empfehlungen aus; setzt außerdem den Index auf „Nein“. | `yes` oder `no` |
| `hidefromtoc` | Entfernt aus der Inhaltsnavigation, aber die Seite ist immer noch über einen direkten Link zugänglich. | `yes` oder `no` |
| `index` | Steuert, ob die Seite in der externen Suche/Sitemap angezeigt wird. | `yes`/`no` oder `y`/`n`; Standard: `no` (indiziert) |
| `recommendations` | Steuert das Widget-Verhalten „Weitere Hilfe zu dieser Funktion“. | `noDisplay` (verhindert die Anzeige von Widgets), `noCatalog` (schließt aus dem Recommendations-Pool aus) |
| `internal` | Markiert die Seite als „Nur intern“ in Adobe. Verhindert das Kennzeichnen interner Links. | `yes` |
| `short-description` | Zusammengefasste Beschreibung für ExL-Landingpages. Verwendet `description`, wenn ausgelassen. | Ein Satz; max. ~20 Wörter |
| `activity` | Klassifizierung der Seitenverwendung. | `understand`, `implement`, `troubleshoot` (Kleinschreibung) |
| `sub-product` | Produkt-Unterkomponente. Arbeiten Sie mit Lösungsteams für gültige Auflistungen. | Kleinbuchstaben; z. B. `search`, `assets`, `sites` |
| `team` | Team-Arbeitsauftrag für Analysen. | E.g. `TM` |
| `landing-page-name` | Breadcrumb-Links zur Landingpage. | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | Breadcrumb-Text für Landingpage-Link. | E.g. `AEM` |
| `auto-video-transcripts` | Aktiviert standardmäßig Videotranskripte. | `true` |
| `badgeType` | Abzeichen für den Inhaltsstatus. | variiert; z. B. `informative`, `positive` |
| `badgePremium` | Premium-Badge-Anzeige. | Gemäß Adobe-Badge-Spezifikation |
| `badgeLabel` | Text der Abzeichenbeschriftung. | Kurze Zeichenfolge |
| `source-git-url` | Source-Repository-URL. | Vollständige GitHub-URL |
| `cloud` | Überschreiben der Cloud-Kategorie auf Artikelebene. | Title case; muss mit cloud.yml übereinstimmen |

---

## TOC.md-Felder

| Feld | Beschreibung | Notizen |
|-------|-------------|-------|
| `user-guide-title` | In ExL-Breadcrumbs und Landingpages angezeigter Guide-Name. | Erforderlich für Inhaltsverzeichnisdateien |
| `breadcrumb-title` | Kürzerer Leitfaden-Name für Breadcrumbs, wenn der Benutzerhandbuch-Titel zu lang ist. | optional |
| `user-guide-description` | Handbuch-Zusammenfassung für ExL-Landingpage. | Ein Satz; max. ~20 Wörter empfohlen |
| `product` | Analytics-Tracking für das Handbuch. Nur ein Wert. | Muss product.yml entsprechen (siehe Gültige Produktwerte) |
| `mini-toc-levels` | Anzahl der Überschriftenebenen, die im Mini-Inhaltsverzeichnis der rechten Navigationsleiste angezeigt werden. | Ganze Zahl 1-6; Standard 2 |
| `role` | Standard-Zielgruppenrolle für den Guide. | Gleiche Werte wie Artikel `role`; durch Komma getrennt |
| `index` | Gibt an, ob der Guide indiziert ist. | `yes`/`no` |

---

## Metadaten.md-Felder auf Repo-Ebene

| Feld | Notizen |
|-------|-------|
| `cloud` | Cloud-Standardkategorie für alle Artikel im Repository |
| `solution` | Standardlösung für alle Artikel |
| `product` | Standardprodukt für das Analytics-Tracking |
| `type` | Standardmäßiger Guide-Typ |
| `doc-type` | Standarddokumenttyp |
| `mini-toc-levels` | Standard-Mini-Inhaltsverzeichnisebenen |
| `git-repo` | GitHub-Repo-URL; aktiviert die Schaltflächen „Diese Seite bearbeiten“ und „Problem protokollieren“ |
| `index` | Standardeinstellung für Index |

---

## Gültige Lösungswerte (unter Berücksichtigung von Groß- und Kleinschreibung)

In diesem Repository verwendete allgemeine Werte:
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

Mehrere Werte: durch Komma getrennt, z. B. `Real-Time Customer Data Platform, Campaign`

---

## Gültige Produktwerte (für `product` Feld - Analytics-Tracking)

Siehe Systemaufforderung für vollständige Liste. Schlüsselwerte:
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

---

## Gültige Rollenwerte

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

---

## Wichtige Validierungsregeln

1. Lassen Sie `exl-id` niemals mit derselben UUID in einer kopierten Datei - löschen Sie sie und lassen Sie das System eine neue zuweisen.
2. Leere/Null-`thumbnail` und `kt` sind zulässig. Dies sind veraltete Felder.
3. `solution` Werte müssen exakt mit der genehmigten Enumeration übereinstimmen - Groß-/Kleinschreibung wird beachtet.
4. `description` Validierung schlägt fehl, wenn fehlt oder null ist. Geben Sie immer einen aussagekräftigen Wert an.
5. `title` Werte werden in Anführungszeichen gesetzt, wenn sie Doppelpunkte, Klammern oder führende Sonderzeichen enthalten.
6. Mehrere `solution` werden innerhalb eines einzelnen Zeichenfolgenwerts durch Kommas getrennt.
7. `product` ist nur ein Einzelwert (für das Analytics-Tracking). Verwenden Sie keine kommagetrennten Werte.
8. Um neue Aufzählungswerte anzufordern, reichen Sie ein UGP JIRA-Ticket mit der Komponente „Inhalts-Tagging“ ein.
