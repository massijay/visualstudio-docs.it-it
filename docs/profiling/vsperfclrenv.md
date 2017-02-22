---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti da riga di comando, VSPerfCLREnv"
  - "riga di comando, strumenti"
  - "strumenti per le prestazioni, VSPerfCLREnv"
  - "strumenti per la profilatura,VSPerfCLREnv"
  - "VSPerfCLREnv (strumento)"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento VSPerfCLREnv viene utilizzato per impostare le variabili di ambiente che sono necessarie per profilare un'applicazione .NET Framework.  e utilizza la sintassi seguente:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 L'opzione scelta dipende da quale dei tre tipi della profilatura si desidera utilizzare: campionamento, strumentazione o globale.  Un'opzione separata è necessaria per includere i dati di interazione del livello nei dati di profilatura.  Nelle seguenti tabelle viene elencata la sintassi per ogni opzione.  
  
> [!NOTE]
>  Al termine della profilatura, eseguire **VSPerfCLREnv** con l'opzione **\/off** o **\/globaloff** per eliminare le variabili di ambiente necessarie per la profilatura.  Per ulteriori informazioni, vedere l'argomento Opzioni di VSPerfCLREnv per eliminare le impostazioni di ambiente riportato di seguito.  
  
 **Opzioni di VSPerfCLREnv per includere dati di interazione dei livelli**  
  
> [!WARNING]
>  La profilatura dell'interazione tra livelli può essere raccolta utilizzando [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], o [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Tuttavia, i dati della profilatura dell'interazione tra livelli possono essere visualizzati solo in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] e in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 Il profilo interazione tra livelli fornisce informazioni aggiuntive relative alle query ADO.NET in applicazioni a più livelli.  I dati vengono raccolti solo per chiamate di funzione sincrone.  I dati di interazione possono essere aggiunti all'esecuzione di qualsiasi profilatura utilizzando qualunque metodo di profilatura.  
  
 Le opzioni **InteractionOn** e **GlobalInteractionOn** abilitano la raccolta dei dati di interazione dei livelli.  L'opzione d'interazione deve essere impostata dopo avere impostato la variabile di ambiente VSPerfCLREnv necessaria per profilare un'applicazione.  
  
 Nell'esempio seguente vengono inclusi dati di interazione dei livelli nell'esecuzione di una profilatura che utilizza il metodo di campionamento:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Nell'esempio seguente vengono inclusi dati di interazione dei livelli nell'esecuzione di una profilatura per un servizio Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Opzioni di VSPerfCLREnv per eseguire la profilatura mediante strumentazione**  
  
 Nella seguente tabella vengono elencate le opzioni di VSPerfCLREnv per la profilatura mediante strumentazione:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**TraceOn**|Attiva la profilatura mediante il metodo di strumentazione.  Non attiva la profilatura per l'allocazione di memoria o la raccolta dei dati sulla durata degli oggetti.|  
|**TraceGC**|Attiva la profilatura per l'allocazione di memoria mediante il metodo di strumentazione.  Non attiva la raccolta dei dati sulla durata degli oggetti.|  
|**TraceGCLife**|Abilita la profilatura dell'allocazione di memoria e la raccolta di dati relativi alla durata degli oggetti utilizzando il metodo di strumentazione.|  
  
 **Opzioni di VSPerfCLREnv per eseguire la profilatura mediante campionamento**  
  
 Nella seguente tabella vengono elencate le opzioni di VSPerfCLREnv per la profilatura mediante campionamento:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**SampleOn**|Attiva la profilatura mediante il metodo di campionamento.  Non attiva la profilatura per l'allocazione di memoria o la raccolta dei dati sulla durata degli oggetti.|  
|**SampleGC**|Attiva la profilatura per l'allocazione di memoria mediante il metodo di campionamento.  Non attiva la raccolta dei dati sulla durata degli oggetti.|  
|**SampleGCLife**|Attiva la profilatura per l'allocazione di memoria mediante il metodo di campionamento.  Attiva anche la raccolta dei dati sulla durata degli oggetti.|  
|**SampleLineOff**|Disabilita la raccolta dei dati di profilatura a livello di riga .NET.|  
  
 **Opzioni di VSPerfCLREnv per la profilatura globale**  
  
 Per profilare un servizio gestito, ad esempio un'applicazione Web ASP.NET avviata dal sistema operativo anziché dall'utente, utilizzare le opzioni per la profilatura globale disponibili in VSPerfCLREnv.  Nella tabella seguente vengono descritte le versioni globali delle opzioni di VSPerfCLREnv.  Queste opzioni impostano le variabili di ambiente appropriate nel Registro di sistema.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**GlobalTraceOn**|Attiva la profilatura globale mediante il metodo di strumentazione.  Non attiva la raccolta degli eventi di allocazione di memoria o dei dati sulla durata degli oggetti.|  
|**GlobalTraceGC**|Attiva la profilatura globale per l'allocazione di memoria mediante il metodo di strumentazione.  Non attiva la raccolta dei dati sulla durata degli oggetti.|  
|**GlobalTraceGCLife**|Attiva la profilatura globale per l'allocazione di memoria mediante il metodo di strumentazione.  Attiva anche la raccolta dei dati sulla durata degli oggetti.|  
|**GlobalSampleOn**|Attiva la profilatura globale mediante il metodo di campionamento.  Non attiva la raccolta degli eventi di allocazione di memoria o dei dati sulla durata degli oggetti.|  
|**GlobalSampleGC**|Attiva la profilatura globale per l'allocazione di memoria mediante il metodo di campionamento.  Non attiva la raccolta dei dati sulla durata degli oggetti.|  
|**GlobalSampleGCLife**|Attiva la profilatura globale per l'allocazione di memoria mediante il metodo di campionamento.  Attiva anche la raccolta dei dati sulla durata degli oggetti.|  
  
 **Opzioni di VSPerfCLREnv per eliminare le impostazioni di ambiente**  
  
 Al termine delle operazioni di profilatura dell'applicazione gestita, utilizzare una delle seguenti opzioni per eliminare le variabili di ambiente aggiunte da VSPerfCLREnv.  Nella seguente tabella viene descritta la procedura per l'eliminazione delle variabili di ambiente locali e globali:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Off**|Elimina le variabili di ambiente per la profilatura standard di .NET.  Utilizzare questa opzione se sono state utilizzate le opzioni VSPerfClrEnv non globali per impostare le variabili di ambiente del profiler.|  
|**GlobalOff**|Elimina le variabili di ambiente per la profilatura globale di .NET.  Utilizzare questa opzione se l'applicazione è stata avviata dal sistema operativo e non dal profiler.|  
  
## Note  
 Queste opzioni non sono necessarie per la profilatura di un'applicazione gestita se essa viene avviata nell’IDE utilizzando Esplora prestazioni.  Esplora prestazioni regola automaticamente tutte le impostazioni di ambiente necessarie.  
  
 Se durante la profilatura non è stato impostato l'ambiente corretto, l'analisi restituirà un avviso e i nomi delle funzioni gestite non verranno risolti correttamente.  
  
## Vedere anche  
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)