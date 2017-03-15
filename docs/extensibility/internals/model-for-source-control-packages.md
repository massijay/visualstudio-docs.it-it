---
title: "Modello per i pacchetti di controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo [Visual Studio SDK], modello di origine"
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Modello per i pacchetti di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il modello seguente rappresenta un esempio di implementazione di controllo del codice sorgente.  Nel modello, le interfacce che è necessario implementare i servizi dell'ambiente che è necessario chiamare.  Come tutti i servizi, effettivamente chiama i metodi di interfaccia particolare ottenuto dal servizio.  I nomi delle classi sono identificati per semplificare osservare come il controllo del codice sorgente viene eseguito.  
  
 ![Esempi SCC&#95;TUP](../../extensibility/internals/media/scc_tup.png "SCC\_TUP")  
Progetto di controllo del codice sorgente di esempio  
  
## Interfacce  
 È possibile distribuire il controllo del codice sorgente per i nuovi tipi di progetto in Visual Studio utilizzando l'elenco delle interfacce illustrate nella tabella seguente.  
  
|Interfaccia|Utilizzare|  
|-----------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato dai progetti e gli editor prima di salvare o modificare i file \(modificati.  Questa interfaccia è accessibile tramite il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti richiedere l'autorizzazione per aggiungere, rimuovere, o rinominare un file o una directory.  Questa interfaccia viene chiamata dai progetti notificare all'ambiente quando un approvato aggiungere, rimuovere, rinominare o l'azione è completo.  È possibile accedere tramite il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementata da qualsiasi entità che effettua la registrazione per essere passate ai progetti aggiunti, rinominare, o rimuovere un file o una directory.  Per registrarsi per la notifica di eventi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>di chiamata.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chiamato dai progetti registrati con il pacchetto del controllo del codice sorgente e ottenere informazioni sullo stato del controllo del codice sorgente.  Questa interfaccia è accessibile tramite il servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Viene implementata dal progetto rispondere alle richieste di informazioni del controllo del codice sorgente su file e ottenere le impostazioni controllo del codice sorgente necessarie per il file di progetto.|  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Supporto di controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)