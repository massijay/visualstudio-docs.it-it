---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
Inserisce il modulo di gestione di scripting in stato specificato.  Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Sintassi  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### Parametri  
 `ss`  
 \[in\] imposta il motore di scripting stato specificato.  Può essere uno dei valori definiti nell'enumerazione [Enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md).  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_FAIL`|Il motore di scripting non supporta la transizione di nuovo allo stato inizializzato.  L'host deve rimuovere il motore di scripting e creare, l'inizializzazione e caricare un nuovo modulo di gestione di script per ottenere lo stesso risultato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\) e pertanto non è stata avuto esito negativo.|  
|`OLESCRIPT_S_PENDING`|Il metodo è stata accodata correttamente, ma lo stato non è stato ancora.  Quando i cambiamenti di stato, il sito verranno chiamati dal metodo [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).|  
|`S_FALSE`|Il metodo corretto, ma lo script era già stato specificato.|  
  
## Note  
 Per ulteriori informazioni sugli stati del motore di script, vedere gli stati del modulo di gestione di script la sezione [Motori di script Windows](../../winscript/windows-script-engines.md).  
  
## Vedere anche  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)