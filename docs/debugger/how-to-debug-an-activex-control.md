---
title: "Procedura: eseguire il debug di un controllo ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "controlli ActiveX (debug del contenitore) [Visual Studio]"
  - "controlli ActiveX, debug"
  - "contenitori, specifica per sessioni di debug"
  - "controlli con associazione a dati, ActiveX"
  - "debug dei controlli ActiveX"
  - "Test Container"
  - "test [Visual Studio], controlli ActiveX"
  - "test [Visual Studio], Test Container"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: eseguire il debug di un controllo ActiveX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Per effettuare il debug di un controllo ActiveX, è necessario specificare un contenitore \(eseguibile\) in cui elaborare il controllo stesso.  
  
### Per specificare un contenitore per la sessione di debug  
  
1.  Selezionare il progetto in Esplora soluzioni.  
  
2.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà del progetto** aprire la cartella **Proprietà di configurazione** e selezionare **Debug**.  
  
4.  Nella categoria **Debug** individuare la proprietà **Comando**.  
  
5.  Specificare il percorso del contenitore.  Ad esempio, C:\\Programmi\\Internet Explorer\\IEXPLORE.EXE.  
  
6.  Se si specifica Internet Explorer come contenitore ed è attivata la modalità Active Desktop, digitare `/new`  nella casella **Argomenti del comando**.  
  
7.  Scegliere **OK**.  
  
     Se non viene specificato alcun contenitore nella finestra di dialogo **Pagine delle proprietà del progetto**, sarà possibile specificarlo all'avvio del debug.  Quando si seleziona un comando per avviare il debug, viene visualizzata la finestra di dialogo [Eseguibile per la sessione di debug](../debugger/executable-for-debugging-session-dialog-box.md).  Nella finestra di dialogo specificare il nome percorso del contenitore.  
  
## Vedere anche  
 [Controlli ActiveX](/visual-cpp/mfc/activex-controls)   
 [Test di proprietà ed eventi con Test Container](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)