---
title: "IDiaStackWalkFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkFrame (interfaccia)"
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gestisce il contesto dello stack tra le chiamate di [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo.  
  
## Sintassi  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaStackWalkFrame`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|recupera il valore di un registro.|  
|[IDiaStackWalkFrame::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Legge la memoria nell'immagine.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Cercare lo stack frame specificato l'indirizzo di ritorno di una funzione più vicino.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Cercare lo stack frame specificato un indirizzo del mittente in corrispondenza dell'indirizzo specificato.|  
  
## Note  
 Questa interfaccia viene utilizzata durante l'esecuzione del programma per leggere e scrivere i registri nonché gli indirizzi del mittente di ricerca e di memoria di accesso.  
  
## Note per i chiamanti  
 L'applicazione client implementa questa interfaccia e passa un'istanza dell'interfaccia a [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metodo.  La stessa istanza di questa interfaccia viene utilizzata più volte per gestire lo stato dei registri durante ogni chiamata di `execute` metodo.  `execute` il metodo utilizza questa interfaccia per determinare l'indirizzo di ritorno.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)