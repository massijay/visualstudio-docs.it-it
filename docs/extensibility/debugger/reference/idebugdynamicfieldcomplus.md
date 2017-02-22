---
title: "IDebugDynamicFieldCOMPlus | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugDynamicFieldCOMPlus"
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

rappresenta un campo dinamico per [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) un oggetto.  
  
## Sintassi  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## Metodi  
 Oltre ai metodi [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo fornito il tipo primitivo.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo fornito il relativo token.|  
  
## Requisiti  
 intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll