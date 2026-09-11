---
title: Eigenschaft erstellen
description: Erstellen Sie eine Ereignisweiterleitungseigenschaft mit einem Datenelement und einer Regel, die eingehende Erlebnisereignisse an einen Webhook-Endpunkt weiterleitet.
doc-type: article
solution: Experience Platform
exl-id: eabd5f75-7706-4c96-982e-2512509bdc55
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 0%

---


# Eigenschaft erstellen

Normalerweise möchten wir ein Erlebnisereignis an einen Drittanbieter weiterleiten (obwohl dies nicht unbedingt erforderlich ist). Dies wird in der Regel verwendet, wenn eine Ereigniskopie in Echtzeit benötigt wird, um einen Drittanbieter unter bestimmten Umständen zu benachrichtigen (z. B. wenn Google, Meta oder TikTok über einen Kauf informiert werden).

>[!NOTE]
>
>Erinnerung: Eine Eigenschaft enthält alle Erweiterungen, Datenelemente und Regeln, die für die Entscheidung über die Weiterleitung und den Zielort erforderlich sind

1. Klicken Sie in der linken Leiste auf Ereignisweiterleitung .
2. Klicken Sie dann auf Neue Eigenschaft

![Abschnitt „Ereignisweiterleitung“ mit hervorgehobener Schaltfläche „Neue Eigenschaft](assets/create-property-new-property-button.png " Erstellen einer neuen Ereignisweiterleitungseigenschaft")

3. Aktualisieren Sie den Eigenschaftsnamen mithilfe der folgenden Formel: `Event Forward Property SB + [sandbox number]`. Ihr endgültiger Name würde in etwa wie folgt aussehen: **Event Forward Property SB01**

4. Klicken Sie abschließend **Speichern**.

![Eigenschaftsname für die Ereignisweiterleitung, ausgefüllt mit hervorgehobener Schaltfläche „Speichern“](assets/create-property-name-property-form.png)

## Installieren einer Erweiterung

1. Klicken Sie auf die soeben erstellte Ereignisweiterleitungs-Eigenschaft

![Liste der Properties der Ereignisweiterleitung mit der hervorgehobenen neu erstellten Eigenschaft](assets/create-property-open-new-property.png "Öffnen der Ereigniseigenschaft")



2. Es sollte ein Bildschirm wie unten angezeigt werden.  Klicken Sie auf **Erweiterungen**.

![Übersichtsbildschirm der Ereignisweiterleitungs-Eigenschaft mit hervorgehobener Registerkarte „Erweiterungen“](assets/create-property-click-extensions-tab.png)



3. Installieren Sie die Erweiterung Adobe Cloud Connector wie folgt:

4. Klicken Sie in **oberen Navigationsleiste auf** Katalog“.
5. Klicken Sie auf die Karte **Adobe Cloud Connector** .
6. Klicken Sie in der rechten Leiste auf die Schaltfläche **Installieren**

![Erweiterungskatalog mit hervorgehobener Adobe Cloud Connector-Karte und hervorgehobener Schaltfläche „Installieren“](assets/create-property-install-cloud-connector-extension.png)



Nach dem Klicken auf Installieren sollte die Erweiterung unter Installierte Erweiterungen für Ihre Eigenschaft angezeigt werden, wie unten dargestellt

![Liste der installierten Erweiterungen mit der erfolgreich installierten Adobe Cloud Connector-Erweiterung](assets/create-property-extension-installed-confirmation.png "Vollständig installierte Erweiterung")

## Datenelement erstellen

>[!NOTE]
>
>Ein Datenelement verweist auf das eingehende Ereignis und kann es bei Bedarf in mehrere einzelne Komponenten zerlegen

1. Klicken Sie in der linken Leiste auf **Datenelemente**



![Navigation in der linken Leiste mit hervorgehobenem Link „Datenelemente](assets/create-property-navigate-to-data-elements.png "Navigieren zu Datenelementen")



2. Klicken Sie auf **Schaltfläche Neues Datenelement erstellen**

![Seite „Datenelemente“ mit hervorgehobener Schaltfläche „Neues Datenelement erstellen](assets/create-property-create-new-data-element-button.png " „Neues Datenelement erstellen“")



3. Konfigurieren Sie das neue Datenelement mit den folgenden Informationen:

| Elementtyp | Zu konfigurierender Wert |
| ----------------- | ------------------ |
| Name | Datenobjekt |
| Erweiterung | Core |
| Datenelementtyp | Benutzerspezifischer Code |

![Datenelementkonfiguration mit den Feldern „Name“, „Erweiterung“ und „Datenelementtyp“ festgelegt](assets/create-property-data-element-config-step-1.png "Schritt 1 der Datenelementkonfiguration")



4. Klicken Sie auf die Schaltfläche **Editor öffnen**, um den folgenden benutzerdefinierten Code hinzuzufügen:

![Datenelementeinstellungen mit hervorgehobener Schaltfläche „Editor öffnen“ für benutzerdefinierten Code](assets/create-property-open-custom-code-editor.png "Editor öffnen")



5. Fügen Sie dem Editor auf diese Weise benutzerdefinierten Code hinzu und speichern Sie ihn

```none
var xdm = arc?.event || '';
return xdm;
```

![Benutzerdefinierter Code-Editor, der das Skript anzeigt, das das eingehende XDM-Ereignisobjekt zurückgibt](assets/create-property-custom-code-added.png "Benutzerdefinierter Code")

>[!NOTE]
>
>Dadurch wird das gesamte XDM-Objekt erfasst, ohne dass Übersetzungen an der Payload durchgeführt werden.  Bei Bedarf können wir jedes einzelne Element innerhalb des XDM-Objekts (z. B. Seitenname, Kaufbetrag) in ein Datenelement pro Feld analysieren.  Der Grund dafür könnte sein, wenn es eine Umwandlung der Struktur in eine andere Struktur gibt





6. Klicken Sie auf **Speichern**, um Ihr Datenelement zu speichern.

![Datenelement-Editor mit hervorgehobener Schaltfläche „Speichern“](assets/create-property-save-data-element-button.png)



Wenn Sie fertig sind, sollte der folgende Bildschirm angezeigt werden, der bestätigt, dass Ihr Datenelement hinzugefügt wurde:

![Liste der Datenelemente mit dem neu gespeicherten Datenelement, das der Eigenschaft hinzugefügt wurde](assets/create-property-data-element-saved-confirmation.png)


## Regeln erstellen

>[!NOTE]
>
>Eine Regel enthält:
>
>1. Bedingungen für die Weiterleitung
>2. Aktionen, die die Payload transformieren und definieren können, wohin sie gesendet werden soll



1. Klicken Sie in der linken Leiste auf **Regeln**

![Navigation in der linken Leiste mit hervorgehobenem Link „Regeln“](assets/create-property-navigate-to-rules.png)



2. Klicken Sie dann auf **Neue Regel erstellen**

![Seite „Regeln“ mit hervorgehobener Schaltfläche „Neue Regel erstellen“](assets/create-property-new-rule-button.png)



3. Aktualisieren Sie den Regelnamen mithilfe der folgenden Formel: `"EF Rule SB" + [your sandbox number]` (d. h. EF-Regel SB01). Ihre Sandbox-Nummer finden Sie oben rechts im Browser-Fenster, wie unten dargestellt\…

![Browser-Fenster oben rechts mit der im Regelnamen verwendeten Sandbox-Nummer](assets/create-property-sandbox-number-location.png)

4. Klicken Sie abschließend **Speichern**.

>[!NOTE]
>
>Stellen Sie sicher, dass Ihr Regelname dem Formelmuster von `"EF Rule SB" + [sandbox number]` folgt

![Feld für den Regelnamen mit dem EF-Regel-Sandbox-Namensmuster ausgefüllt](assets/create-property-add-rule-name.png "Name zu Regel hinzufügen")



5. Fügen Sie Ihrer Regel eine Aktion hinzu, indem Sie auf das Pluszeichen (+) klicken, um eine neue Aktion hinzuzufügen

![Regeleditor mit hervorgehobenem Pluszeichen, um eine neue Aktion hinzuzufügen](assets/create-property-add-action-button.png "Aktion hinzufügen")

## Webhook-URL abrufen (zur Verwendung in Aktion)

>[!NOTE]
>
>Dieses Labor verwendet hier einen Webhook, mit dem Sie sehen können, ob die Daten bei dem Ziel angekommen sind, an das Sie senden. In einem realen Szenario würden Sie sich stattdessen bei diesem Ziel anmelden und seine Tools verwenden, um zu sehen, was angekommen ist.



1. Öffnen Sie den folgenden Link in einer neuen Registerkarte in Ihrem Browser -> [https://webhook.site](https://webhook.site/)
2. Kopieren Sie die angezeigte eindeutige URL und speichern Sie sie an einem sicheren Ort

![Webhook.site-Seite mit hervorgehobener eindeutiger URL für das Kopieren](assets/create-property-webhooksite-copy-url.png)



3. Konfigurieren Sie Ihre Aktion mit den folgenden Informationen:

| Einstellung | Wert |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Erweiterung | Adobe Cloud Connector |
| Aktionstyp | Abrufaufruf ausführen |
| Methode | Veröffentlichen |
| URL | Verwenden Sie dieselbe Webhook-URL wie beim Einrichten Ihres Streaming-Ziels. Sie können ihn finden, indem Sie eine neue Registerkarte im Browser öffnen und zu Ziele navigieren -> Durchsuchen |
| Textkörper | Roh |
| Hauptteildaten | \{ „Daten“: \{ „Ereignis“: &quot;\{\{Datenobjekt\}\}&quot; } } |

>[!NOTE]
>
>Das hier referenzierte \{\{Datenobjekt\}\} ist das zuvor erstellte Datenelement. Hier bestand die Anforderung des nachgelagerten Systems darin, das Ereignis in einem Datenobjekt in ein Ereignisobjekt einzuschließen. Sie können hier beliebige Formatierungen einfügen.
>
>Wenn wir \{\{Data Object\}\} in mehrere Felder aufgeteilt hätten (z. B. Seitenname, Kauf usw.), konnten wir die JSON-Struktur transformieren, indem wir jedes Feld an der gewünschten Stelle platzierten, was uns mehr Kontrolle über die Zuordnung des Ziels gab.





Wenn Sie fertig sind, überprüfen Sie, ob Ihr Bildschirm ähnlich wie unten aussieht und klicken Sie dann auf **Änderungen beibehalten**

![Mit dem Adobe-Cloud-Connector konfigurierte Regelaktion Abrufeinstellungen und Webhook-URL vornehmen](assets/create-property-configure-action-settings.png "Aktion konfigurieren")



4. Wenn Sie fertig sind, sollte Ihre Aktion zu Ihrer Regel hinzugefügt werden. Klicken Sie auf **Speichern**, um fortzufahren.

![Regeleditor mit der konfigurierten Aktion und hervorgehobener Schaltfläche „Speichern](assets/create-property-save-rule-button.png " Regel speichern")

>[!WARNING]
>
>Wenn Sie ein Erlebnisereignis senden, senden Sie das Ereignis, nicht das Profil oder eines seiner Attribute, einschließlich aller Zielgruppenqualifikationen (auch wenn es eine Edge-Zielgruppe ist).
>
>Dies geschieht zu Geschwindigkeitszwecken.



## Veröffentlichen der Änderungen

1. Klicken Sie in der linken Leiste auf **Veröffentlichungsfluss**

![Navigation in der linken Leiste mit hervorgehobenem Link „Veröffentlichungsfluss](assets/create-property-navigate-to-publishing-flow.png "Navigieren Sie zum Veröffentlichungsfluss")



2. Klicken Sie auf die Schaltfläche **Bibliothek hinzufügen**

![Seite „Publishing-Ablauf“ mit hervorgehobener Schaltfläche „Bibliothek hinzufügen](assets/create-property-add-library-button.png " „Bibliothek hinzufügen“")



3. Konfigurieren Sie die Bibliothek mit den folgenden Informationen:

- Name -> **EF Library**
- Umgebung -> **Entwicklung**
- Klicken Sie auf **Alle geänderten Ressourcen hinzufügen**


Danach sollte der Bildschirm dem folgenden Screenshot ähneln.  Wenn alles gut aussieht, klicken Sie auf die Schaltfläche **Speichern und in Entwicklung erstellen**

![Bibliothekskonfiguration mit Namen, Entwicklungsumgebung und der Schaltfläche „Speichern und in Entwicklung erstellen“](assets/create-property-configure-library-save-and-build.png)



4. Anschließend sollte der Entwicklungs-Build grün angezeigt werden, sodass er einsatzbereit ist

![Veröffentlichungsfluss, der den Status des Entwicklungs-Builds anzeigt, der grün leuchtet und einsatzbereit ist](assets/create-property-development-build-ready.png)
