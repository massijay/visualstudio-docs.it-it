---
title: "Thunk | Microsoft Docs"
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
  - "thunk (proprietà) [DIA SDK]"
  - "thunk (simbolo)"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Thunk
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ciascuno `thunk` è identificato da un oggetto  `SymTagThunk` tag.  
  
## Proprietà  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Attributo del modificatore di accesso, uno di [Enumerazione CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md) valori \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte offset di posizione, per ulteriori informazioni, vedere [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Parte della sezione di posizione, per ulteriori informazioni, vedere [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Elemento padre della classe interna, se qualsiasi \(solo in DIA SDK V8.0 o versioni successive\).|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID del simbolo della classe padre interna \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|TRUE se il thunk viene contrassegnato come costante \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|TRUE se il thunk viene un'introduzione a una funzione virtuale \(solo DIA SDK in V8.0 o in versioni successive\)|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|TRUE se il thunk viene considerato static \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Numero di byte del codice nel thunk.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|I simboli per il modulo, il blocco, o la funzione di inclusione.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|i punti finali hanno posizione statica; per ulteriori informazioni, vedere [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md) enumerazione.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome del thunk.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|TRUE se il thunk è puramente virtuale \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa del thunk all'interno del form.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagThunk` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Parte offset del percorso di destinazione di thunk.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Indirizzo virtuale relativo del database di destinazione di thunk nel blocco di inclusione.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Parte della sezione di destinazione thunk.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Percorso di destinazione thunk nell'immagine eseguibile.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Tipo di thunk, come definito da [Enumerazione THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Il tipo del thunk \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID del simbolo del tipo \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` se il thunk non è allineato \(solo DIA SDK in V8.0 o in versioni successive\),|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` se il thunk è virtuale \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione del thunk l'interno dell'immagine eseguibile.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|L'offset nella tabella virtuale al thunk \(solo DIA SDK in V8.0 o in avanti\).|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` se il thunk è contrassegnato come volatile \(solo DIA SDK in V8.0 o in versioni successive\).|  
  
## Vedere anche  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Enumerazione THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)