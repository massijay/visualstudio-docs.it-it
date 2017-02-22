---
title: "How to: Search for a Message in Messages View | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Message Search dialog box"
  - "Messages view"
  - "messages, searching for"
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Message in Messages View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare un messaggio specifico nella visualizzazione messaggi utilizzando come criterio di ricerca l'handle, il tipo o l'ID messaggio.  Ciascuno di questi o la relativa combinazione è considerato un criterio di ricerca valido.  È possibile inoltre specificare la direzione iniziale della ricerca.  Nei campi della finestra di dialogo vengono precaricati gli attributi del messaggio attualmente selezionato.  
  
### Per cercare un messaggio nella visualizzazione messaggi  
  
1.  Disporre le finestre in modo che la finestra di Spy\+\+ e una finestra [Visualizzazione messaggi](../debugger/messages-view.md) attiva siano visibili.  
  
2.  Scegliere **Trova messaggio** dal menu **Cerca**.  
  
     Viene visualizzata la [finestra di dialogo Ricerca messaggi](../debugger/message-search-dialog-box.md).  
  
3.  Trascinare lo **strumento di ricerca** sulla finestra desiderata.  Quando si trascina lo strumento, nella finestra di dialogo **Ricerca messaggi** vengono visualizzati i dettagli sulla finestra selezionata.  
  
     \- oppure \-  
  
     Se si conosce l'handle della finestra di cui si desidera esaminare i messaggi, digitarlo nella casella di testo **Handle**.  
  
     \- oppure \-  
  
     Se si conosce il tipo di messaggio e\/o l'ID messaggio desiderati, selezionarli dai menu a discesa **Tipo** e **Messaggio** e deselezionare la casella di testo **Handle**.  
  
4.  Deselezionare qualsiasi campo per il quale non si desideri specificare valori.  
  
    > [!TIP]
    >  Per semplificare l'organizzazione dello schermo, selezionare l'opzione **Nascondi Spy**.  Questa opzione consente di nascondere la finestra principale di Spy\+\+ e di mantenere solo la finestra di dialogo **Trova finestra** visibile in primo piano rispetto alle altre applicazioni.  La finestra principale di Spy\+\+ viene ripristinata quando si fa clic su **OK** o su **Annulla** oppure quando si deseleziona l'opzione **Nascondi Spy\+\+**.  
  
5.  Scegliere **Su** o **Giù** per la direzione iniziale della ricerca.  
  
6.  Scegliere **OK**.  
  
 Il messaggio corrispondente eventualmente rilevato sarà evidenziato nella finestra di visualizzazione messaggi.  Vedere [Visualizzazione messaggi](../debugger/messages-view.md).