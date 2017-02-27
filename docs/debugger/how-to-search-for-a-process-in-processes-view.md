---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare un processo specifico nella visualizzazione processi utilizzando come criterio di ricerca l'ID processo o la stringa del modulo.  È possibile inoltre specificare la direzione iniziale della ricerca.  Nei campi della finestra di dialogo saranno visualizzati gli attributi del processo selezionato nella struttura ad albero del processo.  
  
### Per cercare un processo nella visualizzazione processi  
  
1.  Disporre le finestre in modo che la finestra di Spy\+\+ e una finestra [Visualizzazione processi](../debugger/processes-view.md) attiva siano visibili.  
  
2.  Scegliere **Trova processo** dal menu **Cerca**  
  
     Viene visualizzata la [finestra di dialogo Ricerca processi](../debugger/process-search-dialog-box.md).  
  
3.  Digitare l'ID processo o una stringa del modulo come criterio di ricerca.  
  
4.  Deselezionare qualsiasi campo per il quale non si desideri specificare valori.  
  
    > [!TIP]
    >  Per trovare tutti i processi di proprietà di un modulo, deselezionare la casella di testo **Processo** e digitare il nome del modulo nella casella **Modulo**.  Utilizzare quindi l'opzione **Trova successivo** per continuare la ricerca dei processi.  
  
5.  Scegliere **Su** o **Giù** per la direzione iniziale della ricerca.  
  
6.  Scegliere **OK**.  
  
 Il processo corrispondente eventualmente rilevato sarà evidenziato nella finestra **Visualizzazione processi**.