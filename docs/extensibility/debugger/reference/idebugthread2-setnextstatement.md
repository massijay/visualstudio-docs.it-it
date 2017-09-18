---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il puntatore all'istruzione corrente al contesto di codice specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Parametri  
 `pStackFrame`  
 Riservato per un utilizzo futuro, impostare su un valore null.  
  
 `pCodeContext`  
 \[in\]  [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Un oggetto che specifica la posizione di codice su da eseguire e il relativo contesto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati altri valori possibili.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME OF E\_CAN NOT|L'istruzione seguente non può essere in uno stack frame situato più in profondità nello stack frame.|  
|\_SETIP\_TO\_DIFFERENT\_FUNCTION OF E\_CAN NOT|L'istruzione successiva non è associato ad alcun frame nello stack.|  
|\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION OF E\_CAN NOT|Alcuni motori di debug non possono impostare l'istruzione successiva dopo un'eccezione.|  
  
## Note  
 Il puntatore all'istruzione indica l'istruzione o l'istruzione successiva esecuzione.  Questo metodo viene utilizzato per ritentare una riga di codice sorgente o per forzare l'esecuzione procedano in un'altra funzione, ad esempio.  
  
## Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)