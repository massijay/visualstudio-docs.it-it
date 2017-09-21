---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Controlla per l'esecuzione o le modifiche che controllano per l'esecuzione\) per verificare il thread specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### Parametri  
 `pOriginatingProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Un oggetto che rappresenta il programma che viene eseguito l'istruzione.  
  
 `dwTid`  
 \[in\]  Specifica l'identificatore di thread per verificare.  
  
 `fWatch`  
 \[in\]  Controllare iniziale di diversi da zero implementa \(di`TRUE`\) per l'esecuzione sul thread identificato da `dwTid`; in caso contrario, implementa zero \(`FALSE`\) cessano di controllare per l'esecuzione in `dwTid`.  
  
 `dwFrame`  
 \[in\]  Specifica un indice del frame che controlla il tipo di passaggio.  Quando questo viene valore è zero \(0\), il tipo di passaggio è “passaggio in„ e il programma deve essere interrotta ogni volta che il thread identificato da `dwTid` esegue.  Quando `dwFrame` è diverso da zero, il tipo di passaggio è “esegue„ e il programma verrà arrestata solo se il thread identificato da `dwTid` è in esecuzione nel frame a cui indice è uguale o superiore dello stack che `dwFrame`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Quando i passaggi di amministratore di debug \(SDM\) della sessione un programma, identificato dal parametro di `pOriginatingProgram` , notifica tutti gli altri programmi connessi chiamando il metodo.  
  
 Questo metodo è applicabile solo all'esecuzione di istruzioni in stesso\-thread.  
  
## Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)