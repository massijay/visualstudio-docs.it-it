---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "Interfaccia IDebugPortRequest2"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene descritta una porta.  Questa descrizione viene utilizzata per aggiungere la porta a un fornitore di porte.  
  
## Sintassi  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## Note per gli implementatori  
 Visual Studio in genere implementa questa interfaccia nel processo di ottenere una porta di debug da un fornitore di porte.  
  
## Note per i chiamanti  
 Questa interfaccia viene [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) passato per creare una porta di debug.  Una chiamata [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) a restituisce questa interfaccia, che rappresenta la chiamata utilizzata per creare la porta per primo.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPortRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ottiene il nome della porta a creare.|  
  
## Note  
 Il modulo di debug in genere non interagisce con un fornitore di porte e non si utilizzano per l'interfaccia.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)