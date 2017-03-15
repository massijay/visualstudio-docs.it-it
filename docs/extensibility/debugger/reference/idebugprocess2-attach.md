---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Associa l'amministratore \(SDM\) di debug della sessione al processo.  
  
## Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### Parametri  
 `pCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Un oggetto utilizzato per la notifica di eventi di debug.  
  
 `rgguidSpecificEngines`  
 \[in\]  Una matrice di GUID dei motori di debug da utilizzare ai programmi di debug in esecuzione nel processo.  questo parametro può essere un valore null.  Vedere le note per i dettagli.  
  
 `celtSpecificEngines`  
 \[in\]  Il numero dei motori di debug nella matrice di `rgguidSpecificEngines` e la dimensione della matrice di `rghrEngineAttach` .  
  
 `rghrEngineAttach`  
 \[in, out\]  Una matrice di codici di HRESULT restituiti dai motori di debug.  La dimensione della matrice viene specificata nel parametro di `celtSpecificEngines` .  ogni codice è in genere `S_OK` o `S_ATTACH_DEFERRED`.  L'ultima indica che il DE è attualmente connesso a nessun programmi.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Nella tabella seguente vengono illustrati altri valori possibili.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il processo specificato è già connesso al debugger.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Una violazione della sicurezza è stata apportata durante la routine di connessione.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processo desktop non può essere collegato al debugger.|  
  
## Note  
 Connessione a un processo aggiunge lo SDM a tutti i programmi in esecuzione nel processo di cui è possibile eseguire il debug dai motori di \(DE\) debug specificati nella matrice di `rgguidSpecificEngines` .  Impostare il parametro di `rgguidSpecificEngines` a un valore null o importare `GUID_NULL` nella matrice per connettersi a tutti i programmi nel processo.  
  
 Tutti gli eventi di debug che si verificano nel processo vengono inviati all'oggetto specificato [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) .  Questo oggetto di `IDebugEventCallback2` viene fornito quando lo SDM chiama questo metodo.  
  
## Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)