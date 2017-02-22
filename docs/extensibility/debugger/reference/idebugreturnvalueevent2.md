---
title: "IDebugReturnValueEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2"
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione dopo avere eseguito l'istruzione da o su una funzione.  
  
## Sintassi  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per fornire il valore restituito da una funzione da cui è stato eseguito l'istruzione o più.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per fornire il valore restituito di una funzione.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è associata al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugReturnValueEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Ottiene il valore restituito o l'esecuzione di istruzioni da una funzione.|  
  
## Note  
 il valore restituito da una funzione può essere ottenuto chiamando [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md).  Il valore restituito viene visualizzato nella finestra di **automobili** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)