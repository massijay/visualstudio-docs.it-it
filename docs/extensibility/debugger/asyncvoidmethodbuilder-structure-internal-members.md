---
title: "Struttura AsyncVoidMethodBuilder - membri interni | Microsoft Docs"
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
  - "motori di debug, la struttura AsyncVoidMethodBuilder [.NET Framework]"
  - "Struttura AsyncVoidMethodBuilder [motori di debug di .NET Framework]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Struttura AsyncVoidMethodBuilder - membri interni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni della <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Per informazioni generali sulla classe, vedere il <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questi membri interni di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Membri interni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore al debugger.|  
|[campo m\_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Rappresenta l'oggetto inizializzato in modalità differita utilizzato dal debugger per identificare in modo univoco questo generatore.|  
  
## Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Elementi interni di estensione parallela per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)