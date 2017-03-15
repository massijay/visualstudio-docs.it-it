---
title: "Salvare in modo permanente la propriet&#224; di un elemento di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proprietà, aggiunta a un elemento di progetto"
  - "elementi di progetto, l'aggiunta di proprietà"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Salvare in modo permanente la propriet&#224; di un elemento di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È consigliabile mantenere una proprietà che aggiungere un elemento di progetto, ad esempio l'autore di un file di origine. È possibile farlo archiviando la proprietà nel file di progetto.  
  
 È il primo passaggio per mantenere una proprietà in un file di progetto per ottenere la gerarchia del progetto come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia. È possibile ottenere questa interfaccia utilizzando l'automazione o utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Una volta ottenuto l'interfaccia, è possibile utilizzare, per determinare quale elemento del progetto è attualmente selezionato. Dopo aver ottenuto l'ID di elemento di progetto, è possibile utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> per aggiungere la proprietà.  
  
 Nelle procedure seguenti, mantenere la proprietà VsPkg.cs `Author` con il valore `Tom` nel file di progetto.  
  
### Per ottenere la gerarchia del progetto con l'oggetto DTE  
  
1.  Aggiungere il codice seguente per il pacchetto Visual Studio:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### Per mantenere la proprietà di elemento di progetto con l'oggetto DTE  
  
1.  Aggiungere il codice seguente al codice fornito nel metodo nella procedura precedente:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Per ottenere la gerarchia del progetto mediante IVsMonitorSelection  
  
1.  Aggiungere il codice seguente per il pacchetto Visual Studio:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### Per mantenere la proprietà di elemento di progetto selezionato, data la gerarchia del progetto  
  
1.  Aggiungere il codice seguente al codice fornito nel metodo nella procedura precedente:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Per verificare che la proprietà è persistente  
  
1.  Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire o creare una soluzione.  
  
2.  Selezionare il progetto elemento VsPkg.cs in **Esplora**.  
  
3.  In caso contrario, determinare che il pacchetto Visual Studio viene caricato ed eseguita SetItemAttribute utilizzare un punto di interruzione.  
  
    > [!NOTE]
    >  È possibile caricare automaticamente un VSPackage nel contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Per altre informazioni, vedere [Caricamento VS](../extensibility/loading-vspackages.md).  
  
4.  Chiudi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire il file di progetto nel blocco note. Il tag \< Author \> con il valore Tom, verrà visualizzato come segue:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## Vedere anche  
 [Strumenti personalizzati](../extensibility/internals/custom-tools.md)