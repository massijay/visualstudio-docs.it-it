---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
Recupera lo stato corrente del motore di scripting.  Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Sintassi  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### Parametri  
 `pss`  
 \[out\] l'indirizzo di una variabile che riceve un valore definito nell'enumerazione [Enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md).  Il valore indica lo stato corrente del motore di scripting associato al thread chiamante.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_POINTER` se un puntatore non valido è stato specificato.  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)