---
title: "CA2231: Eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; all&#39;override di ValueType.Equals | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: Eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; all&#39;override di ValueType.Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di valore esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName>, ma non implementa l'operatore di uguaglianza.  
  
## Descrizione della regola  
 La maggior parte dei linguaggi di programmazione non prevede un'implementazione predefinita dell'operatore di uguaglianza \(\=\=\) per i tipi di valore.  Se il linguaggio di programmazione in uso supporta gli overload dell'operatore, è consigliabile implementare l'operatore di uguaglianza.  Il relativo comportamento dovrebbe essere identico a quello di <xref:System.Object.Equals%2A>.  
  
 Non è possibile utilizzare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza.  Questa operazione causerebbe un overflow dello stack.  Per implementare l'operatore di uguaglianza, utilizzare il metodo Object.Equals nell'implementazione.  Ad esempio:  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura; è tuttavia consigliabile fornire l'operatore di uguaglianza, se possibile.  
  
## Esempio  
 Nell'esempio riportato di seguito viene definito un tipo che viola questa regola.  
  
 [!CODE [FxCop.Usage.EqualsGetHashCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode#1)]  
  
## Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## Vedere anche  
 <xref:System.Object.Equals%2A?displayProperty=fullName>