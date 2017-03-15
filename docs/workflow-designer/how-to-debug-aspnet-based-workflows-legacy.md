---
title: "Procedura: eseguire il debug di flussi di lavoro basati su ASP.NET (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Flussi di lavoro ASP.NET, debug"
  - "ASP.NET, debug dei flussi di lavoro"
  - "debug dei flussi di lavoro, Flussi di lavoro ASP.NET"
  - "debug, Flussi di lavoro ASP.NET"
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: eseguire il debug di flussi di lavoro basati su ASP.NET (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] basate su [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che fanno riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.  
  
 È possibile eseguire il debug di flussi di lavoro legacy avviati in ASP.NET o flussi di lavoro legacy pubblicati come servizio Web connettendoli al processo nel quale è ospitato il flusso di lavoro.  
  
### Per eseguire il debug del flusso di lavoro basato su ASP.NET  
  
1.  Abilitare l'esecuzione del debug per l'applicazione ASP.NET impostando **debug \= true** nel file web.config.  
  
2.  Impostare la libreria del flusso di lavoro come progetto di avvio e impostare i punti di interruzione sul flusso di lavoro.  
  
3.  Immettere l’URL della pagina Web predefinita nella casella di testo delle proprietà del progetto di flusso di lavoro **Debug** opzione **Avvia browser con URL esterno**.  
  
4.  Scegliere **Connetti a processo** dal menu **Debug**.  
  
5.  Selezionare il processo per allegare dall'elenco **Processi disponibili**.  
  
     Allegare al processo w3wp.exe, webdev.webserver o aspnet\_wp che ospita il flusso di lavoro.  
  
6.  Scegliere **Seleziona** accanto alla casella di testo **Allega a**.  
  
     La finestra di dialogo **Seleziona tipo di codice** verrà visualizzata.  
  
7.  Selezionare **Esegui il debug di questi tipi di codice** e selezionare **Flusso di lavoro**.  
  
8.  Scegliere **OK**.  
  
9. Scegliere **Allega**.  
  
10. Aprire la pagina Web predefinita in un browser e avviare il flusso di lavoro.  
  
## Vedere anche  
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation \(legacy\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Procedura: impostare punti di interruzione nei flussi di lavoro \(legacy\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)