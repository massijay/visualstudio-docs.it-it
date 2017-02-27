---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene avviato un file eseguibile.  
  
## Sintassi  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### Parametri  
 `pszExe`  
 \[in\]  Il nome dell'eseguibile da avviare.  È possibile specificare un percorso completo o relativo alla directory di lavoro specificata nel parametro di `pszDir` .  
  
 `pszArgs`  
 \[in\]  Gli argomenti da passare eseguibile.  Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 \[in\]  Il nome della directory di lavoro utilizzata dall'eseguibile.  Può essere un valore null se non è necessaria alcuna directory di lavoro obbligatoria.  
  
 `bstrEnv`  
 \[in\]  Blocco di ambiente di stringhe con terminazione null, seguito da un carattere di terminazione null aggiuntivo.  
  
 `hStdInput`  
 \[in\]  Un handle per un flusso di input alternativo.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdOutput`  
 \[in\]  Un handle per un flusso di output alternativo.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdError`  
 \[in\]  Un handle per un flusso di output alternativo di errori.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `ppPortProcess`  
 \[out\]  restituisce [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) un oggetto che rappresenta il processo avviato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo deve avviare il processo in modo da sospenderlo e non eseguendone qualsiasi codice.  [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) Il metodo viene chiamato per riprendere il processo.  
  
 Un programma può inoltre essere avviato da un motore di debug.  Per informazioni dettagliate, vedere [Avviare un programma](../../../extensibility/debugger/launching-a-program.md).  
  
## Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Avviare un programma](../../../extensibility/debugger/launching-a-program.md)