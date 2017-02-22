---
title: "Nell&#39;Editor di componenti di base | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - editor principale"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Nell&#39;Editor di componenti di base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor di base di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è un set di diversi componenti che consentono di modificare ed eseguire una query sulle informazioni di testo.  Se è stato personalizzato editor principale tramite le API legacy, è possibile continuare a utilizzare queste personalizzazioni, che saranno interessate dagli adattatori dell'editor.  Si consiglia, tuttavia, che si adatta le personalizzazioni al nuovo editor API.  
  
 Le aree seguenti sono alcuni aspetti dell'editor principale:  
  
-   buffer di testo  
  
-   Visualizzazione di testo  
  
-   Finestra del codice  
  
-   marcatori di testo  
  
-   Amministratore del testo  
  
-   integrazione con i servizi di linguaggio  
  
## In questa sezione  
 [Creazione di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come utilizzare l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance\(System.UInt32, System.String, System.String, Microsoft.VisualStudio.Shell.Interop.IVsHierarchy, System.UInt32, System.IntPtr, System.IntPtr@, System.IntPtr@, System.String@, System.Guid@, System.Int32@\) per creare un'istanza dell'editor principale.  
  
 [Accesso ai Buffer di testo tramite l'API Legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Viene descritto il ruolo del buffer di testo nell'editor principale, tra i sistemi associati utilizzati per accedere al buffer e viene fornito un elenco delle interfacce implementate dall'oggetto del buffer di testo, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventi nel Buffer di testo nell'API Legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Viene fornito un elenco delle interfacce utilizzate per la notifica degli eventi del buffer di testo.  
  
 [Procedura: registrare gli eventi del Buffer di testo con l'API Legacy](../Topic/How%20to:%20Register%20for%20Text%20Buffer%20Events%20with%20the%20Legacy%20API.md)  
 Viene descritto come visualizzeranno solo gli eventi del buffer di testo.  
  
 [Mediante la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato come amministratore di testo viene utilizzato per condividere le informazioni globali di preferenza con i componenti principali dell'editor e come ricevere la notifica di eventi di gestione del testo.  
  
 [Accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Viene descritto il ruolo della visualizzazione di testo nell'editor principale ed elenca le interfacce implementate dall'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [Personalizzazione di Windows di codice tramite l'API Legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Vengono fornite informazioni su come una finestra del codice viene utilizzata per racchiudere la visualizzazione di testo, viene illustrato come gestione finestre del codice viene utilizzato per fornire le decorazioni alla finestra del codice e fornisce la notifica di nuove visualizzazioni.  
  
 [Modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come definire le impostazioni di visualizzazione e come rimuovere le impostazioni si forza.  
  
 [Servizi per linguaggi e l'Editor di componenti di base](../extensibility/language-services-and-the-core-editor.md)  
 Viene descritta la creazione di istanze di un servizio di linguaggio le decorazioni del codice.  
  
## Sezioni correlate  
 [Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Vengono fornite istruzioni dettagliate su come avviare l'editor principale dal codice gestito.  
  
 [Barra dei menu a discesa](../extensibility/drop-down-bar.md)  
 Viene illustrato come la barra a discesa nella finestra del codice e vengono descritte le interfacce utilizzate quando si distribuisce una barra a discesa.  
  
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Vengono illustrati il concetto dei marcatori di testo e come vengono utilizzati nell'editor principale ed elenca le interfacce utilizzate per accedere e gestire i marcatori di testo.  
  
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un marcatore di testo e come aggiungere un comando personalizzato a un menu di scelta rapida.  
  
 [Procedura: creare indicatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un marcatore di testo personalizzato e come fornire il tipo del marcatore come servizio.