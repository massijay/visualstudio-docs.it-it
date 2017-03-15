---
title: "Option Strict On non consente conversioni implicite da &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On non consente conversioni implicite da &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39;
Si è provato a convertire un tipo in un altro tipo che potrebbe non essere in grado di contenere il valore, ad esempio da un tipo `Long` a un tipo `Integer`, mentre l'opzione di controllo del tipo \([Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) è impostata su `On`.  
  
 Questa conversione viene chiamata *conversione verso un tipo di dati più piccolo* e può non riuscire in fase di esecuzione. Per questo motivo, `Option Strict On` non consente le conversioni implicite verso un tipo di dati più piccolo.  
  
 **ID errore:** BC30512  
  
### Per correggere l'errore  
  
1.  Determinare se esiste una conversione di qualsiasi tipo da `<type1>` a `<type2>`. Se entrambi sono tipi elementari di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o sono entrambi istanze di classi, in genere è possibile determinare questo aspetto consultando la tabella in [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
2.  Se esiste solo una conversione verso un tipo di dati più piccolo da `<type1>` a `<type2>`, è consigliabile usare il cast esplicito. Le parole chiave [Funzione CType](/dotnet/visual-basic/language-reference/functions/ctype-function) e [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator) generano un'eccezione in fase di esecuzione se la conversione non riesce. La parola chiave [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator) si applica solo ai tipi riferimento e restituisce [Nothing](/dotnet/visual-basic/language-reference/nothing) se la conversione non riesce.  
  
3.  Se esiste una conversione verso un tipo di dati più piccolo e il programma può tollerare un errore in fase di esecuzione oppure si ritiene che un errore in fase di esecuzione sia improbabile, è possibile specificare `Option Strict Off` all'inizio del codice sorgente. È tuttavia necessario inserire la conversione in un blocco [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) per evitare risultati imprevisti o una terminazione anticipata del programma.  
  
4.  Se non esiste alcuna conversione da `<type1>` a `<type2>`, è necessario rivalutare la logica del programma. Potrebbe essere possibile scrivere codice in grado di assegnare valori a `<type2>` corrispondenti ai valori previsti di `<type1>`.  
  
5.  Se non esiste alcuna conversione da `<type1>` a `<type2>` e uno dei tipi è una classe o una struttura definita, potrebbe essere possibile definire un operatore di conversione da questo tipo all'altro tipo o viceversa. Per altre informazioni, vedere [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md).  
  
6.  In tutti i casi e come indicazione generale, è consigliabile evitare di usare le conversioni verso un tipo di dati più piccolo, a meno che non sia possibile inserire gli errori in un blocco `Catch` e gestirli in modo efficace.  
  
## Vedere anche  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Funzione CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)