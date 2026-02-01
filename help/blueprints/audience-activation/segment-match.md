---
title: Zielgruppen-Collaboration mit Segment Match
description: Erfahren Sie mehr zu [!UICONTROL Segment Match] in Adobe Experience Platform (AEP). [!UICONTROL Segment Match] ist ein Service zur gemeinsamen Nutzung von Daten, mit dem Sie Segmentdaten auf der Basis gemeinsamer Branchenkennungen auf sichere, kontrollierte und datenschutzkonforme Weise austauschen können.
solution: Experience Platform
exl-id: d7e6d555-56aa-4818-8218-b87f6286a75e
source-git-commit: 88a15765c0a998d49c19d9853ad0c44d6e3bfaa1
workflow-type: tm+mt
source-wordcount: '2123'
ht-degree: 80%

---

# Zielgruppen-Collaboration mit Segment Match-Blueprint

Segment Match ermöglicht es Partnermarken, Zielgruppen über ihre Experience Platform-Umgebungen freizugeben. Der Schlüssel zu erfolgreicher Geschäftstätigkeit ist die Pflege von Kundenbeziehungen mithilfe von Daten, die über den direkten Kontakt mit Verbrauchern und Verbraucherinnen erfasst werden. Marketer haben nun die Möglichkeit, durch innovative Systeme zur Verwaltung von Daten-Governance, Berechtigungen und Einstellungen und durch die Zusammenarbeit mit Partnern eine präzisere Auswahl ihrer durch First-Party-Daten authentifizierten Zielgruppen zu treffen.

[!UICONTROL Segment Match] ist ein Service zur gemeinsamen Nutzung von Daten, mit dem Kunden von Experience Platform (AEP) (als _Partner_ bezeichnet) Segmentdaten auf der Grundlage gemeinsamer Branchenkennungen auf sichere, kontrollierte und datenschutzkonforme Weise austauschen können.

Dieser Service ermöglicht es Kunden, übereinstimmende IDs sicher und neutral zu identifizieren, ohne ihre gesamte Datenbank offenlegen zu müssen. Partner erhalten für übereinstimmende IDs nur zuvor festgelegte Attribute (Segmentname), was eine schnelle und einfache gemeinsame Nutzung ermöglicht, die kontrolliert ist und auf aktivem Einverständnis basiert.

[!UICONTROL Segment Match] setzt auf dem Datenverwaltungs- und Einverständnis-Framework von AEP auf. Segment Match ist für alle B2C- und B2P-Kunden von Real-time Customer Data Platform verfügbar. Die Hauptfunktionen von [!UICONTROL [!UICONTROL Segment Match]]:

* Segmentfreigabe für Profile, die sich überschneiden und ihr Einverständnis gegeben haben
* Berichte vor der Datenfreigabe mit Informationen zum geschätzten Volumen der sich überschneidenden Identitäten
* Vollständig integrierte DULE-Richtlinie und Berechtigungsdurchsetzung
* Framework für die Verwaltung des Einverständnisses zur Datenfreigabe
* Daten-Feeds zum Organisieren von Segmenten und Partnern

## Programme

Zwischen Marke und Publisher:

Der „Publisher-Anwendungsfall“ ist am stärksten vom Wegfall von Third-Party-Cookies und ID-Daten für mobile Werbung betroffen. Dieser Anwendungsfall hat erhebliche Auswirkungen auf die Medien- und Unterhaltungsbranche, deren Geschäftsmodell auf dem Verkauf von Werbung basiert. [!UICONTROL Segment Match] bietet Publishern, die über große Mengen an First-Party-Zielgruppendaten verfügen und direkt mit Advertisern zusammenarbeiten möchten, eine neue Umsatzchance. Advertiser wiederum können direkt mit Publishern zusammenarbeiten und in granularen Targeting- oder Kundengewinnungskampagnen Werbung für übereinstimmende Zielgruppen auf Publisher-Properties schalten.

### Zwischen Marke und Marke:

Customer Journeys verlaufen nie linear. Beispiel: Eine Person ist loyale Kundin einer Fluggesellschaft und eines Kreditkartenunternehmens. Durch Verwendung von [!UICONTROL Segment Match] können die Fluggesellschaft und das Kreditkartenunternehmen nun eine Datenpartnerschaft eingehen, um sich überschneidende Zielgruppen zu ermitteln und anschließend den loyalen Kunden und Kundinnen eines jeden Unternehmens maßgeschneiderte Angebote mit personalisierten Erlebnissen zu unterbreiten.

### Zwischen Geschäftseinheit und Geschäftseinheit:

Für global tätige multinationale Unternehmen ist es oft schwierig, die gemeinsame Nutzung von Daten zwischen unabhängig operierenden Geschäftseinheiten zu gewährleisten. Das Zusammenführen von Daten in eine gemeinsame Sandbox ist u. U. aufgrund unterschiedlicher Datenschutzrichtlinien, Akquisitionen oder Berechtigungen in den diversen Geschäftseinheiten nicht möglich.

[!UICONTROL Segment Match] hilft separaten Marketing-Teams in großen Unternehmen, effizienter zusammenzuarbeiten und gleichzeitig unabhängig zu agieren.

## Architektur

![Die Architektur von Segment Match](assets/architecture-segment-match.png){zoomable="yes"}

[!UICONTROL Segment Match] ist kein Daten-Marketplace, auf dem Daten gekauft werden können. Vielmehr handelt es sich dabei um eine AEP-Funktion, die ausgewählten Partnern den Austausch von First-Party-Daten ermöglicht. Steuerwerkzeuge sorgen dabei für die Einhaltung des Datenschutzes und die Prüfung des Einverständnisses. [!UICONTROL Segment Match] ermöglicht die Verbesserung der Kundenbeziehungen und die Steigerung des Geschäftswachstums. Dieser Service ist insbesondere dort von Vorteil, wo bereits Marken- oder Partnerbeziehungen bestehen. [!UICONTROL Segment Match] ist einfach zu verwalten, skalierbar und ermöglicht es Administratoren und Administratorinnen, Segmente kontrolliert per Opt-in freizugeben.

[!UICONTROL Segment Match] bietet Folgendes:

* Den sicheren Austausch von Segmentzugehörigkeitsdaten zwischen Unternehmen mithilfe von standardmäßigen personenbezogenen Kennungen, wie Hash-E-Mail-Adresse oder Telefonnummer
* Eine Benutzeroberfläche zur Zielgruppenfreigabe und Workflows mit Benachrichtigungen
* Die Bereitstellung von Schätzungen zu den sich überschneidenden Segmenten vor der Segmentfreigabe
* Partner-Einrichtung im Self-Service
* Überschneidungen bei ausgewählten standardisierten Namespaces (Hash-E-Mail, Hash-Telefon, ECID, IDFA, GAID)
* Durchsetzung des Datenfreigabe-Einverständnisses
* Verwaltung des Lebenszyklus freigegebener Zielgruppen
* DULE-Durchsetzung im Freigabe-Workflow
* Tägliche Batch-Aktualisierungen

[!UICONTROL Segment Match] ermöglicht die Erstellung eines vielschichtigen Kundenerlebnisses. Die unterstützten dauerhaften Kennungen sind Hash-E-Mails, Hash-Telefonnummern und Kennungen wie ECID, IDFA und GAID. Kunden können Feeds erstellen, mit denen Zielgruppendaten zwischen Marken-Sandboxes verglichen und verschoben werden. Dabei stehen für Werbe- und Marketing-Aktivierungen effektive Funktionen zur Datenverwaltung, zur Gewährleistung der Transparenz und zur Rücknahme der Identitäten zur Verfügung.

## Voraussetzungen

Die Voraussetzungen für die Verwendung von [!UICONTROL Segment Match] sind:

* Aktive RT-CDP-Lizenz
* Die unterstützten standardmäßigen Hash-Kennungen sind SHA256-Hash-E-Mail, Hash-Telefon, ECID, Apple IDFA und GAID
* Datenschutz-Framework- und Einverständnisstrategie
* Datenfreigabevereinbarungen zwischen Kunden

## Sicherheit

### Rollenbasierte Zugriffskontrolle

Der [!UICONTROL Segment Match]-Fluss zur Verwaltung von Partnern wird durch eine rollenbasierte Zugriffskontrolle geschützt. Nur Personen mit der entsprechenden Berechtigung können Partner initiieren, akzeptieren oder verwalten. Dies kann im Abschnitt „Datenaufnahme“ des Produktprofils erfolgen. Die folgenden Berechtigungen sind erforderlich:

![Zielgruppenfreigabe-Verbindung](assets/data-ingestion.png){zoomable="yes"}

| Berechtigung | Beschreibung |
|---|---|
| **Verwalten von Zielgruppenfreigabe-Verbindungen** | Mit dieser Berechtigung können Sie den Partner-Handshake-Prozess ausführen, mit dem zwei IMS-Organisationen verbunden werden, um [!UICONTROL Segment Match]-Flüsse zu aktivieren. |
| **Verwalten von Zielgruppenfreigaben** | Mit dieser Berechtigung können Sie Feeds (d. h. das für [!UICONTROL Segment Match] verwendete Datenpaket) für aktive Partner erstellen, bearbeiten und veröffentlichen (Partner, die vom Administrator bzw. der Administratorin eine Zugriffsberechtigung für **Zielgruppenfreigabe-Verbindungen** erhalten haben). |

Weitere Informationen zu Berechtigungen finden Sie in der [offiziellen Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=de#understanding-segment-match-permissions).

### Connect ID

Der Partnerverbindungsprozess wird über die **[!UICONTROL Connect ID]** verwaltet. Hierbei handelt es sich um eine zufällig generierte Kennung, die einer bestimmten AEP-Sandbox zugeordnet ist. Diese Connect ID ist erforderlich, um Partner-Sandboxes zu initiieren und zu verwalten. Außerdem kann eine Connect ID bei Bedarf auch neu generiert werden, um eine Partnerverbindung neu zu konfigurieren.

### Governance

Datensätze oder Datenattribute mit der Vertragskennzeichnung *C11* ermöglichen die Einschränkung des [!UICONTROL Segment Match]-Service. Segmente mit diesen Attributen können nicht für [!UICONTROL Segment Match] verwendet werden. Damit können Sie steuern, auf welche Segmente [!UICONTROL Segment Match] angewendet werden kann. Darüber hinaus werden auch benutzerdefinierte Richtlinien und Marketing-Aktionen angewendet. Standardmäßig sind Richtlinien deaktiviert und müssen aktiviert sein, um berücksichtigt zu werden. Auch Einschränkungen in Bezug auf E-Mail-Marketing und Onsite-Werbung, die während der Freigabe von Segmenten ausgewählt werden, werden übermittelt und an die Partner kommuniziert.

### Einverständnis

Die Einverständniseinstellungen für [!UICONTROL Segment Match] können wie folgt verwaltet werden:

* Auf Unternehmensebene während des Onboardings durch die Verwendung der Opt-out- oder Opt-in-Einstellung zur Einverständnisprüfung.

  Mit dieser Einstellung wird festgelegt, ob Benutzerdaten freigegeben werden können oder nicht. Die Standardeinstellung ist „Opt-out“, was bedeutet, dass Benutzerdaten unter der Voraussetzung freigegeben werden, dass der AEP-Kunde bereits über die erforderliche Einverständnisvereinbarung zur Verwendung der Datenfreigabe verfügt. Diese Einstellung kann in „Opt-in“ geändert werden, indem Sie den Kundenbetreuer von Adobe kontaktieren und eine zusätzliche Prüfung einrichten lassen, durch die AEP-Kunden das Einverständnis explizit einholen müssen.

* Festlegen des für Identitäten spezifischen Freigabeattributs (idSpecific) mithilfe der [Feldergruppe „Einwilligungen und Voreinstellungen“](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=de).

  Diese Feldergruppe besitzt ein einziges Objekt-Feld mit der Bezeichnung „Einverständniserklärungen“, um Informationen zum Einverständnis und Voreinstellungen zu erfassen. [!UICONTROL Segment Match] schließt standardmäßig alle Identitäten ein, die nicht explizit ausgeschlossen wurden, z. B.:

  ```
  "share": {
  `                `"val": "n"
  `     `}
  ```

  Diese Einstellung kann geändert werden, indem Sie sich an den Kundenbetreuer bzw. die Kundenbetreuerin von Adobe wenden und nur Identitäten mit explizitem Opt-in einschließen lassen, z. B.:

  ```
  "share": {
  `                `"val": "y"
  `     `}
  ```

### Warnhinweise

Warnhinweise werden generiert, wenn eine Partnerverbindung initiiert wird oder wenn Segment-Feeds für Partner freigegeben werden.

## Einrichtungs-Workflow

Der Workflow zum Einrichten einer Partnerverbindung wird wie oben beschrieben über die rollenbasierte Zugriffskontrolle verwaltet. Wenn die richtigen Berechtigungen vorliegen, muss für die Herstellung einer Verbindung zu einer Partner-Sandbox die Connect ID dieser Sandbox/Instanz im Unternehmen des Partners freigegeben werden.

Nachdem eine Verbindung vom sendenden Partner angefordert wurde, muss sie auf der Empfängerseite genehmigt werden, damit eine sichere und zuverlässige Verbindung zwischen den Partnern hergestellt werden kann. Der Verbindungs-Handshake mit dem Partner stellt sicher, dass zwischen den beiden Unternehmen eine Vereinbarung besteht, und Adobe den Prozess [!UICONTROL Segment Match] im Namen des Unternehmens durchführen darf. Wenn die Verbindung genehmigt ist und sich im aktiven Status befindet, kann der Prozess der Segmentfreigabe von beiden Seiten aus initiiert werden.

### Segmentfreigabe

Die Segmentfreigabe mit dem Partner erfolgt nur, wenn für die ausgewählte Kennung eine Übereinstimmung vorhanden ist. Es ist auch eine Eins-zu-viele-Partnerbeziehung möglich, d. h. Segmente können für mehrere Partner freigegeben werden.

Um die Segmentfreigabe zu starten, nachdem die Partnerverbindung hergestellt wurde, muss der sendende Partner einen Feed erstellen. Wählen Sie dann die Marketing-Anwendungsfälle oder -Aktionen aus, von denen die Segmentdaten ausgeschlossen werden sollen, sowie die dauerhaften Kennungen. Danach können relevante Segmente zum Feed hinzugefügt werden, um freigegeben zu werden.

Im Zuge dieses Segmentfreigabe-Workflows kann der sendenden Partner mithilfe von Überschneidungsschätzungen potenziell hochwertige Segmente ermitteln, bevor Daten übermittelt wurden.

Der gesamte Prozessablauf sieht folgendermaßen aus:

![Segmentfreigabe](assets/segment-sharing.png){zoomable="yes"}

Diese Überschneidungsschätzungen bieten wichtige Informationen. Sie ermöglichen das Ermitteln von Partnern und liefern Daten, auf deren Basis Vereinbarungen zur Datenzusammenarbeit getroffen werden können. Um diese Metriken für die Überschneidungsschätzung zu erhalten, werden keine Kunden- oder Segmentdaten zischen Sandboxes ausgetauscht. Die vom Kunden ausgewählten, gehashten und anwendbaren Identitäten in einer Sandbox werden in eine probabilistischen Datenstruktur eingefügt, mit der Adobe Vereinigungs- und Schnittvorgänge durchführen kann. Durch diese Vorgänge kann [!UICONTROL Segment Match] die geschätzte Schnittmenge aus zwei Datenstrukturen abrufen, die aus Identitäten aus zwei verschiedenen Sandboxes bestehen, ohne die tatsächlichen Werte vergleichen zu müssen.

Der Identitätsüberschneidungsprozess basiert auf dem Datensatz aus einem **vollständigen täglichen Profilexport** von sowohl der Absender- als auch der Empfänger-Sandbox, um gemeinsame Profile in den freigegebenen Segmenten identifizieren zu können. Der detaillierte Prozessablauf für den Überschneidungsprozess ist unten dargestellt:

![Identitätsüberschneidungsprozess](assets/overlap-process.png){zoomable="yes"}

Nachdem die Segmentfreigabe beim Sendepartner abgeschlossen ist, erhält der Empfänger eine Benachrichtigung über den freigegebenen Segment-Feed. Dieser Segment-Feed muss für das Profil beim Empfänger aktiviert sein, damit der Segmentzugehörigkeits-Datenfluss gestartet wird. Nur die Segmentzugehörigkeit wird in die sich überschneidenden Profilfragmente der IMS-Organisation des Empfängers aufgenommen und keine zusätzliche Identität wird vom Absender an den Empfänger übertragen.

Das freigegebene Segment ist im **[!UICONTROL Segment Builder]** auf der Registerkarte **[!UICONTROL Zielgruppen]** im Bereich `AEPSegmentMatch` verfügbar und kann beim Erstellen von Segmenten in der Empfänger-Sandbox für die Einbeziehung oder den Ausschluss von Zielgruppen verwendet werden.

Der tägliche Überschneidungsprozess sorgt dafür, dass die Segmentzugehörigkeit beim Absender und Empfänger stets synchronisiert bleibt. Der Empfänger kann das Profil für den empfangenen Segment-Feed deaktivieren, um den Segmentfreigabevorgang zu pausieren.

#### Segmentausstieg/-einstieg

Beim vollständigen Profilexport hat der Status der freigegebenen Segment-IDs unter der Segmentzugehörigkeit für Profile einen dieser Werte: _durchgeführt_, _beendet_ oder _vorhanden_.

Wenn während des täglichen Identitätsüberschneidungsprozesses die entsprechende Identität in der Empfänger-Sandbox vorhanden ist, werden diese Segmentzugehörigkeitsstatus für freigegebene Segmente zur Aufnahme an den Empfänger gesendet.

#### Segmentrücknahme

Bei Bedarf kann beim Absender eine Segmentrücknahme/-löschung durchgeführt werden. Dabei werden dem Empfänger alle Profile mit den zurückgeforderten Segment-IDs wieder entzogen. Die Segment-IDs werden aus der Segmentzugehörigkeit dieser Identitäten entfernt und am Empfänger erneut aufgenommen. Dadurch wird das vorhandene Segmentzugehörigkeitsfragment überschrieben, wodurch die Zugehörigkeit für dieses Segment gelöscht wird.

## Segment Match in programmatischen Angeboten verwenden

Angesichts der zunehmenden Einschränkungen bei Third-Party-Cookies und Geräte-IDs sucht programmgesteuerte Werbung nach neuen Möglichkeiten, Zielgruppen zu erstellen und anzusprechen. Es wurden immer mehr „universelle ID“-Lösungen vorgeschlagen, doch die Branche ist noch im Umbruch, da es keine vereinbarte, skalierbare Möglichkeit gibt, dasselbe Targeting zu erreichen und dabei anwendbare Datenschutzbelange gegeneinander abzuwägen.

Sie können Adobe Experience Platform Segment Match in der datenschutzorientierten Zielgruppenkollektion verwenden und programmgesteuerte private Angebote zwischen Werbetreibenden und Publishern verbessern. Mit Segment Match können Sie:

* Aufspaltung **Workflows** Anzeigenhandel und **Zielgruppe**.
* Zulassen, dass Partnermarken Zielgruppen-Metadaten für gemeinsam genutzte und mit Einverständnis übereinstimmende Identitäten mit dauerhaften Kennungen wie Hash-E-Mails und Hash-Telefonnummern innerhalb eines durch Einverständnis erzwungenen Prozesses freigeben können.

### Anwendungsfälle

* Erstanbieter-Zielgruppen mithilfe programmatischer privater Angebote ansprechen.
* Unterdrückung von First-Party-Zielgruppen über programmatische private Angebote.
* Lookalike-Zielgruppen aus Erstanbieter-Zielgruppen ansprechen, die über programmatische private Angebote gesendet werden.

>[!BEGINSHADEBOX]

**Betrachten Sie den folgenden Beispiel-Workflow zwischen einer Marke (Luma) und einem Mediennetzwerk (ACME):**

1. Eine Marke (Luma) führt über Segment Match einen Audience Match mit einem Mediennetzwerk (ACME) durch.
2. ACME überträgt die Zielgruppe(n) über Adobe Real-Time CDP Destination(s) an den Anzeigen-Server oder das programmgesteuerte SSP.
3. ACME richtet einen Abschluss mit privatem Inventar (ID) mit den entsprechenden Zielgruppenkriterien ein, einschließlich der im vorherigen Schritt festgelegten Audience. Die Deal-ID des privaten Inventars wird dann an die DSP von Luma gesendet.
4. Luma richtet ein privates Inventar-Geschäft und Traffic-Kampagne/Werbeanzeige-Kreative ein.
5. Die Kampagne wird dann über einen programmgesteuerten Abschluss mit privatem Inventar bereitgestellt.
6. Als Nächstes liefert der Anzeigen-Server oder das SSP Anzeigen-Impressions, die den festgelegten Targeting-Kriterien entsprechen. (Zusätzliche Zielgruppenkriterien, wie Frequenzlimitierung, sind über den Werbeserver und/oder DSP verfügbar, je nachdem, ob ein garantierter Abschluss oder ein Preferred Deal im Vertrag festgelegt wurde.)
7. Der Traffic wird auf die Markeneigenschaften von Luma geleitet.
8. ACME gibt dann die Erkenntnisse oder Zielgruppen nach der Kampagne über Segment Match für das Retargeting wieder frei.

>[!ENDSHADEBOX]

![Abbildung des Workflows zwischen Marke und Herausgeber.](./assets/segment-match-blueprints.png)

>[!IMPORTANT]
>
> Die oben beschriebene Lösung bietet zwar eine einfache Möglichkeit, First-Party-Daten über programmatische private Angebote anzusprechen, es können jedoch einige Überlegungen vor der Ausführung anstehen, darunter die folgenden Beispiele:
>
>* Einverständnis : Gültige Einverständniserfassung durch die Marke, den Herausgeber oder das Retail-Media-Netzwerk, um Daten auf diese Weise zu nutzen.
>
>* Richtlinien und Lizenzvereinbarungen: Einhaltung der geltenden Richtlinien (einschließlich Datenschutzrichtlinien und Vereinbarungen mit Drittanbietern) durch die Marke, den Herausgeber oder das Retail-Media-Netzwerk, um Daten auf diese Weise zu nutzen und zu aktivieren.



## Weitere Informationen

* [Segment Match](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=de#)
* [Berechtigungen](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=de)
* [Fehlerbehebung](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=de)
* [XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=de)
