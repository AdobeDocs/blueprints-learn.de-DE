---
title: Konzept für gruppenbasiertes Marketing und Journey-Management
description: Erfahren Sie, wie Sie in Adobe Journey Optimizer B2B edition eine Journey finden, entwerfen und erstellen können, die sich als Leads zu einer Einkaufsgruppe qualifiziert.
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: b777ea5c301fb1fac39bc243b09a02a2f411f40e
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Konzept für gruppenbasiertes Marketing und Journey-Management

Marketing-Teams stehen derzeit vor vielen Herausforderungen, wenn es darum geht, Vertrieb mit qualifizierten Leads bereitzustellen. Eine dieser Herausforderungen besteht darin, mit den richtigen Personen in der Organisation zusammenzuarbeiten, was sich in der Regel aus Aufwand und Genauigkeit ergibt. Bei _Lead-Scoring_ ist die Gruppe zu eng und Teams verpassen möglicherweise die richtigen Personen. Bei der _Kontoauswertung_ ist ein größerer Aufwand erforderlich, um die richtige Person mit einer derart umfassenden Ansicht eines Kontos zu identifizieren.

Bei dieser Herausforderung wird das Konzept der **_Einkaufsgruppe_** eingeführt. Eine Einkaufsgruppe ermöglicht es Marketing-Experten, die richtige Gruppe von Personen in dem Konto zu finden und mit diesen Personen zu arbeiten, um die Leads zu qualifizieren und ihre Rolle in der Gruppe zu identifizieren.

## Verwendung von Einkaufsgruppen zur Qualifizierung von Leads und Konten

Das Erstellen und Bestreben, eine Einkaufsgruppe abzuschließen, erhöht die Effektivität der Marketing-Aktivität beim Qualifizieren von Leads zu Verkaufsmöglichkeiten. Gruppen zum Kaufen hängen von übereinstimmenden Leads zu Rollenvorlagen ab, die mit der Lösungsabsicht verknüpft sind.

Ein Beispiel für eine Einkaufsgruppe könnte _Acme Corp Seeds Buying Group_ sein, die ein Lösungsinteresse von _AI Driven Seeds_ hat.

Einkaufsgruppen repräsentieren eine Gruppe von Personen im Unternehmen, die sich für eine Lösung durch eine Lösungsabsicht interessieren. Und eine Einkaufsgruppe könnte für mehr als ein Lösungsinteresse identifiziert werden, und die Einzelpersonen erscheinen in mehr als einer Einkaufsgruppe.

Dank der verbesserten B2B-Funktionen von Journey Optimizer B2B edition können Sie jetzt diese Herausforderungen bewältigen:

* Fehlende Marketing-Kampagnen für _customer-first_.
* Inkonsistente Konversion von Marketing Qualified Lead (MQL) in Sales Qualified Lead (SQL), was die Ausrichtung von Initiativen an Vertrieb und Pflege von MQL erfordert
* Fehlende verkäufliche Mechanismen zum Identifizieren und Targeting von _Konkurrenzkonten_.
* Konzentrationsrisiko bei Umsatz und Pipeline.

Die folgenden KPIs stimmen gut mit der Erfolgsmessung von Anwendungsfällen überein:

* **Bewusstsein**: Sehen Zielkunden Ihre Anzeigen und führen sie diese zu einer höheren Rate als zuvor auf Ihre Website?
* **Interaktion**: Werden Kunden, die auf Ihre Website gelangen und sich mit Inhalten beschäftigen, als Ziel ausgewählt?
* **Zeit**: Wie viel Zeit benötigt das Sales-Team, um Kontakte aus verschiedenen Tools zu finden und der Gelegenheit hinzuzufügen?
* **Kosten**: Wie viel Geld kostet jeder Lead auf jeder Plattform?

## Account-basiertes Marketing

Ein gängiger Anwendungsfall und der Schwerpunkt in diesem Blueprint ist eine kontobasierte Marketing-Initiative. In diesem Anwendungsfall wird untersucht, an welchem Punkt Ihre erstellte Einkaufsgruppe mit einem Lead gefüllt wird, wenn sie mit einer Rolle und einem Lösungsinteresse verknüpft sind.

Wenn Sie eine Person durch die Journey führen, sammeln Sie weitere Informationen über den Lead (Arbeitsablauf für die Gruppe &quot;Kaufen&quot;) über Formulare, CRM-Synchronisierung und LinkedIn-Aktivierung.

Wenn ein Lead das Lösungsinteresse deutlich zeigt, zeigt er ein durch ein Business Linse definiertes Geschäftsereignis an. An diesem Punkt ist das Unternehmen zuversichtlich, dass dieser Leiter wirklich an einem Produkt interessiert ist. In Journey Optimizer B2B edition wird der Lead einer Käufergruppe für diese Lösung in einer Rollenvorlage zugeordnet (z. B. Einflussnehmer, Entscheidungsträger, Champions und Sponsoren).

Wie das folgende Diagramm zeigt, können Sie Details in Formularen oder durch LinkedIn-Aktivierung erfassen und eine Lösungsabsicht qualifizieren, wenn eine Interaktion mit einem Chat-Bot stattgefunden hat.

![Journey der Gruppe kaufen](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

Wenn der Prozentsatz für die Fertigstellung der Einkaufsgruppe hoch genug ist, teilen Sie die Gruppe über SQL oder eine SOL zum Sales-Team mit, um die Leads im Konto in einen abgeschlossenen Verkauf zu konvertieren.

## Kundenorientierte Lösung

B2B-Lead-Management konzentriert sich auf Konten und deren Leads. Die technische Ebene wird eingerichtet, um die Daten zu unterstützen, die diese Merkmale repräsentieren. Dies ist eine Voraussetzung für eine erfolgreiche Kontosegmentierung und Journey-Management.

### Voraussetzungen

Die kundenorientierte Lösung erfordert die folgenden Anwendungen und Dienste:

* Adobe Journey Optimizer B2B edition
* Adobe Real-time Customer Data Platform (RTCDP) B2B edition
* Adobe Marketo Engage

>[!NOTE]
>
>Die Lizenzierung von Journey Optimizer B2B edition sollte die folgenden Elemente umfassen:
><ul><li>Journey Optimizer B2B edition-Instanz, die mit Experience Platform B2B verbunden ist</li><li>Marketo Engage-Instanz, die mit RTCDP synchronisiert wird</li></ul>
&gt;<br/>
&gt;Für Bestandskunden von Marketo Engage wird eine Verbindung zur bestehenden Instanz empfohlen.
&gt;<br/><br/>
&gt;Für die Lösung stehen zusätzliche Erweiterungen zur Verfügung, um den Reichtum der Profile zu verbessern:
&gt;<ul><li>Zusätzliche Quellen für RTCDP zur Profilanreicherung</li><li>RTCDP-Ziel auf Marketo Engage</li></ul>

Die Implementierung dieser Lösung erfordert auch ein klares Verständnis des Konzepts von _Konto_ und _Einkaufsgruppe_ sowie darüber, wie diese Ihre Lead-Qualifizierung im Vertrieb verstärken und beschleunigen. Mit diesem Verständnis müssen Sie auch den gewünschten Wert für die Kaufgruppenvollständigkeit identifizieren.

### Architektur

![Lösungsarchitektur für den Kauf von gruppenbasiertem Marketing und Journey-Management](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### Datenschema

Bei jeder Implementierung von datengesteuerter Marketing-Automatisierung ist die Konzeption von Schemas für den Erfolg der Implementierung von entscheidender Bedeutung. Bevor Sie Ihr Schema entwerfen, überprüfen Sie die [B2B-Namespaces und Schemas](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces) und stellen Sie sicher, dass Sie mit dem Dienstprogramm zur automatischen Generierung vertraut sind, das zum Generieren eines neuen Schemas in einem neuen Implementierungsszenario verfügbar ist.

Die Schemas werden speziell mit B2B-Datenelementen angereichert, um die umfassende Beziehung in Profilen zu unterstützen, und enthalten die Kontoperspektive über den `sourceKey`, um Ereignisse und Profile mit dem Kontoschema zu verknüpfen. Schemas stellen eine Darstellung Ihrer organisatorischen Anforderungen sowie der erfassten und profilierten Daten dar. Um diese Anforderungen zu erfüllen, sind B2B-Schemata flexibel und stellen eine Erweiterung der erforderlichen B2B-Elemente dar.

Beim Entwerfen des Datenschemas für Ihr Unternehmen empfiehlt es sich, die Hauptentitäten in Ihrem ERD mit den übergeordneten Entitäten zu repräsentieren und zu kennzeichnen. (Siehe erstes Diagramm in der Dokumentation zum Schema [RTCDP B2B](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-b2b)). Dieser Prozess ist sehr hilfreich, um die erforderlichen Datenelemente zu verstehen, die Sie in jedem Schema definieren müssen.

Zum gegenwärtigen Zeitpunkt können Erlebnisereignisse Journey noch nicht beeinflussen. Zusätzlich zu den Erlebnisereignis-Schemata wird empfohlen, dem Konto Eigenschaften hinzuzufügen, die wichtige, auf Benutzeraktivitäten basierende Entscheidungen darstellen. Diese Eigenschaften werden für geteilte Pfadelemente im Journey Designer verwendet.

>[!NOTE]
>
>Derzeit ist die einzige von Journey Optimizer B2B edition unterstützte Beziehung die direkten Beziehungen über das Attribut `personComponents[0].sourceAccountKey.sourceKey` für die Entität `Person`. Eine künftige Erweiterung ist geplant, um das Objekt der Beziehung zwischen Konto und Person im B2b-Schema aufzunehmen.

### Marketo Engage-Quell-Connector

Zur Anreicherung der Kontodatenelemente können Sie Marketo Engage und die zugehörigen B2B-Daten verwenden, um die RTCDP- und Journey Optimizer B2B edition-Kontoansicht anzureichern. Durch die Einrichtung des Marketo Engage Source Connector und die Zuordnung von Marketo Engage-Daten zu RTCDP-Schemaattributen können Daten von Marketo Engage zu RTCDP und, falls bestimmt, zum Profil übertragen werden.

Ausführliche Informationen zur Connector-Konfiguration und zur erforderlichen Feldzuordnung zum Schema finden Sie in der [Marketo Engage-Connector-Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

### Leitlinien

Die Limits der Journey Optimizer B2B edition werden auf der Seite [Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html) beschrieben.

Limits im Zusammenhang mit der Implementierung

* Alle Limits von B2B-Zielgruppen werden im Blueprint [B2B-Zielgruppe und Profitaktivierung](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails) beschrieben und werden direkt auf den Erfolg von Journey Optimizer B2B edition übertragen.
* Wenn eine Aktivierung über Marketo Engage-Kanäle auf der Konto-Journey erforderlich ist oder wenn die CRM-Synchronisierung zur Anreicherung des Kontos verwendet wird, sind die [Marketo Engage-bezogenen Limits](https://helpx.adobe.com/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails) relevant.

Lesen Sie die Dokumentation zu den [Real-Time CDP-Schutzmechanismen](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview) , um weitere Informationen zu den Schutzmechanismen der RTCDP zu erhalten.

### Bereitstellung

* Alle Instanzen müssen sich in derselben IMS-Organisation befinden.
* Es kann nur eine Journey Optimizer B2B edition-Instanz mit einer Experience Platform-Sandbox verknüpft werden.
* Es wird dringend empfohlen, den [Marketo Source Connector zu Real-time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) zu implementieren.

## Implementierung

Die folgenden Schritte enthalten Anleitungen zum Aktivieren von Einkaufsgruppen in Ihrer Journey Optimizer B2B edition-Instanz, einschließlich der Aktivierung der Zielgruppe, um die Erweiterung Ihrer Kontobasis zu unterstützen, wobei der Schwerpunkt auf fehlenden Bestellrollenvorlagen liegt.

### Erforderliche Schritte

1. Definieren Sie das XDM-Schema, das Ihre Geschäftsansicht von Konten und Leads darstellt.

   Als ersten Schritt definieren und erstellen Sie ein Erlebnisschema, das auf die Anforderungen von B2B-Anwendungsfällen zugeschnitten ist und die Datenquellen sowohl in Batch- als auch in Echtzeit abdeckt. Dieses Design sollte die Art und Weise darstellen, wie das Unternehmen die Konto- und Personenentitäten sowie die Anwendungsfälle betrachtet, die Sie unterstützen möchten. Damit das Schema ein B2B-Schema ist, sollte das Schema den in der [RTCDP B2B-Schema-Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-b2b) verfügbaren Strukturen entsprechen.

   Eine nützliche Vorgehensweise besteht darin, die Entitätsnamen aus dem Diagramm zu nehmen und diese Entitäten in Ihrem Schema zu identifizieren, indem sie auf die gleiche Weise gekennzeichnet werden. Beachten Sie, dass einige Schemas bestimmte Schlüssel benötigen, z. B. `sourceKey`, um in RTCDP B2B zu funktionieren. Kurzfristig wird die _Viele-zu-viele_ -Beziehung zwischen Konto und Person durch die Kontoperson-Beziehung in Journey Optimizer B2B nicht unterstützt. Verwenden Sie die Accelerator-Skripte für den besten Ausgangspunkt:

   * Verwenden Sie das Skript [RTCDP B2B schema Creating script](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility) , um das anfängliche Schema zu generieren
   * Fügen Sie den generierten Schemas anwendungsspezifische Felder hinzu, um das Schema entsprechend den Anforderungen der Organisation auszufüllen.

   In dieser Phase besteht die Verbindung zwischen Marketo Engage und RTCDP und der Schemastruktur, um die Konto- und Personendaten zu akzeptieren, mit denen die Datensätze für die Kontosegmente gefüllt werden. Der nächste Schritt besteht darin, RTCDP mit Marketo Engage und Journey Optimizer B2B edition zu verbinden.

1. Konfigurieren Sie den Marketo Engage-Connector, einschließlich der Zuordnung von Marketo Engage zur XDM-Struktur.

   Wenn die XDM-Struktur und die Felder vorhanden sind, stellen Sie mithilfe des Connectors, der die Datensätze mit Daten von Marketo Engage und Journey Optimizer B2B speist, eine Verbindung zu RTCDP her. Organisieren Sie zunächst die Zuordnung für die Felder von Marketo Engage zu RTCDP-Klassen. Verwenden Sie die Informationen in der [Connector-Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm), um die Felder zu identifizieren, die Sie in Ihre Marketo Engage-Implementierung aufnehmen möchten.

### Gruppenkonfiguration kaufen

1. Erstellen Sie Zielgruppen für Konten in Journey Optimizer B2B edition oder RTCDP.

   Aktivieren Sie auf der Seite Kunden > Zielgruppen > Durchsuchen die Option Alle Zielgruppen planen , um Zielgruppen für Konten zu aktivieren. (In Fällen, in denen dies nicht funktioniert, müssen Sie ein Kundenprofilsegment erstellen, um die Erstellung von Kontozielgruppen zu ermöglichen.)

   Um ein Segment zu erstellen, führen Sie die Schritte in der Dokumentation [Konto-Zielgruppen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview) aus. Die Verwendung von Segment Builder mit den Datenfeldern, die Sie als Schlüssel für Ihre Kontozielgruppe identifiziert haben, wäre die Schlüsselaktivität bei der Definition der Zielgruppe.

   In dieser Phase wissen Sie, dass das Konto dazu führt, sich über die RTCDP zu konzentrieren und für die Bausteine der Einkaufsgruppe zu verwenden.

1. Definieren Sie die Benutzervorlage.

   Identifizieren Sie in jeder Gruppe die Rollen, die die Rolle repräsentieren, die Individuen in der Gruppe übernehmen, die Sie bearbeiten möchten. Sie können beispielsweise _Entscheidungsträger_, _Einflussnehmer_ und _Champion_ verwenden. Definieren Sie außerdem die Gewichtung und die Bedingungen für diese Rolle in der Gruppe.

   In der Dokumentation zu [Benutzerrollen-Vorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates) wird dieser Prozess und die Definition von Sonderbedingungen beschrieben.

1. Definieren Sie das Lösungsinteresse.

   Ein Lösungsinteresse ist eine Möglichkeit, den Schwerpunkt Ihrer Marketingaktivitäten und -strategie auf die Einkaufsgruppen zu legen.

   Um ein Lösungsinteresse zu definieren, führen Sie die Schritte in der Dokumentation [Lösungsinteressen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests) aus. Denken Sie daran, dass Sie es verwenden, um die Einkaufsgruppe mit einer Verkaufsinitiative in der Organisation abzugleichen.

1. Konfigurieren Sie die Kaufgruppe.

   Konfigurieren Sie die Käufergruppe entsprechend den Bausteinen der Käufergruppe, konfigurieren Sie sie für das Lösungsinteresse und passen Sie die Zielgruppe mit einer Zielgruppe an, um die Benutzervorlage mit den richtigen Mitgliedern des Kontos zu vervollständigen. Weisen Sie mit dieser Konfiguration der von Ihnen identifizierten Benutzervorlage ein Lösungsinteresse zu und geben Sie jeder Rolle einen Anteil am Verkaufserfolg für dieses spezifische Produkt.

   Um die Kaufgruppe zu erstellen, führen Sie die Schritte in der Dokumentation [Gruppen kaufen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create) aus.

   In dieser Phase sind Sie bereit, [eine Journey](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey) zu erstellen und mit der Kontozielgruppe zusammenzuarbeiten, um die Einkaufsgruppe zu erstellen und sie für das Lösungsinteresse zu qualifizieren.

### Zielgruppenaktivierung

Erhöhen Sie durch Aktivierung der Zielgruppe die Vollständigkeit der Einkaufsgruppe.

1. Definieren Sie eine LinkedIn Ad Matched Account-Zielgruppe.

   Zusätzlich zu den E-Mail- und Formularausfüllaktivitäten bietet Journey Optimizer B2B edition eine LinkedIn-Anzeigenfunktion, mit der Sie Ihr Konto umfassender gestalten und eine Einkaufsgruppe abschließen können. Dazu werden durch die Erweiterung der Kontoausgabeaufrufe und die Erhöhung der Reichweite Ihrer Marketingaktivitäten unterstützt.

   Wenn Sie mit gebührenpflichtigen LinkedIn-Medien mit Konten kommunizieren möchten, bei denen die Kaufgruppen nicht vollständig oder ausreichend beschäftigt sind, erweitern oder interagieren Sie mit der Kontozielgruppe, verwenden Sie die Funktion [LinkedIn Account Matched Audiences](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences) , um LinkedIn-Anzeigenzielgruppen über kontengerechte Zielgruppen zu generieren.

1. Aktivieren Sie die Zielgruppe für den Kauf von Gruppen.

>[!TIP]
>
>Einige Hinweise für erfolgreiche Kampagnen:
>
>* Eine Kampagne sollte über Rollenfilter verfügen, die auf die Einkaufsgruppen mit fehlenden Rollen abgestimmt sind, um den ROI zu erhöhen.
>* Um Leads zu erfassen, führen Sie direkte Leads zum Ausfüllen von Formularen (LinkedIn- oder Marketo Engage-Formularen) und erneutes Targeting der fehlenden Formulare durch.
