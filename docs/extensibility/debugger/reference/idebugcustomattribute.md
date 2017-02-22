---
title: "IDebugCustomAttribute | Microsoft Docs"
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
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "Interfaccia IDebugCustomAttribute"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un attributo personalizzato e può fornire il nome, l'attività padre e il tipo della classe dell'attributo.  
  
## Sintassi  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia per supportare gli attributi personalizzati associati a un simbolo.  In genere viene implementato nel relativo oggetto.  
  
## Note per i chiamanti  
 Una chiamata [Successivo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) a restituisce questa interfaccia.  Una chiamata [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) al metodo restituirà [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugCustomAttribute`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|Ottiene il campo il cui attributo corrente è collegato.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ottiene il tipo della classe di attributi personalizzati.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ottiene il nome dell'attributo personalizzato.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ottiene informazioni su come BLOB di byte.|  
  
## Note  
 Un attributo personalizzato è una struttura per c\# che fornisce di metadati associato personalizzato a una classe o un metodo specifico.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)