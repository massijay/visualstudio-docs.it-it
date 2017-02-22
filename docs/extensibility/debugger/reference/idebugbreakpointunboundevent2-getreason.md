---
title: "IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs"
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
  - "IDebugBreakpointUnboundEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene il motivo che il punto di interruzione è stato separato.  
  
## Sintassi  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```c#  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### Parametri  
 `pdwUnboundReason`  
 \[out\]  Restituisce un valore [BP\_UNBOUND\_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) dell'enumerazione che specifica il motivo che il punto di interruzione è stato separato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 I motivi includono un punto di interruzione che è riassociata a una posizione diversa dopo un'operazione di Modifica e continuazione, o una definizione di un punto di interruzione è stato associato per errore.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **di CBreakpointUnboundDebugEventBase** che espone [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) l'interfaccia.  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## Vedere anche  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)