---
title: "CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Category|Microsoft.Interoperability|  
|Breaking Change|DependsOnFix|  
  
## Causa  
 Un tipo visibile a COM \(Component Object Model\) deriva da un tipo non visibile a COM.  
  
## Descrizione della regola  
 Quando un tipo visibile a COM aggiunge membri in una nuova versione, deve attenersi a severe linee guida per evitare di compromettere la funzionalità di client COM associati alla versione corrente.  Un tipo invisibile a COM presuppone che non sia necessario rispettare tali regole per la creazione di versioni COM durante l'aggiunta di nuovi membri.  Se, tuttavia, un tipo visibile a COM deriva dal tipo invisibile a COM ed espone un'interfaccia di classe <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> \(l'impostazione predefinita\), tutti i membri pubblici del tipo base, a meno che non siano specificatamente contrassegnati come invisibili a COM, con evidente ridondanza, sono esposti a COM.  Se il tipo base aggiunge nuovi membri in una versione successiva, potrebbe essere compromessa la funzionalità di tutti i client COM associati all'interfaccia di classe del tipo derivato.  Per ridurre la possibilità di compromettere la funzionalità dei client COM, è necessario che i tipi visibili a COM derivino solo da tipi visibili a COM.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere i tipi di base visibili a COM o il tipo derivato invisibile a COM.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## Vedere anche  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/it-it/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)