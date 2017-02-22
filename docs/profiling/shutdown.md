---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Shutdown** attende il termine o la disconnessione del processo correntemente profilato, quindi disattiva il profiler e chiude il file dei dati di profilo.  L'opzione **Shutdown** deve essere l'ultimo comando dell'esecuzione di un profilo.  
  
 Se non è specificato un parametro del timeout, l'attesa dell'opzione **Shutdown** è infinita.  Se viene specificato un parametro del timeout, l'opzione restituisce un risultato dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file di dati.  
  
 **Shutdown** deve essere l'unica opzione specificata nella riga di comando.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Parametri  
 `Timeout`  
 -   \(Facoltativo\) Se viene specificato un parametro del timeout, l'opzione restituisce un risultato dopo il numero di secondi specificato senza disattivare il profiler o chiudere il file dei dati di profilo.  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)