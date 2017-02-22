---
title: "IDebugSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2"
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore di \(DE\) debug per indicare che i simboli di debug per un modulo che viene eseguito il debug sono stati caricati.  
  
## Sintassi  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare che i simboli dei moduli caricati in.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per notificare che i simboli dei moduli caricati in.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 l'interfaccia di `IDebugSymbolSearchEvent2` espone il seguente metodo.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Recupera le informazioni sui risultati di una ricerca del simbolo.|  
  
## Note  
 Questo evento viene inviato anche se i simboli non riesce per caricare.  Chiamare `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` consente al gestore di questo evento per determinare se il modulo in realtà qualsiasi simboli.  
  
 Visual Studio utilizza in genere questo evento per aggiornare lo stato dei simboli caricati nella finestra di **moduli** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)