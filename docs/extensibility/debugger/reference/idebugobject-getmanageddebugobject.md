---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
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
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "Metodo IDebugObject::GetManagedDebugObject"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una copia dell'oggetto gestito nello spazio degli indirizzi del motore di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### Parametri  
 `ppObject`  
 \[out\]  Restituisce [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) un oggetto che rappresenta l'oggetto gestito appena creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  Restituisce E\_FAIL se questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) non rappresenta un'istanza della classe gestita di valore.  
  
## Note  
 Tale [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto deve rappresentare un'istanza della classe gestita di valore, come un'istanza di `System.Decimal` .  Una copia locale, il sovraccarico di chiamare [Valutare](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) viene eliminato.  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)