---
title: IDebugProcess3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 6b98394c4880ce78eb8069534b009ea351608cd6
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprocess3"></a>IDebugProcess3
Questa interfaccia rappresenta un processo in esecuzione e i relativi programmi. Questa interfaccia esiste come una sostituzione per vari metodi di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Fornisce un controllo su tutti i programmi del processo.  
  
> [!NOTE]
>  [Continuare](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), e [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md) metodi sono deprecati e non deve più essere usati. Utilizzare i metodi corrispondenti di `IDebugProcess3` invece di interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un fornitore di porta personalizzato per gestire i programmi come un gruppo. Quando i programmi sono gestiti come gruppo, è possibile controllare l'esecuzione e impostare una lingua per un analizzatore di espressioni. Questa interfaccia deve essere implementata dal fornitore porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata principalmente dal gestore di sessione di debug (SDM) per interagire con un gruppo di programmi identificate in questo processo.  
  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Continuare](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua l'esecuzione di istruzioni tramite un processo o l'esecuzione del.|  
|[Eseguire](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inizia l'esecuzione di un processo.|  
|[Passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Passaggi di inoltrare una istruzione o istruzione nel processo.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ottiene il motivo che il processo è stato avviato per il debug.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Imposta la lingua di hosting in modo che il motore di debug è possibile caricare l'analizzatore di espressioni appropriato.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera la lingua attualmente impostata per questo processo.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Disabilita modifica e Continuazione per questo processo.<br /><br /> Un fornitore di porta personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Ottenere lo stato ENC per questo processo.<br /><br /> Un fornitore di porta personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matrice di identificatori univoci per i motori di debug disponibili.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
