---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
Notifica al motore di scripting del sito dell'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornito dall'host.  Chiamare questo metodo prima che tutti gli altri metodi di interfaccia [IActiveScript](../../winscript/reference/iactivescript.md) sia utilizzato.  
  
## Sintassi  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### Parametri  
 `pScriptSite`  
 \[in\] indirizzo del sito host fornito lo script da associare a questa istanza del motore di scripting.  Il sito deve in modo univoco possibile assegnare a questa istanza del motore di scripting; non può essere condiviso con altri moduli di gestione di script.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_FAIL`|Un errore non specificato è stato estratto, il motore di scripting non è in grado di completare l'inizializzazione del sito.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio un sito è già stato impostato\).|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)