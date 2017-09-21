---
title: "IDebugObject::SetReferenceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::SetReferenceValue"
helpviewer_keywords: 
  - "Metodo IDebugObject::SetReferenceValue"
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore di riferimento dell'oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```c#  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### Parametri  
 `pObject`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un oggetto che rappresenta il nuovo valore di riferimento.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo crea a questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto un riferimento al valore dell'oggetto specificato nel parametro di `pObject` , generando tramite qualsiasi riferimento precedente.  Si noti che questo oggetto di `IDebugObject` deve essere già un tipo di riferimento.  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)