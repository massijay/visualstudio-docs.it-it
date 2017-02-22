---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
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
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco di elementi figlio della proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di flag [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) dall'enumerazione che specifica i campi nelle strutture enumerate [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) devono essere riempiti.  
  
 `dwRadix`  
 \[in\]  Specifica la radice da utilizzare durante la formattazione di qualsiasi informazione numerica.  
  
 `guidFilter`  
 \[in\]  GUID di filtro utilizzato con i parametri di `pszNameFilter` e di `dwAttribFilter` per selezionare quali i figli di `DEBUG_PROPERTY_INFO` devono essere enumerati.  Ad esempio, filtri di `guidFilterLocals` per le variabili locali.  
  
 `dwAttribFilter`  
 \[in\]  Una combinazione di flag [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) dall'enumerazione che specifica il tipo di oggetti da enumerare, ad esempio `DBG_ATTRIB_METHOD` per tutti i metodi che possono essere figlio di questa proprietà.  Utilizzata insieme ai parametri di `pszNameFilter` e di `guidFilter` .  
  
 `pszNameFilter`  
 \[in\]  Il nome del filtro utilizzato con i parametri di `dwAttribFilter` e di `guidFilter` per selezionare quali i figli di `DEBUG_PROPERTY_INFO` devono essere enumerati.  Ad esempio, impostando questo parametro ai filtri “da MyX„ per tutti gli elementi figlio con il nome “MyX„.  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) un oggetto che contiene un elenco delle proprietà figlio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)