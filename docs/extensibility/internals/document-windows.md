---
title: "Finestre di documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, finestre di documento"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Finestre di documento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Visual Studio, un *finestra del documento* è una finestra cornice figlio che è associata a una finestra di interfaccia a documenti multipli \(MDI\). Finestre di documento vengono generalmente utilizzate per la visualizzazione e la modifica del codice sorgente o di testo, ma che possono ospitare anche altri tipi di funzionalità. Finestre di documento:  
  
-   Possono essere organizzati in gruppi di scheda separata orizzontale o verticale del padre MDI in modo che sia possono visualizzare più file contemporaneamente.  
  
-   Può essere ancorata in qualsiasi ordine del padre MDI.  
  
-   Possono essere spostate liberamente.  
  
-   Sono collegate in ordine di tabulazione ad altre finestre MDI.  
  
 I comandi per il raggruppamento, ancorate e mobili sono reperibili nel menu di scelta rapida per una scheda della finestra documento.  
  
 Per ulteriori informazioni sul comportamento di finestra in Visual Studio, vedere [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## Implementazione della finestra documento  
 Finestre di documento vengono create implementando un editor. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia consente di creare finestre di documento come parte di un'istanza di un editor. Per altre informazioni, vedere [Interfacce legacy nell'Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Per fornire all'indietro e inoltrare i punti di navigazione in una finestra, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaccia. L'editor di testo utilizza degli indicatori di testo per identificare i punti di navigazione nel documento.  
  
## La tabella del documento in esecuzione  
 L'IDE utilizza la tabella documento in esecuzione \(RDT\) per tenere traccia dello stato di ogni finestra del documento. Il RDT è il meccanismo attraverso il documento windows viene visualizzata una notifica degli eventi, ad esempio quando una soluzione è chiusa o quando un file è stato modificato. Per altre informazioni, vedere [Tabella Document in esecuzione](../../extensibility/internals/running-document-table.md).  
  
## Vedere anche  
 [Documento caricamento ritardato](../../extensibility/internals/delayed-document-loading.md)