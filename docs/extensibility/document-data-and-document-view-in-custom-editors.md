---
title: "Dati del documento e visualizzazione di documento nell&#39;editor personalizzati | Microsoft Docs"
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
  - "editor [Visual Studio SDK], personalizzato - i dati del documento e visualizzazione del documento"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Dati del documento e visualizzazione di documento nell&#39;editor personalizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un editor personalizzato è costituito da due parti: un oggetto dati di documento e un oggetto di visualizzazione documento. Come suggeriscono i nomi, l'oggetto dati documento rappresenta i dati di testo da visualizzare e l'oggetto visualizzazione documento \(o "view"\) rappresenta una o più finestre in cui visualizzare l'oggetto dati di documento.  
  
## Oggetto dati documento  
 Un oggetto dati di documento è una rappresentazione di dati di testo nel buffer di testo. È un oggetto COM che archivia il testo di documento e altre informazioni, gestisce la persistenza di documento e consente più visualizzazioni dei dati. Per altre informazioni, vedere  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> e [Finestre di documento](../extensibility/internals/document-windows.md).  
  
 Editor personalizzati e finestre di progettazione può scegliere di utilizzare il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto o i propri buffer personalizzato.<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più viste e fornisce interfacce eventi che consentono di gestire più viste.  
  
## Oggetto visualizzazione documento  
 Una finestra che Visualizza codice e altro testo è noto come un documento o una vista. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui è visualizzato in una singola finestra o una vista più, in cui viene visualizzato il testo in più di una finestra. La scelta dipende dall'applicazione. Ad esempio, se è necessario modificare side\-by\-side, selezionare Visualizza più. Ogni visualizzazione è associata a una voce in integrato dell'ambiente di sviluppo \(IDE\) in esecuzione tabella document \(RDT\). Windows vista appartengono a un progetto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.  
  
 Se l'editor supporta più viste di un oggetto dati di documento, quindi i dati di documento e gli oggetti di visualizzazione documento devono essere separati. In caso contrario, essi possono essere raggruppate. Per altre informazioni, vedere [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md).  
  
 L'IDE notifica viste sugli eventi \(ad esempio, quando una soluzione contenente un documento viene chiuso\) mediante la corrispondenza tra un elemento identificatore \(ID\) per ogni voce della tabella document in esecuzione. Per altre informazioni in merito, vedere [Tabella Document in esecuzione](../extensibility/internals/running-document-table.md).  
  
 Sono disponibili due opzioni per la creazione di una visualizzazione per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la vista è ospitata in una finestra con un controllo ActiveX o un oggetto dati di documento. Il secondo è il modello di incorporamento semplificato, in cui la vista è ospitata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> viene implementato per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [Attivazione sul posto](../misc/in-place-activation.md). Per informazioni sul modello di incorporamento semplificato, vedere [Incorporamento semplificato](../extensibility/simplified-embedding.md).  
  
## Vedere anche  
 [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md)   
 [Incorporamento semplificato](../extensibility/simplified-embedding.md)   
 [Procedura: collegare visualizzazioni per tenere traccia dei dati](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestione dei documenti blocco titolare](../extensibility/document-lock-holder-management.md)   
 [Singole e multi\-scheda viste](../extensibility/single-and-multi-tab-views.md)   
 [Salvare un documento Standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenza e la tabella del documento in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinazione di un File in un progetto che verrà aperto l'Editor](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Factory editor](../extensibility/editor-factories.md)