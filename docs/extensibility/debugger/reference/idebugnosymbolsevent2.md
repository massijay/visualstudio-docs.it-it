---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugNoSymbolsEvent2"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Segnala l'interfaccia utente del debugger di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per avvertire l'utente che i simboli non potrebbero trovarsi nell'eseguibile avviato.  
  
## Sintassi  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Implementato dai motori di debug e utilizzato dall'interfaccia utente del debugger di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll