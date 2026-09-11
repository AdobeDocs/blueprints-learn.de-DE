---
title: 'Teil 2: Schlüsselfelder'
description: Identifizieren Sie die Identitätsfelder Primär, Person und Beziehung sowie die erforderlichen Erlebnisereignisfelder mit der Bezeichnung ERD-Tabellen.
doc-type: article
solution: Experience Platform
exl-id: 24b6fdbd-0d59-4fe7-828e-c4bc7036db90
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---


# Teil 2: Schlüsselfelder

## Vortrag

In diesem Video erfahren Sie, wie Sie die primäre Identität, Personenidentitäten und Beziehungsidentitäten in jeder Tabelle sowie die erforderlichen Felder _id, Zeitstempel und Ereignistyp für Erlebnisereignisse identifizieren.

>[!VIDEO](https://video.tv.adobe.com/v/3459085/?quality=12&learn=on)



## Labor-Details

### Identitätsfelder

- **Personenidentität** - Wird zur eindeutigen Identifizierung einer Person verwendet. Sie werden nur in Primären Entitätstabellen verwendet. Es muss mindestens eines davon geben, aber es kann mehr als ein geben.
- **Beziehungsidentität (d. h. Nicht-Person)** Wird verwendet, um Beziehungen von den Primären Entitätstabellen des Echtzeit-Kundenprofils zu einer zugehörigen unterstützenden Entitätsklasse (d. h. Suchen) zu beschreiben.
- **Primäre Identität** - Kann entweder eine Personenidentität oder eine Beziehungsidentität (keine Person) sein, die als Speicherschlüssel verwendet wird und für jedes Schema erforderlich ist, das vom Echtzeit-Kundenprofil verwendet wird. Bei Primären Entitätstabellen identifiziert die Identität außerdem eindeutig eine Person. Wenn für XDM-Profilschemata und Lookup-Schemata angegeben, bestimmt dieses Feld, ob ein neuer Datensatz erstellt oder ein vorhandener Datensatz aktualisiert wird. Es muss genau eines davon geben.

### Erforderliche Felder (nur XDM-Erlebnisereignis)

- **\_id** - wird vom Echtzeit-Kundenprofil in Verbindung mit der Primären Identität verwendet, um einen eindeutigen Speicherschlüssel für das Ereignis zu erstellen. Erforderlich, um eine versehentliche Duplizierung von Ereignisdaten im Profil-Service zu verhindern
- **Zeitstempel** - Alle Ereignisse ereignen sich zu einem bestimmten Zeitpunkt und daher erfordert jedes Ereignis einen Zeitstempel

Nicht erforderlich, aber nachdrücklich empfohlen:

- **Ereignistyp** - beschreibt das allgemeine Verhalten der Ereignisdaten (d. h. Kauf, Reservierung gebucht usw.),

### Allgemeine Regeln

1. Bridge-Tabellenregel #2 - in Situationen, in denen eine Brückentabelle zwischen einer übergeordneten Tabelle &quot;**P**&quot; oder &quot;**E**&quot; (d. h. einer übergeordneten Tabelle) und einer übergeordneten Tabelle &quot;**L**&quot; vorhanden ist, behandeln Sie die Brückentabelle als Teil der übergeordneten Tabelle
1. Überprüfen Sie in diesem Stadium immer, ob Identitäten für **einzelne** Person eindeutig sind, um eine Überarbeitung während der Datenaufnahme zu vermeiden
1. Bei Erlebnisereignis-Schemata ist die Primäre Identität das, was dieses Verhalten einer einzelnen Person eindeutig identifiziert.
1. Bei Nachschlagetabellen ist der Primärschlüssel (PK) des relationalen Modells immer die Primäre Nicht-Personen-Identität

Für jede Tabelle aus dem Connection 5G Warehouse ERD und Streaming ERD, die Sie entweder als **„P“, „E“ oder „L“ gekennzeichnet haben, führen** jetzt die folgenden Schritte aus, um die primären Identitäten, Personenidentitäten, Beziehungsidentitäten und alle erforderlichen Felder für die angegebenen Schemaklassen zu identifizieren.

>[!NOTE]
>
>Beziehen Sie sich während der Labs auf das folgende Diagramm, während Sie Identitäten in Schemata kennzeichnen
>
>![Abbildung mit Beispielkennzeichnungen für Primäre Identität, Personenidentität und Beziehungsidentität, die auf ERD-Tabellen angewendet wurden](assets/part-2-key-fields-identity-labeling-diagram.png)



## Schritt 1: Kennzeichnen von Schlüsselfeldern in den Tabellen „XDM Individual Profile“

Führen Sie die folgenden Schritte aus, um die Schlüsselfelder in der Tabelle des Kundenkontos zu identifizieren:

- Identifizieren Sie das Feld, das als Primäre Identität verwendet werden soll, und beschriften Sie es mit einer `PI`
- Alle anderen Personenidentitäten identifizieren und mit einem `I` kennzeichnen
- Identifizieren Sie alle Beziehungsidentitäten und kennzeichnen Sie sie mit einem `R`



## Schritt 2: Kennzeichnen von Schlüsselfeldern in den XDM-Erlebnisereignistabellen

Führen Sie dieselben Aufgaben aus wie in Schritt 1, aber jetzt für die XDM-Erlebnisereignistabellen:

- Identifizieren Sie das Feld in jeder Tabelle, die die Primäre Identität sein wird, und beschriften Sie es mit einem `PI`
- Alle anderen Personenidentitäten in jeder Tabelle identifizieren und mit einem `I` kennzeichnen
- Identifizieren Sie alle Beziehungsidentitäten und beschriften Sie sie mit einem `R`

Zusätzlich zu den oben genannten Kennzeichnungen sollten Sie auch Folgendes kennzeichnen:

- Identifizieren oder erstellen Sie die eindeutige Ereignis-ID für jede XDM-Erlebnisereignistabelle und beschriften Sie sie mit einer `_id`
- Identifizieren Sie den Zeitstempel des Ereignisses für jede Tabelle und beschriften Sie sie mit einem `T`
- Identifizieren oder erstellen Sie den Ereignistyp für jede Tabelle und beschriften Sie sie mit einer `ET`



## Schritt 3: Kennzeichnen von Schlüsselfeldern in den Suchtabellen

Identifizieren Sie in jeder Nachschlagetabelle das Feld, das als Primäre Identitätstabelle fungieren soll, und beschriften Sie es mit einer `PI`



## Überprüfung

Im folgenden Video werden die Schlüsselfelder überprüft, die in den 5G-Verbindungstabellen identifiziert wurden, einschließlich der Gründe, warum ein verkettetes Feld als eindeutige Ereignis-ID für Datensätze mit veränderlicher Reihenfolge benötigt wurde.

>[!VIDEO](https://video.tv.adobe.com/v/3459088/?quality=12&learn=on)
