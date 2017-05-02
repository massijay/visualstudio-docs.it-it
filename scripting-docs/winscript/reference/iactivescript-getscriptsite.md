---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
Recupera l'oggetto del sito associato al modulo di gestione di script di windows.  
  
## Sintassi  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### Parametri  
 `iid`  
 \[in\] identificatore di interfaccia richiesta.  
  
 `ppvSiteObject`  
 \[out\] indirizzo della posizione che riceve un puntatore a interfaccia all'oggetto del sito dell'host.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_NOINTERFACE`|l'interfaccia specificata non è supportata.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`S_FALSE`|Nessun sito è stato impostato, il parametro `ppvSiteObject` è impostato su `NULL`.|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)