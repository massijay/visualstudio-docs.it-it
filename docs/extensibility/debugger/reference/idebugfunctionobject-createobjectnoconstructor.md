---
title: "IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateObjectNoConstructor"
helpviewer_keywords: 
  - "Metodo IDebugFunctionObject::CreateObjectNoConstructor"
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crea un oggetto senza il costruttore.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### Parametri  
 `pClassObject`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Un oggetto che rappresenta il tipo di oggetto da creare.  
  
 `ppObject`  
 \[out\]  Restituisce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) una rappresentazione dell'oggetto appena creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una struttura o di un tipo complesso \(che non richiede un costruttore\) che sia un parametro alla funzione che è rappresentata [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) dall'interfaccia.  
  
 Se il parametro dell'oggetto richiede un costruttore, chiamare [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) il metodo.  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)