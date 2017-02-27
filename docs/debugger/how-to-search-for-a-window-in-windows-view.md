---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare una finestra specifica nella visualizzazione finestre utilizzando come criterio di ricerca l'handle, il titolo, la classe o una combinazione di titolo e classe.  È possibile inoltre specificare la direzione iniziale della ricerca.  Nei campi della finestra di dialogo saranno visualizzati gli attributi della finestra selezionata nella struttura ad albero della finestra.  
  
 Iniziare con la struttura ad albero espansa al secondo livello \(tutte le finestre figlio del desktop\), in modo che sia possibile identificare le finestre al livello del desktop in base al nome della classe e al titolo.  Una volta scelta una finestra al livello del desktop, è possibile espandere tale livello per individuare una specifica finestra figlio.  
  
### Per cercare una finestra nella visualizzazione finestre  
  
1.  Disporre le finestre in modo che la finestra di Spy\+\+, la finestra [Visualizzazione finestre](../debugger/windows-view.md) e quella di destinazione siano visibili.  
  
2.  Scegliere **Trova finestra** dal menu **Cerca**.  
  
     Viene visualizzata la [finestra di dialogo Ricerca finestre](../debugger/window-search-dialog-box.md).  
  
    > [!TIP]
    >  Per semplificare l'organizzazione dello schermo, selezionare l'opzione **Nascondi Spy**.  Questa opzione consente di nascondere la finestra principale di Spy\+\+ e di mantenere solo la finestra di dialogo **Ricerca finestre** visibile in primo piano rispetto alle altre applicazioni.  La finestra principale di Spy\+\+ viene ripristinata quando si fa clic su **OK** o su **Annulla** oppure quando si deseleziona l'opzione **Nascondi Spy\+\+**.  
  
3.  Trascinare lo **strumento di ricerca** sulla finestra di destinazione.  Quando si trascina lo strumento, nella finestra di dialogo **Ricerca finestre** vengono visualizzati i dettagli sulla finestra selezionata.  
  
     \- oppure \-  
  
     Se si conosce l'handle della finestra desiderata \(ad esempio dal debugger\), è possibile digitarlo nella casella **Handle**.  
  
     \- oppure \-  
  
     Se si conosce il titolo e\/o la classe della finestra desiderata, è possibile digitarli nelle caselle di testo **Titolo** e **Classe** e deselezionare la casella di testo **Handle**.  
  
4.  Scegliere **Su** o **Giù** per la direzione iniziale della ricerca.  
  
5.  Scegliere **OK**.  
  
     La finestra corrispondente eventualmente rilevata sarà evidenziata nella finestra [Visualizzazione finestre](../debugger/windows-view.md).