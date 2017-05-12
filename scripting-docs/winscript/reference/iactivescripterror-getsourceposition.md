---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
Recupera il percorso nel codice sorgente in cui si è verificato un errore durante il motore di scripting stava eseguendo uno script.  
  
## Sintassi  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### Parametri  
 `pdwSourceContext`  
 \[out\] indirizzo di una variabile che riceve un cookie che identificano il contesto.  L'interpretazione di questo parametro dipende dall'applicazione host.  
  
 `pulLineNumber`  
 \[out\] indirizzo di una variabile che riceve il numero di riga del codice sorgente in cui si è verificato l'errore.  
  
 `pichCharPosition`  
 \[out\] indirizzo di una variabile che riceve la posizione del carattere della riga in cui si è verificato l'errore.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL` se la posizione non è stata recuperata.  
  
## Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)