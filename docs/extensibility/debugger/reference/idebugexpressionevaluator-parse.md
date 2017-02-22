---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
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
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "Metodo IDebugExpressionEvaluator::Parse"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo converte una stringa dell'espressione in un'espressione analizzata.  
  
## Sintassi  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### Parametri  
 `upstrExpression`  
 \[in\]  La stringa di un'espressione da analizzare.  
  
 `dwFlags`  
 \[in\]  Una raccolta [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) di costanti che determinano quali l'espressione deve essere analizzata.  
  
 `nRadix`  
 \[in\]  Base da utilizzare per interpretare le informazioni numerica.  
  
 `pbstrError`  
 \[out\]  restituisce l'errore come testo leggibile.  
  
 `pichError`  
 \[out\]  Restituisce la posizione del carattere dell'inizio dell'errore nella stringa dell'espressione.  
  
 `ppParsedExpression`  
 \[out\]  restituisce l'espressione analizzata [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) in un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo produce un'espressione analizzata, non un valore effettivo.  Un'espressione analizzata è pronta per essere valutato, ovvero, viene convertito in un valore.  
  
## Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)