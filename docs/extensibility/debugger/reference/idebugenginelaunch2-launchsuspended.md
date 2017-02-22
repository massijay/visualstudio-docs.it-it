---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo viene avviato un processo tramite il motore di \(DE\) debug.  
  
## Sintassi  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```c#  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### Parametri  
 `pszMachine`  
 \[in\]  Il nome del computer in cui per avviare il processo.  utilizzare un valore null per specificare il computer locale.  
  
 `pPort`  
 \[in\]  [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) L'interfaccia che rappresenta la porta che il programma verrà eseguito in.  
  
 `pszExe`  
 \[in\]  Il nome dell'eseguibile da avviare.  
  
 `pszArgs`  
 \[in\]  Gli argomenti da passare eseguibile.  Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 \[in\]  Il nome della directory di lavoro utilizzata dall'eseguibile.  Può essere un valore null se non è necessaria alcuna directory di lavoro obbligatoria.  
  
 `bstrEnv`  
 \[in\]  Blocco di ambiente di stringhe con terminazione null, seguito da un carattere di terminazione null aggiuntivo.  
  
 `pszOptions`  
 \[in\]  le opzioni per l'eseguibile.  
  
 `dwLaunchFlags`  
 \[in\]  specifica [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) per una sessione.  
  
 `hStdInput`  
 \[in\]  Un handle per un flusso di input alternativo.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdOutput`  
 \[in\]  Un handle per un flusso di output alternativo.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdError`  
 \[in\]  Un handle per un flusso di output alternativo di errori.  può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `pCallback`  
 \[in\]  [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) L'oggetto che riceve gli eventi del debugger.  
  
 `ppDebugProcess`  
 \[out\]  restituisce l'oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) risultante che rappresenta il processo avviato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 In genere, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vara un programma [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) utilizzando il metodo e quindi connettere il debugger a un programma sospeso.  Tuttavia, vi sono casi in cui il motore di debug può avere l'esigenza di avviare un programma \(ad esempio, se il motore di debug fa parte di un interprete e del programma di cui viene eseguito il debug è un linguaggio interpretato, nel qual caso [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utilizza il metodo di `IDebugEngineLaunch2::LaunchSuspended` .  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) Il metodo viene chiamato per avviare il processo dopo che il processo correttamente è stato avviato in uno stato sospeso.  
  
## Vedere anche  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)