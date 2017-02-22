---
title: "IDebugCanStopEvent2::GetCodeContext | Microsoft Docs"
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
  - "IDebugCanStopEvent2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il contesto di codice che specifica la posizione di questo evento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parametri  
 `ppCodeContext`  
 \[out\]  restituisce [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) l'oggetto che rappresenta la posizione corrente di codice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Per la maggior parte delle architetture in fase di esecuzione, un contesto di codice può essere considerato come un indirizzo in un flusso di esecuzione del programma, puntando a un'istruzione specifica.  
  
 Per ottenere il contesto del documento, che è orientato alle righe di codice sorgente, chiamare [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) il metodo.  
  
## Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)