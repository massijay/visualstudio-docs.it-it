---
title: "IDebugPropertyField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "Interfaccia IDebugPropertyField"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce funzioni che consentono di ottenere e impostare una proprietà.  
  
## Sintassi  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia lo stesso oggetto che implementa [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md).  Questa interfaccia è una specializzazione che supporta il concetto di proprietà in una classe.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ISAPI se [GetKind](../Topic/IDebugField::GetKind.md) il metodo restituisce `FIELD_KIND_PROP`.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) le interfacce, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|ottiene il metodo che ottiene la proprietà.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|ottiene il metodo che imposta la proprietà.|  
  
## Note  
 Una proprietà è un concetto di codice gestito e rappresenta un metodo che viene considerato come variabile.  le proprietà non esistono in C\+\+ non gestito.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)