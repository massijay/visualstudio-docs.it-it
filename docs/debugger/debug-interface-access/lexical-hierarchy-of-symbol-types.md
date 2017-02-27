---
title: "Gerarchia lessicale dei tipi di simboli | Microsoft Docs"
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
  - "simboli [DIA SDK], gerarchie di tipi"
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Gerarchia lessicale dei tipi di simboli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella tabella seguente viene illustrato il simbolo nella gerarchia lessicale.  
  
## Tipi dei simboli  
  
|Tipo dei simboli|Descrizione|  
|----------------------|-----------------|  
|[Annotazione](../../debugger/debug-interface-access/annotation.md)|Specifica un percorso annotata nel codice programma.|  
|[Blocco](../../debugger/debug-interface-access/block.md)|Specifica annidato gli ambiti funzioni.|  
|`Compiland`|Specifica un oggetto `compiland` l'accesso al file EXE.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Specifica i dati del modulo che possono richiedere i dettagli aggiuntivi del modulo e provocare tale sovraccarico di runtime da recuperare.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Specifica tutte le variabili di ambiente significative alla compilazione del modulo.|  
|[Custom \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Specifica un simbolo definito dall'utente.|  
|[Dati \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Specifica tali variabili come parametri, variabili locali, le variabili globali e i membri della classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Specifica l'ambito globale dei dati, corrisponde a un intero file EXE o al file DLL.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Specifica una funzione con un determinato punto su cui eseguire il debug sia di fine.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Specifica una funzione con un determinato punto su cui eseguire il debug verrà avviato.|  
|[Funzione \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|specifica una funzione.|  
|[Etichetta \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Specifica una posizione nel codice programma.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Specifica un simbolo esterno che viene visualizzato quando si compila il programma eseguibile.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Specifica un oggetto `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Specifica un oggetto `namespace`identificatore.|  
  
> [!NOTE]
>  Le proprietà aggiuntive dei simboli possono essere disponibili in base al tipo del simbolo.  Queste proprietà sono elencate nei singoli argomenti del simbolo.  
  
## Vedere anche  
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)