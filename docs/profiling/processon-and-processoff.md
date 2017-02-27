---
title: "ProcessOn e ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ProcessOn e ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I sottocomandi **ProcessOff** e **ProcessOn** di VSPerfCmd.exe consentono di sospendere e di riprendere la profilatura per il processo specificato in una sessione di profilatura dalla riga di comando.  **ProcessOff** arresta la profilatura del processo, mentre **ProcessOn** la avvia.  
  
 Nella maggior parte dei casi, si specifica **ProcessOn** o **ProcessOff** come unica opzione in una riga di comando VSPerfCmd.exe, anche se è possibile combinare questi comandi con i sottocomandi **GlobalOn**, **GlobalOff**, **ThreadOn** e **ThreadOff**.  
  
 I sottocomandi **ProcessOn** e **ProcessOff** interagiscono con i sottocomandi **GlobalOn** e **GlobalOff** che controllano la raccolta dei dati per tutti i processi di una sessione di profilo dalla riga di comando e con i sottocomandi **ThreadOn** e **ThreadOff** che controllano la raccolta dei dati per un thread specificato.  
  
 I sottocomandi **ProcessOff** e **ProcessOn** influiscono anche sul conteggio Start\/Stop del processo modificato dalle funzioni API del profiler.  
  
-   **ProcessOff** imposta immediatamente il conteggio Start\/Stop del processo su 0 e sospende l'operazione di profilo.  
  
-   **ProcessOn** imposta immediatamente il conteggio Start\/Stop del processo su 1 e riprende l'operazione di profilo.  
  
 Per ulteriori informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).  
  
## Sintassi  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Parametri  
 `PID`  
 Identificatore Integer del processo da avviare o interrompere.  Gli ID processo vengono elencati nella scheda Processi di Gestione attività di Windows.  
  
## Sottocomandi obbligatori  
 Nessuno  
  
## Sottocomandi validi  
 È possibile specificare **ProcessOn** e **ProcessOff** sulle righe di comando che contengono anche i sottocomandi seguenti.  
  
 **Start:** `Method`  
 Inizializza la sessione di profilo dalla riga di comando e imposta il metodo di profilo specificato.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'operazione di profilo con il metodo di campionamento.  
  
 **Attach:** `PID`  
 Avvia il profilo del processo specificato.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Interrompe o avvia il profilo di tutti i processi in una sessione di profilo dalla riga di comando.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Interrompe o avvia il profilo per il thread specificato \(solo metodo di strumentazione\).  
  
## Esempio  
 In questo esempio, il sottocomando **ProcessOff** viene utilizzato per raccogliere dati di profilo per l'avvio dell'applicazione.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)