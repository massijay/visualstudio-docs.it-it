---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il modulo in fase di caricamento o scaricati.  
  
## Sintassi  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### Parametri  
 `pModule`  
 \[out\]  Restituisce [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) un oggetto che rappresenta il modulo in fase di caricamento o scaricati.  
  
 `pbstrDebugMessage`  
 \[in, out\]  restituisce un messaggio facoltativo che descrive questo evento.  Se questo parametro è un valore null, non viene visualizzato alcun messaggio è obbligatorio.  
  
 `pbLoad`  
 \[in, out\]  Diverso da zero \(`TRUE`\) se il modulo viene caricato e zero \(`FALSE`\) se il modulo è terminato.  Se questo parametro è un valore null, il alcuno stato è obbligatorio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)