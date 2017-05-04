---
title: "Enumerazione BREAKRESUMEACTION | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione BREAKRESUMEACTION"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Enumerazione BREAKRESUMEACTION
Descrive come proseguire da un punto di interruzione.  
  
## Sintassi  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|BREAKRESUMEACTION\_ABORT|Interrompe l'applicazione.|  
|BREAKRESUMEACTION\_CONTINUE|Continua l'esecuzione.|  
|BREAKRESUMEACTION\_STEP\_INTO|Esegue l'istruzione di una routine.|  
|BREAKRESUMEACTION\_STEP\_OVER|Ignora una routine.|  
|BREAKRESUMEACTION\_STEP\_OUT|Esce dalla routine corrente.|  
|BREAKRESUMEACTION\_IGNORE|Continua l'esecuzione con lo stato.|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|Passa al documento successivo.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)