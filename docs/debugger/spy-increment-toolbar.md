---
title: "Spy++ Toolbar | Microsoft Docs"
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
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La barra degli strumenti viene visualizzata sotto la barra dei menu in Spy\+\+.  Per visualizzare o nascondere la barra degli strumenti, scegliere **Barra degli strumenti** dal menu **Visualizza**.  
  
 I seguenti controlli sono disponibili nella barra degli strumenti.  
  
## Elenco UIElement  
  
|Button|Effetto|  
|------------|-------------|  
|![Pulsante Finestre di Spy&#43;&#43;](../debugger/media/icon_spy--_windows.png "Icon\_Spy\+\+\_Windows")|Viene mostrata una visualizzazione struttura ad albero delle finestre e dei controlli nel sistema.  Per ulteriori informazioni, vedere [Windows View](../debugger/windows-view.md).|  
|![Pulsante Processi di Spy&#43;&#43;](../debugger/media/icon_spy--_processes.png "Icon\_Spy\+\+\_Processes")|Viene mostrata una visualizzazione struttura ad albero dei processi nel sistema.  Per ulteriori informazioni, vedere [Processes View](../debugger/processes-view.md).|  
|![Pulsante Thread di Spy&#43;&#43;](../debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|Viene mostrata una visualizzazione struttura ad albero dei thread nel sistema.  Per ulteriori informazioni, vedere [Threads View](../debugger/threads-view.md).|  
|![Pulsante Messaggi di Spy&#43;&#43;](../debugger/media/icon_spy--_messages.png "Icon\_Spy\+\+\_Messages")|Consente di creare una finestra che visualizza messaggi e di aprire la finestra di dialogo **Opzioni messaggio** in modo che sia possibile selezionare sia la finestra di cui saranno visualizzati i messaggi sia le altre opzioni.  Per ulteriori informazioni, vedere [Messages View](../debugger/messages-view.md).|  
|![Pulsante Avvia registro di Spy&#43;&#43;](../debugger/media/icon_spy--_startlog.png "Icon\_Spy\+\+\_StartLog")|Consente di avviare la registrazione di messaggi e di visualizzarne il flusso.  Questo controllo è disponibile solo quando una finestra **Messaggi** è la finestra attiva.  Per ulteriori informazioni, vedere [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Pulsante Arresta registro di Spy&#43;&#43;](../debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|Consente di arrestare la registrazione di messaggi e la visualizzazione del relativo flusso.  Questo controllo è disponibile solo quando una finestra **Messaggi** è la finestra attiva.  Per ulteriori informazioni, vedere [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Pulsante Opzioni registro di Spy&#43;&#43;](../debugger/media/icon_spy--_logoptions.png "Icon\_Spy\+\+\_LogOptions")|Viene visualizzata la finestra di dialogo [Opzioni messaggio](../debugger/message-options-dialog-box.md).  Utilizzare questa finestra di dialogo per selezionare i tipi di finestre e messaggi per la visualizzazione.  Questo controllo è disponibile solo quando una finestra **Messaggi** è la finestra attiva.|  
|![Pulsante Cancella log di Spy&#43;&#43;](../debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|Consente di cancellare il contenuto della finestra **Messaggi** attiva.  Questo controllo è disponibile solo quando una finestra **Messaggi** è la finestra attiva.|  
|![Pulsante Trova finestra di Spy&#43;&#43;](../debugger/media/icon_spy--_findwindow.png "Icon\_Spy\+\+\_FindWindow")|Apre la finestra di dialogo [Trova finestra](../debugger/find-window-dialog-box.md) per impostare i criteri di ricerca della finestra e visualizzare le proprietà o i messaggi.  Per ulteriori informazioni, vedere [How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|  
|![Pulsante Trova prima finestra di Spy&#43;&#43;](../debugger/media/icon_spy--_window.png "Icon\_Spy\+\+\_Window")|Consente di cercare una finestra, un processo, un thread o un messaggio corrispondente nella visualizzazione corrente.|  
|![Pulsante Trova finestra successiva di Spy&#43;&#43;](../debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|Consente di cercare la finestra, il processo, il thread o il messaggio successivo corrispondente nella visualizzazione corrente.  Questo controllo \(e il comando di menu correlato\) è disponibile solo quando viene restituito un risultato di ricerca valido e non univoco.  Ad esempio quando si utilizza un handle di finestra come criterio di ricerca nella struttura ad albero della finestra, verranno restituiti risultati univoci poiché è disponibile una sola finestra con tale handle nella struttura ad albero della finestra; in questo caso, l'opzione **Trova successivo** non è disponibile.|  
|![Pulsante Trova finestra precedente di Spy&#43;&#43;](../debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|Consente di cercare la finestra, il processo, il thread o il messaggio precedente corrispondente nella visualizzazione corrente.  Questo controllo \(e il comando di menu correlato\) è disponibile solo quando viene restituito un risultato di ricerca valido e non univoco.  Ad esempio quando si utilizza un handle di finestra come criterio di ricerca nella struttura ad albero della finestra, verranno restituiti risultati univoci poiché è disponibile una sola finestra con tale handle nella struttura ad albero della finestra; in questo caso, l'opzione **Trova precedente** non è disponibile.|  
|![Pulsante di visualizzazione proprietà di Spy&#43;&#43;](../debugger/media/icon_spy--_propexp.png "Icon\_Spy\+\+\_PropExp")|Vengono visualizzare le proprietà della finestra selezionata nella visualizzazione finestre.|  
|![Pulsante Aggiorna di Spy&#43;&#43;](../debugger/media/icon_spy--_refresh.png "Icon\_Spy\+\+\_Refresh")|Aggiorna le visualizzazioni di sistema.|  
  
## Vedere anche  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)