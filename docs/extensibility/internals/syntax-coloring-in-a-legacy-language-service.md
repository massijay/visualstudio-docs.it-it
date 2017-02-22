---
title: "In un servizio di linguaggio Legacy colorazione della sintassi | Microsoft Docs"
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
  - "colorazione sintassi"
  - "servizi di linguaggio, la colorazione della sintassi"
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# In un servizio di linguaggio Legacy colorazione della sintassi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza un servizio di colorazione per identificare gli elementi del linguaggio e visualizzare con colori specificati in un editor.  
  
## modello di Colorizer  
 Il servizio di linguaggio implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> , che viene quindi utilizzata dagli editor.  Questa implementazione è un oggetto separato dal servizio di linguaggio, come illustrato nella figura seguente.  
  
 ![Rappresentazione grafica dell'applicazione dei colori SVC](../../extensibility/internals/media/figlgsvccolorizer.png "FigLgSvcColorizer")  
Modello semplice di colorizer  
  
> [!NOTE]
>  Il servizio di colorazione della sintassi dal meccanismo di generale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per assegnare un colore al testo.  Per ulteriori informazioni sul colore che supporta il meccanismo di generale [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , vedere [Utilizzando i tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
 Oltre a colorizer, il servizio di linguaggio possibile fornire gli elementi colorabili personalizzati utilizzati dall'editor comunicando vocalmente che forniscono gli elementi colorabili personalizzati.  Questo è possibile implementando l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> lo stesso oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  Restituisce il numero di elementi colorabili personalizzati quando l'editor chiama il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e restituisce un singolo elemento il colore personalizzato quando l'editor chiama il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
 il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> restituisce un oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  Se valori di bit o di colore attivato di supportare del servizio di linguaggio i 24, deve implementare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> lo stesso oggetto dell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  
  
## come un VSPackage utilizza un servizio di linguaggio Colorizer  
  
1.  Il package VS deve ottenere il servizio di linguaggio appropriato, che richiede al servizio di linguaggio VSPackage di eseguire le operazioni seguenti:  
  
    1.  Utilizzare un oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per ottenere il testo per essere coloratoe.  
  
         Il testo in genere visualizzato utilizzando un oggetto che implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
    2.  Ottenere il servizio di linguaggio eseguire una query sul provider di servizi del package VS per il servizio di linguaggio GUID.  I servizi di linguaggio sono identificati nel Registro di sistema dall'estensione di file.  
  
    3.  Associare il servizio di linguaggio con <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .  
  
2.  Il package VS possibile ottenere e utilizzare l'oggetto del colorizer come segue:  
  
    > [!NOTE]
    >  Package VS che utilizza l'editor principale non deve ottenere gli oggetti del colorizer di un servizio di linguaggio in modo esplicito.  Una volta creata un'istanza dell'editor principale ottiene un servizio di linguaggio appropriato, esegue tutte le attività di colorazione illustrate in questo argomento.  
  
    1.  Ottenere l'oggetto del colorizer del servizio di linguaggio, che implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`e le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> , chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> l'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> del servizio di linguaggio.  
  
    2.  Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per ottenere informazioni di colorizer per un intervallo specifico di testo.  
  
         l'entity\_M:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine\(System.Int32, System.Int32, System.IntPtr, System.Int32, System.UInt32\[\]\)  I valori sono indici in un elenco di elementi che il colore è l'elenco di elementi il colore predefinito gestito dall'editor principale o un elenco di elementi il colore personalizzato gestito dal servizio di linguaggio stesso.  
  
    3.  Utilizzare le informazioni di colorazione restituite dal metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per visualizzare il testo selezionato.  
  
> [!NOTE]
>  Oltre a utilizzare un colorizer del servizio di linguaggio, un VSPackage anche possibile utilizzare il meccanismo di utilizzo generale di colorazione del testo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  per ulteriori informazioni su questo meccanismo, vedere [Utilizzando i tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md).  
  
## Argomenti della sezione  
 [Implementazione di colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)  
 Viene illustrato come un editor accede alla colorazione della sintassi di un servizio di linguaggio e il servizio di linguaggio deve implementare per supportare la colorazione della sintassi.  
  
 [Procedura: utilizzare gli elementi di colori predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Viene illustrato come utilizzare gli elementi colorabili incorporati dal servizio di linguaggio.  
  
 [Elementi di colori personalizzati](../../extensibility/internals/custom-colorable-items.md)  
 Viene illustrato come implementare gli elementi colorabili personalizzati.  
  
## Vedere anche  
 [Utilizzando i tipi di carattere e colori](../../extensibility/using-fonts-and-colors.md)