---
title: "CA2220: I finalizzatori devono chiamare il finalizzatore della classe base | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: I finalizzatori devono chiamare il finalizzatore della classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo che esegue l'override di <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il metodo <xref:System.Object.Finalize%2A> nella relativa classe base.  
  
## Descrizione della regola  
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà.  A tale scopo, i tipi devono chiamare il metodo <xref:System.Object.Finalize%2A> della propria classe base dal proprio metodo <xref:System.Object.Finalize%2A>.  Il compilatore C\# aggiunge automaticamente la chiamata al finalizzatore della classe base.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare il metodo <xref:System.Object.Finalize%2A> del tipo di base dal metodo <xref:System.Object.Finalize%2A>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Alcuni compilatori destinati a Common Language Runtime inseriscono una chiamata al finalizzatore del tipo di base in Microsoft intermediate language \(MSIL\).  Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata ed è necessario aggiungerla nel codice.  
  
## Esempio  
 Nell'esempio di Visual Basic illustrato di seguito viene illustrato un tipo `TypeB` che chiama correttamente il metodo <xref:System.Object.Finalize%2A> nella relativa classe base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## Vedere anche  
 [Modello Dispose](../Topic/Dispose%20Pattern.md)