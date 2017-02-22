---
title: "IDebugEngine2::SetMetric | Microsoft Docs"
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
  - "IDebugEngine2:::SetMetric"
helpviewer_keywords: 
  - "IDebugEngine2:::SetMetric"
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo imposta un valore del Registro di sistema noto come metrica.  
  
## Sintassi  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```c#  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### Parametri  
 `pszMetric`  
 \[in\]  Il nome ".  
  
 `varValue`  
 \[in\]  Specifica il valore ".  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Metrica è un valore del Registro di sistema utilizzato per modificare il comportamento del modulo di debug o per annunciare la funzionalità supportata.  Questo metodo può inoltrare la chiamata al form adatto [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) alla funzione, `SetMetric`.  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)