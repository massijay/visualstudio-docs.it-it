---
title: IDebugStopCompleteEvent2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e92138f969189a33e1a5aad5a083c8ac57852dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Il motore di debug (DE) è possibile inviare questo evento facoltativo da gestore di sessione di debug (SDM) quando un programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Si tratta di una nuova interfaccia per [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Le versioni precedenti non supportava interruzione asincrona.  
  
 [Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM in più processi o un programma più scenari. Quando un programma invia un evento di arresto per il SDM, il SDM richiede altri programmi di arrestare.  
  
 Utilizzato per comunicare in modo asincrono SDM che un programma è stato arrestato. Ciò è utile per un motore di debug interprete, in cui a volte codice non è in esecuzione all'interno del programma sottoposto a debug, in modo [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug decide di utilizzare questa notifica asincrona, deve restituire `S_ASYNC_STOP` da [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll