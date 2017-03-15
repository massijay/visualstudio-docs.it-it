---
title: "Campo TASK_STATE_EXECUTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_EXECUTED, classe di attività [motori di debug di .NET Framework]"
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Campo TASK_STATE_EXECUTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'attività è in esecuzione ma non è ancora stata completata.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## Note  
 Se il [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene il valore di <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)