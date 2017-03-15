---
title: "Procedura: testare un visualizzatore ed eseguirne il debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "debug [Visual Studio], visualizzatori"
  - "visualizzatori, debug"
  - "visualizzatori, test"
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: testare un visualizzatore ed eseguirne il debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo avere scritto un visualizzatore, è necessario testarlo ed eseguirne il debug.  
  
 Una possibile soluzione per testare un visualizzatore consiste nell'installarlo in Visual Studio e nel chiamarlo da un finestra del debugger. Per ulteriori informazioni, vedere [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md). Se si sceglie questa soluzione, sarà necessario utilizzare una seconda istanza di Visual Studio per la connessione e il debug del visualizzatore, che verrà eseguito nella prima istanza del debugger.  
  
 Una soluzione più semplice per il debug di un visualizzatore consiste nell'eseguire il visualizzatore da un driver di test.  Utilizzando le API del visualizzatore è possibile creare con facilità un driver di questo tipo, che viene definito *host di sviluppo del visualizzatore*.  
  
### Per creare un host di sviluppo del visualizzatore  
  
1.  Nella classe del lato debugger includere un metodo statico che consenta di creare un oggetto <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> e di chiamare il relativo metodo di visualizzazione:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Come parametri per la costruzione dell'host vengono utilizzati l'oggetto dati che verrà mostrato nel visualizzatore \(`objectToVisualize`\) e il tipo della classe del lato debugger.  
  
2.  Aggiungere l'istruzione riportata di seguito per chiamare `TestShowVisualizer`.  Se il visualizzatore è stato creato in una libreria di classi, sarà necessario creare un eseguibile per chiamare la libreria di classi e inserire questa istruzione nell'eseguibile:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Per un esempio più esaustivo, vedere [Procedura dettagliata: scrittura di un visualizzatore in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## Vedere anche  
 [Procedura dettagliata: scrittura di un visualizzatore in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)