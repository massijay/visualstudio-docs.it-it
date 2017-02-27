---
title: "IDebugPointerField::GetDereferencedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField::GetDereferencedField"
helpviewer_keywords: 
  - "Metodo IDebugPointerField::GetDereferencedField"
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce il tipo di oggetto che punta di questo oggetto del puntatore.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### Parametri  
 `ppField`  
 \[out\]  Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) una descrizione del tipo di oggetto di destinazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se, ad esempio, [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) i punti di oggetto a un intero, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) il tipo restituito da questo metodo viene descritto il tipo integer.  
  
## Vedere anche  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)