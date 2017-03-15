---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **AutoMark** specifica il numero di millisecondi tra gli insiemi di eventi di raccolta dati del contatore delle prestazioni software di Windows.  I contatori di prestazioni Windows vengono specificati nell'opzione **WinCounter**.  
  
 È possibile specificare una sola opzione **AutoMark** sulla riga di comando.  Si noti che l'intervallo di campionamento **WinCounter** specificato da **AutoMark** è indipendente dall'intervallo di campionamento principale.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Parametri  
 `Milliseconds`  
 Specifica il numero di millisecondi tra le raccolte di eventi del contatore delle prestazioni Windows.  
  
## Opzioni obbligatorie  
 **WinCounter:** `Path`  
 Specifica il contatore delle prestazioni Windows di cui raccogliere i dati.  Quando si utilizza il metodo di strumentazione, è possibile specificare più contatori di Windows.  Quando si utilizza il metodo di campionamento, è possibile specificare un solo contatore software.  È necessario specificare l'opzione **WinCounter** in una riga di comando che contiene l'opzione **Start**.  
  
## Esempio  
 In questo esempio, viene impostato un intervallo di campionamento di 1000 millisecondi per due contatori di prestazioni Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)