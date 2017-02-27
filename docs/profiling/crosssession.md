---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **CrossSession** di VSPerfCmd.exe consente al profiler di raccogliere dati da qualsiasi sessione della console.  L'opzione **CrossSession** deve essere utilizzata con **Start**.  
  
 È possibile utilizzare l'abbreviazione **CS** al posto di **CrossSession**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Parametri  
 Nessuno  
  
## Opzioni valide  
 Per abilitare la profilatura in un'altra sessione, è necessario specificare l'opzione **CrossSession** con l'opzione **Start**.  È necessario specificare **CrossSession** anche in qualsiasi comando **VSPerfCmd Attach** e **Detach**.  
  
 **Start:** `Method`  
 L'opzione **Start** consente di inizializzare il profiler al metodo di profilo specificato.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Avvia la profilatura dei processi specificati.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Interrompe la profilatura dei processi specificati.  
  
## Esempio  
 In questo esempio, l'opzione **CrossSession** viene utilizzata per connettersi a un'applicazione avviata in un'altra sessione della console.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)