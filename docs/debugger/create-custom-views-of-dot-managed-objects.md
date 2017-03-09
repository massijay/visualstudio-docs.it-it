---
title: "Visualizzazione di tipi di dati personalizzati | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat (file)"
  - "tipi di dati personalizzati"
  - "tipi di dati [C#], personalizzati"
  - "debugger, espansione di tipi di dati"
  - "codice gestito, tipi di dati personalizzati"
  - "mcee_cs.dat (file)"
  - "mcee_mc.dat (file)"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione di tipi di dati personalizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.  
  
## Attributi  
 In C\# e Visual Basic, è possibile aggiungere espansioni per dati personalizzati tramite <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Nel codice [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Visual Basic non supporta l'attributo DebuggerBrowsable.  Questa limitazione è stata rimossa nelle versioni più recenti di .NET Framework.  
  
## Visualizzatori  
 È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito.  Per ulteriori informazioni, vedere [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md).  
  
## Codice nativo  
 Per il codice nativo, è possibile aggiungere espansioni per tipi di dati personalizzati al file autoexp.dat, che si trova nella directory Programmi\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger.  Le istruzioni relative alla sintassi delle regole `autoexp` sono contenute nel file stesso.  
  
> [!CAUTION]
>  La struttura di questo file e la sintassi delle regole autoexp possono variare in base alle diverse versioni di Visual Studio.  
  
 Le visualizzazioni del tipo nativo possono anche essere personalizzate scrivendo un componente aggiuntivo dell'analizzatore di espressioni.  Per ulteriori informazioni, vedere [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/it-it/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## Vedere anche  
 [Utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)