---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Elimina l'ID univoco associato a questa proprietà, per indicare che il chiamante non è più preoccupa per identificare questa proprietà in modo univoco da tutte le altre proprietà.  
  
## Sintassi  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se il motore di debug non deve supportare gli identificatori univoci di una proprietà \(in quanto vengono registrati in modo univoco internamente\), può restituire semplicemente `E_NOTIMPL` per il metodo.  
  
 Gli identificatori univoci vengono creati mediante una chiamata [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) al metodo quando il chiamante desidera assicurarsi che questa proprietà in modo univoco sia identificata da tutte le altre proprietà.  
  
## Vedere anche  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)