---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare un thread specifico nella visualizzazione thread utilizzando come criterio di ricerca l'ID thread o la stringa del modulo.  È possibile inoltre specificare la direzione iniziale della ricerca.  Nei campi della finestra di dialogo saranno visualizzati gli attributi del thread selezionato nella struttura ad albero del thread.  
  
### Per cercare un thread nella visualizzazione thread  
  
1.  Disporre le finestre in modo che la finestra di Spy\+\+ e una finestra [Visualizzazione finestre](../debugger/threads-view.md) attiva siano visibili.  
  
2.  Scegliere **Trova thread** dal menu **Cerca**.  
  
     Viene visualizzata la [finestra di dialogo Ricerca thread](../debugger/thread-search-dialog-box.md).  
  
3.  Digitare l'ID thread o una stringa del modulo come criterio di ricerca.  
  
4.  Deselezionare qualsiasi campo per il quale non si desideri specificare valori.  
  
    > [!TIP]
    >  Per trovare tutti i thread di proprietà di un modulo, deselezionare la casella di testo **Thread** e digitare il nome del modulo nella casella **Modulo**.  Utilizzare quindi l'opzione **Trova successivo** per continuare la ricerca dei thread.  
  
5.  Scegliere **Su** o **Giù** per la direzione iniziale della ricerca.  
  
6.  Scegliere **OK**.  
  
 Il thread corrispondente eventualmente rilevato sarà evidenziato nella finestra di visualizzazione dei thread.