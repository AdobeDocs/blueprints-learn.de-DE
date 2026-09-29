---
title: Automatisieren mit APIs
description: Führen Sie eine Postman-Sammlung aus, die die Erstellung von Schemata, Feldergruppen, Identitäts- und Beziehungsdeskriptoren und Datensätzen in einer einzigen Ausführung automatisiert.
doc-type: article
solution: Experience Platform
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%
---

# Automatisieren mit APIs

## Einführung

Um zu sehen, wie Sie Bereitstellungen mithilfe von APIs automatisieren können, führen Sie einen Ordner mit APIs aus, in dem die folgenden Objekte erstellt werden:

- Kundenkonto und Plan \[Lookup] Schema(s)
- Feldergruppen, aus denen die oben genannten Schemata bestehen
- Für das Profil erforderliche Identitätsdeskriptoren
- Beziehung und Referenzdeskriptoren, die für die Erstellung der Beziehungen zwischen Kundenkonto und Plan erforderlich sind \[Lookup]
- Zwei Datensätze, die jedem erstellten Schema entsprechen



## Ausführen des Ordners

1. Navigieren Sie in Postman zum Ordner **Automatisierung mit APIs** im Ordner **XDM Schema Lab**

   ![Automatisierung mit APIs im Ordner „XDM Schema Lab“ in Postman](assets/automate-with-apis-postman-automation-folder.png)



1. Klicken Sie auf den **Automatisierung mit APIs** und klicken Sie im Arbeitsbereich auf die Schaltfläche **Ausführen**

   >[!NOTE]
   >
   >Die Schaltfläche Ausführen befindet sich oben rechts in Ihrem Postman-Arbeitsbereich

   ![Schaltfläche „Ausführen“ oben rechts im Postman-Arbeitsbereich für den Ordner „Automatisierung mit APIs“](assets/automate-with-apis-click-folder-run-button.png "Klicken Sie auf den Ordner „Ausführen“")



1. Es wird ein neues Fenster angezeigt, in dem alle API-Aufrufe im Ordner angezeigt werden. Stellen Sie **Verzögerung** auf **500ms** ein und klicken Sie dann auf die Schaltfläche **Ausführen**.

   ![Das Dialogfeld „Automatisierung ausführen“ mit einer Verzögerung von 500 ms vor dem Klicken auf „Ausführen](assets/automate-with-apis-execute-automation-dialog.png "Automatisierung ausführen“")



1. Sie sehen, dass die API-Aufrufe in der richtigen Reihenfolge ausgeführt werden. Nach Abschluss werden 32 erfolgreiche Tests angezeigt.

   ![Erfolgreicher Automatisierungsdurchgang mit 32 bestanden Tests](assets/automate-with-apis-successful-automation-32-passed-tests.png "Erfolgreiche Automatisierung")



1. Wechseln Sie zur Experience Platform-Benutzeroberfläche. Dort sehen Sie zwei Schemata und zwei Datensätze, die erstellt und für das Profil aktiviert wurden und das Präfix **postman:** aufweisen

![Zwei Schemata, die für das Profil mit dem Postman erstellt und aktiviert wurden: Präfix](assets/automate-with-apis-schemas-created-in-ui.png "Automatisierungsschemata")



![Zwei mit dem Postman erstellte Datensätze: Präfix, das mit den automatisierten Schemata/](assets/automate-with-apis-datasets-created-in-ui.png "-Datensätzen übereinstimmt")

>[!SUCCESS]
>
>Herzlichen Glückwunsch!  Sie haben die Bereitstellung von Identity-Namespaces, Feldergruppen, Schemata, Identitäts-/Beziehungsdeskriptoren automatisiert, ein Schema für ein Profil aktiviert und einen Datensatz mithilfe des Schemas generiert
