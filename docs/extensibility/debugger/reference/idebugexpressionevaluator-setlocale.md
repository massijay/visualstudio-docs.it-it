---
title: "IDebugExpressionEvaluator::SetLocale | Microsoft Docs"
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
  - "IDebugExpressionEvaluator::SetLocale"
helpviewer_keywords: 
  - "Metodo IDebugExpressionEvaluator::SetLocale"
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo imposta il linguaggio da utilizzare per creare i risultati stampabili.  
  
## Sintassi  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### Parametri  
 `wLangID`  
 \[in\]  L'identificatore del linguaggio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo può essere chiamato più volte durante l'analizzatore di \(EE\) espressioni è caricato, pertanto EE deve essere in grado di passare i linguaggi immediatamente.  L'EE utilizza queste impostazioni locali per restituire i messaggi di errore e stringhe nel linguaggio appropriato.  
  
## Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)