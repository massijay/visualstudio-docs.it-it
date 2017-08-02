---
title: "Personalizzazione di Windows di codice tramite l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - finestre del codice"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Personalizzazione di Windows di codice tramite l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una finestra del codice è un oggetto finestra di documento che supporta uno o più visualizzazioni di testo. Esattamente le stesse funzionalità di una finestra del codice dipendono dal servizio di linguaggio associato. In modalità interfaccia a documenti multipli \(MDI\), la finestra del codice è la cornice figlio MDI.  
  
 Finestre del codice sono controllate da servizi di linguaggio e ogni servizio di linguaggio possa fornire un proprio gestore di finestra di codice. In questo modo il servizio di linguaggio aggiungere le proprie aree di controllo nella finestra di codice, ad esempio linee a zigzag, colorazione e altro ancora. Per ulteriori informazioni su come creare una finestra principale, vedere [Creazione di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Una finestra del codice è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto con una visualizzazione di testo e le aree di controllo ospitati nell'oggetto. Quando si crea la finestra del codice durante la creazione di istanze di base dell'editor, il servizio di linguaggio è possibile collegare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> alla finestra del codice, come è illustrato nella figura seguente.  
  
 ![Grafica CodeWindow](~/extensibility/media/vscodewindow.gif "vscodewindow")  
Finestra del codice  
  
 Il servizio di linguaggio implementa la gestione di finestre di codice ed è responsabile per la gestione delle aree di controllo, ad esempio una barra dei menu a discesa. Il finestra di codice chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodo durante l'inizializzazione di finestra di codice. Quando viene effettuata la chiamata, il servizio di linguaggio è possibile aggiungere una barra dei menu a discesa o una barra \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) alla finestra del codice.  
  
## Contenuto della sezione  
 `Customizing Code Windows by Using the Legacy API`  
 Viene illustrato come personalizzare le finestre di codice tramite l'API legacy.  
  
 [Procedura: ospitare un Editor in un altro Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Viene illustrato come ospitare un secondo revisore all'interno di una finestra dell'editor.  
  
 [Procedura: generare eventi quando l'Editor non è attivo](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Viene illustrato come connettere una visualizzazione del documento a un oggetto dati di documento.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Creazione di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)