---
title: Für Profil konfigurieren
description: Erfahren Sie, wie Sie einen E-Mail-Kanal mit dem Attribut personalEmail.address von AEP für Journey und orchestrierte Kampagnen konfigurieren.
doc-type: article
solution: Experience Platform
exl-id: bb85e0aa-554e-4527-bf91-e7fd4f69ce71
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 8%

---


# Für Profil konfigurieren

## Ziel

In den nächsten Schritten erstellen Sie eine E-Mail-Kanalkonfiguration mit Journey und koordinierten Kampagnen unter Verwendung des `personalEmail.address` AEP-Profilattributs

## Kanalkonfiguration erstellen

1. Navigieren Sie zu **Kanalkonfigurationen** im Menü **Administration → Kanäle → Allgemeine Einstellungen**
2. Klicken Sie auf **Schaltfläche** Konfiguration erstellen“

   ![Kanalkonfiguration erstellen](assets/configure-for-profile-create-configuration-button.png)

3. Legen Sie im Assistenten „Erstellen“ die folgenden Werte fest:
   - **name:** `Profile-Email`
   - **channel:** `Email`
   - **Marketing-Aktion:** `Email Targeting`

![Kanalkonfigurationsdetails](assets/configure-for-profile-channel-configuration-name-values.png)

>[!NOTE]
>
>Wenn Sie E-Mail als Kanal auswählen, wird ein neuer Abschnitt **E-Mail** Einstellungen) angezeigt.

## Konfigurieren des E-Mail-Typs

Legen Sie den **E-Mail-Typ** auf **Marketing** fest

![Email Type](assets/configure-for-profile-set-email-type-marketing.png)

## Subdomain konfigurieren

Wählen Sie aus dem **Subdomain**-Dropdown **email.dep-labs.com**

![Subdomain-Dropdown mit email.dep-labs.com selected](assets/configure-for-profile-select-email-subdomain.png "configure Subdomain")

## Konfigurieren von IP-Pool-Details

Wählen Sie aus der Dropdown **Liste** IP-Pool“ **Marketing**

![Dropdown-Liste „IP-Pool“ mit ](assets/configure-for-profile-select-marketing-ip-pool.png " Details zum Marketing-IP-Pool")

## Abmeldeliste konfigurieren

1. Stellen Sie sicher, dass der Umschalter **aktiviert** für die Abmeldung von einer Liste ist
1. Stellen Sie unter dem Voreinstellungsbereich Abmelden von Liste sicher, dass alle Kontrollkästchen **aktiviert**
1. Stellen Sie unter Linkverwaltung sicher, dass **Adobe verwaltet** ausgewählt ist
1. Stellen Sie für die Einverständnisebene sicher, dass dies auf &quot;**&quot; festgelegt**

![Abmeldung von der Config-Liste](assets/configure-for-profile-configure-list-unsubscribe-settings.png)

## Konfigurieren von Kopfzeilenparametern

1. Legen Sie die folgenden Felder wie folgt fest:
   - **Absendername:** `DEP Labs`
   - **Von E-Mail-Präfix:** `dep`
   - **Antwort an Name:** `DEP Labs Support`
   - **Antwort an E-Mail:** `reply@email.dep-labs.com`
   - **Fehler-E-Mail-Präfix:** `error`

![Kopfzeilenparameter](assets/configure-for-profile-email-header-parameters.png)

## BCC-E-Mail konfigurieren

Leer lassen

>[!NOTE]
>
>Eine Kopie der gesendeten E-Mails kann aufbewahrt werden, indem sie an einen BCC-Posteingang gesendet wird. Gewünschte E-Mail-Adresse eingeben, sodass jede gesendete E-Mail blind an diese BCC-Adresse gesendet wird. Die Domain der BCC-Adresse muss sich von jeder an Adobe delegierten Subdomain unterscheiden. Diese Funktion ist optional. *Verwendung von BCC für E-Mails*

## Konfigurieren von E-Mail-Wiederholungsparametern

Lassen Sie die Standardeinstellungen von **Stunden** auf **84**

## URL-Tracking-Parameter konfigurieren

Mit den Standardeinstellungen verlassen

## Ausführungsdetails

1. Füllen Sie **Abschnitt** aus. Wählen Sie auf der Registerkarte **Journey und** Aktion“ -> **Ausführungsdimension** die Option **Profil** als **Source** aus und klicken Sie auf das Bearbeitungssymbol für **Versandadresse** im Abschnitt **Ausführungsadresse**

   ![Ausführungsdetails](assets/configure-for-profile-execution-details-journey-tab.png)

2. Klicken Sie auf den Ordner **Persönliche E-Mail**, um ihn zu öffnen

   ![Lieferadresse](assets/configure-for-profile-personal-email-folder.png)

3. Klicken Sie im `Address` auf **Kontrollkästchen** und dann auf die Schaltfläche **Auswählen**.

   ![Persönliche E-Mail als Lieferadresse](assets/configure-for-profile-select-address-checkbox-journeys.png)

4. Für **Profil** ist die `personalEmail.address` jetzt als **Versandadresse** im Abschnitt **Ausführungsadresse** konfiguriert

   ![Versandadresse konfiguriert](assets/configure-for-profile-delivery-address-configured-journeys.png)

5. Klicken Sie auf die Registerkarte Orchestrierte Kampagne und aktivieren **das** Aktiviert .

   ![Orchestrierte Kampagnenkonfiguration](assets/configure-for-profile-enable-orchestrated-campaign-tab.png)

6. Konfigurieren Sie unter der Überschrift „Ausführungsdimension“ Folgendes:
   - **Eine Nachricht pro:** `Target Dimension` senden
   - **Profile Target Dimension:** `dep-rel: Customer Account - customer_id`

   ![Target Dimension](assets/configure-for-profile-target-dimension-settings.png)

7. Konfigurieren Sie unter Ausführungsadresse Folgendes:
   - **Source:** `Profile`
   - **Lieferadresse:** `click on the Edit icon`

   ![Ausführungsadresse](assets/configure-for-profile-execution-address-source-profile.png)

8. Suchen Sie nach dem Ordner `Personal Email` und klicken Sie darauf, um ihn zu öffnen

   ![Persönliches E-Mail-Profilattribut](assets/configure-for-profile-search-personal-email-folder.png)

9. Wählen Sie das Feld `Address` im Ordner Persönliche E-Mail aus und klicken Sie auf **Auswählen**

   ![Persönliche E-Mail als Lieferadresse](assets/configure-for-profile-select-address-field-orchestrated.png)

10. Für **Orchestrierte Kampagne** wird **dep-rel: Kundenkonto - customer\_id** als **Profile Target Dimension** für **Ausführungsdimension** mit **Ausführungsadresse** mit einer **Source** von **Profile** und `personalEmail.address` als **Versandadresse** konfiguriert

![Ausführungsdimension konfiguriert](assets/configure-for-profile-orchestrated-execution-dimension-configured.png)

>[!NOTE]
>
>Bei orchestrierten Kampagnen können Sie das Kundenkonto mit einer E-Mail ansprechen, sodass Sie nur (*Nachricht pro Profil)* müssen.  Die verwendete Ausführungsadresse stammt aus dem Profil selbst (d. h., sie wird im AEP-Profil unter dem Attribut **personalEmail.address** gespeichert)


## Überprüfen und speichern

1. Überprüfen Sie erneut alle Details, um sicherzustellen, dass sie übereinstimmen.
1. Scrollen Sie nach oben und klicken Sie auf **Senden**.

>[!NOTE]
>
>Die Verarbeitung der E-Mail-Kanal-Konfiguration dauerte bis zu 2 Stunden!  Oh je!
>
>Fahren Sie mit der nächsten Übung fort, während Sie warten, bis diese Kanalkonfiguration verarbeitet wird.

>[!TIP]
>
>🚀 Sobald der Konfigurationsstatus des E-Mail-Kanals **Aktiv** ist, ist er bereit und kann jetzt direkt in **E-Mail-Aktivitäten** in orchestrierten Kampagnen ausgewählt werden.

## Zusammenfassung

Sie haben jetzt gesehen, wie Sie eine E-Mail-Kanalkonfiguration erstellen, um das AEP-Profilattribut sowohl für Journey- als auch für orchestrierte Kampagnen zu verwenden.
