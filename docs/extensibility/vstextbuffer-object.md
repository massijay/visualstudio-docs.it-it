---
title: "Oggetto VSTextBuffer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextBuffer"
helpviewer_keywords: 
  - "Oggetto VSTextBuffer, riferimento"
  - "visualizzazioni [Visual Studio SDK], oggetto VSTextBuffer"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Oggetto VSTextBuffer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'oggetto TextBuffer rappresenta un flusso di testo Unicode, che è generalmente associato a un file. Oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto può essere utilizzato all'esterno del contesto dell'editor di componenti di base, come nel caso di una procedura guidata.  
  
 Nella tabella seguente mostra le interfacce di `VSTextBuffer`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Interfaccia OLE standard. Utilizzata principalmente per la gestione del buffer di annullamento\/ripristino.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Interfaccia OLE standard.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composti \(vale a dire le azioni che vengono raggruppate in un'unità di annullamento\/ripristino singolo\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Consente la persistenza dei dati del documento gestiti da buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti clienti.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Utilizzato per la ricerca di un buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Consente di lettura e scrittura funzionalità usando le coordinate bidimensionale. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Consente di lettura e scrittura funzionalità usando le coordinate unidimensionale. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accesso sequenza, orientato al flusso di testo nel buffer rapido.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome o moniker, del buffer. È possibile archiviare dati casuali nel buffer con questa interfaccia mediante la creazione di un GUID e l'uso come chiave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta punti di connessione per gli eventi.|  
  
## Note  
 Il `VSTextBuffer` trova in genere da un `QueryInterface` chiamare `IVsTextBuffer`. Per ulteriori informazioni, vedere [textBuffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/it-it/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)