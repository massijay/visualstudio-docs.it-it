---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
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
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia effettua il marshalling delle interfacce correlate al programma oltre i limiti dei processi.  
  
## Sintassi  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia lo stesso oggetto che implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per supportare le interfacce di marshalling oltre i limiti dei processi.  
  
## Note per i chiamanti  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia di `IDebugProgramNode2` per ottenere questa interfaccia.  Se questa interfaccia non può essere ottenuta, il DE non supporta il marshalling delle interfacce.  
  
## Metodi nell'ordine di Vtable  
 questa interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ottiene un'interfaccia specificata mediante i limiti dei processi.|  
  
## Note  
 Questa interfaccia viene implementata quando le esecuzioni di DE in uno spazio del processo separato dal programma sottoposto a debug: ad esempio, quando il DE è in esecuzione nello spazio del processo di Visual Studio anziché lo spazio del processo del programma sottoposto a debug.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)