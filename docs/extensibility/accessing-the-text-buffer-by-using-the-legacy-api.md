---
title: "Accesso ai Buffer di testo tramite l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - buffer di testo"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Accesso ai Buffer di testo tramite l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il testo è responsabile della gestione dei flussi di testo e la persistenza del file.  Sebbene il buffer possa leggere o scrivere altri formati, le comunicazioni comune con il buffer viene eseguita utilizzando Unicode.  Nell'API legacy, il buffer di testo possibile utilizzare un o un sistema di coordinate bidimensionale per identificare le posizioni dei caratteri nel buffer.  
  
## Sistemi di coordinate di Due\-Dimensione e uno  
 Una posizione della coordinata unidimensionale è basata su una posizione di carattere dal primo carattere nel buffer, ad esempio 147.  Utilizzare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> per accedere a una posizione unidimensionale nel buffer.  Un sistema di coordinate bidimensionale viene archiviato in base indice e in linea.  Ad esempio, un carattere nel buffer su 43, 5 sarebbe 43 in linea, cinque caratteri a destra del primo carattere della riga.  Si accede a una posizione bidimensionale nel buffer tramite l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> .  Sia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> che le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> vengono implementati dall'oggetto del buffer di testo \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\) e possono essere utilizzatialtro mediante `QueryInterface`.  Nel diagramma seguente viene illustrata questa e altre interfacce della chiave su <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Oggetto TextBuffer](~/docs/extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Oggetto del buffer di testo  
  
 Sebbene qualsiasi funzionamento del sistema di coordinate del buffer di testo, sia ottimizzata per utilizzare le coordinate bidimensionali.  Un sistema di coordinate unidimensionale possibile creare il sovraccarico delle prestazioni.  Pertanto, per utilizzare il sistema di coordinate bidimensionale quando possibile.  
  
 La responsabilità del buffer di testo secondo è la persistenza del file.  A tale scopo, implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> dell'oggetto del buffer di testo e funge da parte dell'oggetto dati del documento per gli elementi di progetto e altri componenti dell'ambiente coinvolti nella persistenza.  Per ulteriori informazioni, vedere [Apertura e salvataggio di elementi di progetto](../extensibility/internals/opening-and-saving-project-items.md).  
  
## Argomenti della sezione  
 [Modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Viene illustrato come modificare le impostazioni di visualizzazione utilizzando legacy API.  
  
 [Mediante la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato come utilizzare gestione del testo per monitorare le impostazioni globali.  
  
## Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)