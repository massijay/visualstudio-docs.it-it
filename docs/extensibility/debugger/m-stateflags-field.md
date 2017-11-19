---
title: Campo m_stateFlags | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 624f9ef2f5cf2d44b565e8dd16c46938819a5df0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="mstateflags-field"></a>Campo m_stateFlags
Archivia le informazioni sullo stato corrente del <xref:System.Threading.Tasks.Task> oggetto.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>Note  
 In genere si usa il <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> proprietà per accedere a questo valore.  
  
 Questo membro può essere qualsiasi combinazione dei valori seguenti:  
  
-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)