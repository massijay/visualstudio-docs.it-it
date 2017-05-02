---
title: "Interfaccia IDebugExpression | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugExpression"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugExpression
Rappresenta un'espressione in modo asincrono valutata.  I moduli di gestione di script in genere implementano l'interfaccia.  Un IDE del debugger utilizza in genere questa interfaccia per abilitare una finestra o una finestra Espressioni di controllo immediata di esecuzione.  
  
> [!NOTE]
>  L'interfaccia `IDebugExpression` è disponibile solo da uno stack frame.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugExpression` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Inizia la valutazione di un'espressione.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Interrompe l'espressione.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Determina se l'operazione viene completata.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Restituisce il risultato della valutazione di un'espressione come una stringa e il valore restituito dell'operazione.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Restituisce il risultato della valutazione di un'espressione come una proprietà di debug e il valore restituito dell'operazione.|