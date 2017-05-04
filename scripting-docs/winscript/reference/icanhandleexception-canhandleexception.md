---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
Determina se il chiamante del modulo di gestione di script può gestire un'eccezione specificata.  
  
## Sintassi  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### Parametri  
 `pExcepInfo`  
 \[in\] puntatore a una struttura `EXCEPINFO` contenente informazioni che verranno segnalate se non viene trovato alcun gestore di eccezioni.  
  
 `pvar`  
 \[in\] il valore di Su è associato all'eccezione, come valore generato da un'istruzione `throw`.  Il parametro può essere `NULL`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il chiamante può gestire l'eccezione|  
|`E_FAIL`|Il chiamante non può gestire l'eccezione.|  
  
## Note  
 Se una chiamata a `IDispatchEx::InvokeEx`, o sul metodo, genera un'eccezione, il modulo di gestione di script di un chiamante nella catena del chiamante di script che supporta l'interfaccia `ICanHandleException` e indica che può gestire l'eccezione.  Se nessun chiamante può gestire l'eccezione, il motore di gestione di script termina.  
  
## Vedere anche  
 [Interfaccia ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)