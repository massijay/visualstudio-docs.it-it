---
title: "Funzioni intrinseche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Funzioni intrinseche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un'espressione in SAL può essere un'espressione C\/C\+\+ a condizione che sia un'espressione che non ha effetti collaterali— ad esempio, \+\+, \-\- e le chiamate di funzione tutte hanno effetti collaterali in questo contesto.  Tuttavia, SAL fornisce alcuni oggetti del tipo di funzione e alcuni simboli privati che possono essere utilizzati nelle espressioni SAL.  Esse sono denominate *funzioni intrinseche*.  
  
## Utilizzo generale  
 Le annotazioni intrinseche di funzione forniscono l'utilità generale per l'utilizzo di SAL.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Curr_`|Sinonimo dell'oggetto attualmente annotato.  Quando viene utilizzata l'annotazione `_At_`, `_Curr_` è identica al primo parametro di `_At_`.  In caso contrario, è il parametro o l'intera funzione\/valore restituito con cui l'annotazione è lessicalmente associata.|  
|`_Inexpressible_(expr)`|Esprime una situazione in cui la dimensione di un buffer è troppo complessa per essere rappresentata con un'espressione di annotazione, ad esempio quando viene calcolata esaminando un set di dati di input e successivamente contando i membri selezionati.|  
|`_Nullterm_length_(param)`|`param` è il numero di elementi nel buffer fino a un terminatore null, non incluso.  Può essere applicato a un qualsiasi buffer che contenga tipi non aggregati e non void.|  
|`_Old_(expr)`|Una volta valutato nella precondizione, `_Old_` restituisce il valore di input `expr`.  Una volta valutato nella post condizione, restituisce il valore `expr` come sarebbe stato valutato nella precondizione|  
|`_Param_(n)`|Il parametro `n`\-esimo di una funzione, contando da 1 a `n`, e `n` è una costante integrale letterale.  Se il parametro è denominato, questa annotazione ha lo stesso effetto di accedere al parametro per nome. **Note:**  `n` può fare riferimento ai parametri posizionali definiti dai puntini di sospensione, oppure potrebbe essere utilizzato in prototipi di funzioni in cui i nomi non vengono utilizzati.|  
|`return`|La parola chiave riservata `return` di C\/C\+\+ può essere utilizzata in un'espressione SAL per indicare il valore restituito di una funzione.  Il valore è disponibile solo nello stato di post; è un errore di sintassi utilizzarlo in uno stato di pre.|  
  
## Specifico di una stringa  
 Le seguenti annotazioni di funzione intrinseca abilitano la modifica delle stringhe.  Tutte e quattro queste funzioni presentano lo stesso scopo: per restituire il numero di elementi del tipo trovato prima di un terminatore null.  Le differenze sono i tipi di dati negli elementi a cui fanno riferimento.  Si noti che se si desidera specificare la lunghezza del buffer con terminazione null che non è composto da caratteri, utilizzare l'annotazione di `_Nullterm_length_(param)` dalla sezione precedente.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_String_length_(param)`|`param` è il numero di elementi nella stringa fino a un terminatore null, non incluso.  Questa voce è riservata per i tipi di carattere stringa\-di\-caratteri.|  
|`strlen(param)`|`param` è il numero di elementi nella stringa fino a un terminatore null, non incluso.  Questa annotazione è riservata all'utilizzo sugli array di caratteri ed è similare alla funzione runtime del C [strlen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param` è il numero di elementi nella stringa fino a un terminatore null, non incluso.  Questa annotazione è riservata all'utilizzo sugli array di caratteri wide ed è similare alla funzione runtime del C [wcslen\(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)