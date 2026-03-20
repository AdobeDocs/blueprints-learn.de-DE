---
name: use-case-icon-generator
description: Erzeugen von Symbolspezifikationen und Bildgenerierungsaufforderungen für Anwendungsfallsymbole im Adobe Experience Platform Blueprints-Repository. Verwenden Sie diese Fähigkeit, wenn Sie Symbole für neue branchenspezifische Anwendungsfälle erstellen, wenn der branchenspezifische Anwendungsfall-Builder ein Symbol benötigt oder wenn der Benutzer nach der Erstellung oder Aktualisierung von Anwendungsfall-Symbolen fragt. Gibt eine detaillierte Eingabeaufforderung zur Bildgenerierung aus, die der Benutzer mit Midjourney, DALL-E, Adobe Firefly oder ähnlichen Tools verwenden kann, zusammen mit der korrekten Dateinamen und Platzierung.
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Anwendungsfall-Symbol-Generator

Erzeugen Sie detaillierte Symbolspezifikationen und Eingabeaufforderungen zur Erzeugung von KI-Bildern für Anwendungsfallsymbole im Blueprints-Repository.

## Wann diese Kenntnisse zu verwenden sind

- Erstellen eines neuen Anwendungsfalls, für den ein Symbol erforderlich ist
- Wird von der Fähigkeit des branchenspezifischen Anwendungsfall-Builders aufgerufen, eine Symbolspezifikation zu generieren
- Der Benutzer stellt Fragen zum Erstellen, Aktualisieren oder Ersetzen eines Anwendungsfallsymbols
- Benutzer möchte einen Satz von Symbolen für eine neue vertikale Branche generieren

## Schritt 1: Erfassen Sie die Eingaben

Sammeln Sie die folgenden Informationen vom Benutzer oder von der aufrufenden Fähigkeit:

**Erforderlich:**
- **Name des Anwendungsfalls** - Der für Menschen lesbare Name des Anwendungsfalls (z. B. „Transaktionsabbruch“, „Lead-Bewertung„)
- **Branche vertikal** - Eines von: Automobil, B2B, Finanzdienstleistungen, Gesundheitswesen, Versicherungen, Medien-Entertainment, Einzelhandel, Telekommunikation, Reise-Hospitality
- **Kurzbeschreibung** - 1-2 Sätze, die beschreiben, was der Anwendungsfall tut

**optional:**
- **Bevorzugte visuelle Metapher oder Thema** - Wenn der/die Benutzende eine bestimmte Vorstellung davon hat, was das Symbol darstellen soll

Wenn eine erforderliche Eingabe fehlt, fragen Sie den Benutzer, bevor Sie fortfahren.

## Schritt 2: Stilhandbuch lesen

Lesen Sie die Datei `references/icon-style-guide.md` (relativ zum Verzeichnis dieser Qualifikation), um das vollständige Stilhandbuch zu laden, einschließlich:

- Technische Spezifikationen
- Visuelle Stilrichtlinien
- Beispiele für visuelle Metaphern nach Branche
- Die Eingabeaufforderungsvorlage
- Das vorhandene Symbolinventar

Verwenden Sie das Stilhandbuch, um Konsistenz mit vorhandenen Symbolen sicherzustellen.

## Schritt 3: Erzeugen der Symbolspezifikation

Erstellen Sie alle drei Teile der Symbolspezifikation:

### A. Dateispezifikation

Ermitteln Sie den Dateinamen und den Pfad aus dem Namen des Anwendungsfalls und der Branche:

- **Dateiname:** `icon-{kebab-case-name}.png`
   - Name des Anwendungsfalls in kebab-case konvertieren (Kleinbuchstaben, Bindestriche für Leerzeichen)
   - Beispiele: „Transaktionsabbruch“ wird `icon-abandoned-cart.png`, „Crossselling“ wird `icon-cross-sell-upsell.png`
- **path:** `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- **Abmessungen:** 1024 x 1024 Pixel
- **format:** PNG, 8-Bit RGB oder RGBA
- **Target-Dateigröße:** 900 KB - 1,4 MB

### B. Eingabeaufforderung zur Bildgenerierung

Erstellen Sie eine detaillierte, kopierbereite Eingabeaufforderung für KI-Bildgenerierungs-Tools. Die Eingabeaufforderung muss

1. **Klare visuelle Metapher beschreiben** - Wählen Sie eine einzelne, starke visuelle Metapher, die das Anwendungsfallkonzept sofort vermittelt. Wenn der Benutzer eine bevorzugte Metapher angegeben hat, verwenden Sie sie. Wählen Sie andernfalls eine basierend auf den Beispielen für das Stil-Handbuch und der Beschreibung des Anwendungsfalls aus.

2. **Angeben des künstlerischen Stils** - Schließen Sie diese Stilrichtlinien ein:
   - Sauberer, moderner Icon-Illustrationsstil
   - Professionelle Corporate Design Ästhetik
   - Fette Formen und klare Linien
   - Poliert, gerendert (nicht fotorealistisch)
   - Konsistent mit einem einheitlichen Design-System

3. **Enthalten technische Spezifikationen:**
   - Quadratisches Format, 1024 x 1024 Pixel
   - Einzelnes zentriertes Motiv
   - Vollständiger oder subtiler Verlaufshintergrund
   - Hoher Kontrast zwischen Motiv und Hintergrund

4. **Erzwingen Sie die Lesbarkeit kleiner Dateien:**
   - Kein Text oder Schriftzug jeglicher Art
   - Keine feinen Details oder komplizierten Muster
   - Keine komplexen Hintergründe oder Szenen mit mehreren Elementen
   - Fette Silhouette, die bei 40px deutlich liest
   - Starke Formerkennung auch ohne Farbe

5. **Farbpalette steuern:**
   - Professionelle, unternehmensgerechte Farben
   - Lebhaft, aber raffiniert (kein Neon oder übermäßig gesättigt)
   - Hoher Kontrast für Zugänglichkeit
   - Zusammenhalt mit anderen Symbolen in derselben vertikalen Branche

Strukturieren Sie die Eingabeaufforderung als einen einzigen Absatz, der in ein beliebiges Tool zur Bilderstellung eingefügt werden kann.

### C. Katalog-Referenzausschnitt

Generieren Sie das HTML-Snippet für die Verwendung in der Katalogtabelle:

```
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Alt Text}" width="40">
```

Dabei ist `{Alt Text}` der für Menschen lesbare Name des Anwendungsfalls.

## Schritt 4: Vorhandene Symbole in derselben Branche auflisten

Überprüfen Sie den Abschnitt zum vorhandenen Symbolinventar des Stil-Handbuchs und listen Sie alle aktuellen Symbole für dieselbe Branche auf. Dies hilft Benutzenden:
- Sicherstellen der visuellen Konsistenz beim Generieren des neuen Symbols
- Das Duplizieren eines bereits vorhandenen Symbols vermeiden
- Vorhandene Symbole als Stilbeispiele referenzieren

## Schritt 5: Ausgabe präsentieren

Formatieren Sie die Ausgabe mit diesen Abschnitten deutlich:

---

### Symbolspezifikation: {Use Case Name}

**Branche:** {Industry}

**Dateidetails:**
- Dateiname: `icon-{kebab-case-name}.png`
- Pfad: `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- Abmessungen: 1024 x 1024 Pixel
- Format: PNG (8-Bit RGB/RGBA)

**Eingabeaufforderung zur Bildgenerierung:**

> {Die vollständige, detaillierte Eingabeaufforderung - als Blockquote formatiert, damit sie leicht zu kopieren ist}

**Katalog HTML:**

```html
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Use Case Name}" width="40">
```

**Vorhandene Symbole in {Industry}:**
- {list of existing icon names}

**Nächste Schritte:**
1. Kopieren Sie die obige Eingabeaufforderung zur Bilderstellung.
2. Fügen Sie es in Ihr bevorzugtes Tool zur Bilderzeugung ein (Adobe Firefly, Midjourney, DALL-E oder Ähnliches).
3. Generieren Sie das Bild und wählen Sie das beste Ergebnis aus.
4. Ändern Sie bei Bedarf die Größe/exportieren Sie sie auf genau 1024 x 1024 Pixel.
5. Speichern Sie als `{filename}` im oben gezeigten Pfad.
6. Stellen Sie sicher, dass das Symbol bei einer Displaygröße von 40 Pixel klar und erkennbar aussieht.
7. Verwenden Sie das Snippet Catalog HTML , wenn Sie diesen Anwendungsfall zur Katalogtabelle hinzufügen.

---

## Richtlinien

- **Nie das eigentliche Bild generieren** - Diese Fähigkeit erzeugt nur die Spezifikation und Eingabeaufforderung. Der/die Benutzende muss ein externes Tool zur Bilderzeugung verwenden.
- **Ein Symbol pro Anwendungsfall** - Jeder Anwendungsfall erhält genau ein Symbol.
- **Auf Duplikate prüfen** - Wenn ein Symbol mit demselben oder einem sehr ähnlichen Namen bereits im Inventar vorhanden ist, den Benutzer warnen.
- **Priorisiere Lesbarkeit** — Wenn Sie Zweifel zwischen einer detaillierten Metapher und einer einfachen haben, wählen Sie immer die einfachere Option, die mit 40px gut lesbar ist.
- **Seien Sie bei Eingabeaufforderungen spezifisch** - Vage Eingabeaufforderungen führen zu inkonsistenten Ergebnissen. Konkrete visuelle Details (z. B. „ein Warenkorb mit zwei bunten Kisten im Inneren“ anstelle von „einem Einkaufskonzept„).
- **Vermeiden Sie nach Möglichkeit Klischees** — Versuchen Sie, frische, aber dennoch sofort erkennbare visuelle Metaphern zu finden. Eine Glühbirne für jeden „intelligenten“ Anwendungsfall wiederholt sich.
