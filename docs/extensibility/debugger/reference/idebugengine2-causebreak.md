---
title: "IDebugEngine2::CauseBreak | Microsoft Docs"
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
  - "IDebugEngine2::CauseBreak"
helpviewer_keywords: 
  - "IDebugEngine2::CauseBreak"
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Richieste tali tutti i programmi in corso il debug nel motore di \(DE\) debug per interrompere l'esecuzione nel successivo uno dei thread tenta di eseguire.  
  
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
 questo metodo è asincrono: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) un evento viene inviato quando il programma dopo tenta di eseguire dopo che questo metodo viene chiamato.  
  
## Vedere anche  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)