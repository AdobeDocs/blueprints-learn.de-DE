---
title: 'Teil 1: Verbleibende Tabellentypen'
description: Identifizieren und beschriften Sie Brückentabellen und Tabellen, die eine Denormalisierung in den einzelnen Profil-, Erlebnisereignis- und Lookup-ERDs erfordern.
doc-type: article
solution: Experience Platform
exl-id: 742b58fa-3feb-4275-ab45-eb8d3aade22c
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Teil 1: Verbleibende Tabellentypen

## Vortrag

In diesem Video erfahren Sie, wie Sie die verbleibenden nicht gekennzeichneten Tabellen mit einem Dennormalisierungstyp von D oder B beschriften, einschließlich der Frage, wie Bridge Table Rule #1 die Viele-zu-eins-Seite einer Brückentabelle in eine Suche verwandelt.

>[!VIDEO](https://video.tv.adobe.com/v/3459082/?quality=12&learn=on)



## Labor-Details

Identifizieren und Kennzeichnen von Tabellen im 5G-Warehouse der Verbindung und in Streaming-ERDs, die in eine der folgenden Kategorien passen

- Bridge-Tabelle (mit &quot;**B**&quot; gekennzeichnet)
- Neue Lookup-Tabellen, die aufgrund von Brückentabellen vorhanden sind
- Tabellen, für die eine Denormalisierung erforderlich ist (mit &quot;**D** gekennzeichnet)

>[!CAUTION]
>
>Hier ist die Bestellung sehr wichtig! Stellen Sie sicher, dass Sie die Schritte in der richtigen Reihenfolge ausführen, da jeder Schritt vom vorherigen abhängt



## Schritt 1: Identifizieren und Kennzeichnen von einzelnen XDM-Profiltabellen

1. Identifizieren Sie alle Tabellen, die direkt mit den Tabellen des individuellen XDM-Profils in Verbindung stehen (einen Sprung weg) und noch keine Beschriftung haben. Markieren Sie sie mit dem Stern &quot;**\***&quot;.
1. Wenn Sie nur die Schemata betrachten, die Sie gerade mit einem Stern gekennzeichnet haben, führen Sie die folgenden Aufgaben aus:
   1. **Beschriftung „B“ für Brückentabelle hinzufügen** - Eine Tabelle wird als Brückentabelle betrachtet, wenn zwei oder mehr Tabellen damit verknüpft sind, wobei die vielen Seiten der Beziehung aus beiden Tabellen auf die Brückentabelle zeigen
   2. **Beschriftung „D“ für zu denormalisierende Tabellen hinzufügen** - Jede Entität, die eine 1\:M- oder M:1-Kardinalität mit der Tabelle „XDM Individual Profile“ hat und noch nicht markiert ist

>[!NOTE]
>
>Bridge-Tabellenregel speichern #1.
>
>Wenn eine Brückentabelle auftritt, die direkt mit einem „P“ oder „E“ verbunden ist, verhält sich die M:1-Beziehung wie eine Suche. Andernfalls sind die standardmäßigen Denormalisierungsregeln zu befolgen.



## Schritt 2: XDM-Erlebnisereignistabellen identifizieren und beschriften

1. Identifizieren Sie alle Tabellen, die direkt mit den mit Erlebnisereignis gekennzeichneten Tabellen in Verbindung stehen (einen Sprung davon entfernt) und noch keine Beschriftung aufweisen. Markiere sie mit einem Stern.
1. Wenn Sie nur die Tabellen betrachten, die gerade mit einem Stern gekennzeichnet wurden, führen Sie die folgenden Aufgaben aus:
   1. **Beschriftung „B“ für Brückentabellen hinzufügen** - Eine Tabelle wird als Brückentabelle betrachtet, wenn zwei oder mehr Tabellen damit verknüpft sind, wobei die vielen Seiten der Beziehung auf die Brückentabelle zeigen
   2. **Beschriftung „D“ für zu denormalisierende Tabellen hinzufügen** - Jede Tabelle, die eine 1\:M- oder M:1-Kardinalität mit der beschrifteten Tabelle des XDM-Erlebnisereignisses aufweist und noch nicht markiert ist

>[!NOTE]
>
>Bridge-Tabellenregel speichern #1.
>
>Wenn eine Brückentabelle auftritt, die direkt mit einem „P“ oder „E“ verbunden ist, verhält sich die M:1-Beziehung wie eine Suche. Andernfalls sind die standardmäßigen Denormalisierungsregeln zu befolgen.



## Schritt 3: Lookup-Tabellen identifizieren und beschriften

1. Identifizieren Sie alle Tabellen, die mit einer der Suchtabellen mit der Bezeichnung, die noch keine Bezeichnung haben, in Verbindung stehen (es spielt keine Rolle, wie viele Hops Sie ausführen). Markieren Sie sie mit dem Stern &quot;**\***&quot;.
1. Wenn Sie nur die Tabellen betrachten, die gerade mit einem Stern gekennzeichnet wurden, führen Sie die folgenden Aufgaben aus:
   1. Hinzufügen einer Beschriftung **B** für Brückentabellen : Eine Tabelle wird als Brückentabelle betrachtet, wenn zwei oder mehr Tabellen damit verknüpft sind, wobei die vielen Seiten der Beziehung auf die Brückentabelle zeigen
   2. Fügen Sie eine Beschriftung &quot;**D**&quot; für Tabellen hinzu, die denormalisiert werden sollen - für jede Tabelle mit einer 1\:M- oder M:1-Kardinalität mit einer Lookup-Tabelle oder Brückentabelle, die mit einer Suche verbunden ist

>[!NOTE]
>
>Bridge-Tabellenregel speichern #1.
>
>Wenn eine Brückentabelle auftritt, die direkt mit einem „P“ oder „E“ verbunden ist, verhält sich die M:1-Beziehung wie eine Suche. Andernfalls folgen Sie den standardmäßigen Denormalisierungsregeln **(hint, hint)**



## Überprüfung

Im folgenden Video werden die richtigen D- und B-Kennzeichnungen für das Data Warehouse von Connection 5G und die Streaming-ERDs behandelt, einschließlich der Gründe, warum der Produkttyp eine denormalisierte Tabelle und keine Suche ist.

>[!VIDEO](https://video.tv.adobe.com/v/3459064/?quality=12&learn=on)
