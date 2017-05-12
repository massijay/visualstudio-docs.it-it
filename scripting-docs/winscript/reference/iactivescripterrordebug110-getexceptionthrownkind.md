---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
Restituisce un valore che indica il tipo di eccezione generata.  
  
> [!IMPORTANT]
>  [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md) è implementato da PDM versioni 11.0 e successiva.  Rilevata in activdbg100.h.  
  
## Sintassi  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### Parametri  
 `pExceptionKind`  
 \[out\] Tipo di eccezione generato, ad esempio un'eccezione first\-chance o non gestita, rappresentato da un valore di enumerazione [Enumerazione SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md).  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)