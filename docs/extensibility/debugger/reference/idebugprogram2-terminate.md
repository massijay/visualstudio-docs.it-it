---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Terminare il programma.  
  
## Sintassi  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se possibile, il programma verrà terminato e scaricato dal processo; in caso contrario, il motore \(DE\) di debug esegue le operazioni di pulitura necessarie.  
  
 Questo metodo o [Termina](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) il metodo viene chiamato dall'IDE, in genere in risposta all'utente che interrompe il debug.  L'implementazione del metodo deve, terminare nel programma all'interno del processo.  Se non è possibile, il DE preferibile che il programma dall'altro in questo processo e apportare alcuna pulizia necessaria\).  Se il metodo di `IDebugProcess2::Terminate` viene chiamato dall'IDE di, l'intero processo verrà chiuso prima o quindi dopo che il metodo di `IDebugProgram2::Terminate` viene chiamato.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Termina](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)