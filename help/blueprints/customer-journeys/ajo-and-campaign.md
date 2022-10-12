---
title: 'Blueprint: Journey Optimizer mit Adobe Campaign'
description: Zeigt, wie Adobe Journey Optimizer mit Adobe Campaign verwendet werden kann, um nativ mithilfe des Echtzeit-Messaging-Servers in Campaign Nachrichten zu versenden
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 92%

---

# Journey Optimizer mit Adobe Campaign

Zeigt, wie Adobe Journey Optimizer mit Adobe Campaign verwendet werden kann, um nativ mithilfe des Echtzeit-Messaging-Servers in Campaign Nachrichten zu versenden.

<br>

## Architektur

<img src="assets/ajo-campaign-architecture.svg" alt="Referenzarchitektur für die Blueprint „Journey Optimizer“" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>Die Verwendung sowohl von Journey Optimizer als auch von Campaign zum unabhängigen Versand von Nachrichten ist möglich, allerdings müssen dabei einige technische Überlegungen angestellt werden. Wenn Sie diesen Ansatz verfolgen möchten, besprechen Sie ihn mit Ihrem Pre-Sales Enterprise Architect, um sicherzustellen, dass Sie die Voraussetzungen für die Implementierung verstehen.

<br>

## Voraussetzungen

### Adobe Experience Platform

* Schemas und Datensätze müssen im System konfiguriert werden, bevor Sie Journey Optimizer-Datenquellen konfigurieren können.
* Fügen Sie für Schemas, die auf der Klasse „Erlebnisereignis“ basieren, die Feldgruppe „Orchestrierungsereignis-ID“ hinzu, wenn ein Ereignis ausgelöst werden soll, das kein regelbasiertes Ereignis ist.
* Fügen Sie für Schemas, die auf der Klasse „Individuelles Profil“ basieren, die Feldgruppe „Profil-Testdetails“ hinzu, um die Testprofile für die Verwendung mit Journey Optimizer laden zu können.
* Journey Optimizer und Campaign werden in derselben IMS-Organisation bereitgestellt.

### Campaign v7/v8 oder Campaign Standard

* Ausführungsinstanz des Echtzeit-Messaging-Service (d. h. Message Center) muss von Adobe Managed Cloud Services gehostet werden.
* Sämtliches Nachrichten-Authoring erfolgt direkt in der Campaign-Instanz.

<br>

## Leitlinien

[Produkt-Link zu Journey Optimizer-Leitlinien](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=de)

### Weitere Leitlinien für Journey Optimizer

* Die Begrenzung ist jetzt über eine API möglich. So wird sichergestellt, dass das Zielsystem nicht so überlastet wird, dass ein Fehler auftritt. Dies bedeutet, dass Nachrichten, die die Begrenzung überschreiten, vollständig ignoriert und niemals gesendet werden. Drosselung wird nicht unterstützt.
   * Max. Verbindungen: Maximale Zahl der http/s-Verbindungen, die ein Ziel bewältigen kann
   * Max. Aufrufanzahl: Maximale Aufrufzahl, die im Parameter periodInMs erfolgen kann
   * periodInMs: Zeit in Millisekunden
* Von der Segmentzugehörigkeit initiierte Journeys können in zwei Modi operieren:
   * Batch-Segmente (alle 24 Stunden aktualisiert)
   * Streaming-Segmente (Qualifikation &lt;5 Minuten)
* Batch-Segmente: Stellen Sie sicher, dass Sie das tägliche Volumen an qualifizierten Nutzern verstehen und dass das Zielsystem den maximalen Durchsatz pro Journey und für sämtliche Journeys bewältigen kann
* Streaming-Segmente: Stellen Sie sicher, dass der erste Strom von Profilqualifikationen neben täglichen Streaming-Volumen pro Journey und für sämtliche Journeys bewältigt werden kann
* Entscheidungs-Management wird nicht unterstützt
* Unternehmens-Events werden nicht unterstützt
* Ausgehende Integrationen mit Drittanbietersystemen
   * Keine Unterstützung für einzelne statische IPs, da wir eine Mehrmandanten-Infrastruktur verwenden (alle Daten-Center-IPs müssen aufgelistet sein)
   * Nur die POST- und die PUT-Methode werden für benutzerdefinierte Aktionen unterstützt
   * Authentifizierungsunterstützung: Token | Passwort | OAuth2
* Keine Möglichkeit, einzelne Komponenten von Adobe Experience Platform oder Journey Optimizer zu packen und zwischen verschiedenen Sandboxes zu verschieben. Muss in neuen Umgebungen erneut implementiert werden

<br>

### Campaign-Integrationen

Hinweise zur Integration in Ihre spezifische Version von Adobe Campaign und Adobe Journey Optimizer finden Sie im entsprechenden Handbuch für jede Adobe Campaign-Version.

* [Adobe Journey Optimizer und Campaign v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer &amp; Campaign v8](ajo-and-campaign-v8.md)