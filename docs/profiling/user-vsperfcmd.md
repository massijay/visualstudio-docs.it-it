---
title: "User (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# User (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **User** specifica il dominio e il nome utente dell'account proprietario del processo di profilo.  Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.  
  
 L'opzione **User** può essere specificata solo in una riga di comando che contiene anche l'opzione **Start**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### Parametri  
 `Domain`  
 Il nome del dominio dell'utente.  
  
 `UserName`  
 Nome dell'utente.  
  
## Opzioni obbligatorie  
 L'opzione **User** può essere utilizzata solo con l'opzione **Start**.  
  
 **Start:** `Method`  
 Inizializza il profiler al metodo di profilo specificato.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'opzione **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)