---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "Metodo IDebugFunctionObject::CreatePrimitiveObject"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un oggetto dati primitivo, ad esempio un Integer semplice.  
  
## Sintassi  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### Parametri  
 `ot`  
 \[in\]  Un valore [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) dell'enumerazione che rappresenta il tipo di dati primitivi da creare.  
  
 `ppObject`  
 \[out\]  Restituisce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) una rappresentazione dell'oggetto appena creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un oggetto primitivo che è un parametro alla funzione che è rappresentata [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) dall'interfaccia.  Ad esempio, se la stringa dell'espressione “myString \(5\)„, questo metodo viene utilizzato per creare un oggetto che rappresenta i 5. Integer.  
  
## Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)