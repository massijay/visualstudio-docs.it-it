---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
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
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "Metodo IDebugParsedExpression::EvaluateSync"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce l'espressione analizzata e facoltativamente eseguire il cast del risultato in un altro tipo di dati.  
  
## Sintassi  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Parametri  
 `dwEvalFlags`  
 \[in\]  Una combinazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) di costanti che controllano il modo in cui deve essere valutata l'espressione.  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `pSymbolProvider`  
 \[in\]  Il provider dei simboli, espresso come [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia.  
  
 `pAddress`  
 \[in\]  La posizione corrente all'interno di un metodo, espresso come [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
 `pBinder`  
 \[in\]  Il raccoglitore, espresso come [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia.  
  
 `bstrResultType`  
 \[in\]  Il tipo del risultato deve essere eseguito il cast su.  In questo argomento può essere un valore null.  
  
 `ppResult`  
 \[out\]  Restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) l'interfaccia che rappresenta i risultati di valutazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il contesto di valutazione di un'espressione viene fornito da`pAddress`, che consente di determinare il metodo contenitore e utilizzare quindi la definizione di linguaggio regole per determinare il valore dei simboli nell'espressione.  
  
## Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)