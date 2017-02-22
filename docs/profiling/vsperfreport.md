---
title: "VSPerfReport | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "riga di comando, strumenti"
  - "strumenti della riga di comando, VSPerfReporttool"
  - "strumentazione, VSPerfReporttool"
  - "strumenti di prestazioni, VSPerfReport (strumento)"
  - "strumenti di profilatura, VSPerfReport"
  - "VSPerfReport (strumento)"
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfReport
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento da riga di comando VSPerfReport consente di creare rapporti utilizzando gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sui file di dati.  Il formato predefinito del report è un file con estensione csv.  
  
 VSPerfReport utilizza la seguente sintassi:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Notare che `filename` deve essere un file vsp o vsps valido.  
  
 Lo strumento della riga di comando Vsperfreport viene utilizzato anche per confrontare file .vsp o .vsps.  Per generare un report di differenza \("diff"\), utilizzare la seguente sintassi:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` devono essere file vsp o vsps validi.  
  
## File di simboli  
 Per visualizzare informazioni sui simboli quali i nomi della funzione e i numeri di riga, in VSPerfReport è necessario disporre di accesso ai file di simboli \(con estensione pdb\) dei componenti profilati e ai file di simboli di Windows.  Per ulteriori informazioni, vedere [Procedura: specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## Opzioni generali del report  
 Nella seguente tabella vengono descritte le opzioni generali per la formattazione del report e le opzioni che consentono di selezionare i dati da inserire nel report.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**U**|L'output del report e l'output della console reindirizzato vengono scritti come Unicode.  Deve essere la prima opzione specificata.|  
|**Summary:**\[*types*\]|Crea uno o più tipi di rapporti.<br /><br /> -   `All`: vengono generati tutti i tipi di report.<br />-   `CallerCallee`: relazioni padre\/figlio tra funzioni.<br />-   `Function`: funzioni chiamate.<br />-   `CallTree`: gerarchia delle funzioni chiamate.<br />-   `Counter`: tutti i contrassegni insieme ai valori del contatore delle prestazioni di Windows.<br />-   `Ip`: istruzioni profilate.<br />-   `Life`: durata degli oggetti allocati \(disponibile quando i dati di allocazione sono stati raccolti\).<br />-   `Line`: dati di profilo della riga del codice sorgente.<br />-   `Header`\- il report contiene informazioni sull'intestazione del file.<br />-   `Mark`: tutti i contrassegni.<br />-   `Module`: moduli profilati.<br />-   `Process`: processi profilati.<br />-   `Thread`: thread profilati.<br />-   `Type`: tipi allocati.<br />-   `Contention`: conflitti tra risorse.<br />-   `RuleWarnings`: problemi relativi alle regole di prestazioni.<br />-   `ETW` : tutti gli eventi ETW \(Event Tracing for Windows\) raccolti durante l'esecuzione della profilatura.  Il file di dati con estensione etl deve trovarsi nel percorso originale o nella directory contenente il file con estensione vsp o vsps.|  
|**Xml**|Esegue l'output del report in formato XML.|  
|**CallTrace**|Crea un elenco di ingressi e uscite delle funzioni, di eventi ETW e contrassegni.|  
|**ClearPackedSymbols**|Rimuove i simboli precedentemente incorporati da un file di dati del profiler.  Eseguire questo comando prima di eseguire PackSymbols una seconda volta.|  
|**SymbolPath:** `path`|Specifica uno o più percorsi di ricerca o server di simboli che contengono simboli per il file di dati del profiler.|  
|**DebugSymPath**|Elenca i percorsi in cui viene eseguita la ricerca di simboli e indica se questi vengono trovati.  Questa opzione è utile per risolvere problemi di risoluzione dei simboli.|  
|**PackSymbols**|Salva simboli nel file di dati di profilatura \(con estensione vsp\) in modo che i file di simboli \(con estensione pdb\) non siano necessari per l'analisi.|  
|**Output:** *path* &#124;*filename*|Specifica un percorso alternativo per i file di rapporto generati.  Per impostazione predefinita, i rapporti vengono creati nella directory corrente.|  
|**SummaryFile**|Analizzare e salvare le informazioni analizzate in un file di riepilogo con estensione vsps.|  
|**PrintMarks**|Mostrare i nomi e timestamp per tutti i contrassegni nel file di report specificato.|  
|**?**|Visualizza le informazioni sull'utilizzo.|  
|**NoLogo**|Nasconde le informazioni sulla versione quando il report è in esecuzione.|  
|**UserRulesDirectory**|Specifica la directory contenente le regole di prestazioni definite dall'utente \[non ancora implementato\].|  
  
## Opzioni di filtro  
 Nella seguente tabella vengono indicate le opzioni che consentono di filtrare i dati disponibili.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**JustMyCode**\[**:**\[`caller`\]\[,`callee`\]\]|Mostra solo le chiamate di funzione dell'applicazione utente e nasconde le chiamate di sistema.<br /><br /> -   Nessun parametro: nasconde tutte le funzioni di sistema.<br />-   `caller`: mostra un livello di funzioni di sistema che chiamano funzioni dell'applicazione.<br />-   `callee`: mostra un livello di funzioni di sistema chiamate dalle funzioni dell'applicazione utente.|  
|**StartTime:**\[*value*\]|Mostra soltanto i dati raccolti dopo il valore \(in millisecondi.\)|  
|**EndTime:**\[*value*\]|Mostra soltanto i dati raccolti prima del valore \(in millisecondi.\)|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file filtro generato dalla finestra Rapporto di prestazioni di Visual Studio.|  
|**MsFilter:**\[*starttime,duration*\]|Mostra solo i dati da `starttime` fino a `duration` \(in millisecondi\).|  
|**Process:**\[*pid*\]|Mostra soltanto dati dal processo specificato.|  
|**Thread:**\[*threadid*\]|Mostra soltanto dati dal thread specificato.|  
|**Thread:**\[*threadid,processid*\]|Mostra soltanto dati dal thread specificato associato al processo specificato.|  
  
## Opzioni di confronto report  
 Nella seguente tabella vengono indicate le opzioni per il confronto di file di report.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**Diff**  `vspfile1 vspfile2`|Confronta due file di report \(vsp o vsps\).  Le opzioni di riepilogo vengono ignorate con l'opzione diff.|  
|**Diff:**\[*value*\]|Al di sotto di questo valore soglia la differenza tra due valori verrà ignorata.  Inoltre, non verranno visualizzati neanche nuovi dati con valori al di sotto di questa soglia.|  
|**DiffTable:**\[*tablename*\]|Utilizzare questa tabella specifica per confrontare i file.  L'impostazione predefinita è la tabella delle funzioni.|  
|**DiffColumn:**\[*columnname*\]|Utilizzare questa specifica colonna di confronto dei valori.  Il valore predefinito è la colonna percentuale campioni esclusivi.|  
|**QueryDiffTables**|Elenca le tabelle e le colonne valide per i due file di report specificati.|  
  
## Vedere anche  
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)