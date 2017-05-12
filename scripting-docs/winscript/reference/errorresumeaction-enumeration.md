---
title: "Enumerazione ERRORRESUMEACTION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione ERRORRESUMEACTION"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Enumerazione ERRORRESUMEACTION
Viene descritto come passare da un errore di runtime.  
  
## Sintassi  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|Esegue nuovamente l'istruzione che ha generato l'errore.|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|Consente al motore di linguaggio gestire l'errore.|  
|ERRORRESUMEACTION\_SkipErrorStatement|Riprende l'esecuzione nel codice che segue l'istruzione che ha generato l'errore.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)