---
title: "CA0143: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA0143: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che utilizza un tipo di indice diverso da <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> o <xref:System.String?displayProperty=fullName>.  
  
## Descrizione della regola  
 Gli indicizzatori, ossia proprietà indicizzate, devono utilizzare tipi integer o string per l'indice.  Questi tipi sono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'utilizzabilità della libreria.  L'utilizzo del tipo <xref:System.Object> deve essere limitato ai casi in cui non è possibile specificare in fase di progettazione il tipo integer o string specifico.  Se la progettazione richiede altri tipi per l'indice, valutare se il tipo rappresenta un archivio dati logico.  In caso contrario, utilizzare un metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare l'indice in un tipo integer o string oppure utilizzare un metodo anziché l'indicizzatore.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo dopo aver considerato attentamente la necessità di un indicizzatore non standard.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un indicizzatore che utilizza un indice <xref:System.Int32>.  
  
 [!code-cs[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## Regole correlate  
 [CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)