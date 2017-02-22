---
title: "IDebugProperty2 | Microsoft Docs"
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
  - "IDebugProperty2"
helpviewer_keywords: 
  - "Interfaccia IDebugProperty2"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una proprietà dello stack frame, una proprietà del documento di programma, o un'altra proprietà.  La proprietà è in genere il risultato della valutazione di un'espressione.  
  
> [!NOTE]
>  Questo utilizzo di “proprietà„ non deve essere confuso con tale significato una variabile membro di una classe, sebbene `IDebugProperty2` può rappresentare una tale entità.  
  
## Sintassi  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per rappresentare un particolare tipo di valore.  Ad esempio, il valore può essere un valore numerico come risultato della valutazione di un'espressione, di un contesto di memoria utilizzato per la visualizzazione della memoria, o un elenco di log e i relativi valori.  
  
## Note per i chiamanti  
 Chiamata [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ottenere questa interfaccia, che rappresenta il risultato della valutazione.  `IDebugExpression2::EvaluateAsync` restituisce questa interfaccia inviando [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) un'interfaccia a SDM, che a sua volta chiama [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) per recuperare la proprietà.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) restituisce questa interfaccia per definire il documento associato dello script.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) restituisce questa interfaccia per rappresentare il valore restituito di una funzione.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) restituisce questa interfaccia per rappresentare le varie proprietà del programma come un nome o un contesto di memoria.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) restituisce questa interfaccia per rappresentare le varie proprietà dello stack frame come variabili locali.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProperty2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Compila [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) una struttura che descrive una proprietà.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Imposta il valore della proprietà dal valore di un riferimento specificato.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Enumera gli elementi figlio di una proprietà.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Restituisce l'elemento padre di una proprietà.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|restituisce la proprietà che descrive la proprietà più\-derivata di una proprietà.|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|Restituisce i byte di memoria che costituiscono il valore di una proprietà.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Restituisce il contesto di memoria per un valore di proprietà.|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|Restituisce la dimensione, in byte, del valore della proprietà.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Restituisce un riferimento al valore della proprietà.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Restituisce informazioni estese di una proprietà.|  
  
## Note  
 Una proprietà, come rappresentata da un'interfaccia di `IDebugProperty2` , può essere considerata come un valore con un nome, un tipo e un indirizzo.  In termini più generali, `IDebugProperty2` può rappresentare qualsiasi operazione che in una struttura gerarchica, con elementi padre e i nodi figlio.  
  
 Una proprietà è in genere transitoria, durando solo finché lo stack frame corrente, ad esempio.  Di altra parte, un riferimento, come indicato [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) da un'interfaccia, dura finché il valore rimane in memoria.  
  
 L'ide possibile utilizzare l'interfaccia di `IDebugProperty2` per consentire agli utenti di esplorare e modificare le proprietà in fase di esecuzione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)