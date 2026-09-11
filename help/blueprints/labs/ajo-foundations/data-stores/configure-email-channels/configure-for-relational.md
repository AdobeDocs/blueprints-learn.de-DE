---
hold: true
title: Konfigurieren von für relationale
description: Erfahren Sie, wie Sie einen E-Mail-Kanal mithilfe des E-Mail-Attributs aus einem relationalen Schema nur für orchestrierte Kampagnen konfigurieren.
doc-type: article
solution: Experience Platform
exl-id: 6f299942-79a6-42c2-8a5b-dd4bccd6aad4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 10%

---


# Konfigurieren von für relationale

## Ziel

In den nächsten Schritten erstellen Sie eine E-Mail-Kanal-Konfiguration, die nur mit orchestrierten Kampagnen verwendet werden kann, indem Sie das Attribut `email` aus dem `dep-rel: Customer Account` Relationales Schema verwenden

## Kanalkonfiguration erstellen

1. Navigieren Sie zu **Kanalkonfigurationen** im Menü **Administration → Kanäle → Allgemeine Einstellungen**
2. Klicken Sie auf **Schaltfläche** Konfiguration erstellen“

![Kanalkonfiguration erstellen](assets/configure-for-profile-create-configuration-button.png)

3. Legen Sie im Assistenten „Erstellen“ die folgenden Werte fest:
   - **name:** `Relational-Email`
   - **channel:** `Email`
   - **Marketing-Aktion:** `Email Targeting`

![Kanalkonfigurationsdetails](assets/configure-for-relational-channel-configuration-name-values.png)

>[!NOTE]
>
>Wenn Sie E-Mail als Kanal auswählen, wird ein neuer Abschnitt E-Mail-Einstellungen angezeigt.





## Konfigurieren des E-Mail-Typs

Legen Sie den **E-Mail-Typ** auf **Marketing** fest

![E-Mail-Einstellungen](assets/configure-for-profile-set-email-type-marketing.png)

## Subdomain konfigurieren

Wählen Sie aus dem **Subdomain**-Dropdown **email.dep-labs.com**

![Subdomain-Dropdown mit email.dep-labs.com selected](assets/configure-for-profile-select-email-subdomain.png "configure Subdomain")

## Konfigurieren von IP-Pool-Details

Wählen Sie aus der Dropdown **Liste** IP-Pool“ **Marketing**

![Dropdown-Liste IP-Pool mit ausgewähltem Marketing](assets/configure-for-profile-select-marketing-ip-pool.png "IP-Pool-Details konfigurieren")

## Abmeldeliste konfigurieren

1. Stellen Sie sicher, dass der Umschalter **aktiviert** für die Abmeldung von einer Liste ist
1. Stellen Sie unter dem Voreinstellungsbereich Abmelden von Liste sicher, dass alle Kontrollkästchen **aktiviert**
1. Stellen Sie unter Linkverwaltung sicher, dass **Adobe verwaltet** ausgewählt ist
1. Stellen Sie für die Einverständnisebene sicher, dass dies auf &quot;**&quot; festgelegt**

![Abmelden von Liste konfigurieren](assets/configure-for-profile-configure-list-unsubscribe-settings.png)

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

1. Aktivieren Sie auf der Registerkarte Orchestrierte Kampagne **Kontrollkästchen** aktiviert .

![Konfigurieren einer orchestrierten Kampagne](assets/configure-for-profile-enable-orchestrated-campaign-tab.png)

2. Konfigurieren Sie unter der Ausführungsdimension Folgendes:
   - **Eine Nachricht pro:** `Target Dimension ` senden
   - **Profile Target Dimension:** `dep-rel: Customer Account - customer_id`

![Ausführungsdimension](assets/configure-for-relational-execution-dimension-target-settings.png)

3. Konfigurieren Sie unter Ausführungsadresse Folgendes:
   - **Source:** `Target Dimension`
   - **Lieferadresse:** `click on the Edit button`

![Target Dimension](assets/configure-for-relational-execution-address-source-target-dimension.png)

4. Klicken Sie im Popup-Fenster auf den Ordner **dep-rel: Kundenkonto**

![Konfigurieren der Versandadresse](assets/configure-for-relational-customer-account-folder.png)

5. Wählen Sie **E-** aus und klicken Sie auf die Schaltfläche **Auswählen**.

![E-Mail als Versandadresse](assets/configure-for-relational-select-email-as-delivery-address.png)

6. Wenn Sie fertig sind, sehen Ihre endgültigen Ausführungsdetails wie im folgenden Screenshot aus

![Ausführungsdimension konfiguriert](assets/configure-for-relational-execution-details-final-result.png)

>[!NOTE]
>
>Bei orchestrierten Kampagnen sollten Sie das Kundenkonto mit einer E-Mail-Adresse ansprechen, sodass Sie nur eine Nachricht pro Target Dimension senden müssen.  Die verwendete Ausführungsadresse stammt aus der Target-Dimension selbst (d. h. was in der Tabelle **dep-rel: Kundenkonto** für **E-Mail** Adresse) gespeichert


## Überprüfen und speichern

1. Überprüfen Sie erneut alle Details, um sicherzustellen, dass sie übereinstimmen.
1. Scrollen Sie nach oben und klicken Sie auf **Absenden**.
1. Wenn Sie fertig sind, sehen Sie zwei E-Mail-Kanal-Konfigurationen, die sich beide wahrscheinlich in einem Status „Verarbeitung läuft“ befinden.

>[!WARNING]
>
>Die Verarbeitung der E-Mail-Kanal-Konfiguration dauerte bis zu 2 Stunden!

## Zusammenfassung

Sie haben jetzt gesehen, wie Sie eine E-Mail-Kanal-Konfiguration erstellen, um das relationale Schemaattribut für orchestrierte Kampagnen zu verwenden.
