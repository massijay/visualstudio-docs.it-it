---
title: "IEnumDebugPropertyInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2"
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia enumera [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) le strutture.  
  
## Sintassi  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per rappresentare le informazioni per una determinata proprietà.  
  
## Note per i chiamanti  
 Chiamare [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere questa interfaccia che rappresenta gli elementi figlio di una particolare proprietà.  Chiamare [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md) per ottenere questa interfaccia che rappresenta le proprietà di uno stack frame specifico.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugPropertyInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un numero specificato [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) di strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora un numero specificato [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) di strutture in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../Topic/IEnumDebugPropertyInfo2::GetCount.md)|Ottiene il numero [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) di strutture in un enumeratore.|  
  
## Note  
 Una proprietà è solitamente una gerarchia di informazioni che può includere un nome, valore, il routing e di tipo nonché qualsiasi altra informazione appropriata all'oggetto o allo stack frame della proprietà associata.  Per ulteriori informazioni, vedere [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)