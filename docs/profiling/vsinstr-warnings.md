---
title: "Avvisi di VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumentazione, VSInstr (strumento)"
  - "strumenti di prestazioni, VSInstr (strumento)"
  - "VSInstr (strumento)"
  - "avvisi"
  - "avvisi, VSInstr (strumento)"
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avvisi di VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella tabella riportata di seguito sono elencati gli avvisi generati dallo strumento VSInstr.exe.  Per evitare che i messaggi vengano visualizzati, è possibile utilizzare l'opzione NOWARN insieme al numero di avviso appropriato.  
  
|Numero avviso|Descrizione|  
|-------------------|-----------------|  
|**VSP2000**|Errore interno.  Impossibile ottenere il nome del file di modulo per questo eseguibile.|  
|**VSP2001**|\<nome assembly\> è un assembly con nome sicuro.  Deve essere firmato di nuovo prima dell'esecuzione.<br /><br /> Questo avviso viene visualizzato quando un assembly firmato viene sottoposto a strumentazione.  È possibile utilizzare lo strumento sn.exe per firmare nuovamente il binario o disattivare temporaneamente il requisito del nome sicuro.  Per ulteriori informazioni, vedere [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).|  
|**VSP2002**|Impossibile trovare la funzione \<nome funzione\> nel file \<nome file\>.<br /><br /> Questo avviso viene visualizzato quando non è possibile individuare una funzione nel file specificato.|  
|**VSP2003**|Impossibile trovare salti incrociati alla funzione \<nome funzione\> nel file \<nome file\>.<br /><br /> Questo avviso viene visualizzato se VSInstr non è in grado di annullare i salti incrociati,  che vengono utilizzati per l'ottimizzazione del codice.|  
|**VSP2004**|La funzione \<nome funzione\> è stata esclusa mediante l'opzione della riga di comando EXCLUDE, ma era una funzione richiesta in quanto contenente un salto incrociato.<br /><br /> Questo avviso viene visualizzato se la funzione è stata esclusa mediante l'opzione EXCLUDE, ma è necessaria nel corso del processo di strumentazione.  Il profiler include automaticamente la funzione richiesta.|  
|**VSP2005**|Errore interno di strumentazione \<testo errore\><br /><br /> Questo avviso viene generato se non è possibile eseguire la strumentazione.  Esaminare il testo dell'errore per stabilire se è possibile correggerlo.|  
|**VSP2006**|Impossibile individuare il PDB per \<nome\><br /><br /> Questo avviso viene visualizzato se il file PDB non è presente nel percorso di ricerca o non corrisponde al file binario.|  
|**VSP2007**|\<nome file\> non contiene codice instrumentabile.<br /><br /> Questo avviso viene generato se le funzioni presenti nel file binario sono state tutte escluse o se il file specificato contiene solo risorse.|  
|**VSP2008**|Impossibile ottenere gli attributi di sicurezza da \<nome\>.  Codice di errore \<codice\><br /><br /> Questo avviso viene visualizzato se l'utente non dispone dell'autorizzazione READ\_DAC.  Durante il processo di strumentazione il profiler tenta di preservare l'elenco DACL originale per il binario.  Poiché il binario originale viene sostituito con uno nuovo, l'elenco DACL del file originale deve essere copiato e applicato al nuovo binario.  Questa operazione può avere esito negativo se l'utente non dispone dell'accesso READ\_DAC per il binario originale.|  
|**VSP2009**|Impossibile impostare gli attributi di sicurezza per \<nome\>.  Codice di errore \<numero errore\><br /><br /> Questo avviso viene visualizzato se l'utente non dispone dell'autorizzazione WRITE\_DAC.  Durante il processo di strumentazione il profiler tenta di preservare l'elenco DACL originale per il binario.  Poiché il binario originale viene sostituito con uno nuovo, l'elenco DACL del file originale deve essere copiato e applicato al nuovo binario.  Questa operazione può avere esito negativo se l'utente non dispone dell'accesso WRITE\_DAC per il nuovo binario.|  
|**VSP2010**|Nessuna funzione selezionata in modo specifico per la strumentazione a causa delle opzioni \/INCLUDE o \/EXCLUDE.|  
|**VSP2011**|Funcspec Include\/Exclude \<nome\> non corrispondente ad alcuna funzione.|  
|**VSP2012**|L'immagine non contiene codice che possa essere instrumentato per il code coverage.<br /><br /> Il profiler non esegue la strumentazione del tipo di codice riportato di seguito.<br /><br /> -   Funzioni CRT statiche<br />-   Metodi gestiti attribuiti con NonUserCodeAttribute<br />-   Metodi gestiti attribuiti con DebuggerHiddenAttribute<br />-   Blocchi MASM<br /><br /> Questo avviso viene generato se, dopo l'applicazione di filtri, non rimane codice.|  
|**VSP2013**|La strumentazione di questa immagine ne richiede l'esecuzione come processo a 32 bit.  I flag dell'intestazione CLR sono stati aggiornati di conseguenza.<br /><br /> Il profiler modifica il binario in modo che i sistemi operativi a 64 bit possano aprire il processo a 32 bit nell'emulatore WOW64.  Questa operazione può non riuscire per le librerie \(DLL\) caricate in un processo a 64 bit esistente.  L'avviso in questione notifica la dipendenza all'utente.|  
|**VSP2014**|L'immagine instrumentata risultante sembra non valida e potrebbe non essere eseguita.<br /><br /> Questo messaggio viene visualizzato quando l'assembly instrumentato finale presenta un'intestazione PE non valida.|  
  
## Vedere anche  
 [VSInstr](../profiling/vsinstr.md)