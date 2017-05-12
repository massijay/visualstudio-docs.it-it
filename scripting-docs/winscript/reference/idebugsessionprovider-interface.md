---
title: "Interfaccia IDebugSessionProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugSessionProvider"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugSessionProvider
L'interfaccia primaria fornita da un IDE del debugger per abilitare l'host e il linguaggio ha avviato il debug.  Stabilisce una sessione di debug per un'applicazione in esecuzione.  L'interfaccia viene implementata dall'amministratore del computer di debug.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugSessionProvider` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Avviare una sessione di debug con l'applicazione specificata.|