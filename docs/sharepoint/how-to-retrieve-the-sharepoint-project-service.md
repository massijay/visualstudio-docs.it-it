---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  È possibile accedere al servizio di progetto SharePoint nei tipi di soluzioni seguenti:  
  
-   Estensione del sistema di progetto SharePoint, ad esempio un'estensione di progetto, un'estensione di elemento di progetto o una definizione di tipo di elemento di progetto.  Per ulteriori informazioni su questi tipi di estensioni, vedere [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Estensione del nodo **Connessioni di SharePoint** in **Esplora server**.  Per ulteriori informazioni su questi tipi di estensioni, vedere [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Estensione di Visual Studio di altro tipo, ad esempio un componente aggiuntivo o un VSPackage.  
  
## Recupero del servizio nelle estensioni del sistema di progetto  
 In qualsiasi estensione del sistema di progetto SharePoint, è possibile accedere al servizio di progetto tramite la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  
  
 Il servizio di progetto può essere recuperato anche mediante le procedure seguenti.  
  
#### Per recuperare il servizio in un'estensione di progetto  
  
1.  Nell'implementazione dell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, individuare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  
  
2.  Utilizzare il parametro *projectService* per accedere al servizio.  
  
     Nell'esempio di codice seguente viene mostrato come utilizzare il servizio di progetto per scrivere un messaggio nelle finestre **Output** ed **Elenco errori** in un'estensione di progetto semplice.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     Per ulteriori informazioni sulla creazione di estensioni di progetto, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### Per recuperare il servizio in un'estensione di elemento di progetto  
  
1.  Nell'implementazione dell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, individuare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  
  
2.  Utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> del parametro *projectItemType* per recuperare il servizio.  
  
     Nell'esempio di codice seguente viene mostrato come utilizzare il servizio di progetto per scrivere un messaggio nelle finestre **Output** ed **Elenco errori** in un'estensione semplice dell'elemento di progetto **Definizione di elenco**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     Per ulteriori informazioni sulla creazione di estensioni di elemento di progetto, vedere [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### Per recuperare il servizio in una definizione di tipo di elemento di progetto  
  
1.  Nell'implementazione dell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, individuare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  
  
2.  Utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> del parametro *typeDefinition* per recuperare il servizio.  
  
     Nell'esempio di codice seguente viene mostrato come utilizzare il servizio di progetto per scrivere un messaggio nelle finestre **Output** ed **Elenco errori** in una definizione di tipo di elemento di progetto semplice.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     Per ulteriori informazioni sulla definizione di tipi di elemento di progetto, vedere [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Recupero del servizio nelle estensioni di Esplora server  
 In un'estensione del nodo **Connessioni di SharePoint** in **Esplora server** è possibile accedere al servizio di progetto tramite la proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>.  
  
#### Per recuperare il servizio in un'estensione di Esplora server  
  
1.  Ottenere un oggetto <xref:System.IServiceProvider> dalla proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> nell'estensione.  
  
2.  Utilizzare il metodo <xref:System.IServiceProvider.GetService%2A> per richiedere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
     Nell'esempio di codice seguente viene mostrato come utilizzare il servizio di progetto per scrivere un messaggio nelle finestre **Output** ed **Elenco errori** da un menu di scelta rapida che l'estensione aggiunge ai nodi di elenco in **Esplora server**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     Per ulteriori informazioni sull'estensione del nodo **Connessioni di SharePoint** in **Esplora server**, vedere [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Recupero del servizio in estensioni di Visual Studio di altro tipo  
 È possibile recuperare il servizio di progetto in un VSPackage o in qualsiasi estensione di Visual Studio in grado di accedere a un oggetto <xref:EnvDTE80.DTE2> nel modello a oggetti di automazione, ad esempio un componente aggiuntivo o una procedura di creazione guidata di modelli di progetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
 In un VSPackage è possibile richiedere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> tramite uno dei metodi seguenti:  
  
-   Il metodo <xref:System.IServiceProvider.GetService%2A> di un VSPackage gestito che deriva dalla classe <xref:Microsoft.VisualStudio.Shell.Package>.  Per ulteriori informazioni, vedere [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md).  
  
-   Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>.  Per ulteriori informazioni, vedere [Procedura: Usare GetGlobalService](../Topic/How%20to:%20Use%20GetGlobalService.md).  
  
 In un'estensione di Visual Studio in grado di accedere a un oggetto <xref:EnvDTE80.DTE2> è possibile richiedere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> tramite il metodo <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> di un oggetto <xref:Microsoft.VisualStudio.Shell.ServiceProvider>.  Per ulteriori informazioni, vedere [Procedura: Ottenere un servizio dall'oggetto DTE](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md).  
  
### Esempio  
 Nell'esempio di codice seguente viene illustrato come recuperare il servizio di progetto in un componente aggiuntivo di Visual Studio.  Per utilizzare questo codice, eseguirlo dalla classe `Connect` in un progetto di componente aggiuntivo.  L'oggetto `_applicationObject` viene generato automaticamente nei progetti di componente aggiuntivo. Questo oggetto è un'istanza dell'interfaccia <xref:EnvDTE80.DTE2>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 L'esempio presenta i seguenti requisiti:  
  
-   Progetto di componente aggiuntivo di Visual Studio  Per ulteriori informazioni, vedere [Procedura: creare un componente aggiuntivo](../Topic/How%20to:%20Create%20an%20Add-In.md).  
  
-   Riferimenti agli assembly Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell e Microsoft.VisualStudio.SharePoint.  
  
## Vedere anche  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Procedura: creare un componente aggiuntivo](../Topic/How%20to:%20Create%20an%20Add-In.md)   
 [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Procedura: Ottenere un servizio dall'oggetto DTE](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)   
 [Procedura: utilizzare procedure guidate con modelli di progetto](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  