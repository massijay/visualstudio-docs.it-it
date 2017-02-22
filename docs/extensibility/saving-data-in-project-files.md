---
title: "Salvataggio di dati nei file di progetto | Microsoft Docs"
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
  - "dati [Visual Studio], salvare in file di progetto"
  - "file di progetto"
  - "file di progetto, il salvataggio dei dati"
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Salvataggio di dati nei file di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un sottotipo di progetto può salvare e recuperare i dati sottotipo\-specifici nel file di progetto.  Il pacchetto gestito Framework \(MPF\) fornisce due interfacce per eseguire questa attività:  
  
-   L'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> consente ai valori delle proprietà di accesso dalla sezione di **MSBuild** del file di progetto.  I metodi forniti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> possono essere chiamati da qualsiasi utente ogni volta che l'utente deve caricare o salvare la compilazione relativi dati.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> viene utilizzato per rendere persistenti i dati correlati non compilazione in formato libero XML.  I metodi forniti da <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> vengono chiamati da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che le necessità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di mantenere il non compilazione relativi dati nel file di progetto.  
  
 Per ulteriori informazioni su come mantenere la compilazione e il non compilazione dati correlati, vedere [Rendere persistenti i dati nel File di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## Salvare e recuperare i dati correlati di compilazione  
  
#### Per salvare una compilazione correlate ai dati nel file di progetto  
  
-   Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> per salvare un percorso completo del file di progetto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### Per recuperare la compilazione correlate ai dati del file di progetto  
  
-   Chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> per recuperare un percorso completo del file di progetto.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## Salvare e recuperare i dati correlati non di compilazione  
  
#### Per salvare il non compilazione correlate ai dati nel file di progetto  
  
1.  Implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> per determinare se un frammento XML è stato modificato dal momento dell'ultimo salvataggio del file corrente.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> per salvare i dati XML nel file di progetto.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### Per recuperare le informazioni di descrizione che verrà visualizzata per il nome della proprietà evidenziato, la finestra **Proprietà** chiama <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> per la proprietà selezionata, specificando l'attributo desiderato `lcid` per la stringa di output.  
  
1.  Implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> per inizializzare le proprietà dell'estensione di progetto e altri dati dell'build\-indipendente.  Questo metodo viene chiamato se non sono disponibili dati di configurazione XML presenti nel file di progetto.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> per caricare i dati XML dal file di progetto.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Tutti gli esempi di codice forniti in questo argomento fanno parte di un esempio più esaustivo [Esempi di VSSDK](../misc/vssdk-samples.md).  
  
## Vedere anche  
 [Rendere persistenti i dati nel File di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)