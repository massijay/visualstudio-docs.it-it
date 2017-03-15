---
title: "IDebugPointerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField"
helpviewer_keywords: 
  - "Interfaccia IDebugPointerField"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta un tipo di puntatore.  
  
## Sintassi  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## Note per gli implementatori  
 Il provider del simbolo implementa questa interfaccia per rappresentare un puntatore.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ISAPI se [GetKind](../Topic/IDebugField::GetKind.md) restituisce `FIELD_TYPE_POINTER`.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi nelle interfacce per `IDebugContainerField` e di `IDebugField` , l'interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) una descrizione della destinazione del puntatore.|  
  
## Note  
 In C\/C\+\+, un puntatore può essere un contenitore se viene utilizzato con notazione di matrice.  Ad esempio, specificata `char *pString`, `pString` dispone di un tipo di puntatore a `char`.  `pString[3]` ha il tipo di contenitore che sia un puntatore a `char` che fa riferimento al quarto elemento del contenitore.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)