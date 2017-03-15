---
title: "Metodo GetScheduledTasksForDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Metodo GetScheduledTasksForDebugger, classe oggetto TaskScheduler [motori di debug di .NET Framework]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo GetScheduledTasksForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una matrice di tutte le attività pianificate.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## Valore restituito  
 Matrice di tutte le operazioni pianificate. Ogni attività è in esecuzione o ha terminato l'esecuzione.  
  
## Note  
 Questo metodo non è thread\-safe e non deve essere utilizzato contemporaneamente con altre istanze di <xref:System.Threading.Tasks.TaskScheduler> deve essere chiamato da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## Vedere anche  
 [Oggetto TaskScheduler \(classe\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)