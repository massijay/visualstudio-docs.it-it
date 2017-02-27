---
title: "Campo TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_RAN_TO_COMPLETION, classe di attività [motori di debug di .NET Framework]"
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Campo TASK_STATE_RAN_TO_COMPLETION
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esecuzione dell'attività è stata completata correttamente.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## Note  
 Se il [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene il valore di <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)