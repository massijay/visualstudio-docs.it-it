---
title: "IDiaStackWalker | Microsoft Docs"
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
  - "IDiaStackWalker (interfaccia)"
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornisce metodi per fare un percorso chiamate nello stack utilizzando informazioni nel file con estensione pdb.  
  
## Sintassi  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaStackWalker`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumeratore dello stack frame per le piattaforme x86.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumeratore dello stack frame per un tipo di piattaforma specifico.|  
  
## Note  
 Questa interfaccia viene utilizzata per ottenere un elenco degli stack frame per un modulo caricato.  Ognuno dei metodi viene passato [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto \(implementata dall'applicazione client\) che fornisce le informazioni necessarie per creare l'elenco degli stack frame.  
  
## Note per i chiamanti  
 Questa interfaccia è ottenuto chiamando `CoCreateInstance` metodo con l'identificatore di classe  `CLSID_DiaStackWalker` e l'ID dell'interfaccia di  `IID_IDiaStackWalker`.  Nell'esempio viene illustrata questa interfaccia viene ottenuta.  
  
## Esempio  
 In questo esempio viene illustrato come ottenere `IDiaStackWalker` interfaccia.  
  
```cpp#  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)