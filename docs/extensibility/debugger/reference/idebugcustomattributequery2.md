---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "Interfaccia IDebugCustomAttributeQuery"
  - "Interfaccia IDebugCustomAttributeQuery2"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina l'esistenza di un attributo personalizzato per questo campo e, se esiste, restituisce le informazioni sugli attributi.  
  
## Sintassi  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia lo stesso oggetto che implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) per supportare attributi personalizzati.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ISAPI.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi **di interfaccia di IDebugCustomAttributeQuery** .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina se un attributo personalizzato esistente per nome.|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|Ottiene le informazioni sull'attributo personalizzato specificato.|  
  
 oltre ai metodi di **IDebugCustomAttributeQuery** , `IDebugCustomAttributeQuery2` implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ottiene un enumeratore per tutti gli attributi personalizzati associati a questo campo.|  
  
## Note  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Il metodo può restituire un enumeratore per tutti gli attributi personalizzati definiti per il campo.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)