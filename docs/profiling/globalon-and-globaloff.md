---
title: "GlobalOn e GlobalOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# GlobalOn e GlobalOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le opzioni **GlobalOff** e **GlobalOn** di VSPerfCmd.exe consentono di sospendere e di riprendere il profilo per tutti i processi e i thread in una sessione di profilo dalla riga di comando.  
  
 È possibile specificare **GlobalOn** e **GlobalOff** come le uniche opzioni in una riga di comando VSPerfCmd.exe o includerle in righe di comando contenenti anche **Start**, **Launch** o **Attach**.  
  
 Le opzioni **GlobalOn** e **GlobalOff** possono anche essere combinate con le opzioni **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.  
  
 Le opzioni **GlobalOn** e **GlobalOff** interagiscono con le opzioni **ProcessOn** e **ProcessOff** che controllano la raccolta dei dati per un processo specificato e con le opzioni **ThreadOn** e **ThreadOff** che controllano la raccolta dei dati per un thread specificato.  
  
 Le opzioni **GlobalOff** e **GlobalOn** influiscono anche sul conteggio Start\/Stop globale gestito dalle funzioni API del profiler.  
  
-   **GlobalOff** consente di impostare immediatamente il conteggio Start\/Stop globale su 0 e di sospendere il profilo.  
  
-   **GlobalOn** consente di impostare immediatamente il conteggio Start\/Stop globale su 1 e di riprendere il profilo.  
  
 Per ulteriori informazioni, vedere [API per strumenti di profilatura](../profiling/profiling-tools-apis.md).  
  
## Sintassi  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn} [Options]  
```  
  
#### Parametri  
 Nessuno  
  
## Opzioni valide  
 È possibile specificare le opzioni **GlobalOn** e **GlobalOff** in righe di comando che contengono anche le opzioni seguenti.  
  
 **Start:** `Method`  
 Inizializza la sessione del profiler dalla riga di comando e imposta il metodo di profilo specificato.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'operazione di profilo con il metodo di campionamento.  
  
 **Attach:** `PID`  
 Avvia il profilo del processo specificato.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Interrompe o avvia il profilo per il processo specificato.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Interrompe o avvia il profilo per il processo specificato \(solo il metodo di strumentazione\).  
  
## Esempio  
 In questo esempio le opzioni **GlobalOff** e **GlobalOn** vengono utilizzate per evitare la raccolta dei dati di profilo per l'avvio e l'arresto dell'applicazione.  
  
```  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)