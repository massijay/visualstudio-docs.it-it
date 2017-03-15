---
title: "Estensibilit&#224; del Debugger di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Visual Studio], Debugging SDK"
  - "Debug SDK"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Estensibilit&#224; del Debugger di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio include un debugger di codice sorgente completamente interattiva, che fornisce uno strumento potente e facile da utilizzare per tenere traccia dei bug nel programma. Il debugger ha il completo supporto di Visual Basic, c\#, C\/C\+\+ e JavaScript. Tuttavia, con la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], che è disponibile il [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front\-end comune \(ovvero, l'interfaccia utente\) per i componenti di debug che sono, a sua volta, a seconda della lingua in fase di debug. Per nuove lingue, è sufficiente per supportare per la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger consiste nel creare i componenti necessari di back\-end, ad esempio un motore di debug \(DE\). Casi di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra in gioco.  
  
 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento completo a tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi necessari per creare un nuovo DE. Inoltre, esistono esempi ed esercitazioni che consentono di iniziare.  
  
 Per un esempio end\-to\-end di un sistema di progetto linguaggio con supporto per il debug, vedere il [IronPython sample](http://msdn.microsoft.com/it-it/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Nelle sezioni seguenti viene descritto come estendere il debugger tramite il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## In questa sezione  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Vengono descritte le operazioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug offerte e su come installare il SDK.  
  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta il processo DE personalizzato, dalla preparazione del programma per un DE per scollegare il DE.  
  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Viene spiegato se è necessario scrivere un analizzatore di espressioni.  
  
 [Scelta di una strategia di implementazione del motore di Debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Viene illustrato come implementare il DE.  
  
 [Reference](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'API di debug.  
  
 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene collegamenti per un esempio di common language runtime espressione analizzatore e un esempio di motore di debug.