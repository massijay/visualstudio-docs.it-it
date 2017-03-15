---
title: "Campo TASK_STATE_FAULTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_FAULTED, classe di attività [motori di debug di .NET Framework]"
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Campo TASK_STATE_FAULTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'attività è stata completata a causa di un'eccezione non gestita.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## Note  
 Se il [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene il valore di <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)