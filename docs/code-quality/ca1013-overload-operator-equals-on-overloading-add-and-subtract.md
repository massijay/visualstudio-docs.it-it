---
title: "CA1013: Eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; all&#39;overload degli operatori di addizione e sottrazione | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: Eseguire l&#39;overload dell&#39;operatore &quot;uguale a&quot; all&#39;overload degli operatori di addizione e sottrazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Categoria|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.  
  
## Descrizione della regola  
 Se le istanze di un tipo possono essere combinate utilizzando operazioni quali l'addizione e la sottrazione è quasi sempre necessario definire l'uguaglianza in modo che restituisca `true` per due istanze aventi gli stessi valori costitutivi.  
  
 Non è possibile utilizzare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza.  Questa operazione causerebbe un overflow dello stack.  Per implementare l'operatore di uguaglianza, utilizzare il metodo Object.Equals nell'implementazione.  Vedere l'esempio che segue.  
  
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
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza affinché sia matematicamente coerente con gli operatori di addizione e sottrazione.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura quando l'implementazione predefinita dell'operatore di uguaglianza fornisce il comportamento corretto per il tipo.  
  
## Esempio  
 Nell'esempio riportato di seguito viene definito un tipo \(`BadAddableType`\) che viola questa regola.  Questo tipo deve implementare l'operatore di uguaglianza per fare sì che in caso due istanze presentino gli stessi valori di campo restituiscano `true` per l'uguaglianza.  Il tipo `GoodAddableType` presenta l'implementazione corretta.  Si noti che questo tipo implementa anche l'operatore di disuguaglianza ed esegue l'override di <xref:System.Object.Equals%2A> per soddisfare le altre regole.  Un'implementazione completa prevede anche l'implementazione di <xref:System.Object.GetHashCode%2A>.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene testata l'uguaglianza utilizzando istanze dei tipi definiti in precedenza in questo argomento per illustrare il comportamento predefinito e il comportamento corretto dell'operatore di uguaglianza.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Bad type:  {2,2} {2,2} are equal?  No**  
**Good type: {3,3} {3,3} are equal?  Yes**  
**Good type: {3,3} {3,3} are \=\= ?   Yes**  
**Bad type:  {2,2} {9,9} are equal?  No**  
**Good type: {3,3} {9,9} are \=\= ?   No**    
## Vedere anche  
 [Operatori di uguaglianza](../Topic/Equality%20Operators.md)