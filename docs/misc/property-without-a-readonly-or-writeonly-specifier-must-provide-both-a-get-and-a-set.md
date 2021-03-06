---
title: "Una propriet&#224; senza identificatore &#39;ReadOnly&#39; o &#39;WriteOnly&#39; deve fornire sia un elemento &#39;Get&#39; che un elemento &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una propriet&#224; senza identificatore &#39;ReadOnly&#39; o &#39;WriteOnly&#39; deve fornire sia un elemento &#39;Get&#39; che un elemento &#39;Set&#39;
Se una proprietà non è dichiarata come `ReadOnly` o `WriteOnly`, deve fornire le routine per la lettura e scrittura del proprio valore.  
  
 **ID errore:** BC30124  
  
### Per correggere l'errore  
  
1.  Assicurarsi di includere sia una routine `Get` che una routine `Set` tra l'istruzione `Property` e l'istruzione `End Property`.  
  
2.  Verificare che le altre routine all'interno della dichiarazione `Property` vengano terminate correttamente.  
  
## Vedere anche  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)