---
title: "Annotazione del comportamento delle funzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Annotazione del comportamento delle funzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Oltre ad annotare [parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md), è possibile annotare le proprietà dell'intera funzione.  
  
## Annotazioni di funzione  
 Le seguenti annotazioni si applicano all'intera funzione e descrivono come si comporta o cosa si aspetta per essere true.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Called_from_function_class_(name)`|Non inteso singolarmente; invece, è un predicato da utilizzare con l'annotazione `_When_`.  Per ulteriori informazioni, vedere [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Il parametro `name` è una stringa arbitraria che appare in un'annotazione di `_Function_class_` nella dichiarazione di funzioni. Restituisce `_Called_from_function_class_` diverso da zero se la funzione attualmente analizzata viene annotata con `_Function_class_` che ha lo stesso valore di `name`; in caso contrario, restituisce zero.|  
|`_Check_return_`|Annota un valore restituito e dichiara che il chiamante dovrebbe esaminarlo.  Il verificatore segnala un errore se la funzione viene chiamata in un contesto void.|  
|`_Function_class_(name)`|Il parametro `name` è una stringa arbitraria definita dall'utente.  Esiste in uno spazio dei nomi distinto da tutti gli altri spazi dei nomi.  Una funzione, il puntatore a funzione, o—più utilmente— un tipo puntatore a funzione possono essere definiti come appartenenti a una o più classi di funzione.|  
|`_Raises_SEH_exception_`|Annota una funzione che solleva sempre una gestione strutturata delle eccezioni, soggetta alle condizioni `_When_` e `_On_failure_`.  Per ulteriori informazioni, vedere [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Annota una funzione che può eventualmente sollevare un eccezione SEH, soggetta alle condizioni `_When_` e `_On_failure_`.|  
|`_Must_inspect_result_`|Annota un qualsiasi valore di output, compreso il valore restituito, i parametri e i globals.  L'analizzatore segnala un errore se il valore dell'oggetto annotato non è controllato in seguito. "L'ispezione" include se è utilizzata in un'espressione condizionale, viene assegnata a un parametro di output o globale, o passata come parametro.  Per i valori restituiti, `_Must_inspect_result_` implica `_Check_return_`.|  
|`_Use_decl_annotations_`|Può essere utilizzato in una definizione di funzione \(nota anche come corpo della funzione\) anziché l'elenco delle annotazioni nell'intestazione. Quando `_Use_decl_annotations_` viene utilizzato, le annotazioni visualizzate su un'intestazione nell'ambito per la stessa funzione vengono utilizzate come se fossero inoltre presenti nella definizione con l'annotazione di `_Use_decl_annotations_`.|  
  
## Annotazioni di successo o errore  
 Una funzione può non riuscire e quando questo accade, i risultati possono essere incompleti o differire dai risultati della funzione quando ha esito positivo.  Le annotazioni nell'elenco seguente forniscono le modalità per esprimere il comportamento dell'errore.  Per utilizzare ognuna di queste annotazioni, è necessario consentire loro di determinare l'esito positivo; pertanto è necessaria un'annotazione `_Success_`.  Si noti che `NTSTATUS` e `HRESULT` già dispongono di un'annotazione di `_Success_` compilata in esse; tuttavia, se si specifica una propria annotazione di `_Success_` su `NTSTATUS` o su `HRESULT`, eseguire l'override dell'annotazione incorporata.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Always_(anno_list)`|Equivalentemente a `anno_list _On_failure_(anno_list)`, le annotazioni in `anno_list` si applicano indipendentemente se la funzione ha o no esito positivo.|  
|`_On_failure_(anno_list)`|Per essere utilizzato solo quando `_Success_` viene utilizzato anche per annotare la funzione—esplicitamente, o implicitamente mediante `_Return_type_success_` su un typedef.  Quando l'annotazione `_On_failure_` è presente in un parametro di funzione o un valore restituito, ciascuna annotazione in `anno_list` \(anno\) si comporta come se fosse codificata come `_When_(!expr, anno)`, dove `expr` è il parametro dell'annotazione richiesta `_Success_`.  Ciò significa che l'applicazione implicita di `_Success_` a tutte le post\-condizioni non è applicabile per `_On_failure_`.|  
|`_Return_type_success_(expr)`|Può essere applicato a un typedef.  Indica che tutte le funzioni che restituiscono quel tipo e non hanno `_Success_` sono contrassegnate come se avessero `_Success_(expr)`.  `_Return_type_success_` non può essere utilizzato in una funzione o nel puntatore a funzione typedef.|  
|`_Success_(expr)`|`expr` è un'espressione che produce un rvalue.  Quando l'annotazione `_Success_` è presente in una dichiarazione di funzione o una definizione, ciascuna annotazione \(`anno`\) nella funzione e in post\-condizione, si comporta come se fosse codificata come `_When_(expr, anno)`.  L'annotazione `_Success_` può essere utilizzata solo su una funzione, non sui relativi parametri o sul tipo restituito.  Potrebbe contenere al massimo un'annotazione `_Success_` su una funzione e non può essere all'interno di qualsiasi `_When_`, `_At_`, o `_Group_`.  Per ulteriori informazioni, vedere [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)