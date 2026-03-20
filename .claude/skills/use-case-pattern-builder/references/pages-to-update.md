---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---
# Beim Hinzufügen eines Anwendungsfallmusters zu aktualisierende Seiten

Wenn ein neues Anwendungsfallmuster erstellt wird, müssen die folgenden Seiten aktualisiert werden, um sicherzustellen, dass das Muster auffindbar und korrekt verknüpft ist.

## Erforderliche Aktualisierungen

### &#x200B;1. Inhaltsverzeichnis.md
- **Datei:** `/help/blueprints/TOC.md`
- **Aktion:** Fügen Sie einen neuen Eintrag unter dem richtigen Kategorieabschnitt hinzu.
- **format:** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **Standort nach Kategorie:**
   - Zielgruppenerstellung und Aktivierung: nach Zeile ~47 (nach vorhandenen Einträgen in diesem Abschnitt)
   - Personalization: nach Zeile ~52
   - Kampagnenverwaltung und Orchestrierung: nach Zeile ~58
   - Analyse: nach Zeile ~61
   - Konversationserlebnis: nach Zeile ~63

#### Zuordnung von Kategorie zu Inhaltsverzeichnis

| Kategorie-Slug | Inhaltsverzeichnis-Abschnittsüberschrift | Anker |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### Einrückungsregeln

- Kategorieüberschriften verwenden zwei Leerzeichen + `+` (z. B. `  + Personalization{#personalization-patterns}`)
- Mustereinträge verwenden vier Leerzeichen + `+` (z. B. `    + [Pattern Title](path)`)

### &#x200B;2. Übersicht über Anwendungsfallmuster
- **Datei:** `/help/blueprints/use-case-patterns/overview.md`
- **Aktion:** Fügen Sie der richtigen Kategorietabelle eine neue Zeile hinzu.
- **format:** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- **Kategorien im Überblick:**
   - Zielgruppenerstellung und -aktivierung (Zeile ~18)
   - Personalization (Zeile ~29)
   - Kampagnenverwaltung und Orchestrierung (Zeile ~40)
   - Analyse (Zeile ~52)
   - Gesprächserlebnis (Zeile ~61)

#### Beispiel für ein Zeilenformat

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## Validierungs-Checkliste

- [ Markdown-Datei für ]-Muster im richtigen Kategorieverzeichnis erstellt
- [ ] Frontmatter umfasst Titel, Beschreibung, Lösung und exl-id
- [ ] Eintrag TOC.md unter der richtigen Kategorie hinzugefügt
- [ ] Tabellenzeile Overview.md unter der richtigen Kategorie hinzugefügt
- [ ] Alle Links zu Geschäftszielen verweisen auf vorhandene Dateien
- [ ] Datei verwendet die Namenskonvention für Kebab-Groß-/Kleinschreibung
- [ ] Alle Experience League-Links sind gültige URLs
- [ ] Adobe-Produktnamen verwenden `[!DNL ...]` Syntax
- [ ] Funktionskette verwendet ` > ` Trennzeichenformat
- [ ] Musterdatei enthält alle erforderlichen Abschnitte (siehe pattern-template.md)
