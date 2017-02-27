---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Connettere una sessione nel programma.  
  
## Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### Parametri  
 `pCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Un oggetto che rappresenta la funzione di callback che il motore di debug allegato invia gli eventi in.  
  
 `dwReason`  
 \[in\]  Un valore [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) dell'enumerazione che descrive il motivo per l'operazione di connessione.  
  
 `pSession`  
 \[in\]  Un valore che identifica in modo univoco la sessione che si sta connettendo al programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già associata.  
  
## Note  
 La porta che contiene il programma possibile utilizzare il valore in `pSession` per determinare la sessione tenta di connettersi al programma.  Ad esempio, se una porta consente solo una sessione di debug all'attaccatura a un processo alla volta, la porta può determinare se la stessa sessione è già collegata ad altri programmi nel processo.  
  
> [!NOTE]
>  Interfaccia passata in `pSession` deve essere considerata solo come cookie, un valore che identifica in modo univoco l'amministratore di debug della sessione che si connette a questo programma; nessuno dei metodi in un'interfaccia fornita sono funzionanti.  
  
## Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)