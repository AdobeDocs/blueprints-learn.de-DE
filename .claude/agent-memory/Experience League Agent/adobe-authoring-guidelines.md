---
name: Adobe Experience League Authoring Guidelines
description: Vollständige Referenz für Adobe Experience League Markdown-Authoring-Regeln, crawlen im offiziellen Authoring-Handbuch im März 2026.
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Authoring-Richtlinien für Adobe Experience League

Source: https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
Crawlen: 15.03.2026

&#x200B;---

## &#x200B;1. METADATEN/VORDERE MATERIE

### Erforderliche Felder
| Feld | Anforderung | Regeln |
|---|---|---|
| `title` | Erforderlich | Max. 60 Zeichen (Englisch). Title Case. Keine Produktnamen, es sei denn, dies ist aus Gründen der Klarheit erforderlich. System hängt &quot; | ProductName“ automatisch. In Anführungszeichen setzen, wenn es Doppelpunkte oder Klammern enthält. |
| `description` | Erforderlich | Max. 150-160 Zeichen Darf nicht leer/null sein. Konzepte beginnen mit „Mehr erfahren über…“ Aufgaben beginnen mit „Erfahren Sie, wie Sie…“ oder Verben „Imperativ“. |

### Optionale, aber häufig verwendete Felder
| Feld | Gültige Werte | Notizen |
|---|---|---|
| `feature` | Muss mit YAML-Funktionswerten übereinstimmen; Großschreibung des Titels mit Leerzeichen (z. B. „Inhaltsfragment„) | 1-2 pro Artikel; wird in Themen angezeigt |
| `feature-set` | Muss anhand der YAML-Funktion validiert werden | Übergeordnete Anwendung der Funktion |
| `role` | Benutzer, Entwickler, Leader, Admin, Architekt, Datenarchitekt, Dateningenieur | Groß-/Kleinschreibung wird beachtet; wird als „Erstellt für“ angezeigt |
| `level` | Anfänger, Fortgeschrittene, Erfahrene | Die Standardeinstellung ist Anfänger, wenn nicht angegeben |
| `solution` | Muss mit der YAML-Lösung übereinstimmen (z. B. „Campaign, Campaign Standard v7„) | Mehrere Werte zulässig; wird für die Suchfilterung verwendet |
| `topic` | Muss Thema YAML entsprechen; Title Case mit Leerzeichen | Für produktübergreifende Filterung (z. B. „Integrationen„) |
| `type` | Dokumentation, Tutorial, Fehlerbehebung | Repo-Ebene; standardmäßig auf Dokumentation eingestellt |
| `short-description` | Ein Satz, maximal 20 Wörter | Für ExL-Landingpages mit zu langer Beschreibung |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | Badge auf Seitenebene |
| `mini-toc-levels` | 1-6 (Standard 2) | Steuert die Anzeigetiefe der rechten Navigationsleiste |
| `hidefromtoc` | true/false | Schließt aus der linken Navigationsleiste aus, behält jedoch die URL bei |

### Platzierung von Metadaten
- Artikelebene: Anfang der Markdown-Datei als YAML-Vorderseite wichtig
- Inhaltsverzeichnisebene: in Datei TOC.md
- Repo-Ebene: in der Datei metadata.md

### Wichtige Formatierungsregeln
- Werte, die Kommas oder Klammern enthalten, in Anführungszeichen setzen
- Mehrere Werte, durch Kommas getrennt
- Abgleich mit YAML-Definitionen unter Berücksichtigung der Groß- und Kleinschreibung
- Leere/leere Tag-Werte verursachen einen Validierungsfehler

### Verworfene Felder
SEO-Titel, SEO-Beschreibung, Zielgruppe, Schwierigkeit, UUID (aus dem Migrationszeitalter)

&#x200B;---

## &#x200B;2. MARKDOWN-SYNTAX (MIT ADOBE-VERSION)

### Textformatierung
- Fett: `**text**`
- Kursiv: `*text*`
- Fett + Kursiv: `***text***`
- Sonderzeichen mit Escape-Zeichen versehen: Vor dem `# { } [ ] * + - . !` Umgekehrter Schrägstrich `\`
- HTML-Entitäten: `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### Überschriften
- ATX-Stil verwenden (nur `#`, niemals Unterstrichen/Textstil)
- Ein H1 pro Dokument (normalerweise die `title` für den Seitentitel, der mit den Metadaten übereinstimmt)
- Alle nachfolgenden Positionen H2 (`##`) oder darunter
- Leere Zeilen vor und nach Überschriften erforderlich (mit Ausnahme der ersten Überschrift)
- Maximal 69 Zeichen (Englisch) / 120 Zeichen (Lokalisiert)
- Maximal ~5 Wörter bevorzugt
- Groß-/Kleinschreibung für alle Überschriften (nur das erste Wort und die Eigennamen werden großgeschrieben)
- Nur Groß-/Kleinschreibung für das `title` Metadatenfeld
- Kein Satzzeichen am Ende (Fragezeichen für FAQ-Überschriften zulässig)
- Benutzerdefinierte Anker-IDs: `## Title {#custom-id}` - verwenden Sie Bindestriche, keine Punkte
- Keine doppelten Anker-IDs für Überschriften in einem Dokument
- Reservierte Ankernamen vermeiden: Suche, Ergebnisse, Facetten, Paginierung, Sortierung, Abfrage, Suchfeld, Inhalt, Kopfzeile, Fußzeile, Haupt, Navigation, Seitenleiste, Seite, Container, Wrapper
- Folgen Sie jeder Überschrift mit mindestens einem Absatz im Textkörper (platzieren Sie Listen/Tabellen nicht direkt nach einer Überschrift)
- Konzept-Überschriften: Substantiv-/Substantivsätze
- Aufgabenüberschriften: Verben im Imperativ (KEINE Gründe - „Segment erstellen“ statt „Segment erstellen„)
- Parallele Struktur über Überschriftenebenen hinweg

### Listen
- Aufzählungszeichen (unsortiert): `*`, `-` oder `+` - wird in einem Dokument konsistent verwendet
- Bestellt: `1.` für jeden Artikel (automatische Nummerierung)
- Leere Zeilen vor und nach Listen
- Verschachtelte nummerierte Elemente 3 Leerzeichen einrücken; verschachtelte Aufzählungszeichen 2 Leerzeichen
- Satzzeichen: Semikolons/Kommas/Konjunktionen am Ende weglassen; Punkte nur für vollständige Sätze hinzufügen
- Punkte nicht hinzufügen, wenn alle Elemente ≤3 Wörter oder Beschriftungen/Überschriften der Benutzeroberfläche sind

### Relationen
- Extern: `[text](https://url.com)`
- Relativ (gleiche Ebene): `[text](file.md)`
- Stamm-Verwandter: `[text](/help/path/file.md)` — muss mit `/` beginnen
- Deep-Links (gleiche Seite): `[text](#heading-anchor)`
- Cross-Doc Deep-Links: `[text](file.md#heading-id)`
- Neue Registerkarte erzwingen: `[text](url){target="_blank"}`
- Leere URLs: schließen Sie sie in eckige Klammern ein, `<https://example.com>` sie anklickbar zu machen
- Referenzverknüpfungen: Für Verweisstil-Links funktionieren nur absolute Links
- Dieselbe Datei darf nicht über relative Links an mehreren Orten des Inhaltsverzeichnisses gespeichert werden.
- Windows-Benutzer: Konvertieren von umgekehrten Schrägstrichen in Pfade

### Bilder
- Einfach: `![alt text](image.png "hover tooltip")`
- Größe ändern: `{width="300"}`
- Ausrichten: `{align="center"}` oder `{align="right"}`
- Zoombar: `{zoomable="yes"}` oder `{modal="regular"}`
- Maximale Dateigröße: 100 MB (empfohlen unter 5 MB)
- Alternativtext ist für alle Bilder ERFORDERLICH (für SEO und Barrierefreiheit)
- Bilddateinamen: Kleinbuchstaben mit Bindestrichen
- Speichern von Bildern in einem spezifischen Asset-Ordner

### Code-Blöcke
- Inline: Backticks `` `code` ``
- Verwenden Sie für: Dateinamen, URLs, benutzerdefinierte Begriffe, Befehle
- Abgegrenzte Code-Blöcke: Dreifach-Backticks mit Sprachkennung

  ```
  ```javascript

  code here

  ```

  ```

  
  
- Optionen: `{line-numbers="true"}`, `{start-line="7"}`, `{highlight="11-13, 16"}`
- In abgegrenzten Codeblöcken muss immer eine Sprachkennung enthalten sein

### Tabellen
- Für eine Trennzeile sind mindestens 3 Bindestriche pro Spalte erforderlich: `|---|---|---|`
- Ausrichtung: linke `|---|`, mittlere `|:---:|`, rechte `|---:|`
- Literale Pipes ausblenden: `\|` oder `&vert;` verwenden
- HTML-Tabellen zulässig; `<table style="table-layout:auto">` oder `table-layout:fixed` verwenden
- HTML-Tabellenausrichtung: `<td align="left|center|right">`
- Vermeiden Sie Markdown-Syntax in HTML-Tabellen (z. B. `[!NOTE]` funktioniert nicht in HTML-Tabellen)
- Rahmen entfernen: `<tr style="border: 0;">`
- Option „Markdown-Tabellen-Layout“: `{style="table-layout:auto"}` nach Tabelle mit Leerzeilen hinzufügen
- Vermeiden Sie sehr breite/hohe Tabellen aufgrund von Problemen mit der Sichtbarkeit der horizontalen Bildlaufleiste.

&#x200B;---

## &#x200B;3. BESONDERE ADOBE-SYNTAXERWEITERUNGEN

### Hinweise/Ermahnungen

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```

- KRITISCH: Kein Abstand zwischen `>` und `[ !` — `>[!NOTE]` NICHT `> [!NOTE]`
- Leerzeile zwischen `>[!NOTE]` und Textzeile des Textkörpers hinzufügen

### Registerkarten

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### Reduzierbare Abschnitte (Akkordeons)

```
+++Click to expand
Content inside
+++
```

Hinweis: Verschachtelte ausblendbare Abschnitte werden NICHT unterstützt.

### Schattenboxen

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### Videos

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```

`{transcript=true}` für Transkripte hinzufügen.

### Ähnliche Themen

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### Kontextuelle Hilfe

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### Abzeichen (inline)

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```

Typen: `Informative` (blau), `Positive` (grün), `Negative` (rot), `Neutral` (grau), `Caution` (gelb)

### Texthervorhebung (Vorschau)

```html
<span class="preview">highlighted text</span>
```

### Einschlüsse und Snippets
- Gesamte Datei einschließen: `{{$include /help/_includes/legal-blurb.md}}`
- Snippet (keine Überschriften): `{{snippet-id}}`
- Wiederverwendbare Dateien in `help > _includes/` Ordner speichern
- In `help > _includes/snippets.md` gespeicherte Snippets
- Einschlüsse können Überschriften haben; Snippets KÖNNEN NICHT
- Funktioniert nur innerhalb desselben Repositorys (nicht repo-übergreifend)
- Escape-Zeichen `{{` oder `}}` Zeichen in Dateien, die nicht auf Verweise verweisen

### DNL-Tag (nicht lokalisieren)
- `[!DNL ProductName]` - Verpackt Produkt-/Markennamen, die nicht übersetzt werden sollen
- Bei der ersten oder markanten Erwähnung innerhalb einer Seite verwenden

### UICONTROL-Tag
- `[!UICONTROL Button Label]` - Schließt den Text der Benutzeroberflächenelemente ein (Schaltflächen, Menüs, Feldnamen)
- Stellt sicher, dass die Zeichenfolgen der Benutzeroberfläche aus den Produktdatenbanken und nicht aus maschineller Übersetzung abgerufen werden
- Keine Apostrophe, Anführungszeichen oder Satzzeichen innerhalb von UICONTROL-Tags
- Fettformatierung für Benutzeroberflächenelemente verwenden, auf die in Schritten verwiesen wird

### Nicht unterstützte Funktionen
- Aufgabenlisten (Kontrollkästchen)
- Emoji
- Horizontale Regeln
- Verschachtelte ausblendbare Abschnitte

&#x200B;---

## &#x200B;4. DATEIBENENNUNG UND ORDNERSTRUKTUR

### Dateibenennungsregeln
- Dateinamen in Kleinbuchstaben nur mit Bindestrichen
- Keine Großbuchstaben, Unterstriche, Punkte oder Leerzeichen
- Beschreibende, SEO-freundliche Namen (z. B. `calculated-metric-overview.md` nicht `cmo.md`)
- Vermeiden Sie Zahlen in Dateinamen; verwenden Sie beschreibende Wörter
- Vermeiden Sie reservierte/widersprüchliche Namen: `metadata.md`, `search.md`
- Das Umbenennen von Live-Dateien erfordert eine Umleitungsverwaltung (URL-Änderungen)

### Ordnerstruktur
- Verzeichnis-/Ordnernamen wirken sich NICHT auf URLs aus (nur Repo-Namen und Dateinamen wirken sich auf URLs aus)
- TOC.md steuert die Navigationshierarchie, nicht den Speicherort des Git-Ordners
- Speichern von Bildern/Assets in einem spezifischen Asset-Ordner
- Wiederverwendbare Includes gespeichert in `help/_includes/`
- In `help/_includes/snippets.md` gespeicherte Snippets

### TOC.md-Regeln
- Jeder Artikel muss in TOC.md aufgelistet sein, damit er in Experience League gerendert werden kann
- H1-Format: `# Guide Title {#anchor-id}` — Anker generiert Basis-URL-Pfad
- Abschnittsüberschriften müssen Anker-IDs enthalten: `+ Section Name {#section-id}`
- Abschnittsüberschriften (übergeordnete Elemente) können selbst keine Links sein
- Artikel-Links: `+ [Title](path/file.md)`
- Durch das Ändern der Abschnittsanker-IDs werden alle verschachtelten Artikel-URLs geändert (Umleitungen erforderlich)
- Verwenden Sie durchgängig einen einheitlichen Aufzählungsstil (`+`, `*` oder `-`)
- Inhaltsverzeichnismetadaten: `user-guide-description`, optional `breadcrumb-title`
- `mini-toc-levels`: Steuert die Anzeige der rechten Navigationskopfzeile (1-6, Standard 2)

&#x200B;---

## &#x200B;5. INHALTSQUALITÄT UND REDAKTIONELLE STANDARDS

### Stimme und Ton
- Aktive Stimme wird gegenüber passiver bevorzugt
- Präsenz über Zukunftsspannung
- Zweite Person („Sie„) für Anleitungsinhalte
- Sätze unter 35 Wörtern
- Aussagekräftige, präzise Verben - vermeiden Sie schwache Adverbien („sehr“, „extrem„)

### Schritte/Verfahren
- Jeder Schritt ist EIN einziger, knapper Befehl (ein Satz)
- Zusätzliche Informationen erscheinen in der nächsten Zeile (eingerückt unter dem Schritt)
- Beginnen Sie jeden Schritt mit einem Verb des Imperativs
- Begrenzen Sie Prozeduren auf etwa 7 Schritte (max. ~10, bevor Sie in Teilaufgaben einbrechen)
- Platzieren von konzeptionellen Informationen VOR Schritten
- Platzieren von Screenshots NACH dem entsprechenden Schritt
- Wiederholen von Seiten-/Registerkartennamen zur Leserorientierung
- Fett formatierte UICONTROL für UI-Elemente in Schritten

### Terminologie der Benutzeroberfläche
- **Öffnen/Schließen**: Programme und Programme
- **Wechseln zu**: Menüs, Registerkarten oder Benutzeroberflächenspeicherorte
- **Auswählen**: Text, Zellen oder Optionen aus Listen
- **Klicken**: Mausaktionen (außer bei wesentlichen Elementen sollten keine Steuerelementtypen angegeben werden)
- **Dropdown-Menü** (nicht „Dropdown-Liste„)

### Produktnamen
- Den Titeln/Überschriften keinen Produktnamen hinzufügen, es sei denn, die Klarheit erfordert dies
- „das“ vor den Produktnamen auslassen
- &quot;Adobe&quot; bei der ersten Erwähnung auf der Ebene des Handbuchs einschließen (Markenanforderung)
- &quot;Adobe&quot; in sekundären Erwähnungen ablegen, sofern nicht gesetzlich vorgeschrieben
- Verwendung von DNL-Tags für Produktnamen, um Übersetzungsfehler zu vermeiden

### Hervorhebung und Formatierung
- Fett: Benutzeroberflächenelemente und Tastaturaktionen
- Kursiv: Fehlermeldungen, Fremdwörter, Hervorhebung
- Code (Backticks): Dateinamen, URLs, benutzerdefinierte Begriffe
- Keine Anführungszeichen um Benutzeroberflächenelemente (stattdessen UICONTROL-Tag verwenden)

### Großschreibung
- Groß-/Kleinschreibung für Überschriften, Navigation, Unterüberschriften
- Nur Groß-/Kleinschreibung für `title` Metadatenfeld
- Eigennamen werden immer großgeschrieben

&#x200B;---

## &#x200B;6. BEST PRACTICES FÜR SEO

- Ein H1 pro Seite - muss kurz und beschreibend sein und den Benutzern mitteilen, worum es auf der Seite geht
- Hierarchie der sequenziellen Überschriften (h1 → h2 → h3, Ebenen nie überspringen)
- Schlüsselwörter in H1, Textkörper und Metadaten einschließen (nicht das `keywords` Meta-Tag - Google ignoriert es)
- Keyword-Stopfen vermeiden (Intent > Häufigkeit)
- Titel: max. 50-60 Zeichen; System hängt &quot;| Adobe ProductName“ automatisch
- Beschreibung: 150-160 Zeichen; sollte eine call to action sein, keine Inhaltswiederholung
- Allen Bildern beschreibenden Alternativtext hinzufügen
- Videotranskripte einschließen (Suchmaschinen können nur Text lesen)
- Strategisch mit verwandten Seiten verknüpfen (verwaiste Seiten vermeiden)
- Strukturierte Elemente einschließen: nummerierte Listen, Unterüberschriften, Codeblöcke
- Verwenden Sie Tools wie AnswerThePublic, Google Trends, um Keywords zu recherchieren
- Die Inhalte sollten E-E-A-T (Erfahrung, Fachwissen, Autorität, Vertrauenswürdigkeit) nachweisen

&#x200B;---

## &#x200B;7. LOKALISIERUNG

### Maschinelle Übersetzung zuerst
- Englische Quellinhalte generieren lokalisierte Versionen automatisch
- Unterstützte Sprachen: Deutsch, Französisch, Japanisch, Italienisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (vereinfacht), Chinesisch (traditionell), Koreanisch, Niederländisch, Schwedisch

### Schreiben für die Lokalisierung
- Konsistente Terminologie
- Kurze Sätze und aktive Stimme
- Standardmäßige englische Wortreihenfolge (Betreff → Verb → Objekt)
- Verwenden Sie relative Pronomina („that“, „which„)
- Vermeiden Sie: Humor, Idiome, Jargon, regionale Phrasen, Metaphern, unnötige Wörter

### Lokalisierungs-Tags
- `[!UICONTROL Label]` - Stellt sicher, dass die Zeichenfolgen der Benutzeroberfläche aus der Produkt-DB abgerufen werden und nicht maschinell übersetzt werden
- `[!DNL ProductName]` - verhindert die Übersetzung von Produkt-/Markennamen
- Bilder in einem Ordner „nicht lokalisieren“ sind von der Lokalisierung ausgeschlossen

&#x200B;---

## &#x200B;8. CONTENT-TYPEN

- **Handbuch**: Online-Sammlung von Seiten, auf die in einem Inhaltsverzeichnis verwiesen wird; behandelt offizielle Best Practices
- **Tutorial**: Anleitungsinhalte (Video oder Text) für bestimmte Anwendungsfälle, veröffentlicht in Lern-Repos
- **Referenzhandbuch**: Entwickler-APIs/SDKs; normalerweise Tabellenformat; veröffentlicht auf developer.adobe.com
- **Kurs**: Von Experten kuratierte Sammlung von Lektionen, die auf bestimmte Benutzerrollen abzielen
- **Knowledge Base-Artikel**: Kurzer, vorübergehend relevanter Fehlerbehebungsinhalt
- **Landingpage/Startseite**: Separat verwaltet (SCCM)

&#x200B;---

## &#x200B;9. HÄUFIGE ZU VERMEIDENDE VALIDIERUNGSFEHLER

- Fehlende oder leere `title` oder `description` Metadaten
- `description` nicht mit „Weitere Informationen…“ oder „Learn how to…“
- Leerzeichen zwischen `>` und `[ !` in der Callout-Syntax (`> [!NOTE]` statt `>[!NOTE]`)
- Leerzeichen in fett gedruckten Markierungen: `**text **` (Leerzeichen am Ende werden fett umbrochen)
- Markdown-Syntax in HTML-Tabellen (Callouts funktionieren dort z. B. nicht)
- Doppelte Anker-IDs für Überschriften in einem Dokument
- Anker-IDs, die Punkte enthalten (stattdessen Bindestriche verwenden)
- Verwenden reservierter Ankernamen (Suche, Ergebnisse, Kopf- und Fußzeile usw.)
- `role`, `level`, `feature`, `topic` Werte, die nicht mit YAML-Definitionen übereinstimmen
- Gestapelte Überschriften ohne dazwischen liegenden Hauptteiltext
- H1 wird mehr als einmal pro Dokument verwendet
- Übersprungene Überschriftenebenen (z. B. H1 → H3)
- Dateinamen mit Großbuchstaben, Unterstrichen oder Leerzeichen
- Fehlender ALT-Text auf Bildern
- Gerundete Aufgabenüberschriften („Wird erstellt…„) anstelle von „Erstellen…„)
