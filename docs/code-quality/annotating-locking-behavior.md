---
title: "Annotazione del comportamento di blocco | Microsoft Docs"
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
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Annotazione del comportamento di blocco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per evitare i bug di concorrenza in un programma multithread, utilizzare sempre una appropriata disciplina di blocco e utilizzare le annotazioni SAL.  
  
 I bug di concorrenza sono notoriamente difficili da riprodurre, diagnosticare e farne il debug perché sono non deterministici.  Ragionare sull'interfoliazione delle thread è difficile idealmente e diventa pratico quando si progetta un corpo di codice che dispone di più di una thread.  Pertanto, è consigliabile seguire una disciplina di blocco nei programmi multithread.  Ad esempio, obbedendo a un ordine di blocco mentre si acquisiscono molteplici blocchi aiuta ad evitare deadlock e acquisendo correttamente la guardia del blocco prima di accedere ad una risorsa condivisa aiuta a impedire una race condition.  
  
 Sfortunatamente, queste regole di blocco in apparenza semplici sono sorprendentemente difficili da utilizzare nella pratica.  Una limitazione elementare degli odierni linguaggi di programmazione e compilatori è che non supportano direttamente la specifica e l'analisi dei requisiti di concorrenza.  I programmatori devono fare affidamento sui commenti informali del codice per esprime le intenzioni su come utilizzare i blocchi.  
  
 Le annotazioni di concorrenza SAL sono progettate per specificare gli effetti collaterali del blocco, la responsabilità del blocco, la tutela di dati, la gerarchia d'ordine e altri comportamenti previsti del blocco.  Creando regole implicite esplicite, le annotazioni di concorrenza SAL forniscono un metodo coerente per documentare come il codice utilizza le regole di blocco.  Le annotazioni di concorrenza migliorano anche la capacità degli strumenti di analisi codice di trovare race condition, deadlock, operazioni di sincronizzazione non corrispondenti e altri difficili errori di concorrenza.  
  
## Indicazioni generali  
 Utilizzando le annotazioni, è possibile indicare i contratti impliciti nelle definizioni di funzione tra le implementazioni \(chiamati\) e i client \(chiamanti\), ed esprimere invarianti e altre proprietà del programma che possono migliorare ulteriormente l'analisi.  
  
 SAL supporta molti tipi diversi di primitive di blocco—come ad esempio, le sezioni critiche, i mutex, gli spinlock e altri oggetti risorsa.  Molte annotazioni di concorrenza utilizzano un'espressione di blocco come parametro.  Per convenzione, un blocco è indicato dall'espressione del percorso dell'oggetto del blocco sottinteso.  
  
 Alcune regole sulle proprietà delle thread da tenere in considerazione:  
  
-   Gli spinlock sono blocchi non contati in grado di vedere le proprietà delle thread.  
  
-   I mutex e le sezioni critiche sono blocchi contati in grado di vedere le proprietà delle thread.  
  
-   I semafori e gli eventi sono considerati blocchi che non sono in grado di vedere le proprietà delle thread.  
  
## Annotazioni di blocco  
 Nella tabella seguente sono elencate le annotazioni di blocco.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio del blocco esclusivo dell'oggetto del blocco denominato da `expr`.|  
|`_Acquires_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio del blocco dell'oggetto del blocco denominato da `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Il blocco denominato da `expr` viene acquisito.  Un errore viene restituito se il blocco è già utilizzato.|  
|`_Acquires_shared_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione incrementando di uno il conteggio del blocco condiviso dell'oggetto del blocco denominato da `expr`.|  
|`_Create_lock_level_(name)`|Un'istruzione che dichiara il simbolo `name` come un livello di blocco in modo che possa essere utilizzato nelle annotazioni `_Has_Lock_level_` e in `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|L'annotazione di qualsiasi oggetto per migliorare le informazioni sul tipo di un oggetto risorsa.  Talvolta un tipo comune viene utilizzato per diversi tipi di risorse e il tipo di overload non è sufficiente per distinguere i requisiti di semantica tra le varie risorse.  Di seguito è riportato un elenco di parametri predefiniti di `kind` :<br /><br /> `_Lock_kind_mutex_`<br /> ID di tipo blocco per i mutex.<br /><br /> `_Lock_kind_event_`<br /> ID di tipo blocco per gli eventi.<br /><br /> `_Lock_kind_semaphore_`<br /> ID di tipo blocco per i semafori.<br /><br /> `_Lock_kind_spin_lock_`<br /> ID di tipo blocco per gli spinlock.<br /><br /> `_Lock_kind_critical_section_`<br /> ID di tipo blocco per le sezioni critiche.|  
|`_Has_lock_level_(name)`|Annota un oggetto del blocco e lo fornisce al livello di blocco `name`.|  
|`_Lock_level_order_(name1, name2)`|Un'istruzione che fornisce l'ordine di blocco tra `name1` e `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Annota una funzione e indica che lo stato successivo dei due blocchi `expr1` e `expr2`, verrà considerato come se fosse lo stesso oggetto del blocco.|  
|`_Releases_exclusive_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione decrementando di uno il conteggio del blocco esclusivo dell'oggetto del blocco denominato da `expr`.|  
|`_Releases_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione decrementando di uno il conteggio del blocco dell'oggetto del blocco denominato da `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Il blocco denominato da `expr` viene rilasciato.  Un errore viene restituito se il blocco non è attualmente utilizzato.|  
|`_Releases_shared_lock_(expr)`|Annota una funzione e indica lo stato successivo della funzione decrementando di uno il conteggio del blocco condiviso dell'oggetto del blocco denominato da `expr`.|  
|`_Requires_lock_held_(expr)`|Annota una funzione e indica che in uno stato precedente il conteggio del blocco dell'oggetto denominato `expr` è almeno uno.|  
|`_Requires_lock_not_held_(expr)`|Annota una funzione e indica che in uno stato precedente il conteggio del blocco dell'oggetto denominato `expr` è zero.|  
|`_Requires_no_locks_held_`|Annota una funzione e indica che il conteggio del blocco è zero in tutti i blocchi noti al controllore.|  
|`_Requires_shared_lock_held_(expr)`|Annota una funzione e indica che in uno stato precedente il conteggio del blocco condiviso dell'oggetto denominato `expr` è almeno uno.|  
|`_Requires_exclusive_lock_held_(expr)`|Annota una funzione e indica che in uno stato precedente il conteggio del blocco esclusivo dell'oggetto denominato `expr` è almeno uno.|  
  
## Intrinseci SAL per oggetti di blocco non esposti  
 Alcuni oggetti del blocco non vengono esposti dall'implementazione delle funzioni collegate di blocco.  Nella tabella seguente sono elencate le variabili intrinseche di SAL che attivano le annotazioni sulle funzioni che operano sugli oggetti non esposti al blocco.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Viene descritto lo spin lock di annullamento.|  
|`_Global_critical_region_`|Viene descritta l'area critica.|  
|`_Global_interlock_`|Vengono descritte le operazioni interlocked.|  
|`_Global_priority_region_`|Viene descritta la regione di prioritaria.|  
  
## Annotazioni di accesso ai dati condivisi  
 Nella tabella seguente sono elencate le annotazioni che utilizzano l'accesso ai dati condivisi.  
  
|Annotazione|Descrizione|  
|-----------------|-----------------|  
|`_Guarded_by_(expr)`|Annota una variabile e indica se la variabile è accessibile, il conteggio dei blocchi dell'oggetto del blocco denominato `expr` varrà almeno uno.|  
|`_Interlocked_`|Annota una variabile ed è equivalente a `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Il parametro di funzione annotato è l'operando di destinazione di una delle diverse funzioni collegate.  Gli operandi devono presentare proprietà aggiuntive specifiche.|  
|`_Write_guarded_by_(expr)`|Annota una variabile e indica se la variabile è modificabile, il conteggio dei blocchi dell'oggetto del blocco denominato `expr` varrà almeno uno.|  
  
## Vedere anche  
 [Uso delle annotazioni SAL per ridurre gli errori del codice C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informazioni su SAL](../code-quality/understanding-sal.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento delle funzioni](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Specificare dove e quando applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funzioni intrinseche](../code-quality/intrinsic-functions.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)   
 [Blog del team di Analisi del codice](http://go.microsoft.com/fwlink/p/?LinkId=251197)