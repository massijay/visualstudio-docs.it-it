---
title: "IEnumDebugAddresses | Microsoft Docs"
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
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "Interfaccia IEnumDebugAddresses"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una raccolta di oggetti che [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) implementano l'interfaccia.  
  
## Sintassi  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata dal provider dei simboli per fornire insiemi di oggetti che implementano [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) l'interfaccia.  Si noti che questa non è un'enumerazione standard COM a causa della presenza [GetCount](../Topic/IEnumDebugAddresses::GetCount.md) del metodo.  
  
## Note per i chiamanti  
 Questa interfaccia viene restituita da [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md).  
  
## Metodi nell'ordine di Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../Topic/IEnumDebugAddresses::Next.md)|Recupera il set [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) di oggetti dall'enumerazione.|  
|[Skip](../Topic/IEnumDebugAddresses::Skip.md)|Ignora un numero specificato di voci.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Reimposta l'enumerazione alla prima voce.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|Recupera il numero di voci dell'enumerazione.|  
  
## Note  
 Questa interfaccia in genere utilizzata dal motore di debug per determinare l'indirizzo appropriato per fornire analizzatore di espressioni.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)