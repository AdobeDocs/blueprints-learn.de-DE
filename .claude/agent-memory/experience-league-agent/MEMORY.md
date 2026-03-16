---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Experience League Agent-Speicher

## Wichtige Referenzdateien in diesem Repository
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` - Standardmäßige Metadaten auf Repo-Ebene
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` - Metadaten auf Führungsebene
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` - Authoring-Muster für Blueprints

## Metadatenregeln (vollständige Referenz finden Sie unter metadata-fields.md )
- Erforderliche Artikelvorderseite: `title`, `description`, `exl-id`
- Artikel auf der Vorderseite DRINGEND EMPFOHLEN: `solution`
- `exl-id` muss eine gültige UUID sein; beim Kopieren von Dateien löschen/leer lassen (vom System automatisch zugewiesen)
- `description` sollten mit „Erfahren Sie, wie Sie…“ beginnen. oder „Weitere Informationen …“ Gemäß Adobe-Richtlinien
- `title` max. 60 Zeichen für SEO; `[!DNL ProductName]` für Produktnamen im Titel verwenden
- `solution` Werte unterscheiden nach Groß- und Kleinschreibung und müssen mit der genehmigten Enumeration übereinstimmen (siehe metadata-fields.md)
- `thumbnail: null` oder `thumbnail:` (leer) werden beide verwendet. Leer ist akzeptabel
- `kt:` ist ein älteres Feld (JIRA-Nummer des Wissensartikels); wird noch in diesem Repository angezeigt; leer ist zulässig
- Verwenden von Inhaltsverzeichnisdateien: `user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`
- `metadata.md` auf Repo-Ebene verwendet: `cloud`, `solution`, `product`, `type`, `doc-type`, `mini-toc-levels`, `git-repo`, `index`

## Allgemeine Muster in diesem Repository (blueprints-learn.de)
- Die meisten Blueprint-Dateien verfügen über: `title`, `description`, `solution`, `exl-id`
- Einige ältere Dateien umfassen auch: `kt`, `thumbnail`
- Einige Dateien verwenden `version` (Campaign v8-Blueprints)
- `doc-type: overview-page` für Übersichtsseiten
- `solution` enthält oft mehrere kommagetrennte Werte: z. B. `Real-Time Customer Data Platform, Campaign`
- Dateien OHNE `solution` bestehen die Validierung weiterhin, wenn `exl-id` vorhanden ist

## In diesem Repository verwendete Adobe-Markdown-Erweiterungen
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- `>[!BEGINTABS]`/`>[!TAB Name]`/`>[!ENDTABS]` für Inhalt mit Registerkarten
- `[!DNL ProductName]` - Tags für Produktnamen nicht lokalisieren
- `[!UICONTROL Label]` - Benutzeroberflächen-Steuerelementverweise
- `{zoomable="yes"}` — Bild-Zoom-Attribut
- `{width="1000"}` — Attribut für Bildbreite
- `{target="_blank"}` — Ziel des externen Links

## Detaillierte Verweise
- Vollständige Metadatenfeld-Referenz: `metadata-fields.md`
- Authoring-Handbuch crawlen: https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home (Februar 2026)
