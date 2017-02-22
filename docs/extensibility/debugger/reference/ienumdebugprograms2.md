---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia enumera i programmi in esecuzione nella sessione di debug corrente.  
  
## Sintassi  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per definire un elenco di programmi in corso il debug da DE.  
  
## Note per i chiamanti  
 chiamate di Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) per ottenere questa interfaccia.  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) non viene utilizzato da Visual Studio.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugPrograms2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../Topic/IEnumDebugPrograms2::Next.md)|Recupera un numero specificato di programmi in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora un numero specificato di programmi in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../Topic/IEnumDebugPrograms2::Clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|Ottiene il numero dei programmi in un enumeratore.|  
  
## Note  
 Visual Studio utilizza questa interfaccia:  
  
-   Popolare la finestra di **moduli** chiamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) quindi chiamando [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) su ogni programma\).  
  
-   Compilare l'elenco di **Connettersi da elaborare** chiamando `IDebugProcess2::EnumPrograms` quindi chiamando [QueryInterface](/visual-cpp/atl/queryinterface) su ogni [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per ottenere [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) un'interfaccia\).  
  
-   Compilare un elenco di DES in grado di eseguire il debug ogni programma nel processo [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)mediante.  
  
-   Applicare aggiornamenti di Modifica e continuazione \(ENC\) a ogni programma \(chiamando IDebugProcess2:: EnumPrograms quindi chiamare [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)