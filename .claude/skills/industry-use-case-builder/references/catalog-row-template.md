---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---
# Anwendungsfall - Katalogzeilen-Vorlage

## Zeilenformat

Jede Zeile in der Anwendungsfall-Katalogtabelle folgt genau diesem Format:

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### Zeile ohne Symbol (verwenden, wenn das Symbol noch nicht verfügbar ist)

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## Feldverweis

| Feld | Format | Beispiel |
| --- | --- | --- |
| Branche | kebab-case-Verzeichnisname | Einzelhandel, Finanzdienstleistungen, Reise-Hospitality |
| kebab-name | Anwendungsfall für Kebab-Fall: Name für Symbol | Transaktionsabbruch, Bleipflege |
| ALT-Text | Title Case, short | Transaktionsabbruch, Bleipflege |
| Steueranker | Kebab-Case der ## Überschrift in der Übersicht | dropped-cart-email-recovery |
| Reifegrad + Typ | Badge-Syntax | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## Branchenregisterkarten-Markierungen im Katalog

Die Katalogdatei verwendet diese Registerkartenstruktur:

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## Sortieren innerhalb von Registerkarten

Die Zeilen sind nach Reifegrad sortiert:

1. **Grundlegend** Zeilen zuerst (type=neutral)
2. **Emerging** Zweite Zeilen (type=Informative)
3. **Erweitert** letzten Zeilen (type=Caution)

Fügen Sie innerhalb derselben Fälligkeitsstufe am Ende dieser Gruppe neue Zeilen hinzu.
