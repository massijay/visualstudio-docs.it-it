---
title: "IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot"
helpviewer_keywords: 
  - "Metodo IDebugExpressionEvaluator::SetRegistryRoot"
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo imposta la chiave radice del Registro di sistema.  Utilizzato per il debug side\-by\-side.  
  
## Sintassi  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### Parametri  
 `ustrRegistryRoot`  
 \[in\]  La nuova chiave radice del Registro di sistema.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 La chiave radice del Registro di sistema specificato in genere è impostata quando nell'analizzatore di espressioni in cui ne viene creata un'istanza e punta alla chiave del Registro di sistema per una specifica versione di Visual Studio \(\\SOFTWARE\\Microsoft\\VisualStudio HKEY\_LOCAL\_MACHINE \\*X.Y*, dove *X.Y* è un numero di versione\).  
  
## Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)