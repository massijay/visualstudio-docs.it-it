---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
Stabilisce una connessione tra l'oggetto semplice del punto di connessione e il sink del client.  
  
## Sintassi  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### Parametri  
 `pdisp`  
 \[in\] puntatore all'interfaccia `IDispatch` il sink di notifica del client.  Il sink del client riceve le chiamate in uscita dal punto di connessione semplice.  
  
 `pdwCookie`  
 \[out\] puntatore a un token restituito che identifica in modo univoco questa connessione.  Il chiamante utilizza più avanti in l token per eliminare la connessione passandola al metodo `ISimpleConnectionPoint::Unadvise`.  Se la connessione corretta non è stata stabilita, questo valore è zero.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo stabilisce una connessione tra l'oggetto semplice del punto di connessione e il sink del client.  
  
## Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)