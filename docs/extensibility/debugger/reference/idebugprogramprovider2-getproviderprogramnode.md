---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il nodo del programma per un programma specifico.  
  
## Sintassi  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\]  La porta che il processo chiamante viene eseguito.  
  
 `processId`  
 \[in\]  [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Una struttura contenente l'ID del processo che contiene il programma in questione.  
  
 `guidEngine`  
 \[in\]  GUID del motore di debug che il programma è associato \(se presente\).  
  
 `programId`  
 \[in\]  ID del programma per il quale ottenere il nodo del programma.  
  
 `ppProgramNode`  
 \[out\]  [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) un oggetto che rappresenta il nodo richiesto di programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)