---
title: "How to: Extend a SharePoint Node in Server Explorer"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  È possibile estendere i nodi sotto il nodo **Connessioni di SharePoint** in **Esplora server**.  Ciò si rivela utile quando si desidera aggiungere a un nodo esistente nuovi nodi figlio, elementi di menu di scelta rapida o proprietà.  Per ulteriori informazioni, vedere [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### Per estendere un nodo SharePoint in Esplora server  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> al costruttore dell'attributo.  
  
5.  Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe.  Questo attributo specifica l'identificatore di stringa per il tipo di nodo che si desidera estendere.  
  
     Per specificare i tipi di nodi predefiniti forniti da Visual Studio, passare uno dei valori di enumerazione seguenti al costruttore dell'attributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: utilizzare questi valori per specificare i nodi relativi alla connessione ai siti \(i nodi in cui è visualizzato l'URL del sito\), i nodi dei siti o tutti gli altri nodi padre in **Esplora server**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: utilizzare questi valori per specificare uno dei nodi incorporati che rappresentano un singolo componente in un sito SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.  
  
6.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, utilizzare i membri del parametro *nodeType* per aggiungere funzionalità al nodo.  Questo parametro è un oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> che fornisce accesso agli eventi definiti nell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  Ad esempio, è possibile gestire gli eventi seguenti:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: gestire questo evento per aggiungere al nodo nuovi nodi figlio.  Per ulteriori informazioni, vedere [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: gestire questo evento per aggiungere al nodo un elemento di menu di scelta rapida personalizzato.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: gestire questo evento per aggiungere al nodo proprietà personalizzate.  Le proprietà vengono visualizzate nella finestra **Proprietà** quando il nodo viene selezionato.  
  
## Esempio  
 Nell'esempio di codice seguente viene mostrato come creare due tipi diversi di estensioni di nodo:  
  
-   Un'estensione che aggiunge un elemento di menu di scelta rapida ai nodi di sito SharePoint.  Quando si fa clic sulla voce di menu, verrà visualizzato il nome del nodo selezionato.  
  
-   Un'estensione che aggiunge una proprietà personalizzata denominata **ContosoExampleProperty** a ogni nodo che rappresenta un campo denominato **Body**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 Questa estensione aggiunge ai nodi una proprietà stringa modificabile.  È inoltre possibile creare proprietà personalizzate che visualizzano dati di sola lettura ottenuti dal server SharePoint.  Per un esempio che illustra come eseguire questa operazione, vedere [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione di **Esplora server**, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  