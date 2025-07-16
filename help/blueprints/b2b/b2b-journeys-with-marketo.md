---
title: B2B-Journey, die Marketo Data Blueprint verwenden
description: Blueprint für die schnelle Bereitstellung von Journey Optimizer B2B edition mithilfe von Marketo Engage-Daten.
solution: Journey Optimizer B2B Edition
source-git-commit: 29ac41aa5d1d33b63c094ef56b03af73b88f96af
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 3%

---

# B2B-Journey, die Marketo Data Blueprint verwenden

In diesem umfassenden Handbuch wird der Prozess der Integration von Marketo Engage in Adobe Journey Optimizer B2B edition beschrieben. Es behandelt die Konfiguration benutzerdefinierter Schemata, die Aufnahme von Profilen und Konten sowie die Orchestrierung personalisierter Journey für Einkaufsgruppen. Durch die Verwendung von Marketo Engage-Daten stellt dieser Blueprint eine präzise Zielgruppenbestimmung und Interaktion über mehrere Kanäle hinweg sicher, was zu einer höheren Nachfrage und verbesserten Kundenerlebnissen führt.

## Anwendungsfälle

* **Einkaufsgruppen erstellen und verwalten**: Verwenden Sie generative KI, um Einkaufsgruppen innerhalb von Zielkonten zusammenzustellen und zu verwalten und so eine umfassende Abdeckung der wichtigsten Stakeholder sicherzustellen.
* **Mitgliedszuweisung automatisieren**: Mitglieder auf der Grundlage definierter Kriterien wie Inhaltsnutzung und CRM-Daten automatisch Kaufgruppenrollen zuweisen
* **Personalisierte Journey**: Entwerfen und visualisieren Sie mehrstufige Journey, die auf die jeweilige Einkaufsgruppe und deren Mitglieder basierend auf ihrer Rolle, ihrem Account, ihrem Produktinteresse und ihrer Lebenszyklus zugeschnitten sind
* **Echtzeit-Automatisierung**: Automatisieren Sie die Progression von Accounts und Einkaufsgruppen durch Journey mit Echtzeit-Interaktions-Trigger und Qualifizierungs-Scoring
* **Cross-Channel Engagement**: Binden Sie Einkaufsgruppen über mehrere Kanäle ein, einschließlich E-Mail, SMS, Anzeigen, Chat, Veranstaltungen und Webinare, um die Nachfragegenerierung und -qualifizierung zu optimieren
* **KI-gesteuerte Insights**: Verwenden Sie KI-gesteuerte Insights, um die Bereitstellung von Inhalten und die Interaktionsstrategien für einzelne Käufer und ganze Einkaufsgruppen zu optimieren
* **Einheitliche Datenaktivierung**: Aktivieren Sie einheitliche Kontolisten von Adobe Real-Time Customer Data Platform, um die neuesten und vollständigen Daten für die Erstellung und Verwaltung von Einkaufsgruppen bereitzustellen
* **Enhanced Collaboration**: Koordinieren Sie Marketing- und Vertriebsmaßnahmen, um präzisere Verkaufsmöglichkeiten zu schaffen und die Pipeline-Erstellung zu beschleunigen

## Programme

* Journey Optimizer B2B Edition
* Real-time Customer Data Platform B2B Edition
* Marketo Engage

## Integrationsmuster

| Integration | Beschreibung |
| :-- | :--- |
| [Marketo Engage-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) | Adobe Experience Platform erleichtert die Aufnahme von Daten aus Marketo und bietet Funktionen zum Strukturieren, Kennzeichnen und Erweitern der Daten mithilfe der Services von. |
| [Journey Optimizer B2B edition - Marketo Engage-Aktion](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes/action-nodes#marketo-engage-actions) | Synchronisieren Sie Account-Based Marketing in Journey Optimizer B2B edition mit Lead-basierten Aktivitäten in Marketo Engage mithilfe von personenbasierten Aktionen, um Listenmitgliedschaften, Personenpartitionen und Anfragekampagnen zu verwalten. |
| [Journey Optimizer B2B edition - Marketo Engage Assets](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/content-management/assets/marketo-engage-dam/marketo-engage-design-studio) | Marketo Engage Design Studio ist die standardmäßige Asset-Quelle für Journey Optimizer B2B edition und ermöglicht eine einfache Asset-Verwaltung für Account-Journey. |

## Architektur

![Lösungsarchitektur für AJO B2B mit ausschließlich Marketo-Daten](./assets/ajo-b2b-marketo-only.png){zoomable="yes"}

## Leitlinien

* Begrenzt auf 50 Kontosegmente pro Sandbox.
* Bewertung der Batch-Segmentierung.
   * Wird automatisch alle 24 Stunden nach Abschluss der Batch-Audience-Ausführung und der Profilexportvorgänge ausgewertet.
   * Keine Unterstützung für Edge-, Streaming- oder Ad-hoc-Auswertungen.
* Kontoattribute sind für den Export verfügbar.
* Ereignisse von Personen.
   * Bis zu 30 Tage Ereignis-Lookback, keine Sortierung von Ereignis-Eigenschaften.
   * UND/ODER wird unterstützt (sodass Sie sagen können: „A und B müssen passieren,“  aber man kann nicht sagen „A muss 3 Tage vor B passieren„).
* Maximal 5 Millionen Konten in allen Account-Journeys
* Maximal 40 Millionen Menschen in allen Account Journey
* Max. 1.000 Personen pro Konto in einer Einkaufsgruppe und Journey
* [Leitlinien für Profile und Segmentierung](https://experienceleague.adobe.com/de/docs/experience-platform/profile/guardrails)

## Implementierungsschritte

* Installieren Sie B2B-Schemas und -Namespaces mit einer der folgenden Optionen
   * Verwendete [Postman-Sammlung](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility)
   * Verwenden von [Vorlagen](https://experienceleague.adobe.com/de/docs/experience-platform/sources/ui-tutorials/templates) in der Platform-Benutzeroberfläche
* Erstellen eines Datenwörterbuchs, das die Zuordnung zwischen Marketo-Feldern und dem Experience Platform-XDM-Schema definiert
   * Verwenden Sie die [Marketo](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/field-management/export-all-object-metadata)Objektmetadaten als Ausgangspunkt
   * [Anpassen des XDM-](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/ui/fields/overview), um Ihre benutzerdefinierten Felder einzuschließen
   * Überprüfen Sie die [ (XDM-Felder](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/accounts/field-mapping), die von Journey Optimizer B2B edition unterstützt werden. Wenn Sie zusätzliche Felder benötigen, öffnen Sie ein Support-Ticket, um sie konfigurieren zu lassen
      * **workEmail.address** ist für den Personendatensatz erforderlich
      * **accountName** ist für den Kontodatensatz erforderlich
   * Fügen Sie eine neue XDM-Feldspalte zur exportierten Marketo-Metadaten-Tabelle hinzu, um die beabsichtigte Zuordnung aufzuzeichnen
* Konfigurieren Sie den [Marketo Engage-Quell-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
   * Verwenden Sie das oben definierte Datenwörterbuch, um die [Importzuordnung“ ](https://experienceleague.adobe.com/de/docs/experience-platform/data-prep/ui/mapping#import-mapping) Quell-Connectors zu definieren
   * Es wird nicht empfohlen, das Profil zu aktivieren, bevor die [Überlegungen zur Implementierung“ ](#implementation-considerations)
   * Empfehlung, mindestens Personen, Unternehmen, Chancen und Aktivitäten aufzunehmen, da diese Objekte bei der Erstellung Ihrer Konto-Zielgruppen am nützlichsten sind
* Implementieren [Verknüpfungsregeln für Identitätsdiagramme](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) für Personen:
   * Definieren, wie Personendatensätze mithilfe von Identity-Namespaces (z. B. E-Mail, B2B_Person) verknüpft werden.
   * Konfigurieren von Identitäts-Namespaces und Identitätszuordnungsregeln in AEP.
   * Validieren der Verknüpfung mit Beispieldaten für Personen und Vorschau-Tools.
* Aktivieren der Datensätze „Person“, „Unternehmen“, „Vertriebschancen“ und „Aktivitäten“ für [Profil](https://experienceleague.adobe.com/de/docs/experience-platform/catalog/datasets/user-guide#enable-profile)
* Definieren der ersten [Konto-Zielgruppe](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/accounts/account-audience-overview)
* Definieren [Einkaufsgruppen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/accounts/buying-groups/buying-groups-overview) oder einer [Account-Journey](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/account-journeys/journey-overview) mithilfe der Kontozielgruppe
   * Der Gruppenvorgang für den Einkauf wird täglich ausgeführt und verarbeitet neue Konten, die sich als Kontozielgruppe oder neu verknüpfte Personen qualifizieren
   * Der Kauf von Gruppenwartung wird jeden Freitag um Mitternacht CT ausgeführt, sodass das Entfernen von Mitgliedern oder das Hinzufügen neu qualifizierter Mitglieder nur freitags erfolgt

## Empfohlene Einrichtung

Um die Implementierung zu optimieren und die Kompatibilität mit Adobe Journey Optimizer B2B edition sicherzustellen, wird die folgende Einrichtung empfohlen:

* **Standard-Identitätsfelder verwenden:**
   * _email_ und _b2b_person_ sollten als Identitätsfelder im Personenschema beibehalten werden, um Identitätszuordnung und Zielgruppenaktivierung zu unterstützen.
* **Verwenden Sie die Standardzuordnungen für den Marketo Source-Connector:**
   * Nutzen Sie die von Adobe bereitgestellten vordefinierten Feldzuordnungen, um die Datenaufnahme zu vereinfachen und den Konfigurationsaufwand zu reduzieren.
* **Verwenden von Standardzuordnungen für AJO B2B:**
   * Verwenden Sie die [Standardfeldzuordnungen](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/accounts/field-mapping) für Journey Optimizer B2B edition, um die Kompatibilität mit der Einkaufsgruppenlogik und der Journey-Orchestrierung sicherzustellen.
* **Feldaktualisierungen für alle Felder außer E-Mail blockieren:**
   * Konfigurieren Sie in Marketo Engage die Feldverwaltung so, [ Aktualisierungen für alle Felder ](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) Adobe Experience Platform blockiert werden (außer _E-Mail_. Dies hilft, die Datenintegrität aufrechtzuerhalten und gleichzeitig die Identitätsauflösung zu ermöglichen.
* **Implementieren von Identitätsverknüpfungsregeln mit E-Mail als eindeutigem Identity-Namespace**
   * Konfigurieren Sie [Regeln zur Identitätsdiagramm](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/identity-graph-linking-rules/overview)Verknüpfung) in Adobe Experience Platform so, dass _E-Mail_ explizit als eindeutiger Identity-Namespace verwendet wird. Diese Regeln stellen sicher, dass Profile korrekt über Datenquellen hinweg zugeordnet werden, in denen _E-Mail_ vorhanden ist, was eine robuste Identitätsauflösung ermöglicht. Gemäß den Best Practices von Adobe definieren Sie Verknüpfungsregeln, die E-Mail als stabile und global eindeutige Kennung priorisieren, um ein konsistentes und datenschutzkonformes Identitätsdiagramm zu erhalten.
Diese Einrichtung bietet ein Gleichgewicht zwischen einfacher Bereitstellung und Data Governance und stellt eine zuverlässige Grundlage für die Orchestrierung von B2B-Journey sicher.

## Überlegungen bei der Implementierung

Bei der Implementierung von Adobe Journey Optimizer B2B edition ist es wichtig, die Funktionen zur Identitätszuordnung zu verstehen, die von der Real-time Customer Data Platform bereitgestellt werden. Diese Plattform führt Identitätszusammenfügungen sowohl auf Personen- als auch auf Kontoebene durch, wodurch eine einheitliche Sicht auf Kundendaten sichergestellt wird.

### Wichtigste Punkte

* **Identitätszuordnung**: Die Plattform verknüpft Identitäten mit Standardkennungen wie Marketo-ID, CRM-ID und E-Mail. Dies hilft bei der Erstellung eines umfassenden Profils, indem Daten aus verschiedenen Quellen zusammengeführt werden.
* **Potenzielle Risiken**: Die Verwendung von E-Mail als Kennung für das Zusammenfügen kann zu einem unbeabsichtigten Zusammenbruch der Identität führen. Dies bedeutet, dass verschiedene Personen, die dieselbe E-Mail-Adresse verwenden, fälschlicherweise zu einem einzigen Profil zusammengeführt werden können. Dieser Identitätszusammenbruch kann sich negativ auf die Genauigkeit der CRM-Daten auswirken und deren Integrität beeinträchtigen.
* **Zusammenführungsstrategie**: Die B2B-CDP verwendet eine zeitbasierte Zusammenführungsstrategie, bei der das letzte lastUpdatedDate für ein bestimmtes Profilattribut verwendet wird. Dadurch wird sichergestellt, dass die neuesten Daten im Profil angezeigt werden.
* **Überlegungen zur E-**: Es ist wichtig, die Verwendung von E-Mails als Kennung zum Zusammenführen von Profilfragmenten sorgfältig zu prüfen. Auch wenn dies von Vorteil sein kann, muss das Risiko eines Identitätszusammenbruchs sorgfältig gegen die Vorteile abgewogen werden. Ein Nachteil ist, dass ohne E-Mail als Kennung die von AJO B2B erstellte externe Zielgruppenzugehörigkeit nicht in das bestehende Profil integriert wird.
* **Marketo-Personenintegration**: AJO B2B verwendet die Marketo-Person mit der niedrigsten Lead-ID, wenn mehrere Marketo-Datensätze zu einem einzigen Profil zusammengeführt werden.

Unter Berücksichtigung dieser Punkte können Sie fundierte Entscheidungen darüber treffen, wie Sie die Identitätszuordnung in Adobe Journey Optimizer B2B edition konfigurieren und so genaue und zuverlässige Kundenprofile sicherstellen.

### Bewerten der Ergebnisse der Identitätszuordnung

Der Abfrage-Service kann verwendet werden, um die Auswirkungen der Identitätszuordnung in einem nicht profilaktivierten Datensatz zu sehen. Die folgende Abfrage kann für die Auswertung verwendet werden

#### Anzahl der aufgenommenen Datensätze

Diese Abfrage gibt die Gesamtzahl der Datensätze zurück, die in den Datensatz des Personenprofils aufgenommen wurden

```sql
select
    count(distinct b2b.personKey.sourceKey)
from
    marketo_person_ajo_b2b
```

#### E-Mails duplizieren

Diese Abfrage gibt die Anzahl der Personendatensätze zurück, die im Rahmen der Identitätszuordnung der Plattform zusammengeführt werden

```sql
select
    SUM(personCount)
from
    (
        select
            emailAddress,
            count(*) as personCount
        from
            (
                select
                    MAX(workemail.address) as emailAddress
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
```

#### E-Mail-Adressen mit doppelten Einträgen

Diese Abfrage gibt die E-Mails mit den meisten doppelten Datensätzen im Datensatz zurück.  Diese Liste kann verwendet werden, um einige dieser Datensätze zu überprüfen, um besser zu verstehen, wie sich die Verknüpfung der Identitäten auf Marketo und CRM auswirken kann.  Weitere Informationen zur Funktionsweise [ Identitätsverknüpfung finden Sie ](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home) „Identity Service - Übersicht“ .

```sql
select
    *
from
    (
        select
            emailAddress,
            MAX(personId) as personId,
            count(*) as personCount
        from
            (
                select
                    b2b.personKey.sourceKey,
                    MAX(workemail.address) as emailAddress,
                    MAX(b2b.personKey.sourceId) as personId
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
order by
    personCount desc
```

### Optionen

#### E-Mail als Identität entfernen

Wenn Sie nach der Analyse feststellen, dass E-Mail kein gültiges Feld ist, das als Identitätsfeld verwendet werden soll, kann das Personenschema geändert werden, um E-[ als Identitätsfeld zu entfernen](https://experienceleague.adobe.com/de/docs/experience-platform/xdm/ui/fields/identity)

#### Updates von Adobe Experience Platform blockieren

Wenn die Beibehaltung von E-Mail als Identitätsfeld für Ihre Anwendungsfälle am besten geeignet ist, gibt es die Option, [Feldaktualisierungen zu blockieren](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) die von AJO B2B stammen und es AJO B2B ermöglichen, hauptsächlich auf Marketo-Daten auszuführen.

## Verwandte Dokumentation

* [B2B Edition von Real-time Customer Data Platform](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Erste Schritte mit Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [Leitplanken für Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/de/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/de/docs/experience-platform)
* [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/de/docs/experience-platform/identity/home)
* [Marketo Engage](https://experienceleague.adobe.com/de/docs/marketo/using/home)
* [Adobe Experience Platform - Marketo-Quell-Connector](https://experienceleague.adobe.com/de/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
* [Dokumentation zu Adobe Journey Optimizer B2B edition](https://experienceleague.adobe.com/de/docs/journey-optimizer-b2b/user/guide-overview)
