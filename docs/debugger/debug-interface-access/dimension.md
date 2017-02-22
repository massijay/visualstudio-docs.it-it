---
title: "Dimensione | Microsoft Docs"
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
  - "simbolo della dimensione"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dimensione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ogni matrice FORTRAN ha dimensioni che viene identificata da un oggetto `SymTagDimension` simbolo.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà valide aggiuntive per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|Limite inferiore di una dimensione della matrice FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|ID del simbolo limite inferiore.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagDimension` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Limite superiore della dimensione di una matrice FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|ID del simbolo limite superiore.|  
  
## Vedere anche  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)