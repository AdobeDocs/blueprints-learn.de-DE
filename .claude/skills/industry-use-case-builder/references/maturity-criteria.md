---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---
# Kriterien für die Reifegradbewertung des Anwendungsfalls

## Reifegrad

### grundlegend

**BADGE:** `[!BADGE Foundational]{type=Neutral}`

Ein Anwendungsfall ist **Grundlegend** wenn er:

- Wird einem einstufigen oder ereignisausgelösten Muster zugeordnet (ereignisausgelöstes Messaging, Aktivierung von Batch-ausgehenden Nachrichten)
- Hat einfache Datenanforderungen (einzelner Ereignistyp, Standardprofilattribute)
- Erfordert minimale oder keine KI-/ML-Funktionen
- Verwendet einen Standardkanal-Versand (E-Mail, SMS, Push) ohne komplexe Orchestrierung
- Verfügt über etablierte Implementierungsmuster mit klaren Best Practices
- Erfordert weniger Systemintegrationen (normalerweise 1-2 Datenquellen)

**Typische Muster:** Ereignisausgelöstes Messaging, Aktivierung ausgehender Nachrichten im Batch

**Beispiele:** Wiederherstellung bei Transaktionsabbruch, Terminerinnerungen, Service-Benachrichtigungen, Warnhinweise bei Preisrückgängen, Erinnerungen an Rechnungszahlungen

### aufstrebend

**BADGE:** `[!BADGE Emerging]{type=Informative}`

Ein Anwendungsfall ist **Emerging** wenn:

- Ordnet einem mehrstufigen oder Personalisierungsmuster zu (mehrstufige orchestrierte Journey, Personalization für bekannte Besucher, Verhaltensempfehlungen, Personalization für anonyme Besucher)
- Erfordert Erfassung und Analyse von Verhaltensdaten
- Verwendet Empfehlungsmodelle oder die Auflösung bekannter Besucherprofile
- Beinhaltet Multi-Touch-Pflegesequenzen mit Verzweigungslogik
- Ist mäßig komplex in die Integration (2-4 Datenquellen)
- Zielgruppenaktivierung oder segmentbasiertes Targeting erforderlich machen

**Typische Muster:** Mehrstufige orchestrierte Journey, Web-/App-Personalization für bekannte Besucher, Verhaltensempfehlungen, Web-Personalization für anonyme Besucher, B2B-Audience Activation

**Beispiele:** Begrüßungsserie, Kampagnen zur Einhaltung von Medikamenten, personalisierte Konto-Dashboards, Lead-Bewertung, Inhaltsempfehlungen

### Erweitert

**BADGE:** `[!BADGE Advanced]{type=Caution}`

Ein Anwendungsfall ist **Erweitert** wenn er:

- Ordnet einem Entscheidungs- oder kanalübergreifenden Orchestrierungsmuster zu (Cross-Channel-Journey mit Decisioning, Offer Decisioning)
- Erfordert KI-gestützte Prognose oder Tendenzauswertung
- Gleichzeitige Verwendung zentralisierter Entscheidungslogik über mehrere Kanäle hinweg
- Komplexe Orchestrierung mit Echtzeit-Entscheidungsfindung an mehreren Journey-Punkten
- Hohe Integrationskomplexität (über 4 Datenquellen, Echtzeit-Daten-Feeds)
- Erfordert ausgefeilte Geschäftsregeln, Prioritätsverwaltung und Häufigkeitssteuerung

**Typische Muster:** Cross-Channel-Journey mit Decisioning, Offer Decisioning

**Beispiele:** mit KI-Bewertung, Produktempfehlungen für die gesamte Lebensdauer, Crosssell-Optimierung, Personalisierung von Treueprogrammen und exklusiven VIP-Angeboten

## Bewertungs-Workflow

1. Ermitteln, welchem Anwendungsfallmuster der Anwendungsfall zugeordnet ist
2. Prüfen Sie die obige Liste „Typische Muster“ auf eine schnelle Übereinstimmung.
3. Wenn das Muster nicht eindeutig auf Reife hinweist, bewerten Sie die Datenkomplexität, die KI/ML-Anforderungen und den Integrationsbereich
4. Übermitteln Sie die Bewertung dem Benutzer mit einer Begründung: „Aufgrund der Musterzuordnung ({pattern}) und der {key factors} würde ich dies {reasoning} als {level} klassifizieren.“
5. Der Benutzer muss den Vorgang bestätigen oder überschreiben, bevor er fortfährt
