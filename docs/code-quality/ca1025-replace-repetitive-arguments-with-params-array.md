---
title: "Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri | Microsoft Docs"
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
  - "CA1025"
  - "ReplaceRepetitiveArgumentsWithParamsArray"
helpviewer_keywords: 
  - "ReplaceRepetitiveArgumentsWithParamsArray"
  - "CA1025"
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta più di tre parametri e i relativi ultimi tre parametri sono dello stesso tipo.  
  
## Descrizione della regola  
 Utilizzare una matrice di parametri anziché argomenti ripetuti quando non si conosce il numero esatto di argomenti e gli argomenti variabili sono, o possono essere passati, dello stesso tipo.  Ad esempio, il metodo <xref:System.Console.WriteLine%2A> fornisce un overload di scopo generale che utilizza una matrice di parametri per accettare qualsiasi numero di argomenti <xref:System.Object>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire gli argomenti ripetuti con una matrice di parametri.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sempre sicura, tuttavia questa progettazione potrebbe causare problemi di utilizzabilità.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-cs[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]