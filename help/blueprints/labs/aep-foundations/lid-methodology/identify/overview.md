---
title: Identifizieren
description: Lernen Sie den zweiteiligen Schritt Identifizieren der LID-Methodik kennen - Kennzeichnen der verbleibenden Tabellentypen und Identifizieren wichtiger Identitätsfelder.
doc-type: overview-page
solution: Experience Platform
exl-id: 83657cf0-db35-4d4d-8cfb-1934ff40baca
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%
---

# Identifizieren

## Lernziele

Der **Identifizieren**-Schritt innerhalb der LID-Methodik ist in zwei verschiedene Teile unterteilt:

1. Teil 1: Verbleibende Tabellentypen -> Identifizieren der verbleibenden nicht gekennzeichneten Tabellen und Kennzeichnen des Entnormierungstyps
1. Teil 2 - Schlüsselfelder -> identifiziert die Schlüsselfelder sowohl der primären als auch der unterstützenden Entitäten



Sie lernen, die folgenden Elemente in einem relationalen Modell zu identifizieren, die Sie für das Entwerfen des Echtzeit-Kundenprofils benötigen:

- Bridge-Tabellen (Tabellen, die Viele-zu-viele-Beziehungen verarbeiten)
- Tabellen, die denormalisiert werden müssen
- Primäre Identitäten im Echtzeit-Kundenprofil
- Personenbasierte Identitäten innerhalb der primären Entitätsklassen, die zur eindeutigen Identifizierung einer Person verwendet werden können
- Beziehungskennungen zwischen einzelnen Profil-/Erlebnisereignistabellen und zugehörigen Lookup-Tabellen
- Erforderliche Felder für die Erlebnisereignis-Schemata
- Empfohlene Felder für individuelle Profile und Lookup-Schemata
