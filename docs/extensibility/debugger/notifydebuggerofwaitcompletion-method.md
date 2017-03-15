---
title: "Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Metodo NotifyDebuggerOfWaitCompletion, classe di attività [motori di debug di .NET Framework]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo NotifyDebuggerOfWaitCompletion
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Metodo segnaposto utilizzato come destinazione del punto di interruzione dal debugger. Questo metodo non deve essere resa inline o ottimizzata.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
## Sintassi  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## Note  
 Tutte le operazioni di join con un'attività devono chiamare questo metodo se è impostato il bit di notifica di debugger.  
  
## Requisiti  
  
## Vedere anche  
 [Classe attività](../../extensibility/debugger/task-class-internal-members.md)