---
title: "IDebugProcess3 | Microsoft Docs"
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
  - "IDebugProcess3"
helpviewer_keywords: 
  - "Interfaccia IDebugProcess3"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un processo in esecuzione e i programmi.  Questa interfaccia è presente in sostituzione a diversi metodi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nell'interfaccia.  Fornisce il controllo su tutti i programmi nel processo.  
  
> [!NOTE]
>  [Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md)e [Passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md) metodi essere deprecato e potrebbe non essere più utilizzato.  Utilizzare i metodi corrispondenti sull'interfaccia di `IDebugProcess3` anziché.  
  
## Sintassi  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da un fornitore di porte personalizzato per gestire programmi come gruppo.  Quando i programmi vengono gestiti come gruppo, è possibile controllare la loro esecuzione e stabilire un linguaggio per un analizzatore di espressioni.  Questa interfaccia deve essere implementata dal fornitore di porte.  
  
## Note per i chiamanti  
 Questa interfaccia è denominata principalmente dall'amministratore di debug della sessione \(SDM\) per interagire con un gruppo di programmi identificati in questo processo.  
  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) su un'interfaccia per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi ereditati da [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua l'esecuzione di o l'esecuzione di istruzioni tramite un processo.|  
|[Esegui](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Avvia l'esecuzione di un processo.|  
|[Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Passi lungo un l'istruzione o l'istruzione nel processo.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ottiene il motivo per cui il processo è stato avviato per il debug.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Consente di impostare il linguaggio di hosting in modo da poter caricare il motore di debug l'analizzatore di espressioni appropriato.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera il linguaggio attualmente impostato per il processo.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Disabilitare Modifica e continuazione \(ENC\) per questo processo.<br /><br /> Un fornitore di porte personalizzato non implementa questo metodo \(restituiscano sempre `E_NOTIMPL`\).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|ottenere lo stato di ENC per questo processo.<br /><br /> Un fornitore di porte personalizzato non implementa questo metodo \(restituiscano sempre `E_NOTIMPL`\).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matrice di identificatori univoci per i motori di debug.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)