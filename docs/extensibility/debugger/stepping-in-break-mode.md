---
title: "L&#39;esecuzione in modalit&#224; di interruzione | Microsoft Docs"
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
  - "modalità di interruzione, l'esecuzione di istruzioni"
  - "esecuzione di istruzioni, in modalità di interruzione"
  - "debug [Debugging SDK], esecuzione di istruzioni in modalità di interruzione"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# L&#39;esecuzione in modalit&#224; di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve eseguire il codice un'istruzione alla volta:  
  
## Processo avanzare  
  
1.  chiamata [IDebugProgram2:: passaggio](../../extensibility/debugger/reference/idebugprogram2-step.md) con gli argomenti di [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e di [STEPKIND](../../extensibility/debugger/reference/stepkind.md) per eseguire un passaggio.  
  
2.  Quando il passaggio viene completato, inviare [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) come evento bloccato.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)