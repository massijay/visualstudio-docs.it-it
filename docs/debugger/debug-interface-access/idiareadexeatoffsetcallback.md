---
title: "IDiaReadExeAtOffsetCallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaReadExeAtOffsetCallback (interfaccia)"
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaReadExeAtOffsetCallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente a un'applicazione client fornire i byte di un file eseguibile come specificato dalla posizione del file.  
  
## Sintassi  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaReadExeAtOffsetCallback`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Legge il numero di byte che iniziano all'offset specificato da un file eseguibile.|  
  
## Note  
 L'applicazione client implementa questa interfaccia per definire i byte dell'eseguibile utilizzando un offset di assoluto nel file eseguibile.  Per utilizzare un indirizzo virtuale relativo, distribuire [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaccia.  
  
## Note per i chiamanti  
 Questo metodo viene implementato dall'applicazione client e viene passato a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo come metodo alternativo per la lettura del file.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)