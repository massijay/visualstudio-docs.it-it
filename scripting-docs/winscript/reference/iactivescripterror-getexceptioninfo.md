---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
Recupera le informazioni su un errore che si è verificato quando il motore di scripting stava eseguendo uno script.  
  
## Sintassi  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### Parametri  
 `pexcepinfo`  
 \[out\] indirizzo di una struttura `EXCEPINFO` che riceve informazioni sugli errori.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL` se si è verificato un errore.  
  
## Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)