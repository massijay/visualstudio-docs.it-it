---
title: "Classe di oggetto TaskScheduler - membri interni | Microsoft Docs"
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
  - "Classe di oggetto TaskScheduler [motori di debug di .NET Framework]"
  - "motori di debug, la classe oggetto TaskScheduler [.NET Framework]"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Classe di oggetto TaskScheduler - membri interni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni della <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe che consentono di implementare un debugger personalizzate. Per informazioni generali sulla classe, vedere il <xref:System.Threading.Tasks.TaskScheduler> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questi membri interni di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## Membri  
  
### Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matrice di tutte le attività pianificate.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.|  
  
## Note  
  
## Vedere anche  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Elementi interni di estensione parallela per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)