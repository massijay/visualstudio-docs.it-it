---
title: "IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CreateInstanceAtApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CreateInstanceAtApplication"
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::CreateInstanceAtApplication
Consente la creazione di oggetti nel processo dell'applicazione dal codice che è out\-of\-process all'applicazione.  
  
## Sintassi  
  
```  
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### Parametri  
 `rclsid`  
 \[in\] identificatore di classe \(CLSID\) dell'oggetto da creare.  
  
 `pUnkOuter`  
 \[in\] se `NULL`, l'oggetto non viene creato come parte di un'operazione di aggregazione.  In caso contrario, `pUnkOuter` è un puntatore a interfaccia di aggregazione `IUnknown` dell'oggetto \( `IUnknown`di controllo.  
  
 `dwClsContext`  
 \[in\] contesto del codice eseguibile in esecuzione.  I valori vengono ottenuti dall'enumerazione `CLSCTX`.  
  
 `riid`  
 \[in\] identificatore di interfaccia utilizzata per comunicare con l'oggetto.  
  
 `ppvObject`  
 \[out\] Indirizzo della variabile puntatore che riceve il puntatore a interfaccia richiesto in `riid`.  Nel ritorno, \*`ppvObject` contiene un puntatore a interfaccia richiesta.  Quando si verifica un errore, \*`ppvObject` contiene `NULL`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Delegati di questo metodo a `CoCreateInstance`.  
  
## Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)