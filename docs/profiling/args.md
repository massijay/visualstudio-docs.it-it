---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Args** di VSPerfCmd.exe consente di specificare un elenco di argomenti passati all'applicazione di destinazione del sottocomando **Launch**.  
  
 **Args** può essere utilizzata solo quando anche **Launch** è specificata nella riga di comando.  **Args** è facoltativa quando **Launch** è specificata.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### Parametri  
 `Arguments`  
 Elenco di argomenti per l'applicazione di destinazione del comando **Launch**.  
  
## Opzioni obbligatorie  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'operazione di profilo con il metodo di campionamento.  
  
## Esempio  
 Nell'esempio seguente viene utilizzata l'opzione **Args** per passare argomenti a TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)