---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramNode2"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma che può essere eseguito il debug.  
  
## Sintassi  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il modulo di \(DE\) debug o un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un programma che può essere eseguito il debug.  Questa interfaccia in genere viene implementata nello stesso oggetto che implementa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) l'interfaccia.  Questa interfaccia registrata con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## Note per i chiamanti  
 Chiamare [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per restituire questa interfaccia.  un fornitore di porte personalizzato riceve questa interfaccia con una chiamata a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  Un DE riceve questa interfaccia con una chiamata a [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProgramNode2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|ottiene il nome di un programma.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ottiene il nome di hosting di un programma.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ottiene l'identificatore di processo di sistema per l'hosting di un programma.|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|DEPRECATO.  NOT UTILIZZARE.|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|DEPRECATO.  NOT UTILIZZARE.  vedere [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) l'interfaccia per un'alternativa.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ottiene il nome e l'identificatore di DE running questo programma.|  
|[DetachDebugger\_V7](../Topic/IDebugProgramNode2::DetachDebugger_V7.md)|DEPRECATO.  NOT UTILIZZARE.|  
  
## Note  
 La sessione di debug delle \(SDM\) chiamate in genere [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per ottenere questa interfaccia.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)