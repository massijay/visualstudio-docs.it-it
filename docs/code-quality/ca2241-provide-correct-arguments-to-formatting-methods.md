---
title: "CA2241: Fornire argomenti corretti ai metodi di formattazione | Microsoft Docs"
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
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2241: Fornire argomenti corretti ai metodi di formattazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Categoria|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 L'argomento stringa `format` passato a un metodo quale <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> o <xref:System.String.Format%2A?displayProperty=fullName> non contiene un elemento di formato corrispondente a ogni argomento dell'oggetto o viceversa.  
  
## Descrizione della regola  
 Gli argomenti per metodi quali <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.String.Format%2A> sono costituiti da una stringa di formato seguita da diverse istanze di <xref:System.Object?displayProperty=fullName>.  La stringa di formato è costituita da testo e da elementi di formato incorporati nella forma {index\[,alignment\]\[:formatString\]}. 'index' è un intero in base zero che indica quali oggetti sono da formattare.  Se un oggetto non presenta un indice corrispondente nella stringa di formato, tale oggetto viene ignorato.  Se l'oggetto specificato da "index" non esiste, in fase di esecuzione verrà generata un'eccezione <xref:System.FormatException?displayProperty=fullName>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, fornire un elemento di formato per ogni argomento di oggetto e un argomento di oggetto per ogni elemento di formato.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate due violazioni di questa regola.  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-cs[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]