---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
Recupera l'interfaccia `IDispatch` per le proprietà e i metodi associati allo script attualmente in esecuzione.  
  
## Sintassi  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### Parametri  
 `pstrItemName`  
 \[in\] indirizzo di un buffer che contiene il nome dell'elemento per il quale il chiamante disponga dell'oggetto collegato di invio.  Se questo parametro è `NULL`, l'oggetto di invio contiene come membri tutti i metodi globali e le proprietà definite dallo script.  Tramite l'interfaccia `IDispatch` e l'interfaccia collegata `ITypeInfo`, l'host può richiamare i metodi o la visualizzazione dello script e modificare le variabili dello script.  
  
 `ppdisp`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore all'oggetto associato ai metodi globali e le proprietà dello script.  Se il motore di scripting non supporta tale oggetto, `NULL` viene restituito.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di invio; il parametro `ppdisp` è impostato SU NULL.|  
  
## Note  
 Poiché i metodi e le proprietà possono essere aggiunti chiamando l'interfaccia [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md), l'interfaccia `IDispatch` restituito da questo metodo può supportare dinamicamente i nuovi metodi e proprietà.  Analogamente, il metodo `IDispatch::GetTypeInfo` deve restituire una nuova interfaccia, univoca `ITypeInfo` quando i metodi e le proprietà aggiunte.  Si noti, tuttavia, che i motori di linguaggio non devono modificare l'interfaccia `IDispatch` in modo che è incompatibile con un'interfaccia precedente `ITypeInfo` restituita.  Ciò implica, ad esempio, i dispid che non venga riutilizzato mai.  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)