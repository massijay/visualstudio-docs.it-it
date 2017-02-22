---
title: "IDebugThread2::Resume | Microsoft Docs"
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
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Riprende l'esecuzione di un thread.  
  
## Sintassi  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### Parametri  
 `pdwSuspendCount`  
 \[out\]  Restituisce il numero di sospensione dopo l'operazione riprendi.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a 0 quando, l'esecuzione viene effettivamente riattivata.  Questo conteggio di sospensione visualizzato nella finestra di debug di **thread** .  
  
 Per ogni chiamata a questo metodo, è necessario che esista una chiamata precedente [Sospendi](../Topic/IDebugThread2::Suspend.md) al metodo.  il conteggio di sospensione determina quante volte il metodo di `IDebugThread2::Suspend` è stato chiamato finora.  
  
## Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Sospendi](../Topic/IDebugThread2::Suspend.md)