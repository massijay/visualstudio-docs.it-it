---
title: "Enumerazione BREAKREASON | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione BREAKREASON"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Enumerazione BREAKREASON
Indica che causa l'interruzione.  
  
## Sintassi  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKREASON\_STEP|Il motore di linguaggio è in modalità di esecuzione di istruzioni.|  
|BREAKREASON\_BREAKPOINT|Il motore di linguaggio ha rilevato un punto di interruzione esplicito.|  
|BREAKREASON\_DEBUGGER\_BLOCK|Il motore del linguaggio ha rilevato un blocco del debugger in un altro thread.|  
|BREAKREASON\_HOST\_INITIATED|L'host ha richiesto di interruzione.|  
|BREAKREASON\_LANGUAGE\_INITIATED|Il motore di linguaggio richiedeva di interruzione.|  
|BREAKREASON\_DEBUGGER\_HALT|L'ide del debugger ha richiesto di interruzione.|  
|BREAKREASON\_ERROR|Un errore di esecuzione ha causato l'interruzione.|  
|BREAKREASON\_JIT|Causato dall'avvio del debug JIT.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)