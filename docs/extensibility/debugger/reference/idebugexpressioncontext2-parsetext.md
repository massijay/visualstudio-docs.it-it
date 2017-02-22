---
title: "IDebugExpressionContext2::ParseText | Microsoft Docs"
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
  - "IDebugExpressionContext2::ParseText"
helpviewer_keywords: 
  - "IDebugExpressionContext2::ParseText"
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionContext2::ParseText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Analizza un'espressione in formato di testo per la valutazione successiva.  
  
## Sintassi  
  
```cpp#  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```c#  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in\]  l'espressione da analizzare.  
  
 `dwFlags`  
 \[in\]  Una combinazione di flag [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) dall'enumerazione che controlla l'analisi.  
  
 `nRadix`  
 \[in\]  La radice da utilizzare quando si analizzano le informazioni numerica in `pszCode`.  
  
 `ppExpr`  
 \[out\]  Restituisce [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) l'oggetto che rappresenta l'espressione analizzata, che è pronta per l'associazione e la valutazione.  
  
 `pbstrError`  
 \[out\]  restituisce il messaggio di errore se l'espressione contiene un errore.  
  
 `pichError`  
 \[out\]  Restituisce l'indice di caratteri dell'errore in `pszCode` se l'espressione contiene un errore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Quando questo metodo viene chiamato, un motore \(DE\) di debug deve analizzare l'espressione e convalidarlo per la precisione.  I parametri di `pichError` e di `pbstrError` possono essere sostituiti se l'espressione non è valida.  
  
 Si noti che l'espressione non viene valutata, solo analizzato.  una chiamata successiva [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ai metodi valuta l'espressione analizzata.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CEnvBlock` che espone [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) l'interfaccia.  Questo esempio presuppone l'espressione di essere analizzato come nome di una variabile di ambiente e recupera il valore della variabile.  
  
```cpp#  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## Vedere anche  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)