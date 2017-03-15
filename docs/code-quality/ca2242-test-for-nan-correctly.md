---
title: "CA2242: Testare i valori NaN in modo corretto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242: Testare i valori NaN in modo corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'espressione testa un valore in base a <xref:System.Single.Nan?displayProperty=fullName> o a <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Descrizione della regola  
 <xref:System.Double.NaN?displayProperty=fullName>, che rappresenta un valore non numerico, viene restituito quando un'operazione aritmetica non è definita.  Le espressioni che testano l'uguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituiscono sempre `false`.  Le espressioni che testano la disuguaglianza tra un valore e <xref:System.Double.NaN?displayProperty=fullName> restituiscono sempre `true`.  
  
## Come correggere le violazioni  
 Per risolvere una violazione di questa regola e determinare accuratamente se un valore rappresenta <xref:System.Double.NaN?displayProperty=fullName>, testare il valore utilizzando <xref:System.Single.IsNan%2A?displayProperty=fullName> o <xref:System.Double.IsNan%2A?displayProperty=fullName>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate due espressioni che erroneamente testano un valore in base a <xref:System.Double.NaN?displayProperty=fullName> e un'espressione che utilizza correttamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> per testare il valore.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]