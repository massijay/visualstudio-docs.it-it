---
title: "Interfacce e i campi di propriet&#224; finestra | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfacce, campi e proprietà finestra"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfacce e i campi di propriet&#224; finestra
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il modello per la selezione per determinare quale informazioni visualizzate nella finestra di **Proprietà** è basato sulla finestra che ha lo stato attivo nell'IDE.  Ogni finestra e l'oggetto all'interno della finestra selezionata, possono disporre dell'oggetto di contesto di selezione inserito al contesto globale di selezione.  L'ambiente aggiorna il contesto globale di selezione con i valori contenuti in una struttura della finestra quando tale finestra ha lo stato attivo.  Quando le modifiche dello stato attivo, quindi esegue il contesto di selezione.  
  
## Selezione di rilevamento nell'IDE  
 La struttura della finestra o del sito, di proprietà dall'IDE di, ha un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.  Nei passaggi seguenti viene illustrato come una modifica in una selezione, causato dall'utente che modifica lo stato attivo su un'altra finestra aperta o seleziona un elemento di progetto diverso in **Esplora soluzioni**, viene distribuita per modificare il contenuto visualizzato nella finestra di **Proprietà** .  
  
1.  L'oggetto creato dal package VS che viene situato nella finestra selezionata chiama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> per essere chiamata <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>di <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> .  
  
2.  Il contenitore di selezione, se dalla finestra selezionata, crea il proprio oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  When the selection changes, the VSPackage calls <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> to notify any listeners in the environment, including the **Properties** window, of the change.  Fornisce inoltre l'accesso alla gerarchia e l'elemento correlate alla nuova selezione.  
  
3.  Calling <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> and passing it the selected hierarchy items in the `VSHPROPID_BrowseObject` parameter populates the <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> object.  
  
4.  Un oggetto derivato da [IDispatch Interface](http://msdn.microsoft.com/it-it/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) viene restituito per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> per l'elemento richiesto e l'ambiente ne eseguirà il wrapping in <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(vedere il passaggio successivo\).  Se la chiamata ha esito negativo, l'ambiente viene creata una seconda chiamata a `IVsHierarchy::GetProperty`, passando il contenitore <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> di selezione che l'elemento o gli elementi di struttura fornisce.  
  
     Il progetto VSPackage non crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché la finestra ambiente\-fornita package VS che la implementa \(ad esempio, **Esplora soluzioni**\) crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> al nome.  
  
5.  L'ambiente richiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per ottenere gli oggetti basati sull'interfaccia di `IDispatch` compilare la finestra di **Proprietà** .  
  
 Quando un valore nella finestra di **Proprietà** viene modificato, utilizzare `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` di package VS per segnalare la modifica del valore dell'elemento.  L'ambiente richiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> per mantenere le informazioni visualizzate nella finestra di **Proprietà** sincronizzata con i valori della proprietà.  Per ulteriori informazioni, vedere [Aggiornamento dei valori della proprietà nella finestra Proprietà](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Oltre a selezionare un elemento di progetto diverso in **Esplora soluzioni** per visualizzare le proprietà correlate all'elemento, è possibile scegliere un oggetto diverso dall'interno di un form o una finestra del documento utilizzando l'elenco a discesa disponibile nella finestra di **Proprietà** .  Per ulteriori informazioni, vedere [Elenco di oggetti finestra delle proprietà](../../extensibility/internals/properties-window-object-list.md).  
  
 È possibile modificare la modalità con cui le informazioni visualizzate nella griglia della finestra di **Proprietà** da alfabetico a organizzato per categorie e, se disponibile, è anche possibile aprire una pagina delle proprietà di un oggetto selezionato facendo clic sui pulsanti appropriati nella finestra di **Proprietà** .  Per ulteriori informazioni, vedere [Pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md) e [Pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
 Infine, inferiore della finestra di **Proprietà** contiene anche una descrizione del campo selezionato nella griglia della finestra di **Proprietà** .  Per ulteriori informazioni, vedere [Descrizioni dei campi dalla finestra Proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)