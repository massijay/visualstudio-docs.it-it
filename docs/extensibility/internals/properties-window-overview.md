---
title: "Panoramica della finestra proprietà | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
Il **proprietà** finestra consente di visualizzare le proprietà per gli oggetti selezionati i due tipi principali di windows disponibile nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Questi due tipi di windows sono:  
  
-   Finestre degli strumenti, ad esempio browser Esplora soluzioni, Visualizzazione classi e oggetti  
  
-   Finestre di documento che contiene tali editor e finestre di progettazione come finestra di progettazione di form, editor XML, editor HTML  
  
## <a name="using-the-properties-window"></a>Utilizzando la finestra proprietà  
 Il **proprietà** finestra Visualizza le proprietà di uno o più elementi selezionati. Se vengono selezionati più elementi, viene visualizzato l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.  
  
 Gli eventi correlati a un oggetto selezionato in una finestra di progettazione form o un editor HTML utilizzando i metadati di COM+ sono visualizzati nel **proprietà** finestra. Ad esempio, è possibile selezionare un pulsante e visualizzare gli eventi associati, ad esempio un `OnClick` evento, che può essere collegato a tale pulsante.  
  
 Gli eventi visualizzati nel **proprietà** finestra vengono utilizzati principalmente con gli oggetti associati al codice. Se si sta modificando un formato di file che non hanno nulla a che fare con il codice, non si desidera disporre di tutti gli eventi. Gli eventi vengono visualizzati solo nel **proprietà** finestra quando si verifica un'associazione tra l'esecuzione di codice e alcuni eventi associati a oggetti specifici. Un esempio di questo sarebbe code-behind di un oggetto selezionato che viene eseguito quando viene attivato l'oggetto.  
  
 Nella tabella seguente elenca le interfacce principali utilizzate dal **proprietà** finestra.  
  
|Nome dell'interfaccia.|Descrizione|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie per il **proprietà** finestra ed esegue il mapping di ogni proprietà per una categoria.|  
|[Interfaccia IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Espone metodi e proprietà per la programmazione di strumenti e altre applicazioni che supportano l'automazione di un oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornisce i pulsanti con puntini di sospensione (...) denominati *generatori* che aprire finestre di dialogo modali implementate dall'oggetto stesso. Utilizzato quando si digita un valore non facilmente dall'utente in un campo di testo. Ad esempio, potrebbe essere consente di aprire un selettore di colore che determina il valore RGB per l'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornisce l'accesso agli oggetti utilizzati per aggiornare le informazioni visualizzate nel **proprietà** finestra. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>è implementato dal package VS per ogni finestra che contiene oggetti selezionabili con le proprietà correlate da visualizzare.</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di oggetto, ad esempio metodi di interfaccia e i campi di una struttura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente di VS per ricevere la notifica degli eventi di selezione e recuperare le informazioni sulla gerarchia del progetto corrente, elemento, il valore di elemento e il contesto di comando dell'interfaccia utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilizzato per fornire nomi localizzati su alcune proprietà visualizzate di **proprietà** finestra.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a VSPackage registrato di modifiche alla selezione corrente, un valore dell'elemento o un contesto dell'interfaccia utente del comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica di una modifica della selezione corrente nell'ambiente e fornisce accesso alle informazioni di gerarchia e articoli riguardanti la nuova selezione.|  
  
 Per ulteriori informazioni su `IDispatch`, consultare la MSDN library.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)   
 [Interfacce e i campi di proprietà finestra](../../extensibility/internals/properties-window-fields-and-interfaces.md)
