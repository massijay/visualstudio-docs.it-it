---
title: 'CA2220: I finalizzatori devono chiamare il finalizzatore di classe di base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa5ed3329d4168a0781243a4faf021de3488e77c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: I finalizzatori devono chiamare il finalizzatore della classe base
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Un tipo che esegue l'override <xref:System.Object.Finalize%2A?displayProperty=fullName> non chiama il <xref:System.Object.Finalize%2A> metodo nella classe base.  
  
## <a name="rule-description"></a>Descrizione della regola  
 La finalizzazione deve essere propagata tramite la gerarchia di ereditarietà. A tale scopo, i tipi devono chiamare la relativa classe base <xref:System.Object.Finalize%2A> metodo all'interno di propri <xref:System.Object.Finalize%2A> metodo. Il compilatore c# aggiunge automaticamente la chiamata al finalizzatore della classe base.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Object.Finalize%2A> metodo i <xref:System.Object.Finalize%2A> metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Alcuni compilatori destinati a common language runtime inserire una chiamata al finalizzatore del tipo di base in Microsoft intermediate language (MSIL). Se viene segnalato un avviso da questa regola, il compilatore non inserisce la chiamata e aggiungerla al codice.  
  
## <a name="example"></a>Esempio  
 L'esempio di Visual Basic seguente mostra un tipo `TypeB` che chiama correttamente la <xref:System.Object.Finalize%2A> metodo nella classe base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)