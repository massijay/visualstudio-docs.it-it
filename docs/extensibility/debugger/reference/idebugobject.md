---
title: "IDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject"
helpviewer_keywords: 
  - "Interfaccia IDebugObject"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un oggetto che lo strumento di associazione crea per incapsulare i valori dei simboli ed espressioni.  
  
## Sintassi  
  
```  
IDebugObject : IUnknown  
```  
  
## Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto.  
  
## Note per chiamanti  
 Questa interfaccia è la classe base per tutti gli oggetti che utilizza l'analizzatore di espressioni nelle espressioni analizzate. Viene restituito da una chiamata al [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md) metodo.[QueryInterface](/visual-cpp/atl/queryinterface) Ottiene le interfacce più specializzate da questa interfaccia.  
  
## Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IDebugObject`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ottiene le dimensioni dell'oggetto.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ottiene il valore dell'oggetto come una serie consecutiva di byte.|  
|[SetValue](../Topic/IDebugObject::SetValue.md)|Imposta il valore dell'oggetto da una serie consecutiva di byte.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Imposta il valore di riferimento di questo oggetto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|Verifica se questo oggetto è un riferimento null.|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|Confronta un oggetto a questa.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina se questo oggetto è di sola lettura.|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina se l'oggetto è un proxy trasparente.|  
  
## Note  
 L'analizzatore di espressioni utilizza questa interfaccia come classe di base per rappresentare gli oggetti in un albero di analisi.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)