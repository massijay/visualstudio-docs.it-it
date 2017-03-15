---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **WinCounter** specifica un contatore delle prestazioni Windows e delle applicazioni di cui raccogliere i dati a intervalli regolari durante l'esecuzione del profilo.  I contatori di prestazioni Windows e delle applicazioni vengono elencati come contrassegni nel file dei dati di profilo.  È possibile specificare più contatori di prestazioni di cui raccogliere i dati in opzioni separate.  
  
 Per impostazione predefinita, i dati dei contatori vengono raccolti ogni 500 millisecondi.  Utilizzare l'opzione **AutoMark** per specificare un'intervallo di raccolta diverso.  
  
 Viene utilizzata una sola opzione **AutoMark**.  Se si specificano più opzioni **AutoMark**, viene utilizzata l'ultima.  
  
 L'opzione **WinCounter** può essere utilizzata solo con l'opzione **Start**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Parametri  
 `Path`  
 contatore delle prestazioni Windows nel percorso del contatore in formato PDH.  
  
## Opzioni obbligatorie  
 L'opzione **WinCounter** può essere utilizzata solo con l'opzione **Start**.  
  
 **Start:** `Method`  
 L'opzione **Start** consente di inizializzare il profiler al metodo di profilo specificato.  
  
## Opzioni esclusive  
 L'opzione **AutoMark** può essere utilizzata solo con l'opzione **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Specifica il numero di millisecondi tra le raccolte di dati del contatore delle prestazioni Windows.  
  
## Esempio  
 Nell'esempio seguente, vengono specificati due contatori di prestazioni Windows di cui raccogliere i dati a un intervallo di 1000 millisecondi.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)