---
title: "Gerarchia di classi dei tipi di simboli | Microsoft Docs"
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
  - "simboli [DIA SDK], gerarchie di classi"
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Gerarchia di classi dei tipi di simboli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella tabella seguente viene descritto il simbolo nella gerarchia di classi.  
  
## Tipi dei simboli  
  
|Tipo dei simboli|Descrizione|  
|----------------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Simbolo utilizzato per rappresentare ogni classe, struttura o unione.|  
|[Enum \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|I simboli per i tipi enumerati.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|I simboli per i tipi di puntatore.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|I simboli per i tipi di matrice.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|I simboli per i tipi di base|  
|[Typedef \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|simbolo che introduce i nomi per altri tipi.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Simbolo utilizzato per ciascuna classe base del tipo \(UDT\).|  
|[Friend \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Simbolo per le classi e friend le funzioni friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Simbolo per ogni firma della funzione univoca.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Simbolo per ogni parametro a una funzione.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Simbolo per la dimensione della tabella virtuale.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|simbolo per una tabella virtuale.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|simbolo per tipo fornitore\-definito.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|I simboli per un tipo definito nei metadati.|  
|[Dimensione](../../debugger/debug-interface-access/dimension.md)|Simbolo per le dimensioni della matrice.|  
  
> [!NOTE]
>  Ciascun simbolo può disporre di proprietà che utilizzano le informazioni sul simbolo oltre a riferimenti ad altri simboli.  Queste proprietà sono elencate nei singoli argomenti del simbolo.  
  
## Vedere anche  
 [Enumerazione CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)