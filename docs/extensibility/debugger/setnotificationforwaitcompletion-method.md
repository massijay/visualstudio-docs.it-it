---
title: Metodo SetNotificationForWaitCompletion | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385ae98e90d8f3a466c0983405c367347bb8ca10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>Metodo SetNotificationForWaitCompletion
Imposta o Cancella il bit di stato TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametri  
 `enabled`  
  
 `true`Per impostare il bit; `false` a non è impostato il bit.  
  
## <a name="exceptions"></a>Eccezioni  
  
## <a name="remarks"></a>Note  
 Il debugger imposta questo bit per uscire il corpo di un metodo asincrono. Se `enabled` è `true`, questo metodo deve essere chiamato solo su un'attività che non è ancora stata completata. Se `enabled` è `false`, questo metodo può essere chiamato per le attività completate. In entrambi i casi deve essere utilizzato solo per le attività di tipo pianificato.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)