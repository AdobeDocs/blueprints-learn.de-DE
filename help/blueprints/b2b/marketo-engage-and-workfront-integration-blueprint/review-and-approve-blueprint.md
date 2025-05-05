---
title: Blueprint überprüfen und genehmigen
description: Blueprint überprüfen und genehmigen – Marketo Engage- und Workfront-Integrations-Blueprint
exl-id: a446faab-7db4-42a2-b4b9-395725c49c9f
source-git-commit: 3d6a2416cdb9956e59be4b2918ba19f88cd2150b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 87%

---

# Blueprint überprüfen und genehmigen {#review-and-approve-blueprint}

Sicherzustellen, dass Marketing-Assets und -Kampagnen die Erwartungen und Standards eines Unternehmens erfüllen, geht über das Bereitstellen der richtigen Inhalte und Nachrichten an die richtige Zielgruppe hinaus. Unternehmen tragen auch die Verantwortung dafür, interne Politiken, Branchenvorschriften und sogar rechtliche Voraussetzungen bei der Einleitung neuer Marketing-Initiativen einzuhalten. Durch die Integration von Überprüfungs- und Genehmigungsschritten in den Kampagnenentwicklungsprozess können Marketing-Teams sicherstellen, dass Inhalte und Nachrichten korrekt sind und den Branchenstandards entsprechen, insbesondere für Branchen wie Finanzdienstleistungen, Gesundheitswesen und Arzneimittel.

Mit Workfront und Marketo Engage haben Marketing-Teams die Möglichkeit, ein eng vernetztes Marketing-System mit genauen und konformen Botschaften zu entwickeln.

## Nutzen Sie das Proofing und die Erweiterten Genehmigungen für Marketo Engage mit Workfront {#unlock-proofing-and-advanced-approvals}

Wenn wir über das Erstellen von Marketing-Kampagnen nachdenken, müssen wir berücksichtigen, dass mehrere Systeme die verschiedenen erforderlichen Schritte unterstützen, darunter Planung, Erstellung, Überprüfung, Feedback, Genehmigung und Ausführung. Mit Workfront und Marketo Engage verfügen Teams über alle nötigen Tools, die sie durch den durchgängigen Prozess für Planung und Launch einer neuen Marketing-Kampagne führen. Darüber hinaus können Teams ihren Überprüfungs- und Genehmigungsprozess weiter optimieren, um Kampagnen noch schneller zu entwickeln und gleichzeitig sicherzustellen, dass Genauigkeit und Compliance den höchsten Standards entsprechen.

### Anwendungsfälle prüfen und genehmigen, die mit Marketo Engage und Workfront entsperrt wurden {#review-and-approve-use-cases-unlocked-with-marketo-engage-and-workfront}

* Vermeiden Sie uneinheitliches Feedback und verbessern Sie die Zusammenarbeit an einem zentralen Ort, indem Sie die Anmerkungs- und Kommentarfunktionen von Workfront für Marketo Engage-Assets nutzen.

* Zentralisieren Sie Ihre Genehmigungen, indem Sie sie in Marketo Engage aus den Workfront-Genehmigungs-Workflows heraus auslösen.

* Unterstützen und optimieren Sie komplexe Genehmigungs-Workflows für Marketing-Assets, indem Sie die erweiterten Genehmigungsfunktionen von Workfront mit Marketo Engage-Assets nutzen.

* Demokratisieren Sie den Zugriff auf Marketing-Entwürfe, indem Sie Marketo-Assets programmgesteuert in Workfront abrufen, um sie von mehreren Stakeholdern überprüft zu werden.

* Verfolgen Sie Änderungen und erzeugen Sie eine Datenspur, indem Sie alle Überprüfungs- und Proofing-Arbeiten für Marketo Engage-Assets in Workfront zentralisieren.

## Planen Sie Ihren Workflow für Testversand und Genehmigung {#planning-your-proof-and-approval-workflow}

Beachten Sie vor dem Einrichten der Integration von Testversand und Genehmigung zwischen Marketo Engage und Workfront die folgenden Aspekte:

* Welche Assets müssen überprüft und genehmigt werden?
* Wer muss die genehmigende Person sein?
* Muss es mehrere genehmigende Personen geben, bevor ein Marketing-Asset live geschaltet werden kann?
* An welchem Punkt des Kampagnenentwicklungsprozesses werden Marketing-Assets zusammengestellt und können überprüft werden?

Wenn Sie diese Fragen beantworten, erhalten Sie eine Baseline dafür, wie Ihr Genehmigungsfluss aussehen wird und wie Sie erhalten einen Ansatz für die Konfiguration Ihrer Workfront-Instanz.

## Erstellen eines Workflows für Testversand und Genehmigung zwischen Marketo Engage und Workfront {#building-a-proof-and-approval-workflow}

Zur Optimierung von Testversand und Genehmigung zwischen Workfront und Marketo Engage können Sie die beiden Lösungen mithilfe von Workfront Fusion integrieren. Workfront Fusion bietet eine Workflow-Oberfläche zum Auslösen von Aktionen und Übergeben von Informationen zwischen Ihren Workfront- und Marketo Engage-Instanzen.

Beachten Sie dazu die folgenden Schritte als Teil des Prozesses für eine integrierte Überprüfung und Genehmigung.

1. Konfigurieren Sie Ihr Workfront-Projekt mit der Aufgabe „Bereit für Überprüfung“.
1. Lösen Sie die Synchronisierung Ihrer Marketo Engage-E-Mails mit Workfront bei einer Änderung des Aufgabenstatus aus.
1. Konvertieren Sie in Workfront Ihre Marketo Engage-E-Mail-Datei in einen überprüfbaren Testversand.
1. Verwenden Sie das Workfront-Proofing, um über Kommentare und Anmerkungen zusammenzuarbeiten.
1. Genehmigen Sie den Workfront-Testversand, um die Asset-Genehmigung in Marketo Engage auszulösen, und markieren Sie dann die Aufgabe als abgeschlossen.

### Konfigurieren eines Workfront-Projekts mit einer Aufgabe Bereit für Überprüfung“ {#configure-a-workfront-project-with-a-ready-for-review-task}

Verwenden Sie [Projektvorlagen](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/create-and-manage-project-templates/project-template-overview.html?lang=de){target="_blank"}, um die meisten der wiederholbaren Prozesse, Informationen und Einstellungen zu erfassen, die mit den Projekten in Ihrem Unternehmen verbunden sind. Sie können Aufgaben definieren, Themen in die Warteschlange stellen, benutzerdefinierte Formulare erstellen und Dokumente an Ihre Vorlage anhängen.

Nehmen Sie in Ihre Projektvorlage in Workfront Aufgaben für die Überprüfung von Assets auf, die Teil Ihrer Marketing-Kampagne sind. Darüber hinaus können Sie einen Genehmigungsprozess hinzufügen, um einzelne Genehmigungen oder komplexere mehrstufige Genehmigungen zu bearbeiten.

Wenn Sie eine neue E-Mail-Kampagne starten möchten, sollten Sie über eine Projektvorlage verfügen, die eine Aufgabe zur Überprüfung der E-Mail sowie einen Genehmigungsprozess enthält, um sicherzustellen, dass die E-Mail vom richtigen Stakeholder genehmigt wird, bevor sie gesendet werden kann.

![Aufgabenbildschirm](assets/review-and-approve-blueprint-1.png){zoomable="yes"}

### Auslösen der Synchronisierung einer Marketo Engage-E-Mail mit Workfront bei Änderung des Aufgabenstatus {#trigger-your-marketo-engage-email-to-sync-to-workfront}

Im Rahmen des Überprüfungsprozesses sollten Sie E-Mails mit Ihrem Workfront-Projekt synchronisieren können, sobald sie für die Überprüfung durch Ihr Marketing-Team bereit sind. Zu diesem Zweck empfiehlt es sich, eine Aufgabe „Bereit zur Überprüfung“ mit einem [Aufgabenstatus](https://experienceleague.adobe.com/docs/workfront/using/manage-work/projects/update-work-on-a-project/update-task-status.html?lang=de){target="_blank"} einzurichten, der angibt, wann die E-Mail zur Überprüfung bereit ist. In unserem Beispiel haben wir unserer Aufgabe den Status „Marketo-E-Mail überprüfen“ hinzugefügt, der ausgewählt werden kann, wenn der E-Mail-Entwurf zur Überprüfung durch Stakeholder bereit ist.

Wenn dieser Status in Ihrem Workfront-Projekt vorhanden ist, können Sie Ihr Workfront Fusion-Szenario so konfigurieren, dass auf die Aufgabe „Bereit zur Überprüfung“, die auf „Marketo-E-Mail überprüfen“ aktualisiert werden soll, gewartet wird. Nach der Aktualisierung kann Ihr Szenario die Marketo Engage-E-Mail als HTML-Datei abrufen, sie komprimieren und eine Kopie davon in den zu überprüfenden Workfront-Projektdokumenten speichern.

![Bereit für den Überprüfungsbildschirm](assets/review-and-approve-blueprint-2.png){zoomable="yes"}

### Konvertieren einer Marketo Engage-E-Mail in einen überprüfbaren Testversand in Workfront {#convert-your-marketo-engage-email-to-reviewable-proof-in-workfront}

Sobald Ihre Aufgabe „Bereit zur Überprüfung“ in den Status „Marketo-E-Mail überprüfen“ überführt und die Marketo Engage-E-Mail in Workfront gespeichert wurde, können Sie Ihr Workfront Fusion-Szenario so konfigurieren, dass die E-Mail in einen Workfront-Testversand konvertiert wird.

### Verwenden des Workfront-Proofings zur Zusammenarbeit über Kommentare und Anmerkungen {#use-workfront-proofing-to-collaborate}

Mit den Proofing[&#128279;](https://experienceleague.adobe.com/docs/workfront/using/review-and-approve-work/proofing/proofing-overview/proofing-basics.html?lang=de){target="_blank"}-Funktionen von Workfront kann Ihr Marketing-Team ein neues Asset wie ein Bild oder eine E-Mail aufnehmen und über Kommentare und Anmerkungen zusammenarbeiten. Sobald ein Korrekturabzug bereit für die Live-Schaltung ist, können Entscheidungsträger das Asset über das Proofing-Tool genehmigen.

![E-Mail-Bildschirm konvertieren](assets/review-and-approve-blueprint-3.png){zoomable="yes"}

### Asset-Genehmigung für Workfront Proof und Trigger in Marketo Engage genehmigen und Aufgabe als abgeschlossen markieren {#approve-workfront-proof-and-trigger-asset-approval-in-marketo-engage}

Workfront Fusion kann erkennen, wann die E-Mail von Stakeholdern genehmigt wurde, und eine Anfrage an Marketo Engage senden, um die E-Mail in Marketo zu genehmigen.

Nachdem die E-Mail von den richtigen Team-Mitgliedern geprüft/genehmigt wurde, ist die E-Mail bereit, in Marketo Engage live zu gehen!

## Vorlagen für Fusion-Szenarios {#fusion-scenario-templates}

Um die Entwicklung von Überprüfungs- und Genehmigungs-Workflows in Ihrer eigenen Workfront- und Marketo Engage-Instanz zu optimieren, haben wir Fusion-Vorlagen entwickelt, die Ihnen bei den ersten Schritten mit der Integration helfen. Sie können diese Vorlagen verwenden, indem Sie im Bereich „Öffentliche Vorlagen“ von Fusion nach „Marketo“ suchen und die Vorlagen auf Ihre Instanz herunterladen.

### Prüfen eines E-Mail-Testversands eines Marketo Engage-E-Mail-Entwurfs in Workfront {#review-an-email-proof-of-your-marketo-engage-email-draft-in-workfront}

Das nachstehende Fusion-Szenario führt Sie durch die erste Hälfte des Überprüfungs- und Genehmigungsflusses, in dem der E-Mail-Entwurf von Marketo Engage abgerufen und als Testversand in Workfront gespeichert werden kann. Sobald er als Testversand in den Workfront-Projektdokumenten gespeichert ist, kann er von den Marketing-Stakeholdern geprüft, kommentiert und mit Anmerkungen versehen werden, was Teil des Prüfungsprozesses ist.

![Fluss zur Überprüfung und Genehmigung des Fusionsszenarios](assets/review-and-approve-blueprint-4.png){zoomable="yes"}

### Genehmigung einer E-Mail in Workfront, die die Genehmigung des Assets in Marketo Engage auslöst {#approve-an-email-in-workfront-that-triggers-approval}

Das nachstehende Fusion-Szenario kann verwendet werden, um festzustellen, wann ein Testversand in Workfront genehmigt wurde, und es kann diese Genehmigung an Marketo Engage weiterleiten, um den E-Mail-Entwurf zu aktualisieren, damit er live ist und in einem Marketo Engage-Programm verwendet werden kann.

![Testversand-Genehmigung für Fusionsszenario](assets/review-and-approve-blueprint-5.png){zoomable="yes"}

Gemeinsam können diese beiden Szenarien verwendet werden, um einen bidirektionalen Pfad zu erstellen, über den Marketing-Assets von Marketo Engage in die stabilen Überprüfungs- und Genehmigungs-Workflows von Workfront gezogen und Genehmigungen von Workfront zurück an Marketo Engage übertragen werden.
