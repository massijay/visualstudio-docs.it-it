---
title: "Colorazione in editor personalizzati della sintassi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], personalizzato - colorazione della sintassi"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Colorazione in editor personalizzati della sintassi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli editor dell'ambiente SDK di Visual Studio, compresi l'editor principale, utilizzano servizi di linguaggio per identificare gli elementi sintattici specifici e visualizzare con colori specificati per una specifica visualizzazione del documento.  
  
## requisiti di colorazione  
 tutti gli editor che implementano il colorizer di un servizio di linguaggio devono:  
  
1.  Utilizzare un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> per gestire il testo i colori e un oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per fornire una visualizzazione del documento di testo.  
  
2.  Ottenere un'interfaccia a un servizio di linguaggio particolare eseguire una query sul provider di servizi del package VS che utilizza il GUID di identificazione del servizio di.  
  
3.  Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> dell'oggetto che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  Questo metodo associa il servizio di linguaggio tramite l'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> che il package VS utilizza per gestire il testo che deve essere coloratoe.  
  
## Svuotare l'utilizzo dell'editor di Colorizer di un servizio di linguaggio  
 Quando un servizio di linguaggio con un colorizer viene ottenuto da un'istanza dell'editor principale, l'analisi e il rendering del testo da colorizer di un servizio di linguaggio si verifica automaticamente senza richiedere l'intervento nuovo sulla parte.  
  
 L'ide transparent:  
  
-   Chiama il colorizer in base alle necessità per analizzare e analizzare il testo quando viene aggiunto o modificato nell'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.  
  
-   Verificare che la visualizzazione fornita dalla visualizzazione del documento fornite dall'implementazione di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> viene aggiornata e aggiornata utilizzando le informazioni restituite dal colorizer.  
  
## Utilizzo non fondamentale dell'editor di Colorizer di un servizio di linguaggio  
 Le istanze non fondamentali dell'editor possono inoltre utilizzare il servizio di colorazione della sintassi di un servizio di linguaggio, ma devono esplicitamente recuperare e applicare il colorizer del servizio e aggiornare lo corrispondente documento è visualizzazioni.  
  
 Per eseguire questa operazione richiede un editor non fondamentale:  
  
1.  Ottenere l'oggetto del colorizer di un servizio di linguaggio \(che implementa `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>\).  Il package VS questa operazione chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> sull'interfaccia del servizio di linguaggio.  
  
2.  Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> per richiedere che un intervallo specifico di testo sia colorata.  
  
     Il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> restituisce una matrice di valori, uno per ogni lettera intervallo di testo che si colorato.  Identifica inoltre l'intervallo di testo come determinato tipo di elemento il colore, ad esempio un commento, una parola chiave, o un tipo di dati.  
  
3.  Use the colorization information returned by <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> to repaint and display its text.  
  
> [!NOTE]
>  Oltre a utilizzare il colorizer di un servizio di linguaggio, un VSPackage possibile scegliere di utilizzare il meccanismo di utilizzo generale di testo\-colorazione dell'ambiente SDK di Visual Studio.  per ulteriori informazioni su questo meccanismo, vedere [Utilizzando i tipi di carattere e colori](../extensibility/using-fonts-and-colors.md).  
  
## Vedere anche  
 [In un servizio di linguaggio Legacy colorazione della sintassi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../extensibility/internals/implementing-syntax-coloring.md)   
 [Procedura: utilizzare gli elementi di colori predefiniti](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Elementi di colori personalizzati](../extensibility/internals/custom-colorable-items.md)