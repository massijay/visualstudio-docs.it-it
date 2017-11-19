---
title: Campo TASK_STATE_FAULTED | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9e0a5bb80cd3a89f1e200b75b4910328c6652da
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="taskstatefaulted-field"></a>Campo TASK_STATE_FAULTED
L'attività è stata completata a causa di un'eccezione non gestita.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>Note  
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene questo valore, il <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)