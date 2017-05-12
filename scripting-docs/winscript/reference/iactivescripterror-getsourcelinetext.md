---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
Recupera la riga del codice sorgente in cui si è verificato un errore durante un motore di scripting stava eseguendo uno script.  
  
## Sintassi  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## Parametro  
 `pbstrSourceLine`  
 \[out\] indirizzo di un buffer che riceve la riga di codice sorgente in cui si è verificato l'errore.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL` se la riga nel file di origine non è stata recuperata.  
  
## Vedere anche  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)