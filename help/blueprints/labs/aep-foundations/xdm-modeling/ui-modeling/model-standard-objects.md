---
title: Standardobjekte modellieren
description: Erstellen Sie ein Schema „Individuelles Profil“ in der Benutzeroberfläche und fügen Sie Standardfeldgruppen wie „Demografische Details“ und „Einverständnis“ sowie „Voreinstellungen“ hinzu und kürzen Sie sie.
doc-type: article
solution: Experience Platform
exl-id: ea516c0b-3644-483c-a167-0264cc795449
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 1d6ba1444c119437eb8a86d5c4a1050d56d16023
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%
---

# Standardobjekte modellieren

## Zu Schemata navigieren

1. Klicken Sie in der **Leiste auf** Schemata“.

   ![Registerkarte Schemata in der linken Leiste Navigation](assets/model-standard-objects-schemas-tab-left-rail.png "Navigieren Sie mithilfe der linken Leiste zu Schemata")



1. In der oberen Navigation sehen Sie Optionen zum Durchsuchen vorhandener Schemata sowie zum Anzeigen von Feldergruppen und Datentypen, die sich derzeit in der XDM-Registrierung befinden.

![Top-Navigationsoptionen zum Durchsuchen von Schemas, Feldergruppen und Datentypen](assets/model-standard-objects-browse-schemas-top-nav.png "Schemas durchsuchen Top-Navigationsbereich")

>[!NOTE]
>
>Sie sehen, dass es bereits Schemas gibt, die in Ihrer Sandbox vorerstellt wurden. Dazu gehören Schemas, die im Rahmen dieses Bootcamps vorerstellt wurden (sie sind mit dem Präfix `dep` versehen), sowie systemgenerierte Schemas für Adobe Real-Time CDP und Adobe Journey Optimizer.


## Individuelles Profilschema erstellen

1. Klicken Sie zunächst auf **Schema erstellen**

   ![Schaltfläche „Schema erstellen](assets/model-standard-objects-create-schema-button.png "Schema erstellen")



1. Wählen Sie **Manuell**

   ![Wählen Sie die Option „Manuelle Schemaerstellung“](assets/model-standard-objects-select-manual-option.png "Wählen Sie „Manuell“")



1. Wählen Sie **Individuelles Profil**

![Klasse „Individuelles Profil“ auswählen](assets/model-standard-objects-select-individual-profile-class.png "Wählen Sie die Klasse „Individuelles Profil“ aus")


## Benennen des Schemas

Mit klassenbasierten XDM Individual Profile-Schemata können Sie Attribute über eine Person erfassen, die mit dem Profil verknüpft sind. Die Klasse selbst enthält Felder, die nicht bearbeitet werden können, *modifiedByBatchID*, *PersonID* usw.

1. Geben Sie Ihrem Schema einen Namen und eine Beschreibung.
   - **Anzeigename des Schemas** —> *Kundenkonto - \[Ihre Initialen]*
   - **Beschreibung** —> Dieses Schema erfasst Identitäten, Plandaten, demografische Details und Kontaktdaten einer Person.
1. Speichern Sie Ihr Schema mithilfe **Schaltfläche** Beenden“ oben rechts.

![Benennen Sie Ihr Schema, fügen Sie eine Beschreibung hinzu und speichern Sie](assets/model-standard-objects-name-schema-and-save.png "Benennen Sie Ihr Schema, fügen Sie eine Beschreibung hinzu und speichern Sie")

## Hinzufügen der Feldergruppe „Demografische Details“

Es gibt viele Feldergruppen, die als Standard-XDM in Adobe Experience Platform vorhanden sind, sodass Sie sie Ihrem Schema hinzufügen und anpassen können.

1. Klicken Sie auf **+ (Hinzufügen** in der linken Leiste im Abschnitt Feldergruppe .

   ![Schaltfläche „Feldergruppe hinzufügen“ in der linken Leiste](assets/model-standard-objects-add-field-group-button.png "Feldergruppe hinzufügen")



1. Suchen Sie nach **Demografische Details** oder finden Sie sie in der Liste.

   - Wenn Sie die Feldergruppe gefunden haben, klicken Sie auf die Lupe rechts neben der Feldergruppe, um deren Struktur anzuzeigen.  Dieser Schritt ist nützlich, um eine Vorschau dessen anzuzeigen, was Sie Ihrem Schema hinzufügen möchten, ohne es hinzuzufügen.
   - Vorschau nach Überprüfung schließen



   ![Klicken Sie auf das Lupensymbol, um eine Vorschau der Struktur der Feldergruppe anzuzeigen](assets/model-standard-objects-click-magnify-glass-to-preview-field-group-structure.png "Klicken Sie auf das Lupensymbol, um eine Vorschau der Struktur der Feldergruppe anzuzeigen")

   ![Vorschau der Feldergruppenstruktur „Demografische Details“](assets/model-standard-objects-demographic-details-structure-preview.png)



1. **Aktivieren** das Kontrollkästchen neben der Feldergruppe und klicken Sie dann auf die Schaltfläche **Feldergruppen hinzufügen**

![Wählen Sie die Feldergruppe Demografische Details aus, um sie zu Ihrem Schema hinzuzufügen](assets/model-standard-objects-select-demographic-details-field-group.png "Wählen Sie die Feldergruppe Demografische Details aus, um sie zu Ihrem Schema hinzuzufügen")


## Hinzufügen anderer Standardfeldgruppen

Sie müssen Ihrem Schema zusätzliche Standardfeldgruppen hinzufügen. Wiederholen Sie die vorherigen Schritte, um Ihrem Schema die beiden zusätzlichen Feldergruppen hinzuzufügen:

- Persönliche Kontaktdaten
- Details zu Einverständnis und Voreinstellungen

Wenn Sie fertig sind, sieht Ihr Schema wie in der Abbildung unten aus. Klicken Sie unbedingt auf die Schaltfläche **Speichern** und speichern Sie Ihre Arbeit!

![Schema nach dem Hinzufügen von demografischen Details, persönlichen Kontaktdetails und Einverständnis- und Präferenzdetails](assets/model-standard-objects-final-schema-after-adding-field-groups.png "Endgültiges Schema nach dem Speichern von ")

>[!NOTE]
>
>Beachten Sie, dass die ausgewählten und hinzugefügten Feldergruppen jetzt in Ihrem Schema angezeigt und in der linken Leiste angezeigt werden. Beachten Sie, dass nicht alle Felder in jeder hinzugefügten Feldergruppe unbedingt erforderlich sind.  Im nächsten Schritt werden die überflüssigen Felder entfernt.

>[!WARNING]
>
>Denken Sie daran, Ihr Schema zu speichern, bevor Sie fortfahren!


## Anpassen von Standardfeldgruppen

### Feldergruppe „Demografische Details“

Die Feldergruppe Demografische Details enthält viele Felder, aber basierend auf Ihrem Schemadesign aus der LID-Methodik benötigen Sie nur die folgenden Felder:

- person.name.firstName
- person.name.lastName
- person.bornDayAndMonth
- person.BirthYear

Um Felder aus einer Adobe-Standardfeldgruppe zu entfernen, verwenden Sie die Option **Verwandte Felder verwalten**. Mit „Verknüpfte Felder verwalten“ können Sie Standardfelder aus Ihrem Schema entfernen, sodass nur die benötigten Felder verbleiben.

1. Wählen Sie das **Person**-Objekt in Ihrem Schema aus
1. Klicken Sie auf **Verknüpfte Felder verwalten** in der rechten Leiste

   ![Option „Verwandte Felder verwalten“ für das Personenobjekt in der Feldergruppe „Demografische Details](assets/model-standard-objects-manage-related-fields-person-object.png " „Verwandte Felder für das Personenobjekt als Teil der Feldergruppe „Demografische Details“ verwalten")



1. Erweitern Sie das Objekt Person , indem Sie auf den Pfeil links neben Person klicken, und erweitern Sie das Objekt Vollständiger Name , indem Sie auf den Pfeil links neben dem Objekt Name klicken. Nur die folgenden Felder beibehalten:

   - person.name.firstName
   - person.name.lastName
   - person.bornDayAndMonth
   - person.BirthYear

   Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **Bestätigen** in der oberen rechten Ecke.

   ![Dialogfeld „Verknüpfte Felder verwalten“ mit ausgewählten Personenfeldern „Demografische Details](assets/model-standard-objects-demographic-details-person-fields-dialog.png " „Verknüpfte Felder des Personenobjekts „Demografische Details“ verwalten")

   >[!NOTE]
   >
   >Klicken Sie auf das oberste Kontrollkästchen für **Demografische Details**, um die Auswahl aller untergeordneten Objekte automatisch aufzuheben und dann nur die gewünschten Objekte erneut auszuwählen.



1. Wenn Sie fertig sind, sollte das Objekt Person in Ihrem Schema angezeigt werden, wie unten dargestellt. Um Ihr Schema zu speichern, klicken Sie auf die Schaltfläche **Speichern**, wenn alles gut aussieht.

![Endgültige demografische Details Personenobjekt mit nur den erforderlichen Feldern](assets/model-standard-objects-final-demographic-details-person-object.png "Endgültige demografische Details -Feldergruppe mit nur den erforderlichen Feldern")

### Feldergruppe „Einverständnis und Voreinstellungen“

Führen Sie dieselben Schritte wie zuvor aus, aber dieses Mal für die Feldergruppe „Einverständnis“ und „Voreinstellungen“.

1. Klicken Sie in der linken Leiste auf **Name der Feldergruppe „Einverständnis und**&quot;, um die entsprechenden Felder in Ihrem Schema zu markieren.
1. Wählen Sie das **Einverständnis**-Objekt aus und verwenden Sie dann den **Verwandte Felder verwalten**-Prozess, um nicht benötigte Felder aus dem Einverständnisobjekt zu entfernen. Nur die folgenden Felder beibehalten:

- consents.marketing.email.val
- consents.marketing.sms.val

>[!NOTE]
>
>Stellen Sie sicher, dass der Umschalter für **Anzeigenamen für Felder anzeigen** in der oberen rechten Ecke des Schemaarbeitsbereichs deaktiviert ist
>
>![Der Umschalter Anzeigenamen für Felder anzeigen ist deaktiviert](assets/model-standard-objects-show-display-names-toggle-off.png)



Wenn Sie fertig sind, sieht Ihr endgültiges Schema jetzt wie folgt aus. Klicken Sie unbedingt auf **Speichern**, bevor Sie fortfahren.

![Schema nach der Verwaltung verwandter Felder für die Feldergruppe „Einverständnis“ und „Voreinstellungen](assets/model-standard-objects-final-consent-and-preferences-fields.png "Verwaltet verwandter Felder für die Feldergruppe „Einverständnis“ und „Voreinstellungen“")

>[!SUCCESS]
>
>Sie haben nun das Hinzufügen von Standardkomponenten zu Ihrem Schema abgeschlossen. Gut gemacht! Fahren Sie mit dem Erstellen einiger benutzerdefinierter Attribute für Ihr Schema fort.
