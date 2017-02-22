---
title: "IDebugPortNotify2 | Microsoft Docs"
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
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "Interfaccia IDebugPortNotify2"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia registra o annulla la registrazione di un programma che può essere eseguito il debug con la porta che viene eseguito.  
  
## Sintassi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per supportare l'aggiunta e programmi rimuovere dalla porta.  In genere viene implementato lo stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) l'interfaccia.  
  
## Note per i chiamanti  
 Una chiamata [QueryInterface](/visual-cpp/atl/queryinterface) sull'interfaccia di `IDebugPort2` restituisce questa interfaccia.  Inoltre, una chiamata [GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md) a restituisce questa interfaccia.  Il modulo di debug possibile visualizzare questa interfaccia come parametro a [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPortNotify2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma che può essere eseguito il debug con la porta che viene eseguito.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma che è possibile eseguire il debug dalla porta che viene eseguito.|  
  
## Note  
 A meno che una porta di debug disponga di riconoscere quando i programmi vengono caricati o scaricati, un fornitore di porte personalizzato deve implementare questa interfaccia.  Tutti i programmi caricati per eseguire il debug da una porta specifica vengono rilevati utilizzando questa interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)