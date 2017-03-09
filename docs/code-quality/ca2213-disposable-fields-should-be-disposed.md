---
title: "CA2213: I campi Disposable devono essere eliminati | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: I campi Disposable devono essere eliminati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> dichiara i campi di tipi che implementano anch'essi <xref:System.IDisposable>.  Il metodo <xref:System.IDisposable.Dispose%2A> del campo non viene chiamato dal metodo <xref:System.IDisposable.Dispose%2A> del tipo dichiarante.  
  
## Descrizione della regola  
 Un tipo è responsabile dell'eliminazione di tutte le risorse non gestite. Questa operazione viene eseguita mediante l'implementazione di <xref:System.IDisposable>.  Questa regola controlla se un tipo Disposable `T` dichiara un campo `F` costituito da un'istanza di un tipo Disposable `FT`.  Per ogni campo `F`, la regola tenta di individuare una chiamata a `FT.Dispose`.  La regola cerca i metodi chiamati da `T.Dispose` e il livello inferiore \(metodi chiamati da metodi chiamati da `FT.Dispose`\).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> su campi di tipi che implementano <xref:System.IDisposable> se si è responsabili dell'allocazione e del rilascio delle risorse non gestite contenute in un campo.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se non si è responsabili del rilascio della risorsa contenuta dal campo o se la chiamata a <xref:System.IDisposable.Dispose%2A> viene effettuata a un livello di chiamata più profondo rispetto a quanto controllato dalla regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable> \(`FT` nella spiegazione precedente\).  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo `TypeB` che viola la regola dichiarando un campo `aFieldOfADisposableType` \(`F` nella spiegazione precedente\) come tipo Disposable \(`TypeA`\) e non chiamando <xref:System.IDisposable.Dispose%2A> sul campo.  `TypeB` corrisponde a `T` nella spiegazione precedente.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)