---
title: Architekturdiagramm zu Adobe Experience Platform und Programmen
description: Dieses Architekturdiagramm zeigt, wie Adobe Experience Platform mit anderen Programmen und Programm-Services von Adobe Experience Cloud zusammenarbeitet.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 6c4b72159d4ba2a171215678e4e4842956d82745
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# Adobe Experience Platform und Programme

## Architekturdiagramm zu Adobe Experience Platform und Programmen

Dieses Architekturdiagramm zeigt, wie Adobe Experience Platform mit Programmen und Programm-Services von Adobe Experience Cloud zusammenarbeitet.

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform und Programme" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Detailliertes Architekturdiagramm zu Adobe Experience Platform und Programmen

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform und Programme" style="border:1px solid #4a4a4a; width:80%;" />

## Integrationen von Adobe Experience Platform- und Experience Cloud-Anwendungen

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>Anwendung</th>
      <th>Experience Platform zur Anwendung</th>
      <th>Anwendung auf Experience Platform</th>
      <th>Verwandte Blueprints</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Ad Cloud zum Targeting über Audience Manager freigegeben werden.</li>
        </ul>
      </td>
      <td colspan="1">Keine aktuelle Integration</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anonyme Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online-/Offline-Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Aktivierung mit Experience Platform und Anwendungen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>Keine aktuelle Integration</td>
      <td>
        <ul>
          <li>Von Analytics erfasste Daten können an Experience Platform Data Lake und Profilspeicher gesendet werden. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Analytics Data Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Datenflüsse der Experience Platform</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Audience Manager freigegeben werden, um sie für Drittanbieter-Cookie-Ziele zu aktivieren.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Die erfassten und ausgewerteten Zielgruppenzugehörigkeiten können für den Experience Platform Data Lake und den Profilspeicher freigegeben werden. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Audience Manager Source Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anonyme Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online-/Offline-Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Aktivierung mit Experience Platform und Anwendungen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Campaign Classic als Zielgruppe zum Initiieren von Kampagnen freigegeben werden.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Von Campaign erfasste Interaktions- und Kampagnendaten können in Experience Platform als Datenquelle erfasst werden, die über die Echtzeit-Kundendatenplattform und die Analyse über den Customer Journey Analytics- und Experience Platform-Abfragedienst und Data Science Workspace weiter beim Erstellen von Zielgruppen verwendet werden kann.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Batch-Nachrichten</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Campaign Standard als Zielgruppe zum Initiieren von Kampagnen freigegeben werden.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Von Campaign erfasste Interaktions- und Kampagnendaten können in Experience Platform als Datenquelle erfasst werden, die über die Echtzeit-Kundendatenplattform und die Analyse über den Customer Journey Analytics- und Experience Platform-Abfragedienst und Data Science Workspace weiter beim Erstellen von Zielgruppen verwendet werden kann.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">Batch-Nachrichten</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>Daten, die erfasst und in den Experience Platform Data Lake aufgenommen wurden, werden zur Verarbeitung in den Customer Journey Analytics zur Verfügung gestellt. </li>
        </ul>
      </td>
      <td colspan="1">Keine aktuelle Integration verfügbar. Die Möglichkeit, die Ergebnisse der Zielgruppe über Customer Journey Analytics für die Experience Platform freizugeben, liegt auf der Roadmap.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Das Experience Platform-Profil kann serverseitig direkt aufgerufen werden, um personalisierte Erlebnisse zu ermöglichen, die über Experience Manager bereitgestellt werden. Beachten Sie, dass Personalisierungsaktivitäten meist über Experience Manager über die Target-Integration bereitgestellt werden. </li>
        </ul>
      </td>
      <td colspan="1">Über das Experience Platform Web und Mobile SDK werden keine aktuellen Integrations-, Verhaltens- und Interaktionen erfasst, die auf Experience Manager-Sites durchgeführt werden.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online-/Offline-Zielgruppenaktivierung</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Datenereignisse und -profile, die in Experience Platform erfasst werden, werden Journey Optimizer zur Verfügung gestellt, um Journey in Journey Optimizer zu initiieren und zu aktivieren.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Interaktions- und Kampagnendaten, die von Journey Optimizer erzeugt werden, werden in Experience Platform gesammelt und zur weiteren Verwendung beim Erstellen von Zielgruppen über die Echtzeit-Kundendatenplattform und Analysen über Customer Journey Analytics, Experience Platform Query Service und Data Science Workspace verwendet.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=en">Ausgelöste Nachrichten</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">Keine aktuelle Integration</td>
      <td colspan="1">Keine aktuelle Integration</td>
      <td colspan="1">Keine aktuelle Integration</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Marketo als Zielgruppe freigegeben werden, um Marketo-Kampagnen zu initiieren und Marketo-Objekte zu aktualisieren.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Marketo-Konten, Kontakte und Opportunities-Daten sowie von Marketo erstellte Interaction- und Kampagnendaten werden in Experience Platform erfasst und können zur weiteren Verwendung in der Zielgruppenbildung über die B2B-CDP und zur Analyse über Customer Journey Analytics, Experience Platform Query Service und Data Science Workspace verwendet werden. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Marketo Engage Connector</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>B2B Activation - in Entwicklung</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Echtzeit-Kundendatenplattform</td>
      <td colspan="1">
        <ul>
          <li>Daten, die in Experience Platform erfasst und erfasst werden, sind die Datenquelle für die Zusammenstellung von Echtzeit-Kundenprofilen, die die Echtzeit-Kundendatenplattform unterstützen.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Zielgruppen- und Profilmetriken werden an den Experience Platform Data Lake gesendet, um die Dashboards für die Profileinblicke-Berichterstellung zu optimieren.</li>
          <li>Die Zielgruppen- und Profildaten im Data Lake können über Query Service, Data Science Workspace und Customer Journey Analytics für weitere Einblicke verwendet werden.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online-/Offline-Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Aktivierung mit Experience Platform und Anwendungen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Target</td>
      <td colspan="1">
        <ul>
          <li>In der Echtzeit-Kundendatenplattform definierte Zielgruppen können für Target freigegeben und in von Target bereitgestellten Personalisierungs- und Targeting-Erlebnissen verwendet werden. </li>
          <li>Die direkte Integration von Experience Edge mit Target für die Segmentzugehörigkeit in Echtzeit und den Profilattributzugriff finden Sie auf der Roadmap.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Daten, die für Target-Erlebnisse und -Interaktionen erfasst werden, können über das Experience Platform Web SDK für Experience Platform erfasst werden. Diese Daten können beim Erstellen von Zielgruppen über die Echtzeit-Kundendatenplattform und zur Analyse über Customer Journey Analytics,  Experience Platform Query Service und Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online-/Offline-Zielgruppenaktivierung</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Aktivierung mit Experience Platform und Anwendungen</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
