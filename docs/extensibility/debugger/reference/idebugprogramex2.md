---
title: "IDebugProgramEx2 | Microsoft Docs"
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
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramEx2"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente la connessione dell'amministratore di \(SDM\) debug della sessione in un programma e ottiene il nodo del programma associato a un programma.  
  
## Sintassi  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia lo stesso oggetto come [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per consentire la connessione di SDM a un programma mentre contemporaneamente consentendo al fornitore di porte tenere traccia di tutte le sessioni di connessione al programma.  Il fornitore di porte personalizzato può implementare questa interfaccia se scegliere.  
  
## Note per i chiamanti  
 Le chiamate di SDM [QueryInterface](/visual-cpp/atl/queryinterface) su `IDebugProgram2` interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni chiuse associato ai programmi.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProgramEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Associa un programma a una sessione.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo del programma associato a un programma.|  
  
## Note  
 Questa interfaccia è privata tra lo SDM e il programma.  
  
## Requisiti  
 intestazione: Portpriv.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)