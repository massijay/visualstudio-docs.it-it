---
title: "How to: Handle Deployment Conflicts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  È possibile fornire il proprio codice ai conflitti di distribuzione dell'handle per un elemento di progetto SharePoint.  Ad esempio, è possibile determinare se i file nell'elemento di progetto corrente sono già presenti nel percorso di distribuzione, quindi eliminare i file distribuiti prima della distribuzione dell'elemento di progetto corrente.  Per ulteriori informazioni sui conflitti di distribuzione, vedere [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Per gestire un conflitto di distribuzione  
  
1.  Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto.  Per ulteriori informazioni, vedere i seguenti argomenti:  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Nell'estensione gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> \(in un'estensione di elemento di progetto o in un'estensione di progetto\) o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> \(in una definizione di un nuovo tipo di elemento di progetto\).  
  
3.  Nel gestore eventi determinare se esiste un conflitto tra l'elemento di progetto che si sta distribuendo e la soluzione distribuita nel sito di SharePoint, in base ai criteri che si applicano allo scenario.  È possibile utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> del parametro degli argomenti dell'evento per analizzare l'elemento del progetto che si sta distribuendo ed è possibile analizzare i file nel percorso di distribuzione chiamando un comando di SharePoint definito per questo scopo.  
  
     Per molti tipi di conflitti è possibile che si voglia innanzitutto determinare quale passaggio relativo alla distribuzione viene eseguito.  È possibile eseguire questa operazione utilizzando la proprietà <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> del parametro degli argomenti dell'evento.  Sebbene in genere sia opportuno rilevare i conflitti durante il passaggio relativo alla distribuzione <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> incorporato, è possibile verificare se esistono conflitti durante qualsiasi passaggio relativo alla distribuzione.  
  
4.  In caso di conflitti, utilizzare il metodo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> della proprietà <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> degli argomenti dell'evento per creare un nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>.  Questo oggetto rappresenta il conflitto di distribuzione.  Nella chiamata al metodo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> specificare anche il metodo chiamato per risolvere il conflitto.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato il processo di base per gestire un conflitto di distribuzione in un'estensione di elemento di progetto per gli elementi del progetto di definizione di elenco.  Per gestire un conflitto di distribuzione per un altro tipo di elemento di progetto, passare una stringa diversa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Per ulteriori informazioni, vedere [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
 Per semplicità, nel gestore eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> in questo esempio si presuppone che un conflitto di distribuzione esista \(ovvero, aggiunge sempre un nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\) e il metodo `Resolve` restituisca semplicemente **true** per indicare che il conflitto è stato risolto.  In uno scenario reale il gestore eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> innanzitutto determinerebbe se esiste un conflitto tra un file nell'elemento di progetto corrente e un file nel percorso di distribuzione e quindi aggiungerebbe un oggetto <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> solo in presenza di un conflitto.  Ad esempio, è possibile utilizzare la proprietà `e.ProjectItem.Files` nel gestore eventi per analizzare i file nell'elemento di progetto e chiamare un comando di SharePoint per analizzare i file nel percorso di distribuzione.  Analogamente, in uno scenario reale il metodo `Resolve` potrebbe chiamare un comando di SharePoint per risolvere il conflitto sul sito di SharePoint.  Per ulteriori informazioni sulla creazione di comandi di SharePoint, vedere [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  