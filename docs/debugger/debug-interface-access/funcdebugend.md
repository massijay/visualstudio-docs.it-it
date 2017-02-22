---
title: "FuncDebugEnd | Microsoft Docs"
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
  - "FuncDebugEnd (simbolo)"
  - "debug [DIA SDK], punto finale"
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# FuncDebugEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se una funzione dispone di un determinato punto su cui eseguire il debug sia della fine, il punto iniziale di debug è identificato da un simbolo con un oggetto `SymTagFuncDebugEnd` tag.  
  
## Proprietà  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte offset di posizione, per ulteriori informazioni, vedere [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte della sezione di posizione, per ulteriori informazioni, vedere [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` se la funzione viene utilizzata una convenzione di chiamata personalizzata \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` se la funzione ha eseguito per un return \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` se la funzione contiene un ritorno dall'interruzione \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` se la funzione è statica \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per la funzione che lo contiene.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|i punti finali hanno posizione statica; per ulteriori informazioni, vedere [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` se la funzione è stata specificata con  [noinline](/visual-cpp/cpp/noinline) attributo \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` se la funzione è stata specificata con  [noreturn](/visual-cpp/cpp/noreturn) attributo \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` se la funzione non viene mai chiamata \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del simbolo in memoria, per ulteriori informazioni, vedere [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md),  `LocIsRegRel`.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` se la funzione contiene informazioni di debug per il codice ottimizzato \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa della fine di questa funzione all'interno del form.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagFuncDebugEnd` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Percorso di questa funzione l'interno dell'immagine eseguibile.|  
  
## Vedere anche  
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)