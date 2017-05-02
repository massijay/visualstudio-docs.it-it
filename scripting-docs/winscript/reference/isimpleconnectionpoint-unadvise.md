---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.  
  
## Sintassi  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### Parametri  
 `dwCookie`  
 \[in\] token di connessione da terminare, restituiti da `ISimpleConnectionPoint::Advise`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Quando una connessione consultiva è terminata, il punto di connessione chiama il metodo `Release` sul puntatore che è stato salvato per la connessione durante il metodo `ISimpleConnectionPoint::Advise`.  La chiamata viene invertito `AddRef` in cui è stato eseguito durante `ISimpleConnectionPoint::Advise` quando il punto di connessione chiama `QueryInterface`il sink consultivo.  
  
## Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)