---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
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
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "Metodo IDebugBinder::ResolveRuntimeType"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo determina il tipo di runtime di un oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### Parametri  
 `pObject`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Essere risolto.  
  
 `ppResolved`  
 \[out\]  Restituisce il tipo di oggetto come [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il tipo di runtime di oggetto non è noto sempre in fase di compilazione.  Ad esempio, utilizzando il polimorfismo, un argomento può essere passato a una funzione come la classe base, come una classe del pulsante.  Effettivo argomento di una classe derivata, come una classe del pulsante di opzione.  
  
## Vedere anche  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)