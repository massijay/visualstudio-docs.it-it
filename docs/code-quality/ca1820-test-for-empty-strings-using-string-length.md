---
title: "CA1820: Testare le stringhe vuote utilizzando la lunghezza di stringa | Microsoft Docs"
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
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1820: Testare le stringhe vuote utilizzando la lunghezza di stringa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Una stringa viene confrontata con la stringa vuota mediante <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descrizione della regola  
 Il confronto di stringhe mediante la proprietà <xref:System.String.Length%2A?displayProperty=fullName> o il metodo <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> è notevolmente più veloce rispetto all'utilizzo di <xref:System.Object.Equals%2A>.  <xref:System.Object.Equals%2A> infatti esegue un numero di istruzioni MSIL maggiore rispetto al metodo <xref:System.String.IsNullOrEmpty%2A> o al numero di istruzioni eseguite per recuperare il valore della proprietà <xref:System.String.Length%2A> e confrontarlo con zero.  
  
 Occorre tenere presente che <xref:System.Object.Equals%2A> e <xref:System.String.Length%2A> \=\= 0 presentano comportamenti diversi per le stringhe null.  Se si tenta di ottenere il valore della proprietà <xref:System.String.Length%2A> su una stringa null, in Common Language Runtime viene generata un'eccezione <xref:System.NullReferenceException?displayProperty=fullName>.  Se si esegue un confronto tra una stringa null e la stringa vuota, in Common Language Runtime non viene generata un'eccezione e il confronto restituisce `false`.  Il test per null non incide in modo significativo sulle prestazioni relative di questi due approcci.  Quando la destinazione è [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare il metodo <xref:System.String.IsNullOrEmpty%2A>.  In caso contrario utilizzare il confronto <xref:System.String.Length%2A> \=\= quando possibile.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il confronto in modo che utilizzi la proprietà <xref:System.String.Length%2A> ed esegua il test per la stringa null.  Se la destinazione è [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare il metodo <xref:System.String.IsNullOrEmpty%2A>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se le prestazioni non sono importanti.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate le diverse tecniche utilizzate per cercare una stringa vuota.  
  
 [!code-cs[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]