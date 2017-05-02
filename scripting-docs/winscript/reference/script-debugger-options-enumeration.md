---
title: "Enumerazione SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Enumerazione SCRIPT_DEBUGGER_OPTIONS"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Enumerazione SCRIPT_DEBUGGER_OPTIONS
Indica un set di opzioni di funzionalità e\/o che si applicano al debugger collegato.  Utilizzato in [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e in [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Queste costanti sono implementate da PDM v10.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|SDO\_NONE|0x00000000|Non è impostata alcuna opzione.|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|Indica che il runtime di script devono generare eventi di BREAKREASON\_ERROR quando viene generata un'eccezione.  Questa opzione può essere impostata dal debugger, o dal set dal codice utente tramite `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|Indica che il debugger collegato supporta i lavoratori Web.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)