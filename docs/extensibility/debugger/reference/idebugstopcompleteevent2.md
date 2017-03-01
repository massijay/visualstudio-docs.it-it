---
title: IDebugStopCompleteEvent2 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
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
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Il motore di debug (DE) può inviare l'evento facoltativo al gestore di sessione di debug (SDM) quando un programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Si tratta di una nuova interfaccia per [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Le versioni precedenti non supportava l'interruzione asincrona.  
  
 [Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM in più processi o un programma più scenari. Quando un programma invia un evento di arresto per il modello SDM, il modello SDM richiede altri programmi, troppo.  
  
 Consente di comunicare in modo asincrono SDM che un programma è stato arrestato. Ciò è utile per un motore di debug interprete, in cui talvolta codice non è in esecuzione all'interno del programma di debug, in modo [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug desidera impiegare questa notifica asincrona, deve restituire `S_ASYNC_STOP` da [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
