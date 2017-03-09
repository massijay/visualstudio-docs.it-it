---
title: "La risoluzione dell&#39;overload non &#232; riuscita perch&#233; nessun &#39;&lt;metodo&gt;&#39; accessibile &#232; specifico per questi argomenti: &lt;errore&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "errore di risoluzione"
  - "BC30521"
  - "risoluzione dell'overload non riuscita"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La risoluzione dell&#39;overload non &#232; riuscita perch&#233; nessun &#39;&lt;metodo&gt;&#39; accessibile &#232; specifico per questi argomenti: &lt;errore&gt;
È stata eseguita una chiamata a un metodo di overload, ma il compilatore ha trovato due o più overload con elenchi di parametri in cui è possibile convertire l'elenco di argomenti e non è in grado di effettuare una scelta.  
  
 Il compilatore tenta di far corrispondere il più possibile i tipi di dati nell'elenco di argomenti di chiamata all'elenco di parametri di overload. Sia che l'opzione di controllo del tipo \([Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) sia impostata su `On` oppure su `Off`, è necessaria una conversione verso un tipo di dati più grande da ciascun argomento al parametro corrispondente.  
  
 Se il compilatore trova più overload che soddisfano il requisito di conversione verso un tipo di dati più grande, cercherà quello più specifico per i tipi di dati degli argomenti, ovvero quello che richiede il minor grado di ampliamento. Questo messaggio di errore viene generato quando un overload è più specifico per il tipo di dati di un determinato argomento, mentre un altro overload è più specifico per il tipo di dati di un argomento diverso. Per altre informazioni e un esempio, vedere [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 **ID errore:** BC30521  
  
### Per correggere l'errore  
  
1.  Esaminare tutti gli overload del metodo per determinare quello che si vuole chiamare.  
  
2.  Fare in modo che nell'istruzione di chiamata i tipi di dati degli argomenti corrispondano a quelli dei parametri definiti per l'overload desiderato. Può essere necessario usare la [Funzione CType](/dotnet/visual-basic/language-reference/functions/ctype-function) per convertire uno o più tipi di dati nei tipi definiti.  
  
## Vedere anche  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Funzione CType](/dotnet/visual-basic/language-reference/functions/ctype-function)