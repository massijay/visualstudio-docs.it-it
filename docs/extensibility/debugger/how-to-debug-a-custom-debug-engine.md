---
title: "Procedura: Eseguire il Debug di un motore di Debug personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, il debug"
  - "debug [debug SDK], motori di debug personalizzati"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Procedura: Eseguire il Debug di un motore di Debug personalizzato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un tipo di progetto avvia il modulo \(DE\) di debug dal metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> .  Ciò significa che il DE viene avviato sotto il controllo dell'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che controlla il tipo di progetto.  Tuttavia, tale istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] impossibile eseguire il debug di DE.  Che segue vengono illustrate le operazioni necessarie per consentire il debug personalizzate DE.  
  
> [!NOTE]
>  :     “Eseguendo il debug nella routine del modulo di debug personalizzato„, è necessario attendere il DE per iniziare prima di poter connettere.  Se si inserisce una finestra di messaggio da parte superiore di DE visualizzato quando il DE viene avviata, è possibile associare a quel punto quindi deselezionare la finestra di messaggio continuare.  In questo modo, è possibile rilevare qualsiasi DE events.  
  
> [!WARNING]
>  È necessario che il debug remoto prima di tentare le procedure riportate di seguito.  Per informazioni dettagliate, vedere [Debug remoto](../../debugger/remote-debugging.md).  
  
### Eseguire il debug di un modulo di debug personalizzato  
  
1.  Msvsmon.exe iniziale, Remote Debugging Monitor.  
  
2.  Dal menu di **strumenti** in msvsmon.exe, **opzioni** selezionare per aprire la finestra di dialogo di **opzioni** .  
  
3.  Selezionare “l'opzione di nessuna autenticazione„ e fare clic **OK**.  
  
4.  Avviare un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto di DE personalizzate.  
  
5.  Avviare una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e aprire il progetto personalizzato che avvia il DE \(per lo sviluppo, si tratta in genere nell'hive funzioni del Registro di sistema che vengono configurati quando il VSIP viene installato\).  
  
6.  Nella seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], caricare un file di origine dal progetto personalizzato e avviare il programma da sottoporre a debug.  Attendere alcuni minuti per consentire il DE il caricamento, o attendere a un punto di interruzione viene premuto.  
  
7.  Prima di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(con il progetto DE\), **Connettersi da elaborare** scegliere dal menu Debug.  
  
8.  Nella finestra di dialogo di **Connettersi da elaborare** , modificare **trasporto** a **Remoto \(solo nativo senza autenticazione\)**.  
  
9. Modificare **qualificatore** al nome del computer \(nota: esiste una cronologia delle voci, pertanto è necessario digitare solo una volta in questo nome\).  
  
10. Nell'elenco di **processi disponibili** , selezionare l'istanza di DE che esegue e fare clic sul pulsante di **Connessione** .  
  
11. Dopo che i simboli caricati in DE, impostare i punti di interruzione nel codice di DE.  
  
12. Ogni volta che si arresta quindi riavviare il processo di debug, ripetere i passaggi da 6 a 10.  
  
### Per eseguire il debug di un tipo di progetto personalizzato  
  
1.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iniziale nell'hive normali del Registro di sistema e carica il progetto del tipo di progetto \(in, il database di origine al tipo di progetto, non una creazione di istanze del tipo di progetto\).  
  
2.  Aprire le proprietà del progetto e passare alla pagina di **debug** .  Per il commando, digitare il percorso dell'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(per impostazione predefinita, viene *\[unità\]*\\Program Files\\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\Common7\\IDE \\ devenv.exe\).  
  
3.  Per **Argomenti passati dalla riga di comando**, tipo `/rootsuffix esp` per le funzioni hive del Registro di sistema \(creati quando il VSIP è stato installato\).  
  
4.  Scegliere **OK** per confermare le modifiche.  
  
5.  Avviare il tipo di progetto premendo F5.  Verrà avviata una seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  A questo punto, è possibile inserire punti di interruzione nel codice sorgente del tipo di progetto.  
  
7.  Nella seconda istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il caricamento o crea una nuova istanza del tipo di progetto.  Durante il caricamento o la creazione, i punti di interruzione possono essere raggiunti.  
  
8.  Eseguire il debug del tipo di progetto.  
  
9. Se si sceglie di eseguire il debug del processo di avviare un DE, è possibile eseguire la procedura “che si esegue il debug nella routine del modulo di debug personalizzato„ per connettersi al DE una volta avviato.  Ciò fornisce tre istanze dell'esecuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] : uno per l'origine del tipo di progetto, un secondo per il tipo di progetto per creare un'istanza e un terzo associato a DE.  
  
## Vedere anche  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)