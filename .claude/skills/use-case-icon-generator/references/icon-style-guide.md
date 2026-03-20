---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---
# Stil-Handbuch für Anwendungsfall-Symbole

## Überblick

Anwendungsfall-Symbole dienen in der Katalogtabelle des Anwendungsfalls als visuelle Kennungen. Sie müssen bei einer Bildschirmbreite von 40 Pixel sofort erkennbar sein, während die Qualität bei ihrer nativen Auflösung von 1024 x 1024 beibehalten wird.

## Technische Spezifikationen

| Eigenschaft | Wert |
| --- | --- |
| Dimensionen | 1024 x 1024 Pixel |
| Format | PNG (8-Bit RGB oder RGBA) |
| Dateigröße | 900 KB - 1,4 MB (Standard) |
| Anzeigegröße | 40px Breite in Katalogtabellen |
| Benennung | `icon-{kebab-case-name}.png` |
| Speicherpfad | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## Visuelle Stilrichtlinien

### Komposition
- **Zentrales Thema** - Jedes Symbol sollte eine klare visuelle Metapher für das Anwendungsfallkonzept enthalten
- **Zentrierte Komposition** - Das Hauptfach sollte mit einem ausgeglichenen Leerraum zentriert sein.
- **Kein Text** — Text ist bei 40px unleserlich; verlassen Sie sich ausschließlich auf visuelle Metaphern
- **Keine komplexen Szenen** - Vermeiden Sie Kompositionen mit mehreren Elementen, Hintergründe mit vielen Objekten oder erzählende Szenen
- **Fettformatierung** - Die Form des Symbols sollte selbst als winzige Silhouette erkennbar sein

### Farbe und Ton
- **Saubere, moderne Palette** - Verwenden Sie professionelle, unternehmensgerechte Farben
- **Branchenzusammenhalt** - Symbole innerhalb derselben Branche sollten sich zusammengehörig anfühlen
- **Hoher Kontrast** - Stellen Sie sicher, dass das Hauptmotiv sich deutlich vom Hintergrund abhebt
- **Vermeiden Sie neonfarbene oder übersättigte Farben** - Halten Sie die Palette raffiniert und professionell

### Stil
- **Modern und professionell** — Saubere Linien, polierte Oberfläche
- **Konsistentes Rendern** - Alle Symbole sollten aus demselben Design-System stammen
- **3D oder flach ist akzeptabel** — aber innerhalb einer vertikalen Branche konsistent sein
- **Vermeiden Sie Fotorealismus** - Illustrierter oder gerenderter Stil wird für Konsistenz bevorzugt
- **Keine Markenlogos oder markengeschützten Bilder** — Verwenden Sie allgemeine visuelle Metaphern

### Kleinleserlichkeitsprüfung
Skalieren Sie das Bild vor dem Abschluss mental auf 40 Pixel:
- Kannst du das Hauptsubjekt identifizieren?
- Gibt es einen ausreichenden Kontrast zwischen Vordergrund und Hintergrund?
- Gibt es feine Details, die zu visuellem Rauschen führen?
- Liest die Form deutlich ohne Farbe (bei Barrierefreiheit)?

## Beispiele für visuelle Metaphern nach Branche

### Einzelhandel
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Transaktionsabbruch | Warenkorb mit Artikeln |
| Produkt Recommendations | Geschenkbox oder kuratierte Produkte |
| Crosssell-Upsell | Verbundene Einkaufsartikel |
| Begrüßungsreihe | Willkommenskarte oder Geschenk |
| Preissturz | Preisschild mit Abwärtspfeil |

### Automobil
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Service-Erinnerungen | Schraubenschlüssel oder Servicekalender |
| Fahrzeugkauf | Auto mit Schlüssel |
| Inzahlungnahme | Wagenwechselpfeile |
| vernetztes Fahrzeug | Fahrzeug mit digitaler Verbindung |

### Gesundheitswesen
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Terminerinnerung | Kalender mit Stethoskop |
| Adhärenz | Tablettenflasche oder Rezept |
| vorbeugende Behandlung | Schild mit Gesundheitssymbol |

### Finanzdienstleistungen
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Bleipflege | Wachstumstabelle für Sämlinge |
| Abwanderungsprävention | Schild oder Haltesymbol |
| Lebensphase | Zeitlicher Ablauf der Lebensmeilensteine |

### B2B
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| ABM | Zielgruppe mit Gebäude |
| Lead-Bewertung | Scoring-Messgerät oder Thermometer |
| Vertragsverlängerung | Dokument mit Aktualisierungssymbol |

### Reisen und Gastgewerbe
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Warenkorbabbruch | Koffer oder Buchung |
| Treueprogramm | Treuekarte oder Sternenzeichen |
| Buchungserinnerungen | Kalender mit Flugzeug/Hotel |

### Versicherung
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Erneuerung der Police | Dokument mit Erneuerungspfeilen |
| Schadensbearbeitung | Zwischenablage mit Häkchen |
| Crosssell | Verbundene Richtliniendokumente |

### Medien und Unterhaltung
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Neuer Inhalt | Wiedergabeschaltfläche oder Spotlight |
| Inhaltsempfehlungen | Kuratierte Wiedergabeliste für gestartete Inhalte |
| Abonnementabwanderung | Beschädigte Abonnementkarte |

### Telekommunikation
| Nutzungsszenario | Visuelle Metapher |
| --- | --- |
| Planoptimierung | Signalbalken mit Getriebe |
| Geräte-Upgrade | Telefon mit Pfeil nach oben |
| Abwanderungsprävention | Schild mit Signal |

## Eingabeaufforderungsvorlage für die Bildgenerierung

Verwenden Sie diese Vorlage als Ausgangspunkt, um den Betreff und die Details für jeden Anwendungsfall anzupassen:

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### Tipps zur sofortigen Anpassung

- **Seien Sie konkret zum Thema** - „Ein leuchtend roter Warenkorb mit zwei bunten Geschenkboxen im Inneren“ ist besser als „ein Warenkorb“
- **Hintergrundbehandlung angeben** - „auf einem weichen blauen Farbverlaufshintergrund“ oder „auf einem sauberen weißen Hintergrund mit subtilen Schatten“
- **Erwähnen Sie Beleuchtung** - „weiche Studiobeleuchtung“ oder „sanfter Umgebungsglanz“ hilft, Konsistenz zu erzielen
- **Stilmodifikatoren hinzufügen** - „minimalistisch“, „geometrisch“, „isometrisch“ oder „flaches Design“, um die Ästhetik zu steuern
- **Negative Eingabeaufforderungen einschließen, falls unterstützt** — „kein Text, keine Wasserzeichen, keine Rahmen, keine fotorealistischen Elemente“

## Vorhandenes Symbol Inventar

### Nach Branche

**Einzelhandel (9 Symbole):**
icon-dropped-cart, icon-inventory-priority, icon-price-drop, icon-product-recommendations, icon-category-pages, icon-welcome-series, icon-replenished, icon-post-purchase, icon-cross-sell-upsell

**Automotive (12 Symbole):**
icon-service-reminders, icon-recall-notifications, icon-test-drive, icon-model-launch, icon-trade-in, icon-parts-accessoires, icon-warranty, icon-connected-car, icon-dealer-network, icon-Vehicle-purchase, icon-finance, icon-owner-loyalty

**Finanzdienstleistungen (6 Symbole):**
icon-lead-nurturing, icon-account-dashboard, icon-product-recommendation, icon-churn-prevention, icon-life-stage

**Gesundheitswesen (4 Symbole):**
Icon-Appointment-Reminder, Icon-Post-Visit, Icon-Preventive-Care, Icon-Medication-Adhärence

**Versicherung (3 Symbole):**
icon-policy-renew, icon-claims-process, icon-cross-sell

**Medien und Unterhaltung (3 Symbole):**
icon-new-content, icon-content-recommendations, icon-subscription-churn

**Telekommunikation (3 Symbole):**
icon-plan-optimization, icon-device-upgrade, icon-churn-prevention

**Reisen und Gastgewerbe (12 Symbole):**
icon-cart-cancel, icon-booking-reminders, icon-season-campaigns, icon-personalized-homepage, icon-high-intent, icon-post-booking-upsell, icon-win-back, icon-dynamic-itinerary, icon-newly-browsed, icon-group-booking, icon-exit-intent, icon-loyalty-program

**B2B (11 Symbole):**
icon-webinar-demo, icon-abm, icon-lead-scoring, icon-content-personalization, icon-event-registration, icon-trial-conversion, icon-customer-onboarding, icon-Competitive-replace, icon-case-study, icon-Contract-renewal, icon-upsell-expansion
