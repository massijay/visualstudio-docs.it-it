---
title: "CA1011: Considerare il passaggio di tipi di base come parametri | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1011: Considerare il passaggio di tipi di base come parametri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Una dichiarazione di metodo include un parametro formale costituito da un tipo derivato e il metodo chiama solo membri del tipo di base del parametro.  
  
## Descrizione della regola  
 Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente.  Quando l'argomento viene utilizzato all'interno del corpo del metodo, il metodo specifico che viene eseguito dipende dal tipo dell'argomento.  Se la funzionalità aggiuntiva fornita dal tipo derivato non è richiesta, l'utilizzo del tipo di base consente un utilizzo più esteso del metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo del parametro nel relativo tipo di base.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura  
  
-   se il metodo richiede la funzionalità specifica fornita dal tipo derivato  
  
     \- oppure \-  
  
-   per imporre di passare al metodo solo il tipo derivato o un tipo più derivato.  
  
 In questi casi, il codice sarà più sicuro grazie al rigido controllo dei tipi fornito dal compilatore e dal runtime.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato il metodo `ManipulateFileStream`, che può essere utilizzato solo con un oggetto <xref:System.IO.FileStream>, il quale viola la regola.  Un secondo metodo, `ManipulateAnyStream`, soddisfa la regola sostituendo il parametro <xref:System.IO.FileStream> mediante un oggetto <xref:System.IO.Stream>.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Regole correlate  
 [CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)