---
title: "Struttura AsyncTaskMethodBuilder - membri interni | Microsoft Docs"
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
  - "motori di debug, la struttura AsyncTaskMethodBuilder [.NET Framework]"
  - "Struttura AsyncTaskMethodBuilder [motori di debug di .NET Framework]"
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Struttura AsyncTaskMethodBuilder - membri interni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Per informazioni generali sulla classe, vedere il <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questi membri interni di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Membri interni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore al debugger.|  
|[campo m\_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Rappresenta l'oggetto generatore generico a cui delega questa istanza non generici.|  
  
## Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Elementi interni di estensione parallela per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)