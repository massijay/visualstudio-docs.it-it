---
title: "Finestra di dialogo Risolvi ambiguit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "finestra di dialogo Risolvi ambiguità"
  - "debugger, finestra di dialogo Risolvi ambiguità"
  - "debug [C++], risoluzione dell'ambiguità"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Finestra di dialogo Risolvi ambiguit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La finestra di dialogo `Resolve Ambiguity` viene visualizzata quando il debugger non è in grado di determinare il percorso da visualizzare.  Se, ad esempio, si utilizzano i modelli C\+\+, è possibile creare più funzioni da un unico modello di funzione.  Se il debugger si arresta in corrispondenza di un percorso di origine nel modello e si sceglie `Go To Disassembly`, possono verificarsi più condizioni.  Ciascuna funzione creata dal modello ha un proprio codice disassembly e il debugger non è in grado di determinare quale codice si desidera visualizzare.  La finestra di dialogo `Resolve Ambiguity` consente di selezionare il percorso desiderato da un elenco di tutti i percorsi corrispondenti.  
  
 `Choose the specific location`  
 Elenca tutti i percorsi corrispondenti al comando.  
  
 `Address`  
 Mostra gli indirizzi di memoria per ciascuna funzione.  
  
 `Function`  
 Mostra il nome di ciascuna funzione.  
  
 `Module`  
 Mostra il modulo \(EXE o DLL\) che contiene il codice oggetto per la funzione.  
  
## Vedere anche  
 [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)