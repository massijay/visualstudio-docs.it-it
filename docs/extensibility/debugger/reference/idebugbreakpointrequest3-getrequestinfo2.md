---
title: "IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs"
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
  - "IDebugBreakpointRequest3::GetRequestInfo2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera le informazioni su richiesta del punto di interruzione che descrivono la richiesta di un punto di interruzione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### Parametri  
 `dwFields`  
 \[in\]  Una combinazione di flag [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) dall'enumerazione che determinano quali campi di `pBPRequestInfo` devono essere riempiti.  
  
 `bBPRequestInfo`  
 \[out\]  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) la struttura da riempire.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 Esistono ulteriori informazioni nella richiesta che viene restituito [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) dal metodo.  
  
## Vedere anche  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)