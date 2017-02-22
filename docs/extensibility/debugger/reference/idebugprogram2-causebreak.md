---
title: "IDebugProgram2::CauseBreak | Microsoft Docs"
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
  - "IDebugProgram2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProgram2::CauseBreak"
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le richieste che il programma verrà interrotta la volta successiva che uno dei thread tenta di eseguire.  
  
## Sintassi  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) Un evento viene inviato quando il programma dopo tenta di eseguire codice dopo che questo metodo viene chiamato.  
  
 Questo metodo è asincrono in quanto il metodo restituisce immediatamente senza necessariamente attendere il programma per arrestare.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)