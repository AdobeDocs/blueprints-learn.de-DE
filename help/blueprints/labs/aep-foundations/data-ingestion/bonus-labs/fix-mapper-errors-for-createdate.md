---
title: Beheben von MAPPER-Fehlern für CreateDate
description: Fehlerbehebung und Behebung eines MAPPER-Fehlers, der durch einen fehlerhaft formatierten createDate-Wert verursacht wurde, der in ein leeres Feld umgewandelt wurde.
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%
---

# Beheben von MAPPER-Fehlern für CreateDate

In dieser Übung müssen Sie herausfinden, wie Sie den MAPPER-Fehler entfernen, den wir im Labor für die Batch-Aufnahme gesehen haben. Der Fehler muss behoben werden, da die Datensätze dennoch aufgenommen werden, obwohl createDate kein erforderliches Feld ist, da das falsch formatierte Datum stattdessen in ein leeres Feld umgewandelt wird.

![createDate-Wert mit einem ungültigen Format, das den MAPPER-Fehler verursacht](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
