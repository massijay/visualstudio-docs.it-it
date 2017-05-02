---
title: "Istruzione &#39;return&#39; esterna alla funzione | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Istruzione &#39;return&#39; esterna alla funzione
È stata utilizzata un'istruzione `return` nell'ambito globale del codice.  L'istruzione `return` deve essere visualizzata solo nel corpo di una funzione.  
  
 Il richiamo di una funzione con l'operatore `()` rappresenta un'espressione.  Tutte le espressioni presentano valori. L'istruzione `return` viene utilizzata per specificare il valore restituito da una funzione.  La forma generale è la seguente:  
  
```  
  
return [ expression ];  
```  
  
 Quando l'istruzione `return` viene eseguita, viene valutato e restituito il valore della funzione *expression*.  Se non è presente alcuna espressione, viene restituito **undefined**.  
  
 L'esecuzione della funzione viene arrestata quando viene eseguita l'istruzione `return`, anche se nel corpo della funzione compaiono ancora altre istruzioni.  Questa regola non viene applicata nel caso in cui l'istruzione **return** compaia all'interno di un blocco **try** ed esista un corrispondente blocco **finally**. In questo caso, infatti, il blocco **finally** verrà eseguito prima del termine della funzione.  
  
 Se viene restituita una funzione perché raggiunge la fine del corpo della funzione senza eseguire un'istruzione `return`, il valore restituito è il valore **undefined**, ovvero il risultato della funzione non può essere utilizzato come parte di un'espressione più estesa.  
  
### Per correggere l'errore  
  
-   Rimuovere l'istruzione `return` dal corpo principale del codice \(l'ambito globale\).  
  
## Vedere anche  
 [Istruzione return](../../javascript/reference/return-statement-javascript.md)   
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà caller \(Function\)](../../javascript/reference/caller-property-function-javascript.md)