---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, strumentazione"
  - "strumentazione, strumento VSInstr"
  - "strumenti per la profilatura, VSInstr"
  - "strumenti della riga di comando, strumentazione"
  - "riga di comando, strumenti"
  - "VSInstr"
  - "VSInstr (strumento)"
  - "strumenti per le prestazioni, VSInstr"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento VSInstr consente di eseguire la strumentazione dei binari  e viene richiamato mediante la sintassi seguente:  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 Nella tabella riportata di seguito sono descritte le opzioni dello strumento VSInstr.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**Help** o **?**|Consente di visualizzare la Guida.|  
|**U**|Scrive l'output di console reindirizzato in formato Unicode.  Deve essere la prima opzione specificata.|  
|`@filename`|Specifica il nome di un file di risposta contenente un'opzione di comando per riga.  Non utilizzare le virgolette.|  
|**OutputPath** `:path`|Specifica una directory di destinazione per l'immagine instrumentata.  Se non si specifica un percorso di output, il binario originale viene rinominato con l'aggiunta di "Orig" alla fine del nome file all'interno della stessa directory e viene instrumentata una copia del binario.|  
|**Exclude** `:funcspec`|Specifica una specifica di funzione da escludere dalla strumentazione tramite probe.  Tale opzione risulta utile quando l'inserimento di controlli di profilatura in una funzione causa risultati imprevedibili o indesiderati.<br /><br /> Non utilizzare le opzioni **Exclude** e **Include** che fanno riferimento a funzioni nello stesso file binario.<br /><br /> È possibile specificare più specifiche di funzione con opzioni **Exclude** separate.<br /><br /> `funcspec` viene definita come:<br /><br /> \[namespace\<separatore1\>\] \[class\<separatore2\>\]function<br /><br /> \<separatore1\> corrisponde rispettivamente a `::` per il codice nativo e `.` per il codice gestito.<br /><br /> \<separatore2\> è sempre `::`<br /><br /> L'opzione **Exclude** è supportata con il code coverage.<br /><br /> È supportato l'utilizzo del carattere jolly \*.  Per escludere tutte le funzioni in uno spazio dei nomi, ad esempio, utilizzare:<br /><br /> MyNamespace::\*<br /><br /> È possibile utilizzare **VSInstr \/DumpFuncs** per elencare i nomi completi delle funzioni nel file binario specificato.|  
|**Include** `:funcspec`|Indica una specifica di funzione in un file binario da instrumentare con probe.  Tutte le altre funzioni dei binari non vengono instrumentate.<br /><br /> È possibile specificare più specifiche di funzione con opzioni **Include** separate.<br /><br /> Non utilizzare le opzioni **Include** e **Exclude** che fanno riferimento a funzioni nello stesso file binario.<br /><br /> L'opzione **Include** non è supportata con il code coverage.<br /><br /> `funcspec` viene definita come:<br /><br /> \[namespace\<separatore1\>\] \[class\<separatore2\>\]function<br /><br /> \<separatore1\> corrisponde rispettivamente a `::` per il codice nativo e `.` per il codice gestito.<br /><br /> \<separatore2\> è sempre `::`<br /><br /> È supportato l'utilizzo del carattere jolly \*.  Per includere tutte le funzioni in uno spazio dei nomi, ad esempio, utilizzare:<br /><br /> MyNamespace::\*<br /><br /> È possibile utilizzare **VSInstr \/DumpFuncs** per elencare i nomi completi delle funzioni nel file binario specificato.|  
|**DumpFuncs**|Elenca le funzioni all'interno dell'immagine specificata.  La strumentazione non viene eseguita.|  
|**ExcludeSmallFuncs**|Dalla strumentazione vengono escluse le piccole funzioni che sono funzioni brevi che non effettuano alcuna chiamata di funzione.  L'opzione **ExcludeSmallFuncs** garantisce un sovraccarico di strumentazione minore e, pertanto, una maggiore velocità di strumentazione.<br /><br /> L'esclusione di piccole funzioni riduce inoltre la dimensione del file .vsp e il tempo necessario per l'analisi.|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|Inserisce un contrassegno del profilo, ovvero un identificatore che consente di delimitare i dati nei rapporti, che è possibile utilizzare per identificare l'inizio o la fine di un intervallo dati nel file di rapporto con estensione vsp.<br /><br /> **Before**  `` : immediatamente prima dell'ingresso della funzione di destinazione.<br /><br /> **After**  `` : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top**  `` : immediatamente dopo l'ingresso della funzione di destinazione.<br /><br /> **Bottom**  `` : immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.<br /><br /> `Markid`: Integer positivo \(long\) da utilizzare come identificatore del contrassegno del profilo.|  
|**Coverage**|Esegue la strumentazione di tipo code coverage  Si può utilizzare solo con le opzioni seguenti: **Verbose**, **OutputPath**, **Exclude** e **Logfile**.|  
|**Verbose**|L'opzione **Verbose** consente di visualizzare informazioni dettagliate sul processo di strumentazione.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Elimina tutti gli avvisi o avvisi specifici.<br /><br /> `Message Number`: numero dell'avviso.  Se il parametro `Message Number` viene omesso, vengono eliminati tutti gli avvisi.<br /><br /> Per ulteriori informazioni, vedere [Avvisi di VSInstr](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|Specifica il livello di profilatura delle opzioni di controllo della raccolta dati di VSInstr seguenti.<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  `` : specifica le funzioni di controllo della raccolta dei dati a livello di thread.  La profilatura viene avviata o interrotta solo per il thread corrente.  Non viene influenzato lo stato di profilatura degli altri thread.  Il valore predefinito è thread.<br /><br /> **Process**  `` : specifica le funzioni di controllo della raccolta dei dati di profilatura a livello di processo.  La profilatura viene avviata o interrotta per tutti i thread del processo corrente.  Non viene influenzato lo stato di profilatura degli altri processi.<br /><br /> **Global**  `` : specifica le funzioni di controllo della raccolta dei dati a livello globale \(tra processi\).<br /><br /> Se non si specifica il livello di profilatura, si verifica un errore.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Limita la raccolta dati alla funzione di destinazione e alle funzioni figlio chiamate da tale funzione.<br /><br /> **Inside**  `` : inserisce la funzione StartProfile immediatamente dopo l'ingresso nella funzione di destinazione.  Inserisce la funzione StopProfile prima di ogni restituzione nella funzione di destinazione.<br /><br /> **Outside**  `` : inserisce la funzione StartProfile immediatamente prima di ogni chiamata alla funzione di destinazione.  Inserisce la funzione StopProfile dopo ogni chiamata alla funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Esclude la raccolta dei dati per la funzione di destinazione e le funzioni figlio chiamate da tale funzione.<br /><br /> **Inside**  `` : inserisce la funzione SuspendProfile dopo l'ingresso nella funzione di destinazione.  Inserisce la funzione ResumeProfile prima di ogni restituzione nella funzione di destinazione.<br /><br /> **Outside**  `` : inserisce la funzione SuspendProfile immediatamente prima dell'ingresso nella funzione di destinazione.  Inserisce la funzione ResumeProfile dopo l'uscita dalla funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StartProfile, prima di quest'ultima verrà inserita la funzione SuspendProfile.  Se la funzione di destinazione contiene una funzione StopProfile, dopo di essa verrà inserita la funzione ResumeProfile.|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|Avvia la raccolta dei dati durante l'esecuzione di una profilatura.  Tale opzione inserisce la funzione API StartProfile nella posizione specificata.<br /><br /> **Before**  `` : immediatamente prima dell'ingresso della funzione di destinazione.<br /><br /> **After**  `` : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top**  `` : immediatamente dopo l'ingresso della funzione di destinazione.<br /><br /> **Bottom**  `` : immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Interrompe la raccolta dei dati durante l'esecuzione di una profilatura.  Tale opzione inserisce la funzione StopProfile nella posizione specificata.<br /><br /> **Before**  `` : immediatamente prima dell'ingresso della funzione di destinazione.<br /><br /> **After**  `` : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top**  `` : immediatamente dopo l'ingresso della funzione di destinazione.<br /><br /> **Bottom**  `` : immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Interrompe la raccolta dei dati durante l'esecuzione di una profilatura.  Tale opzione inserisce la funzione API SuspendProfile nella posizione specificata.<br /><br /> **Before**  `` : immediatamente prima dell'ingresso della funzione di destinazione.<br /><br /> **After**  `` : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top**  `` : immediatamente dopo l'ingresso della funzione di destinazione.<br /><br /> **Bottom**  `` : immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StartProfile, prima di quest'ultima verrà inserita la funzione SuspendProfile.|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Avvia o riprende la raccolta dei dati durante l'esecuzione di una profilatura.<br /><br /> Viene in genere utilizzata per avviare la profilatura dopo che questa è stata interrotta da un'opzione **SuspendOnly**.  Tale opzione inserisce la funzione API ResumeProfile nella posizione specificata.<br /><br /> **Before**  `` : immediatamente prima dell'ingresso della funzione di destinazione.<br /><br /> **After**  `` : immediatamente dopo l'uscita della funzione di destinazione.<br /><br /> **Top**  `` : immediatamente dopo l'ingresso della funzione di destinazione.<br /><br /> **Bottom**  `` : immediatamente prima di ogni restituzione nella funzione di destinazione.<br /><br /> `funcname`: nome della funzione di destinazione.<br /><br /> Se la funzione di destinazione contiene una funzione StopProfile, dopo di essa verrà inserita la funzione ResumeProfile.|  
  
## Vedere anche  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Avvisi di VSInstr](../profiling/vsinstr-warnings.md)   
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)