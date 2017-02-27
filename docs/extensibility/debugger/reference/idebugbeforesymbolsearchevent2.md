---
title: "IDebugBeforeSymbolSearchEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugBeforeSymbolSearchEvent2"
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Il motore \(DE\) di debug invia questa interfaccia gestione \(SDM\) di debug della sessione per impostare il messaggio della barra di stato durante il caricamento dei simboli.  
  
## Sintassi  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia quando necessario impostare il messaggio della barra di stato durante il caricamento dei simboli.  Questa interfaccia è implementata solo dai motori di debug che utilizzano o è una parte degli interpreti dello script.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto di questa interfaccia \(utilizzi **QueryInterface** di SDM accedere all'interfaccia **IDebugEvent2** \).  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento quando necessario impostare il messaggio della barra di stato durante il caricamento dei simboli.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback fornite da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi di `IDebugBeforeSymbolSearchEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera il nome del modulo attualmente in corso di debug.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll