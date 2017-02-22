---
title: "IDebugErrorEvent2 | Microsoft Docs"
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
  - "IDebugErrorEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugErrorEvent2"
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia specifica un messaggio di errore da segnalare all'utente.  
  
## Sintassi  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per la segnalazione degli errori come messaggi leggibili.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per segnalare un errore.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 questa interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetErrorMessage`|restituisce un errore come stringa leggibile.|  
  
## Note  
 Se il motore di debug si verifica un errore, può utilizzare questa interfaccia per indicare il messaggio con Visual Studio all'utente.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)