---
title: "IDebugBinder::GetMemoryContext | Microsoft Docs"
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
  - "IDebugBinder::GetMemoryContext"
helpviewer_keywords: 
  - "Metodo IDebugBinder::GetMemoryContext"
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo converte una posizione dell'oggetto o un indirizzo di memoria in un contesto di memoria.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parametri  
 `pField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Una descrizione dell'oggetto per individuare.  Se `NULL`, quindi utilizza `dwConstant` anziché.  
  
 `dwConstant`  
 \[in\]  un indirizzo di memoria costante, come 0x5000.  
  
 `ppMemCxt`  
 \[out\]  Restituisce [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) l'interfaccia che rappresenta l'indirizzo dell'oggetto, o l'indirizzo in memoria.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)