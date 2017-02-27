---
title: "CA1009: Dichiarare correttamente i gestori eventi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1009: Dichiarare correttamente i gestori eventi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un delegato che gestisce un evento pubblico o protetto non dispone della firma, del tipo restituito o dei nomi di parametri corretti.  
  
## Descrizione della regola  
 I metodi di gestione eventi accettano due parametri.  Il primo è di tipo <xref:System.Object?displayProperty=fullName> ed è denominato "sender".  Corrisponde all'oggetto che ha generato l'evento.  Il secondo parametro è di tipo <xref:System.EventArgs?displayProperty=fullName> ed è denominato "e".  Questi sono i dati associati all'evento.  Se ad esempio l'evento viene generato ogni volta che viene aperto un file, i dati dell'evento conterranno il nome del file.  
  
 I metodi di gestione eventi non devono restituire un valore.  Nel linguaggio di programmazione C\#, viene indicato dal tipo restituito `void`.  Un gestore eventi può richiamare più metodi in più oggetti.  Se ai metodi fosse consentito restituire un valore, sarebbero presenti più valori restituiti per ogni evento e solo il valore dell'ultimo metodo richiamato sarebbe disponibile.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o i nomi di parametri del delegato.  Per informazioni dettagliate, vedere l'esempio riportato di seguito.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio seguente viene illustrato un delegato adatto per la gestione di eventi.  I metodi che possono essere richiamati da questo gestore dell'evento sono conformi alla firma specificata nelle Linee guida di progettazione.  `AlarmEventHandler` è il nome del tipo del delegato.  `AlarmEventArgs` deriva dalla classe base per i dati degli eventi, <xref:System.EventArgs>, e contiene i dati degli eventi di allarme.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Regole correlate  
 [CA2109: Controllare i gestori di eventi visibili](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## Vedere anche  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Eventi e delegati](http://msdn.microsoft.com/it-it/d98fd58b-fa4f-4598-8378-addf4355a115)