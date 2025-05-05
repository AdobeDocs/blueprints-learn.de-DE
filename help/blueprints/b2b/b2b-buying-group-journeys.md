---
title: Kaufen von gruppenbasiertem Marketing und Journey-Management-Blueprint
description: Erfahren Sie, wie Sie eine Journey entwickeln, entwerfen und erstellen, die für eine Einkaufsgruppe in Adobe Journey Optimizer B2B edition qualifiziert ist.
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: b777ea5c301fb1fac39bc243b09a02a2f411f40e
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Einkauf von gruppenbasiertem Marketing und Journey-Management-Blueprint

Marketing-Teams sehen sich derzeit vielen Herausforderungen gegenüber, wenn es darum geht, dem Vertrieb qualifizierte Leads zur Verfügung zu stellen. Eine dieser Herausforderungen besteht darin, mit den richtigen Personen in der Organisation zusammenzuarbeiten, was sich in der Regel in Anstrengung und Genauigkeit widerspiegelt. Bei _Lead-Scoring_ ist die Gruppe zu eng gefasst und die Teams vermissen möglicherweise die richtigen Mitarbeiter. Bei _Account-Bewertung_ ist ein größerer Aufwand erforderlich, um die richtige Person mit einer solch umfassenden Ansicht eines Accounts zu identifizieren.

In dieser Herausforderung wird das Konzept **_Einkaufsgruppe_** eingeführt. Eine Einkaufsgruppe ermöglicht es Marketing-Experten, die richtige Gruppe von Personen im Konto zu finden und mit diesen Personen zusammenzuarbeiten, indem sie die Leads qualifizieren und ihre Rolle in der Gruppe identifizieren.

## Verwendung von Einkaufsgruppen zur Qualifizierung von Leads und Konten

Das Erstellen und Anstreben, eine Einkaufsgruppe abzuschließen, erhöht die Effektivität der Marketing-Aktivität bei der Qualifizierung von Leads zu Verkaufsmöglichkeiten. Einkaufsgruppen sind darauf angewiesen, Leads mit Rollenvorlagen abzugleichen, die mit der Lösungsabsicht verknüpft sind.

Ein Beispiel für eine Einkaufsgruppe könnte die _Acme Corp Seeds Buying Group_ sein, die ein Lösungsinteresse an „AI-_Seeds“_.

Einkaufsgruppen repräsentieren eine Gruppe von Personen im Unternehmen, die an einer Lösung durch einen Lösungszweck interessiert sind. Eine Einkaufsgruppe kann für mehr als ein Lösungsinteresse identifiziert werden, und die Einzelpersonen erscheinen in mehr als einer Einkaufsgruppe.

Dank der erweiterten B2B-Funktionen von Journey Optimizer B2B edition können Sie nun diese Herausforderungen bewältigen:

* Fehlende Marketing _Kampagnen, bei denen der Kunde_.
* Inkonsistente Konversion von Marketing Qualified Lead (MQL) in Sales Qualified Lead (SQL), was die Abstimmung von Initiativen mit dem Vertrieb erfordert, um MQL zu fördern
* Es fehlt ein verkäuflicher Mechanismus, um (_)_ zu identifizieren und anzusprechen.
* Konzentrationsrisiko in Umsatz und Pipeline.

Die folgenden KPIs stimmen gut mit der Messung des Erfolgs von Anwendungsfällen überein:

* **Awareness**: Werden Ihre Anzeigen von Target-Kunden angezeigt und werden diese dadurch schneller auf Ihre Website geleitet als zuvor?
* **Interaktion**: Kommen Target-Kunden auf Ihre Website und interagieren mit Inhalten?
* **Time**: Wie lange dauert es, bis das Vertriebsteam Kontakte aus verschiedenen Tools findet und zu der Opportunity hinzufügt?
* **Cost**: Wie viel Geld kostet jeder Lead auf jeder Plattform?

## Account-Based Marketing

Ein gängiges Anwendungsbeispiel und der Schwerpunkt in diesem Blueprint ist eine Account-basierte Marketing-Initiative. In diesem Anwendungsbeispiel wird untersucht, wo Ihre erstellte Einkaufsgruppe mit einem Lead gefüllt wird, wenn sie mit einer Rolle und einem Lösungsinteresse verknüpft ist.

Wenn Sie einen Kontakt über die Journey führen, sammeln Sie weitere Informationen über den Lead (Einkaufsgruppen-Workflow), über Formulare, CRM-Synchronisierung und LinkedIn-Aktivierung.

Wenn ein Lead das Lösungsinteresse klar aufzeigt, zeigt er ein Geschäftsereignis an, das durch eine Geschäftsbrille definiert ist. Zu diesem Zeitpunkt ist das Unternehmen zuversichtlich, dass dieser Lead wirklich an einem Produkt interessiert ist. In Journey Optimizer B2B edition wird der Lead einer Einkaufsgruppe für diese Lösung in einer Rollenvorlage zugeordnet (z. B. Influencer, Entscheidungsträger, Champions und Sponsoren).

Wie die folgende Abbildung zeigt, können Sie Details in Formularen oder durch LinkedIn-Aktivierung erfassen und einen Lösungszweck qualifizieren, wenn eine Interaktion mit einem Chat-Bot stattgefunden hat.

![Gruppen-Journey kaufen](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

Wenn der vollständige Prozentsatz der Einkaufsgruppe hoch genug ist, geben Sie die Gruppe über SQL oder einen SOL an das Vertriebs-Team weiter, um die Leads im Konto in einen abgeschlossenen Verkauf umzuwandeln.

## Account-orientierte Lösung

Der Schwerpunkt des B2B-Lead-Managements liegt auf Accounts und ihren Leads. Die technische Ebene wurde eingerichtet, um die Daten zu unterstützen, die diese Merkmale darstellen. Dies ist eine Voraussetzung für eine erfolgreiche Kontosegmentierung und Journey-Verwaltung.

### Anforderungen

Für die Lösung mit Schwerpunkt auf Kunden sind die folgenden Anwendungen und Services erforderlich:

* Adobe Journey Optimizer B2B edition
* Adobe Real-time Customer Data Platform (RTCDP) B2B edition
* Adobe Marketo Engage

>[!NOTE]
>
>Die Lizenzierung von Journey Optimizer B2B edition sollte die folgenden Elemente enthalten:
><ul><li>Journey Optimizer B2B edition-Instanz, die mit Experience Platform B2B verbunden ist</li><li>Marketo Engage-Instanz, die mit RTCDP synchronisiert wird</li></ul>
>&gt;<br/>
>&gt;Für bestehende Marketo Engage-Kunden ist eine Verbindung zur bestehenden Instanz der empfohlene Ansatz.
>&gt;<br/><br/>
>&gt;Es sind zusätzliche Erweiterungen für die Lösung verfügbar, um die Profilreichhaltigkeit zu verbessern:
>&gt;<ul><li>Zusätzliche Quellen zur RTCDP zur Anreicherung des Profils</li><li>RTCDP-Ziel auf Marketo Engage</li></ul>

Die Implementierung dieser Lösung setzt auch ein klares Verständnis des Konzepts von _Account_ und _Buying Group_ voraus, sowie davon, wie diese Ihre Sales Lead-Qualifizierung verstärken und beschleunigen. Mit diesem Verständnis müssen Sie auch den gewünschten Kaufgruppen-Vollständigkeitswert identifizieren.

### Architektur

![Lösungsarchitektur für den Kauf von gruppenbasiertem Marketing und Journey-Management](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### Datenschema

Bei jeder Implementierung einer datengesteuerten Marketing-Automatisierung ist das Design von Schemas für den Erfolg der Implementierung von entscheidender Bedeutung. Bevor Sie Ihr Schema entwerfen, überprüfen Sie die [B2B-Namespaces und -](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces) und stellen Sie sicher, dass Sie mit dem Dienstprogramm zur automatischen Generierung vertraut sind, das zum Generieren eines neuen Schemas in einem neuen Implementierungsszenario verfügbar ist.

Die Schemata werden speziell mit B2B-Datenelementen angereichert, um die umfangreiche Beziehung in Profilen zu unterstützen und die Account-Perspektive durch die `sourceKey` einzuschließen, Ereignisse und Profile mit dem Account-Schema zu verknüpfen. Schemata sind eine Darstellung Ihrer Unternehmensanforderungen und der erfassten und profilierten Daten. Um diese Anforderungen zu erfüllen, sind B2B-Schemata flexibel und stellen eine Erweiterung der erforderlichen B2B-Elemente dar.

Beim Entwerfen des Datenschemas für Ihre Organisation ist es eine Best Practice, die Hauptentitäten in Ihrem ERD mit den übergeordneten Entitäten darzustellen und zu kennzeichnen. (Siehe erstes Diagramm in der [RTCDP B2B-Schema-Dokumentation](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-b2b)). Dieser Prozess ist sehr hilfreich, um die erforderlichen Datenelemente zu verstehen, die Sie in jedem Schema definieren müssen.

In dieser Phase können Erlebnisereignisse noch keinen Einfluss auf Journey haben. Zusätzlich zu den Erlebnisereignis-Schemata wird empfohlen, dem Konto Eigenschaften hinzuzufügen, die wichtige Entscheidungen basierend auf Benutzeraktivitäten darstellen. Diese Eigenschaften werden für Split-Path-Elemente im Journey-Designer verwendet.

>[!NOTE]
>
>Derzeit werden von Journey Optimizer B2B edition nur die direkten Beziehungen über das `personComponents[0].sourceAccountKey.sourceKey`-Attribut in der `Person`-Entität unterstützt. Die zukünftige Erweiterung ist geplant, um das Konto-Personen-Beziehungsobjekt im B2B-Schema zu berücksichtigen.

### Marketo Engage-Quell-Connector

Um die Kontodatenelemente anzureichern, können Sie Marketo Engage und die zugehörigen B2B-Daten verwenden, um die RTCDP- und Journey Optimizer B2B edition-Kontoansicht anzureichern. Durch das Einrichten des Marketo Engage-Source-Connectors und das Zuordnen von Marketo Engage-Daten zu RTCDP-Schemaattributen können Daten von Marketo Engage zu RTCDP und, falls angegeben, zum -Profil übertragen werden.

Detaillierte Informationen zur Connector-Konfiguration und zur erforderlichen Feldzuordnung zum Schema finden Sie in der Dokumentation zum [Marketo Engage-Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

### Leitlinien

Die Journey Optimizer B2B edition-Leitplanken werden auf der Seite [Produktbeschreibung“ ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html).

Leitplanken im Zusammenhang mit der Implementierung

* Alle Leitplanken für B2B-Zielgruppen werden im Blueprint [B2B-Zielgruppen- und -Profilaktivierung](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails) beschrieben, der direkt auf den Erfolg von Journey Optimizer B2B edition übertragen wird.
* Wenn die Aktivierung über Marketo Engage-Kanäle auf der Konto-Journey erforderlich ist oder wenn die CRM-Synchronisierung zur Anreicherung des Kontos verwendet wird, sind die [Schutzmechanismen in Bezug auf die Marketo Engage](https://helpx.adobe.com/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails) von Bedeutung.

Weitere Informationen zu RTCDP-Leitplanken finden Sie [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview) Dokumentation zu Real-Time CDP-Leitplanken .

### Bereitstellung

* Alle Instanzen müssen derselben IMS-Organisation angehören.
* Es kann nur eine Journey Optimizer B2B edition-Instanz mit einer Experience Platform-Sandbox verknüpft werden.
* Es wird dringend empfohlen, den [Marketo Source Connector für Real-time Customer Data Platform zu implementieren](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

## Implementierung

Die folgenden Schritte bieten Anleitungen zur Aktivierung von Einkaufsgruppen in Ihrer Journey Optimizer B2B edition-Instanz, einschließlich der Zielgruppenaktivierung, um die Erweiterung Ihrer Kontobasis zu unterstützen, wobei der Schwerpunkt auf fehlenden Einkaufsgruppenrollenvorlagen liegt.

### Vorausgesetzte Schritte

1. Definieren Sie das XDM-Schema, das Ihre Geschäftsansicht von Konten und Leads darstellt.

   Als ersten Schritt definieren und erstellen Sie ein Erlebnisschema, das den Anforderungen des B2B-Anwendungsfalls entspricht und die Datenquellen sowohl in Batch- als auch in Echtzeit abdeckt. Dieses Design sollte die Art und Weise repräsentieren, wie das Unternehmen über die Konto- und Personenentitäten und die Anwendungsfälle denkt, die Sie unterstützen möchten. Damit das Schema ein B2B-Schema ist, sollte das Schema den Strukturen folgen, die in der Dokumentation zum [RTCDP B2B-Schema](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-b2b) verfügbar sind.

   Eine nützliche Praxis besteht darin, die Entitätsnamen aus dem Diagramm zu übernehmen und diese Entitäten in Ihrem Schema zu identifizieren, indem Sie sie auf die gleiche Weise kennzeichnen. Beachten Sie, dass für einige Schemata spezifische Schlüssel wie `sourceKey` erforderlich sind, damit sie in RTCDP B2B funktionieren. Kurzfristig wird die _Viele-zu-Viele_-Beziehung zwischen Konto und Person über die Konto-Personen-Beziehung in Journey Optimizer B2B nicht unterstützt. Verwenden Sie die Beschleunigerskripte für den besten Ausgangspunkt:

   * Verwenden Sie das Skript [RTCDP B2B-Schemaerstellung](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility), um das anfängliche Schema zu generieren
   * Fügen Sie den generierten Schemata Anwendungsfall-spezifische Felder hinzu, um das Schema entsprechend den Anforderungen des Unternehmens zu vervollständigen.

   In dieser Phase haben Sie die Verbindung zwischen Marketo Engage und RTCDP. Es wird die Schemastruktur definiert, um die Konto- und Personendaten zu akzeptieren, mit denen die Datensätze für die Kontosegmente ausgefüllt werden. Der nächste Schritt besteht darin, RTCDP mit Marketo Engage und Journey Optimizer B2B edition zu verbinden.

1. Konfigurieren Sie den Marketo Engage-Connector, einschließlich der Zuordnung von Marketo Engage zur XDM-Struktur.

   Wenn die XDM-Struktur und die Felder eingerichtet sind, verbinden Sie Marketo Engage mit RTCDP mithilfe des Connectors, der die Datensätze mit Daten von Marketo Engage und Journey Optimizer B2B speist. Organisieren Sie zunächst die Zuordnung für die Felder vom Marketo Engage zu den RTCDP-Klassen. Verwenden Sie die Informationen in der [Connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm)-Dokumentation, um die Felder zu identifizieren, die Sie aus Ihrer Marketo Engage-Implementierung aufnehmen möchten.

### Konfiguration der Einkaufsgruppe

1. Kontozielgruppen in Journey Optimizer B2B edition oder RTCDP erstellen.

   Aktivieren Sie die Option Planung für alle Zielgruppen auf der Seite Durchsuchen der → „Zielgruppen →&quot;, um Konto-Zielgruppen zu aktivieren. (In Fällen, in denen dies nicht funktioniert, müssen Sie ein Kundenprofilsegment erstellen, um Kontozielgruppen erstellen zu können.)

   Um ein Segment zu erstellen, befolgen Sie die Schritte in der [Dokumentation zu Konto-Zielgruppen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview). Die Verwendung von Segment Builder mit den Datenfeldern, die Sie als Schlüssel für Ihre Konto-Zielgruppe identifiziert haben, wäre die wichtigste Aktivität bei der Definition der Zielgruppe.

   In dieser Phase wissen Sie, dass sich das Konto über RTCDP auf konzentriert und für die Bausteine der kaufenden Gruppe verwendet.

1. Definieren Sie die Rollenvorlage.

   Identifizieren Sie in jeder Einkaufsgruppe die Rollen, die die Rolle darstellen, die Einzelpersonen in der Gruppe einnehmen, die Sie ansprechen möchten. Sie können beispielsweise _Entscheidungsträger_, _Influencer_ und _Champion_. Legen Sie auch die Gewichtung und die Bedingungen für diese Rolle in der Einkaufsgruppe fest.

   In der [Dokumentation zu Rollenvorlagen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates) wird dieser Prozess beschrieben und es wird beschrieben, wie spezielle Bedingungen definiert werden.

1. Definieren Sie das Lösungsinteresse.

   Ein Interesse an einer Lösung ist eine Möglichkeit, den Fokus auf die Einkaufsgruppen für Ihre Marketing-Aktivitäten und -Strategien zu verdeutlichen.

   Um ein Interesse an einer Lösung zu definieren, führen Sie die Schritte in der [Dokumentation zu Lösungsinteressen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests) aus. Denken Sie daran, dass Sie damit die Einkaufsgruppe mit einer Verkaufsinitiative in der Organisation abgleichen.

1. Konfigurieren Sie die Einkaufsgruppe.

   Konfigurieren Sie nun, wenn die Bausteine der Einkaufsgruppe fertig sind, die Einkaufsgruppe für die Zielgruppe des Lösungsinteresses und des Kontos mit einer Zielgruppe, um die Rollenvorlage mit den richtigen Mitgliedern des Kontos abzuschließen. Weisen Sie mit dieser Konfiguration der von Ihnen identifizierten Rollenvorlage eine Interessenslösung zu und geben Sie jeder Rolle eine Gewichtung für den Verkaufserfolg für dieses spezifische Produkt.

   Um die Einkaufsgruppe zu erstellen, befolgen Sie die Schritte in der [Einkaufsgruppen-Dokumentation](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create).

   In dieser Phase sind Sie bereit, [eine Journey zu erstellen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey) und mit der Account-Zielgruppe zu arbeiten, um die Einkaufsgruppe aufzubauen und sie für das Lösungsinteresse zu qualifizieren.

### Zielgruppen-Aktivierung

Erhöhen Sie die Vollständigkeit der Einkaufsgruppe durch Zielgruppenaktivierung.

1. Definieren Sie eine LinkedIn Ad Matched Account-Zielgruppe.

   Zusätzlich zu den Aktivitäten zum Ausfüllen von E-Mails und Formularen bietet Journey Optimizer B2B edition eine LinkedIn-Anzeigenfunktion, mit der Sie die Breite Ihres Kontos erhöhen und die Bemühungen zum Abschluss einer Einkaufsgruppe durch die Erweiterung der Lead-Spanne im Konto und die Erhöhung der Reichweite Ihrer Marketing-Aktivitäten unterstützen können.

   Um bezahlte LinkedIn-Medien für die Kommunikation mit Konten zu verwenden, bei denen die Einkaufsgruppen nicht ausreichend abgeschlossen oder interagiert wurden, die Konto-Zielgruppe zu erweitern oder mit ihr zu interagieren, verwenden Sie die Funktion [Zielgruppen mit übereinstimmendem LinkedIn-Konto](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences), um LinkedIn-Anzeigenzielgruppen über Zielgruppen mit übereinstimmendem Account zu generieren.

1. Zielgruppe für Einkaufsgruppen aktivieren.

>[!TIP]
>
>Einige Hinweise für erfolgreiche Kampagnen:
>
>* Eine Kampagne sollte über Rollenfilter verfügen, die für Einkaufsgruppen mit fehlenden Rollen geeignet sind, um den ROI zu erhöhen.
>* Um Leads zu erfassen, leiten Sie Leads zum Ausfüllen von Formularen (LinkedIn- oder Marketo Engage-Formulare) und zielen Sie die fehlenden Formulare erneut ab.
