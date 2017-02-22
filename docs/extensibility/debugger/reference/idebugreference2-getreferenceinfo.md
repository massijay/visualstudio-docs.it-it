---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
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
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) la struttura che descrive un riferimento.  Riservato per un utilizzo futuro.  
  
## Sintassi  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di flag [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) dall'enumerazione che determinano i campi da compilare [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) nella struttura.  
  
 `nRadix`  
 \[in\]  La radice da utilizzare durante la formattazione delle informazioni numerica.  
  
 `dwTimeout`  
 \[in\]  Tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `rgpArgs`  
 \[in\]  Una matrice [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) di oggetti.  Riservato per un utilizzo futuro, impostare su un valore null.  
  
 `dwArgCount`  
 \[in\]  Il numero di argomenti di riferimento nella matrice di `rgpArgs` .  Riservato per un utilizzo futuro, impostare su 0.  
  
 `pReferenceInfo`  
 \[out\]  [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Una struttura che viene soddisfatta di descrizione della proprietà.  
  
## Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)