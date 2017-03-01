---
title: IDebugProgramNameChangedEvent2 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
caps.latest.revision: 6
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d0032971225d25b054cd66ee500800de4bcd7b97
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Inviato dal motore di debug (DE) al gestore di sessione di debug (SDM) quando cambia il nome di un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il DE implementa questa interfaccia per report che è stato modificato il nome del programma. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Utilizza il modello SDM [QueryInterface](/visual-cpp/atl/queryinterface) per l'accesso di **IDebugEvent2** interfaccia.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 La dice crea e invia l'oggetto evento per segnalare una modifica del nome del programma. Questo evento viene inviato il DE utilizzando il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando associato al programma in fase di debug. Il fornitore porta personalizzata invia questo evento utilizzando che l'interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
