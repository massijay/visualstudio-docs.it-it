---
title: "IDebugMemoryContext2::GetInfo | Microsoft Docs"
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
  - "IDebugMemoryContext2::GetInfo"
helpviewer_keywords: 
  - "Metodo GetInfo"
  - "Metodo IDebugMemoryContext2::GetInfo"
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) una struttura che descrive il contesto.  
  
## Sintassi  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di flag [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) dall'enumerazione che indicano quali campi [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) della struttura devono essere compilati.  
  
 `pInfo`  
 \[in, out\]  La struttura di `CONTEXT_INFO` che viene soddisfatta.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)