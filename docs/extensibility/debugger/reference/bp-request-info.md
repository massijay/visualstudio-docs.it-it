---
title: "BP_REQUEST_INFO | Microsoft Docs"
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
  - "BP_REQUEST_INFO"
helpviewer_keywords: 
  - "Struttura BP_REQUEST_INFO"
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene le informazioni necessarie per implementare un punto di interruzione.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## Membri  
 `dwFields`  
 Una combinazione di flag [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) dall'enumerazione che specifica quali campi vengono compilati.  
  
 `guidLanguage`  
 il linguaggio GUID.  
  
 `bpLocation`  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) La struttura che specifica il tipo della posizione del punto di interruzione.  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) L'oggetto che rappresenta l'applicazione in cui il punto di interruzione si verifica.  
  
 `bstrProgramName`  
 Il nome dell'applicazione in cui il punto di interruzione si verifica.  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) L'oggetto che rappresenta il thread nel quale il punto di interruzione si verifica.  
  
 `bstrThreadName`  
 Il nome del thread in cui il punto di interruzione si verifica.  
  
 `bpCondition`  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) La struttura che descrive le condizioni in cui il punto di interruzione verrà generato.  
  
 `bpPassCount`  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) La struttura che contiene le informazioni di conteggio della sessione del punto di interruzione.  
  
 `dwFlags`  
 Una combinazione di flag [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) dall'enumerazione che specifica i flag per il punto di interruzione richiesto.  
  
## Note  
 Questa struttura viene restituito dal [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) metodo.  
  
 Per ottenere il fornitore GUID del motore di debug, il vincolo del punto di interruzione o di analisi, vedere [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) la struttura.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)