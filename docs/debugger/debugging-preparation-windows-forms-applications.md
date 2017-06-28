---
title: "Preparazione al debug: applicazioni Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "debug [C#], Windows (applicazioni)"
  - "debug [J#], Windows (applicazioni)"
  - "debug [Visual Basic], Windows (applicazioni)"
  - "debug [Visual Studio], Windows (applicazioni)"
  - "debug di applicazioni Windows"
  - "Windows (applicazioni), debug"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Preparazione al debug: applicazioni Windows Form
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modello di progetto Windows Forms consente di creare un'applicazione Windows Forms.  Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice.  Per ulteriori informazioni, vedere [Creating a Windows Application Project](http://msdn.microsoft.com/it-it/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio.  Se necessario, è possibile modificare tali impostazioni.  Queste impostazioni possono essere modificate nella finestra di dialogo **Pagine delle proprietà di \<nome progetto\>** \(**Progetto** in Visual Basic\).  
  
 Per ulteriori informazioni, vedere [Impostazioni consigliate delle proprietà](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Nella tabella riportata di seguito è indicata un'impostazione consigliata aggiuntiva per le proprietà.  
  
### Proprietà di configurazione disponibili nella scheda Debug  
  
|**Nome proprietà**|**Impostazione**|  
|------------------------|----------------------|  
|**Azione di avvio**|-   Nella maggior parte dei casi, impostare questa proprietà su **Avvia progetto**.  Impostare questa proprietà su **Avvia programma esterno** se si desidera avviare un altro eseguibile quando si inizia il debug \(in genere per il debug di DLL\).|  
  
 È possibile eseguire il debug di applicazioni Windows Form dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oppure stabilendo una connessione a un'applicazione già in esecuzione.  Per ulteriori informazioni sulla connessione, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### Per eseguire il debug di un'applicazione Windows Form in C\#, F\# o Visual Basic  
  
1.  Aprire il progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Creare i punti di interruzione necessari.  
  
     Poiché le applicazioni Windows Form sono guidate da eventi, i punti di interruzione dovranno essere inseriti nel codice del gestore eventi o nei metodi chiamati dal codice del gestore eventi.  Alcuni eventi tipici in cui impostare i punti di interruzione sono:  
  
    1.  Eventi associati a un controllo, ad esempio Click, Enter e così via  
  
    2.  Eventi associati all'avvio e alla chiusura dell'applicazione, ad esempio Load, Activated e così via  
  
    3.  Eventi di convalida e relativi allo stato attivo.  
  
     Per ulteriori informazioni, vedere [Creating Event Handlers in Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  Scegliere **Avvia** dal menu **Debug**.  
  
4.  Eseguire il debug utilizzando le tecniche descritte in [Nozioni di base sul debugger](../debugger/debugger-basics.md).  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Impostazioni di progetto per le configurazioni di debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Form](../Topic/Windows%20Forms.md)