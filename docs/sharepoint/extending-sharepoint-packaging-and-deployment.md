---
title: "Extending SharePoint Packaging and Deployment | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  È possibile estendere il processo di creazione di pacchetti e distribuzione per i progetti SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> Creazione delle fasi di distribuzione  
 Per la distribuzione di un progetto SharePoint in [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] sono previste varie fasi.  Visual Studio include fasi di distribuzione predefinite per molte attività, quali la ritrazione e l'aggiunta di soluzioni.  È comunque possibile creare fasi di distribuzione personalizzate.  
  
 Per una procedura dettagliata sulla creazione di una fase di distribuzione, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating_deployment_configurations"></a> Creazione delle configurazioni di distribuzione  
 Una configurazione di distribuzione è un set di fasi di distribuzione che viene eseguito per un determinato progetto, ma può influire su tutti gli elementi del progetto SharePoint.  Tutte le configurazioni di distribuzione includono un set di passaggi eseguito quando viene distribuito il progetto e un altro set eseguito in caso di retrazione.  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] include due configurazioni di distribuzione incorporate, ma è anche possibile crearne di proprie.  Quando si crea una configurazione di distribuzione, è possibile includere fasi di distribuzione predefinite e fasi personalizzate.  
  
 Per una procedura dettagliata sulla creazione di una configurazione di distribuzione, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> Eseguire codice quando una soluzione SharePoint viene distribuita o ritratta  
 È possibile gestire gli eventi per eseguire attività aggiuntive quando una soluzione SharePoint viene distribuita o ritratta.  Visual Studio genera eventi che è possibile gestire negli scenari seguenti:  
  
-   Prima e dopo l'esecuzione di ogni passaggio di distribuzione per un elemento di progetto SharePoint.  Per altre informazioni, vedere [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Prima e dopo che un progetto SharePoint viene distribuito o ritratto.  Per altre informazioni, vedere [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="deployment_conflicts"></a> Gestione dei conflitti di distribuzione  
 Alcuni tipi di elementi di progetto SharePoint, tra cui moduli, Web part, istanze di elenco e tipi di contenuto, forniscono la risoluzione incorporata dei conflitti di distribuzione.  Quando si distribuisce una soluzione che contiene uno di questi elementi di progetto, Visual Studio verifica innanzitutto se esiste già un file nel sito di SharePoint con lo stesso nome, URL o ID come file nell'elemento che si sta distribuendo.  Se si verifica un conflitto, Visual Studio è in grado di risolvere automaticamente il conflitto o di chiedere conferma all'utente per determinare se desidera risolvere il conflitto o annullare la distribuzione in Visual Studio.  Per altre informazioni, vedere [Risoluzione dei problemi relativi alla creazione di pacchetti e alla distribuzione di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 È possibile estendere questa funzionalità fornendo codice personalizzato per la verifica e la risoluzione dei conflitti di distribuzione.  Per altre informazioni, vedere [How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> Eseguire le operazioni della riga di comando prima o dopo la distribuzione di un progetto  
 Se si desidera eseguire un'operazione della riga di comando quando si distribuisce una soluzione SharePoint, è possibile impostare le proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  Visual Studio esegue questi comandi prima e dopo la distribuzione del progetto.  
  
 In alcuni casi, possono verificarsi conflitti di distribuzione.  Sono disponibili diversi modi per risolvere i conflitti.  Per altre informazioni, vedere [Risoluzione dei problemi relativi alla creazione di pacchetti e alla distribuzione di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing_validation_rules"></a> Personalizzazione delle regole di convalida  
 Prima di distribuire un pacchetto di soluzioni \(con estensione wsp\), è possibile creare funzionalità personalizzate e regole di convalida del pacchetto per verificare che la funzionalità o il pacchetto siano validi.  Ad esempio, è possibile segnalare informazioni, avvisi o errori per consentire agli sviluppatori di risolvere i problemi di convalida.  Per altre informazioni, vedere [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Vedere anche  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  