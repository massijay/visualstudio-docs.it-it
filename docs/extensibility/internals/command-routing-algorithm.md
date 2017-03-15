---
title: "Algoritmo di Routing di comandi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi, routing"
  - "comandi (routing)"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Algoritmo di Routing di comandi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Visual Studio i comandi vengono gestiti da una serie di diversi componenti. Indirizzare i comandi da un contesto più interno, che è basato sulla selezione corrente, nel contesto più esterno \(noto anche come globale\). Per altre informazioni, vedere [Disponibilità](../../extensibility/internals/command-availability.md).  
  
## Ordine di risoluzione di comando  
 I comandi vengono passati tramite i seguenti livelli di contesto del comando:  
  
1.  Componenti aggiuntivi: L'ambiente in primo luogo offre il comando per tutti i componenti aggiuntivi che sono presenti.  
  
2.  I comandi di priorità: questi comandi vengono registrati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Che vengono chiamati per ogni comando in Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.  
  
3.  Comandi del menu contestuale: un comando che si trova in un menu di scelta rapida prima viene offerto alla destinazione di comando che viene fornita per il menu di scelta rapida e in seguito al ciclo tipico.  
  
4.  Barra degli strumenti imposta destinazioni dei comandi: queste destinazioni comandi vengono registrate quando si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Il `pCmdTarget` parametro può essere `null`. Se non è `null`, la destinazione del comando viene utilizzato per aggiornare tutti i comandi si trova sulla barra degli strumenti che si sta impostando. Se la shell è l'impostazione la barra degli strumenti, quindi passa la cornice della finestra come il `pCmdTarget` in modo che tutti gli aggiornamenti per i comandi sulla barra degli strumenti flusso tramite la cornice della finestra, anche quando non è attivo.  
  
5.  Finestra degli strumenti: Strumenti di windows, che solitamente implementano la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l'interfaccia, deve inoltre implementare la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia in modo che Visual Studio è possibile ottenere la destinazione del comando quando la finestra degli strumenti è la finestra attiva. Tuttavia, se la finestra degli strumenti con lo stato attivo è il **progetto** finestra, quindi il comando viene indirizzato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia che rappresenta l'elemento padre comune degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia contiene i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metodi che sono simili ai comandi corrispondenti nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
6.  Finestra del documento: Se il comando è associato il flag RouteToDocs impostato nel relativo file. vsct, Visual Studio cerca una destinazione del comando sull'oggetto di visualizzazione documento, vale a dire un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia o un'istanza di un oggetto documento \(in genere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia o un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface\). Se l'oggetto visualizzazione documento non supporta il comando, Visual Studio instrada il comando per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia restituita. \(Questa è un'interfaccia facoltativa per gli oggetti dati documento\).  
  
7.  Gerarchia corrente: la gerarchia corrente può essere il progetto che possiede la finestra del documento attivo o la gerarchia selezionata nel **Esplora**. Visual Studio cerca i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia implementata sulla gerarchia corrente o attiva. La gerarchia deve supportare comandi validi ogni volta che la gerarchia è attiva, anche se una finestra del documento di un elemento di progetto ha lo stato attivo. Tuttavia, i comandi che si applicano solo quando **Esplora** ha lo stato attivo deve essere supportato tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia e il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>metodi.  
  
     **Taglia**, **Copia**, **Incolla**, **eliminare**, **rinominare**, **INVIO**, e **DoubleClick** comandi richiedono una gestione speciale. Per informazioni su come gestire **eliminare** e **rimuovere** comandi nelle gerarchie, vedere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaccia.  
  
8.  Globale: Se un comando non è stato gestito da contesti menzionati in precedenza, Visual Studio tenta di inviarlo a VSPackage che possiede un comando che implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Se il package VS non è già stato caricato, non viene caricato quando Visual Studio chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Il package VS viene caricato solo quando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> viene chiamato il metodo.  
  
## Vedere anche  
 [Progettazione di comando](../../extensibility/internals/command-design.md)