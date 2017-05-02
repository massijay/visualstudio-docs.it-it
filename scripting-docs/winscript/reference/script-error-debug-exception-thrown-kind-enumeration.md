---
title: "Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica il tipo di eccezione generata.  Questa enumerazione è utilizzata dal metodo [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md).  
  
> [!IMPORTANT]
>  Queste costanti sono implementate da PDM versione 11.0 e successiva.  Rilevata in activdbg100.h.  
  
## Sintassi  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|ETK\_FIRST\_CHANCE|0x00000000|L'eccezione è un'eccezione first\-chance.|  
|ETK\_USER\_UNHANDLED|0x00000001|L'eccezione non è gestita nel codice utente.|  
|ETK\_UNHANDLED|0x00000002|L'eccezione non è gestita nel codice.|  
  
## Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)