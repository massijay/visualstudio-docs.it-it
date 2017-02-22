---
title: "IDebugArrayObject | Microsoft Docs"
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
  - "IDebugArrayObject"
helpviewer_keywords: 
  - "Metodo IDebugArrayObject"
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un oggetto matrice.  
  
## Sintassi  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare una matrice.  
  
## Note per chiamanti  
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia è possibile ottenere questa interfaccia tramite [QueryInterface](/visual-cpp/atl/queryinterface) Se l'oggetto rappresenta una matrice.  
  
## Metodi nell'ordine Vtable  
 Oltre ai metodi nel `IDebugObject` interfaccia, i seguenti metodi sono implementati nel `IDebugArrayObject` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ottiene il numero di elementi nella matrice.|  
|[GetElement](../Topic/IDebugArrayObject::GetElement.md)|Ottiene un elemento della matrice.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ottiene tutti gli elementi della matrice.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ottiene il rango della matrice.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ottiene le dimensioni della matrice.|  
  
## Note  
 Un analizzatore di espressioni utilizza questa interfaccia per rappresentare le matrici in una struttura di analisi.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)