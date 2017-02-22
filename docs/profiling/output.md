---
title: "Output | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Output** specifica il nome del file dei dati di profilo per la sessione di prestazioni.  **Output** deve essere utilizzata con l'opzione **Start**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parametri  
 `FileName`  
 Nome del file di dati.  Sono accettati i percorsi completi e parziali.  Se non si specifica un percorso, il file viene creato nella directory corrente.  
  
## Opzioni obbligatorie  
 L'opzione **Output** deve essere utilizzata con **Start**.  
  
 **Start:** `Method`  
 Specifica il nome del file di output.  
  
## Esempio  
 Nell'esempio seguente viene creato un file dei dati di profilo nella directory corrente.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)