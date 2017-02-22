---
title: "Icona controllo (origine controllo VSPackage) | Microsoft Docs"
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
  - "glifi, pacchetti di controllo di origine"
  - "pacchetti di controllo di origine, glifi"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Icona controllo (origine controllo VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La parte dell'integrazione approfondita disponibile nel controllo del codice sorgente Vspackage è la possibilità di visualizzare i propri icone per indicare lo stato degli elementi nel controllo del codice sorgente.  
  
## Livelli di controllo del glifo  
 Un'icona di stato viene visualizzata un'icona che indica lo stato corrente di un elemento quando viene visualizzato, ad esempio in **Esplora soluzioni** o in **Visualizzazione classi**.  Un controllo del codice sorgente VSPackage possibile utilizzare due livelli di controllo del glifo.  È possibile limitare la scelta dei glifi a un insieme predefinito di glifi forniti dall'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , o possibile definire un set personalizzato dei glifi da visualizzare.  
  
### Set predefinito di glifi  
 Per determinare le icone di stato associati a un elemento in **Esplora soluzioni**, un progetto il glifo di stato dal controllo del codice sorgente utilizzando dell'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph\(System.Int32, System.String\[\], Microsoft.VisualStudio.Shell.Interop.VsStateIcon\[\], System.UInt32\[\]\).  Un controllo del codice sorgente VSPackage possibile decidere di mantenere la scelta dei glifi limitati ai glifi predefiniti forniti dall'IDE.  In questo caso, il package VS il passaggio di una matrice di valori che rappresentano le enumerazioni di glifo definite in vsshell.idl.  Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Si tratta di un insieme predefinito di glifi impostati dall'IDE, ad esempio un lucchetto per il glifo “archiviato e un segno di spunta come “ha avuto„ il glifo.  
  
### Personalizzato insieme di glifi  
 Un controllo del codice sorgente VSPackage possibile utilizzare i propri glifi per “un aspetto univoco e proprio„ quando viene installato.  Quando un nuovo controllo del codice sorgente VSPackage è attivo, deve poter iniziare utilizzando i propri glifi anche se un controllo del codice sorgente precedente VSPackage viene caricato ma inattivo.  In questa modalità, il controllo del codice sorgente VSPackage ancora possibile utilizzare le icone esistenti per gestire un essere coerente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se scegliere.  
  
 Il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> supporta un'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, che il package VS possibile implementare e che saranno richiesto dall'IDE.  Quando l'ide esegue una richiesta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a sua volta tenterà di ottenere questa interfaccia dal controllo del codice sorgente attualmente registrato VSPackage.  Se l'interfaccia esiste nel package VS registrato, la richiesta dell'IDE per i glifi personalizzati ha esito positivo; in caso contrario, l'ide di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza il relativo set predefinito di glifi.  
  
 Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> viene utilizzato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per ottenere un elenco di immagini che mostrano i diversi stati del controllo del codice sorgente.  Il controllo del codice sorgente VSPackage restituisce all'handle all'elenco di immagini per i glifi personalizzati.  L'ide esegue una copia dell'elenco immagini in questa fase e utilizzarla in un secondo momento per selezionare i glifi da visualizzare.  Se la nuova interfaccia non è supportata o il metodo di `IVsSccGlyphs::GetCustomGlyphList` restituisce E\_NOTIMPL, quindi l'ide ottiene i glifi dall'elenco predefinito dei glifi forniti da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>