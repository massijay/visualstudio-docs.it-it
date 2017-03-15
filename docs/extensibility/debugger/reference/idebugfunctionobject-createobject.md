---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "Metodo IDebugFunctionObject::CreateObject"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un oggetto utilizzando il costruttore.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### Parametri  
 `pConstructor`  
 \[in\]  [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Un oggetto che rappresenta il costruttore dell'oggetto da creare.  
  
 `dwArgs`  
 \[in\]  Il numero di parametri nella matrice di`pArg` .  Rappresenta il numero dei parametri passati al costruttore.  
  
 `pArg`  
 \[in\]  Una matrice [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) di oggetti che rappresentano i parametri passati al costruttore.  
  
 `ppObject`  
 \[out\]  Restituisce `IDebugObject` che rappresenta l'oggetto appena creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe \(o di altro tipo complesso che richiede un costruttore\) che sia un parametro alla funzione che è rappresentata [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) dall'interfaccia.  
  
 Se il parametro dell'oggetto non richiede un costruttore, chiamare [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) il metodo.  
  
## Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)