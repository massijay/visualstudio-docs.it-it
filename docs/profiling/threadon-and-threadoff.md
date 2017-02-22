---
title: "ThreadOn e ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ThreadOn e ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I sottocomandi **ThreadOff** e **ThreadOn** di VSPerfCmd.exe sono disponibili solo nelle sessioni di profilatura della riga di comando che utilizzano il metodo di strumentazione.  **ThreadOff** sospende l'esecuzione del profilo per il thread specificato, laddove **ThreadOn** la riprende.  **ThreadOff** arresta la profilatura del thread, mentre **ThreadOn** la avvia.  
  
 Nella maggior parte dei casi, **ThreadOn** o **ThreadOff** viene specificata come unica opzione in una riga di comando VSPerfCmd.exe, anche se è possibile combinarla con i sottocomandi **GlobalOn**, **GlobalOff**, **ProcessOn** e **ProcessOff**.  
  
 I sottocomandi **ThreadOn** e **ThreadOff** interagiscono con i sottocomandi **GlobalOn** e **GlobalOff** che controllano la raccolta dei dati per tutti i processi di una sessione di profilo dalla riga di comando e con i sottocomandi **ProcessOn** e **ProcessOff** che controllano la raccolta dei dati per un processo specificato.  
  
 I sottocomandi **ThreadOff** e **ThreadOn** influiscono anche sul conteggio Start\/Stop del thread modificato dalle funzioni API del profiler.  
  
-   **ThreadOff** imposta immediatamente il conteggio Start\/Stop del thread su 0 e sospende l'operazione di profilo.  
  
-   **ThreadOn** imposta immediatamente il conteggio Start\/Stop del thread su 1 e riprende l'operazione di profilo.  
  
 Per ulteriori informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).  
  
## Sintassi  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Parametri  
 `TID`  
 Identificatore Integer del thread da avviare o interrompere.  
  
## Opzioni valide  
 È possibile specificare **ThreadOn** e **ThreadOff** sulle righe di comando che contengono anche i sottocomandi seguenti.  
  
 **Start:** `Method`  
 Inizializza la sessione di profilo dalla riga di comando e imposta il metodo di profilo specificato.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Interrompe o avvia il profilo di tutti i processi in una sessione di profilo dalla riga di comando.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Interrompe o avvia il profilo per il processo specificato.  
  
## Esempio  
 In questo esempio il sottocomando **ThreadOff** viene utilizzato per interrompere la raccolta dei dati di profilo affinché vengano raccolti solo i dati di avvio dell'applicazione.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)