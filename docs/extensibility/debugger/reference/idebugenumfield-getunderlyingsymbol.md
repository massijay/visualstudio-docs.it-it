---
title: "IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs"
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
  - "IDebugEnumField::GetUnderlyingSymbol"
helpviewer_keywords: 
  - "Metodo IDebugEnumField::GetUnderlyingSymbol"
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) un oggetto che rappresenta il nome dell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### Parametri  
 `ppField`  
 \[out\]  Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) la descrizione del nome dell'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il nome dell'enumerazione contiene anche il tipo dell'enumerazione, associato a una posizione di memoria utilizzando [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)