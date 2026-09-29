---
title: Definieren von Beziehungen
description: Erfahren Sie, wie Beziehungsdeskriptoren ein Kundenschema über die API mit einem Lookup-Schema in der XDM-Schemaregistrierung verknüpfen.
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%
---

# Definieren von Beziehungen

## Beziehungsdeskriptoren

Um eine Beziehung von einem Schema zum anderen zu erstellen, müssen Sie einen Beziehungsdeskriptor in der Schemaregistrierung erstellen. Ein Beispiel für einen Schema-Deskriptor sieht wie folgt aus:

Eins-zu-eins-Deskriptor

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

Referenz-Identitätsdeskriptor

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## Ihr Ziel

Erstellen Sie Beziehungsidentitäten für das Kundenkontenschema. Nachdem Sie die Schritte im nächsten Abschnitt ausgeführt haben, sollte Ihr Schema wie folgt aussehen.

![Kundenkontenschema, das die Beziehung und Referenz-Identitätsdeskriptoren anzeigt](assets/overview-schema-with-relationship-identities.png)
