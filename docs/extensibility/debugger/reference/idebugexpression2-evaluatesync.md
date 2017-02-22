---
title: "IDebugExpression2::EvaluateSync | Microsoft Docs"
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
  - "IDebugExpression2::EvaluateSync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateSync"
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce l'espressione in modo sincrono.  
  
## Sintassi  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Parametri  
 `dwFlags`  
 \[in\]  Una combinazione di flag [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) dall'enumerazione che controllano la valutazione di espressioni.  
  
 `dwTimeout`  
 \[in\]  Tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `pExprCallback`  
 \[in\]questo parametro è sempre un valore null.  
  
 `ppResult`  
 \[out\]  Restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) l'oggetto che contiene il risultato della valutazione di un'espressione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Alcuni codici di errore tipici comprendono:  
  
|delle modifiche a..."|Descrizione|  
|---------------------------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Un'altra espressione viene attualmente valutazione e la valutazione simultanea dell'espressione non è supportata.|  
|E\_EVALUATE\_TIMEOUT|Valutazione timeout.|  
  
## Note  
 Per la valutazione sincrona, non è necessario inviare un evento di tornare a Visual Studio al completamento della valutazione.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CExpression` che implementa [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) l'interfaccia.  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## Vedere anche  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)