---
title: "Exe | Microsoft Docs"
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
  - ".dll (file)"
  - "Exe (simbolo)"
  - ".exe (file)"
  - "file eseguibili, Exe (simbolo)"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il file EXE è l'unico simbolo senza lessicale o le classi il padre, poiché rappresenta l'ambito globale del file EXE o DLL.  È presente un simbolo con `SymTagExe` tag per file.  [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) il metodo restituisce il simbolo.  
  
## Proprietà  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Validità del file eseguibile.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` del file eseguibile.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` se il file di simboli associato all'eseguibile contiene i tipi C \(solo DIA SDK in v8.0 o in avanti\).|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` se privato i simboli sono stati rimossi dal file di simboli associato all'eseguibile \(solo DIA SDK in v8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valore che indica la CPU di destinazione \(uno di [Enumerazione CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valori\).|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome del file EXE.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Firma dell'eseguibile.|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Percorso completo del file con estensione pdb o di dbg del file EXE.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagExe` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
  
## Vedere anche  
 [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)