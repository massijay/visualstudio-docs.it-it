---
title: "IDebugIDECallback | Microsoft Docs"
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
  - "Interfaccia IDebugIDECallback"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Consente un analizzatore di espressioni \(EE\) visualizzare un messaggio nella finestra di output del debugger.  
  
## Sintassi  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## Note per gli implementatori  
 Questo callback viene implementato dal motore di debug gestito.  
  
## Note per chiamanti  
 Che può essere utilizzata da un analizzatore di espressioni per inviare l'output alla finestra di output del debugger.  
  
## Metodi  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|Invia la stringa di messaggio specificato alla finestra di output del debugger.|  
  
## Requisiti  
 Intestazione: Ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll