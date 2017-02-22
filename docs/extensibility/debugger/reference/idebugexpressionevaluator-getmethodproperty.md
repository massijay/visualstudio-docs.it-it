---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
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
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "Metodo IDebugExpressionEvaluator::GetMethodProperty"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene un oggetto proprietà contenente le variabili locali, argomenti e altre proprietà di un metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Parametri  
 `pSymbolProvider`  
 \[in\]  Il provider del simbolo da utilizzare, espresso come [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) oggetto.  
  
 `pAddress`  
 \[in\]  L'indirizzo nel codice, espresso come [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto, che deve essere risolto alla funzione contenente più vicina.  
  
 `pBinder`  
 \[in\]  il gestore di associazione da utilizzare, espresso come [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.  
  
 `fIncludeHiddenLocals`  
 \[in\]  Diverso da zero \(`TRUE`\) significa importare le variabili locali nascosti, implementa zero \(`FALSE`\) per lasciare le variabili locali a nascosti  
  
 `ppProperty`  
 \[out\]  restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un oggetto che rappresenta il metodo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Le variabili locali nascosti in genere variabili generate dal compilatore.  
  
## Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)