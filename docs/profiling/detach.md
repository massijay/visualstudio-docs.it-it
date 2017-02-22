---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Detach** di VSPerfCmd.exe disconnette il profiler dai processi specificati o da tutti i processi se non ne vengono specificati.  Il profilo deve essere stato inizializzato tramite il metodo di campionamento.  
  
 Il profilo avviato con le opzioni **Launch** o **Attach** può essere disconnesso con **Detach**.  Il profiler può essere connesso nuovamente tramite i comandi **Attach** successivi.  
  
 **Detach** non chiude il file dei dati di profilo.  Utilizzare l'opzione **Shutdown** per terminare il profilo e chiudere il file di dati.  
  
> [!NOTE]
>  Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, le chiamate a **VSPerfCmd \/Attach** o **VSPerfCmd \/Detach** devono specificare anche **Crosssession**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Parametri  
 `PIDs|ProcessNames`  
 `PID`: identificatore del sistema numerico di uno o più processi.  
  
 `ProcessNames`: nome del processo.  Se sono in esecuzione più istanze del processo denominato, i risultati sono imprevedibili.  
  
 Separare i processi con virgole.  
  
 Se non viene specificato alcun processo, il profiler viene disconnesso da tutti i processi profilati.  
  
## Opzioni valide  
 Le opzioni **VSPerfCmd** seguenti possono essere combinate con l'opzione **Attach** in una sola riga di comando.  
  
 **Crosssession**  
 Abilita il profilo di applicazioni in sessioni diverse da quella di accesso.  Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.  
  
## Esempio  
 In questo esempio, il comando **Detach** sospende il profilo e il comando **Shutdown** chiude il file di dati del profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)