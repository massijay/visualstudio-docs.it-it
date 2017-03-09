---
title: "La variabile &#39;&lt;nomevariabile&gt;&#39; &#232; stata passata per riferimento prima dell&#39;assegnazione di un valore | Microsoft Docs"
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
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variabile &#39;&lt;nomevariabile&gt;&#39; &#232; stata passata per riferimento prima dell&#39;assegnazione di un valore
La variabile '\<nomevariabile\>' è stata passata per riferimento prima dell'assegnazione di un valore. È possibile che in fase di esecuzione venga restituita un'eccezione dovuta a un riferimento Null.  
  
 Una chiamata di routine passa una variabile come argomento a un parametro `ByRef` prima dell'assegnazione di qualsiasi valore alla variabile.  
  
 Se a una variabile non è mai stato assegnato alcun valore, questa manterrà il valore predefinito per il tipo di dati. Per un tipo di dati di riferimento, il valore predefinito è [Nothing](/dotnet/visual-basic/language-reference/nothing). La lettura di una variabile di riferimento con un valore `Nothing` può causare un'eccezione <xref:System.NullReferenceException> in alcune circostanze.  
  
 Il passaggio di un argomento a una routine `ByRef` espone la variabile sottostante all'argomento a possibili modifiche da parte della routine.  
  
 Per impostazione predefinita, si tratta di un messaggio di avviso. Per altre informazioni su come nascondere gli avvisi o considerarli come errori, vedere [Configurazione degli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID errore:** BC42030  
  
### Per correggere l'errore  
  
-   Se si vuole che la routine assegni un valore alla variabile attraverso l'argomento `ByRef` e se il fatto che la variabile contiene già un valore non è importante, non è necessaria alcuna operazione.  
  
-   Se la logica presente nella routine legge l'argomento prima di assegnargli un valore e se la variabile è un tipo valore, accertarsi che la logica della routine non dipenda dalla presenza di un valore predefinito nella variabile.  
  
-   Se la logica della routine legge l'argomento prima di assegnargli un valore e se la variabile è un tipo riferimento, accertarsi che la logica della routine sia in grado di gestire un valore di `Nothing`. Potrebbe ad esempio usare un'istruzione [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) per intercettare un'eccezione <xref:System.NullReferenceException>.  
  
## Vedere anche  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Dichiarazione di variabili](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Risoluzione dei problemi relativi alle variabili](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)