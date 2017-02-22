---
title: "IDebugPort2::GetPortRequest | Microsoft Docs"
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
  - "IDebugPort2::GetPortRequest"
helpviewer_keywords: 
  - "IDebugPort2::GetPortRequest"
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene la descrizione di una porta che era stato utilizzato per creare la porta \(se disponibile\).  
  
## Sintassi  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### Parametri  
 `ppRequest`  
 \[out\]  Restituisce [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) un oggetto che rappresenta la chiamata utilizzata per creare la porta.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_PORT_NO_REQUEST` se una porta non è stato creato [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) utilizzando una richiesta di porta.  
  
## Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)