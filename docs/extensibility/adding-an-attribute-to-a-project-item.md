---
title: "Aggiunta di un attributo a un elemento di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributi [Visual Studio], aggiunta a un elemento di progetto"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Aggiunta di un attributo a un elemento di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

The methods <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> and <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> get and set the value of the attributes of a project item.  SetItemAttribute crea l'attributo se non ne esiste già, aggiungendolo ai metadati di elemento di progetto.  
  
## Aggiungere un attributo a un elemento di progetto  
  
#### Per aggiungere un attributo a un elemento di progetto  
  
-   Il codice seguente utilizza l'oggetto ActiveX di <xref:EnvDTE.DTE> e il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> per aggiungere un attributo a un elemento di progetto.  L'elemento di progetto ID viene ottenuto dal nome “program.cs„ elemento di progetto.  L'attributo “MyAttribute„ viene aggiunta a questo elemento di progetto e viene assegnato il valore “MyValue„.  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## Vedere anche  
 [Rendere persistenti i dati nel File di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)