---
title: "IEnumDebugObjects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects"
helpviewer_keywords: 
  - "Interfaccia IEnumDebugObjects"
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia.  
  
## Sintassi  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per specificare set di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia. Si noti che questo non è un'enumerazione COM standard a causa della presenza di [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) metodo.  
  
## Note per chiamanti  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) Restituisce questa interfaccia.  
  
## Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera il set successivo di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora un numero specificato di voci.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera il numero di voci nell'enumerazione.|  
  
## Note  
 Questa interfaccia consente a un motore di debug enumerare un set di oggetti in una matrice.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)