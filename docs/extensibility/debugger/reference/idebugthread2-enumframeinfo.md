---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
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
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco degli stack frame per il thread.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### Parametri  
 `dwFieldSpec`  
 \[in\]  Una combinazione di flag [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) dall'enumerazione che specifica i campi [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture devono essere compilati.  Specificare il flag di `FIF_FUNCNAME_FORMAT` per formattare il nome della funzione in una singola stringa.  
  
 `nRadix`  
 \[in\]  Base utilizzata la formattazione informazioni numeriche nell'enumeratore.  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) un oggetto che contiene un elenco [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture che descrivono lo stack frame.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 I frame del thread vengono enumerati in ordine, con il frame corrente enumerato per primo e il frame precedente enumerato per ultima.  
  
## Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)