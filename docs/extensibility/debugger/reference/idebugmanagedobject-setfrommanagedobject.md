---
title: "IDebugManagedObject::SetFromManagedObject | Microsoft Docs"
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
  - "IDebugManagedObject::SetFromManagedObject"
helpviewer_keywords: 
  - "Metodo IDebugManagedObject::SetFromManagedObject"
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore dell'istanza dell'oggetto classe di valore dall'istanza della classe di valore fornito come parametro.  
  
## Sintassi  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```c#  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### Parametri  
 `pManagedObject`  
 \[in\]  un'interfaccia che rappresenta l'oggetto gestito che contiene il nuovo valore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene utilizzato per modificare l'oggetto gestito come rappresentato [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) dall'oggetto.  
  
## Vedere anche  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)