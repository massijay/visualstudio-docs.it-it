---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Events** di VSPerfCmd.exe controlla la registrazione di Traccia eventi per Windows \(ETW\).  I dati ETW vengono salvati in un file con estensione etl separato dal file di dati del profiler.  È possibile visualizzare i dati in un rapporto utilizzando il comando [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw.  
  
 È possibile chiamare l'opzione **Events** in qualsiasi momento prima che venga chiamato il comando **Shutdown** di VSPerfCmd per interrompere il profilo.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Parametri  
 **On**&#124;**Off**  
 Avvia o interrompe la raccolta di dati degli eventi.  
  
 `Guid`  
 GUID di controllo del provider.  
  
 `ProviderName`  
 Nome del provider registrato con Strumentazione gestione Windows \(WMI\).  
  
 `Flags`  
 Valore di flag esadecimale con prefisso "0x" definito dal provider di eventi.  
  
 `Level`  
 Specifica la quantità di dati raccolti.  `Level` è definito dal provider di eventi.  
  
 L'opzione **Events** riconosce come nomi di provider le parole chiave del kernel indicate di seguito:  
  
 **Process**  
 Eventi di processo  
  
 **Thread**  
 Eventi thread  
  
 **Image**  
 Eventi di caricamento e scaricamento di immagini  
  
 **Disk**  
 Eventi di I\/O del disco  
  
 **File**  
 Eventi di I\/O file  
  
 **Hardfault**  
 Errori di pagina hardware  
  
 **Pagefault**  
 Errori di pagina software  
  
 **Network**  
 Eventi di rete  
  
 **Registry**  
 Eventi di accesso al Registro di sistema  
  
 Il provider del kernel può solo essere attivato.  Non è infatti possibile disabilitarlo né modificarne i flag fino allo spegnimento del monitor.  
  
## Note  
  
> [!NOTE]
>  Quando gli eventi ETW CLR sono attivati, nel report Trace View vengono raccolti anche altri dati di avvio.  Per evitare che gli eventi di avvio vengano visualizzati nel report, utilizzare il comando seguente:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Se gli eventi di avvio non vengono esclusi perché non elencati nel file MOF \(Managed Object Format\), verranno visualizzati come GUID nel rapporto.  Per ulteriori informazioni, vedere questa pagina nel sito Web Microsoft: [File di esempio Managed Object Format \(MOF\)](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)