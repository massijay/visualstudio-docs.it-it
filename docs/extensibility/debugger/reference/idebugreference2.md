---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "Interfaccia IDebugReference2"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un riferimento a una proprietà dello stack frame o a un'altra proprietà.  
  
> [!NOTE]
>  `IDebugReference2` è riservato per un utilizzo futuro e tutti i metodi restituiscono `E_NOTIMPL`.  
  
## Sintassi  
  
```  
IDebugReference2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per rappresentare un riferimento a un particolare tipo di valore.  Ad esempio, il valore può essere un valore numerico come risultato della valutazione di un'espressione, di un contesto di memoria utilizzato per la visualizzazione della memoria, o un elenco di log e i relativi valori.  
  
## Note per i chiamanti  
 Chiamare [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) per ottenere questa interfaccia.  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) anche [GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md) e restituire questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugReference2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ottiene [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) la struttura che descrive il riferimento.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Imposta il valore di questo riferimento da una stringa.|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|Imposta il valore di questo riferimento da un altro riferimento.|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|Enumera gli elementi figlio di questo riferimento.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ottiene l'elemento padre di questo riferimento.|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|Ottiene il riferimento maggiormente derivato del riferimento.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|ottiene i byte di memoria a cui questo riferimento si riferisce.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ottiene un contesto di memoria di questo riferimento.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ottiene la dimensione, in byte, del riferimento.|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|Imposta questo tipo di riferimento.|  
|[Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Confronta questo riferimento a un altro.|  
  
## Note  
  
> [!NOTE]
>  Questo utilizzo di “proprietà„ non deve essere confuso con tale significato una variabile membro di una classe, sebbene `IDebugReference2` può rappresentare una tale entità.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rappresenta una proprietà, mentre `IDebugReference2` rappresenta un riferimento a una proprietà, in genere un riferimento a un oggetto nel programma sottoposto a debug.  
  
 La differenza principale tra una proprietà e un riferimento è che una proprietà fa riferimento a un'istanza denominata di un oggetto, mentre un riferimento fa riferimento a un'istanza senza nome.  Ad esempio, una proprietà può fare riferimento a un oggetto nell'heap del programma da `"a.b"`.  Un'altra proprietà può fare riferimento allo stesso oggetto di `"c.d"`.  La modalità di fare riferimento a questa proprietà richiede tale `"a.b"` o `"c.d"`ambito.  Un riferimento allo stesso oggetto è senza nome; l'oggetto può fare riferimento a condizione che la memoria per tale oggetto è valida.  
  
 Un'interfaccia di `IDebugProperty2` può essere considerata come un valore con un nome, un tipo e un indirizzo.  `IDebugReference2`, invece, può essere considerato come un tipo e un indirizzo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)