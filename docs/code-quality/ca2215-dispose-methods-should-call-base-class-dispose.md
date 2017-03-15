---
title: "CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: I metodi Dispose devono chiamare il metodo Dispose della classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo che implementa <xref:System.IDisposable?displayProperty=fullName> eredita da un tipo che implementa anch'esso <xref:System.IDisposable>.  Il metodo <xref:System.IDisposable.Dispose%2A> del tipo che eredita non chiama il metodo <xref:System.IDisposable.Dispose%2A> del tipo padre.  
  
## Descrizione della regola  
 Se un tipo eredita da un tipo Disposable, deve chiamare il metodo <xref:System.IDisposable.Dispose%2A> del tipo di base dall'interno del proprio metodo <xref:System.IDisposable.Dispose%2A>.  Chiamando il metodo del tipo di base Elimina si garantisce che tutte le risorse create dal tipo di base vengano rilasciate.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare `base`.<xref:System.IDisposable.Dispose%2A> nel metodo <xref:System.IDisposable.Dispose%2A>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se la chiamata a `base`.<xref:System.IDisposable.Dispose%2A> viene effettuata a un livello di chiamata più profondo rispetto a quanto controllato dalla regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo `TypeA` che implementa <xref:System.IDisposable>.  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo `TypeB` che eredita da `TypeA` e chiama correttamente il relativo metodo <xref:System.IDisposable.Dispose%2A>.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## Vedere anche  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)