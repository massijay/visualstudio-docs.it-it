---
title: "Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Struttura PROFILER_HEAP_OBJECT_SCOPE_LIST
Questa struttura associata agli oggetti funzione solo.  L'elenco di ambito rappresenta la chiusura della funzione come elenco degli ambiti dove ogni ambito è un oggetto dell'heap con un elenco di proprietà associate che rappresenta le variabili di ogni ambito specificato.  In alcuni casi, i nomi degli oggetti in tale ambito potrebbero non essere disponibili solo e il relativo indice nell'elenco di proprietà è disponibile.  
  
## Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Membri  
  
|Membro|Type|Descrizione|  
|------------|----------|-----------------|  
|Conteggio|UINT|Il numero degli ambiti|  
|scopes|[Tipo PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Una matrice degli ambiti.|