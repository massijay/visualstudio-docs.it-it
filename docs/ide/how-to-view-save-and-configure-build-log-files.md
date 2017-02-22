---
title: "Procedura: visualizzare, salvare e configurare file di log di compilazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: visualizzare, salvare e configurare file di log di compilazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo aver compilato un progetto nell'IDE di Visual Studio, è possibile visualizzare le informazioni sulla compilazione nella finestra **Output**.  Utilizzando queste informazioni, è possibile, ad esempio, la risoluzione di un errore di compilazione.  Per i progetti C\+\+, è possibile visualizzare le stesse informazioni in un file txt creato e salvato automaticamente.  Per i progetti di codice gestito, è possibile copiare e incollare le informazioni dalla finestra **Output** in un file txt e salvare manualmente.  È inoltre possibile utilizzare l'ide di per specificare quali tipi di informazioni si desidera visualizzare su ogni compilazione.  
  
 Se si compila qualsiasi tipo di progetto utilizzando MSBuild, è possibile creare un file txt per salvare le informazioni sulla compilazione.  Per ulteriori informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### Per visualizzare il file di log di compilazione per un progetto c\+\+  
  
1.  In **Esplora risorse** in **Esplora file**, aprire il file seguente: … \\  \\Visual Studio *Versione*\\Projects\\*ProjectName**ProjectName*\\Debug\\*ProjectName*TXT  
  
### Per creare un file di log di compilazione per un progetto di codice gestito  
  
1.  Sulla barra del menu, scegliere **Build**, **Genera soluzione**.  
  
2.  Nella finestra **Output**, evidenziare le informazioni di compilazione e quindi copiarlo negli Appunti.  
  
3.  Aprire un editor di testo, come Blocco Note, incollare le informazioni nel file e quindi salvarlo.  
  
### Per modificare la quantità di informazioni incluse nel log di compilazione  
  
1.  Sulla barra dei menu, scegliere **Strumenti**, **Options**.  
  
2.  Nella pagina **Progetti e soluzioni**, selezionare la pagina **Compila ed esegui**.  
  
3.  Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild**, scegliere uno dei seguenti valori e quindi scegliere il pulsante **OK**.  
  
    |Livello di dettaglio|Descrizione|  
    |--------------------------|-----------------|  
    |Quiet|Visualizza un riepilogo di compilazione solo.|  
    |Minimal|Visualizza un riepilogo di compilazione ed errori, avvisi e messaggi suddivisi in categorie come estremamente importante.|  
    |Normal|Visualizza un riepilogo della compilazione; errori, avvisi e messaggi suddivisi in categorie come molto importanti; i passaggi principali della compilazione.  Si utilizzerà questo livello di dettaglio più di frequente.|  
    |Detailed|Visualizza un riepilogo della compilazione; errori, avvisi e messaggi suddivisi in categorie come molto importanti; tutti i passaggi di compilazione; e messaggi suddivise in categorie dall'importanza normale.|  
    |Diagnostic|Visualizza tutti i dati disponibili per la compilazione.  È possibile utilizzare questo livello di dettaglio per eseguire il debug dei problemi con gli script e l'altro di compilazione personalizzata problemi di compilazione.|  
  
     Per ulteriori informazioni, vedere [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    >  È necessario ricompilare il progetto affinché le modifiche diventino operative nella finestra **Output** \(tutti i progetti\) e il file di *ProjectName*\(TXT progetti C\+\+ solo\).  
  
## Vedere anche  
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilazione di applicazioni in Visual Studio](../ide/compiling-and-building-in-visual-studio.md)