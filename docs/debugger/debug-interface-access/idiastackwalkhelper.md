---
title: "IDiaStackWalkHelper | Microsoft Docs"
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
  - "IDiaStackWalkHelper2 (interfaccia)"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Facilitates che verifica il percorso chiamate nello stack utilizzando il file di database di debug del programma \(PDB\).  
  
## Sintassi  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## Metodi nell'ordine di VTable  
 Nella tabella riportata di seguito sono illustrati i metodi di `IDiaStackWalkHelper`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|recupera il valore di un registro.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Imposta il valore di un registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Legge un blocco di dati nell'immagine eseguibile in memoria.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Cercare lo stack frame specificato l'indirizzo di ritorno di una funzione più vicino.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Cercare lo stack frame specificato un indirizzo del mittente in corrispondenza dell'indirizzo specificato dello stack.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera lo stack frame contenente l'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera il simbolo contenente l'indirizzo virtuale specificato. **Note:**  il simbolo deve avere il tipo `SymTagFunctionType` \(un valore dal  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione\).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Restituisce il blocco di dati PDATA associato all'indirizzo virtuale specificato.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Viene recuperato l'indirizzo virtuale iniziale di un eseguibile, immesso un indirizzo virtuale nello spazio di memoria dell'eseguibile.|  
  
## Note  
 Questa interfaccia viene chiamata dal codice di diametro per ottenere informazioni sul file eseguibile per creare un elenco con stack frame durante l'esecuzione del programma.  
  
## Note per i chiamanti  
 Un'applicazione client implementa questa interfaccia per supportare la consultazione lo stack durante l'esecuzione del programma.  Un'istanza di questa interfaccia viene passata a [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o  [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metodi.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)