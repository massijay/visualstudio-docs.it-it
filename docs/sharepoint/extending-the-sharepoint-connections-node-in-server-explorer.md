---
title: "Extending the SharePoint Connections Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  In Visual Studio, è possibile connettersi ai siti di SharePoint locali nel computer di sviluppo tramite il nodo di  **Connessioni di SharePoint** nella finestra di**Esplora server** .  Questo nodo consente di visualizzare molti dei componenti dei siti di SharePoint locali in una visualizzazione struttura ad albero gerarchica.  Ad esempio, è possibile visualizzare elenchi, raccolte documenti e i tipi di contenuto nei siti locali. Per ulteriori informazioni sull'utilizzo di **Esplora server** per connettersi ai siti di SharePoint locali, vedere [Esplorazione di connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 È possibile estendere il nodo **Connessioni di SharePoint** creando estensioni per i nodi esistenti o creando un tipo di nodo personalizzato e aggiungendolo alla gerarchia di nodi.  
  
## Attività per estendere il nodo Connessioni di SharePoint  
 Per estendere un nodo esistente, creare un'estensione di Visual Studio che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Quando si estende un nodo, è possibile aggiungere funzionalità al nodo, ad esempio voci di menu di scelta rapida o proprietà personalizzate.  Per ulteriori informazioni, vedere [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Per creare un tipo di nodo personalizzato, creare un'estensione di Visual Studio che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Creare un nodo personalizzato se si desidera visualizzare i componenti dei siti di SharePoint che, per impostazione predefinita, non sono visualizzati in **Esplora server**.  Ad esempio, per impostazione predefinita, in **Esplora server** non viene visualizzata la raccolta di web part di un sito di SharePoint, ma è possibile aggiungere un nodo personalizzato che consente di eseguire tale operazione.  Per ulteriori informazioni, vedere [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) e [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Aggiunta di proprietà personalizzate ai nodi  
 Quando si estende un nodo o si crea un tipo di nodo personalizzato, è possibile aggiungere proprietà personalizzate al nodo.  Le proprietà vengono visualizzate nella finestra **Proprietà** quando il nodo viene selezionato.  
  
 Sono due i tipi di proprietà personalizzate che è possibile aggiungere a un nodo:  
  
-   Proprietà che consentono di visualizzare un set di dati di sola lettura dal sito di SharePoint.  I dati descrivono il componente di SharePoint rappresentato dal nodo.  Per la relativa procedura dettagliata, vedere [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Proprietà che consentono di visualizzare dati personalizzati in lettura\/scrittura.  Per un esempio di codice che illustra come eseguire questa operazione, vedere [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Acquisizione di dati per nodi incorporati  
 Tutti i nodi incorporati forniti da Visual Studio includono dati relativi al componente di SharePoint che rappresentano.  Ad esempio, un nodo che rappresenta un elenco nel sito di SharePoint fornisce dati sull'elenco, quali il titolo e l'URL della visualizzazione predefinita dell'elenco.  
  
 Per accedere a questi dati, recuperare un oggetto dati dalla proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> che rappresenta il nodo di interesse.  Il tipo dell'oggetto dati varia in base al tipo del nodo.  
  
 Nell'esempio di codice seguente viene illustrato come ottenere l'oggetto dati per un nodo elenco.  Per vedere questo esempio nel contesto di un esempio più esaustivo, vedere [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 Nella tabella seguente sono elencati i tipi di oggetto dati per ogni tipo di nodo incorporato.  
  
|Tipo di nodo|Tipo di oggetto dati|  
|------------------|--------------------------|  
|Nodo del sito di SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Tipo di contenuto|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Funzionalità|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Modello di elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Visualizzazione elenco \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Associazione flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Modello di flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Per ulteriori informazioni sull'utilizzo della proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, vedere [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Vedere anche  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  