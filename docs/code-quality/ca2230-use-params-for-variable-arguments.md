---
title: "CA2230: Utilizzare params per argomenti variabili | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: Utilizzare params per argomenti variabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto contiene un metodo pubblico o protetto che utilizza la convenzione di chiamata `VarArgs`.  
  
## Descrizione della regola  
 La convenzione di chiamata `VarArgs` viene utilizzata con determinate definizioni di metodi che accettano un numero variabile di parametri.  Un metodo che utilizza la convezione di chiamata `VarArgs` non è conforme a CLS \(Common Language Specification\) e potrebbe non essere accessibile tra i diversi linguaggi di programmazione.  
  
 In C\#, la convenzione di chiamata `VarArgs` viene utilizzata quando l'elenco di parametri di un metodo termina con la parola chiave `__arglist`.  In Visual Basic la convenzione di chiamata `VarArgs` non è supportata e Visual C\+\+ ne consente l'utilizzo solo nel codice non gestito che utilizza la notazione dei puntini di sospensione `...`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola in C\#, utilizzare la parola chiave [params](/dotnet/csharp/language-reference/keywords/params) anziché `__arglist`.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati due metodi, uno che viola la regola e uno che la soddisfa.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## Vedere anche  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)