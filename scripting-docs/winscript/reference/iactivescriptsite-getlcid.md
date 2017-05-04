---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
Recupera l'identificatore impostazioni locali associato all'interfaccia utente dell'host.  Il motore di scripting utilizzato l'identificatore per assicurare che le stringhe di errore e altri elementi di interfaccia utente generati dal motore vengono visualizzati nel linguaggio appropriato.  
  
## Sintassi  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### Parametri  
 `plcid`  
 \[out\] l'indirizzo di una variabile che riceve l'identificatore impostazioni locali per gli elementi dell'interfaccia utente viene visualizzato nel motore di scripting.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_NOTIMPL`|Il metodo non è implementato.  Utilizzare le impostazioni locali definite dal sistema.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
  
## Note  
 Se questo metodo restituisce `E_NOTIMPL`, l'identificatore impostazioni locali definito dal sistema deve essere utilizzato.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)