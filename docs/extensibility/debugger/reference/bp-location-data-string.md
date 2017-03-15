---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_DATA_STRING"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilizzato per impostare i punti di interruzione di dati basati su una stringa che l'utente può immettere dall'ambiente di sviluppo integrato \(IDE\).  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## Membri  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) L'oggetto che rappresenta il thread in cui il punto di interruzione si verifica.  
  
 `bstrContext`  
 Il contesto del punto di interruzione nel codice, in genere un nome di funzione o di metodo come indicato in uno stack di chiamate.  
  
 `bstrDataExpr`  
 I dati supporti l'utente INVIO per impostare il punto di interruzione.  
  
 `dwNumElements`  
 Il numero di elementi nella stringa di dati in cui il punto di interruzione si verifica.  
  
## Note  
 Questa struttura è un membro [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) della struttura come parte di unione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)