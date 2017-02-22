---
title: "Impossibile visualizzare il codice sorgente o il disassembly | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "codice disassembly, errori"
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Impossibile visualizzare il codice sorgente o il disassembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il testo del messaggio di errore è il seguente:  
  
 Impossibile visualizzare il codice sorgente o disassembly relativo alla posizione corrente in cui si è interrotta l'esecuzione.  
  
 Questo messaggio di errore può essere visualizzato in alcune situazioni:  
  
-   È possibile che sia stato raggiunto un punto di interruzione in una posizione per la quale non esiste un codice sorgente, mentre si esegue il debug di un linguaggio che non supporta il disassembly.  Aprire la finestra **Punti di interruzione**, individuare il punto di interruzione ed eliminarlo.  
  
-   Se si sta eseguendo il debug di script, è possibile che sia stato raggiunto un punto di interruzione mentre non esistevano thread nel programma.  Scegliere **Esegui** o **Continua** dal menu **Debug** per continuare l'esecuzione del debug.  
  
-   È possibile che per aspetti relativi alla sicurezza il debugger non sia stato in grado di leggere lo stack, il thread, il registro e altre informazioni sul contesto dal programma di cui si sta eseguendo il debug.  Questa condizione si verifica più spesso se si esegue il debug di un'applicazione Web e non si dispone dell'autorizzazione corretta per accedere alla directory virtuale.  Impostare la sicurezza anonima per la directory virtuale e riprovare.  
  
## Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)