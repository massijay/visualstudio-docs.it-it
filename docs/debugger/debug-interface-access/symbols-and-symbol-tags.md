---
title: "Simboli e relativi tag | Microsoft Docs"
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
  - "simboli [DIA SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Simboli e relativi tag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le informazioni di debug su un programma compilato vengono memorizzate nel file di database di programma \(PDB\) come simboli che sono accessibili tramite il Debug Interface Access \(DIA\) SDK di.  Tutti i simboli con un'[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e  [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) proprietà.  `symTag` la proprietà indica il tipo di simbolo definito da  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione.  `symIndexId` la proprietà è un oggetto  `DWORD` prevedere che contiene l'identificatore univoco per ogni istanza di un simbolo.  
  
 I simboli dispongono di proprietà che possono specificare informazioni aggiuntive sul simbolo oltre a riferimenti ad altri simboli, in genere a [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o  [IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md).  Quando si esegue una query su una proprietà che contiene un riferimento, il riferimento viene restituito [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto.  Tali proprietà sono sempre combinate con un'altra proprietà con lo stesso nome ma sono suffiggute con “id„, ad esempio, [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e  [IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md).  Le tabelle in [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md),  [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)e  [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) descrivere le proprietà per ognuno dei tipi diversi di simboli.  Queste proprietà possono presentare informazioni rilevanti su o riferimenti ad altri simboli.  Poiché `*Id` le proprietà sono identificatori ordinali semplicemente numerici delle proprietà correlate, che vengono omessi da altre discussioni.  Si riferiscono solo a cui necessario per chiarimento di parametro.  
  
 Nel provare ad accedere alla proprietà, se non si verificano errori e la proprietà del simbolo è stato assegnato un valore, la proprietà “get„ il metodo restituisce `S_OK`.  un valore restituito di `S_FALSE` indica che la proprietà non è valida per il simbolo corrente.  
  
## In questa sezione  
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)  
 Vengono descritti i diversi tipi di posizioni che un simbolo può avere.  
  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Vengono descritti i tipi di simboli che costituiscono le gerarchie lessicali come i file, moduli e funzioni.  
  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Vengono descritti i tipi di simboli che corrispondono agli elementi del linguaggio diversi quali classi, matrici e tipi restituiti dalla funzione.  
  
## Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)