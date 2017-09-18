---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un oggetto servizio fornito il relativo identificatore univoco.  
  
## Sintassi  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### Parametri  
 `uid`  
 \[in\]  Identificatore univoco del servizio da recuperare.  
  
 `ppService`  
 \[out\]  restituisce un oggetto che rappresenta il servizio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Ciò può essere utilizzata da un analizzatore di espressioni di terze parti per ottenere servizi da un altro analizzatore di espressioni.  Ad esempio, questo metodo può essere utilizzato per ottenere l'interfaccia per il servizio del visualizzatore dall'analizzatore di espressioni predefinito.  Gli analizzatori di espressioni di terze parti non saranno da essere necessario implementare questa interfaccia.  
  
## Vedere anche  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)