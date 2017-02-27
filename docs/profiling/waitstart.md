---
title: "WaitStart | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# WaitStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione WaitStart comporta che il sottocomando Start VSPerfCmd.exe restituisca un risultato solo in seguito all'inizializzazione del profiler o una volta trascorso il numero di secondi specificato.  Per impostazione predefinita, il comando Avvia viene immediatamente restituito.  Se il sotto comando Avvio ritorna senza inizializzare il profiler, viene restituito un errore.  Se non è specificato il numero di secondi, il comando Avvio attende indefinitamente.  
  
 L'opzione WaitStart è utile nei file batch per assicurarsi che il profiler sia stato inizializzato.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### Parametri  
 `Seconds`  
 Numero di secondi di attesa prima del ritorno dal sottocomando di avvio.  
  
## Opzioni obbligatorie  
 L'opzione WaitStart può essere utilizzata con il sottocomando Start.  
  
 **Output:** `filename`  
 Specifica il nome del file di output.  
  
## Note  
  
## Esempio  
 In questo esempio di file batch, il comando Start attenderà 5 secondi affinché il profiler venga inizializzato.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```