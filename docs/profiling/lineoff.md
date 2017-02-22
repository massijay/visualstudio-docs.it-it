---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, il profiler raccoglie il numero di riga del codice sorgente e l'offset del numero di riga quando si utilizza il metodo di profilo campione.  L'opzione **LineOff** di VSPerfCmd consente di disabilitare la raccolta del numero di riga quando si utilizza VSPerfCmd per avviare l'applicazione.  Quando si specifica **LineOff**, i dati di profilo vengono raccolti al livello della funzione.  
  
 È possibile utilizzare **LineOff** solo con l'opzione **Launch** e solo quando il profiler è stato inizializzato per il campionamento tramite l'opzione **Start**: **Sample**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Parametri  
 Nessuno  
  
## Opzioni obbligatorie  
 L'opzione **LineOff** può essere utilizzata unicamente in una riga di comando che contiene l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia l'applicazione specificata e l'operazione di profilo con il metodo di campionamento.  
  
## Esempio  
 In questo esempio vengono avviati l'applicazione e il profiler e viene disabilitato il campionamento a livello di riga.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)