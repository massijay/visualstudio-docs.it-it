---
title: "Metodo GetTaskSchedulersForDebugger | Microsoft Docs"
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
  - "Metodo GetTaskSchedulersForDebugger, classe oggetto TaskScheduler [motori di debug di .NET Framework]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Metodo GetTaskSchedulersForDebugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## Valore restituito  
 Matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi in <xref:System.AppDomain>.  
  
## Note  
 Questo metodo non è thread\-safe e non deve essere utilizzato contemporaneamente con altre istanze di <xref:System.Threading.Tasks.TaskScheduler>. Deve essere chiamata da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## Vedere anche  
 [Oggetto TaskScheduler \(classe\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)