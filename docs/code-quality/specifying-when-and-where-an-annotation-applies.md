---
title: "Specificare dove e quando applicare un&#39;annotazione | Microsoft Docs"
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
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Specificare dove e quando applicare un&#39;annotazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando un'annotazione è condizionale, può richiedere ad altre annotazioni di specificarlo all'analizzatore.  Ad esempio, se una funzione dispone di una variabile che può essere sincrona o asincrona, la funzione si comporta nel modo seguente: Nel caso sincrono ha sempre eventualmente esito positivo, ma in modo asincrono viene segnalato un errore se potrebbe non riuscire immediatamente.  Quando la funzione viene chiamata in modo sincrono, controllare il valore di ritorno non fornisce alcun valore per l'analizzatore di codice, perché potrebbe non avere restituito alcun valore.  Tuttavia, quando la funzione viene chiamata in modo asincrono e il risultato della funzione non è controllato, un errore grave può verificarsi.  In questo esempio viene illustrata una situazione in cui è possibile utilizzare l'annotazione `_When_` —descritta più avanti in questo articolo—per abilitate il controllo.  
  
## Annotazioni strutturali  
 Per controllare quando e dove le annotazioni vengono applicate, utilizzare le annotazioni strutturali seguenti.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` è un'espressione che produce un lvalue.  Le annotazioni in `anno-list` si applicano all'oggetto denominato da `expr`.  Ciascuna annotazione in `anno-list`, `expr` verrà interpretata in pre\-condizione se la voce viene interpretata in pre\-condizione ed in post\-condizione se la voce viene interpretata in post\-condizione.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` è un'espressione che produce un lvalue.  Le annotazioni in `anno-list` si applicano all'oggetto denominato da `expr`.  Ciascuna annotazione in `anno-list`, `expr` verrà interpretata in pre\-condizione se la voce viene interpretata in precondizione ed in post\-condizione se la voce viene interpretata in post\-condizione.<br /><br /> `iter` è il nome di una variabile con ambito annotazione \(incluso `anno-list`\).  `iter` ha un tipo implicito `long`.  Le variabili denominate identicamente, in qualsiasi ambito che lo contiene, sono nascoste dalla valutazione.<br /><br /> `elem-count` è un'espressione che restituisce un Integer.|  
|`_Group_(anno-list)`|Le annotazioni in `anno-list` dovrebbero contenere tutte qualche qualificatore che vale per il gruppo di annotazioni, applicato ad ogni annotazione.|  
|`_When_(expr, anno-list)`|`expr` è un'espressione che può essere convertita in `bool`.  Quando sono diverse da zero \(`true`\), le annotazioni specificate in `anno-list` sono considerate applicabili.<br /><br /> Per impostazione predefinita, per ciascuna annotazione in `anno-list`, `expr` viene interpretato utilizzando i valori di input se l'annotazione è una precondizione, e i valori di output se l'annotazione è una post\-condizione.  Per eseguire l'override dell'impostazione predefinita, è possibile utilizzare `_Old_` intrinsecamente quando viene valutata una post\-condizione per indicare che i valori immessi devono essere utilizzati. **Note:**  Diverse annotazioni potrebbero essere abilitate come conseguenza dell'utilizzo di `_When_` se è coinvolto un valore mutabile—ad esempio, `*pLength`—poiché il risultato di valutazione di `expr` in precondizione, può essere diverso da quello valutato in post\-condizione.|  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)