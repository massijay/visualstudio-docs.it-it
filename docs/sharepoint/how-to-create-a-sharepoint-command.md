---
title: "How to: Create a SharePoint Command"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API.  Tale comando viene definito in un assembly in grado di effettuare chiamate direttamente nel modello a oggetti del server.  
  
 Per ulteriori informazioni sull'uso dei comandi di SharePoint, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Per creare un comando di SharePoint  
  
1.  Creare un progetto Libreria di classi avente la configurazione seguente:  
  
    -   Destinata a .NET Framework 3.5.  Per ulteriori informazioni sulla scelta del framework di destinazione, vedere [Procedura: destinare una versione di .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Destinata alla piattaforma AnyCPU o x64.  Per impostazione predefinita, la piattaforma di destinazione per i progetti Libreria di classi è AnyCPU.  Per ulteriori informazioni sulla scelta della piattaforma di destinazione, vedere [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/it-it/294a75d2-4279-4b72-8298-2bea05be907a).  
  
    > [!NOTE]  
    >  Non è possibile implementare un comando di SharePoint nello stesso progetto che definisce un'estensione degli strumenti di SharePoint, poiché i comandi di SharePoint sono destinati a .NET Framework 3.5 e le estensioni degli strumenti di SharePoint sono destinate a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Tutti i comandi di SharePoint utilizzati dall'estensione devono essere definiti in un progetto a parte.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  In una classe nel progetto, creare un metodo che definisce il comando di SharePoint.  Il metodo deve attenersi alle linee guida seguenti:  
  
    -   Può presentare uno o due parametri.  
  
         Il primo parametro deve essere un oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>.  Questo oggetto fornisce l'oggetto Microsoft.SharePoint.SPSite o Microsoft.SharePoint.SPWeb in cui viene eseguito il comando.  Fornisce inoltre un oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> che può essere utilizzato per scrivere messaggi nella finestra **Output** o nella finestra **Elenco errori** in Visual Studio.  
  
         Il secondo parametro può essere un tipo di propria scelta, ma è facoltativo.  Questo parametro può essere aggiunto al comando di SharePoint se è necessario passare dati dall'estensione degli strumenti di SharePoint al comando.  
  
    -   Può presentare un valore restituito.  
  
    -   Il secondo parametro e il valore restituito devono poter essere serializzati da Windows Communication Foundation \(WCF\).  Per ulteriori informazioni, vedere [Tipi supportati dal serializzatore dei contratti dati](http://msdn.microsoft.com/library/7381b200-437a-4506-9556-d77bf1bc3f34) e [Utilizzo della classe XmlSerializer](http://msdn.microsoft.com/library/c680602d-39d3-44f1-bf22-8e6654ad5069).  
  
    -   Il metodo può presentare qualsiasi tipo di visibilità \(**public**, **internal**o **private**\) e può essere statico o non statico.  
  
4.  Applicare l'oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al metodo.  Questo attributo specifica un identificatore univoco per il comando. Non è necessario che tale identificatore corrisponda al nome del metodo.  
  
     Questo stesso identificatore univoco deve essere specificato quando si chiama il comando dall'estensione degli strumenti di SharePoint.  Per ulteriori informazioni, vedere [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato un comando di SharePoint avente l'identificatore `Contoso.Commands.UpgradeSolution`.  Questo comando utilizza API nel modello a oggetti del server per eseguire l'aggiornamento a una soluzione distribuita.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 Oltre al primo parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implicito, questo comando presenta un parametro stringa personalizzato che contiene il percorso completo del file con estensione .wsp che si sta aggiornando al sito di SharePoint.  Per vedere questo codice nel contesto di un esempio più esaustivo, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## Distribuzione del comando  
 Per distribuire il comando, includere l'assembly del comando nello stesso pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) con l'assembly dell'estensione che utilizza il comando.  È inoltre necessario aggiungere una voce per l'assembly del comando nel file extension.vsixmanifest.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  