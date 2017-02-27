---
title: "Creazione di un&#39;estensione con una finestra degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Creazione di un&#39;estensione con una finestra degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura imparare a utilizzare il modello di progetto VSIX e **finestra degli strumenti personalizzata** modello di elemento per creare un'estensione con una finestra degli strumenti.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Creazione di una finestra degli strumenti  
  
1.  Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento della finestra strumento denominato **FirstWindow**. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome file della finestra strumento di **FirstWindow.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Verrà visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, passare a **Vista o altre finestre**.  
  
     Dovrebbe essere una voce di menu per **FirstWindow**. Fare clic.  
  
     Si dovrebbe essere una finestra degli strumenti con il titolo **FirstWindow** e una massima pulsante **Click Me\!.**