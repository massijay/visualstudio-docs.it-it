---
title: "IApplicationDebugger::onDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebuggerEvent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebuggerEvent"
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebuggerEvent
Gestisce l'evento dell'applicazione personalizzata.  
  
## Sintassi  
  
```  
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### Parametri  
 `riid`  
 \[in\] identificatore di interfaccia per l'oggetto.  
  
 `punk`  
 \[in\] l'oggetto evento, che implementa l'interfaccia definita da `riid`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è attualmente distribuito.|  
  
## Note  
 La semantica `IUnknown` è completamente applicazione\/debugger definito.  
  
 Questo metodo consente più estensioni personalizzate del modello del debugger, attualmente non viene implementato.  
  
 Questo metodo viene chiamato quando `IDebugApplication::FireDebuggerEvent` viene chiamato.  
  
## Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)