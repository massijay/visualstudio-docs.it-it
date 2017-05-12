---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  È possibile aggiungere nodi personalizzati sotto il nodo **Connessioni di SharePoint** in **Esplora server**.  Questa operazione è utile quando si desidera visualizzare componenti di SharePoint aggiuntivi che, per impostazione predefinita, non sono visualizzati in **Esplora server**.  Per ulteriori informazioni, vedere [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Per aggiungere un nodo personalizzato, creare innanzitutto una classe che consente di definire il nuovo nodo.  Successivamente creare un'estensione che consente di aggiungere il nodo come elemento figlio di un nodo esistente.  
  
### Per definire il nuovo nodo  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Creare una classe che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Aggiungere gli attributi seguenti alla classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> al costruttore di attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  In una definizione del nodo, questo attributo consente di specificare l'identificatore di stringa per il nuovo nodo.  È consigliabile utilizzare il formato *nome società*.*nome nodo* per assicurarsi che tutti i nodi dispongano di un identificatore univoco.  
  
5.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> utilizzare i membri del parametro *typeDefinition* per configurare il comportamento del nuovo nodo.  Questo parametro è un oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> che fornisce accesso agli eventi definiti nell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  
  
     Nell'esempio di codice seguente viene illustrato come definire un nuovo nodo.  In questo esempio si presuppone che nel progetto sia inclusa un'icona denominata CustomChildNodeIcon come risorsa incorporata  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### Per aggiungere il nuovo nodo come elemento figlio di un nodo esistente  
  
1.  Nello stesso progetto della definizione del nodo creare una classe che consente di implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
2.  Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> al costruttore dell'attributo.  
  
3.  Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe.  In un'estensione del nodo questo attributo consente di specificare l'identificatore di stringa per il tipo di nodo che si desidera estendere.  
  
     Per specificare i tipi di nodi predefiniti forniti da Visual Studio, passare uno dei valori di enumerazione seguenti al costruttore dell'attributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: utilizzare questi valori per specificare i nodi relativi alla connessione ai siti \(i nodi in cui è visualizzato l'URL del sito\), i nodi dei siti o tutti gli altri nodi padre in **Esplora server**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: utilizzare questi valori per specificare uno dei nodi incorporati che rappresentano un singolo componente in un sito SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.  
  
4.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> del parametro <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>.  
  
5.  Nel gestore dell'evento <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> aggiungere il nuovo nodo alla raccolta dei nodi figlio dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> esposto dal parametro degli argomenti dell'evento.  
  
     Nell'esempio di codice seguente viene illustrato come aggiungere il nuovo nodo come figlio del nodo del sito di SharePoint in **Esplora server**.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## Esempio completo  
 Nell'esempio di codice seguente viene fornito il codice completo per definire un nodo semplice e aggiungerlo come figlio del nodo del sito di SharePoint in **Esplora server**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## Compilazione del codice  
 In questo esempio si presuppone che nel progetto sia inclusa un'icona denominata CustomChildNodeIcon come risorsa incorporata  e sono inoltre richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione di **Esplora server**, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  