---
source-git-commit: f7104d114a2644a494003bc78eb20768904f652c
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---
﻿---
title: Gesundheitswesen
description: Erfahren Sie mehr über den Health Care Shield, ein Adobe Experience Platform-Add-on zu plattformbasierten Anwendungen wie Real-Time CDP, Customer Journey Analytics und Adobe Journey Optimizer. Das Add-on macht diese Anwendungen für HIPAA- und PHI-Anforderungen qualifiziert.
solution: Experience Platform
---
# Gesundheitsschild

Der Gesundheitsschild ist ein Adobe Experience Platform-Add-on für Adobe Experience Platform-basierte Anwendungen wie Real-Time CDP, Customer Journey Analytics und Adobe Journey Optimizer, mit dem diese Anwendungen HIPAA so gestaltet werden können, dass sie den Anforderungen an die Verarbeitung und Nutzung geschützter Gesundheitsinformationen (PHI) entsprechen.

## Häufig gestellte Fragen zum Gesundheitsschild

Die folgenden häufig gestellten Fragen beantworten häufig gestellte Fragen zum Gesundheitsschild.

### Was ist HIPAA?

HIPAA ist der Health Insurance Portability and Accounability Act (HIPAA), eine US-Verordnung, die wichtige Schutzvorkehrungen zur Beschränkung der Verwendung und Offenlegung von geschützten Gesundheitsinformationen (PHI) bei der Erstellung, beim Erhalt, bei der Pflege oder bei der Übermittlung durch eine von HIPAA abgedeckte Einrichtung oder Geschäftspartner (z. B. Adobe-Kunden) an einen Geschäftspartner (Technologiepartner wie Adobe) vorsieht.

Adobe ist HIPAA-konform in Bezug auf die spezifischen HIPAA-konformen Adobe-Lösungen und die Einhaltung der HIPAA-Sicherheits-, Datenschutz- und Verstoßbenachrichtigungsregeln.

### Was ist ein Business Associate Agreement (BAA) und warum ist es wichtig?

Wenn ein abgedeckter RECHTSTRÄGER oder ein Unternehmensverband (ein Adobe-Kunde) die Dienstleistungen eines Business Associate (z. B. eine Adobe) nutzt, um bestimmte Arten von Verbraucherdaten zu erstellen, zu empfangen, zu pflegen oder zu übertragen, bei denen es sich um geschützte Gesundheitsdaten (PHI) oder ePHI (elektronische Version des PHI) handelt, müssen das abgedeckte Unternehmen und das Business Associate einen Business Associate Agreement (BAA) schließen.

Die BAA benötigt vertraglich die Adobe als Business Associate, um PHI angemessen zu schützen, indem sie die Anforderungen der HIPAA-Datenschutzbestimmungen, der HIPAA-Sicherheits- und der Breach Notification Rules erfüllt.

Mit dem Healthcare Shield-Add-on für Real-Time CDP kann Adobe jetzt eine BAA mit Kunden ausführen, die diese Funktion gemeinsam mit Adobe Real-Time CDP B2C und den Verbraucherströmen der Adobe Real-Time CDP B2P Edition lizenzieren.

### Warum ist der Gesundheitsschild für Real-Time CDP (und zukünftige plattformbasierte Anwendungen) nur in den USA verfügbar?

Da HIPAA ein US-Gesetz ist, beschränken wir die Verfügbarkeit des Healthcare Shield für die USA und für Unternehmen, die HIPAA unterliegen. Adobe plant, den Geltungsbereich auf andere Rechtsordnungen auszuweiten, da wir lokale Anforderungen einbeziehen und zuversichtlich sind, dass wir diese erfüllen können.

### Was ist der Gesundheitsschild für Real-Time CDP?

Der Gesundheitsschild für Real-Time CDP richtet sich an Kunden, die ein abgedeckter Entitäts- oder Business Associate sind und beabsichtigen, PHI in Real-Time CDP für die Datenerfassung, Zielgruppenerstellung und kanalübergreifende Aktivierung zu nutzen und Adobe zur Ausführung einer BAA zu benötigen. Gesundheitsschild ist für abgedeckte Entitäten mit HIPAA erforderlich, um Anwendungsfälle für die Echtzeit-Kundendatenplattform zu ermöglichen.

### Warum sollten die Gesundheitsaussichten des Real-Time CDP-Kaufschilds im Gesundheitswesen verbessert werden?

Als Add-on zu Real-Time CDP aktualisiert der Gesundheitsschild die Anwendung auf den Status &quot;HIPAA-bereit&quot;. Dies bedeutet, dass die Anwendung über die erforderlichen Garantien verfügt, um PHI gemäß den HIPAA-Anforderungen zu nutzen. Darüber hinaus ist die Adobe mit dem Gesundheitsschild bereit und in der Lage, dem Kunden zu gestatten, bestimmte Arten vertraulicher personenbezogener Daten in die HIPAA-fertige Anwendung einzubringen. Adobe wird mit Kunden, die Gesundheitsfürsorge-Schilde für eine kompatible plattformbasierte Anwendung lizenzieren, Business Associate Agreements (BAAs) unterzeichnen.

### Welche Datentypen sind für Real-Time CDP mit dem Gesundheitsschild zugelassen (und welche nicht)?

Mit dem Gesundheitsschild können Marken folgende PHI in plattformbasierte Anwendungen wie Real-Time CDP (&quot;Permitted Sensitive Personal Data&quot;) integrieren: Finanzinformationen, medizinische oder gesundheitliche Informationen einer Person. Wir schließen jedoch ausdrücklich Daten aus, die verwendet werden können, um Substanzmissbrauch, psychische Gesundheit, genetische Gesundheitsdaten oder Gesundheitsaufzeichnungen einer kleineren, vollständigen Kontonummer, vollständige Kreditkartennummern, staatliche Identifikatoren (wie SSN) und personenbezogene Daten von Kindern, die nach Kinderschutzgesetzen geschützt sind (wie die personenbezogenen Daten, die im US-amerikanischen Gesetz über die Privatsphäre von Kindern (&quot;COPPA&quot;) definiert sind), zu identifizieren.

### Können Real-Time CDP-Kunden mit dem Gesundheitsschild beliebige PHI-Typen zum Aufbau und zur Aktivierung von Zielgruppen verwenden?

Selbst wenn ein Kunde berechtigte vertrauliche personenbezogene Daten in Platform-native Anwendungen einbringen kann, müssen Kunden wissen, dass er allein dafür verantwortlich ist, dass er alle geltenden Vorschriften einhält und angemessene Berechtigungen, Einverständnisse, Genehmigungen und Genehmigungen von Verbrauchern erhält, um Daten auf die vorgesehene Weise zu nutzen.

### Welche Nuancen gibt es beim Erfassen und Aktivieren von Kundendaten mit nicht HIPAA-fähigen Adobe-Applikationen?

Ein Kunde, der eine Lizenz für das Gesundheitsschutzschild erteilt, darf personenbezogene Daten, die nicht für die HIPAA-Bereitschaft bestimmt sind, nicht in Anwendungen und Dienste der Adobe verwenden, erfassen, teilen oder integrieren. Beispielsweise sollte ein Kunde keine Segmente aktivieren, die PHI in Anwendungen wie Audience Manager, Adobe Target und Adobe Analytics enthalten. Kunden, die den Gesundheitsschild lizenzieren, können zulässige vertrauliche personenbezogene Daten oder genehmigte PHI in HIPAA-fähige Adoben-Anwendungen aufnehmen, unabhängig davon, ob die Datenquelle als HIPAA-bereit gilt oder nicht.

### Welche Nuancen gibt es beim Erfassen und Aktivieren von Kundendaten mit Nicht-HIPAA-fähigen Nicht-Adobe-Anwendungen?

Ein Kunde, der einen Gesundheitsschild lizenziert, sollte nach bestem Wissen bestimmen, wo er Segmente aktiviert, die PHI außerhalb der Adobe Apps enthalten. Adobe hat keine Kontrolle und ist nicht für Drittanbieter verantwortlich. Daten, die von einem Kunden an einen Drittanbieter gesendet werden, unterstützen möglicherweise nicht die Verarbeitung von Daten gemäß den Datennutzungsbezeichnungen der Adobe im Kundenschema. Darüber hinaus kann Adobe unseren Kunden keine Rechtsberatung anbieten.

## Wichtige Anwendungsfälle der Gesundheitsversorgung

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

|**RTCDP B2C Edition Standard Anwendungsfälle**|**Beschreibung**| | - | - | |Streaming-Datenerfassung|<p>- Normalisierte, flexible Datenmodelle, die über Adobe- und Nicht-Adobe-Verbindungen hinweg verwendet werden können</p><p>- Personen- und kontobasierte Datenschemata für das B2C-Marketing</p><p>- Tag-Management und Ereignisweiterleitung erfassen und verteilen Daten auf Ereignisebene in Echtzeit.</p><p>- Optimierte Profile, die die Bereitstellungszeit von Erlebnissen beschleunigen</p>| |Vertrauenswürdige Profilverwaltung|<p>- Einheitliche Profile, die Verbraucherattribute, Verhaltensdaten und Präferenzdaten enthalten</p><p>- Das Data Governance-Framework ist flexibel, transparent und wird auf einheitliche Profile angewendet, wobei Richtlinien erstellt und die automatische Durchsetzung erfolgt, um den Missbrauch von Daten zu verhindern. </p>| |Echtzeit-Aktivierung|<p>- Drag &amp; Drop-Segmentierung für B2C-Marketer</p><p>- Identitätsauflösung auf Personen- und Kontoebene und Profilanreicherung für kanalübergreifende Aktivierung</p><p>- Konsistente Kundenerlebnisse durch Zielgruppensorchestrierung und Echtzeit-Aktivierung über Kanäle und Umgebungen hinweg (Adobe und Nicht-Adobe)</p>| |Kundenakquise|<p>- Einblicke in die Konvertierung nicht authentifizierter Benutzer in erkannte/authentifizierte Benutzer</p><p>- Ermutigen Sie nicht registrierte Benutzer, sich für die Mitgliedschaft anzumelden.</p><p>- Abonnements erhöhen und/oder zurückgewinnen</p><p>- Analysieren Sie Kundenprofile, um die Tendenz zu verstehen (z. B. . Vergleich von Segmenten mit hohem Wert mit Segmenten mit geringer Performance und Optimierung der Akquise) </p>| |Kundeninteraktion|<p>- Angebote auf Basis der Neuigkeit des Verbraucherverhaltens und der Häufigkeit von Aktionen für Angebote auswählen (online und offline)</p><p>- Vereinheitlichung der digitalen Eigenschaften für ein vernetztes Erlebnis (z. B. Förderung von Downloads mobiler Apps und Nutzung der kanalübergreifenden Segmentaktivierung, um Erlebnisse miteinander zu verbinden)</p>| |Personalisierung im Maßstab|<p>- Bewerten von Segmenten am Edge für die Echtzeit-Personalisierung derselben Seite und der nächsten Seite</p><p>- Erhöhen Sie die Interaktion, indem Sie Besuchern, die eine Journey-übergreifende Sitzung abbrechen (z. B. Stehen gelassener Warenkorb oder wiederkehrende Besucher, die nicht konvertieren), eindeutige und zielgerichtete Erlebnisse bereitstellen.</p><p>- Vereinheitlichen und Verbinden von Offline- und Online-Verhaltensweisen zur Optimierung und Interaktion der Benutzer</p>| |Cross-Selling/Upsell|<p>- Kundenbindung beim Ausbau und der Pflege vorhandener Beziehungen zu Benutzern</p><p>- Fördern neuer Umsatzströme durch eine geschäftsübergreifende Einheit/Marke/Angebot des Kundenlebenszeitwerts</p><p>- Erhalten Sie Einblicke in AOV über Produkte und SKUs hinweg (z. B. häufige Bundles, Preisempfindlichkeit)</p>| |Kundentreue/Treue|<p>- Reaktivieren Sie Verbraucher, um die Loyalität zu steigern und Kundenabwanderungen zu vermeiden.</p><p>- Kuratieren personalisierter Produktempfehlungen für hochwertige Kunden basierend auf Präferenzen und Tendenz</p><p>- Erstellen einer Standardkadenz für Interaktion und Sonderangebote für treue Verbraucher</p><p>- Online- und Offline-Voreinstellungen verknüpfen, um Angebote kanalübergreifend zu optimieren</p>| |Datenerfassung|<p>- Erstellen Sie Handshakes in einer Benutzeroberfläche, um Workflows für die Datenzusammenarbeit zu erstellen.</p><p>- (Nutzen von branchenübergreifenden Überschneidungen bei Erstanbieterdaten für fundierte strategische Geschäftsentscheidungen und Kampagnen.</p><p>- Aufschlüsseln von Datensilos und Verstehen einer ganzheitlichen Journey</p><p>- Ehrenvoreinstellungen und Einverständnis nach Anwendungsfall</p>| |Medien-/Marketing-Effizienz &amp; Optimierung|<p>- Effizienzgewinne in der Organisation durch die Zentralisierung und Verwaltung von Kundendaten und Aktivierungskanälen in einem Aufzeichnungssystem</p><p>- Unterstützung von Unterdrückungskampagnen für effektive Ausgaben/Effizienz von Medien</p><p>- Anpassung an IT-Richtlinien durch Governance und Durchsetzung von Richtlinien</p><p>- Gewähren Sie bei Bedarf Zugriff auf Daten in Echtzeit, um rechtzeitige Kampagnen zu unterstützen.</p>|

## **3 - Relevante technische Funktionen**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

**Unterschiede**:

||**Vorkonfiguriert**|**Gesundheitsschild**| | - | - | - | |Verschlüsselung|Datenverschlüsselung in AEP [amtliche Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)|<p>Datenverschlüsselung in AEP [amtliche Dokumentation](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)</p><p>+</p><p>Vom Kunden verwaltete Schlüssel </p>| |Datenhygiene|<p>**Foundation**: Self-Service-Tool, mit dem Kunden den Datenlebenszyklus verwalten können. Dazu gehören das Löschen von Kundendaten und das Feld</p><p>-Level-Updates und Festlegen des Datenablaufs für Datensätze, um Daten nach Ablauf zu entfernen.</p><p>Limit von **10.000 Löschanfragen** pro Monat </p><p>Limit von 2 Datensatz-TTLs</p>|<p>**Premium**: Erweitern Sie die tägliche Kapazität/Schwelle der Data Hygiene-Funktion, um größere Datensätze in kürzerer Zeit zu kuratieren.</p><p>Limit von **2.000.000 Löschanfragen** monatlich im Rahmen des HealthCare Shield</p><p>Limit von 20 TTLs des Datensatzes</p>| |Einverständnis|<p>**Foundation**: Präzise Zustimmung und Voreinstellungen durch manuelles Hinzufügen von Zustimmungs- und Präferenzattributen zur Zielgruppensegmentierung.</p><p></p>|<p>**Premium**: Erstellen und erzwingen Sie automatisch Richtlinien dazu, wie Kundendaten basierend auf der Zustimmung und den Voreinstellungen verwendet werden sollen.</p><p></p>|

### **Governance:**
- **Datenhygiene**
   - [**Data Hygiene - Übersicht**](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-hygiene/overview.html?lang=en)
   - [**Datenhygiene in Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)
- **Durchsetzung von Richtlinien**
   - [**Data Governance - Übersicht**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html?lang=en)
   - [**Datennutzungsrichtlinien - Übersicht**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en)
   - [**Governance, Datenschutz und Sicherheit in Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/overview.html?lang=en#consent)

### **Datenschutz:**
- **Einverständnis**
   - [**Automatische Richtliniendurchsetzung**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en#consent-policy-evaluation)

### **Sicherheit:**
- **Zugriffssteuerungen**
   - [**Attributbasierte Zugriffskontrolle - Übersicht**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html)
- **Audits zur Benutzeraktivität**
   - [**Auditprotokolle**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html)
- **Verbesserte Verschlüsselung**
   - [**Sicherheitsübersicht für Adobe Experience Platform**](https://www.adobe.com/content/dam/cc/en/security/pdfs/AEP_SecurityOverview.pdf)
   - [**Verschlüsseln von Werten**](https://experienceleague.adobe.com/docs/experience-platform/tags/api/guides/encrypting-values.html?lang=en)
   - [**Datenverschlüsselung in Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/catalog/data-protection.html)
   - [**Zuordnungsfunktionen für Datenvorbereitung - Hashing**](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=en#hashing)
- [**Adobe Real-time Customer Data Platform und Gesundheitsschild | Adobe Experience Cloud**](https://experienceleague.adobe.com/docs/customer-data-management-voices-events/events/healthcare-shield.html?lang=en)

Bereitstellung des Erlebnisversprechens mit Zugriff auf weniger Daten. Unabhängig davon, ob Sie ein Advertiser, Herausgeber oder Agentur sind, hilft dieses Webinar bei der Entsperrung des

- [**Übersicht über Auditprotokolle | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html "https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html")

Erfahren Sie, wie Sie mithilfe von Audit-Protokollen sehen können, wer welche Aktionen in Adobe Experience Platform durchgeführt hat.

- [**Übersicht über die Datenhygiene | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)

Mit Adobe Experience Platform Data Hygiene können Sie den Lebenszyklus Ihrer Daten verwalten, indem Sie veraltete oder ungenaue Datensätze aktualisieren oder bereinigen.

- [**Automatische Durchsetzung von Richtlinien | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en)

In diesem Dokument wird beschrieben, wie Datennutzungsrichtlinien automatisch durchgesetzt werden, wenn Segmente in Experience Platform für Ziele aktiviert werden.

- [**Attributbasierte Zugriffssteuerung - Übersicht | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html "https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html")

Dieses Dokument enthält Informationen zur attributbasierten Zugriffskontrolle in Adobe Experience Platform
## **4 - HIPAA und Adobe - Produkte und Dienstleistungen**
Adobe ist weiterhin innovativ und passt sich an die Bedürfnisse unserer Kunden in der Gesundheitsbranche an, um ihre spezifischen Datenschutz- und Sicherheitsanforderungen zu erfüllen. 

Hier finden Sie die [details](https://www.adobe.com/trust/compliance/hipaa-ready.html).
## **5 - Marketingdiagramm auf hoher Ebene**
Produkte, die HIPAA-bereit sind (und nicht):

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

[https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0#](https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0)

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)
## **6 - Ansatz:**
### **Implementierungsphasen:**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

Bei jedem Schritt zu berücksichtigende Aspekte:

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

In diesem Abschnitt werden einige Best Practices beschrieben, die befolgt werden sollten. Dieser Abschnitt ist in drei Phasen unterteilt:
### **Interviewphase:**
Der Prozess der Befragung mit Interessenträgern ist von zentraler Bedeutung, um die folgenden Aspekte zu verstehen:

- Zielsetzung: Art der Anwendungsfälle - Konversion, Perspektive, Interaktion usw.
- Leistung: Alle Target-Erwartungen auf Dienstebene
- Datenquellen: Web/Analytics, Offline/Online, CRM, Loyalität usw.
- Datenvolumen
- SLT-/SLA-Anforderungen
- Identitäten - Anzahl der Identitäten, authentifiziert vs. anonyme Datenverarbeitung
- Format der Daten: JSON, CSV usw.
- Datenqualität, Datenumwandlung erforderlich
- Alle Pläne für die Segmentübereinstimmung (Freigabe) mit Partnern 
- Alle externen Zielgruppen, die importiert werden sollen
- Verschlüsselung: Standardschlüssel im Vergleich zum kundenverwalteten Schlüssel
- Zusammenführen von Daten: wird als e-PHI angesehen
- Einverständnisdatenerfassung - OneTrust, Consent SDK
- Zielanforderungen: Anforderungen hinsichtlich Häufigkeit und Latenz und Zugriffskontrolle
- Zugriffssteuerung
- Datenbereinigungsanforderungen
- Anforderungen an die Datenaktualisierung
- Warnmeldungen
- API-Zugriff

### **Designphase:**
Auf der Grundlage des Interviewprozesses wird sich die Designphase mit folgenden Themen befassen: Selbstverständlich muss die Design-Dokumentation überarbeitet und unterzeichnet werden. Das Designdokument kann die folgenden Aspekte abdecken:

- Wert der Daten:
   - Volumen - Menge der aufgenommenen Daten
   - Zeitbereich - Länge der aufgenommenen Daten
   - Treue - Profilvielfalt
- Berücksichtigen Sie AEP-Limits zusammen mit SLT-/SLA-Anforderungen. 
- Lizenzverwendung
- Anforderungen an die Datenisolierung - mehrere Sandboxes in einem oder mehreren Organisationen
- Datenfilter
- Anforderungen an die Datenhygiene (Datenmenge und Häufigkeit)
- Verfahren und Methoden zur Erfüllung der Anforderungen an die Löschung/Aktualisierung von Daten 
- Anforderungen an die Datenumwandlung - Upstream, Data Prep, Query Service
- Primäre und andere Identitäten verstehen und bestimmen
- [XDM-Schema-Design](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en)
- Bestimmen der Anzahl der Datensätze, der Profile und der Profile
- Zusammenführungsrichtliniendesign
- Einverständnisdatenverwaltung
- Governance: Rollen, Beschriftungen, Richtlinien, Marketing-Aktionen und Zugriffssteuerung
- [Profilanreicherung](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=de)
- Segmentierungsdesign-Anforderungen für Edge/Streaming/Batch
- Erwartete Ziele und Aktivierungspläne. Nur HIPAA-bereite Zielanforderungen berücksichtigen
- Pläne für Analytics
- Warnhinweise
- API-Zugriffsanforderungen hinzufügen

### **Implementierungsphase:**
Sobald das Design-Dokument überprüft und unterzeichnet wurde, kann die Implementierungsphase beginnen, die folgenden Bereiche zu behandeln:

- Anzahl erforderlicher Sandboxes: Entwicklung/Test/Produktion
- Zugriffssteuerung für Sandboxes
- Bereitstellungsmethode
- TTL-Anforderungen und -Häufigkeit (Data Hygiene)
- XDM-Schema und Zugriffskontrolle
- Einverständnisdurchsetzung
- Governance: Rollen, Bezeichnungen, Richtlinien und Marketing-Aktionen 
- Segmentierung
- Datensätze und Zugriffskontrolle
- Einrichtung der Datenhygiene
- Einrichten von Zielen und Zugriffssteuerung
- Warnhinweise einrichten
- API-Zugriffsanforderungen implementieren
- Testen von Ende bis Ende mit nachgeahmten Daten

