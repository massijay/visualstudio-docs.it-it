---
title: "IEnumDebugFields | Microsoft Docs"
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
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "Interfaccia IEnumDebugFields"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una raccolta di oggetti che [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) implementano l'interfaccia.  
  
## Sintassi  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata dal provider dei simboli per fornire insiemi di oggetti che implementano [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) l'interfaccia.  Si noti che questa non è un'enumerazione standard COM a causa della presenza [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) del metodo.  
  
## Note per i chiamanti  
 Questa interfaccia viene restituita da [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md) e [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## Metodi nell'ordine di Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Recupera il set [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) di oggetti dall'enumerazione.|  
|[Skip](../Topic/IEnumDebugFields::Skip.md)|Ignora un numero specificato di voci.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Reimposta l'enumerazione alla prima voce.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Recupera il numero di voci dell'enumerazione.|  
  
## Note  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)