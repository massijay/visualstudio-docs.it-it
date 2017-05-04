---
title: "Calling into the SharePoint Object Models | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  Quando si creano estensioni per gli strumenti di SharePoint in Visual Studio, potrebbe essere necessario chiamare le API di SharePoint per effettuare alcune attività.  Ad esempio, se si crea un passaggio di distribuzione personalizzato per i progetti SharePoint, potrebbe essere necessario chiamare le API di SharePoint per effettuare alcune delle attività richieste per l'implementazione delle soluzioni.  
  
 In [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vengono forniti due modelli a oggetti diversi che è possibile utilizzare nelle estensioni degli strumenti di SharePoint: un modello a oggetti del server e uno del client.  Ogni modello a oggetti presenta vantaggi e svantaggi relativamente alle estensioni degli strumenti di SharePoint.  
  
 Per una panoramica sui modelli a oggetti di SharePoint, vedere [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Utilizzo del modello a oggetti del client nei progetti di estensione  
 Quando si sviluppa un'estensione per gli strumenti di SharePoint, il modello a oggetti del client nel progetto può essere utilizzato come qualsiasi altro set di API gestite.  È possibile aggiungere al progetto riferimenti agli assembly del modello a oggetti del client, nonché chiamare le API in tale modello direttamente dal codice.  
  
 Tuttavia, il modello a oggetti del client presenta due svantaggi relativamente alle estensioni degli strumenti di SharePoint:  
  
-   Nel modello a oggetti del client viene fornito solo un sottoinsieme del modello a oggetti del server.  Per poter utilizzare la funzionalità SharePoint che non è esposta nel modello a oggetti del client, è necessario utilizzare il modello a oggetti del server.  
  
-   Sebbene l'utilizzo del modello a oggetti del client nelle estensioni degli strumenti di SharePoint dovrebbe funzionare nella maggior parte dei casi, si potrebbero riscontrare delle situazioni in cui le chiamate al modello a oggetti del client non funzionano come previsto.  Il modello a oggetti del client è progettato per essere utilizzato nelle applicazioni client per effettuare chiamate nei siti di SharePoint su una farm o un server remoto.  Gli strumenti di SharePoint in Visual Studio funzionano solo con un'installazione di SharePoint locale sul computer di sviluppo.  Di conseguenza, quando si utilizza il modello a oggetti del client in un'estensione degli strumenti di SharePoint, le chiamate vengono effettuate in un sito di SharePoint nel computer locale, una modalità diversa rispetto a quella in cui il modello a oggetti del client è progettato per essere utilizzato.  
  
 Per una procedura dettagliata che illustra come utilizzare il modello a oggetti del client in un'estensione degli strumenti di SharePoint in Visual Studio, vedere [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Utilizzo del modello a oggetti del server nei progetti di estensione  
 Il modello a oggetti del server è un superset del modello a oggetti del client.  Quando si utilizza il modello a oggetti del server, è possibile utilizzare tutte le funzionalità esposte a livello di codice da [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  
  
 Nelle estensioni degli strumenti di SharePoint è possibile utilizzare le API nel modello a oggetti del server, ma non chiamarle direttamente.  Il modello a oggetti del server può essere chiamato solo da un processo a 64 bit destinato a .NET Framework 3.5.  Tuttavia, per le estensioni degli strumenti di SharePoint è richiesto [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e tali estensioni vengono eseguite nel processo di Visual Studio a 32 bit.  Ciò evita che le estensioni degli strumenti di SharePoint facciano riferimento in modo diretto agli assembly nel modello a oggetti del server SharePoint.  
  
 Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API.  Tale comando viene definito in un assembly secondario che consente di effettuare direttamente chiamate nel modello a oggetti del server.  Nel progetto di estensione, il comando di SharePoint viene chiamato indirettamente tramite il metodo ExecuteCommand di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Per ulteriori informazioni sulla creazione e l'utilizzo dei comandi di SharePoint, vedere [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) e [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  Per informazioni sulla distribuzione dei comandi di SharePoint, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Per le procedure dettagliate in cui viene illustrato come creare e utilizzare i comandi di SharePoint, vedere [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### Informazioni sull'esecuzione dei comandi di SharePoint  
 Gli assembly che definiscono i comandi di SharePoint vengono caricati in un processo host a 64 bit denominato vssphost4.exe.  Dopo avere chiamato un comando di SharePoint in un'estensione degli strumenti di SharePoint, il comando viene eseguito da vssphost4.exe, anziché dal processo a 32 bit di Visual Studio \(devenv.exe\).  È possibile controllare alcuni aspetti dell'esecuzione dei comandi di SharePoint impostando i valori nel Registro di sistema.  Per ulteriori informazioni, vedere [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  