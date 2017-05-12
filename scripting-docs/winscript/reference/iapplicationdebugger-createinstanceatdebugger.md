---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::CreateInstanceAtDebugger"
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::CreateInstanceAtDebugger
Consente la creazione di oggetti nel processo del debugger dal codice che è out\-of\-process al debugger.  
  
> [!IMPORTANT]
>  Questo metodo non deve essere distribuito, perché consente al codice non attendibile creare oggetti arbitrari in un thread del debugger attendibile.  
  
## Sintassi  
  
```  
HRESULT CreateInstanceAtDebugger(  
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
  
 Il metodo non è attualmente distribuito.  
  
## Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)