---
title: "Supporto del servizio del linguaggio per il debug | Microsoft Docs"
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
  - "debugger, supporto del linguaggio"
  - "servizi Language, supporto per il debug"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Supporto del servizio del linguaggio per il debug
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio di linguaggio può fornire funzionalità che supportano un debugger tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaccia. Queste funzionalità includono la convalida dei punti di interruzione e si fornisce un elenco di espressioni per il **Auto** finestra.  
  
 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug del linguaggio. L'analizzatore di espressioni è responsabile per la valutazione di espressioni per produrre valori durante il debug. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere:  
  
-   [Analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Esempio di analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## Output del compilatore  
 Il tipo di compilatore determina ciò che è necessario eseguire per implementare il debug per la propria lingua. Se il compilatore riguarda il sistema operativo Windows e scrive un file con estensione pdb, è possibile eseguire il debug di programmi con il codice nativo, debug motore è integrato in Visual Studio. Se il compilatore produce Microsoft intermediate language \(MSIL\), è possibile eseguire il debug di programmi con il codice gestito, debug motore, è inoltre integrato in Visual Studio. Se il compilatore fa riferimento un sistema operativo proprietario o un ambiente di runtime diversi, è necessario scrivere il proprio motore di debug.  
  
 Per ulteriori informazioni sull'implementazione di debug per la lingua, vedere [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.