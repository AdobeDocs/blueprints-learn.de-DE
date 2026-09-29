---
title: Inhaltsimulation
description: Erfahren Sie, wie Sie das Simulationstool von Adobe Journey Optimizer mit Beispielprofildaten verwenden, um personalisierte Felder, Inhaltsvarianten und Fallback-Verhalten zu validieren.
doc-type: article
solution: Experience Platform
exl-id: 3e2b064f-5680-461c-a49e-2a61514e146f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%
---

# Inhaltsimulation

**Zweck:** Validieren von Personalisierung, Bedingungslogik und Inhaltsvarianten mithilfe der Simulations- und Testversand-Tools von Adobe Journey Optimizer.

## Lernziele

Am Ende dieses Moduls haben Sie folgende Möglichkeiten:

1. Hochladen und Verwenden von Testprofildaten für die Simulation.
1. Validieren von personalisierten Feldern und Variantenlogik.
1. Testen Sie das Fallback-Verhalten auf fehlende oder nicht übereinstimmende Daten.

## Einführung

In diesem letzten Modul testen Sie Ihre E-Mail mit **zwei bedingten Varianten** mithilfe des Simulationstools in Adobe Journey Optimizer.
Auf diese Weise können Sie sich eine Vorschau davon ansehen, wie Ihre personalisierte Nachricht verschiedenen Kundinnen und Kunden angezeigt wird, und so die Genauigkeit gewährleisten, bevor Sie die Kampagne starten.

Sie verwenden die Beispieltestprofildatei **sample.csv** aus Ihrem Toolkit.

![Beispiel-Testprofildatei sample.csv aus dem Toolkit](assets/content-simulation-sample-csv-toolkit-file.png)

## Öffnen des Simulationstools

1. Öffnen Sie die abgeschlossene E-Mail.
1. Klicken Sie **Inhalt simulieren**.
1. Wählen **Inhaltsvariante simulieren** aus.

![Klicken auf Inhalt simulieren und wählen Sie Inhaltsvariante simulieren aus](assets/content-simulation-click-simulate-content-variation.png)

Nach einigen Sekunden wird ein Simulationsfenster geöffnet.

## Hochladen der Testprofildaten

1. Öffnen Sie **sample.csv** über den Toolkit-Ordner.
   - **Alex** → Über 40 Jahre alt
   - **Jason** → Unter 40 Jahre alt
2. Klicken Sie **Eingabedaten hochladen**.

   ![Schaltfläche „Eingabedaten hochladen“ im Simulationsbedienfeld](assets/content-simulation-click-upload-input-data.png)

3. Wählen Sie **sample.csv** aus und klicken Sie auf **Weiter**.

![Auswahl von sample.csv und Klicken auf „Weiter“](assets/content-simulation-choose-sample-csv-continue.png)

AJO verarbeitet die Datei und bereitet die Vorschau vor.


## Varianten-Rendering überprüfen

AJO zeigt beide Varianten basierend auf den hochgeladenen Profilen nebeneinander an.

**Erwartete Ergebnisse:**

- **Alex** → sieht **Variante 1** (Alter über 40)

![Alex-Profil-Rendering-Variante 1 für Kinder über 40 ](assets/content-simulation-variant-1-age-above-40.png)

Wenn Sie nach oben scrollen, sehen Sie auch personalisierte Felder mit dem Namen jetzt, wie Sie unten sehen können.

![Personalisiertes Namensfeld für Alex in Variante 1 angezeigt](assets/content-simulation-personalized-name-field-variant-1.png)

- **Jason** → sieht **Variante 2** (Alter unter 40)

![Jason-Profil-Rendering-Variante 2 für Kinder unter 40 ](assets/content-simulation-variant-2-age-below-40.png)

Mit Jasons vollem Namen auch. Wie cool ist das denn!

![Personalisiertes Feld mit vollem Namen wird für Jason in Variante 2 angezeigt](assets/content-simulation-personalized-name-field-variant-2.png)



## Fallback-Verhalten überprüfen

**Fallbacks und Standardeinstellungen:** Sie, dass Ihre E-Mail fehlende Daten oder Szenarien, in denen keine Übereinstimmung erzielt werden kann, ordnungsgemäß verarbeitet. Simulieren Sie beispielsweise ein Profil mit einem leeren Feld „Geburtsjahr“ oder eines, das für kein Zielangebot qualifiziert ist. Die Vorschau sollte entweder einen standardmäßigen Inhaltsbaustein oder einen sinnvollen Platzhalter anstelle von beschädigtem oder leerem Inhalt anzeigen. Wenn Ihre Simulation einen leeren Abschnitt anzeigt, in dem die Inhalte sein sollten, bedeutet dies, dass Sie möglicherweise ein Fallback-Angebot oder Standardtext in Ihrem Design konfigurieren müssen.


## Zusammenfassung

In diesem Modul haben Sie erfolgreich:

- Simulierte personalisierte Inhalte mithilfe von Beispielprofilen
- Validierte Variantenwechsellogik
- Bestätigte personalisierte Felder werden korrekt ausgefüllt

Sie sind nun bereit für das nächste Modul: **Markenausrichtung**,
wo Sie Ihre E-Mail anhand der Richtlinien für die 5G-Marke von Connection mithilfe von KI bewerten werden.
