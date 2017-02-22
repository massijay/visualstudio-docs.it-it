---
title: "IDebugEnumField | Microsoft Docs"
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
  - "IDebugEnumField"
helpviewer_keywords: 
  - "Interfaccia IDebugEnumField"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un tipo di enumerazione.  
  
## Sintassi  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia per rappresentare enumerazione.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ISAPI se [GetKind](../Topic/IDebugField::GetKind.md) restituisce `FIELD_TYPE_ENUM`.  
  
## Metodi nell'ordine di VTable  
 Oltre ai metodi nelle interfacce per `IDebugContainerField` e di `IDebugField` , l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) una descrizione del nome per questo tipo di enumerazione.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Restituisce il nome del controllo associato costante di enumerazione con il valore specificato.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Restituisce il valore associato al nome di una costante di enumerazione specificata|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|Restituisce il valore associato al nome di una costante di enumerazione specificata ma che viene ignorata.|  
  
## Note  
 È il simbolo sottostante cui viene effettivamente associato a una posizione protetta [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)