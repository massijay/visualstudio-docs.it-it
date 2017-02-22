---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
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
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Arresta tutti i thread in esecuzione nel programma.  
  
## Sintassi  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene chiamato quando il programma si sta eseguendo il debug in un ambiente di multi\-programma.  Quando un evento bloccato da un altro programma viene ricevuto, questo metodo viene chiamato in questo programma.  L'implementazione del metodo deve essere asincrona, ovvero non tutti i thread devono essere obbligatori essere arrestato prima che questo metodo restituisce.  L'implementazione di questo metodo può essere sufficiente chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) il metodo sul programma.  
  
 Nessun evento di debug viene inviato in risposta a questo metodo.  
  
## Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)