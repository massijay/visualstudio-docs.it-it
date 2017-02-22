---
title: "IDebugPropertyField::GetPropertySetter | Microsoft Docs"
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
  - "IDebugPropertyField::GetPropertySetter"
helpviewer_keywords: 
  - "Metodo IDebugPropertyField::GetPropertySetter"
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene il metodo che imposta la proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```c#  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### Parametri  
 `ppField`  
 \[out\]  restituisce [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) un oggetto che rappresenta il metodo che imposta la proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario restituisce un codice di errore.  
  
## Note  
 per ottenere il metodo che ottiene la proprietà, chiamare [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) il metodo.  
  
## Vedere anche  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)