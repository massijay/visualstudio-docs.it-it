---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **GC** consente di abilitare la raccolta dei dati sull'allocazione di memoria di .NET Framework e sulla durata degli oggetti.  L'opzione **GC** può essere utilizzata unicamente con il metodo di profilo campione e solo con l'opzione **Launch**.  
  
 Quando si utilizza l'opzione **GC**, il comando **\/sampleon** di VSPerfClrEnv non è obbligatorio.  
  
 Se non viene specificato alcun parametro o se viene specificato il parametro **Allocation**, verranno raccolti solo i dati sull'allocazione di memoria di .NET Framework.  Se viene specificato il parametro **Lifetime**, vengono raccolti sia i dati sull'allocazione di memoria sia i dati sulla durata degli oggetti di .NET Framework.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Parametri  
 **Allocation**  
 Predefinito.  Raccoglie i dati sull'allocazione di memoria .NET.  
  
 **Lifetime**  
 Raccoglie i dati sull'allocazione di memoria e sulla durata degli oggetti di memoria .NET.  
  
## Opzioni obbligatorie  
 L'opzione **GC** può essere utilizzata solo con l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'operazione di profilo con il metodo di campionamento.  
  
## Esempio  
 Nell'esempio seguente viene avviata un'applicazione e vengono raccolti dati sull'allocazione di memoria di .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)