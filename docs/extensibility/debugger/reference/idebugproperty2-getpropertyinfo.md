---
title: "IDebugProperty2::GetPropertyInfo | Microsoft Docs"
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
  - "IDebugProperty2::GetPropertyInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetPropertyInfo"
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) la struttura che descrive una proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di valori [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) dall'enumerazione che specifica i campi devono essere compilati nella struttura di `pPropertyInfo` .  
  
 `nRadix`  
 \[in\]  Base da utilizzare durante la formattazione delle informazioni numerica.  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `rgpArgs`  
 \[in, out\]  Riservato per un utilizzo futuro, impostare su un valore null.  
  
 `dwArgCount`  
 \[in\]  Riservato per un utilizzo futuro, impostare su zero.  
  
 `pPropertyInfo`  
 \[out\]  [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Una struttura che viene soddisfatta di descrizione della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)