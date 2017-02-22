---
title: "Campo TASK_STATE_WAITING_ON_CHILDREN | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_WAITING_ON_CHILDREN, classe di attività [motori di debug di .NET Framework]"
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Campo TASK_STATE_WAITING_ON_CHILDREN
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'attività ha terminato l'esecuzione del delegato ed è in attesa implicita del completamento delle attività figlio collegate.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## Note  
 Se il [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene il valore di <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)