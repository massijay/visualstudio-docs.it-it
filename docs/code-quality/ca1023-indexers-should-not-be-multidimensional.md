---
title: "CA1023: Gli indicizzatori non devono essere multidimensionali | Microsoft Docs"
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
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1023: Gli indicizzatori non devono essere multidimensionali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto contiene un indicizzatore pubblico o protetto che utilizza più di un indice.  
  
## Descrizione della regola  
 Gli indicizzatori, ossia proprietà indicizzate, devono utilizzare un unico indice.  Gli indicizzatori multidimensionali possono ridurre sensibilmente l'utilizzabilità della libreria.  Se la progettazione richiede più indici, valutare se il tipo rappresenta un archivio dati logico.  In caso contrario, utilizzare un metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la progettazione per utilizzare un solo Integer o indice di stringa oppure utilizzare un metodo anziché l'indicizzatore.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo dopo aver considerato attentamente la necessità di un indicizzatore non standard.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo, `DayOfWeek03`, con un indicizzatore multidimensionale che viola la regola.  L'indicizzatore può essere considerato come un tipo di conversione e pertanto è esposto come un metodo in modo più appropriato.  Il tipo è riprogettato in `RedesignedDayOfWeek03` per soddisfare la regola.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Regole correlate  
 [CA0143: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)