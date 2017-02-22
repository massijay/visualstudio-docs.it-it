---
title: "IDebugProcess2::GetInfo | Microsoft Docs"
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
  - "IDebugProcess2::GetInfo"
helpviewer_keywords: 
  - "IDebugProcess2::GetInfo"
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene una descrizione del processo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### Parametri  
 `Fields`  
 \[in\]  Una combinazione di valori [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) dall'enumerazione che specifica quali campi del parametro di `pProcessInfo` devono essere riempiti.  
  
 `pProcessInfo`  
 \[out\]  [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) Una struttura che viene soddisfatta di descrizione del processo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)