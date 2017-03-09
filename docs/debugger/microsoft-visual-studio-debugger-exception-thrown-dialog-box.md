---
title: "Finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)"
  - "gestione delle eccezioni, durante il debug"
  - "debugger, eccezioni"
  - "generazione eccezioni, durante il debug"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si è verificata un'eccezione nel programma.  In questa finestra di dialogo è indicato il tipo di eccezione generata.  Il codice deve gestire questa eccezione.  Per la gestione dell'eccezione sono disponibili le seguenti opzioni:  
  
 **Interrompi**  
 Consente il passaggio dell'esecuzione nel debugger.  Il gestore dell'eccezione non viene richiamato prima dell'interruzione,  ma solo se si sceglie di continuare dopo l'interruzione.  
  
 **Continua**  
 Consente all'esecuzione di continuare offrendo al gestore dell'eccezione la possibilità di gestirla.  Questa opzione non è disponibile per alcuni tipi di eccezioni.  **Continua** consentirà all'applicazione di proseguire.  In un'applicazione nativa, l'eccezione verrà generata nuovamente.  In un'applicazione gestita, il programma verrà interrotto oppure l'eccezione verrà gestita da un'applicazione host.  
  
> [!NOTE]
>  Non è possibile scegliere di continuare dopo un'eccezione non gestita nel codice gestito.  Se si sceglie **Continua** dopo un'eccezione non gestita nel codice gestito, il debug verrà interrotto.  
  
 **Ignora**  
 Consente all'esecuzione di continuare senza richiamare il gestore dell'eccezione.  Poiché il gestore dell'eccezione non viene richiamato, questa scelta può comportare ulteriori conseguenze, tra cui altre eccezioni o errori.  Questa opzione non è disponibile per alcuni tipi di eccezioni.  
  
## Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Suggerimenti per le eccezioni](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)