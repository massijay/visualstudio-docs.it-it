---
title: "Ca1003: Utilizzare istanze di gestori eventi generici | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseGenericEventHandlerInstances"
  - "CA1003"
helpviewer_keywords: 
  - "CA1003"
  - "UseGenericEventHandlerInstances"
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ca1003: Utilizzare istanze di gestori eventi generici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo contiene un delegato che restituisce un tipo void, la cui firma contiene due parametri \(il primo è un oggetto e il secondo un tipo assegnabile a EventArgs\) e l'assembly che lo contiene è destinato a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Descrizione della regola  
 Prima di [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], per passare informazioni personalizzate al gestore eventi era necessario dichiarare un nuovo delegato che specificasse una classe derivata dalla classe <xref:System.EventArgs?displayProperty=fullName>.  In [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], con l'introduzione del delegato <xref:System.EventHandler%601?displayProperty=fullName>, non è più necessario.  Questo delegato generico consente di utilizzare con il gestore dell'evento tutte le classi derivate da <xref:System.EventArgs>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituirne l'utilizzo con il delegato <xref:System.EventHandler%601?displayProperty=fullName>.  Se il delegato viene generato automaticamente dal compilatore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], modificare la sintassi della dichiarazione di evento per utilizzare il delegato <xref:System.EventHandler%601?displayProperty=fullName>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un delegato che viola la regola.  Nell'esempio [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i commenti descrivono la procedura per modificare l'esempio in modo che soddisfi la regola.  Per l'esempio nel linguaggio C\#, di seguito è riportato un esempio che illustra il codice modificato.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-cs[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## Esempio  
 Nell'esempio seguente viene rimossa la dichiarazione del delegato dall'esempio precedente, che soddisfa la regola, e ne viene sostituito l'utilizzo nei metodi `ClassThatRaisesEvent` e `ClassThatHandlesEvent` con il delegato <xref:System.EventHandler%601?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## Regole correlate  
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Vedere anche  
 [Generics](/dotnet/csharp/programming-guide/generics/index)