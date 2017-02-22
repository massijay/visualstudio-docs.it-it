---
title: "VTableShape | Microsoft Docs"
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
  - "VTableShape (simbolo)"
  - "Tag SymTagVTableShape"
ms.assetid: dd97f4c3-115d-46a9-b506-2531e30a0d8f
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VTableShape
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[VTable](../../debugger/debug-interface-access/vtable.md) il simbolo è simbolo figlio della classe identificata da  `SymTagVTableShape` tag.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà valide aggiuntive per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` se la classe di Riferimento è contrassegnata come costante.|  
|[IDiaSymbol::get\_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Numero di voci nella tabella VTable.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo del modulo di inclusione.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagVTableShape` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` se la classe di VTable non è allineato.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` se la classe di Riferimento è contrassegnata come volatile.|  
  
## Vedere anche  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTable](../../debugger/debug-interface-access/vtable.md)