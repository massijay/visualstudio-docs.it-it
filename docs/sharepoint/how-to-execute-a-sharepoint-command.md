---
title: "How to: Execute a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API.  Dopo aver definito il comando e averlo distribuito nell'estensione degli strumenti di SharePoint, l'estensione può utilizzare il comando per eseguire chiamate nel modello a oggetti del server SharePoint.  Per eseguire il comando, utilizzare uno dei metodi ExecuteCommand di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Per ulteriori informazioni sull'uso dei comandi di SharePoint, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Per eseguire un comando di SharePoint  
  
1.  Nell'estensione degli strumenti di SharePoint, ottenere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Il modo in cui ottenere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> dipende dal tipo di estensione da creare:  
  
    -   In un'estensione del sistema di progetto SharePoint, utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>.  
  
         Per ulteriori informazioni sulle estensioni del sistema di progetto, vedere [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   In un'estensione del nodo **Connessioni di SharePoint** in **Esplora server**, utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>.  Per ottenere l'oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>.  
  
         Per ulteriori informazioni sulle estensioni di **Esplora server**, vedere [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Nel codice che non fa parte di un'estensione degli strumenti di SharePoint, ad esempio una creazione guidata di modelli di progetto, utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.  
  
         Per ulteriori informazioni sul recupero del servizio del progetto, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Chiamare uno dei metodi ExecuteCommand dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Passare il nome del comando che si desidera eseguire al primo argomento del metodo ExecuteCommand.  Se il comando presenta un parametro personalizzato, passare tale parametro al secondo argomento del metodo ExecuteCommand.  
  
     È previsto un diverso overload del metodo ExecuteCommand per ogni firma del comando supportata.  Nella tabella seguente vengono elencate le firme supportate e l'overload da utilizzare per ognuna di esse.  
  
    |Firma del comando|Overload del metodo ExecuteCommand da utilizzare|  
    |-----------------------|------------------------------------------------------|  
    |Il comando dispone solo del parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e non presenta alcun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando dispone solo del parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e di un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando dispone di due parametri \(il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e un parametro personalizzato\) e non presenta alcun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Il comando dispone di due parametri e di un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come utilizzare l'overload di <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> per chiamare il comando `Contoso.Commands.UpgradeSolution` descritto in [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 Il metodo `Execute` mostrato in questo esempio è un'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> dell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> in un passaggio relativo alla distribuzione personalizzata.  Per vedere questo codice nel contesto di un esempio più esaustivo, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Tenere presente i dettagli seguenti relativi alla chiamata al metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>:  
  
-   Il primo parametro identifica il comando che si desidera chiamare.  Questa stringa corrisponde al valore passato all'oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sulla definizione dei comandi.  
  
-   Il secondo parametro è il valore che si desidera passare al secondo parametro personalizzato del comando.  In questo caso, è il percorso completo del file con estensione .wsp che si sta aggiornando al sito di SharePoint.  
  
-   Il codice non consente di passare il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implicito al comando.  Questo parametro viene passato nel comando automaticamente quando quest'ultimo viene chiamato da un'estensione del sistema di progetto SharePoint o da un'estensione del nodo **Connessioni di SharePoint** in **Esplora server**.  In altri tipi di soluzioni, ad esempio in una creazione guidata di modelli di progetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, questo parametro è **null**.  
  
## Compilazione del codice  
 In questo esempio viene richiesto un riferimento all'assembly Microsoft.VisualStudio.SharePoint.  
  
## Vedere anche  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  