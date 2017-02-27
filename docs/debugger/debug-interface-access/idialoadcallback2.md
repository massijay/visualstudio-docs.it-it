---
title: "IDiaLoadCallback2 | Microsoft Docs"
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
  - "IDiaLoadCallback2 (interfaccia)"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Riceve i callback dal simbolo di diametro che individua la routine, consentendo le restrizioni per imporre al processo un'eccezione.  
  
## Sintassi  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## Metodi nell'ordine di Vtable  
 oltre ai metodi in [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) collegare, esposte da questa interfaccia i seguenti metodi:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se la ricerca di un file con estensione pdb nella directory di origine di debug.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina se trovare un file con estensione pdb viene consentito il percorso in cui si trova il file EXE si trova.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se la ricerca delle informazioni di debug è consentito dai file di estensione dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se trovare i file con estensione pdb è consentita nella directory radice del sistema.|  
  
## Note  
 L'applicazione client implementa questa interfaccia e viene fornito un riferimento a nella chiamata a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodo.  Ricordare implementare tutti i metodi in [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interfaccia anche.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)