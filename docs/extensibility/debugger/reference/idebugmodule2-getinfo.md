---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "Metodo GetInfo"
  - "Metodo IDebugModule2::GetInfo"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene informazioni su questo modulo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di flag [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) dall'enumerazione che specificano i campi di `pInfo` devono essere compilati.  
  
 `pInfo`  
 \[in, out\]  [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Una struttura che viene soddisfatta di descrizione del modulo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) La struttura contiene il nome del modulo visualizzate nella finestra di **moduli** .  
  
## Vedere anche  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)