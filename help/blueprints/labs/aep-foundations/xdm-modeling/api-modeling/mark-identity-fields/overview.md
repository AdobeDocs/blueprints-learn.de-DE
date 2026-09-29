---
title: Identitätsfelder markieren
description: Erfahren Sie, wie Identitätsdeskriptoren Schemafelder mithilfe der XDM-Schema-Registry-API als primäre oder nicht primäre Identitäten kennzeichnen.
doc-type: overview-page
solution: Experience Platform
exl-id: f6498584-0f4d-4baf-86b5-b00cc78e2ba7
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%
---

# Identitätsfelder markieren

## Identitätsdeskriptoren

Um ein Feld als Identität zu markieren, müssen Sie einen Identitätsdeskriptor in der Schemaregistrierung erstellen. Ein Beispiel für einen Schema-Deskriptor sieht wie folgt aus:

```json
{
  "@type": "xdm:descriptorIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/customerID",
  "xdm:namespace": "customerID",
  "xdm:property": "xdm:code",
  "xdm:isPrimary": true
}
```

- **@type** -> immer auf `xdm:descriptorIdentity` gesetzt
- **xdm\:sourceSchema** -> Die `$id` des Schemas, in dem das Feld vorhanden ist
- **xdm\:sourceVersion** -> immer 1
- **xdm\:sourceProperty** -> Pfad des Felds im Schema
- **xdm\:namespace** -> Der Identity-Namespace-Code, in dem das Feld gespeichert werden soll
- **xdm\:property** -> Immer `xdm:code`
- **xdm\:isPrimary** -> Wenn eine primäre Identität verwendet wird, `true` sie andernfalls `false`


## Ihr Ziel

Erstellen Sie sowohl primäre als auch nicht primäre Identitäten für das Kundenkontenschema. Nachdem Sie die Schritte im nächsten Abschnitt ausgeführt haben, sollte Ihr Schema wie folgt aussehen.

![Kundenkontenschema nach der Erstellung primärer und nicht primärer Identitätsdeskriptoren](assets/overview-schema-with-primary-and-non-primary-identities.png)
