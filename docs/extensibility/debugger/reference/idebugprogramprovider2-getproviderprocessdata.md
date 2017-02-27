---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco di programmi in esecuzione in un processo specificato.  
  
## Sintassi  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### Parametri  
 `Flags`  
 \[in\]  Una combinazione di flag [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) dall'enumerazione.  i seguenti flag sono tipici per questa chiamata:  
  
|Flag|Descrizione|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Il chiamante è in esecuzione nel computer remoto.|  
|`PFLAG_DEBUGGEE`|Il chiamante è in corso il debug \(informazioni aggiuntive sul marshalling verranno restituite per ogni nodo\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Il chiamante è stato collegato a ma non è stato avviato dal debugger.|  
|`PFLAG_GET_PROGRAM_NODES`|Il chiamante viene richiesto un elenco di nodi di programma di essere restituito.|  
  
 `pPort`  
 \[in\]  La porta che il processo chiamante viene eseguito.  
  
 `processId`  
 \[in\]  [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Una struttura contenente l'ID del processo che contiene il programma in questione.  
  
 `EngineFilter`  
 \[in\]  Una matrice di GUID per i motori di debug assegnati per eseguire il debug di questo processo \(verranno utilizzate per filtrare i programmi effettivamente restituiti in base al supporto di motori fornito; se nessun motore viene specificato, tutti i programmi verranno restituiti\).  
  
 `pProcess`  
 \[out\]  [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Una struttura che viene compilata con le informazioni richieste.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo in genere viene chiamato da un processo per ottenere un elenco di programmi in esecuzione nel processo.  Le informazioni restituite da un elenco [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) di oggetti.  
  
## Vedere anche  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)