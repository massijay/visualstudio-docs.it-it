---
title: "Interfaccia IDebugThreadCall | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugThreadCall"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugThreadCall
L'interfaccia `IDebugThreadCall` in genere viene implementata da un componente che effettua chiamate cross\-thread con `IDebugThread` che ordina l'implementazione fornita dall'amministratore di processo \(PDM\) di debug.  
  
 Il PDM chiama l'interfaccia `IDebugThreadCall` nel thread desiderato e l'interfaccia `IDebugThreadCall` invia la chiamata all'implementazione desiderata.  L'interfaccia `IDebugThreadCall` esegue il cast delle informazioni di parametro passate nei parametri a l appropriata.  
  
 l'interfaccia `IDebugThreadCall` è un oggetto a thread libero.  
  
## Metodi  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugThreadCall` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Chiamate degli handle al codice in un altro thread.|